---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Configuration de session JEA
ms.openlocfilehash: bdf3659357045203d90e8083613e51cce657da1a
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522952"
---
# <a name="jea-session-configurations"></a>Configuration de session JEA

> S’applique à : Windows PowerShell 5.0

Un point de terminaison JEA est enregistré sur un système en créant et en enregistrant un fichier de configuration de session PowerShell de manière spécifique.
Les configurations de session déterminent *qui* peut utiliser le point de terminaison JEA, et à quel(s) rôle(s) ils ont accès.
Elles définissent également les paramètres globaux qui s’appliquent aux utilisateurs des rôles de la session JEA.

Cette rubrique décrit comment créer un fichier de configuration de session PowerShell et enregistrer un point de terminaison JEA.

## <a name="create-a-session-configuration-file"></a>Créer un fichier de configuration de session

Pour enregistrer un point de terminaison JEA, vous devez spécifier la façon dont ce point de terminaison doit être configuré.
De nombreuses options sont à prendre en compte ici, voici les plus importantes : qui doit avoir accès au point de terminaison JEA, quels rôles leur seront affectés, quelles identités JEA utilisera en coulisses et quel sera le nom du point de terminaison JEA.
Elles sont toutes définies dans un fichier de configuration de session PowerShell, qui est un fichier de données PowerShell se terminant par une extension .pssc.

Pour créer un squelette de fichier de configuration de session pour les points de terminaison JEA, exécutez la commande suivante.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Seules les options de configuration les plus courantes sont incluses dans le squelette de fichier par défaut.
> Utilisez le commutateur `-Full` pour inclure tous les paramètres applicables dans le fichier PSSC généré.

Vous pouvez ouvrir le fichier de configuration de session dans l’éditeur de texte de votre choix.
Le champ `-SessionType RestrictedRemoteServer` indique que la configuration de session sera utilisée par JEA pour une gestion sécurisée.
Les sessions configurées de cette façon fonctionnent en [mode NoLanguage](https://technet.microsoft.com/library/dn433292.aspx) et seules les huit commandes par défaut suivantes (et les alias) sont disponibles :

- Clear-Host (cls, clear)
- Exit-PSSession (exsn, exit)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Measure-Object (measure)
- Out-Default
- Select-Object (select)

Aucun fournisseur PowerShell n’est disponible, ni aucun programme externe (exécutables, scripts, etc.).

Il vous faudra configurer d’autres champs pour la session JEA.
Ils sont décrits dans les sections suivantes.

### <a name="choose-the-jea-identity"></a>Choisir l’identité JEA

En coulisses, JEA a besoin d’une identité (compte) pour exécuter les commandes d’un utilisateur connecté.
Vous choisissez quelle identité JEA utilisera dans le fichier de configuration de session.

#### <a name="local-virtual-account"></a>Compte virtuel local

Si les rôles pris en charge par ce point de terminaison JEA sont tous utilisés pour gérer l’ordinateur local, et qu’un compte Administrateur local est suffisant pour exécuter les commandes, vous devez configurer JEA afin d’utiliser un compte virtuel local.
Les comptes virtuels sont des comptes temporaires propres à un utilisateur spécifique, qui ne durent que le temps de sa session PowerShell.
Sur une station de travail ou un serveur membre, les comptes virtuels appartiennent au groupe **Administrateurs** de l’ordinateur local, et ont accès à la plupart des ressources système.
Sur un contrôleur de domaine Active Directory, les comptes virtuels appartiennent au groupe **Administrateurs du domaine**.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Si les rôles pris en charge par la configuration de session ne requièrent pas ces privilèges étendus, vous pouvez éventuellement spécifier les groupes de sécurité auxquels appartiendra le compte virtuel.
Sur une station de travail ou un serveur membre, les groupes de sécurité spécifiés doivent être des groupes locaux, et non les groupes d’un domaine.

Lorsqu’un ou plusieurs groupes de sécurité sont spécifiés, le compte virtuel n’appartient plus au groupe Administrateurs local ou du domaine.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a>Compte de service administré de groupe


Pour les scénarios exigeant que l’utilisateur JEA accède à des ressources réseau telles que d’autres ordinateurs ou services web, un compte de service géré par un groupe (gMSA) est une identité plus appropriée.
Les comptes gMSA donnent une identité de domaine utilisable pour s’authentifier auprès des ressources de n’importe quel ordinateur du domaine.
Les droits que le compte gMSA vous donne sont déterminés par les ressources auxquelles vous accédez.
Vous ne disposez pas automatiquement de droits d’administrateur sur les ordinateurs ou les services, sauf si l’administrateur du service/de l’ordinateur a accordé explicitement les privilèges Administrateur au compte gMSA.

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

Les comptes gMSA ne doivent être utilisés que lorsque l’accès aux ressources réseau est requis, pour plusieurs raisons :

- Il est plus difficile de retracer les actions d’un utilisateur avec un compte gMSA, étant donné que tous les utilisateurs partagent la même identité « Exécuter en tant que ». Vous devrez consulter les journaux et les transcriptions de sessions PowerShell pour mettre en corrélation les utilisateurs et leurs actions.

- Le compte gMSA peut avoir accès à de nombreuses ressources réseau auxquelles l’utilisateur connecté n’a pas accès. Essayez toujours de limiter les autorisations effectives dans une session JEA en suivant le principe des privilèges minimum.

> [!NOTE]
> Les comptes de service gérés par un groupe sont disponibles uniquement dans Windows PowerShell 5.1 et les versions plus récentes, et sur les ordinateurs joints à un domaine.


#### <a name="more-information-about-run-as-users"></a>Informations complémentaires sur les utilisateurs « Exécuter en tant que »

Vous trouverez plus d’informations sur les identités « Exécuter en tant que » et sur leur rôle dans la sécurité d’une session JEA dans l’article [considérations en matière de sécurité](security-considerations.md).

### <a name="session-transcripts"></a>Transcription de sessions

Il est recommandé de configurer un fichier de configuration de session JEA de manière à enregistrer automatiquement les transcriptions des sessions des utilisateurs.
Les transcriptions de sessions PowerShell contiennent des informations sur l’utilisateur connecté, l’identité « Exécuter en tant que » affectée et les commandes exécutées par l’utilisateur.
Elles peuvent être utiles à une équipe d’audit qui a besoin de comprendre qui a apporté une modification en particulier à un système.

Pour configurer la transcription automatique dans le fichier de configuration de session, fournissez le chemin d’accès du dossier dans lequel les transcriptions devront être stockées.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Le dossier spécifié doit être configuré de façon à empêcher les utilisateurs de modifier ou de supprimer les données qu’il contient.
Les transcriptions sont écrites dans le dossier par le compte système local, qui a besoin d’un accès en lecture et en écriture au répertoire.
Les utilisateurs standard ne doivent avoir aucun accès au dossier, et un ensemble limité d’administrateurs de sécurité doit y avoir accès pour vérifier les transcriptions.

### <a name="user-drive"></a>Lecteur utilisateur

Si vos utilisateurs connectés ont besoin de copier des fichiers vers/à partir du point de terminaison JEA afin d’exécuter une commande, vous pouvez activer le lecteur utilisateur dans le fichier de configuration de session.
Le lecteur utilisateur est un [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) mappé à un dossier unique pour chaque utilisateur connecté.
Ce dossier leur sert d’espace pour copier des fichiers vers/à partir du système, sans qu’ils puissent accéder à la totalité du système de fichiers ou exposer le fournisseur du système de fichiers.
Le contenu du lecteur utilisateur est persistant d’une session à l’autre de façon à gérer les situations dans lesquelles la connectivité réseau risque d’être interrompue.

```powershell
MountUserDrive = $true
```

Par défaut, le lecteur utilisateur vous permet de stocker 50 Mo de données maximum par utilisateur.
Vous pouvez limiter la quantité de données qu’un utilisateur peut consommer avec le champ *UserDriveMaximumSize*.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Si vous ne souhaitez pas que les données du lecteur utilisateur soient persistantes, vous pouvez configurer une tâche planifiée sur le système qui nettoie automatiquement le dossier toutes les nuits.

> [!NOTE]
> Le lecteur utilisateur est disponible uniquement dans Windows PowerShell 5.1 et les versions ultérieures.

### <a name="role-definitions"></a>Définitions de rôles

Les définitions de rôles d’un fichier de configuration de session définissent le mappage des *utilisateurs* aux *rôles*.
Chaque utilisateur ou groupe de ce champ reçoit automatiquement l’autorisation d’accès au point de terminaison JEA lors de son enregistrement.
Chaque utilisateur ou groupe ne peut être inclus qu’une seule fois en tant que clé de la table de hachage, mais plusieurs rôles peuvent lui être affectés.
Le nom de la capacité de rôle doit être le nom du fichier de capacités de rôle, sans l’extension .psrc.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Si un utilisateur appartient à plusieurs groupes de la définition des rôles, il a accès aux rôles de chacun d’entre eux.
Si deux rôles accordent l’accès aux mêmes applets de commande, l’ensemble de paramètres le plus permissif est accordé à l’utilisateur.

Quand vous spécifiez des utilisateurs ou des groupes locaux dans le champ des définitions de rôle, veillez à utiliser le nom de l’ordinateur (et non *localhost* ou  *.*) avant la barre oblique inverse.
Pour vérifier le nom de l’ordinateur, inspectez la variable `$env:computername`.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Ordre de recherche des capacités de rôle
Comme l’indique l’exemple ci-dessus, les capacités de rôle sont référencées par le nom plat (nom du fichier sans l’extension) du fichier de capacités de rôle.
Si plusieurs capacités de rôle sont disponibles sur le système avec le même nom plat, PowerShell utilise son ordre de recherche implicite pour sélectionner le fichier effectif de capacités de rôle.
Il ne donnera **pas** accès à tous les fichiers de capacités de rôle portant le même nom.

JEA utilise la variable d’environnement `$env:PSModulePath` pour déterminer les chemins d’accès à analyser pour rechercher les fichiers de capacités de rôle.
Dans chacun de ces chemins d’accès, JEA recherche les modules PowerShell valides contenant un sous-dossier « RoleCapabilities ».
Tout comme pour l’importation de modules, JEA préfère les capacités de rôle qui sont livrées avec Windows aux capacités de rôle personnalisées portant le même nom.
Pour tous les autres conflits d’affectation de noms, la priorité est déterminée par l’ordre dans lequel Windows énumère les fichiers dans le répertoire (pas forcément par ordre alphabétique).
Le premier fichier de capacités de rôle trouvé qui correspond au nom requis sera utilisé pour l’utilisateur qui se connecte.

Étant donné que l’ordre de recherche des capacités de rôle n’est pas déterministe lorsque deux ou plusieurs capacités de rôle partagent le même nom, il est **fortement recommandé** de vous assurer que les capacités de rôle ont des noms uniques sur votre ordinateur.

### <a name="conditional-access-rules"></a>Règles d’accès conditionnel

Tous les utilisateurs et groupes inclus dans le champ RoleDefinitions reçoivent automatiquement l’accès aux points de terminaison JEA.
Les règles d’accès conditionnel permettent d’affiner cet accès et exigent que les utilisateurs appartiennent à d’autres groupes de sécurité qui n’affectent pas les rôles qui leur sont affectés.
Cela peut être utile si vous souhaitez intégrer une solution de gestion des accès privilégiés en « juste à temps », l’authentification par carte à puce ou une autre solution d’authentification multifacteur avec JEA.

Les règles d’accès conditionnel sont définies dans le champ RequiredGroups d’un fichier de configuration de session.
Vous pouvez y spécifier une table de hachage (éventuellement imbriquée) qui utilise des clés « And » et « Or » pour créer vos règles.
Voici quelques exemples montrant comment tirer parti de ce champ :

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
> Les règles d’accès conditionnel sont disponibles uniquement dans Windows PowerShell 5.1 et les versions ultérieures.

### <a name="other-properties"></a>Autres propriétés
Les fichiers de configuration de session peuvent également faire les mêmes choses qu’un fichier de capacités de rôle, sauf donner accès aux utilisateurs connectés à des commandes différentes.
Si vous souhaitez autoriser tous les utilisateurs à accéder à des applets de commande, fonctions ou fournisseurs spécifiques, vous pouvez le faire directement dans le fichier de configuration de session.
Pour obtenir la liste complète des propriétés prises en charge dans le fichier de configuration de session, exécutez `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Tester un fichier de configuration de session

Vous pouvez tester une configuration de session avec l’applet de commande [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile).
Il est fortement recommandé de tester votre fichier de configuration de session, si vous avez modifié le fichier pssc manuellement à l’aide d’un éditeur de texte, pour vérifier que la syntaxe est correcte.
Si le fichier de configuration de session ne passe pas ce test, son enregistrement sur le système ne réussira pas.

## <a name="sample-session-configuration-file"></a>Exemple de fichier de configuration de session

Voici un exemple complet montrant comment créer et valider une configuration de session pour JEA.
Notez que les définitions de rôles sont créées et stockées dans la variable `$roles` par souci de commodité et de lisibilité.
Il n’y a pas d’obligation à s’y conformer.

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

Si vous avez besoin de modifier les propriétés d’une configuration de session JEA, y compris le mappage des utilisateurs aux rôles, vous devez [annuler](register-jea.md#unregistering-jea-configurations) et [renouveler l’enregistrement](register-jea.md) de la configuration de session JEA.
Lorsque vous enregistrez de nouveau la configuration de session JEA, utilisez un fichier de configuration de session PowerShell mis à jour qui inclut les modifications désirées.

## <a name="next-steps"></a>Étapes suivantes

- [Enregistrer une configuration JEA](register-jea.md)
- [Créer des rôles JEA](role-capabilities.md)