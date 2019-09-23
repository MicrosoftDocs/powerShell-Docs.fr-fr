---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Installation de PowerShellGet
ms.openlocfilehash: a0ef46a9ee4bbf668a58067256d098967bde48c5
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143592"
---
# <a name="installing-powershellget"></a><span data-ttu-id="8d7b1-103">Installation de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8d7b1-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="8d7b1-104">PowerShellGet est un module inclus par défaut dans les versions suivantes</span><span class="sxs-lookup"><span data-stu-id="8d7b1-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="8d7b1-105">[Windows 10](https://www.microsoft.com/windows) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="8d7b1-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="8d7b1-106">[Windows Server 2016](/windows-server/windows-server) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="8d7b1-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="8d7b1-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="8d7b1-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="8d7b1-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="8d7b1-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="8d7b1-109">Obtenir la dernière version de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8d7b1-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="8d7b1-110">Avant d’effectuer la mise à jour de **PowerShellGet**, vous devez toujours installer le dernier fournisseur **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8d7b1-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="8d7b1-111">À partir d’une session PowerShell avec élévation de privilèges, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="8d7b1-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="8d7b1-112">Pour les systèmes avec PowerShell 5.0 (ou version ultérieure), vous pouvez installer la dernière version de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8d7b1-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="8d7b1-113">Pour installer PowerShellGet sur Windows 10, Windows Server 2016, tout système équipé de WMF 5.0 ou 5.1, ou tout système équipé de PowerShell 6, exécutez les commandes suivantes à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="8d7b1-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="8d7b1-114">Utilisez `Update-Module` pour obtenir des versions plus récentes.</span><span class="sxs-lookup"><span data-stu-id="8d7b1-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-preview"></a><span data-ttu-id="8d7b1-115">Pour les systèmes exécutant PowerShell 3 ou PowerShell 4 et qui ont installé la préversion de PackageManagement</span><span class="sxs-lookup"><span data-stu-id="8d7b1-115">For systems running PowerShell 3 or PowerShell 4, that have installed the PackageManagement Preview</span></span>

1. <span data-ttu-id="8d7b1-116">À partir d’une session PowerShell avec élévation de privilèges, utilisez `Save-Module` pour enregistrer les modules dans un répertoire local.</span><span class="sxs-lookup"><span data-stu-id="8d7b1-116">From an elevated PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder
   Exit
   ```

1. <span data-ttu-id="8d7b1-117">Vérifiez que les modules **PowerShellGet** et **PackageManagement** ne sont pas chargés dans d’autres processus.</span><span class="sxs-lookup"><span data-stu-id="8d7b1-117">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="8d7b1-118">Supprimez le contenu des dossiers : `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` et `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="8d7b1-118">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="8d7b1-119">Ouvrez à nouveau la console PowerShell avec élévation de privilèges, puis exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="8d7b1-119">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```
