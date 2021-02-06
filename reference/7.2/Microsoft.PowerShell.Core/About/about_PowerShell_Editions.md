---
description: Les différentes éditions de PowerShell s’exécutent sur des runtimes sous-jacents différents.
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_editions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Editions
ms.openlocfilehash: 3b1b938874b36919a1a0627f3b492cbc961e4a2f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598794"
---
# <a name="about-powershell-editions"></a><span data-ttu-id="4458a-103">À propos des éditions de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4458a-103">About PowerShell Editions</span></span>

## <a name="short-description"></a><span data-ttu-id="4458a-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="4458a-104">Short Description</span></span>
<span data-ttu-id="4458a-105">Les différentes éditions de PowerShell s’exécutent sur des runtimes sous-jacents différents.</span><span class="sxs-lookup"><span data-stu-id="4458a-105">Different editions of PowerShell run on different underlying runtimes.</span></span>

## <a name="long-description"></a><span data-ttu-id="4458a-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="4458a-106">Long Description</span></span>

<span data-ttu-id="4458a-107">À partir de PowerShell 5,1, plusieurs *éditions* de PowerShell s’exécutent sur un autre Runtime .net.</span><span class="sxs-lookup"><span data-stu-id="4458a-107">From PowerShell 5.1, there are multiple *editions* of PowerShell that each run on a different .NET runtime.</span></span> <span data-ttu-id="4458a-108">À compter de PowerShell 6,2, il existe deux éditions de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="4458a-108">As of PowerShell 6.2 there are two editions of PowerShell:</span></span>

- <span data-ttu-id="4458a-109">**Desktop**, qui s’exécute sur .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4458a-109">**Desktop**, which runs on .NET Framework.</span></span> <span data-ttu-id="4458a-110">PowerShell 4 et versions antérieures, ainsi que PowerShell 5,1 sur les éditions Windows complètes, telles que Windows Desktop, Windows Server, Windows Server Core et la plupart des autres systèmes d’exploitation Windows, sont l’édition Desktop.</span><span class="sxs-lookup"><span data-stu-id="4458a-110">PowerShell 4 and below, as well as PowerShell 5.1 on full-featured Windows editions like Windows Desktop, Windows Server, Windows Server Core and most other Windows operating systems are Desktop edition.</span></span>
  <span data-ttu-id="4458a-111">Il s’agit de l’édition PowerShell d’origine.</span><span class="sxs-lookup"><span data-stu-id="4458a-111">This is the original PowerShell edition.</span></span>
- <span data-ttu-id="4458a-112">**Core**, qui s’exécute sur .net core.</span><span class="sxs-lookup"><span data-stu-id="4458a-112">**Core**, which runs on .NET Core.</span></span> <span data-ttu-id="4458a-113">PowerShell 6,0 et versions ultérieures, ainsi que PowerShell 5,1 sur certaines éditions de Windows à encombrement réduit, telles que Windows nano Server et Windows IoT où .NET Framework n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="4458a-113">PowerShell 6.0 and above, as well as PowerShell 5.1 on some reduced-footprint Windows editions such as Windows Nano Server and Windows IoT where .NET Framework is unavailable.</span></span>

<span data-ttu-id="4458a-114">Étant donné que l’édition de PowerShell correspond à son Runtime .NET, il s’agit de l’indicateur principal de la compatibilité des API .NET et des modules PowerShell. certaines API, types ou méthodes .NET ne sont pas disponibles dans les deux runtimes .NET et cela affecte les scripts et les modules PowerShell qui en dépendent.</span><span class="sxs-lookup"><span data-stu-id="4458a-114">Because the edition of PowerShell corresponds to its .NET runtime, it is the primary indicator of .NET API and PowerShell module compatibility; some .NET APIs, types or methods are not available in both .NET runtimes and this affects PowerShell scripts and modules that depend on them.</span></span>

## <a name="the-psedition-automatic-variable"></a><span data-ttu-id="4458a-115">La `$PSEdition` variable automatique</span><span class="sxs-lookup"><span data-stu-id="4458a-115">The `$PSEdition` automatic variable</span></span>

<span data-ttu-id="4458a-116">Dans PowerShell 5,1 et versions ultérieures, vous pouvez déterminer quelle édition vous exécutez avec la `$PSEdition` variable automatique :</span><span class="sxs-lookup"><span data-stu-id="4458a-116">In PowerShell 5.1 and above, you can find out what edition you are running with the `$PSEdition` automatic variable:</span></span>

```powershell
$PSEdition
```

```Output
Core
```

<span data-ttu-id="4458a-117">Dans PowerShell 4 et les versions antérieures, cette variable n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="4458a-117">In PowerShell 4 and below, this variable does not exist.</span></span> <span data-ttu-id="4458a-118">`$PSEdition` la valeur null doit être traitée comme ayant la valeur `Desktop` .</span><span class="sxs-lookup"><span data-stu-id="4458a-118">`$PSEdition` being null should be treated as the same as having the value `Desktop`.</span></span>

### <a name="edition-in-psversiontable"></a><span data-ttu-id="4458a-119">Édition dans `$PSVersionTable`</span><span class="sxs-lookup"><span data-stu-id="4458a-119">Edition in `$PSVersionTable`</span></span>

<span data-ttu-id="4458a-120">La `$PSVersionTable` variable automatique contient également des informations d’édition dans PowerShell 5,1 et versions ultérieures :</span><span class="sxs-lookup"><span data-stu-id="4458a-120">The `$PSVersionTable` automatic variable also has edition information in PowerShell 5.1 and above:</span></span>

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

<span data-ttu-id="4458a-121">Le `PSEdition` champ aura la même valeur que la `$PSEdition` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="4458a-121">The `PSEdition` field will have the same value as the `$PSEdition` automatic variable.</span></span>

## <a name="the-compatiblepseditions-module-manifest-field"></a><span data-ttu-id="4458a-122">`CompatiblePSEditions`Champ du manifeste du module</span><span class="sxs-lookup"><span data-stu-id="4458a-122">The `CompatiblePSEditions` module manifest field</span></span>

<span data-ttu-id="4458a-123">Les modules PowerShell peuvent déclarer les éditions de PowerShell compatibles avec à l’aide du `CompatiblePSEditions` champ du manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="4458a-123">PowerShell modules can declare what editions of PowerShell they are compatible with using the `CompatiblePSEditions` field of the module manifest.</span></span>

<span data-ttu-id="4458a-124">Par exemple, un manifeste de module déclarant la compatibilité avec `Desktop` les `Core` éditions et de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="4458a-124">For example, a module manifest declaring compatibility with both `Desktop` and `Core` editions of PowerShell:</span></span>

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop', 'Core')
}
```

<span data-ttu-id="4458a-125">Exemple de manifeste de module avec compatibilité uniquement `Desktop` :</span><span class="sxs-lookup"><span data-stu-id="4458a-125">An example of a module manifest with only `Desktop` compatibility:</span></span>

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop')
}
```

<span data-ttu-id="4458a-126">L’omission du `CompatiblePSEditions` champ d’un manifeste de module a le même effet que son affectation à la valeur `Desktop` , car les modules créés avant l’introduction de ce champ ont été implicitement écrits pour cette édition.</span><span class="sxs-lookup"><span data-stu-id="4458a-126">Omitting the `CompatiblePSEditions` field from a module manifest will have the same effect as setting it to `Desktop`, since modules created before this field was introduced were implicitly written for this edition.</span></span>

<span data-ttu-id="4458a-127">Pour les modules non fournis avec Windows (c’est-à-dire les modules que vous écrivez ou installez à partir de la Galerie), ce champ est à titre d’information uniquement. PowerShell ne change pas le comportement en fonction du `CompatiblePSEditions` champ, mais l’expose sur l' `PSModuleInfo` objet (retourné par `Get-Module` ) pour votre propre logique :</span><span class="sxs-lookup"><span data-stu-id="4458a-127">For modules not shipped as part of Windows (i.e. modules you write or install from the gallery), this field is informational only; PowerShell does not change behavior based on the `CompatiblePSEditions` field, but does expose it on the `PSModuleInfo` object (returned by `Get-Module`) for your own logic:</span></span>

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
> <span data-ttu-id="4458a-128">Le `CompatiblePSEditions` champ module est compatible uniquement avec PowerShell 5,1 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="4458a-128">The `CompatiblePSEditions` module field is only compatible with PowerShell 5.1 and above.</span></span>
> <span data-ttu-id="4458a-129">L’inclusion de ce champ entraîne l’incompatibilité d’un module avec PowerShell 4 et versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="4458a-129">Including this field will cause a module to be incompatible with PowerShell 4 and below.</span></span>
> <span data-ttu-id="4458a-130">Étant donné que le champ est purement informatif, il peut être omis en toute sécurité dans les versions ultérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4458a-130">Since the field is purely informational, it can be safely omitted in later PowerShell versions.</span></span>

<span data-ttu-id="4458a-131">Dans PowerShell 6,1, `Get-Module -ListAvailable` son formateur a été mis à jour pour afficher l’édition-compatibilité de chaque module :</span><span class="sxs-lookup"><span data-stu-id="4458a-131">In PowerShell 6.1, `Get-Module -ListAvailable` has had its formatter updated to display the edition-compatibility of each module:</span></span>

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

## <a name="edition-compatibility-for-modules-that-ship-as-part-of-windows"></a><span data-ttu-id="4458a-132">Édition-compatibilité pour les modules fournis avec Windows</span><span class="sxs-lookup"><span data-stu-id="4458a-132">Edition-compatibility for modules that ship as part of Windows</span></span>

<span data-ttu-id="4458a-133">Pour les modules qui font partie de Windows (ou qui sont installés dans le cadre d’un rôle ou d’une fonctionnalité), PowerShell 6,1 et versions ultérieures traitent le `CompatiblePSEditions` champ différemment.</span><span class="sxs-lookup"><span data-stu-id="4458a-133">For modules that come as part of Windows (or are installed as part of a role or feature), PowerShell 6.1 and above treat the `CompatiblePSEditions` field differently.</span></span> <span data-ttu-id="4458a-134">Ces modules se trouvent dans le répertoire des modules système de Windows PowerShell ( `%windir%\System\WindowsPowerShell\v1.0\Modules` ).</span><span class="sxs-lookup"><span data-stu-id="4458a-134">Such modules are found in the Windows PowerShell system modules directory (`%windir%\System\WindowsPowerShell\v1.0\Modules`).</span></span>

<span data-ttu-id="4458a-135">Pour les modules chargés à partir de ou trouvés dans ce répertoire, PowerShell 6,1 et versions ultérieures utilisent le `CompatiblePSEditions` champ pour déterminer si le module sera compatible avec la session active et se comporte en conséquence.</span><span class="sxs-lookup"><span data-stu-id="4458a-135">For modules loaded from or found in this directory, PowerShell 6.1 and above uses the `CompatiblePSEditions` field to determine whether the module will be compatible with the current session and behaves accordingly.</span></span>

<span data-ttu-id="4458a-136">Quand `Import-Module` est utilisé, un module sans `Core` dans `CompatiblePSEditions` ne sera pas importé et une erreur s’affichera :</span><span class="sxs-lookup"><span data-stu-id="4458a-136">When `Import-Module` is used, a module without `Core` in `CompatiblePSEditions` will not be imported and an error will be displayed:</span></span>

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

<span data-ttu-id="4458a-137">Lorsque `Get-Module -ListAvailable` est utilisé, les modules sans `Core` dans `CompatiblePSEditions` ne sont pas affichés :</span><span class="sxs-lookup"><span data-stu-id="4458a-137">When `Get-Module -ListAvailable` is used, modules without `Core` in `CompatiblePSEditions` will not be displayed:</span></span>

```powershell
Get-Module -ListAvailable BitsTransfer
```

```Output
# No output
```

<span data-ttu-id="4458a-138">Dans les deux cas, le `-SkipEditionCheck` paramètre de commutateur peut être utilisé pour remplacer ce comportement :</span><span class="sxs-lookup"><span data-stu-id="4458a-138">In both cases, the `-SkipEditionCheck` switch parameter can be used to override this behavior:</span></span>

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
> <span data-ttu-id="4458a-139">`Import-Module -SkipEditionCheck` peut sembler être exécutée correctement pour un module, mais l’utilisation de ce module risque de rencontrer une incompatibilité plus tard. lors du chargement initial du module, une commande peut appeler ultérieurement une API incompatible et échouer spontanément.</span><span class="sxs-lookup"><span data-stu-id="4458a-139">`Import-Module -SkipEditionCheck` may appear to succeed for a module, but using that module runs the risk of encountering an incompatibility later on; while loading the module initially succeeds, a command may later call an incompatible API and fail spontaneously.</span></span>

## <a name="authoring-powershell-modules-for-edition-cross-compatibility"></a><span data-ttu-id="4458a-140">Création de modules PowerShell pour la compatibilité croisée de l’édition</span><span class="sxs-lookup"><span data-stu-id="4458a-140">Authoring PowerShell modules for edition cross-compatibility</span></span>

<span data-ttu-id="4458a-141">Lors de l’écriture d’un module PowerShell pour cibler à la fois les `Desktop` `Core` éditions et de PowerShell, vous pouvez effectuer des opérations pour garantir la compatibilité entre les éditions.</span><span class="sxs-lookup"><span data-stu-id="4458a-141">When writing a PowerShell module to target both `Desktop` and `Core` editions of PowerShell, there are things you can do to ensure cross-edition compatibility.</span></span>

<span data-ttu-id="4458a-142">La seule méthode vraie pour confirmer et valider continuellement la compatibilité consiste toutefois à écrire des tests pour votre script ou module et à les exécuter sur toutes les versions et éditions de PowerShell dont vous avez besoin pour la compatibilité avec.</span><span class="sxs-lookup"><span data-stu-id="4458a-142">The only true way to confirm and continually validate compatibility however is to write tests for your script or module and run them on all versions and editions of PowerShell you need compatibility with.</span></span> <span data-ttu-id="4458a-143">[Pester][]est une infrastructure de test recommandée.</span><span class="sxs-lookup"><span data-stu-id="4458a-143">A recommended testing framework for this is [Pester][].</span></span>

### <a name="powershell-script"></a><span data-ttu-id="4458a-144">Script PowerShell</span><span class="sxs-lookup"><span data-stu-id="4458a-144">PowerShell script</span></span>

<span data-ttu-id="4458a-145">En tant que langage, PowerShell fonctionne de la même façon entre les éditions de. Il s’agit des applets de commande, des modules et des API .NET que vous utilisez et qui sont affectés par la compatibilité de l’édition.</span><span class="sxs-lookup"><span data-stu-id="4458a-145">As a language, PowerShell works the same between editions; it is the cmdlets, modules and .NET APIs you use that are affected by edition compatibility.</span></span>

<span data-ttu-id="4458a-146">En règle générale, les scripts qui fonctionnent dans PowerShell 6,1 et versions ultérieures fonctionnent avec Windows PowerShell 5,1, mais il existe des exceptions.</span><span class="sxs-lookup"><span data-stu-id="4458a-146">Generally, scripts that work in PowerShell 6.1 and above will work with Windows PowerShell 5.1, but there are some exceptions.</span></span>

<span data-ttu-id="4458a-147">La version 1.18.0 du module [PSScriptAnalyzer][] contient des règles telles que [`PSUseCompatibleCommands`][] et [`PSUseCompatibleTypes`][] peuvent détecter l’utilisation potentiellement incompatible des commandes et des API .net dans les scripts PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4458a-147">Version 1.18.0 [PSScriptAnalyzer][] module has rules like [`PSUseCompatibleCommands`][] and [`PSUseCompatibleTypes`][] that are able to detect possibly incompatible usage of commands and .NET APIs in PowerShell scripts.</span></span>

### <a name="net-assemblies"></a><span data-ttu-id="4458a-148">assemblys .NET</span><span class="sxs-lookup"><span data-stu-id="4458a-148">.NET assemblies</span></span>

<span data-ttu-id="4458a-149">Si vous écrivez un module binaire ou un module qui incorpore des assemblys .NET (dll) générés à partir du code source, vous devez compiler par rapport à [.NET standard][] et [PowerShell standard][] pour la validation de la compatibilité au moment de la compilation de .net et de la compatibilité des API PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4458a-149">If you are writing a binary module or a module that incorporates .NET assemblies (DLLs) generated from source code, you should compile against [.NET Standard][] and [PowerShell Standard][] for compile-time compatibility validation of .NET and PowerShell API compatibility.</span></span>

<span data-ttu-id="4458a-150">Bien que ces bibliothèques soient en mesure de vérifier la compatibilité au moment de la compilation, elles ne peuvent pas intercepter les différences de comportement possibles entre les éditions.</span><span class="sxs-lookup"><span data-stu-id="4458a-150">Although these libraries are able to check some compatibility at compile time, they won't be able to catch possible behavioral differences between editions.</span></span> <span data-ttu-id="4458a-151">Pour cela, vous devez toujours écrire des tests.</span><span class="sxs-lookup"><span data-stu-id="4458a-151">For this you must still write tests.</span></span>

## <a name="see-also"></a><span data-ttu-id="4458a-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4458a-152">See also</span></span>

- [<span data-ttu-id="4458a-153">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="4458a-153">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="4458a-154">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="4458a-154">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)
- [<span data-ttu-id="4458a-155">Get-Module</span><span class="sxs-lookup"><span data-stu-id="4458a-155">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)
- [<span data-ttu-id="4458a-156">Modules avec des éditions PowerShell compatibles</span><span class="sxs-lookup"><span data-stu-id="4458a-156">Modules with compatible PowerShell Editions</span></span>](/powershell/scripting/gallery/concepts/module-psedition-support)

[Pester]: https://github.com/pester/Pester/wiki/Pester
[PSScriptAnalyzer]: https://github.com/PowerShell/PSScriptAnalyzer
['PSUseCompatibleCommands']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
[`PSUseCompatibleCommands`]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
['PSUseCompatibleTypes']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[`PSUseCompatibleTypes`]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
