---
ms.date: 06/12/2017
title: Améliorations de Just Enough Administration (JEA)
description: JEA est une nouvelle fonctionnalité de WMF 5.0 qui autorise l’administration basée sur des rôles par le biais de l’accès distant PowerShell. Elle étend l’infrastructure de point de terminaison contrainte existante en autorisant les utilisateurs non administrateurs à exécuter des commandes, des scripts et des exécutables spécifiques en tant qu’administrateur,
ms.openlocfilehash: f255d0ecbd4bbd9a5ade4b6e19f066cc007481fb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654032"
---
# <a name="improvements-to-just-enough-administration-jea"></a>Améliorations de Just Enough Administration (JEA)

Just Enough Administration est une nouvelle fonctionnalité de WMF 5.0 qui autorise l’administration basée sur des rôles par le biais de l’accès distant PowerShell. Elle étend l’infrastructure de point de terminaison contrainte existante en autorisant les utilisateurs non administrateurs à exécuter des commandes, des scripts et des exécutables spécifiques en tant qu’administrateur, ce qui permet de réduire le nombre d’administrateurs complets de l’environnement et d’améliorer la sécurité.

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>Copie de fichiers contrainte vers/depuis des points de terminaison JEA

Il est maintenant possible de copier des fichiers à distance vers/à partir d’un point de terminaison JEA sans que l’utilisateur connecté puisse copier *n’importe quel* fichier sur votre système. Ceci est possible en configurant votre fichier PSSC pour monter un lecteur utilisateur pour la connexion des utilisateurs. Le lecteur utilisateur est un nouveau PSDrive qui est unique pour chaque utilisateur qui se connecte et persiste à travers les sessions. Quand `Copy-Item` est utilisée pour copier des fichiers vers ou à partir d’une session JEA, elle est contrainte d’autoriser l’accès seulement au lecteur utilisateur. Les tentatives de copie de fichiers vers n’importe quel autre PSDrive échouent.

Pour configurer le lecteur utilisateur dans votre fichier de configuration de session JEA, utilisez les nouveaux champs suivants :

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

Le dossier servant de base au lecteur utilisateur est créé dans `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\`. Pour chaque utilisateur qui se connecte au point de terminaison, un dossier est créé avec le nom `$env:USERDOMAIN_$env:USERNAME`.

Pour utiliser le lecteur utilisateur et copier des fichiers vers/à partir d’un point de terminaison JEA configuré pour exposer le lecteur utilisateur, utilisez les paramètres `-ToSession` et `-FromSession` sur `Copy-Item`.

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine.
# You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

Vous pouvez ensuite écrire des fonctions personnalisées pour traiter les données stockées dans le lecteur utilisateur et les mettre à disposition des utilisateurs dans votre fichier de fonctionnalité du rôle.

## <a name="support-for-group-managed-service-accounts"></a>Prise en charge des comptes de service géré par un groupe

Dans certains cas, une tâche que l’utilisateur doit effectuer dans une session JEA doit accéder à des ressources en dehors de l’ordinateur local. Quand une session JEA est configurée pour utiliser un compte virtuel, toute tentative pour atteindre ces ressources apparaît comme provenant de l’identité de l’ordinateur local, et non pas du compte virtuel ou de l’utilisateur connecté. Dans TP5, nous avons activé la prise en charge de l’exécution de JEA dans le contexte d’un [compte de service administré par un groupe](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), facilitant ainsi l’accès aux ressources réseau à l’aide d’une identité de domaine.

Pour configurer une session JEA pour qu’elle s’exécute sous un compte gMSA, utilisez la nouvelle clé suivante dans votre fichier PSSC :

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> Les comptes de service gérés par un groupe n’offrent pas l’isolement ou l’étendue limitée des comptes virtuels.
> Chaque utilisateur qui se connecte partage la même identité gMSA, qui peut avoir des autorisations pour toute votre entreprise. Soyez très prudent quand vous choisissez d’utiliser un compte gMSA, et préférez toujours quand c’est possible les comptes virtuels qui sont limités à l’ordinateur local.

## <a name="conditional-access-policies"></a>Stratégies d’accès conditionnel

JEA est une bonne solution pour limiter ce qu’une personne peut faire quand elle est connectée à un système pour le gérer, mais que se passe-t-il si vous voulez également limiter *les moments* où une personne peut utiliser JEA ? Nous avons ajouté des options de configuration dans les fichiers de configuration de session (.pssc) pour vous permettre de spécifier les groupes de sécurité auxquels l’utilisateur doit appartenir pour pouvoir établir une session JEA. Elles vous seront particulièrement utiles si vous disposez d’un système juste-à-temps (JIT) dans votre environnement et que vous voulez que vos utilisateurs élèvent leurs privilèges pour accéder à un point de terminaison JEA avec des autorisations élevés.

Le nouveau champ *RequiredGroups* du fichier PSSC vous permet de spécifier la logique pour déterminer si l’utilisateur peut se connecter à JEA. Cela consiste à spécifier une table de hachage (éventuellement imbriquée) qui utilise les clés « And » et « Or » pour créer vos règles. Voici quelques exemples d’utilisation de ce champ :

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>Résolu : les comptes virtuels sont maintenant pris en charge sur Windows Server 2008 R2

Dans WMF 5.1, vous pouvez maintenant utiliser des comptes virtuels sur Windows Server 2008 R2, ce qui permet des configurations cohérentes et la parité des fonctionnalités entre Windows Server 2008 R2 et Windows Server 2016. Les comptes virtuels restent non pris en charge quand JEA est utilisé sur Windows 7.
