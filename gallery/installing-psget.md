---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Installation de PowerShellGet
ms.openlocfilehash: 23a53a9117c9f6a7ad157b635cd7ff4b3b3444c5
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054821"
---
# <a name="installing-powershellget"></a><span data-ttu-id="11a13-103">Installation de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="11a13-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="11a13-104">PowerShellGet est un module inclus par défaut dans les versions suivantes</span><span class="sxs-lookup"><span data-stu-id="11a13-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="11a13-105">[Windows 10](https://www.microsoft.com/windows) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="11a13-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="11a13-106">[Windows Server 2016](/windows-server/windows-server) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="11a13-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="11a13-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="11a13-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="11a13-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="11a13-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="11a13-109">Obtenir le module PowerShellGet pour les versions PowerShell 3.0 et 4.0</span><span class="sxs-lookup"><span data-stu-id="11a13-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="11a13-110">PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="11a13-110">PackageManagement MSI</span></span>](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="11a13-111">Obtenir la dernière version de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="11a13-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="11a13-112">Avant d’effectuer la mise à jour de PowerShellGet, vous devez toujours installer le dernier fournisseur Nuget.</span><span class="sxs-lookup"><span data-stu-id="11a13-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="11a13-113">Pour ce faire, exécutez la commande suivante dans une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="11a13-113">To do that, run the following in an elevated PowerShell session.</span></span>

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="11a13-114">Pour les systèmes avec PowerShell 5.0 (ou version ultérieure), vous pouvez installer la dernière version de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="11a13-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="11a13-115">Pour effectuer cette opération sous Windows 10, Windows Server 2016, tout système équipé de WMF 5.0 ou 5.1, ou tout système équipé de PowerShell 6, exécutez les commandes suivantes à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="11a13-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- <span data-ttu-id="11a13-116">Utilisez `Update-Module` pour obtenir des versions plus récentes.</span><span class="sxs-lookup"><span data-stu-id="11a13-116">Use `Update-Module` to get newer versions.</span></span>

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a><span data-ttu-id="11a13-117">Pour les systèmes exécutant PowerShell 3 ou PowerShell 4 et qui ont installé [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span><span class="sxs-lookup"><span data-stu-id="11a13-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span></span>

- <span data-ttu-id="11a13-118">Utilisez l’applet de commande PowerShellGet ci-dessous à partir d’une session PowerShell avec élévation de privilèges pour enregistrer les modules dans un répertoire local</span><span class="sxs-lookup"><span data-stu-id="11a13-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- <span data-ttu-id="11a13-119">Vérifiez que les modules PowerShellGet et PackageManagement ne sont pas chargés dans d’autres processus.</span><span class="sxs-lookup"><span data-stu-id="11a13-119">Ensure that PowerShellGet and PackageManagement modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="11a13-120">Supprimez le contenu des dossiers `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` et `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="11a13-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="11a13-121">Ouvrez à nouveau la Console PS avec élévation de privilèges, puis exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="11a13-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
