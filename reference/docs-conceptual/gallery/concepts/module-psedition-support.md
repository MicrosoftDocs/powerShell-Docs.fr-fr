---
ms.date: 03/28/2019
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Modules avec des éditions PowerShell compatibles
ms.openlocfilehash: 425588c168a4f864fdc0c52aa53cfd748b80dc98
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328500"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="b1ad0-103">Modules avec des éditions PowerShell compatibles</span><span class="sxs-lookup"><span data-stu-id="b1ad0-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="b1ad0-104">À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent la compatibilité de la plateforme et les différents ensembles de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="b1ad0-105">**Édition Desktop :** Basée sur .NET Framework, s’applique à Windows PowerShell v4.0 et aux versions antérieures, ainsi qu’à Windows PowerShell 5.1 sur Windows Desktop, Windows Server, Windows Server Core et la plupart des autres éditions de Windows.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-105">**Desktop Edition:** Built on .NET Framework, applies to Windows PowerShell v4.0 and below as well as Windows PowerShell 5.1 on Windows Desktop, Windows Server, Windows Server Core and most other Windows editions.</span></span>
- <span data-ttu-id="b1ad0-106">**Core Edition :** Basée sur .NET Core, s’applique à PowerShell Core 6.0 et aux versions ultérieures, ainsi qu’à Windows PowerShell 5.1 sur des éditions de Windows à empreinte réduite, telles que Windows IoT et Windows Nanoserver.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-106">**Core Edition:** Built on .NET Core, applies to PowerShell Core 6.0 and above as well as Windows PowerShell 5.1 on reduced footprint Windows Editions such as Windows IoT and Windows Nanoserver.</span></span>

<span data-ttu-id="b1ad0-107">Pour plus d’informations sur les éditions de PowerShell, consultez [about_PowerShell_Editions][].</span><span class="sxs-lookup"><span data-stu-id="b1ad0-107">For more information on PowerShell editions, see [about_PowerShell_Editions][].</span></span>

## <a name="declaring-compatible-editions"></a><span data-ttu-id="b1ad0-108">Déclaration d’éditions compatibles</span><span class="sxs-lookup"><span data-stu-id="b1ad0-108">Declaring compatible editions</span></span>

<span data-ttu-id="b1ad0-109">Les auteurs de modules peuvent déclarer leurs modules comme étant compatibles avec une ou plusieurs éditions de PowerShell en utilisant la clé de manifeste de module CompatiblePSEditions.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-109">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="b1ad0-110">Cette clé est prise en charge seulement sur PowerShell 5.1 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-110">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="b1ad0-111">Une fois qu’un manifeste de module est spécifié avec la clé CompatiblePSEditions, il ne peut pas être importé sur PowerShell 4 et des versions inférieures.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-111">Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on PowerShell versions 4 and below.</span></span>

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

<span data-ttu-id="b1ad0-112">Une fois que vous avez obtenu la liste des modules disponibles, vous pouvez la filtrer par édition de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-112">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

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

## <a name="targeting-multiple-editions"></a><span data-ttu-id="b1ad0-113">Ciblage de plusieurs éditions</span><span class="sxs-lookup"><span data-stu-id="b1ad0-113">Targeting multiple editions</span></span>

<span data-ttu-id="b1ad0-114">Les auteurs de modules peuvent publier un même module ciblant une des deux éditions de PowerShell (Desktop et Core) ou les deux.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-114">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core).</span></span>

<span data-ttu-id="b1ad0-115">Un même module peut fonctionner à la fois sur les versions Desktop et Core : dans ce module, l’auteur doit ajouter la logique nécessaire dans RootModule ou dans le manifeste du module en utilisant la variable $PSEdition.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-115">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span> <span data-ttu-id="b1ad0-116">Les modules peuvent avoir deux ensembles de DLL compilées ciblant à la fois CoreCLR et FullCLR.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-116">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span> <span data-ttu-id="b1ad0-117">Voici les deux options pour empaqueter votre module avec la logique de chargement des DLL appropriées.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-117">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="b1ad0-118">Option 1 : empaquetage d’un module pour cibler plusieurs versions et plusieurs éditions de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b1ad0-118">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

<span data-ttu-id="b1ad0-119">Contenu du dossier du module</span><span class="sxs-lookup"><span data-stu-id="b1ad0-119">Module folder contents</span></span>

- <span data-ttu-id="b1ad0-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="b1ad0-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="b1ad0-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="b1ad0-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="b1ad0-122">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="b1ad0-122">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="b1ad0-123">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="b1ad0-123">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="b1ad0-124">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="b1ad0-124">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="b1ad0-125">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="b1ad0-125">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="b1ad0-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="b1ad0-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="b1ad0-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="b1ad0-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="b1ad0-128">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="b1ad0-128">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="b1ad0-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="b1ad0-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="b1ad0-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="b1ad0-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="b1ad0-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="b1ad0-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="b1ad0-132">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="b1ad0-132">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="b1ad0-133">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="b1ad0-133">Settings\DSC.psd1</span></span>
- <span data-ttu-id="b1ad0-134">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="b1ad0-134">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="b1ad0-135">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="b1ad0-135">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="b1ad0-136">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="b1ad0-136">Settings\ScriptSecurity.psd1</span></span>

<span data-ttu-id="b1ad0-137">Contenu du fichier PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="b1ad0-137">Contents of PSScriptAnalyzer.psd1 file</span></span>

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

<span data-ttu-id="b1ad0-138">La logique ci-dessous charge les assemblys nécessaires en fonction de la version ou de l’édition actuelle.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-138">Below logic loads the required assemblies depending on the current edition or version.</span></span>

<span data-ttu-id="b1ad0-139">Contenu du fichier PSScriptAnalyzer.psm1 :</span><span class="sxs-lookup"><span data-stu-id="b1ad0-139">Contents of PSScriptAnalyzer.psm1 file:</span></span>

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

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="b1ad0-140">Option 2 : utiliser la variable $PSEdition dans le fichier PSD1 pour charger les DLL appropriées et les modules imbriqués/obligatoires</span><span class="sxs-lookup"><span data-stu-id="b1ad0-140">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="b1ad0-141">Dans PowerShell 5.1 ou ultérieur, la variable globale $PSEdition est autorisée dans le fichier manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-141">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span> <span data-ttu-id="b1ad0-142">En utilisant cette variable, l’auteur du module peut spécifier les valeurs conditionnelles dans le fichier manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-142">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="b1ad0-143">La variable $PSEdition peut être référencée en mode de langage restreint ou dans une section Data.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-143">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

> [!NOTE]
> <span data-ttu-id="b1ad0-144">Une fois qu’un manifeste de module est spécifié avec la clé CompatiblePSEditions, ou qu’il utilise la variable `$PSEdition`, il ne peut pas être importé sur des versions antérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-144">Once a module manifest is specified with the CompatiblePSEditions key or uses `$PSEdition` variable, it can not be imported on lower versions of PowerShell.</span></span>

<span data-ttu-id="b1ad0-145">Exemple de fichier manifeste de module avec la clé CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="b1ad0-145">Sample module manifest file with CompatiblePSEditions key</span></span>

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

### <a name="module-contents"></a><span data-ttu-id="b1ad0-146">Contenu du module</span><span class="sxs-lookup"><span data-stu-id="b1ad0-146">Module contents</span></span>

```powershell
dir -Recurse
```

```Output
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

<span data-ttu-id="b1ad0-147">Les utilisateurs de PowerShell Gallery peuvent trouver la liste des modules pris en charge sur une édition spécifique de PowerShell en utilisant les étiquettes PSEdition_Desktop et PSEdition_Core.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-147">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="b1ad0-148">Les modules sans les étiquettes PSEdition_Desktop et PSEdition_Core sont considérés comme fonctionnant correctement sur les éditions de PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="b1ad0-148">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="b1ad0-149">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="b1ad0-149">More details</span></span>

[<span data-ttu-id="b1ad0-150">Scripts avec des éditions PS</span><span class="sxs-lookup"><span data-stu-id="b1ad0-150">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="b1ad0-151">Prise en charge des éditions PS sur PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="b1ad0-151">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)

[<span data-ttu-id="b1ad0-152">Mettre à jour le manifeste du module</span><span class="sxs-lookup"><span data-stu-id="b1ad0-152">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)

<span data-ttu-id="b1ad0-153">[about_PowerShell_Editions][]</span><span class="sxs-lookup"><span data-stu-id="b1ad0-153">[about_PowerShell_Editions][]</span></span>

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
