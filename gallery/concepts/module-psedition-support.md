---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Modules avec des éditions PowerShell compatibles
ms.openlocfilehash: bda924393d37ea1596fbf0d813c10cbdea33c218
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655325"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="b49fb-103">Modules avec des éditions PowerShell compatibles</span><span class="sxs-lookup"><span data-stu-id="b49fb-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="b49fb-104">À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent la compatibilité de la plateforme et les différents ensembles de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="b49fb-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="b49fb-105">Desktop Edition Basé sur .NET Framework et fournit une compatibilité avec les scripts et modules qui ciblent des versions de PowerShell exécutées sur les éditions complètes de Windows telles que Server Core et Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="b49fb-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="b49fb-106">**Core Edition :** Basée sur .NET Core et assure la compatibilité avec les scripts et modules qui ciblent des versions de PowerShell exécutées sur des éditions à encombrement réduit de Windows telles que Nano Server et Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="b49fb-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="b49fb-107">La version de PowerShell en cours d’exécution figure dans la propriété PSEdition de `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="b49fb-107">The running edition of PowerShell is shown in the PSEdition property of `$PSVersionTable`.</span></span>

```powershell
$PSVersionTable
```

```output
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

## <a name="declaring-compatible-editions"></a><span data-ttu-id="b49fb-108">Déclaration d’éditions compatibles</span><span class="sxs-lookup"><span data-stu-id="b49fb-108">Declaring compatible editions</span></span>

<span data-ttu-id="b49fb-109">Les auteurs de modules peuvent déclarer leurs modules comme étant compatibles avec une ou plusieurs éditions de PowerShell en utilisant la clé de manifeste de module CompatiblePSEditions.</span><span class="sxs-lookup"><span data-stu-id="b49fb-109">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="b49fb-110">Cette clé est prise en charge seulement sur PowerShell 5.1 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="b49fb-110">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="b49fb-111">Une fois qu’un manifeste de module est spécifié avec la clé CompatiblePSEditions, il ne peut pas être importé sur des versions inférieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b49fb-111">Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on lower versions of PowerShell.</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

<span data-ttu-id="b49fb-112">Une fois que vous avez obtenu la liste des modules disponibles, vous pouvez la filtrer par édition de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b49fb-112">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```output
    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```output
Desktop
Core
```

## <a name="targeting-multiple-editions"></a><span data-ttu-id="b49fb-113">Ciblage de plusieurs éditions</span><span class="sxs-lookup"><span data-stu-id="b49fb-113">Targeting multiple editions</span></span>

<span data-ttu-id="b49fb-114">Les auteurs de modules peuvent publier un même module ciblant une des deux éditions de PowerShell (Desktop et Core) ou les deux.</span><span class="sxs-lookup"><span data-stu-id="b49fb-114">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core).</span></span>

<span data-ttu-id="b49fb-115">Un même module peut fonctionner à la fois sur les versions Desktop et Core : dans ce module, l’auteur doit ajouter la logique nécessaire dans RootModule ou dans le manifeste du module en utilisant la variable $PSEdition.</span><span class="sxs-lookup"><span data-stu-id="b49fb-115">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span> <span data-ttu-id="b49fb-116">Les modules peuvent avoir deux ensembles de DLL compilées ciblant à la fois CoreCLR et FullCLR.</span><span class="sxs-lookup"><span data-stu-id="b49fb-116">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span> <span data-ttu-id="b49fb-117">Voici les deux options pour empaqueter votre module avec la logique de chargement des DLL appropriées.</span><span class="sxs-lookup"><span data-stu-id="b49fb-117">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="b49fb-118">Option 1 : Empaquetage d’un module pour cibler plusieurs versions et plusieurs éditions de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b49fb-118">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

<span data-ttu-id="b49fb-119">Contenu du dossier du module</span><span class="sxs-lookup"><span data-stu-id="b49fb-119">Module folder contents</span></span>

- <span data-ttu-id="b49fb-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="b49fb-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="b49fb-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="b49fb-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="b49fb-122">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="b49fb-122">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="b49fb-123">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="b49fb-123">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="b49fb-124">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="b49fb-124">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="b49fb-125">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="b49fb-125">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="b49fb-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="b49fb-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="b49fb-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="b49fb-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="b49fb-128">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="b49fb-128">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="b49fb-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="b49fb-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="b49fb-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="b49fb-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="b49fb-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="b49fb-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="b49fb-132">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="b49fb-132">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="b49fb-133">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="b49fb-133">Settings\DSC.psd1</span></span>
- <span data-ttu-id="b49fb-134">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="b49fb-134">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="b49fb-135">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="b49fb-135">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="b49fb-136">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="b49fb-136">Settings\ScriptSecurity.psd1</span></span>

<span data-ttu-id="b49fb-137">Contenu du fichier PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="b49fb-137">Contents of PSScriptAnalyzer.psd1 file</span></span>

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

<span data-ttu-id="b49fb-138">La logique ci-dessous charge les assemblys nécessaires en fonction de la version ou de l’édition actuelle.</span><span class="sxs-lookup"><span data-stu-id="b49fb-138">Below logic loads the required assemblies depending on the current edition or version.</span></span>

<span data-ttu-id="b49fb-139">Contenu du fichier PSScriptAnalyzer.psm1 :</span><span class="sxs-lookup"><span data-stu-id="b49fb-139">Contents of PSScriptAnalyzer.psm1 file:</span></span>

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="b49fb-140">Option 2 : Utiliser la variable $PSEdition dans le fichier PSD1 pour charger les DLL appropriées et les modules imbriqués/obligatoires</span><span class="sxs-lookup"><span data-stu-id="b49fb-140">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="b49fb-141">Dans PowerShell 5.1 ou ultérieur, la variable globale $PSEdition est autorisée dans le fichier manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="b49fb-141">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span> <span data-ttu-id="b49fb-142">En utilisant cette variable, l’auteur du module peut spécifier les valeurs conditionnelles dans le fichier manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="b49fb-142">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="b49fb-143">La variable $PSEdition peut être référencée en mode de langage restreint ou dans une section Data.</span><span class="sxs-lookup"><span data-stu-id="b49fb-143">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

> [!NOTE]
> <span data-ttu-id="b49fb-144">Une fois qu’un manifeste de module est spécifié avec la clé CompatiblePSEditions, ou qu’il utilise la variable `$PSEdition`, il ne peut pas être importé sur des versions antérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b49fb-144">Once a module manifest is specified with the CompatiblePSEditions key or uses `$PSEdition` variable, it can not be imported on lower versions of PowerShell.</span></span>

<span data-ttu-id="b49fb-145">Exemple de fichier manifeste de module avec la clé CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="b49fb-145">Sample module manifest file with CompatiblePSEditions key</span></span>

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

### <a name="module-contents"></a><span data-ttu-id="b49fb-146">Contenu du module</span><span class="sxs-lookup"><span data-stu-id="b49fb-146">Module contents</span></span>

```powershell
dir -Recurse
```

```output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
d-----    7/5/2016   1:37 PM          clr
d-----    7/5/2016   1:36 PM          coreclr
-a----    7/5/2016   1:34 PM     4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode           LastWriteTime    Length Name
----           -------------    ------ ----
-a----    7/5/2016   1:35 PM         0 MyFullClrNM1.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrNM2.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM1.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM2.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrRM.dl
```

<span data-ttu-id="b49fb-147">Les utilisateurs de PowerShell Gallery peuvent trouver la liste des modules pris en charge sur une édition spécifique de PowerShell en utilisant les étiquettes PSEdition_Desktop et PSEdition_Core.</span><span class="sxs-lookup"><span data-stu-id="b49fb-147">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="b49fb-148">Les modules sans les étiquettes PSEdition_Desktop et PSEdition_Core sont considérés comme fonctionnant correctement sur les éditions de PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="b49fb-148">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="b49fb-149">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="b49fb-149">More details</span></span>

[<span data-ttu-id="b49fb-150">Scripts avec des éditions PS</span><span class="sxs-lookup"><span data-stu-id="b49fb-150">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="b49fb-151">Prise en charge des éditions PS sur PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="b49fb-151">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)

[<span data-ttu-id="b49fb-152">Mettre à jour le manifeste du module</span><span class="sxs-lookup"><span data-stu-id="b49fb-152">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)
