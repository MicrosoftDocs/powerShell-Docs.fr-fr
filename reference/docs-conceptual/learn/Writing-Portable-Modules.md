---
ms.date: 12/14/2018
keywords: powershell,applet de commande
title: Écriture de modules portables
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679209"
---
# <a name="portable-modules"></a><span data-ttu-id="2a4c0-103">Modules portables</span><span class="sxs-lookup"><span data-stu-id="2a4c0-103">Portable Modules</span></span>

<span data-ttu-id="2a4c0-104">Windows PowerShell est écrit pour [.NET Framework][] alors que PowerShell Core est écrit pour [.NET Core][].</span><span class="sxs-lookup"><span data-stu-id="2a4c0-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="2a4c0-105">Modules portables sont des modules qui fonctionnent dans Windows PowerShell et PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="2a4c0-106">Bien que .NET Framework et .NET Core sont hautement compatibles, il existe des différences dans les API disponibles entre les deux.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="2a4c0-107">Il existe également des différences dans les API disponibles dans Windows PowerShell et PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="2a4c0-108">Modules destinées à être utilisée dans les deux environnements doivent être conscient de ces différences.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="2a4c0-109">Portage d’un Module existant</span><span class="sxs-lookup"><span data-stu-id="2a4c0-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="2a4c0-110">Portage d’un PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="2a4c0-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="2a4c0-111">PowerShell SnapIns (PSSnapIn) ne sont pas pris en charge dans PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-111">PowerShell SnapIns (PSSnapIn) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="2a4c0-112">Toutefois, il est facile de convertir un PSSnapIn à un module PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="2a4c0-113">En règle générale, le code d’inscription PSSnapIn est dans un fichier source unique d’une classe qui dérive de [PSSnapIn][].</span><span class="sxs-lookup"><span data-stu-id="2a4c0-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="2a4c0-114">Supprimer ce fichier source à partir de la build ; Il n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="2a4c0-115">Utilisez [New-ModuleManifest][] pour créer un nouveau manifeste de module qui remplace la nécessité pour le code d’inscription PSSnapIn.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="2a4c0-116">Certaines des valeurs à partir de la PSSnapIn (par exemple, Description) peuvent être réutilisés dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-116">Some of the values from the PSSnapIn (such as Description) can be reused within the module manifest.</span></span>

<span data-ttu-id="2a4c0-117">Le `RootModule` propriété dans le manifeste de module doit être définie sur le nom de l’assembly (dll) qui implémente les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-117">The `RootModule` property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="2a4c0-118">L’Analyseur de portabilité .NET (également appelé APIPort)</span><span class="sxs-lookup"><span data-stu-id="2a4c0-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="2a4c0-119">Pour les modules de port écrits pour Windows PowerShell fonctionne avec PowerShell Core, commencez par le [Analyseur de portabilité .NET][].</span><span class="sxs-lookup"><span data-stu-id="2a4c0-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="2a4c0-120">Exécutez cet outil sur votre assembly compilé pour déterminer si les API .NET utilisé dans le module sont compatibles avec .NET Framework, .NET Core et autres runtimes .NET.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="2a4c0-121">L’outil suggère des API de remplacement s’ils existent.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="2a4c0-122">Sinon, vous devrez peut-être ajouter [vérifications à l’exécution][] et limiter les fonctionnalités non disponibles dans les runtimes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="2a4c0-123">Création d’un Module</span><span class="sxs-lookup"><span data-stu-id="2a4c0-123">Creating a New Module</span></span>

<span data-ttu-id="2a4c0-124">Si vous créez un nouveau module, la recommandation consiste à utiliser le [INTERFACE CLI .NET][].</span><span class="sxs-lookup"><span data-stu-id="2a4c0-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="2a4c0-125">Installation du modèle de Module PowerShell Standard</span><span class="sxs-lookup"><span data-stu-id="2a4c0-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="2a4c0-126">Une fois l’interface CLI .NET est installée, installez une bibliothèque de modèles pour générer un module PowerShell simple.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="2a4c0-127">Le module sera compatible avec Windows PowerShell, PowerShell Core, Windows, Linux et macOS.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="2a4c0-128">L’exemple suivant montre comment installer le modèle :</span><span class="sxs-lookup"><span data-stu-id="2a4c0-128">The following example shows how to install the template:</span></span>

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


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a><span data-ttu-id="2a4c0-129">Création d’un nouveau projet de Module</span><span class="sxs-lookup"><span data-stu-id="2a4c0-129">Creating a New Module Project</span></span>

<span data-ttu-id="2a4c0-130">Une fois que le modèle est installé, vous pouvez créer un nouveau projet de module PowerShell à l’aide de ce modèle.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="2a4c0-131">Dans cet exemple, le module d’exemple est appelé « myModule ».</span><span class="sxs-lookup"><span data-stu-id="2a4c0-131">In this example, the sample module is called 'myModule'.</span></span>

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

### <a name="building-the-module"></a><span data-ttu-id="2a4c0-132">Créer le Module</span><span class="sxs-lookup"><span data-stu-id="2a4c0-132">Building the Module</span></span>

<span data-ttu-id="2a4c0-133">Utilisez les commandes CLI de .NET standard pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-133">Use standard .NET CLI commands to build the project.</span></span>

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

### <a name="testing-the-module"></a><span data-ttu-id="2a4c0-134">Le Module de test</span><span class="sxs-lookup"><span data-stu-id="2a4c0-134">Testing the Module</span></span>

<span data-ttu-id="2a4c0-135">Après avoir généré le module, vous pouvez importer et exécuter l’applet de commande d’exemple.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

<span data-ttu-id="2a4c0-136">Les sections suivantes décrivent en détail certaines des technologies utilisées par ce modèle.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="2a4c0-137">Bibliothèque .NET standard</span><span class="sxs-lookup"><span data-stu-id="2a4c0-137">.NET Standard Library</span></span>

<span data-ttu-id="2a4c0-138">[.NET standard][] est une spécification formelle des API .NET qui sont disponibles dans toutes les implémentations de .NET.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="2a4c0-139">Ciblage de .NET Standard fonctionne avec les versions de .NET Framework et .NET Core qui sont compatibles avec cette version de .NET Standard de code managé.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="2a4c0-140">Bien qu’une API peut-être exister dans .NET Standard, l’implémentation des API dans .NET Core peut lever une `PlatformNotSupportedException` lors de l’exécution, et par conséquent, pour vérifier la compatibilité avec Windows PowerShell et PowerShell Core, la meilleure pratique consiste à exécuter des tests pour votre module dans les deux environnements.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="2a4c0-141">Également exécuter des tests sur Linux et macOS si votre module est destiné à être inter-plateformes.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="2a4c0-142">Ciblage de .NET Standard permet de s’assurer que, comme le module évolue, API incompatibles n’obtenir introduction accidentelle dans le module.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="2a4c0-143">Incompatibilités sont découvertes au moment de la compilation au lieu de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="2a4c0-144">Toutefois, il n’est pas nécessaire pour cibler .NET Standard pour un module pour travailler avec Windows PowerShell et PowerShell Core, tant que vous utilisez une API compatible.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="2a4c0-145">Le langage intermédiaire (IL) est compatible entre les deux runtimes.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="2a4c0-146">Vous pouvez cibler .NET Framework 4.6.1, qui est compatible avec .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="2a4c0-147">Si vous n’utilisez pas les API en dehors de .NET Standard 2.0, votre module fonctionne avec PowerShell Core 6 sans recompilation.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="2a4c0-148">Bibliothèque Standard de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a4c0-148">PowerShell Standard Library</span></span>

<span data-ttu-id="2a4c0-149">Le [PowerShell Standard][] bibliothèque est une spécification formelle des APIs PowerShell disponibles dans toutes les versions de PowerShell supérieures ou égales à la version de cette norme.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="2a4c0-150">Par exemple, [Standard PowerShell 5.1][] est compatible avec Windows PowerShell 5.1 et PowerShell Core 6.0 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="2a4c0-151">Nous vous recommandons de que vous compilez votre module à l’aide de la bibliothèque Standard de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="2a4c0-152">La bibliothèque garantit que les API sont disponibles et implémentée dans Windows PowerShell et PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="2a4c0-153">PowerShell Standard est destiné à toujours être compatible avec le transfert.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="2a4c0-154">Un module créé à l’aide de PowerShell 5.1 de bibliothèque Standard sera toujours compatible avec les futures versions de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="2a4c0-155">Manifeste de module</span><span class="sxs-lookup"><span data-stu-id="2a4c0-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="2a4c0-156">Indiquant la compatibilité avec Windows PowerShell et PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="2a4c0-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="2a4c0-157">Après avoir vérifié que votre module fonctionne avec Windows PowerShell et PowerShell Core, le manifeste de module doit indiquer explicitement compatibilité à l’aide de la [CompatiblePSEditions][] propriété.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="2a4c0-158">La valeur `Desktop` signifie que le module est compatible avec Windows PowerShell, alors que la valeur `Core` signifie que le module est compatible avec PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="2a4c0-159">Y compris les `Desktop` et `Core` signifie que le module est compatible avec Windows PowerShell et PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="2a4c0-160">`Core` ne pas automatiquement signifie que le module est compatible avec Windows, Linux et macOS.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="2a4c0-161">Le **CompatiblePSEditions** propriété a été introduite dans PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="2a4c0-162">Manifestes de module qui utilisent le **CompatiblePSEditions** propriété ne parviennent pas à charger dans les versions antérieures PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="2a4c0-163">Indiquant la compatibilité de système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="2a4c0-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="2a4c0-164">Tout d’abord, vérifiez que votre module fonctionne sur Linux et macOS.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="2a4c0-165">Ensuite, indiquent la compatibilité avec ces systèmes d’exploitation dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="2a4c0-166">Cela rend plus facile pour les utilisateurs à trouver votre module pour leur système d’exploitation lors de la publication à le [PowerShell Gallery][].</span><span class="sxs-lookup"><span data-stu-id="2a4c0-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="2a4c0-167">Dans le manifeste de module, le `PrivateData` propriété a un `PSData` sous-propriété.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="2a4c0-168">Le paramètre facultatif `Tags` propriété du `PSData` prend un tableau de valeurs qui s’affichent dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="2a4c0-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="2a4c0-169">PowerShell Gallery prend en charge les valeurs de compatibilité suivantes :</span><span class="sxs-lookup"><span data-stu-id="2a4c0-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="2a4c0-170">Légende</span><span class="sxs-lookup"><span data-stu-id="2a4c0-170">Tag</span></span>               | <span data-ttu-id="2a4c0-171">Description</span><span class="sxs-lookup"><span data-stu-id="2a4c0-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="2a4c0-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="2a4c0-172">PSEdition_Core</span></span>    | <span data-ttu-id="2a4c0-173">Compatible avec PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="2a4c0-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="2a4c0-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="2a4c0-174">PSEdition_Desktop</span></span> | <span data-ttu-id="2a4c0-175">Compatible avec Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a4c0-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="2a4c0-176">Windows</span><span class="sxs-lookup"><span data-stu-id="2a4c0-176">Windows</span></span>           | <span data-ttu-id="2a4c0-177">Compatible avec Windows</span><span class="sxs-lookup"><span data-stu-id="2a4c0-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="2a4c0-178">Linux</span><span class="sxs-lookup"><span data-stu-id="2a4c0-178">Linux</span></span>             | <span data-ttu-id="2a4c0-179">Compatible avec Linux (aucune distribution spécifique)</span><span class="sxs-lookup"><span data-stu-id="2a4c0-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="2a4c0-180">macOS</span><span class="sxs-lookup"><span data-stu-id="2a4c0-180">macOS</span></span>             | <span data-ttu-id="2a4c0-181">Compatible avec macOS</span><span class="sxs-lookup"><span data-stu-id="2a4c0-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="2a4c0-182">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2a4c0-182">Example:</span></span>

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

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[vérifications à l’exécution]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[INTERFACE CLI .NET]: /dotnet/core/tools/?tabs=netcore2x
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[Standard PowerShell 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Gallery]: https://www.powershellgallery.com
[Analyseur de portabilité .NET]: https://github.com/Microsoft/dotnet-apiport
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
