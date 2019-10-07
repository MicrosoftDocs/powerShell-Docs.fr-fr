---
ms.date: 09/19/2019
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Installation de PowerShellGet
ms.openlocfilehash: 69dc851c54089b47fb19e5b32990d579d26effb9
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328200"
---
# <a name="installing-powershellget"></a><span data-ttu-id="df936-103">Installation de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="df936-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="df936-104">PowerShellGet est un module inclus par défaut dans les versions suivantes</span><span class="sxs-lookup"><span data-stu-id="df936-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="df936-105">[Windows 10](https://www.microsoft.com/windows) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="df936-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="df936-106">[Windows Server 2016](/windows-server/windows-server) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="df936-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="df936-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="df936-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="df936-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="df936-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="df936-109">Obtenir la dernière version de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="df936-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="df936-110">Avant d’effectuer la mise à jour de **PowerShellGet**, vous devez toujours installer le dernier fournisseur **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="df936-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="df936-111">À partir d’une session PowerShell avec élévation de privilèges, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="df936-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="df936-112">Pour les systèmes avec PowerShell 5.0 (ou version ultérieure), vous pouvez installer la dernière version de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="df936-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="df936-113">Pour installer PowerShellGet sur Windows 10, Windows Server 2016, tout système équipé de WMF 5.0 ou 5.1, ou tout système équipé de PowerShell 6, exécutez les commandes suivantes à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="df936-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="df936-114">Utilisez `Update-Module` pour obtenir des versions plus récentes.</span><span class="sxs-lookup"><span data-stu-id="df936-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a><span data-ttu-id="df936-115">Pour les ordinateurs exécutant PowerShell 3.0 ou PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="df936-115">For computers running PowerShell 3.0 or PowerShell 4.0</span></span>

<span data-ttu-id="df936-116">Ces instructions s’appliquent aux ordinateurs sur lesquels **PackageManagement Preview** est installé ou qui ne disposent d’aucune version de **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="df936-116">These instructions apply to computers that have the **PackageManagement Preview** installed or don't have any version of **PowerShellGet** installed.</span></span>

<span data-ttu-id="df936-117">L’applet de commande `Save-Module` est utilisée dans les deux jeux d’instructions.</span><span class="sxs-lookup"><span data-stu-id="df936-117">The `Save-Module` cmdlet is used in both sets of instructions.</span></span> <span data-ttu-id="df936-118">`Save-Module` permet de télécharger un module et les dépendances éventuelles à partir d’un dépôt inscrit et de les y enregistrer.</span><span class="sxs-lookup"><span data-stu-id="df936-118">`Save-Module` downloads and saves a module and any dependencies from a registered repository.</span></span> <span data-ttu-id="df936-119">La version la plus récente du module est enregistrée sur un chemin spécifié sur l’ordinateur local, mais n’est pas installée.</span><span class="sxs-lookup"><span data-stu-id="df936-119">The module's most current version is saved to a specified path on the local computer, but isn't installed.</span></span> <span data-ttu-id="df936-120">Pour plus d’informations, consultez [Save-Module](/powershell/module/PowershellGet/Save-Module).</span><span class="sxs-lookup"><span data-stu-id="df936-120">For more information, see [Save-Module](/powershell/module/PowershellGet/Save-Module).</span></span>

#### <a name="computers-with-the-packagemanagement-preview-installed"></a><span data-ttu-id="df936-121">Ordinateurs sur lesquels la préversion de PackageManagement est installée</span><span class="sxs-lookup"><span data-stu-id="df936-121">Computers with the PackageManagement Preview installed</span></span>

1. <span data-ttu-id="df936-122">À partir d’une session PowerShell, utilisez `Save-Module` pour enregistrer les modules dans un répertoire local.</span><span class="sxs-lookup"><span data-stu-id="df936-122">From a PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="df936-123">Vérifiez que les modules **PowerShellGet** et **PackageManagement** ne sont pas chargés dans d’autres processus.</span><span class="sxs-lookup"><span data-stu-id="df936-123">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="df936-124">Supprimez le contenu des dossiers : `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` et `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="df936-124">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="df936-125">Ouvrez à nouveau la console PowerShell avec élévation de privilèges, puis exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="df936-125">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a><span data-ttu-id="df936-126">Ordinateurs sans PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="df936-126">Computers without PowerShellGet</span></span>

<span data-ttu-id="df936-127">Les ordinateurs qui ne disposent d’aucune version de **PowerShellGet** ne peuvent pas télécharger les modules. Pour pouvoir le faire, **PowerShellGet** doit être installé sur ces ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="df936-127">For computer's without any version of **PowerShellGet** installed, a computer with **PowerShellGet** installed is needed to download the modules.</span></span>

1. <span data-ttu-id="df936-128">À partir d’un ordinateur sur lequel **PowerShellGet** est installé, utilisez `Save-Module` pour télécharger la version actuelle de **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="df936-128">From the computer that has **PowerShellGet** installed, use `Save-Module` to download the current version of **PowerShellGet**.</span></span> <span data-ttu-id="df936-129">Deux dossiers sont téléchargés : **PowerShellGet** et **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="df936-129">Two folders are downloaded: **PowerShellGet** and **PackageManagement**.</span></span> <span data-ttu-id="df936-130">Chaque dossier contient un sous-dossier avec un numéro de version.</span><span class="sxs-lookup"><span data-stu-id="df936-130">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="df936-131">Copiez les dossiers **PowerShellGet** et **PackageManagement** sur l’ordinateur qui ne dispose pas de **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="df936-131">Copy the **PowerShellGet** and **PackageManagement** folders to the computer that doesn't have **PowerShellGet** installed.</span></span>

   <span data-ttu-id="df936-132">Le répertoire de destination est le suivant : `$env:ProgramFiles\WindowsPowerShell\Modules`</span><span class="sxs-lookup"><span data-stu-id="df936-132">The destination directory is: `$env:ProgramFiles\WindowsPowerShell\Modules`</span></span>
