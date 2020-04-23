---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Configuration de session JEA
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "70017730"
---
# <a name="jea-session-configurations"></a>Configuration de session JEA

Un point de terminaison JEA est inscrit sur un système en créant et en inscrivant un fichier de configuration de session PowerShell. Les configurations de session définissent qui peut utiliser le point de terminaison JEA et à quels rôles il a accès. Elles définissent également les paramètres globaux qui s’appliquent à tous les utilisateurs de la session JEA.

## <a name="create-a-session-configuration-file"></a>Créer un fichier de configuration de session

Pour inscrire un point de terminaison JEA, vous devez spécifier la façon dont ce point de terminaison est configuré. Il y a de nombreuses options à considérer. Les options les plus importantes sont :

- Qui a accès au point de terminaison JEA
- Quels rôles leur sont affectés
- Quelle identité JEA utilise en arrière-plan
- Le nom du point de terminaison JEA

Ces options sont définies dans un fichier de données PowerShell avec une extension `.pssc`, désignée sous le nom de « fichier de configuration de session PowerShell ». Vous pouvez modifier le fichier de configuration de session avec n’importe quel éditeur de texte.

Exécutez la commande suivante pour créer un modèle de fichier de configuration vide.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Seules les options de configuration les plus courantes sont incluses dans le modèle de fichier par défaut. Utilisez le commutateur `-Full` pour inclure tous les paramètres applicables dans le fichier PSSC généré.

Le champ `-SessionType RestrictedRemoteServer` indique que la configuration de session est utilisée par JEA pour la gestion sécurisée. Les sessions de ce type fonctionnent en **mode NoLanguage** et ont accès seulement aux commandes (et à leur alias) par défaut suivantes :

- Clear-Host (cls, clear)
- Exit-PSSession (exsn, exit)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Measure-Object (measure)
- Out-Default
- Select-Object (select)

Aucun fournisseur PowerShell ni aucun programme externe (exécutables, scripts, etc.) ne sont disponibles.

Pour plus d’informations sur les modes de langage, consultez [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).

### <a name="choose-the-jea-identity"></a>Choisir l’identité JEA

En coulisses, JEA a besoin d’une identité (compte) pour exécuter les commandes d’un utilisateur connecté.
Vous définissez quelle identité JEA utilise dans le fichier de configuration de session.

#### <a name="local-virtual-account"></a>Compte virtuel local

Les comptes virtuels locaux sont pratiques quand tous les rôles définis pour le point de terminaison JEA sont utilisés pour gérer la machine locale et qu’un compte d’administrateur local est suffisant pour exécuter les commandes avec succès.
Les comptes virtuels sont des comptes temporaires propres à un utilisateur spécifique, qui ne durent que le temps de sa session PowerShell. Sur une station de travail ou un serveur membre, les comptes virtuels appartiennent au groupe **Administrateurs** de l’ordinateur local. Sur un contrôleur de domaine Active Directory, les comptes virtuels appartiennent au groupe **Administrateurs du domaine**.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Si les rôles définis par la configuration de session ne nécessitent pas de privilèges d’administration complets, vous pouvez spécifier les groupes de sécurité auxquels appartiendra le compte virtuel. Sur une station de travail ou un serveur membre, les groupes de sécurité spécifiés doivent être des groupes locaux, et non les groupes d’un domaine.

Quand un ou plusieurs groupes de sécurité sont spécifiés, le compte virtuel n’est pas affecté au groupe Administrateurs local ou du domaine.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> Le droit « Se connecter en tant que service » est accordé temporairement aux comptes virtuels dans la stratégie de sécurité du serveur local. Si l’un des VirtualAccountGroups spécifiés dans la stratégie a déjà reçu ce droit, le compte virtuel en question ne sera plus ajouté et supprimé de la stratégie. Cela peut être utile dans les scénarios tels que ceux où les révisions de la stratégie de sécurité de contrôleur de domaine sont étroitement auditées. Cette fonctionnalité est disponible uniquement dans Windows Server 2016 avec le correctif cumulatif de novembre 2018 ou plus récent, et Windows Server 2019 avec le correctif cumulatif de janvier 2019 ou plus récent.

#### <a name="group-managed-service-account"></a>Compte de service géré de groupe

Un compte de service géré de groupe (GMSA, Group-Managed Service Account) est l’identité appropriée à utiliser quand les utilisateurs JEA doivent accéder à des ressources réseau, comme des partages de fichiers et des services web. Les comptes GMSA vous donnent une identité de domaine qui est utilisée pour s’authentifier auprès de ressources sur n’importe quelle machine du domaine. Les droits fournis par un compte GMSA sont déterminés par les ressources auxquelles vous accédez. Vous ne disposez pas de droits d’administrateur sur des machines ou des services, sauf si l’administrateur de la machine ou du service a accordé explicitement ces droits au compte GMSA.

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

Les comptes GMSA doivent être utilisés seulement quand c’est nécessaire :

- Il est difficile de retracer les actions jusqu’à un utilisateur s’il utilise un compte GMSA. Tous les utilisateurs partagent la même identité d’identification. Vous devez examiner les journaux et les transcriptions de sessions PowerShell pour mettre en corrélation les utilisateurs individuels et leurs actions.

- Le compte GMSA peut avoir accès à de nombreuses ressources réseau auxquelles l’utilisateur connecté n’a pas besoin d’accéder. Essayez toujours de limiter les autorisations effectives dans une session JEA en suivant le principe des privilèges minimum.

> [!NOTE]
> Les comptes GMSA sont disponibles seulement sur les machines jointes à un domaine avec PowerShell 5.1 ou ultérieur.

Pour plus d’informations sur la sécurisation d’une session JEA, consultez l’article [Considérations sur la sécurité](security-considerations.md).

### <a name="session-transcripts"></a>Transcription de sessions

Il est recommandé de configurer un point de terminaison JEA de manière à enregistrer automatiquement les transcriptions des sessions des utilisateurs. Les transcriptions de sessions PowerShell contiennent des informations sur l’utilisateur connecté, l’identité « Exécuter en tant que » affectée et les commandes exécutées par l’utilisateur. Elles peuvent être utiles à une équipe d’audit qui a besoin de comprendre qui a apporté une modification spécifique à un système.

Pour configurer la transcription automatique dans le fichier de configuration de session, fournissez le chemin d’accès du dossier dans lequel les transcriptions devront être stockées.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Les transcriptions sont écrites dans le dossier par le compte **Système local**, qui nécessite un accès en lecture et en écriture au répertoire. Les utilisateurs standard ne doivent pas avoir accès au dossier. Limitez le nombre d’administrateurs de sécurité qui ont un accès permettant d’auditer les transcriptions.

### <a name="user-drive"></a>Lecteur utilisateur

Si vos utilisateurs connectés ont besoin de copier des fichiers vers ou depuis le point de terminaison JEA, vous pouvez activer le lecteur utilisateur dans le fichier de configuration de session. Le lecteur utilisateur est un **PSDrive** mappé à un dossier unique pour chaque utilisateur connecté. Ce dossier permet aux utilisateurs de copier des fichiers vers ou depuis le système, sans qu’ils puissent accéder à la totalité du système de fichiers ou exposer le fournisseur du système de fichiers. Le contenu du lecteur utilisateur est persistant d’une session à l’autre de façon à gérer les situations dans lesquelles la connectivité réseau risque d’être interrompue.

```powershell
MountUserDrive = $true
```

Par défaut, le lecteur utilisateur vous permet de stocker 50 Mo de données maximum par utilisateur. Vous pouvez limiter la quantité de données qu’un utilisateur peut consommer avec le champ *UserDriveMaximumSize*.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Si vous ne voulez pas que les données du lecteur utilisateur soient persistantes, vous pouvez configurer une tâche planifiée sur le système qui nettoie automatiquement le dossier toutes les nuits.

> [!NOTE]
> Le lecteur utilisateur est disponible seulement dans PowerShell 5.1 et ultérieur.

Pour plus d’informations sur PSDrives, consultez [Gestion des disques PowerShell](/powershell/scripting/samples/managing-windows-powershell-drives).

### <a name="role-definitions"></a>Définitions de rôles

Les définitions de rôles d’un fichier de configuration de session définissent le mappage des **utilisateurs** aux **rôles**. Chaque utilisateur ou groupe de ce champ reçoit l’autorisation d’accès au point de terminaison JEA lors de son inscription.
Chaque utilisateur ou groupe ne peut être inclus qu’une seule fois en tant que clé de la table de hachage, mais plusieurs rôles peuvent lui être affectés. Le nom de la capacité du rôle doit être le même que celui du fichier des capacités des rôles, sans l’extension `.psrc`.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Si un utilisateur appartient à plusieurs groupes dans la définition des rôles, il a accès aux rôles de chacun de ces groupes. Quand deux rôles accordent l’accès aux mêmes applets de commande, l’ensemble de paramètres le plus permissif est accordé à l’utilisateur.

Quand vous spécifiez des utilisateurs ou des groupes locaux dans le champ des définitions de rôle, veillez à utiliser le nom de l’ordinateur, et non pas **localhost** ou des caractères génériques. Pour vérifier le nom de l’ordinateur, inspectez la variable `$env:COMPUTERNAME`.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Ordre de recherche des capacités de rôle

Comme le montre l’exemple ci-dessus, les capacités de rôle sont référencées par le nom de base du fichier des capacités de rôle. Le nom de base d’un fichier est le nom de fichier sans l’extension. Si plusieurs capacités de rôle sont disponibles sur le système avec le même nom, PowerShell utilise son ordre de recherche implicite pour sélectionner le fichier effectif de capacités de rôle. JEA ne donne **pas** accès à tous les fichiers de capacités de rôle portant le même nom.

JEA utilise la variable d’environnement `$env:PSModulePath` pour déterminer les chemins d’accès à analyser pour rechercher les fichiers de capacités de rôle. Dans chacun de ces chemins, JEA recherche les modules PowerShell valides contenant un sous-dossier « RoleCapabilities ». Tout comme pour l’importation de modules, JEA préfère les capacités de rôle qui sont livrées avec Windows aux capacités de rôle personnalisées portant le même nom.

Pour tous les autres conflits de noms, la priorité est déterminée par l’ordre dans lequel Windows énumère les fichiers dans le répertoire. Il n’est pas garanti que l’ordre soit alphabétique. Le premier fichier de capacités de rôle trouvé qui correspond au nom spécifié est utilisé pour l’utilisateur qui se connecte. Comme la recherche des capacités de rôle n’est pas déterministe, il est **fortement recommandé** d’utiliser des noms de fichier uniques pour les capacités de rôle.

### <a name="conditional-access-rules"></a>Règles d’accès conditionnel

Tous les utilisateurs et groupes inclus dans le champ **RoleDefinitions** reçoivent automatiquement l’accès aux points de terminaison JEA. Les règles d’accès conditionnel vous permettent d’affiner cet accès et d’exiger que les utilisateurs appartiennent à d’autres groupes de sécurité qui n’affectent pas les rôles qui leur sont attribués. C’est utile quand vous voulez intégrer une solution de gestion des accès privilégiés en « juste à temps », l’authentification par carte à puce ou une autre solution d’authentification multifacteur avec JEA.

Les règles d’accès conditionnel sont définies dans le champ RequiredGroups d’un fichier de configuration de session.
Vous pouvez y spécifier une table de hachage (éventuellement imbriquée) qui utilise des clés « And » et « Or » pour créer vos règles. Voici quelques exemples d’utilisation de ce champ :

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> Les règles d’accès conditionnel sont disponibles seulement dans PowerShell 5.1 ou ultérieur.

### <a name="other-properties"></a>Autres propriétés

Les fichiers de configuration de session peuvent également faire les mêmes choses qu’un fichier de capacités de rôle, sauf donner accès aux utilisateurs connectés à des commandes différentes. Si vous souhaitez autoriser tous les utilisateurs à accéder à des applets de commande, fonctions ou fournisseurs spécifiques, vous pouvez le faire directement dans le fichier de configuration de session.
Pour obtenir la liste complète des propriétés prises en charge dans le fichier de configuration de session, exécutez `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Tester un fichier de configuration de session

Vous pouvez tester une configuration de session avec l’applet de commande [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile). Il est recommandé de tester votre fichier de configuration de session si vous avez modifié manuellement le fichier `.pssc`. Les tests garantissent que la syntaxe est correcte. Si un fichier de configuration de session échoue à ce test, il ne peut pas être inscrit sur le système.

## <a name="sample-session-configuration-file"></a>Exemple de fichier de configuration de session

L’exemple suivant montre comment créer et valider une configuration de session pour JEA. Les définitions de rôles sont créées et stockées dans la variable `$roles` par souci pratique et de lisibilité. Il n’y a pas d’obligation à procéder ainsi.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>Mettre à jour les fichiers de configuration de session

Pour changer les propriétés d’une configuration de session JEA, notamment la mise en correspondance des utilisateurs aux rôles, vous devez effectuer une [désinscription](register-jea.md#unregistering-jea-configurations). Ensuite, vous devez [réinscrire](register-jea.md) la configuration de session JEA avec le fichier de configuration de session mis à jour.

## <a name="next-steps"></a>Étapes suivantes

- [Enregistrer une configuration JEA](register-jea.md)
- [Créer des rôles JEA](role-capabilities.md)
