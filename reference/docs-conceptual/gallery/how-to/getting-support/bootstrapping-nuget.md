---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Amorcer NuGet
ms.openlocfilehash: 6d8f106bc3b8741203e87e4c097948a843f06d6e
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328430"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="5eb08-103">Amorcer le fournisseur NuGet et NuGet.exe</span><span class="sxs-lookup"><span data-stu-id="5eb08-103">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="5eb08-104">NuGet.exe n’est pas inclus dans le dernier fournisseur NuGet.</span><span class="sxs-lookup"><span data-stu-id="5eb08-104">NuGet.exe is not included in the latest NuGet provider.</span></span> <span data-ttu-id="5eb08-105">Pour les opérations de publication d’un module ou d’un script, PowerShellGet nécessite la version binaire exécutable, NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="5eb08-105">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span> <span data-ttu-id="5eb08-106">Le fournisseur NuGet est requis pour toutes les autres opérations, y compris *trouver*, *installer*, *enregistrer* et *désinstaller*.</span><span class="sxs-lookup"><span data-stu-id="5eb08-106">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="5eb08-107">PowerShellGet inclut une logique pour gérer soit un démarrage combiné du fournisseur NuGet et de NuGet.exe soit un démarrage du fournisseur NuGet uniquement.</span><span class="sxs-lookup"><span data-stu-id="5eb08-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span> <span data-ttu-id="5eb08-108">Dans les deux cas, une seule invite doit s’afficher.</span><span class="sxs-lookup"><span data-stu-id="5eb08-108">In either case, only a single prompt message should occur.</span></span> <span data-ttu-id="5eb08-109">Si l’ordinateur n’est pas connecté à Internet, l’utilisateur ou administrateur doit copier une instance approuvée du fournisseur NuGet et/ou du fichier NuGet.exe sur l’ordinateur déconnecté.</span><span class="sxs-lookup"><span data-stu-id="5eb08-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

> [!NOTE]
> <span data-ttu-id="5eb08-110">À compter de la version 6, le fournisseur NuGet est inclus dans l’installation de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5eb08-110">Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span>

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="5eb08-111">Résolution des erreurs lorsque le fournisseur NuGet n’a pas été installé sur un ordinateur qui est connecté à Internet</span><span class="sxs-lookup"><span data-stu-id="5eb08-111">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="5eb08-112">Résolution des erreurs lorsque le fournisseur NuGet est disponible et que NuGet.exe n’est pas disponible lors de l’opération de publication sur une machine connectée à Internet</span><span class="sxs-lookup"><span data-stu-id="5eb08-112">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="5eb08-113">Résolution des erreurs lorsque ni le fournisseur NuGet ni NuGet.exe ne sont disponibles lors de l’opération de publication sur une machine connectée à Internet</span><span class="sxs-lookup"><span data-stu-id="5eb08-113">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="5eb08-114">Démarrage manuel du fournisseur NuGet sur un ordinateur qui n’est pas connecté à Internet</span><span class="sxs-lookup"><span data-stu-id="5eb08-114">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="5eb08-115">Les processus détaillés ci-dessus supposent que l’ordinateur est connecté à Internet et peut télécharger des fichiers à partir d’un emplacement public.</span><span class="sxs-lookup"><span data-stu-id="5eb08-115">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span> <span data-ttu-id="5eb08-116">Si cela n’est pas possible, la seule option est de démarrer une machine en utilisant les processus ci-dessus et de copier manuellement le fournisseur sur le nœud isolé via un processus approuvé en mode hors connexion.</span><span class="sxs-lookup"><span data-stu-id="5eb08-116">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span> <span data-ttu-id="5eb08-117">Le cas d’utilisation le plus courant pour ce scénario est lorsqu’une galerie privée est disponible pour prendre en charge un environnement isolé.</span><span class="sxs-lookup"><span data-stu-id="5eb08-117">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="5eb08-118">Après avoir suivi le processus ci-dessus pour démarrer une machine connectée à Internet, vous trouverez des fichiers du fournisseur à l’emplacement :</span><span class="sxs-lookup"><span data-stu-id="5eb08-118">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

`C:\Program Files\PackageManagement\ProviderAssemblies\`

<span data-ttu-id="5eb08-119">La structure de dossiers et fichiers du fournisseur NuGet sera (éventuellement avec un autre numéro de version) :</span><span class="sxs-lookup"><span data-stu-id="5eb08-119">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

<span data-ttu-id="5eb08-120">Copiez ces dossiers et fichiers avec un processus approuvé sur les machines en mode hors connexion.</span><span class="sxs-lookup"><span data-stu-id="5eb08-120">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="5eb08-121">Démarrage manuel de NuGet.exe pour prendre en charge les opérations de publication sur un ordinateur qui n’est pas connecté à Internet</span><span class="sxs-lookup"><span data-stu-id="5eb08-121">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="5eb08-122">Outre le processus de démarrage manuel du fournisseur NuGet, si la machine doit être utilisée pour publier des modules ou des scripts dans une galerie privée à l’aide de l’applet de commande `Publish-Module` ou `Publish-Script`, le fichier exécutable binaire NuGet.exe sera nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5eb08-122">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the `Publish-Module` or `Publish-Script` cmdlets, the NuGet.exe binary executable file will be required.</span></span>

<span data-ttu-id="5eb08-123">Le cas d’utilisation le plus courant pour ce scénario est lorsqu’une galerie privée est disponible pour prendre en charge un environnement isolé.</span><span class="sxs-lookup"><span data-stu-id="5eb08-123">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span> <span data-ttu-id="5eb08-124">Il existe deux options pour obtenir le fichier de NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="5eb08-124">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="5eb08-125">Une option consiste à démarrer une machine connectée à Internet et de copier les fichiers sur les machines en mode hors connexion à l’aide d’un processus approuvé.</span><span class="sxs-lookup"><span data-stu-id="5eb08-125">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span> <span data-ttu-id="5eb08-126">Après le démarrage de la machine connectée à Internet, le fichier binaire exécutable NuGet.exe se trouve dans un de ces deux dossiers :</span><span class="sxs-lookup"><span data-stu-id="5eb08-126">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="5eb08-127">Si l’applet de commande `Publish-Module` ou `Publish-Script` a été exécutée avec des autorisations élevées (en tant qu’administrateur) :</span><span class="sxs-lookup"><span data-stu-id="5eb08-127">If the `Publish-Module` or `Publish-Script` cmdlets were executed with elevated permissions (As an Administrator):</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="5eb08-128">Si les applets de commande ont été exécutées en tant qu’utilisateur sans autorisations élevées :</span><span class="sxs-lookup"><span data-stu-id="5eb08-128">If the cmdlets were executed as a user without elevated permissions:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="5eb08-129">L’autre possibilité consiste à télécharger NuGet.exe sur le site web NuGet.Org : [https://dist.nuget.org/index.html](https://www.nuget.org/downloads). Pour les ordinateurs de production, veillez à sélectionner une version de NuGet ultérieure à 2.8.5.208 et étiquetée comme étant « recommandée ».</span><span class="sxs-lookup"><span data-stu-id="5eb08-129">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span> <span data-ttu-id="5eb08-130">N’oubliez pas de débloquer le fichier s’il a été téléchargé à l’aide d’un navigateur.</span><span class="sxs-lookup"><span data-stu-id="5eb08-130">Remember to unblock the file if it was downloaded using a browser.</span></span> <span data-ttu-id="5eb08-131">Vous pouvez pour cela exécuter l’applet de commande `Unblock-File`.</span><span class="sxs-lookup"><span data-stu-id="5eb08-131">This can be performed by using the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="5eb08-132">Dans les deux cas, le fichier NuGet.exe peut être copié vers un emplacement quelconque dans `$env:path`, mais les emplacements standard sont :</span><span class="sxs-lookup"><span data-stu-id="5eb08-132">In either case, the NuGet.exe file can be copied to any location in `$env:path`, but the standard locations are:</span></span>

<span data-ttu-id="5eb08-133">Pour rendre l’exécutable disponible afin que tous les utilisateurs puissent utiliser les applets de commande `Publish-Module` et `Publish-Script` :</span><span class="sxs-lookup"><span data-stu-id="5eb08-133">To make the executable available so that all users can use `Publish-Module` and `Publish-Script` cmdlets:</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="5eb08-134">Pour rendre l’exécutable disponible pour seulement un utilisateur spécifique, copiez vers l’emplacement dans le profil de cet utilisateur uniquement :</span><span class="sxs-lookup"><span data-stu-id="5eb08-134">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```
