---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Améliorations de Just Enough Administration (JEA)
ms.openlocfilehash: 847ae92a6225023bcd0ee3dfe7c7058bdc356836
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71147599"
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="11045-103">Améliorations de Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="11045-103">Improvements to Just Enough Administration (JEA)</span></span>

<span data-ttu-id="11045-104">Just Enough Administration est une nouvelle fonctionnalité de WMF 5.0 qui autorise l’administration basée sur des rôles par le biais de l’accès distant PowerShell.</span><span class="sxs-lookup"><span data-stu-id="11045-104">Just Enough Administration is a new feature in WMF 5.0 that enables role-based administration through PowerShell remoting.</span></span> <span data-ttu-id="11045-105">Elle étend l’infrastructure de point de terminaison contrainte existante en autorisant les utilisateurs non administrateurs à exécuter des commandes, des scripts et des exécutables spécifiques en tant qu’administrateur,</span><span class="sxs-lookup"><span data-stu-id="11045-105">It extends the existing constrained endpoint infrastructure by allowing non-administrators to run specific commands, scripts, and executables as an administrator.</span></span> <span data-ttu-id="11045-106">ce qui permet de réduire le nombre d’administrateurs complets de l’environnement et d’améliorer la sécurité.</span><span class="sxs-lookup"><span data-stu-id="11045-106">This enables you to reduce the number of full administrators in your environment and improve security.</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="11045-107">Copie de fichiers contrainte vers/depuis des points de terminaison JEA</span><span class="sxs-lookup"><span data-stu-id="11045-107">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="11045-108">Il est maintenant possible de copier des fichiers à distance vers/à partir d’un point de terminaison JEA sans que l’utilisateur connecté puisse copier *n’importe quel* fichier sur votre système.</span><span class="sxs-lookup"><span data-stu-id="11045-108">You can now remotely copy files to/from a JEA endpoint and be assured that the connecting user can't copy just *any* file on your system.</span></span> <span data-ttu-id="11045-109">Ceci est possible en configurant votre fichier PSSC pour monter un lecteur utilisateur pour la connexion des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="11045-109">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span> <span data-ttu-id="11045-110">Le lecteur utilisateur est un nouveau PSDrive qui est unique pour chaque utilisateur qui se connecte et persiste à travers les sessions.</span><span class="sxs-lookup"><span data-stu-id="11045-110">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span> <span data-ttu-id="11045-111">Quand `Copy-Item` est utilisée pour copier des fichiers vers ou à partir d’une session JEA, elle est contrainte d’autoriser l’accès seulement au lecteur utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11045-111">When `Copy-Item` is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span> <span data-ttu-id="11045-112">Les tentatives de copie de fichiers vers n’importe quel autre PSDrive échouent.</span><span class="sxs-lookup"><span data-stu-id="11045-112">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="11045-113">Pour configurer le lecteur utilisateur dans votre fichier de configuration de session JEA, utilisez les nouveaux champs suivants :</span><span class="sxs-lookup"><span data-stu-id="11045-113">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="11045-114">Le dossier servant de base au lecteur utilisateur est créé dans `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="11045-114">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="11045-115">Pour utiliser le lecteur utilisateur et copier des fichiers vers/à partir d’un point de terminaison JEA configuré pour exposer le lecteur utilisateur, utilisez les paramètres `-ToSession` et `-FromSession` sur `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="11045-115">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on `Copy-Item`.</span></span>

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

<span data-ttu-id="11045-116">Vous pouvez ensuite écrire des fonctions personnalisées pour traiter les données stockées dans le lecteur utilisateur et les mettre à disposition des utilisateurs dans votre fichier de fonctionnalité du rôle.</span><span class="sxs-lookup"><span data-stu-id="11045-116">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="11045-117">Prise en charge des comptes de service géré par un groupe</span><span class="sxs-lookup"><span data-stu-id="11045-117">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="11045-118">Dans certains cas, une tâche que l’utilisateur doit effectuer dans une session JEA doit accéder à des ressources en dehors de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="11045-118">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span> <span data-ttu-id="11045-119">Quand une session JEA est configurée pour utiliser un compte virtuel, toute tentative pour atteindre ces ressources apparaît comme provenant de l’identité de l’ordinateur local, et non pas du compte virtuel ou de l’utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="11045-119">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span> <span data-ttu-id="11045-120">Dans TP5, nous avons activé la prise en charge de l’exécution de JEA dans le contexte d’un [compte de service administré par un groupe](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), facilitant ainsi l’accès aux ressources réseau à l’aide d’une identité de domaine.</span><span class="sxs-lookup"><span data-stu-id="11045-120">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="11045-121">Pour configurer une session JEA pour qu’elle s’exécute sous un compte gMSA, utilisez la nouvelle clé suivante dans votre fichier PSSC :</span><span class="sxs-lookup"><span data-stu-id="11045-121">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> <span data-ttu-id="11045-122">Les comptes de service gérés par un groupe n’offrent pas l’isolement ou l’étendue limitée des comptes virtuels.</span><span class="sxs-lookup"><span data-stu-id="11045-122">Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="11045-123">Chaque utilisateur qui se connecte partage la même identité gMSA, qui peut avoir des autorisations pour toute votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="11045-123">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span> <span data-ttu-id="11045-124">Soyez très prudent quand vous choisissez d’utiliser un compte gMSA, et préférez toujours quand c’est possible les comptes virtuels qui sont limités à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="11045-124">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="11045-125">Stratégies d’accès conditionnel</span><span class="sxs-lookup"><span data-stu-id="11045-125">Conditional access policies</span></span>

<span data-ttu-id="11045-126">JEA est une bonne solution pour limiter ce qu’une personne peut faire quand elle est connectée à un système pour le gérer, mais que se passe-t-il si vous voulez également limiter *les moments* où une personne peut utiliser JEA ?</span><span class="sxs-lookup"><span data-stu-id="11045-126">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span> <span data-ttu-id="11045-127">Nous avons ajouté des options de configuration dans les fichiers de configuration de session (.pssc) pour vous permettre de spécifier les groupes de sécurité auxquels l’utilisateur doit appartenir pour pouvoir établir une session JEA.</span><span class="sxs-lookup"><span data-stu-id="11045-127">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span> <span data-ttu-id="11045-128">Elles vous seront particulièrement utiles si vous disposez d’un système juste-à-temps (JIT) dans votre environnement et que vous voulez que vos utilisateurs élèvent leurs privilèges pour accéder à un point de terminaison JEA avec des autorisations élevés.</span><span class="sxs-lookup"><span data-stu-id="11045-128">This is especially helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="11045-129">Le nouveau champ *RequiredGroups* du fichier PSSC vous permet de spécifier la logique pour déterminer si l’utilisateur peut se connecter à JEA.</span><span class="sxs-lookup"><span data-stu-id="11045-129">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span> <span data-ttu-id="11045-130">Cela consiste à spécifier une table de hachage (éventuellement imbriquée) qui utilise les clés « And » et « Or » pour créer vos règles.</span><span class="sxs-lookup"><span data-stu-id="11045-130">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="11045-131">Voici quelques exemples d’utilisation de ce champ :</span><span class="sxs-lookup"><span data-stu-id="11045-131">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="11045-132">Résolu : Les comptes virtuels sont maintenant pris en charge sur Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="11045-132">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>

<span data-ttu-id="11045-133">Dans WMF 5.1, vous pouvez maintenant utiliser des comptes virtuels sur Windows Server 2008 R2, ce qui permet des configurations cohérentes et la parité des fonctionnalités entre Windows Server 2008 R2 et Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="11045-133">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span> <span data-ttu-id="11045-134">Les comptes virtuels restent non pris en charge quand JEA est utilisé sur Windows 7.</span><span class="sxs-lookup"><span data-stu-id="11045-134">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>