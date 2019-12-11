---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Considérations de sécurité JEA
ms.openlocfilehash: befc24fec368c4f6d60477daf63bf17e9431133e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70017770"
---
# <a name="jea-security-considerations"></a>Considérations de sécurité JEA

JEA vous aide à améliorer votre sécurité en réduisant le nombre d’administrateurs permanents sur vos machines. JEA utilise une configuration de session PowerShell pour créer un point d’entrée pour les utilisateurs afin de gérer le système. Les utilisateurs ayant besoin d’un accès à la machine avec des privilèges élevés mais pas illimités pour effectuer des tâches d’administration peuvent recevoir l’accès au point de terminaison JEA. Comme JEA les autorise à exécuter des commandes d’administration sans disposer d’un accès d’administration complet, vous pouvez supprimer ces utilisateurs de groupes de sécurité disposant de privilèges élevés.

## <a name="run-as-account"></a>Compte d’identification

Chaque point de terminaison JEA a un compte **d’identification** désigné. Il s’agit du compte sous lequel les actions de l’utilisateur connecté sont exécutées. Ce compte est configurable dans le [fichier de configuration de session](session-configurations.md), et le compte que vous choisissez a une incidence considérable sur la sécurité de votre point de terminaison.

Les **comptes virtuels** sont la méthode recommandée pour la configuration du compte **d’identification**. Les comptes virtuels sont des comptes locaux à usage unique temporaires, qui sont créés pour l’utilisateur qui se connecte à utiliser pendant la durée de sa session JEA. Dès que la session est terminée, le compte virtuel est détruit et ne peut plus être utilisé. L’utilisateur connecté ne connaît pas les informations d’identification pour le compte virtuel. Le compte virtuel ne peut pas être utilisé pour accéder au système par d’autres moyens, comme Bureau à distance ou un point de terminaison PowerShell sans contrainte.

Par défaut, les comptes virtuels appartiennent au groupe **Administrateurs** local sur la machine. Ainsi, ils disposent des droits complets pour gérer n’importe quel élément sur le système, mais pas de droits pour gérer les ressources sur le réseau.
Lors de l’authentification auprès d’autres machines, le contexte de l’utilisateur est celui du compte d’ordinateur local, et non pas celui du compte virtuel.

Les contrôleurs de domaine constituent un cas particulier dans la mesure où il n’y a pas de groupe **Administrateurs** local. Au lieu de cela, les comptes virtuels appartiennent à **Administrateurs du domaine** et peuvent gérer les services d’annuaire sur le contrôleur de domaine. L’identité du domaine reste limitée à une utilisation sur le contrôleur de domaine où la session JEA a été instanciée. Les accès réseau paraissent à la place provenir de l’objet ordinateur du contrôleur de domaine.

Dans les deux cas, vous pouvez définir explicitement les groupes de sécurité auxquels le compte virtuel appartient. Il s’agit d’une bonne pratique quand la tâche peut être effectuée sans privilèges d’administrateur local ou de domaine. Si vous disposez déjà d’un groupe de sécurité défini pour vos administrateurs, accordez l’appartenance au compte virtuel à ce groupe. L’appartenance des comptes virtuels à des groupes est limitée à des groupes de sécurité locaux sur la station de travail et les serveurs membres. Sur les contrôleurs de domaine, les comptes virtuels doivent être membres des groupes de sécurité du domaine.
Une fois que le compte virtuel a été ajouté à un ou plusieurs groupes de sécurité, il n’appartient plus aux groupes par défaut (Administrateurs locaux ou du domaine).

Le tableau suivant récapitule les options de configuration possibles et les autorisations qui en résultent pour les comptes virtuels :

|        Type d’ordinateur         | Configuration du groupe du compte virtuel |                   Contexte de l’utilisateur local                    | Contexte de l’utilisateur réseau |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| Contrôleur de domaine            | Par défaut                             | Utilisateur de domaine, membre de « *DOMAIN*\Domain Admins »         | Compte d'ordinateur     |
| Contrôleur de domaine            | Groupes de domaine A et B               | Utilisateur de domaine, membre de « *DOMAIN*\A », « *DOMAIN*\B »       | Compte d'ordinateur     |
| Serveur membre ou station de travail | Par défaut                             | Utilisateur local, membre de « *BUILTIN*\Administrators »        | Compte d'ordinateur     |
| Serveur membre ou station de travail | Groupes locaux C et D                | Utilisateur local, le membre de« *COMPUTER*\C » et « *COMPUTER*\D » | Compte d'ordinateur     |

Quand vous examinez les événements d’audit de sécurité et les journaux des événements d’applications, vous voyez que chaque session d’utilisateur JEA a un compte virtuel unique. Ce compte unique vous permet de retracer les actions de l’utilisateur dans un point de terminaison JEA jusqu’à l’utilisateur d’origine qui a exécuté la commande. Les noms de compte virtuel sont au format `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>`. Par exemple, si l’utilisateur **Alice** dans le domaine **Contoso** redémarre un service dans un point de terminaison JEA, le nom d’utilisateur associé à des événements du Gestionnaire de contrôle des services est `WinRM Virtual Users\WinRM_VA_1_contoso_alice`.

Les **comptes de service gérés de groupe (GMSA)** sont pratiques quand un serveur membre doit avoir accès à des ressources réseau dans la session JEA. Par exemple, quand un point de terminaison JEA est utilisé pour contrôler l’accès à un service d’API REST hébergé sur une autre machine. Il est facile d’écrire des fonctions pour appeler les API REST, mais vous avez besoin d’une identité réseau pour vous authentifier auprès de l’API. Un compte de service géré de groupe rend possible le second tronçon tout en conservant le contrôle avec lequel les ordinateurs peuvent utiliser le compte. Les autorisations effectives du gMSA sont définies par les groupes de sécurité (locaux ou de domaine) auquel appartient le compte gMSA.

Quand un point de terminaison JEA est configuré pour utiliser un compte GMSA, les actions de tous les utilisateurs JEA paraissent provenir du même compte GMSA. La seule manière de retracer des actions jusqu’à un utilisateur spécifique est d’identifier le jeu de commandes exécuté dans une transcription de session PowerShell.

Des **informations d’identification directes** sont utilisées quand vous ne spécifiez pas de compte**d’identification**. PowerShell utilise les informations d’identification de l’utilisateur connecté pour exécuter des commandes sur le serveur distant. Ceci vous oblige à accorder à l’utilisateur connecté un accès direct à des groupes d’administration privilégiés. Cette configuration n’est **pas** recommandée pour JEA. Si l’utilisateur connecté a déjà des privilèges d’administrateur, il peut éviter JEA et gérer le système par d’autres moyens sans contraintes. Pour plus d’informations, consultez la section ci-dessous sur la façon dont [JEA ne protège pas contre les administrateurs](#jea-doesnt-protect-against-admins).

Les **comptes d’identification standard** vous permettent de spécifier un compte d’utilisateur sous lequel l’ensemble de la session PowerShell s’exécute. Les configurations de session utilisant des comptes **d’identification** (avec le paramètre `-RunAsCredential`) n’ont pas connaissance de JEA. Les définitions de rôles ne fonctionnent plus comme attendu. Chaque utilisateur autorisé à accéder au point de terminaison reçoit le même rôle.

Vous ne devez pas utiliser **RunAsCredential** sur un point de terminaison JEA, car il est difficile de retracer les actions jusqu’à des utilisateurs spécifiques et en raison de l’absence de prise en charge du mappage des utilisateurs aux rôles.

## <a name="winrm-endpoint-acl"></a>Liste de contrôle d’accès de point de terminaison WinRM

Comme avec les points de terminaison de communication à distance PowerShell standard, chaque point de terminaison JEA a une liste de contrôle d’accès (ACL) distincte qui contrôle les utilisateurs pouvant s’authentifier auprès du point de terminaison JEA. S’il est mal configuré, les utilisateurs approuvés pourraient ne pas être en mesure d’accéder au point de terminaison JEA et des utilisateurs non approuvés pourraient par contre y accéder. La liste de contrôle d’accès WinRM n’affecte pas la mise en correspondance des utilisateurs aux rôles JEA. La mise en correspondance est contrôlée par le champ **RoleDefinitions** dans le fichier de configuration de session utilisé pour inscrire le point de terminaison.

Par défaut, quand un point de terminaison JEA a plusieurs capacités de rôle, la liste de contrôle d’accès WinRM est configurée pour autoriser l’accès à tous les utilisateurs mappés. Par exemple, une session JEA configurée à l’aide des commandes suivantes accorde un accès complet à `CONTOSO\JEA_Lev1` et à `CONTOSO\JEA_Lev2`.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Vous pouvez auditer les autorisations des utilisateurs avec l’applet de commande [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration).

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Pour modifier les utilisateurs disposant d’un accès, exécutez `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` pour une invite interactive ou `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` pour mettre à jour les autorisations. Les utilisateurs doivent au moins disposer de droits *Invoke* pour accéder au point de terminaison JEA.

Il est possible de créer un point de terminaison JEA qui n’associe pas un rôle défini à chaque utilisateur qui a accès. Ces utilisateurs peuvent démarrer une session JEA, mais ont accès seulement aux applets de commande par défaut. Vous pouvez auditer les autorisations utilisateur dans un point de terminaison JEA en exécutant `Get-PSSessionCapability`. Pour plus d’informations, consultez [Audit et création de rapports sur JEA](audit-and-report.md).

## <a name="least-privilege-roles"></a>Rôles avec des privilèges minimum

Quand vous concevez des rôles JEA, il est important de se rappeler que le compte virtuel et le compte de service géré de groupe exécuté en arrière-plan peut avoir un accès sans limitations à la machine locale. Les capacités de rôle JEA vous aident à limiter les commandes et les applications qui peuvent être exécutées dans ce contexte privilégié.
Les rôles incorrectement conçus peuvent autoriser des commandes dangereuses qui peuvent permettre à un utilisateur de sortir des limites JEA ou d’accéder à des informations sensibles.

Par exemple, examinez l’entrée de fonctionnalités de rôle suivante :

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Cette capacité de rôle permet aux utilisateurs d’exécuter toutes les applets de commande PowerShell avec le nom **Process** à partir du module **Microsoft.PowerShell.Management**. Les utilisateurs peuvent avoir besoin d’accéder à des applets de commande comme `Get-Process` pour voir quelles applications s’exécutent sur le système, et `Stop-Process` pour mettre fin aux applications qui ne répondent pas. Toutefois, cette entrée autorise également `Start-Process`, qui peut être utilisé pour lancer un programme arbitraire avec des autorisations d’administrateur complètes. Le programme n’a pas besoin d’être installé localement sur le système. Un utilisateur connecté peut démarrer un programme à partir d’un partage de fichiers, qui donne à l’utilisateur des privilèges d’administrateur local, exécute des programmes malveillants, etc.

Une version plus sécurisée de cette même fonctionnalité de rôle ressemblerait à la version suivante :

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Évitez d’utiliser des caractères génériques dans les capacités de rôle. Veillez à [auditer les autorisations effectives des utilisateurs ](audit-and-report.md#check-effective-rights-for-a-specific-user) de façon régulière pour comprendre les commandes accessibles aux utilisateurs.

## <a name="jea-doesnt-protect-against-admins"></a>JEA ne protège pas contre les administrateurs

Un des principes fondamentaux de JEA est de permettre à des utilisateurs non administrateurs d’effectuer certaines tâches d’administration. JEA ne protège pas contre les utilisateurs qui ont déjà des privilèges d’administrateur. Les utilisateurs qui appartiennent au groupe **Admins du domaine**, au groupe **Administrateurs** local ou à d’autres groupes disposant de privilèges élevés peuvent contourner les protections de JEA par d’autres moyens. Par exemple, ils pourraient se connecter avec RDP, utiliser des consoles MMC distantes ou se connecter à des points de terminaison PowerShell sans contraintes. De même, les administrateurs locaux sur un système peuvent modifier les configurations de JEA pour autoriser d’autres utilisateurs ou modifier une capacité de rôle de façon à agrandir l’étendue de ce qu’un utilisateur peut faire dans sa session JEA. Il est important d’évaluer les autorisations étendues de vos utilisateurs JEA pour voir s’ils peuvent obtenir un accès privilégié au système d’une autre manière.

Une pratique courante consiste à utiliser JEA pour une maintenance régulière quotidienne, et à avoir une solution de gestion des accès privilégiés juste-à-temps qui permet aux utilisateurs de devenir temporairement des administrateurs locaux en cas d’urgence. Ainsi, les utilisateurs ne sont pas des administrateurs de manière permanente sur le système, mais ils peuvent obtenir ces droits si et seulement si un workflow documente leur utilisation de ces autorisations.
