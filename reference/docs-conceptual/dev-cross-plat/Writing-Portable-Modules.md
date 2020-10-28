---
ms.date: 10/21/2020
keywords: powershell,applet de commande
title: Écriture de modules portables
description: Cet article explique comment créer des modules nouveaux ou mettre à jour des modules existants afin qu’ils fonctionnent sur les plateformes prises en charge par PowerShell.
ms.openlocfilehash: 6d5c36263c3c6d1219f963cea2e94ae92b07e863
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500791"
---
# <a name="portable-modules"></a><span data-ttu-id="76ad7-104">Modules portables</span><span class="sxs-lookup"><span data-stu-id="76ad7-104">Portable Modules</span></span>

<span data-ttu-id="76ad7-105">Windows PowerShell est écrit pour [.NET Framework][] alors que PowerShell Core est écrit pour [.NET Core][].</span><span class="sxs-lookup"><span data-stu-id="76ad7-105">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="76ad7-106">Les modules portables sont des modules qui fonctionnent à la fois dans Windows PowerShell et PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="76ad7-106">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="76ad7-107">Même si .NET Framework et .NET Core sont hautement compatibles, il existe des différences dans les API disponibles pour ces deux environnements.</span><span class="sxs-lookup"><span data-stu-id="76ad7-107">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="76ad7-108">Il existe également des différences dans les API disponibles dans Windows PowerShell et PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="76ad7-108">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="76ad7-109">Les modules destinés à être utilisés dans les deux environnements doivent prendre en compte ces différences.</span><span class="sxs-lookup"><span data-stu-id="76ad7-109">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="76ad7-110">Portage d’un module existant</span><span class="sxs-lookup"><span data-stu-id="76ad7-110">Porting an existing module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="76ad7-111">Portage d’un module PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="76ad7-111">Porting a PSSnapIn</span></span>

<span data-ttu-id="76ad7-112">Les composants logiciels enfichables PowerShell ([SnapIns](/powershell/scripting/developer/cmdlet/modules-and-snap-ins)) ne sont pas pris en charge dans PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="76ad7-112">PowerShell [SnapIns](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="76ad7-113">Mais vous pouvez facilement convertir un module PSSnapIn en module PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76ad7-113">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="76ad7-114">En règle générale, le code d’inscription PSSnapIn figure dans un fichier source unique d’une classe qui dérive de [PSSnapIn][].</span><span class="sxs-lookup"><span data-stu-id="76ad7-114">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="76ad7-115">Supprimez ce fichier source de la build car il n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="76ad7-115">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="76ad7-116">Utilisez [New-ModuleManifest][] pour créer un manifeste de module qui évite la saisie du code d’inscription PSSnapIn.</span><span class="sxs-lookup"><span data-stu-id="76ad7-116">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="76ad7-117">Certaines valeurs de **PSSnapIn** (par exemple, **Description** ) peuvent être réutilisées dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="76ad7-117">Some of the values from the **PSSnapIn** (such as **Description** ) can be reused within the module manifest.</span></span>

<span data-ttu-id="76ad7-118">La propriété **RootModule** du manifeste de module doit être définie sur le nom de l’assembly (dll) qui implémente les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="76ad7-118">The **RootModule** property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="76ad7-119">Analyseur de portabilité .NET (également appelé APIPort)</span><span class="sxs-lookup"><span data-stu-id="76ad7-119">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="76ad7-120">Pour porter des modules écrits pour Windows PowerShell et les utiliser avec PowerShell Core, commencez par l’[Analyseur de portabilité .NET][].</span><span class="sxs-lookup"><span data-stu-id="76ad7-120">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="76ad7-121">Exécutez cet outil avec votre assembly compilé pour déterminer si les API .NET utilisées dans le module sont compatibles avec .NET Framework, .NET Core et autres runtimes .NET.</span><span class="sxs-lookup"><span data-stu-id="76ad7-121">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="76ad7-122">Le cas échéant, l’outil suggère des API de remplacement.</span><span class="sxs-lookup"><span data-stu-id="76ad7-122">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="76ad7-123">Sinon, vous devrez peut-être ajouter des [vérifications à l’exécution][] et limiter les fonctionnalités non disponibles dans des runtimes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="76ad7-123">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="76ad7-124">Création d’un module</span><span class="sxs-lookup"><span data-stu-id="76ad7-124">Creating a new module</span></span>

<span data-ttu-id="76ad7-125">Si vous créez un module, la recommandation consiste à utiliser l’[interface de ligne de commande (CLI) .NET][].</span><span class="sxs-lookup"><span data-stu-id="76ad7-125">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="76ad7-126">Installation du modèle de module PowerShell Standard</span><span class="sxs-lookup"><span data-stu-id="76ad7-126">Installing the PowerShell Standard module template</span></span>

<span data-ttu-id="76ad7-127">Une fois l’interface CLI .NET installée, installez une bibliothèque de modèles pour générer un module PowerShell simple.</span><span class="sxs-lookup"><span data-stu-id="76ad7-127">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="76ad7-128">Le module sera compatible avec Windows PowerShell, PowerShell Core, Windows, Linux et macOS.</span><span class="sxs-lookup"><span data-stu-id="76ad7-128">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="76ad7-129">L’exemple suivant présente l’installation du modèle :</span><span class="sxs-lookup"><span data-stu-id="76ad7-129">The following example shows how to install the template:</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                        Short Name         Language          Tags
-----------------------------------------------------------------------------------------------
Console Application              console            [C#], F#, VB      Common/Console
Class library                    classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module       psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a><span data-ttu-id="76ad7-130">Création d’un projet de module</span><span class="sxs-lookup"><span data-stu-id="76ad7-130">Creating a new module project</span></span>

<span data-ttu-id="76ad7-131">Une fois le modèle installé, vous pouvez l’utiliser pour créer un projet de module PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76ad7-131">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="76ad7-132">Dans cet exemple, l’exemple de module s’appelle 'myModule'.</span><span class="sxs-lookup"><span data-stu-id="76ad7-132">In this example, the sample module is called 'myModule'.</span></span>

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a><span data-ttu-id="76ad7-133">Génération du module</span><span class="sxs-lookup"><span data-stu-id="76ad7-133">Building the module</span></span>

<span data-ttu-id="76ad7-134">Utilisez les commandes CLI .NET standard pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="76ad7-134">Use standard .NET CLI commands to build the project.</span></span>

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a><span data-ttu-id="76ad7-135">Test du module</span><span class="sxs-lookup"><span data-stu-id="76ad7-135">Testing the module</span></span>

<span data-ttu-id="76ad7-136">Après avoir généré le module, vous pouvez importer et exécuter l’exemple d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="76ad7-136">After building the module, you can import it and execute the sample cmdlet.</span></span>

```powershell
Import-Module .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

### <a name="debugging-the-module"></a><span data-ttu-id="76ad7-137">Débogage du module</span><span class="sxs-lookup"><span data-stu-id="76ad7-137">Debugging the module</span></span>

<span data-ttu-id="76ad7-138">Pour obtenir des instructions sur la configuration de Visual Studio Code en vue de déboguer le module, consultez [Utilisation de Visual Studio Code pour le débogage des applets de commande compilées][].</span><span class="sxs-lookup"><span data-stu-id="76ad7-138">For a guide on setting up Visual Studio Code to debug the module, see [Using Visual Studio Code for debugging compiled cmdlets][].</span></span>

## <a name="supporting-technologies"></a><span data-ttu-id="76ad7-139">Technologies prises en charge</span><span class="sxs-lookup"><span data-stu-id="76ad7-139">Supporting technologies</span></span>

<span data-ttu-id="76ad7-140">Les sections suivantes décrivent en détail certaines des technologies utilisées par ce modèle.</span><span class="sxs-lookup"><span data-stu-id="76ad7-140">The following sections describe in detail some of the technologies used by this template.</span></span>

### <a name="net-standard-library"></a><span data-ttu-id="76ad7-141">Bibliothèque .NET Standard</span><span class="sxs-lookup"><span data-stu-id="76ad7-141">.NET Standard Library</span></span>

<span data-ttu-id="76ad7-142">[.NET Standard][] est une spécification formelle des API .NET disponibles dans toutes les implémentations .NET.</span><span class="sxs-lookup"><span data-stu-id="76ad7-142">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="76ad7-143">Un code managé ciblant .NET Standard fonctionne avec les versions de .NET Framework et .NET Core compatibles avec cette version de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="76ad7-143">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="76ad7-144">Même si une API peut exister dans .NET Standard, l’implémentation de l’API dans .NET Core peut lever une `PlatformNotSupportedException` lors de l’exécution, et par conséquent, pour vérifier la compatibilité avec Windows PowerShell et PowerShell Core, il est recommandé d’exécuter des tests pour votre module dans les deux environnements.</span><span class="sxs-lookup"><span data-stu-id="76ad7-144">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="76ad7-145">Exécutez également des tests sur Linux et macOS si votre module est destiné à une utilisation multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="76ad7-145">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="76ad7-146">Le ciblage .NET Standard permet de s’assurer que, à mesure que le module évolue, les API incompatibles ne sont pas introduites accidentellement dans ce module.</span><span class="sxs-lookup"><span data-stu-id="76ad7-146">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="76ad7-147">Les incompatibilités sont détectées lors de la compilation au lieu de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="76ad7-147">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="76ad7-148">Toutefois, il n’est pas nécessaire de cibler .NET Standard pour qu’un module fonctionne avec Windows PowerShell et PowerShell Core, tant que vous utilisez une API compatible.</span><span class="sxs-lookup"><span data-stu-id="76ad7-148">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="76ad7-149">Le langage intermédiaire (Intermediate Language, IL) est compatible entre les deux runtimes.</span><span class="sxs-lookup"><span data-stu-id="76ad7-149">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="76ad7-150">Vous pouvez cibler .NET Framework 4.6.1, qui est compatible avec .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="76ad7-150">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="76ad7-151">Si vous n’utilisez pas les API en dehors de .NET Standard 2.0, votre module fonctionne avec PowerShell Core 6 sans recompilation.</span><span class="sxs-lookup"><span data-stu-id="76ad7-151">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

### <a name="powershell-standard-library"></a><span data-ttu-id="76ad7-152">Bibliothèque PowerShell Standard</span><span class="sxs-lookup"><span data-stu-id="76ad7-152">PowerShell Standard Library</span></span>

<span data-ttu-id="76ad7-153">La bibliothèque [PowerShell Standard][] est une spécification formelle des API PowerShell disponibles dans toutes les versions de PowerShell supérieures ou égales à la version de cette norme.</span><span class="sxs-lookup"><span data-stu-id="76ad7-153">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="76ad7-154">Par exemple, [PowerShell Standard 5.1][] est compatible avec Windows PowerShell 5.1 et PowerShell Core 6.0 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="76ad7-154">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="76ad7-155">Nous vous recommandons de compiler votre module à l’aide de la bibliothèque PowerShell Standard.</span><span class="sxs-lookup"><span data-stu-id="76ad7-155">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="76ad7-156">Cette bibliothèque garantit la disponibilité et l’implémentation des API dans Windows PowerShell et PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="76ad7-156">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="76ad7-157">PowerShell Standard garantit toujours une compatibilité ascendante.</span><span class="sxs-lookup"><span data-stu-id="76ad7-157">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="76ad7-158">Un module généré à l’aide de PowerShell Standard Library 5.1 sera toujours compatible avec les futures versions de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76ad7-158">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

### <a name="module-manifest"></a><span data-ttu-id="76ad7-159">Manifeste de module</span><span class="sxs-lookup"><span data-stu-id="76ad7-159">Module Manifest</span></span>

#### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="76ad7-160">Indication de la compatibilité avec Windows PowerShell et PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="76ad7-160">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="76ad7-161">Après avoir vérifié que votre module fonctionne avec Windows PowerShell et PowerShell Core, le manifeste de module doit indiquer explicitement la compatibilité à l’aide de la propriété [CompatiblePSEditions][].</span><span class="sxs-lookup"><span data-stu-id="76ad7-161">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="76ad7-162">La valeur `Desktop` signifie que le module est compatible avec Windows PowerShell, tandis que la valeur `Core` signifie que le module est compatible avec PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="76ad7-162">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="76ad7-163">L’utilisation des valeurs `Desktop` et `Core` signifie que le module est compatible avec Windows PowerShell et PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="76ad7-163">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="76ad7-164">`Core` ne signifie pas automatiquement que le module est compatible avec Windows, Linux et macOS.</span><span class="sxs-lookup"><span data-stu-id="76ad7-164">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="76ad7-165">La propriété **CompatiblePSEditions** a été introduite dans PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="76ad7-165">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="76ad7-166">Les manifestes de modules qui utilisent la propriété **CompatiblePSEditions** ne peuvent pas être chargés dans les versions antérieures à PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="76ad7-166">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="76ad7-167">Indication de la compatibilité du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="76ad7-167">Indicating OS Compatibility</span></span>

<span data-ttu-id="76ad7-168">Tout d’abord, vérifiez que votre module fonctionne sur Linux et macOS.</span><span class="sxs-lookup"><span data-stu-id="76ad7-168">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="76ad7-169">Indiquez ensuite la compatibilité avec ces systèmes d’exploitation dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="76ad7-169">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="76ad7-170">Les utilisateurs pourront ainsi trouver plus facilement votre module pour leur système d’exploitation lors de la publication dans [PowerShell Gallery][].</span><span class="sxs-lookup"><span data-stu-id="76ad7-170">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="76ad7-171">Dans le manifeste de module, la propriété `PrivateData` comporte une sous-propriété `PSData`.</span><span class="sxs-lookup"><span data-stu-id="76ad7-171">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="76ad7-172">La propriété facultative `Tags` de `PSData` utilise un tableau de valeurs qui s’affichent dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="76ad7-172">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="76ad7-173">PowerShell Gallery prend en charge les valeurs de compatibilité suivantes :</span><span class="sxs-lookup"><span data-stu-id="76ad7-173">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="76ad7-174">Tag</span><span class="sxs-lookup"><span data-stu-id="76ad7-174">Tag</span></span>               | <span data-ttu-id="76ad7-175">Description</span><span class="sxs-lookup"><span data-stu-id="76ad7-175">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="76ad7-176">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="76ad7-176">PSEdition_Core</span></span>    | <span data-ttu-id="76ad7-177">Compatible avec PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="76ad7-177">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="76ad7-178">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="76ad7-178">PSEdition_Desktop</span></span> | <span data-ttu-id="76ad7-179">Compatible avec Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="76ad7-179">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="76ad7-180">Windows</span><span class="sxs-lookup"><span data-stu-id="76ad7-180">Windows</span></span>           | <span data-ttu-id="76ad7-181">Compatible avec Windows</span><span class="sxs-lookup"><span data-stu-id="76ad7-181">Compatible with Windows</span></span>                    |
| <span data-ttu-id="76ad7-182">Linux</span><span class="sxs-lookup"><span data-stu-id="76ad7-182">Linux</span></span>             | <span data-ttu-id="76ad7-183">Compatible avec Linux (aucune distribution spécifique)</span><span class="sxs-lookup"><span data-stu-id="76ad7-183">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="76ad7-184">macOS</span><span class="sxs-lookup"><span data-stu-id="76ad7-184">macOS</span></span>             | <span data-ttu-id="76ad7-185">Compatible avec macOS</span><span class="sxs-lookup"><span data-stu-id="76ad7-185">Compatible with macOS</span></span>                      |

<span data-ttu-id="76ad7-186">Exemple :</span><span class="sxs-lookup"><span data-stu-id="76ad7-186">Example:</span></span>

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

### <a name="dependency-on-native-libraries"></a><span data-ttu-id="76ad7-187">dépendance envers les bibliothèques natives</span><span class="sxs-lookup"><span data-stu-id="76ad7-187">Dependency on Native Libraries</span></span>

<span data-ttu-id="76ad7-188">Les modules destinés à être utilisés sur des systèmes d’exploitation ou des architectures de processeur différents peuvent dépendre d’une bibliothèque gérée qui dépend elle-même de certaines bibliothèques natives.</span><span class="sxs-lookup"><span data-stu-id="76ad7-188">Modules intended for use across different operating systems or processor architectures may depend on a managed library that itself depends on some native libraries.</span></span>

<span data-ttu-id="76ad7-189">Avant PowerShell 7, vous deviez avoir un code personnalisé pour charger le fichier DLL natif appropriée afin que la bibliothèque gérée puisse le trouver.</span><span class="sxs-lookup"><span data-stu-id="76ad7-189">Prior to PowerShell 7, one would have to have custom code to load the appropriate native dll so that the managed library can find it correctly.</span></span>

<span data-ttu-id="76ad7-190">Avec PowerShell 7, les fichiers binaires natifs à charger sont recherchés dans des sous-dossiers de l’emplacement de la bibliothèque gérée, à la suite d’un sous-ensemble de la notation [catalogue RID .NET][].</span><span class="sxs-lookup"><span data-stu-id="76ad7-190">With PowerShell 7, native binaries to load are searched in sub-folders within the managed library's location following a subset of the [.NET RID Catalog][] notation.</span></span>

```
managed.dll folder
    |
    |--- 'win-x64' folder
    |       |--- native.dll
    |
    |--- 'win-x86' folder
    |       |--- native.dll
    |
    |--- 'win-arm' folder
    |       |--- native.dll
    |
    |--- 'win-arm64' folder
    |       |--- native.dll
    |
    |--- 'linux-x64' folder
    |       |--- native.so
    |
    |--- 'linux-x86' folder
    |       |--- native.so
    |
    |--- 'linux-arm' folder
    |       |--- native.so
    |
    |--- 'linux-arm64' folder
    |       |--- native.so
    |
    |--- 'osx-x64' folder
    |       |--- native.dylib
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[vérifications à l’exécution]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[CLI .NET]: /dotnet/core/tools/?tabs=netcore2x
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[Utilisation de Visual Studio Code pour le débogage des applets de commande compilées]: vscode/using-vscode-for-debugging-compiled-cmdlets.md
[Using Visual Studio Code for debugging compiled cmdlets]: vscode/using-vscode-for-debugging-compiled-cmdlets.md
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Gallery]: https://www.powershellgallery.com
[Analyseur de portabilité .NET]: https://github.com/Microsoft/dotnet-apiport
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/scripting/gallery/concepts/module-psedition-support
[Catalogue RID .NET]: /dotnet/core/rid-catalog
[.NET RID Catalog]: /dotnet/core/rid-catalog
