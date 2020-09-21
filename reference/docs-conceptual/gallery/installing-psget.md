---
ms.date: 09/19/2019
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Installation de PowerShellGet
ms.openlocfilehash: 4a10699be9ff2b64e5848c6749bdd3dedf55e3c7
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88162509"
---
# <a name="installing-powershellget"></a><span data-ttu-id="84420-103">Installation de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="84420-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="84420-104">PowerShellGet est un module inclus par défaut dans les versions suivantes</span><span class="sxs-lookup"><span data-stu-id="84420-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="84420-105">[Windows 10](https://www.microsoft.com/windows) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="84420-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="84420-106">[Windows Server 2016](/windows-server/windows-server) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="84420-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="84420-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="84420-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="84420-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="84420-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="84420-109">Obtenir la dernière version de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="84420-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="84420-110">Avant d’effectuer la mise à jour de **PowerShellGet**, vous devez toujours installer le dernier fournisseur **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="84420-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="84420-111">À partir d’une session PowerShell avec élévation de privilèges, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="84420-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="84420-112">Pour les systèmes avec PowerShell 5.0 (ou version ultérieure), vous pouvez installer la dernière version de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="84420-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="84420-113">Pour installer PowerShellGet sur Windows 10, Windows Server 2016, tout système équipé de WMF 5.0 ou 5.1, ou tout système équipé de PowerShell 6, exécutez les commandes suivantes à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="84420-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
```

<span data-ttu-id="84420-114">Utilisez `Update-Module` pour obtenir des versions plus récentes.</span><span class="sxs-lookup"><span data-stu-id="84420-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a><span data-ttu-id="84420-115">Pour les ordinateurs exécutant PowerShell 3.0 ou PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="84420-115">For computers running PowerShell 3.0 or PowerShell 4.0</span></span>

<span data-ttu-id="84420-116">Ces instructions s’appliquent aux ordinateurs sur lesquels **PackageManagement Preview** est installé ou qui ne disposent d’aucune version de **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="84420-116">These instructions apply to computers that have the **PackageManagement Preview** installed or don't have any version of **PowerShellGet** installed.</span></span>

<span data-ttu-id="84420-117">L’applet de commande `Save-Module` est utilisée dans les deux jeux d’instructions.</span><span class="sxs-lookup"><span data-stu-id="84420-117">The `Save-Module` cmdlet is used in both sets of instructions.</span></span> <span data-ttu-id="84420-118">`Save-Module` permet de télécharger un module et les dépendances éventuelles à partir d’un dépôt inscrit et de les y enregistrer.</span><span class="sxs-lookup"><span data-stu-id="84420-118">`Save-Module` downloads and saves a module and any dependencies from a registered repository.</span></span> <span data-ttu-id="84420-119">La version la plus récente du module est enregistrée sur un chemin spécifié sur l’ordinateur local, mais n’est pas installée.</span><span class="sxs-lookup"><span data-stu-id="84420-119">The module's most current version is saved to a specified path on the local computer, but isn't installed.</span></span> <span data-ttu-id="84420-120">Pour installer les modules dans PowerShell 3.0 ou 4.0, copiez les dossiers enregistrés du module dans `$env:ProgramFiles\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="84420-120">To install the modules in PowerShell 3.0 or 4.0, copy the module saved folders to `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span>

<span data-ttu-id="84420-121">Pour plus d’informations, consultez [Save-Module](/powershell/module/PowershellGet/Save-Module).</span><span class="sxs-lookup"><span data-stu-id="84420-121">For more information, see [Save-Module](/powershell/module/PowershellGet/Save-Module).</span></span>

> [!NOTE]
> <span data-ttu-id="84420-122">PowerShell 3.0 et PowerShell 4.0 ne prenaient en charge qu’une seule version d’un module.</span><span class="sxs-lookup"><span data-stu-id="84420-122">PowerShell 3.0 and PowerShell 4.0 only supported one version of a module.</span></span> <span data-ttu-id="84420-123">À compter de PowerShell 5.0, les modules sont installés dans `<modulename>\<version>`.</span><span class="sxs-lookup"><span data-stu-id="84420-123">Starting in PowerShell 5.0, modules are installed in `<modulename>\<version>`.</span></span> <span data-ttu-id="84420-124">Cela vous permet d’installer plusieurs versions côte à côte.</span><span class="sxs-lookup"><span data-stu-id="84420-124">This allows you to install multiple versions side-by-side.</span></span> <span data-ttu-id="84420-125">Après avoir téléchargé le module à l’aide de `Save-Module`, vous devez copier les fichiers du dossier `<modulename>\<version>` dans le dossier `<modulename>` sur l’ordinateur de destination, comme indiqué dans les instructions ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="84420-125">After downloading the module using `Save-Module` you must copy the files from the `<modulename>\<version>` to the `<modulename>` folder on the destination machine, as shown in the instructions below.</span></span>

#### <a name="preparatory-step-on-computers-running-powershell-30"></a><span data-ttu-id="84420-126">Étape préparatoire sur les ordinateurs exécutant PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="84420-126">Preparatory Step on computers running PowerShell 3.0</span></span>

<span data-ttu-id="84420-127">Les instructions fournies dans les sections ci-dessous permettent d’installer les modules dans le répertoire `$env:ProgramFiles\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="84420-127">The instructions in the sections below install the modules in directory `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span>
<span data-ttu-id="84420-128">Dans PowerShell 3.0, ce répertoire n’est pas listé dans `$env:PSModulePath` par défaut. Vous devez donc l’ajouter pour que les modules se chargent automatiquement.</span><span class="sxs-lookup"><span data-stu-id="84420-128">In PowerShell 3.0, this directory isn't listed in `$env:PSModulePath` by default, so you'll need to add it in order for the modules to be auto-loaded.</span></span> 

<span data-ttu-id="84420-129">Ouvrez une session PowerShell avec élévation de privilèges et exécutez la commande suivante (qui prendra effet dans les sessions ultérieures) :</span><span class="sxs-lookup"><span data-stu-id="84420-129">Open an elevated PowerShell session and run the following command (which will take effect in future sessions):</span></span>

```powershell
[Environment]::SetEnvironmentVariable(
  'PSModulePath',
  ((([Environment]::GetEnvironmentVariable('PSModulePath', 'Machine') -split ';') + "$env:ProgramFiles\WindowsPowerShell\Modules") -join ';'),
  'Machine'
)
```

#### <a name="computers-with-the-packagemanagement-preview-installed"></a><span data-ttu-id="84420-130">Ordinateurs sur lesquels la préversion de PackageManagement est installée</span><span class="sxs-lookup"><span data-stu-id="84420-130">Computers with the PackageManagement Preview installed</span></span>

> [!NOTE] 
> <span data-ttu-id="84420-131">La préversion de PackageManagement était un composant téléchargeable qui rendait PowerShellGet disponible pour les versions 3 et 4 de PowerShell, mais ce composant n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="84420-131">PackageManagement Preview was a downloadable component that made PowerShellGet available to PowerShell versions 3 and 4, but it is no longer available.</span></span>
> <span data-ttu-id="84420-132">Pour déterminer s’il a été installé sur un ordinateur donné, exécutez `Get-Module -ListAvailable PowerShellGet`.</span><span class="sxs-lookup"><span data-stu-id="84420-132">To test if it was installed on a given computer, run `Get-Module -ListAvailable PowerShellGet`.</span></span>

1. <span data-ttu-id="84420-133">À partir d’une session PowerShell, utilisez `Save-Module` pour télécharger la version actuelle de **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="84420-133">From a PowerShell session, use `Save-Module` to download the current version of **PowerShellGet**.</span></span> <span data-ttu-id="84420-134">Deux dossiers sont téléchargés : **PowerShellGet** et **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="84420-134">Two folders are downloaded: **PowerShellGet** and **PackageManagement**.</span></span> <span data-ttu-id="84420-135">Chaque dossier contient un sous-dossier avec un numéro de version.</span><span class="sxs-lookup"><span data-stu-id="84420-135">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="84420-136">Vérifiez que les modules **PowerShellGet** et **PackageManagement** ne sont pas chargés dans d’autres processus.</span><span class="sxs-lookup"><span data-stu-id="84420-136">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>

1. <span data-ttu-id="84420-137">Rouvrez la console PowerShell avec élévation de privilèges, puis exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="84420-137">Reopen the PowerShell console with elevated permissions and run the following command.</span></span>

   ```powershell
   'PowerShellGet', 'PackageManagement' | % { 
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     Remove-Item $targetDir\* -Recurse -Force
     Copy-Item C:\LocalFolder\$_\*\* $targetDir\ -Recurse -Force
   }
   ```

#### <a name="computers-without-powershellget"></a><span data-ttu-id="84420-138">Ordinateurs sans PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="84420-138">Computers without PowerShellGet</span></span>

<span data-ttu-id="84420-139">Les ordinateurs qui ne disposent d’aucune version de **PowerShellGet** (utilisez `Get-Module -ListAvailable PowerShellGet` pour le déterminer) ne peuvent pas télécharger les modules. Pour pouvoir le faire, **PowerShellGet** doit être installé sur ces ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="84420-139">For computers without any version of **PowerShellGet** installed (test with `Get-Module -ListAvailable PowerShellGet`), a computer with **PowerShellGet** installed is needed to download the modules.</span></span>

1. <span data-ttu-id="84420-140">À partir d’un ordinateur sur lequel **PowerShellGet** est installé, utilisez `Save-Module` pour télécharger la version actuelle de **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="84420-140">From the computer that has **PowerShellGet** installed, use `Save-Module` to download the current version of **PowerShellGet**.</span></span> <span data-ttu-id="84420-141">Deux dossiers sont téléchargés : **PowerShellGet** et **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="84420-141">Two folders are downloaded: **PowerShellGet** and **PackageManagement**.</span></span> <span data-ttu-id="84420-142">Chaque dossier contient un sous-dossier avec un numéro de version.</span><span class="sxs-lookup"><span data-stu-id="84420-142">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="84420-143">Copiez le sous-dossier `<version>` respectif dans les dossiers **PowerShellGet** et **PackageManagement** sur l’ordinateur sur lequel **PowerShellGet** n’est pas installé, dans les dossiers `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` et `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` respectivement, ce qui nécessite une session avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="84420-143">Copy the respective `<version>` subfolder in the **PowerShellGet** and **PackageManagement** folders to the computer that doesn't have **PowerShellGet** installed, into folders `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` respectively, which requires an elevated session.</span></span>
   
1. <span data-ttu-id="84420-144">Par exemple, si vous pouvez accéder au dossier de téléchargement sur l’autre ordinateur, par exemple `ws1`, à partir de l’ordinateur cible par le biais d’un chemin UNC, par exemple `\\ws1\C$\LocalFolder`, ouvrez une console PowerShell avec des autorisations élevées et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="84420-144">For instance, if you can access the download folder on the other computer, say `ws1`, from the target computer via a UNC path, say `\\ws1\C$\LocalFolder`, open a PowerShell console with elevated permissions and run the following command:</span></span>

   ```powershell
   'PowerShellGet', 'PackageManagement' | % {
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     $null = New-Item -Type Directory -Force $targetDir
     $fromComputer = 'ws1'  # Specify the name of the other computer here.
     Copy-Item \\$fromComputer\C$\LocalFolder\$_\*\* $targetDir -Recurse -Force
     if (-not (Get-ChildItem $targetDir)) { Throw "Copying failed." }
   }
   ```
