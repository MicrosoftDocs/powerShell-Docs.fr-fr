---
ms.date: 06/10/2020
title: Modules avec des éditions PowerShell compatibles
description: Cet article explique comment les applets de commande PowerShellGet prennent en charge les éditions Desktop et Core des modules PowerShell.
ms.openlocfilehash: 530101590cf83a1f43cbb9ce32d07a7e0ec79253
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661491"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="8b36a-103">Modules avec des éditions PowerShell compatibles</span><span class="sxs-lookup"><span data-stu-id="8b36a-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="8b36a-104">À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent la compatibilité de la plateforme et les différents ensembles de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="8b36a-104">Starting with version 5.1, PowerShell is available in different editions, which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="8b36a-105">**Édition Desktop :** Basée sur .NET Framework, s’applique à Windows PowerShell v4.0 et aux versions antérieures, ainsi qu’à Windows PowerShell 5.1 sur Windows Desktop, Windows Server, Windows Server Core et la plupart des autres éditions de Windows.</span><span class="sxs-lookup"><span data-stu-id="8b36a-105">**Desktop Edition:** Built on .NET Framework, applies to Windows PowerShell v4.0 and below as well as Windows PowerShell 5.1 on Windows Desktop, Windows Server, Windows Server Core and most other Windows editions.</span></span>
- <span data-ttu-id="8b36a-106">**Core Edition :** Basée sur .NET Core, s’applique à PowerShell Core 6.0 et aux versions ultérieures, ainsi qu’à Windows PowerShell 5.1 sur des éditions de Windows à empreinte réduite, telles que Windows IoT et Windows Nanoserver.</span><span class="sxs-lookup"><span data-stu-id="8b36a-106">**Core Edition:** Built on .NET Core, applies to PowerShell Core 6.0 and above as well as Windows PowerShell 5.1 on reduced footprint Windows Editions such as Windows IoT and Windows Nanoserver.</span></span>

<span data-ttu-id="8b36a-107">Pour plus d’informations sur les éditions de PowerShell, consultez [about_PowerShell_Editions][].</span><span class="sxs-lookup"><span data-stu-id="8b36a-107">For more information on PowerShell editions, see [about_PowerShell_Editions][].</span></span>

## <a name="declaring-compatible-editions"></a><span data-ttu-id="8b36a-108">Déclaration d’éditions compatibles</span><span class="sxs-lookup"><span data-stu-id="8b36a-108">Declaring compatible editions</span></span>

<span data-ttu-id="8b36a-109">Les auteurs de modules peuvent déclarer leurs modules comme étant compatibles avec une ou plusieurs éditions de PowerShell en utilisant la clé de manifeste de module `CompatiblePSEditions`.</span><span class="sxs-lookup"><span data-stu-id="8b36a-109">Module authors can declare their modules to be compatible with one or more PowerShell editions using the `CompatiblePSEditions` module manifest key.</span></span> <span data-ttu-id="8b36a-110">Cette clé est prise en charge seulement sur PowerShell 5.1 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="8b36a-110">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="8b36a-111">Une fois qu’un manifeste de module est spécifié avec la clé `CompatiblePSEditions` ou qu’il utilise la variable `$PSEdition`, il ne peut pas être importé sur PowerShell v4 ou version antérieure.</span><span class="sxs-lookup"><span data-stu-id="8b36a-111">Once a module manifest is specified with the `CompatiblePSEditions` key or uses the `$PSEdition` variable, it can not be imported on PowerShell v4 or lower.</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```Output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

<span data-ttu-id="8b36a-112">Une fois que vous avez obtenu la liste des modules disponibles, vous pouvez la filtrer par édition de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b36a-112">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules

ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```Output
Desktop
Core
```

<span data-ttu-id="8b36a-113">À compter de PowerShell 6, la valeur `CompatiblePSEditions` est utilisée pour déterminer si un module est compatible lorsque les modules sont importés à partir de `$env:windir\System32\WindowsPowerShell\v1.0\Modules`.</span><span class="sxs-lookup"><span data-stu-id="8b36a-113">Beginning in PowerShell 6, the `CompatiblePSEditions` value is used to decide if a module is compatible when modules are imported from `$env:windir\System32\WindowsPowerShell\v1.0\Modules`.</span></span>
<span data-ttu-id="8b36a-114">Ce comportement s’applique uniquement à Windows.</span><span class="sxs-lookup"><span data-stu-id="8b36a-114">This behavior only applies to Windows.</span></span> <span data-ttu-id="8b36a-115">En dehors de ce scénario, la valeur est utilisée uniquement en tant que métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8b36a-115">Outside of this scenario, the value is only used as metadata.</span></span>

## <a name="finding-compatible-modules"></a><span data-ttu-id="8b36a-116">Recherche de modules compatibles</span><span class="sxs-lookup"><span data-stu-id="8b36a-116">Finding compatible modules</span></span>

<span data-ttu-id="8b36a-117">Les utilisateurs de PowerShell Gallery peuvent trouver la liste des modules pris en charge sur une édition spécifique de PowerShell en utilisant les étiquettes **PSEdition_Desktop** et **PSEdition_Core**.</span><span class="sxs-lookup"><span data-stu-id="8b36a-117">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags **PSEdition_Desktop** and **PSEdition_Core**.</span></span>

<span data-ttu-id="8b36a-118">Les modules sans les étiquettes **PSEdition_Desktop** et **PSEdition_Core** sont considérés comme fonctionnant correctement sur les éditions de PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="8b36a-118">Modules without **PSEdition_Desktop** and **PSEdition_Core** tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="targeting-multiple-editions"></a><span data-ttu-id="8b36a-119">Ciblage de plusieurs éditions</span><span class="sxs-lookup"><span data-stu-id="8b36a-119">Targeting multiple editions</span></span>

<span data-ttu-id="8b36a-120">Les auteurs de modules peuvent publier un même module ciblant une des deux éditions de PowerShell (Desktop et Core) ou les deux.</span><span class="sxs-lookup"><span data-stu-id="8b36a-120">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core).</span></span>

<span data-ttu-id="8b36a-121">Un même module peut fonctionner à la fois sur les versions Desktop et Core : dans ce module, l’auteur doit ajouter la logique nécessaire dans RootModule ou dans le manifeste du module en utilisant la variable `$PSEdition`.</span><span class="sxs-lookup"><span data-stu-id="8b36a-121">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using `$PSEdition` variable.</span></span> <span data-ttu-id="8b36a-122">Les modules peuvent avoir deux ensembles de DLL compilées ciblant à la fois **CoreCLR** et **FullCLR**.</span><span class="sxs-lookup"><span data-stu-id="8b36a-122">Modules can have two sets of compiled DLLs targeting both **CoreCLR** and **FullCLR**.</span></span> <span data-ttu-id="8b36a-123">Voici les options d’empaquetage avec la logique de chargement des DLL appropriées.</span><span class="sxs-lookup"><span data-stu-id="8b36a-123">Here are the packaging options with logic for loading proper DLLs.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="8b36a-124">Option 1 : Empaquetage d’un module pour cibler plusieurs versions et plusieurs éditions de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b36a-124">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

<span data-ttu-id="8b36a-125">Contenu du dossier du module</span><span class="sxs-lookup"><span data-stu-id="8b36a-125">Module folder contents</span></span>

- <span data-ttu-id="8b36a-126">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="8b36a-126">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="8b36a-127">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="8b36a-127">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="8b36a-128">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="8b36a-128">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="8b36a-129">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="8b36a-129">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="8b36a-130">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="8b36a-130">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="8b36a-131">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="8b36a-131">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="8b36a-132">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="8b36a-132">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="8b36a-133">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="8b36a-133">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="8b36a-134">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="8b36a-134">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="8b36a-135">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="8b36a-135">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="8b36a-136">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="8b36a-136">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="8b36a-137">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="8b36a-137">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="8b36a-138">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="8b36a-138">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="8b36a-139">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="8b36a-139">Settings\DSC.psd1</span></span>
- <span data-ttu-id="8b36a-140">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="8b36a-140">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="8b36a-141">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="8b36a-141">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="8b36a-142">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="8b36a-142">Settings\ScriptSecurity.psd1</span></span>

<span data-ttu-id="8b36a-143">Contenu du fichier `PSScriptAnalyzer.psd1`</span><span class="sxs-lookup"><span data-stu-id="8b36a-143">Contents of `PSScriptAnalyzer.psd1` file</span></span>

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

<span data-ttu-id="8b36a-144">La logique ci-dessous charge les assemblys nécessaires en fonction de la version ou de l’édition actuelle.</span><span class="sxs-lookup"><span data-stu-id="8b36a-144">Below logic loads the required assemblies depending on the current edition or version.</span></span>

<span data-ttu-id="8b36a-145">Contenu du fichier `PSScriptAnalyzer.psm1` :</span><span class="sxs-lookup"><span data-stu-id="8b36a-145">Contents of `PSScriptAnalyzer.psm1` file:</span></span>

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
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
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

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls"></a><span data-ttu-id="8b36a-146">Option n°2 : Utilisation de la variable $PSEdition dans le fichier PSD1 pour charger les DLL appropriées</span><span class="sxs-lookup"><span data-stu-id="8b36a-146">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs</span></span>

<span data-ttu-id="8b36a-147">Dans PowerShell 5.1 ou ultérieur, la variable globale `$PSEdition` est autorisée dans le fichier manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="8b36a-147">In PS 5.1 or newer, `$PSEdition` global variable is allowed in the module manifest file.</span></span> <span data-ttu-id="8b36a-148">En utilisant cette variable, l’auteur du module peut spécifier les valeurs conditionnelles dans le fichier manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="8b36a-148">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="8b36a-149">La variable `$PSEdition` peut être référencée en mode de langage restreint ou dans une section Data.</span><span class="sxs-lookup"><span data-stu-id="8b36a-149">`$PSEdition` variable can be referenced in restricted language mode or a Data section.</span></span>

<span data-ttu-id="8b36a-150">Exemple de fichier manifeste de module avec une clé `CompatiblePSEditions`.</span><span class="sxs-lookup"><span data-stu-id="8b36a-150">Sample module manifest file with `CompatiblePSEditions` key.</span></span>

```powershell
@{
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
}
```

<span data-ttu-id="8b36a-151">Contenu du module</span><span class="sxs-lookup"><span data-stu-id="8b36a-151">Module contents</span></span>

- <span data-ttu-id="8b36a-152">ModuleWithEditions\ModuleWithEditions.psd1</span><span class="sxs-lookup"><span data-stu-id="8b36a-152">ModuleWithEditions\ModuleWithEditions.psd1</span></span>
- <span data-ttu-id="8b36a-153">ModuleWithEditions\clr\MyFullClrNM1.dll</span><span class="sxs-lookup"><span data-stu-id="8b36a-153">ModuleWithEditions\clr\MyFullClrNM1.dll</span></span>
- <span data-ttu-id="8b36a-154">ModuleWithEditions\clr\MyFullClrNM2.dll</span><span class="sxs-lookup"><span data-stu-id="8b36a-154">ModuleWithEditions\clr\MyFullClrNM2.dll</span></span>
- <span data-ttu-id="8b36a-155">ModuleWithEditions\clr\MyFullClrRM.dll</span><span class="sxs-lookup"><span data-stu-id="8b36a-155">ModuleWithEditions\clr\MyFullClrRM.dll</span></span>
- <span data-ttu-id="8b36a-156">ModuleWithEditions\coreclr\MyCoreClrNM1.dll</span><span class="sxs-lookup"><span data-stu-id="8b36a-156">ModuleWithEditions\coreclr\MyCoreClrNM1.dll</span></span>
- <span data-ttu-id="8b36a-157">ModuleWithEditions\coreclr\MyCoreClrNM2.dll</span><span class="sxs-lookup"><span data-stu-id="8b36a-157">ModuleWithEditions\coreclr\MyCoreClrNM2.dll</span></span>
- <span data-ttu-id="8b36a-158">ModuleWithEditions\coreclr\MyCoreClrRM.dll</span><span class="sxs-lookup"><span data-stu-id="8b36a-158">ModuleWithEditions\coreclr\MyCoreClrRM.dll</span></span>

## <a name="more-details"></a><span data-ttu-id="8b36a-159">Détails supplémentaires</span><span class="sxs-lookup"><span data-stu-id="8b36a-159">More details</span></span>

[<span data-ttu-id="8b36a-160">Scripts avec des éditions PS</span><span class="sxs-lookup"><span data-stu-id="8b36a-160">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="8b36a-161">Prise en charge des éditions PS sur PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="8b36a-161">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)

[<span data-ttu-id="8b36a-162">Mettre à jour le manifeste du module</span><span class="sxs-lookup"><span data-stu-id="8b36a-162">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)

<span data-ttu-id="8b36a-163">[about_PowerShell_Editions][]</span><span class="sxs-lookup"><span data-stu-id="8b36a-163">[about_PowerShell_Editions][]</span></span>

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
