---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Considérations de sécurité JEA
ms.openlocfilehash: 9526e141517601ae3b6d6932cd3536fdf49aa9a6
ms.sourcegitcommit: 10c347a8c3dcbf8962295601834f5ba85342a87b
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55887597"
---
# <a name="jea-security-considerations"></a>Considérations de sécurité JEA

> S'applique à : Windows PowerShell 5.0

JEA vous aide à améliorer votre sécurité en réduisant le nombre d’administrateurs permanents sur vos machines.
Il le fait en créant un nouveau point d’entrée pour les utilisateurs leur permettant de gérer le système (une configuration de session PowerShell), qui est étroitement verrouillé par défaut pour empêcher toute utilisation malveillante.
Les utilisateurs ayant besoin d’un accès non forcément illimité à la machine pour effectuer des tâches d’administration peuvent avoir accès au point de terminaison JEA.
JEA les autorisant à exécuter des commandes d’administration sans disposer directement d’un accès administrateur, vous pouvez ensuite supprimer des utilisateurs de groupes de sécurité disposant de privilèges élevés (en les rendant utilisateurs standard).

Cette rubrique décrit le modèle de sécurité JEA et les bonnes pratiques en détail.

## <a name="run-as-account"></a>compte d'identification

Chaque point de terminaison JEA possède un compte d’identification désigné, qui est le compte sous lequel sont effectuées les actions de l’utilisateur qui se connecte.
Ce compte est configurable dans le [fichier de configuration de session](session-configurations.md), et le compte que vous choisissez a une incidence considérable sur la sécurité de votre point de terminaison.

**Les comptes virtuels** sont la méthode recommandée de configuration du compte d’identification.
Les comptes virtuels sont des comptes locaux à usage unique temporaires, qui sont créés pour l’utilisateur qui se connecte à utiliser pendant la durée de sa session JEA.
Dès que la session est terminée, le compte virtuel est détruit et ne peut plus être utilisé.
L’utilisateur qui se connecte ne connaît pas les informations d’identification pour le compte virtuel et ne peut pas utiliser le compte virtuel pour accéder au système par d’autres moyens, notamment le Bureau à distance ou un point de terminaison PowerShell sans contrainte.

Par défaut, les comptes virtuels appartiennent au groupe Administrateurs local sur la machine.
Ainsi, ils disposent des droits complets pour gérer n’importe quel élément sur le système, mais pas de droits pour gérer les ressources sur le réseau.
Lors de l’authentification sur d’autres machines, le contexte de l’utilisateur est celui du compte d’ordinateur local, pas le compte virtuel.

Les contrôleurs de domaine constituent un cas particulier, car il n’existe aucun concept de groupe d’administrateurs locaux.
Au lieu de cela, les comptes virtuels appartiennent aux Administrateurs du domaine et peuvent gérer les services d’annuaire sur le contrôleur de domaine.
L’identité du domaine est toujours limitée à une utilisation sur le contrôleur de domaine où la session JEA a été instanciée, et tout accès au réseau semblera provenir de l’objet ordinateur de contrôleur de domaine.

Dans les deux cas, vous pouvez également définir explicitement les groupes de sécurité auxquels le compte virtuel doit appartenir.
Il s’agit d’une bonne pratique si la tâche que vous effectuez peut être réalisée sans privilèges d’administrateur local ou de domaine.
Si vous disposez déjà d’un groupe de sécurité défini pour vos administrateurs, vous pouvez simplement accorder l’appartenance au compte virtuel à ce groupe afin de lui donner les autorisations dont il a besoin.
L’appartenance au groupe de compte virtuel est limitée aux groupes de sécurité locaux sur la station de travail et les serveurs membres, mais il ne peut s’agir que de membres de groupes de sécurité de domaine sur un contrôleur de domaine.
Une fois que vous spécifiez un ou plusieurs groupes de sécurité auquel le compte virtuel doit appartenir, ils n’appartiennent plus aux groupes par défaut (administrateur local ou administrateur de domaine).

Le tableau ci-dessous résume les options de configuration possibles et les autorisations qui en résultent pour les comptes virtuels

Type d’ordinateur                | Configuration du groupe du compte virtuel | Contexte de l’utilisateur local                                      | Contexte de l’utilisateur réseau
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
Contrôleur de domaine            | Par défaut                             | Utilisateur de domaine, membre de « *DOMAIN*\Domain Admins »         | Compte d'ordinateur
Contrôleur de domaine            | Groupes de domaine A et B               | Utilisateur de domaine, membre de « *DOMAIN*\A », « *DOMAIN*\B »       | Compte d'ordinateur
Serveur membre ou station de travail | Par défaut                             | Utilisateur local, membre de « *BUILTIN*\Administrators »        | Compte d'ordinateur
Serveur membre ou station de travail | Groupes locaux C et D                | Utilisateur local, le membre de« *COMPUTER*\C » et « *COMPUTER*\D » | Compte d'ordinateur

Lorsque vous examinez les événements d’audit de sécurité et les journaux des événements de l’application, vous voyez que chaque session d’utilisateur JEA a un compte virtuel unique.
Cela vous permet de suivre les actions de l’utilisateur dans un point de terminaison JEA jusqu’à l’utilisateur d’origine qui a exécuté la commande.
Les noms de compte virtuel sont au format « Utilisateurs virtuels WinRM \\WinRM\_VA\_*ACCOUNTNUMBER*\_*DOMAINE*\_*sAMAccountName* ». Par exemple, si l’utilisateur « Alice » dans le domaine « Contoso » redémarre un service dans un point de terminaison JEA, le nom d’utilisateur associé à des événements du Gestionnaire de contrôle des services est « Utilisateurs virtuels WinRM\\WinRM\_VA\_1\_contoso\_alice ».


Les **comptes de service administrés de groupe (gMSA)** sont utiles lorsqu’un serveur membre doit avoir accès aux ressources réseau dans la session JEA.
Un exemple de cas d’utilisation est un point de terminaison JEA utilisé pour contrôler l’accès à une API REST hébergée sur une autre machine.
Il est facile d’écrire des fonctions pour effectuer les appels souhaités de l’API REST, mais vous avez besoin d’une identité réseau pour vous authentifier auprès de l’API.
Un compte de service administré de groupe rend possible le « second tronçon » tout en conservant le contrôle avec lequel les ordinateurs peuvent utiliser le compte.
Les autorisations effectives du gMSA sont définies par les groupes de sécurité (locaux ou de domaine) auquel appartient le compte gMSA.

Lorsqu’un point de terminaison JEA est configuré pour utiliser un compte gMSA, les actions de tous les utilisateurs JEA semblent provenir du même compte de service administré de groupe.
La seule manière de tracer des actions jusqu’à un utilisateur spécifique consiste à identifier le jeu de commandes exécuté dans une transcription de session PowerShell.

Les **informations d’identification de relais** sont utilisées lorsque vous ne spécifiez pas une exécution en tant que compte et que vous voulez que PowerShell utilise les informations d’identification de connexion de l’utilisateur pour exécuter des commandes sur le serveur distant.
Cette configuration n’est *pas* recommandée pour JEA, car elle vous oblige à accorder un accès direct à l’utilisateur qui se connecte à des groupes d’administration privilégiés.
Si l’utilisateur connecté possède déjà des privilèges d’administrateur, il peut éviter JEA et gérer le système par d’autres moyens sans contrainte.
Consultez la section ci-dessous pour en savoir plus et découvrir comment [JEA ne protège pas contre les administrateurs](#jea-does-not-protect-against-admins).

**L’exécution standard en tant que comptes** vous permet de spécifier un compte d’utilisateur quelconque sous lequel l’ensemble de la session PowerShell est exécuté.
Cette distinction est importante, car une configuration de session définie avec une exécution fixe de compte (avec le paramètre `-RunAsCredential`) ne prend pas JEA en charge.
Cela signifie que les définitions de rôles ne fonctionnent plus comme prévu, et que chaque utilisateur autorisé à accéder au point de terminaison se voit attribuer le même rôle.

Vous ne devez pas utiliser un RunAsCredential sur un point de terminaison JEA en raison de la difficulté de suivi des actions à des utilisateurs spécifiques et l’absence de prise en charge pour le mappage des utilisateurs aux rôles.

## <a name="winrm-endpoint-acl"></a>Liste de contrôle d’accès de point de terminaison WinRM

Comme avec des points de terminaison PowerShell à distance standard, chaque point de terminaison JEA a une liste de contrôle d’accès (ACL) distincte définie dans la configuration de WinRM qui contrôle les utilisateurs pouvant s’authentifier auprès du point de terminaison JEA.
S’il est mal configuré, les utilisateurs approuvés ne peuvent pas accéder au point de terminaison JEA et/ou des utilisateurs non approuvés peuvent y accéder.
Toutefois, la liste de contrôle d’accès WinRM n’affecte pas le mappage des utilisateurs sur les rôles JEA.
Ce dernier est contrôlé par le champ *RoleDefinitions* dans le fichier de configuration de session qui a été inscrit sur le système.

Par défaut, lorsque vous inscrivez un point de terminaison JEA à l’aide d’un fichier de configuration de session et une ou plusieurs fonctions de rôle, la liste de contrôle d’accès WinRM est configurée de manière à autoriser tous les utilisateurs mappés sur un ou plusieurs rôles à accéder au point de terminaison.
Par exemple, une session JEA configurée à l’aide des commandes suivantes accorde un accès complet à *CONTOSO\JEA\_Lev1* et à *CONTOSO\JEA\_Lev2*.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Vous pouvez auditer les autorisations des utilisateurs avec l’applet de commande [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration).

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Pour modifier les utilisateurs disposant d’un accès, exécutez `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` pour une invite interactive ou `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` pour mettre à jour les autorisations.
Les utilisateurs doivent au moins disposer de droits *Invoke* pour accéder au point de terminaison JEA.

Si des utilisateurs ont accès au point de terminaison JEA mais n’appartiennent à aucun des rôles définis dans le fichier de configuration de session, ils seront en mesure de démarrer une session JEA mais auront uniquement accès aux applets de commande par défaut.
Vous pouvez auditer les autorisations utilisateur dans un point de terminaison JEA en exécutant `Get-PSSessionCapability`.
Lisez l’article [Audit et rapports dans JEA](audit-and-report.md) pour plus d’informations sur l’audit des commandes auxquelles un utilisateur a accès dans un point de terminaison JEA.

## <a name="least-privilege-roles"></a>Rôles avec des privilèges minimum

Lorsque vous concevez des rôles JEA, il est important de se rappeler que le compte virtuel ou le compte de service administré de groupe exécuté en arrière-plan a souvent un accès illimité pour gérer la machine locale.
Les fonctionnalités de rôles JEA permettent de restreindre les possibilités d’utilisation de ce compte en limitant les commandes et les applications qui peuvent être exécutées à l’aide de ce contexte privilégié.
Les rôles incorrectement conçus peuvent autoriser l’exécution de commandes dangereuses qui peuvent autoriser un utilisateur à sortir des limites JEA ou à accéder à des informations sensibles.

Par exemple, examinez l’entrée de fonctionnalités de rôle suivante :

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Cette fonctionnalité de rôle permet aux utilisateurs d’exécuter une applet de commande PowerShell quelconque avec le nom « Process » à partir du module Microsoft.PowerShell.Management.
Les utilisateurs devront peut-être accéder aux applets de commande comme `Get-Process` pour comprendre quelles applications s’exécutent sur le système et `Stop-Process` pour mettre fin à toutes les applications qui ne répondent pas.
Toutefois, cette entrée autorise également `Start-Process`, qui peut être utilisé pour lancer un programme arbitraire avec des autorisations d’administrateur complètes.
Le programme n’a pas besoin d’être installé localement sur le système. Un adversaire pourrait donc lancer simplement un programme sur un partage de fichiers qui donne les privilèges d’administrateur local à l’utilisateur qui se connecte, exécute un logiciel malveillant et bien plus encore.

Une version plus sécurisée de cette même fonctionnalité de rôle ressemblerait à la version suivante :

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Évitez d’utiliser des caractères génériques dans les fonctionnalités de rôle et veillez à [auditer les autorisations d’utilisateur effectives](audit-and-report.md#check-effective-rights-for-a-specific-user) régulièrement afin de comprendre les commandes auxquelles un utilisateur a accès.

## <a name="jea-does-not-protect-against-admins"></a>JEA ne protège pas contre les administrateurs

L’un des principes fondamentaux de JEA est de permettre à des utilisateurs non administrateurs d’effectuer *certaines* tâches d’administration.
JEA ne protège pas contre les utilisateurs qui ont déjà des privilèges d’administrateur.
Les utilisateurs qui appartiennent aux groupes « Admins du domaine », « Administrateurs locaux » ou à d’autres groupes disposant de privilèges élevés dans votre environnement seront toujours en mesure de contourner les protections de JEA en se connectant à l’ordinateur par d’autres moyens.
Ils pourraient, par exemple, se connecter à l’aide de RDP, utiliser des consoles MMC distantes ou se connecter à des points de terminaison PowerShell sans contrainte.
Les administrateurs locaux sur le système peuvent également modifier les configurations JEA pour autoriser des utilisateurs supplémentaires à gérer le système ou à modifier une capacité de rôle de manière à étendre l’étendue de ce qu’un utilisateur peut faire dans sa session JEA.
Il est donc important d’évaluer les autorisations étendues de vos utilisateurs JEA pour voir s’ils peuvent obtenir un accès privilégié au système d’une autre manière.

Une pratique courante consiste à utiliser JEA pour une maintenance régulière quotidienne et à avoir une solution de gestion d’accès privilégiée « just in time » (juste à temps) pour autoriser les utilisateurs à devenir temporairement des administrateurs locaux en cas d’urgence.
Ainsi, les utilisateurs ne sont pas des administrateurs de manière permanente sur le système, mais ils peuvent obtenir ces droits si et seulement si un workflow documente leur utilisation de ces autorisations.