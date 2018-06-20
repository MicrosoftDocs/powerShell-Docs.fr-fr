---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
contributor: ryanpu
title: Améliorations de Just Enough Administration (JEA)
ms.openlocfilehash: 47a58a6fae9f3a41ec527ec1f77ac1c196336669
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222415"
---
# <a name="improvements-to-just-enough-administration-jea"></a>Améliorations de Just Enough Administration (JEA)

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>Copie de fichiers contrainte vers/depuis des points de terminaison JEA

Vous pouvez maintenant copier les fichiers à distance vers/depuis un point de terminaison JEA et être assuré que l’utilisateur connecté ne peut copier absolument *aucun* fichier sur votre système.
Ceci est possible en configurant votre fichier PSSC pour monter un lecteur utilisateur pour la connexion des utilisateurs.
Le lecteur utilisateur est un nouveau PSDrive qui est unique pour chaque utilisateur qui se connecte et persiste à travers les sessions.
Quand Copy-Item est utilisée pour copier des fichiers vers ou depuis une session JEA, elle est contrainte d’autoriser l’accès seulement au lecteur utilisateur.
Les tentatives de copie de fichiers vers n’importe quel autre PSDrive échouent.

Pour configurer le lecteur utilisateur dans votre fichier de configuration de session JEA, utilisez les nouveaux champs suivants :

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

Le dossier servant de base au lecteur utilisateur est créé dans `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

Pour utiliser le lecteur utilisateur et copier des fichiers vers/depuis un point de terminaison JEA configuré pour exposer le lecteur utilisateur, utilisez les paramètres `-ToSession` et `-FromSession` sur Copy-Item.

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

Vous pouvez ensuite écrire des fonctions personnalisées pour traiter les données stockées dans le lecteur utilisateur et les mettre à disposition des utilisateurs dans votre fichier de fonctionnalité du rôle.

## <a name="support-for-group-managed-service-accounts"></a>Prise en charge des comptes de service géré par un groupe

Dans certains cas, une tâche que l’utilisateur doit effectuer dans une session JEA doit accéder à des ressources en dehors de l’ordinateur local.
Quand une session JEA est configurée pour utiliser un compte virtuel, toute tentative pour atteindre ces ressources apparaît comme provenant de l’identité de l’ordinateur local, et non pas du compte virtuel ou de l’utilisateur connecté.
Dans TP5, nous avons activé la prise en charge de l’exécution de JEA dans le contexte d’un [compte de service administré par un groupe] (https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx), facilitant ainsi l’accès aux ressources réseau à l’aide d’une identité de domaine.

Pour configurer une session JEA pour qu’elle s’exécute sous un compte gMSA, utilisez la nouvelle clé suivante dans votre fichier PSSC :

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> **Remarque :** Les comptes de service gérés par un groupe n’offrent pas l’isolement ou l’étendue limitée des comptes virtuels.
> Chaque utilisateur qui se connecte partage la même identité gMSA, qui peut avoir des autorisations pour toute votre entreprise.
> Soyez très prudent quand vous choisissez d’utiliser un compte gMSA, et préférez toujours quand c’est possible les comptes virtuels qui sont limités à l’ordinateur local.

## <a name="conditional-access-policies"></a>Stratégies d’accès conditionnel

JEA est une bonne solution pour limiter ce qu’une personne peut faire quand elle est connectée à un système pour le gérer, mais que se passe-t-il si vous voulez également limiter *les moments* où une personne peut utiliser JEA ?
Nous avons ajouté des options de configuration dans les fichiers de configuration de session (.pssc) pour vous permettre de spécifier les groupes de sécurité auxquels l’utilisateur doit appartenir pour pouvoir établir une session JEA.
Ceci peut s’avérer particulièrement utile si vous avez un système juste-à-temps (JIT) dans votre environnement et que vous voulez que vos utilisateurs élèvent leurs privilèges avant d’accéder à un point de terminaison JEA avec des privilèges élevés.

Le nouveau champ *RequiredGroups* du fichier PSSC vous permet de spécifier la logique pour déterminer si l’utilisateur peut se connecter à JEA.
Cela consiste à spécifier une table de hachage (éventuellement imbriquée) qui utilise les clés « And » et « Or » pour créer vos règles.
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

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>Résolu : Les comptes virtuels sont maintenant pris en charge sur Windows Server 2008 R2
Dans WMF 5.1, vous pouvez maintenant utiliser des comptes virtuels sur Windows Server 2008 R2, ce qui permet des configurations cohérentes et la parité des fonctionnalités entre Windows Server 2008 R2 et Windows Server 2016.
Les comptes virtuels restent non pris en charge quand JEA est utilisé sur Windows 7.
