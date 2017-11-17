---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galerie,powershell,cmdlet,psget
title: Obtenir le module PowerShellGet
ms.openlocfilehash: a5a323b17709e519ec57623a9dd7499e591bbed5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a name="get-powershellget-module"></a><span data-ttu-id="f9da8-103">Obtenir le module PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="f9da8-103">Get PowerShellGet Module</span></span>
========================

### <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="f9da8-104">PowerShellGet est un module inclus par défaut dans les versions suivantes</span><span class="sxs-lookup"><span data-stu-id="f9da8-104">PowerShellGet is an in-box module in the following releases</span></span>
- <span data-ttu-id="f9da8-105">[Windows 10](https://www.microsoft.com/en-us/windows/get-windows-10) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="f9da8-105">[Windows 10](https://www.microsoft.com/en-us/windows/get-windows-10) or newer</span></span>
- <span data-ttu-id="f9da8-106">[Windows Server 2016](https://technet.microsoft.com/en-us/windows-server-docs/get-started/windows-server-2016) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="f9da8-106">[Windows Server 2016](https://technet.microsoft.com/en-us/windows-server-docs/get-started/windows-server-2016) or newer</span></span>
- <span data-ttu-id="f9da8-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="f9da8-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="f9da8-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="f9da8-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

### <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="f9da8-109">Obtenir le module PowerShellGet pour les versions PowerShell 3.0 et 4.0</span><span class="sxs-lookup"><span data-stu-id="f9da8-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>
- [<span data-ttu-id="f9da8-110">PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="f9da8-110">PackageManagement MSI</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) 

### <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="f9da8-111">Obtenir la dernière version de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="f9da8-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="f9da8-112">Avant d’effectuer la mise à jour de PowerShellGet, vous devez toujours installer le dernier fournisseur Nuget.</span><span class="sxs-lookup"><span data-stu-id="f9da8-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="f9da8-113">Pour ce faire, exécutez la commande suivante dans une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="f9da8-113">To do that, run the following in an elevated PowerShell session.</span></span>
```powershell
Install-PackageProvider Nuget –Force
Exit
```

#### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="f9da8-114">Pour les systèmes avec PowerShell 5.0 (ou version ultérieure), vous pouvez installer la dernière version de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="f9da8-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span> 
- <span data-ttu-id="f9da8-115">Pour effectuer cette opération sous Windows 10, Windows Server 2016, tout système équipé de WMF 5.0 ou 5.1, ou tout système équipé de PowerShell 6, exécutez les commandes suivantes à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="f9da8-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>
```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- <span data-ttu-id="f9da8-116">Utilisez Update-Module pour obtenir les versions plus récentes.</span><span class="sxs-lookup"><span data-stu-id="f9da8-116">Use Update-Module to get newer versions.</span></span>
```powershell
Update-Module -Name PowerShellGet
Exit
```

#### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a><span data-ttu-id="f9da8-117">Pour les systèmes exécutant PowerShell 3 ou PowerShell 4 et qui ont installé [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="f9da8-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span></span>

- <span data-ttu-id="f9da8-118">Utilisez l’applet de commande PowerShellGet ci-dessous à partir d’une session PowerShell avec élévation de privilèges pour enregistrer les modules dans un répertoire local</span><span class="sxs-lookup"><span data-stu-id="f9da8-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- <span data-ttu-id="f9da8-119">Assurez-vous que les modules PowerShellGet et PackageManagment ne sont pas chargés dans d’autres processus.</span><span class="sxs-lookup"><span data-stu-id="f9da8-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="f9da8-120">Supprimez le contenu des dossiers `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` et `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="f9da8-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="f9da8-121">Ouvrez à nouveau la Console PS avec élévation de privilèges, puis exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f9da8-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force