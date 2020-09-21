---
ms.date: 06/10/2020
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Modules avec des éditions PowerShell compatibles
ms.openlocfilehash: 522493714916e9fd21f67a6e7bc2cfb165041807
ms.sourcegitcommit: 4a283fe5419f47102e6c1de7060880a934842ee9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84671408"
---
# <a name="modules-with-compatible-powershell-editions"></a>Modules avec des éditions PowerShell compatibles

À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent la compatibilité de la plateforme et les différents ensembles de fonctionnalités.

- **Édition Desktop :** Basée sur .NET Framework, s’applique à Windows PowerShell v4.0 et aux versions antérieures, ainsi qu’à Windows PowerShell 5.1 sur Windows Desktop, Windows Server, Windows Server Core et la plupart des autres éditions de Windows.
- **Core Edition :** Basée sur .NET Core, s’applique à PowerShell Core 6.0 et aux versions ultérieures, ainsi qu’à Windows PowerShell 5.1 sur des éditions de Windows à empreinte réduite, telles que Windows IoT et Windows Nanoserver.

Pour plus d’informations sur les éditions de PowerShell, consultez [about_PowerShell_Editions][].

## <a name="declaring-compatible-editions"></a>Déclaration d’éditions compatibles

Les auteurs de modules peuvent déclarer leurs modules comme étant compatibles avec une ou plusieurs éditions de PowerShell en utilisant la clé de manifeste de module `CompatiblePSEditions`. Cette clé est prise en charge seulement sur PowerShell 5.1 ou ultérieur.

> [!NOTE]
> Une fois qu’un manifeste de module est spécifié avec la clé `CompatiblePSEditions` ou qu’il utilise la variable `$PSEdition`, il ne peut pas être importé sur PowerShell v4 ou version antérieure.

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

Une fois que vous avez obtenu la liste des modules disponibles, vous pouvez la filtrer par édition de PowerShell.

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

À compter de PowerShell 6, la valeur `CompatiblePSEditions` est utilisée pour déterminer si un module est compatible lorsque les modules sont importés à partir de `$env:windir\System32\WindowsPowerShell\v1.0\Modules`.
Ce comportement s’applique uniquement à Windows. En dehors de ce scénario, la valeur est utilisée uniquement en tant que métadonnées.

## <a name="finding-compatible-modules"></a>Recherche de modules compatibles

Les utilisateurs de PowerShell Gallery peuvent trouver la liste des modules pris en charge sur une édition spécifique de PowerShell en utilisant les étiquettes **PSEdition_Desktop** et **PSEdition_Core**.

Les modules sans les étiquettes **PSEdition_Desktop** et **PSEdition_Core** sont considérés comme fonctionnant correctement sur les éditions de PowerShell Desktop.

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="targeting-multiple-editions"></a>Ciblage de plusieurs éditions

Les auteurs de modules peuvent publier un même module ciblant une des deux éditions de PowerShell (Desktop et Core) ou les deux.

Un même module peut fonctionner à la fois sur les versions Desktop et Core : dans ce module, l’auteur doit ajouter la logique nécessaire dans RootModule ou dans le manifeste du module en utilisant la variable `$PSEdition`. Les modules peuvent avoir deux ensembles de DLL compilées ciblant à la fois **CoreCLR** et **FullCLR**. Voici les options d’empaquetage avec la logique de chargement des DLL appropriées.

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a>Option 1 : Empaquetage d’un module pour cibler plusieurs versions et plusieurs éditions de PowerShell

Contenu du dossier du module

- Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- PSScriptAnalyzer.psd1
- PSScriptAnalyzer.psm1
- ScriptAnalyzer.format.ps1xml
- ScriptAnalyzer.types.ps1xml
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- en-US\about_PSScriptAnalyzer.help.txt
- en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- Settings\CmdletDesign.psd1
- Settings\DSC.psd1
- Settings\ScriptFunctions.psd1
- Settings\ScriptingStyle.psd1
- Settings\ScriptSecurity.psd1

Contenu du fichier `PSScriptAnalyzer.psd1`

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

La logique ci-dessous charge les assemblys nécessaires en fonction de la version ou de l’édition actuelle.

Contenu du fichier `PSScriptAnalyzer.psm1` :

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

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls"></a>Option n°2 : Utilisation de la variable $PSEdition dans le fichier PSD1 pour charger les DLL appropriées

Dans PowerShell 5.1 ou ultérieur, la variable globale `$PSEdition` est autorisée dans le fichier manifeste du module. En utilisant cette variable, l’auteur du module peut spécifier les valeurs conditionnelles dans le fichier manifeste du module. La variable `$PSEdition` peut être référencée en mode de langage restreint ou dans une section Data.

Exemple de fichier manifeste de module avec une clé `CompatiblePSEditions`.

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

Contenu du module

- ModuleWithEditions\ModuleWithEditions.psd1
- ModuleWithEditions\clr\MyFullClrNM1.dll
- ModuleWithEditions\clr\MyFullClrNM2.dll
- ModuleWithEditions\clr\MyFullClrRM.dll
- ModuleWithEditions\coreclr\MyCoreClrNM1.dll
- ModuleWithEditions\coreclr\MyCoreClrNM2.dll
- ModuleWithEditions\coreclr\MyCoreClrRM.dll

## <a name="more-details"></a>Détails supplémentaires

[Scripts avec des éditions PS](script-psedition-support.md)

[Prise en charge des éditions PS sur PowerShellGallery](../how-to/finding-packages/searching-by-compatibility.md)

[Mettre à jour le manifeste du module](/powershell/module/powershellget/update-modulemanifest)

[about_PowerShell_Editions][]

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
