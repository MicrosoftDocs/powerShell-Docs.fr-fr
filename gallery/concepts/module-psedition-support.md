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
# <a name="modules-with-compatible-powershell-editions"></a>Modules avec des éditions PowerShell compatibles

À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent la compatibilité de la plateforme et les différents ensembles de fonctionnalités.

- Desktop Edition Basé sur .NET Framework et fournit une compatibilité avec les scripts et modules qui ciblent des versions de PowerShell exécutées sur les éditions complètes de Windows telles que Server Core et Windows Desktop.
- **Core Edition :** Basée sur .NET Core et assure la compatibilité avec les scripts et modules qui ciblent des versions de PowerShell exécutées sur des éditions à encombrement réduit de Windows telles que Nano Server et Windows IoT.

La version de PowerShell en cours d’exécution figure dans la propriété PSEdition de `$PSVersionTable`.

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

## <a name="declaring-compatible-editions"></a>Déclaration d’éditions compatibles

Les auteurs de modules peuvent déclarer leurs modules comme étant compatibles avec une ou plusieurs éditions de PowerShell en utilisant la clé de manifeste de module CompatiblePSEditions. Cette clé est prise en charge seulement sur PowerShell 5.1 ou ultérieur.

> [!NOTE]
> Une fois qu’un manifeste de module est spécifié avec la clé CompatiblePSEditions, il ne peut pas être importé sur des versions inférieures de PowerShell.

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

Une fois que vous avez obtenu la liste des modules disponibles, vous pouvez la filtrer par édition de PowerShell.

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

## <a name="targeting-multiple-editions"></a>Ciblage de plusieurs éditions

Les auteurs de modules peuvent publier un même module ciblant une des deux éditions de PowerShell (Desktop et Core) ou les deux.

Un même module peut fonctionner à la fois sur les versions Desktop et Core : dans ce module, l’auteur doit ajouter la logique nécessaire dans RootModule ou dans le manifeste du module en utilisant la variable $PSEdition. Les modules peuvent avoir deux ensembles de DLL compilées ciblant à la fois CoreCLR et FullCLR. Voici les deux options pour empaqueter votre module avec la logique de chargement des DLL appropriées.

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a>Option 1 : Empaquetage d’un module pour cibler plusieurs versions et plusieurs éditions de PowerShell

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

Contenu du fichier PSScriptAnalyzer.psd1

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

Contenu du fichier PSScriptAnalyzer.psm1 :

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

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a>Option 2 : Utiliser la variable $PSEdition dans le fichier PSD1 pour charger les DLL appropriées et les modules imbriqués/obligatoires

Dans PowerShell 5.1 ou ultérieur, la variable globale $PSEdition est autorisée dans le fichier manifeste du module. En utilisant cette variable, l’auteur du module peut spécifier les valeurs conditionnelles dans le fichier manifeste du module. La variable $PSEdition peut être référencée en mode de langage restreint ou dans une section Data.

> [!NOTE]
> Une fois qu’un manifeste de module est spécifié avec la clé CompatiblePSEditions, ou qu’il utilise la variable `$PSEdition`, il ne peut pas être importé sur des versions antérieures de PowerShell.

Exemple de fichier manifeste de module avec la clé CompatiblePSEditions

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

### <a name="module-contents"></a>Contenu du module

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

Les utilisateurs de PowerShell Gallery peuvent trouver la liste des modules pris en charge sur une édition spécifique de PowerShell en utilisant les étiquettes PSEdition_Desktop et PSEdition_Core.

Les modules sans les étiquettes PSEdition_Desktop et PSEdition_Core sont considérés comme fonctionnant correctement sur les éditions de PowerShell Desktop.

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a>Plus d’informations

[Scripts avec des éditions PS](script-psedition-support.md)

[Prise en charge des éditions PS sur PowerShellGallery](../how-to/finding-packages/searching-by-compatibility.md)

[Mettre à jour le manifeste du module](/powershell/module/powershellget/update-modulemanifest)
