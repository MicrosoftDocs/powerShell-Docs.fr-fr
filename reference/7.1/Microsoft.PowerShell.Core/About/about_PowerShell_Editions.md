---
description: Les différentes éditions de PowerShell s’exécutent sur des runtimes sous-jacents différents.
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_editions?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Editions
ms.openlocfilehash: 63ee3fffb4d7594920fa7052aecee99aa01ddc7d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207285"
---
# <a name="about-powershell-editions"></a>À propos des éditions de PowerShell

## <a name="short-description"></a>Description courte
Les différentes éditions de PowerShell s’exécutent sur des runtimes sous-jacents différents.

## <a name="long-description"></a>Description longue

À partir de PowerShell 5,1, plusieurs *éditions* de PowerShell s’exécutent sur un autre Runtime .net. À compter de PowerShell 6,2, il existe deux éditions de PowerShell :

- **Desktop** , qui s’exécute sur .NET Framework. PowerShell 4 et versions antérieures, ainsi que PowerShell 5,1 sur les éditions Windows complètes, telles que Windows Desktop, Windows Server, Windows Server Core et la plupart des autres systèmes d’exploitation Windows, sont l’édition Desktop.
  Il s’agit de l’édition PowerShell d’origine.
- **Core** , qui s’exécute sur .net core. PowerShell 6,0 et versions ultérieures, ainsi que PowerShell 5,1 sur certaines éditions de Windows à encombrement réduit, telles que Windows nano Server et Windows IoT où .NET Framework n’est pas disponible.

Étant donné que l’édition de PowerShell correspond à son Runtime .NET, il s’agit de l’indicateur principal de la compatibilité des API .NET et des modules PowerShell. certaines API, types ou méthodes .NET ne sont pas disponibles dans les deux runtimes .NET et cela affecte les scripts et les modules PowerShell qui en dépendent.

## <a name="the-psedition-automatic-variable"></a>La `$PSEdition` variable automatique

Dans PowerShell 5,1 et versions ultérieures, vous pouvez déterminer quelle édition vous exécutez avec la `$PSEdition` variable automatique :

```powershell
$PSEdition
```

```Output
Core
```

Dans PowerShell 4 et les versions antérieures, cette variable n’existe pas. `$PSEdition` la valeur null doit être traitée comme ayant la valeur `Desktop` .

### <a name="edition-in-psversiontable"></a>Édition dans `$PSVersionTable`

La `$PSVersionTable` variable automatique contient également des informations d’édition dans PowerShell 5,1 et versions ultérieures :

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      6.2.0-rc.1
PSEdition                      Core           # <-- Edition information
GitCommitId                    6.2.0-rc.1
OS                             Microsoft Windows 10.0.18865
Platform                       Win32NT
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
WSManStackVersion              3.0
```

Le `PSEdition` champ aura la même valeur que la `$PSEdition` variable automatique.

## <a name="the-compatiblepseditions-module-manifest-field"></a>`CompatiblePSEditions`Champ du manifeste du module

Les modules PowerShell peuvent déclarer les éditions de PowerShell compatibles avec à l’aide du `CompatiblePSEditions` champ du manifeste de module.

Par exemple, un manifeste de module déclarant la compatibilité avec `Desktop` les `Core` éditions et de PowerShell :

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop', 'Core')
}
```

Exemple de manifeste de module avec compatibilité uniquement `Desktop` :

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop')
}
```

L’omission du `CompatiblePSEditions` champ d’un manifeste de module a le même effet que son affectation à la valeur `Desktop` , car les modules créés avant l’introduction de ce champ ont été implicitement écrits pour cette édition.

Pour les modules non fournis avec Windows (c’est-à-dire les modules que vous écrivez ou installez à partir de la Galerie), ce champ est à titre d’information uniquement. PowerShell ne change pas le comportement en fonction du `CompatiblePSEditions` champ, mais l’expose sur l' `PSModuleInfo` objet (retourné par `Get-Module` ) pour votre propre logique :

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion '5.1'
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

> [!NOTE]
> Le `CompatiblePSEditions` champ module est compatible uniquement avec PowerShell 5,1 et versions ultérieures.
> L’inclusion de ce champ entraîne l’incompatibilité d’un module avec PowerShell 4 et versions antérieures.
> Étant donné que le champ est purement informatif, il peut être omis en toute sécurité dans les versions ultérieures de PowerShell.

Dans PowerShell 6,1, `Get-Module -ListAvailable` son formateur a été mis à jour pour afficher l’édition-compatibilité de chaque module :

```PowerShell
Get-Module -ListAvailable
```

```Output

    Directory: C:\Users\me\Documents\PowerShell\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Script     1.4.0      Az                                  Core,Desk
Script     1.3.1      Az.Accounts                         Core,Desk {Disable-AzDataCollection, Disable-AzContextAutosave, E...
Script     1.0.1      Az.Aks                              Core,Desk {Get-AzAks, New-AzAks, Remove-AzAks, Import-AzAksCreden...

...

Script     4.4.0      Pester                              Desk      {Describe, Context, It, Should...}
Script     1.18.0     PSScriptAnalyzer                    Desk      {Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer, Invoke-...
Script     1.0.0      WindowsCompatibility                Core      {Initialize-WinSession, Add-WinFunction, Invoke-WinComm...

```

## <a name="edition-compatibility-for-modules-that-ship-as-part-of-windows"></a>Édition-compatibilité pour les modules fournis avec Windows

Pour les modules qui font partie de Windows (ou qui sont installés dans le cadre d’un rôle ou d’une fonctionnalité), PowerShell 6,1 et versions ultérieures traitent le `CompatiblePSEditions` champ différemment. Ces modules se trouvent dans le répertoire des modules système de Windows PowerShell ( `%windir%\System\WindowsPowerShell\v1.0\Modules` ).

Pour les modules chargés à partir de ou trouvés dans ce répertoire, PowerShell 6,1 et versions ultérieures utilisent le `CompatiblePSEditions` champ pour déterminer si le module sera compatible avec la session active et se comporte en conséquence.

Quand `Import-Module` est utilisé, un module sans `Core` dans `CompatiblePSEditions` ne sera pas importé et une erreur s’affichera :

```powershell
Import-Module BitsTransfer
```

```Output
Import-Module : Module 'C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1' does not support current PowerShell edition 'Core'. Its supported editions are 'Desktop'. Use 'Import-Module -SkipEditionCheck' to ignore the compatibility of this module.
At line:1 char:1
+ Import-Module BitsTransfer
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : ResourceUnavailable: (C:\WINDOWS\system32\u2026r\BitsTransfer.psd1:String) [Import-Module], InvalidOperationException
+ FullyQualifiedErrorId : Modules_PSEditionNotSupported,Microsoft.PowerShell.Commands.ImportModuleCommand
```

Lorsque `Get-Module -ListAvailable` est utilisé, les modules sans `Core` dans `CompatiblePSEditions` ne sont pas affichés :

```powershell
Get-Module -ListAvailable BitsTransfer
```

```Output
# No output
```

Dans les deux cas, le `-SkipEditionCheck` paramètre de commutateur peut être utilisé pour remplacer ce comportement :

```powershell
Get-Module -ListAvailable -SkipEditionCheck BitsTransfer
```

```Output

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.0.0    BitsTransfer                        Desk      {Add-BitsFile, Complete-BitsTransfer, Get-BitsTransfer,...

```

> [!WARNING]
> `Import-Module -SkipEditionCheck` peut sembler être exécutée correctement pour un module, mais l’utilisation de ce module risque de rencontrer une incompatibilité plus tard. lors du chargement initial du module, une commande peut appeler ultérieurement une API incompatible et échouer spontanément.

## <a name="authoring-powershell-modules-for-edition-cross-compatibility"></a>Création de modules PowerShell pour la compatibilité croisée de l’édition

Lors de l’écriture d’un module PowerShell pour cibler à la fois les `Desktop` `Core` éditions et de PowerShell, vous pouvez effectuer des opérations pour garantir la compatibilité entre les éditions.

La seule méthode vraie pour confirmer et valider continuellement la compatibilité consiste toutefois à écrire des tests pour votre script ou module et à les exécuter sur toutes les versions et éditions de PowerShell dont vous avez besoin pour la compatibilité avec. [Pester][]est une infrastructure de test recommandée.

### <a name="powershell-script"></a>Script PowerShell

En tant que langage, PowerShell fonctionne de la même façon entre les éditions de. Il s’agit des applets de commande, des modules et des API .NET que vous utilisez et qui sont affectés par la compatibilité de l’édition.

En règle générale, les scripts qui fonctionnent dans PowerShell 6,1 et versions ultérieures fonctionnent avec Windows PowerShell 5,1, mais il existe des exceptions.

La version 1.18.0 du module [PSScriptAnalyzer][] contient des règles telles que [`PSUseCompatibleCommands`][] et [`PSUseCompatibleTypes`][] peuvent détecter l’utilisation potentiellement incompatible des commandes et des API .net dans les scripts PowerShell.

### <a name="net-assemblies"></a>assemblys .NET

Si vous écrivez un module binaire ou un module qui incorpore des assemblys .NET (dll) générés à partir du code source, vous devez compiler par rapport à [.NET standard][] et [PowerShell standard][] pour la validation de la compatibilité au moment de la compilation de .net et de la compatibilité des API PowerShell.

Bien que ces bibliothèques soient en mesure de vérifier la compatibilité au moment de la compilation, elles ne peuvent pas intercepter les différences de comportement possibles entre les éditions. Pour cela, vous devez toujours écrire des tests.

## <a name="see-also"></a>Voir aussi

- [about_Automatic_Variables](about_Automatic_Variables.md)
- [Module d’importation](xref:Microsoft.PowerShell.Core.Import-Module)
- [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module)
- [Modules avec des éditions PowerShell compatibles](/powershell/scripting/gallery/concepts/module-psedition-support)

[Pester]: https://github.com/pester/Pester/wiki/Pester
[PSScriptAnalyzer]: https://github.com/PowerShell/PSScriptAnalyzer
['PSUseCompatibleCommands']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
['PSUseCompatibleTypes']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
