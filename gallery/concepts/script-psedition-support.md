---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Écrire des scripts avec des éditions de PowerShell compatibles
ms.openlocfilehash: e364879f611429a8583e550fb7704431e456fbb1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678624"
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="27383-103">Écrire des scripts avec des éditions de PowerShell compatibles</span><span class="sxs-lookup"><span data-stu-id="27383-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="27383-104">À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent la compatibilité de la plateforme et les différents ensembles de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="27383-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="27383-105">**Desktop Edition :** basée sur le .NET Framework, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions complètes de Windows telles que Server Core et Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="27383-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>

- <span data-ttu-id="27383-106">**Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="27383-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="27383-107">La version de PowerShell en cours d’exécution figure dans la propriété PSEdition de $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="27383-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="27383-108">Les auteurs de scripts peuvent empêcher l’exécution d’un script, sauf s’il est exécuté dans une édition compatible de PowerShell avec le paramètre PSEdition sur une instruction `#requires`.</span><span class="sxs-lookup"><span data-stu-id="27383-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a `#requires` statement.</span></span>

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell editions 'Core'. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

<span data-ttu-id="27383-109">Les utilisateurs de PowerShell Gallery peuvent trouver la liste des scripts pris en charge sur une édition spécifique de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27383-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="27383-110">Les scripts sans les étiquettes PSEdition_Desktop et PSEdition_Core sont considérés comme fonctionnant correctement sur l’édition de PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="27383-110">Scripts without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop edition.</span></span>

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="27383-111">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="27383-111">More details</span></span>

- [<span data-ttu-id="27383-112">Modules avec des éditions PS</span><span class="sxs-lookup"><span data-stu-id="27383-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="27383-113">Prise en charge des éditions PS sur PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="27383-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)
