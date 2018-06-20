---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Modules avec des éditions PowerShell compatibles
ms.openlocfilehash: fbbfda2f913d54c3e69c0724fea4d977923279c1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189514"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="f4b9f-103">Modules avec des éditions PowerShell compatibles</span><span class="sxs-lookup"><span data-stu-id="f4b9f-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="f4b9f-104">À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent la compatibilité de la plateforme et les différents ensembles de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="f4b9f-105">**Desktop Edition :** basée sur le .NET Framework, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions complètes de Windows telles que Server Core et Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="f4b9f-106">**Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="the-running-edition-of-powershell-is-shown-in-the-psedition-property-of-psversiontable"></a><span data-ttu-id="f4b9f-107">L’édition de PowerShell exécutée est indiquée dans la propriété PSEdition de $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

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

## <a name="module-authors-can-declare-their-modules-to-be-compatible-with-one-or-more-powershell-editions-using-the-compatiblepseditions-module-manifest-key-this-key-is-only-supported-on-powershell-51-or-later"></a><span data-ttu-id="f4b9f-108">Les auteurs de modules peuvent déclarer leurs modules comme étant compatibles avec une ou plusieurs éditions de PowerShell en utilisant la clé de manifeste de module CompatiblePSEditions.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-108">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="f4b9f-109">Cette clé est prise en charge seulement sur PowerShell 5.1 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-109">This key is only supported on PowerShell 5.1 or later.</span></span>

<span data-ttu-id="f4b9f-110">*Remarque* : Une fois qu’un manifeste de module est spécifié avec la clé CompatiblePSEditions, il ne peut pas être importé sur des versions inférieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-110">*NOTE* Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on lower versions of PowerShell.</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
Desktop
Core

$ModuleInfo | Get-Member CompatiblePSEditions

   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}

```

<span data-ttu-id="f4b9f-111">Une fois que vous avez obtenu la liste des modules disponibles, vous pouvez la filtrer par édition de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-111">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

```powershell
Get-Module -ListAvailable -PSEdition Desktop

    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions

Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
Desktop
Core

```

## <a name="module-authors-can-publish-a-single-module-targeting-to-either-or-both-powershell-editions-desktop-and-core"></a><span data-ttu-id="f4b9f-112">Les auteurs de modules peuvent publier un même module ciblant une des deux éditions de PowerShell (Desktop et Core) ou les deux.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-112">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core)</span></span>

<span data-ttu-id="f4b9f-113">Un même module peut fonctionner à la fois sur les versions Desktop et Core : dans ce module, l’auteur doit ajouter la logique nécessaire dans RootModule ou dans le manifeste du module en utilisant la variable $PSEdition.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-113">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span>
<span data-ttu-id="f4b9f-114">Les modules peuvent avoir deux ensembles de DLL compilées ciblant à la fois CoreCLR et FullCLR.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-114">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span>
<span data-ttu-id="f4b9f-115">Voici les deux options pour empaqueter votre module avec la logique de chargement des DLL appropriées.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-115">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="f4b9f-116">Option 1 : Empaquetage d’un module pour cibler plusieurs versions et plusieurs éditions de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f4b9f-116">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

#### <a name="module-folder-contents"></a><span data-ttu-id="f4b9f-117">Contenu du dossier du module</span><span class="sxs-lookup"><span data-stu-id="f4b9f-117">Module folder contents</span></span>

- <span data-ttu-id="f4b9f-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="f4b9f-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="f4b9f-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="f4b9f-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="f4b9f-120">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="f4b9f-120">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="f4b9f-121">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="f4b9f-121">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="f4b9f-122">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="f4b9f-122">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="f4b9f-123">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="f4b9f-123">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="f4b9f-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="f4b9f-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="f4b9f-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="f4b9f-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="f4b9f-126">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="f4b9f-126">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="f4b9f-127">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="f4b9f-127">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="f4b9f-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="f4b9f-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="f4b9f-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="f4b9f-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="f4b9f-130">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="f4b9f-130">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="f4b9f-131">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="f4b9f-131">Settings\DSC.psd1</span></span>
- <span data-ttu-id="f4b9f-132">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="f4b9f-132">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="f4b9f-133">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="f4b9f-133">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="f4b9f-134">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="f4b9f-134">Settings\ScriptSecurity.psd1</span></span>

#### <a name="contents-of-psscriptanalyzerpsd1-file"></a><span data-ttu-id="f4b9f-135">Contenu du fichier PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="f4b9f-135">Contents of PSScriptAnalyzer.psd1 file</span></span>

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

#### <a name="contents-of-psscriptanalyzerpsm1-file"></a><span data-ttu-id="f4b9f-136">Contenu du fichier PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="f4b9f-136">Contents of PSScriptAnalyzer.psm1 file</span></span>

<span data-ttu-id="f4b9f-137">La logique ci-dessous charge les assemblys nécessaires en fonction de la version ou de l’édition actuelle.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-137">Below logic loads the required assemblies depending on the current edition or version.</span></span>

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0') {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}

```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="f4b9f-138">Option 2 : Utiliser la variable $PSEdition dans le fichier PSD1 pour charger les DLL appropriées et les modules imbriqués/obligatoires</span><span class="sxs-lookup"><span data-stu-id="f4b9f-138">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="f4b9f-139">Dans PowerShell 5.1 ou ultérieur, la variable globale $PSEdition est autorisée dans le fichier manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-139">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span>
<span data-ttu-id="f4b9f-140">En utilisant cette variable, l’auteur du module peut spécifier les valeurs conditionnelles dans le fichier manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-140">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="f4b9f-141">La variable $PSEdition peut être référencée en mode de langage restreint ou dans une section Data.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-141">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

<span data-ttu-id="f4b9f-142">*Remarque* : Une fois qu’un manifeste de module est spécifié avec la clé CompatiblePSEditions ou s’il utilise la variable $PSEdition, il ne peut pas être importé sur des versions inférieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-142">*NOTE* Once a module manifest is specified with the CompatiblePSEditions key or uses $PSEdition variable, it can not be imported on lower versions of PowerShell.</span></span>


#### <a name="sample-module-manifest-file-with-compatiblepseditions-key"></a><span data-ttu-id="f4b9f-143">Exemple de fichier manifeste de module avec la clé CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="f4b9f-143">Sample module manifest file with CompatiblePSEditions key</span></span>

```powershell
@{
# - - -

# Script module or binary module file associated with this manifest.
RootModule = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrRM.dll'
}
else # Desktop
{
'clr\MyFullClrRM.dll'
}

# Supported PSEditions
CompatiblePSEditions = 'Desktop', 'Core'

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrNM1.dll',
'coreclr\MyCoreClrNM2.dll'
}
else # Desktop
{
'clr\MyFullClrNM1.dll',
'clr\MyFullClrNM2.dll'
}

# -- - -
}
```

#### <a name="module-contents"></a><span data-ttu-id="f4b9f-144">Contenu du module</span><span class="sxs-lookup"><span data-stu-id="f4b9f-144">Module contents</span></span>

```powershell

PS C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions> dir -Recurse

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/5/2016   1:37 PM                clr
d-----         7/5/2016   1:36 PM                coreclr
-a----         7/5/2016   1:34 PM           4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         7/5/2016   1:35 PM              0 MyFullClrNM1.dll
-a----         7/5/2016   1:35 PM              0 MyFullClrNM2.dll
-a----         7/5/2016   1:35 PM              0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM1.dll
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM2.dll
-a----         7/5/2016   1:35 PM              0 MyCoreClrRM.dl
```

## <a name="powershell-gallery-users-can-find-the-list-of-modules-supported-on-a-specific-powershell-edition-using-tags-pseditiondesktop-and-pseditioncore"></a><span data-ttu-id="f4b9f-145">Les utilisateurs de PowerShell Gallery peuvent trouver la liste des modules pris en charge sur une édition spécifique de PowerShell en utilisant les étiquettes PSEdition_Desktop et PSEdition_Core.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-145">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="f4b9f-146">Les modules sans les étiquettes PSEdition_Desktop et PSEdition_Core sont considérés comme fonctionnant correctement sur les éditions de PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="f4b9f-146">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell

# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core

```


## <a name="more-details"></a><span data-ttu-id="f4b9f-147">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="f4b9f-147">More details</span></span>

- [<span data-ttu-id="f4b9f-148">Scripts avec des éditions PS</span><span class="sxs-lookup"><span data-stu-id="f4b9f-148">Scripts with PSEditions</span></span>](script-psedition-support.md)
- [<span data-ttu-id="f4b9f-149">Prise en charge des éditions PS sur PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="f4b9f-149">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-items/searching-by-psedition.md)
- <span data-ttu-id="f4b9f-150">[Mettre à jour le manifeste du module] (/powershell/module/powershellget/update-modulemanifest)</span><span class="sxs-lookup"><span data-stu-id="f4b9f-150">[Update module manifest] (/powershell/module/powershellget/update-modulemanifest)</span></span>