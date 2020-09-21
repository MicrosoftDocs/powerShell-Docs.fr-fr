---
title: Guide pratique pour créer un module binaire de bibliothèque standard
description: La bibliothèque standard PowerShell nous permet de créer des modules multiplateformes qui fonctionnent à la fois dans PowerShell Core et avec Windows PowerShell 5.1.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: ff6a49f70a3fb77f5a30cc909d53bb77b3cd7d43
ms.sourcegitcommit: 8c01e56f0c10ff2637955dc892ea78432d563a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88702743"
---
# <a name="how-to-create-a-standard-library-binary-module"></a><span data-ttu-id="f2c33-103">Guide pratique pour créer un module binaire de bibliothèque standard</span><span class="sxs-lookup"><span data-stu-id="f2c33-103">How to create a Standard Library binary module</span></span>

<span data-ttu-id="f2c33-104">J’ai récemment eu une idée pour le module que je voulais implémenter en tant que module binaire.</span><span class="sxs-lookup"><span data-stu-id="f2c33-104">I recently had an idea for module that I wanted to implement as a binary module.</span></span> <span data-ttu-id="f2c33-105">Je dois encore en créer une en utilisant la [bibliothèque standard PowerShell][], donc cela semblait être une bonne opportunité.</span><span class="sxs-lookup"><span data-stu-id="f2c33-105">I have yet to create one using the [PowerShell Standard Library][] so this felt like a good opportunity.</span></span> <span data-ttu-id="f2c33-106">J’ai utilisé le guide [Création d’un module binaire multiplateforme][] pour créer ce module sans rencontrer d’obstacles.</span><span class="sxs-lookup"><span data-stu-id="f2c33-106">I used the [Creating a cross-platform binary module][] guide to create this module without any roadblocks.</span></span>
<span data-ttu-id="f2c33-107">Nous allons parcourir ce même processus, auquel j’ajouterai quelques commentaires.</span><span class="sxs-lookup"><span data-stu-id="f2c33-107">We're going to walk that same process and I'll add a little extra commentary along the way.</span></span>

> [!NOTE]
> <span data-ttu-id="f2c33-108">La [Version d’origine][] de cet article est parue sur le blog écrit par [@KevinMarquette][].</span><span class="sxs-lookup"><span data-stu-id="f2c33-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="f2c33-109">L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu.</span><span class="sxs-lookup"><span data-stu-id="f2c33-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="f2c33-110">Consultez son blog sur [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="f2c33-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-the-powershell-standard-library"></a><span data-ttu-id="f2c33-111">Qu’est-ce que la bibliothèque standard PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="f2c33-111">What is the PowerShell Standard Library?</span></span>

<span data-ttu-id="f2c33-112">La bibliothèque standard PowerShell nous permet de créer des modules multiplateformes qui fonctionnent à la fois dans PowerShell Core et avec Windows PowerShell 5.1 (ou 3.0).</span><span class="sxs-lookup"><span data-stu-id="f2c33-112">The PowerShell Standard Library allows us to create cross platform modules that work in both PowerShell Core and with Windows PowerShell 5.1 (or 3.0).</span></span>

## <a name="planning-our-module"></a><span data-ttu-id="f2c33-113">Planification de notre module</span><span class="sxs-lookup"><span data-stu-id="f2c33-113">Planning our module</span></span>

<span data-ttu-id="f2c33-114">Le plan pour ce module est de créer un dossier `src` pour le code C# et de structurer le reste comme je le ferais pour un module de script.</span><span class="sxs-lookup"><span data-stu-id="f2c33-114">The plan for this module is to create a `src` folder for the C# code and structure the rest like I would for a script module.</span></span> <span data-ttu-id="f2c33-115">Ceci inclut l’utilisation d’un script de génération pour compiler tous les éléments dans un dossier `output`.</span><span class="sxs-lookup"><span data-stu-id="f2c33-115">This includes using a build script to compile everything into an `output` folder.</span></span> <span data-ttu-id="f2c33-116">La structure des dossiers se présente comme ceci :</span><span class="sxs-lookup"><span data-stu-id="f2c33-116">The folder structure looks like this:</span></span>

```
MyModule
├───src
├───Output
│   └───MyModule
├───MyModule
│   ├───Data
│   ├───Private
│   └───Public
└───Tests
```

## <a name="getting-started"></a><span data-ttu-id="f2c33-117">Mise en route</span><span class="sxs-lookup"><span data-stu-id="f2c33-117">Getting Started</span></span>

<span data-ttu-id="f2c33-118">J’utilise normalement un modèle Plaster, mais mon modèle actuel ne prend pas encore en charge les modules binaires.</span><span class="sxs-lookup"><span data-stu-id="f2c33-118">I normally use a Plaster template but my current template doesn't have any binary module support yet.</span></span> <span data-ttu-id="f2c33-119">Ce n’est pas un gros problème.</span><span class="sxs-lookup"><span data-stu-id="f2c33-119">Not a big deal.</span></span> <span data-ttu-id="f2c33-120">Je vais cette fois le créer manuellement.</span><span class="sxs-lookup"><span data-stu-id="f2c33-120">I'll create this one by hand this time.</span></span>

<span data-ttu-id="f2c33-121">Je dois d’abord créer le dossier, puis le dépôt Git.</span><span class="sxs-lookup"><span data-stu-id="f2c33-121">First I need to create the folder and create the git repo.</span></span> <span data-ttu-id="f2c33-122">J’utilise `$module` comme espace réservé pour le nom du module.</span><span class="sxs-lookup"><span data-stu-id="f2c33-122">I'm using `$module` as a placeholder for the module name.</span></span> <span data-ttu-id="f2c33-123">Vous pourrez ainsi réutiliser ces exemples plus facilement si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="f2c33-123">This should make it easier for you to reuse these examples if needed.</span></span>

```powershell
$module = 'MyModule'
New-Item -Path $module -Type Directory
Set-Location $module
git init
```

<span data-ttu-id="f2c33-124">Je crée ensuite les dossiers de niveau racine.</span><span class="sxs-lookup"><span data-stu-id="f2c33-124">Then create the root level folders.</span></span>

```powershell
New-Item -Path 'src' -Type Directory
New-Item -Path 'Output' -Type Directory
New-Item -Path 'Tests' -Type Directory
New-Item -Path $module -Type Directory
```

### <a name="binary-module-setup"></a><span data-ttu-id="f2c33-125">Configuration du module binaire</span><span class="sxs-lookup"><span data-stu-id="f2c33-125">Binary module setup</span></span>

<span data-ttu-id="f2c33-126">Cet article est principalement consacré au module binaire et c’est donc là que nous allons commencer.</span><span class="sxs-lookup"><span data-stu-id="f2c33-126">This article os focused on the binary module so that is where we'll start.</span></span> <span data-ttu-id="f2c33-127">Cette section utilise des exemples provenant du guide [Création d’un module binaire multiplateforme][].</span><span class="sxs-lookup"><span data-stu-id="f2c33-127">This section pulls examples from the [Creating a cross-platform binary module][] guide.</span></span> <span data-ttu-id="f2c33-128">Consultez ce guide si vous avez besoin de plus de détails ou si vous rencontrez des problèmes.</span><span class="sxs-lookup"><span data-stu-id="f2c33-128">Review that guide if you need more details or have any issues.</span></span>

<span data-ttu-id="f2c33-129">Nous voulons d’abord vérifier la version du [SDK .NET Core][] que nous avons installée.</span><span class="sxs-lookup"><span data-stu-id="f2c33-129">First thing we want to do is check the version of the [dotnet core SDK][] that we installed.</span></span> <span data-ttu-id="f2c33-130">J’utilise 2.1.4, mais vous devez avoir 2.0.0 ou ultérieur avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f2c33-130">I'm using 2.1.4, but you should have 2.0.0 or newer before continuing.</span></span>

```powershell
PS> dotnet --version
2.1.4
```

<span data-ttu-id="f2c33-131">Je travaille dans le dossier `src` pour cette section.</span><span class="sxs-lookup"><span data-stu-id="f2c33-131">I'm working out of the `src` folder for this section.</span></span>

```powershell
Set-Location 'src'
```

<span data-ttu-id="f2c33-132">Avec la commande dotnet, créez une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="f2c33-132">Using the dotnet command, create a new class library.</span></span>

```powershell
dotnet new classlib --name $module
```

<span data-ttu-id="f2c33-133">Ceci a créé le projet de bibliothèque dans un sous-dossier, mais je ne veux pas ce niveau supplémentaire d’imbrication.</span><span class="sxs-lookup"><span data-stu-id="f2c33-133">This created the library project in a subfolder but I don't want that extra level of nesting.</span></span> <span data-ttu-id="f2c33-134">Je vais déplacer ces fichiers au niveau immédiatement supérieur.</span><span class="sxs-lookup"><span data-stu-id="f2c33-134">I'm going to move those files up a level.</span></span>

```powershell
Move-Item -Path .\$module\* -Destination .\
Remove-Item $module -Recurse
```

<span data-ttu-id="f2c33-135">Définissez la version du SDK .NET Core pour le projet.</span><span class="sxs-lookup"><span data-stu-id="f2c33-135">Set the .NET core SDK version for the project.</span></span> <span data-ttu-id="f2c33-136">J’ai le SDK 2.1 : je vais donc spécifier 2.1.0.</span><span class="sxs-lookup"><span data-stu-id="f2c33-136">I have the 2.1 SDK so I'm going to specify 2.1.0.</span></span>
<span data-ttu-id="f2c33-137">Utilisez 2.0.0 si vous utilisez le SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="f2c33-137">Use 2.0.0 if you're using the 2.0 SDK.</span></span>

```powershell
dotnet new globaljson --sdk-version 2.1.0
```

<span data-ttu-id="f2c33-138">Ajoutez le [package NuGet][] de la bibliothèque standard PowerShell au projet.</span><span class="sxs-lookup"><span data-stu-id="f2c33-138">Add the PowerShell Standard Library [NuGet package][] to the project.</span></span> <span data-ttu-id="f2c33-139">Veillez à utiliser la version la plus récente disponible pour le niveau de compatibilité dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="f2c33-139">Make sure you use the most recent version available for the level of compatibility that you need.</span></span> <span data-ttu-id="f2c33-140">Je devrais utiliser par défaut la dernière version, mais je ne pense pas que ce module utilise des fonctionnalités plus récentes que celles de PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f2c33-140">I would default to the latest version but I don't think this module leverages any features newer than PowerShell 3.0.</span></span>

```powershell
dotnet add package PowerShellStandard.Library --version 7.0.0-preview.1
```

<span data-ttu-id="f2c33-141">Nous devrions avoir un dossier src qui se présente comme ceci :</span><span class="sxs-lookup"><span data-stu-id="f2c33-141">We should have a src folder that looks like this:</span></span>

```powershell
PS> Get-ChildItem
    Directory: \MyModule\src

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        7/14/2018   9:51 PM                obj
-a----        7/14/2018   9:51 PM             86 Class1.cs
-a----        7/14/2018  10:03 PM            259 MyModule.csproj
-a----        7/14/2018  10:05 PM             45 global.json
```

<span data-ttu-id="f2c33-142">Nous sommes maintenant prêts à ajouter notre propre code au projet.</span><span class="sxs-lookup"><span data-stu-id="f2c33-142">Now we're ready to add our own code to the project.</span></span>

### <a name="building-a-binary-cmdlet"></a><span data-ttu-id="f2c33-143">Création d’une applet de commande binaire</span><span class="sxs-lookup"><span data-stu-id="f2c33-143">Building a binary cmdlet</span></span>

<span data-ttu-id="f2c33-144">Nous devons mettre à jour `src\Class1.cs` pour qu’il contienne cette applet de commande de démarrage :</span><span class="sxs-lookup"><span data-stu-id="f2c33-144">We need to update the `src\Class1.cs` to contain this starter cmdlet:</span></span>

```csharp
using System;
using System.Management.Automation;

namespace MyModule
{
    [Cmdlet( VerbsDiagnostic.Resolve , "MyCmdlet")]
    public class ResolveMyCmdletCommand : PSCmdlet
    {
        [Parameter(Position=0)]
        public Object InputObject { get; set; }

        protected override void EndProcessing()
        {
            this.WriteObject(this.InputObject);
            base.EndProcessing();
        }
    }
}
```

<span data-ttu-id="f2c33-145">Renommez le fichier pour qu’il corresponde au nom de la classe.</span><span class="sxs-lookup"><span data-stu-id="f2c33-145">Rename the file to match the class name.</span></span>

```powershell
Rename-Item .\Class1.cs .\ResolveMyCmdletCommand.cs
```

<span data-ttu-id="f2c33-146">Nous pouvons ensuite générer notre module.</span><span class="sxs-lookup"><span data-stu-id="f2c33-146">Then we can build our module.</span></span>

```powershell
PS> dotnet build

Microsoft (R) Build Engine version 15.5.180.51428 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

Restore completed in 18.19 ms for C:\workspace\MyModule\src\MyModule.csproj.
MyModule -> C:\workspace\MyModule\src\bin\Debug\netstandard2.0\MyModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:02.19
```

<span data-ttu-id="f2c33-147">Nous pouvons appeler `Import-Module` sur la nouvelle DLL pour charger notre nouvelle applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f2c33-147">We can call `Import-Module` on the new dll to load our new CMDlet.</span></span>

```powershell
PS> Import-Module .\bin\Debug\netstandard2.0\$module.dll
PS> Get-Command -Module $module

CommandType Name                    Version Source
----------- ----                    ------- ------
Cmdlet      Resolve-MyCmdlet        1.0.0.0 MyModule
```

<span data-ttu-id="f2c33-148">Si l’importation échoue sur votre système, essayez en effectuant une mise à jour de .NET vers la version 4.7.1 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="f2c33-148">If the import fails on your system, try updating .NET to 4.7.1 or newer.</span></span> <span data-ttu-id="f2c33-149">Le guide [Création d’un module binaire multiplateforme][] contient plus de détails sur la prise en charge de .NET et la compatibilité des versions antérieures de .NET.</span><span class="sxs-lookup"><span data-stu-id="f2c33-149">The [Creating a cross-platform binary module][] guide goes into more details on .NET support and compatibility for older versions of .NET.</span></span>

### <a name="module-manifest"></a><span data-ttu-id="f2c33-150">Manifeste du module</span><span class="sxs-lookup"><span data-stu-id="f2c33-150">Module manifest</span></span>

<span data-ttu-id="f2c33-151">Nous pouvons importer la DLL et avoir un module qui fonctionne.</span><span class="sxs-lookup"><span data-stu-id="f2c33-151">It's cool that we can import the dll and have a working module.</span></span> <span data-ttu-id="f2c33-152">Je vais continuer et créer un manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="f2c33-152">I like to keep going with it and create a module manifest.</span></span> <span data-ttu-id="f2c33-153">Nous avons besoin du manifeste si nous voulons publier ultérieurement sur PSGallery.</span><span class="sxs-lookup"><span data-stu-id="f2c33-153">We need the manifest if we want to publish to the PSGallery later.</span></span>

<span data-ttu-id="f2c33-154">À partir de la racine de notre projet, nous pouvons exécuter cette commande pour créer le manifeste du module dont nous avons besoin.</span><span class="sxs-lookup"><span data-stu-id="f2c33-154">From the root of our project, we can run this command to create the module manifest that we need.</span></span>

```powershell
$manifestSplat = @{
    Path              = ".\$module\$module.psd1"
    Author            = 'Kevin Marquette'
    NestedModules     = @('bin\MyModule.dll')
    RootModule        = "$module.psm1"
    FunctionsToExport = @('Resolve-MyCmdlet')
}
New-ModuleManifest @manifestSplat
```

<span data-ttu-id="f2c33-155">Je vais également créer un module racine vide pour les fonctions PowerShell futures.</span><span class="sxs-lookup"><span data-stu-id="f2c33-155">I'm also going to create an empty root module for future PowerShell functions.</span></span>

```powershell
Set-Content -Value '' -Path ".\$module\$module.psm1"
```

<span data-ttu-id="f2c33-156">Ceci me permet de mélanger des fonctions PowerShell normales et des applets de commande binaires dans le même projet.</span><span class="sxs-lookup"><span data-stu-id="f2c33-156">This allows me to mix both normal PowerShell functions and binary Cmdlets in the same project.</span></span>

### <a name="building-the-full-module"></a><span data-ttu-id="f2c33-157">Génération du module complet</span><span class="sxs-lookup"><span data-stu-id="f2c33-157">Building the full module</span></span>

<span data-ttu-id="f2c33-158">Je compile tout ensemble dans un dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="f2c33-158">I compile everything together into an output folder.</span></span> <span data-ttu-id="f2c33-159">Pour cela, nous devons créer un script de génération.</span><span class="sxs-lookup"><span data-stu-id="f2c33-159">We need to create a build script to do that.</span></span> <span data-ttu-id="f2c33-160">Je devrais normalement l’ajouter à un script `Invoke-Build`, mais pour cet exemple, nous pouvons procéder plus simplement.</span><span class="sxs-lookup"><span data-stu-id="f2c33-160">I would normally add this to an `Invoke-Build` script, but we can keep it simple for this example.</span></span> <span data-ttu-id="f2c33-161">Ajoutez ceci à un fichier `build.ps1` à la racine du projet.</span><span class="sxs-lookup"><span data-stu-id="f2c33-161">Add this to a `build.ps1` at the root of the project.</span></span>

```powershell
$module = 'MyModule'
Push-Location $PSScriptRoot

dotnet build $PSScriptRoot\src -o $PSScriptRoot\output\$module\bin
Copy-Item "$PSScriptRoot\$module\*" "$PSScriptRoot\output\$module" -Recurse -Force

Import-Module "$PSScriptRoot\Output\$module\$module.psd1"
Invoke-Pester "$PSScriptRoot\Tests"
```

<span data-ttu-id="f2c33-162">Ces commandes génèrent notre DLL et la placent dans notre dossier `output\$module\bin`.</span><span class="sxs-lookup"><span data-stu-id="f2c33-162">These commands build our DLL and place it into our `output\$module\bin` folder.</span></span> <span data-ttu-id="f2c33-163">Elles copient ensuite les autres fichiers du module à leur emplacement de destination.</span><span class="sxs-lookup"><span data-stu-id="f2c33-163">It then copies the other module files into place.</span></span>

```
Output
└───MyModule
    │   MyModule.psd1
    │   MyModule.psm1
    │
    └───bin
            MyModule.deps.json
            MyModule.dll
            MyModule.pdb
```

<span data-ttu-id="f2c33-164">À ce stade, nous pouvons importer notre module avec le fichier psd1.</span><span class="sxs-lookup"><span data-stu-id="f2c33-164">At this point, we can import our module with the psd1 file.</span></span>

```powershell
Import-Module ".\Output\$module\$module.psd1"
```

<span data-ttu-id="f2c33-165">À partir de là, nous pouvons déposer le dossier `.\Output\$module` dans notre répertoire `$env:PSModulePath` : il charge alors automatiquement notre commande chaque fois que nous en avons besoin.</span><span class="sxs-lookup"><span data-stu-id="f2c33-165">From here, we can drop the `.\Output\$module` folder into our `$env:PSModulePath` directory and it autoloads our command whenever we need it.</span></span>

### <a name="update-dotnet-new-psmodule"></a><span data-ttu-id="f2c33-166">Mise à jour : Nouveau PSModule pour dotnet</span><span class="sxs-lookup"><span data-stu-id="f2c33-166">Update: dotnet new PSModule</span></span>

<span data-ttu-id="f2c33-167">J’ai appris que l’outil `dotnet` avait un modèle `PSModule`.</span><span class="sxs-lookup"><span data-stu-id="f2c33-167">I learned that the `dotnet` tool has a `PSModule` template.</span></span>

<span data-ttu-id="f2c33-168">Toutes les étapes décrites ci-dessus restent valides, mais ce modèle fait l’économie de beaucoup d’entre elles. Il s’agit d’un modèle relativement nouveau qui continue de s’améliorer.</span><span class="sxs-lookup"><span data-stu-id="f2c33-168">All the steps that I outlined above are still valid, but this template cuts many of them out. It's still a fairly new template that is still getting some polish placed on it.</span></span> <span data-ttu-id="f2c33-169">Attendez-vous donc à ce qu’il évolue encore.</span><span class="sxs-lookup"><span data-stu-id="f2c33-169">Expect it to keep getting better from here.</span></span>

<span data-ttu-id="f2c33-170">Voici comment vous installez et comment vous utilisez le modèle PSModule.</span><span class="sxs-lookup"><span data-stu-id="f2c33-170">This is how you use install and use the PSModule template.</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
dotnet new psmodule
dotnet build
Import-Module "bin\Debug\netstandard2.0\$module.dll"
Get-Module $module
```

<span data-ttu-id="f2c33-171">Ce modèle minimaliste ajoute le SDK .NET et la bibliothèque standard PowerShell, et il crée un exemple de classe dans le projet.</span><span class="sxs-lookup"><span data-stu-id="f2c33-171">This minimally-viable template takes care of adding the .NET SDK, PowerShell Standard Library, and creates an example class in the project.</span></span> <span data-ttu-id="f2c33-172">Vous pouvez le générer et l’exécuter immédiatement.</span><span class="sxs-lookup"><span data-stu-id="f2c33-172">You can build it and run it right away.</span></span>

## <a name="important-details"></a><span data-ttu-id="f2c33-173">Détails importants</span><span class="sxs-lookup"><span data-stu-id="f2c33-173">Important details</span></span>

<span data-ttu-id="f2c33-174">Pour terminer cet article, voici quelques autres détails qui méritent d’être mentionnés.</span><span class="sxs-lookup"><span data-stu-id="f2c33-174">Before we end this article, here are a few other details worth mentioning.</span></span>

### <a name="unloading-dlls"></a><span data-ttu-id="f2c33-175">Déchargement des DLL</span><span class="sxs-lookup"><span data-stu-id="f2c33-175">Unloading DLLs</span></span>

<span data-ttu-id="f2c33-176">Une fois qu’un module binaire est chargé, vous ne pouvez pas réellement le décharger.</span><span class="sxs-lookup"><span data-stu-id="f2c33-176">Once a binary module is loaded, you can't really unload it.</span></span> <span data-ttu-id="f2c33-177">Le fichier DLL est verrouillé tant que vous ne le déchargez pas.</span><span class="sxs-lookup"><span data-stu-id="f2c33-177">The DLL file is locked until you unload it.</span></span> <span data-ttu-id="f2c33-178">Ce peut être ennuyeux pendant le développement, car quand vous apportez une modification et que vous voulez le générer, le fichier est souvent verrouillé.</span><span class="sxs-lookup"><span data-stu-id="f2c33-178">This can be annoying when developing because every time you make a change and want to build it, the file is often locked.</span></span> <span data-ttu-id="f2c33-179">La seule méthode fiable pour résoudre cela est de fermer la session PowerShell qui a chargé la DLL.</span><span class="sxs-lookup"><span data-stu-id="f2c33-179">The only reliable way to resolve this is to close the PowerShell session that loaded the DLL.</span></span>

### <a name="vs-code-reload-window-action"></a><span data-ttu-id="f2c33-180">Action de la fenêtre de rechargement de VS Code</span><span class="sxs-lookup"><span data-stu-id="f2c33-180">VS Code reload window action</span></span>

<span data-ttu-id="f2c33-181">J’effectue la plupart de mon travail de développement PowerShell dans [Code Visual Studio][].</span><span class="sxs-lookup"><span data-stu-id="f2c33-181">I do most of my PowerShell dev work in [VS Code][].</span></span> <span data-ttu-id="f2c33-182">Quand je travaille sur un module binaire (ou un module avec des classes), j’ai l’habitude de recharger VS Code chaque fois que je lance une génération.</span><span class="sxs-lookup"><span data-stu-id="f2c33-182">When I'm working on a binary module (or a module with classes), I've gotten into the habit of reloading VS Code every time I build.</span></span>
<span data-ttu-id="f2c33-183"><kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> fait apparaître la fenêtre de commande et `Reload Window` est toujours en haut de ma liste.</span><span class="sxs-lookup"><span data-stu-id="f2c33-183"><kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> pops the command window and `Reload Window` is always at the top of my list.</span></span>

### <a name="nested-powershell-sessions"></a><span data-ttu-id="f2c33-184">Sessions PowerShell imbriquées</span><span class="sxs-lookup"><span data-stu-id="f2c33-184">Nested PowerShell sessions</span></span>

<span data-ttu-id="f2c33-185">Une autre option est d’avoir une bonne couverture de test de Pester.</span><span class="sxs-lookup"><span data-stu-id="f2c33-185">One other option is to have good Pester test coverage.</span></span> <span data-ttu-id="f2c33-186">Vous pouvez ensuite ajuster le script build.ps1 pour démarrer une nouvelle session PowerShell, effectuer la génération, exécuter les tests et fermer la session.</span><span class="sxs-lookup"><span data-stu-id="f2c33-186">Then you can adjust the build.ps1 script to start a new PowerShell session, perform the build, run the tests, and close the session.</span></span>

### <a name="updating-installed-modules"></a><span data-ttu-id="f2c33-187">Mise à jour des modules installés</span><span class="sxs-lookup"><span data-stu-id="f2c33-187">Updating installed modules</span></span>

<span data-ttu-id="f2c33-188">Ce verrouillage peut être ennuyeux quand vous essayez de mettre à jour votre module installé localement.</span><span class="sxs-lookup"><span data-stu-id="f2c33-188">This locking can be annoying when trying to update your locally installed module.</span></span> <span data-ttu-id="f2c33-189">Si une session l’a chargé, vous devez la trouver et la fermer.</span><span class="sxs-lookup"><span data-stu-id="f2c33-189">If any session has it loaded, you have to go hunt it down and close it.</span></span> <span data-ttu-id="f2c33-190">Ce n’est pas vraiment un problème lors de l’installation à partir de PSGallery, car la gestion de versions du module place le nouveau dans un dossier différent.</span><span class="sxs-lookup"><span data-stu-id="f2c33-190">This is less of an issue when installing from a PSGallery because module versioning places the new one in a different folder.</span></span>

<span data-ttu-id="f2c33-191">Vous pouvez configurer une PSGallery locale et publier sur celle-ci dans le cadre de votre génération.</span><span class="sxs-lookup"><span data-stu-id="f2c33-191">You can set up a local PSGallery and publish to that as part of your build.</span></span> <span data-ttu-id="f2c33-192">Effectuez ensuite votre installation locale à partir de cette PSGallery.</span><span class="sxs-lookup"><span data-stu-id="f2c33-192">Then do your local install from that PSGallery.</span></span> <span data-ttu-id="f2c33-193">Cela peut sembler être beaucoup de travail, mais ce peut être en fait aussi simple que démarrer un conteneur Docker.</span><span class="sxs-lookup"><span data-stu-id="f2c33-193">This sounds like a lot of work, but this can be as simple as starting a docker container.</span></span> <span data-ttu-id="f2c33-194">Je décris un moyen de faire cela dans mon billet [Utilisation d’un serveur NuGet pour un PSRepository][].</span><span class="sxs-lookup"><span data-stu-id="f2c33-194">I cover a way to do that in my post on [Using a NuGet server for a PSRepository][].</span></span>

## <a name="why-binary-modules"></a><span data-ttu-id="f2c33-195">Pourquoi des modules binaires ?</span><span class="sxs-lookup"><span data-stu-id="f2c33-195">Why binary modules?</span></span>

<span data-ttu-id="f2c33-196">Je viens de décrire directement comment créer un module binaire et je n’ai pas expliqué pourquoi vous voulez en faire un.</span><span class="sxs-lookup"><span data-stu-id="f2c33-196">I jumped right into how to make a binary module and didn't mention why you want to make one.</span></span> <span data-ttu-id="f2c33-197">En réalité, vous écrivez du code C#, et vous donnez un accès facile aux applets de commande et aux fonctions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f2c33-197">In reality, you are writing C# and give up easy access to PowerShell Cmdlets and functions.</span></span> <span data-ttu-id="f2c33-198">C’est la raison principale pour laquelle je ne suis pas passé plus tôt aux modules binaires.</span><span class="sxs-lookup"><span data-stu-id="f2c33-198">That is the main reason why I have not shifted to binary modules sooner.</span></span>

<span data-ttu-id="f2c33-199">Cependant, si vous créez un module qui ne dépend pas d’un grand nombre d’autres commandes PowerShell, l’avantage en termes de performances peut être significatif.</span><span class="sxs-lookup"><span data-stu-id="f2c33-199">But if you are creating a module that doesn't depend on a lot of other PowerShell commands, the performance benefit can be significant.</span></span> <span data-ttu-id="f2c33-200">En passant à C#, vous vous affranchissez de la charge ajoutée par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f2c33-200">By dropping into C#, you get to shed the overhead added by PowerShell.</span></span> <span data-ttu-id="f2c33-201">PowerShell a été optimisé pour l’administrateur et non pas pour l’ordinateur, et ceci ajoute une petite surcharge.</span><span class="sxs-lookup"><span data-stu-id="f2c33-201">PowerShell was optimized for the administrator, not the computer, and that adds a little overhead.</span></span>

<span data-ttu-id="f2c33-202">Dans mon entreprise, nous avons un processus critique qui effectue beaucoup de travail avec JSON et des tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="f2c33-202">At work, we have a critical process that does a lot of work with JSON and Hashtables.</span></span> <span data-ttu-id="f2c33-203">Nous avons optimisé le code PowerShell autant que possible, mais l’exécution de ce traitement durait encore 12 minutes.</span><span class="sxs-lookup"><span data-stu-id="f2c33-203">We optimized the PowerShell as much as we could but this process was still running for 12 minutes.</span></span> <span data-ttu-id="f2c33-204">Le module contenait déjà beaucoup de code PowerShell de style C#.</span><span class="sxs-lookup"><span data-stu-id="f2c33-204">The module already contained a lot of C# style PowerShell.</span></span> <span data-ttu-id="f2c33-205">Ceci a rendu la conversion en module binaire propre et facile à faire.</span><span class="sxs-lookup"><span data-stu-id="f2c33-205">This made the conversion to a binary module clean and easy to do.</span></span> <span data-ttu-id="f2c33-206">Notre conversion a réduit la durée d’exécution de ce traitement de 12 minutes à moins de 4 minutes.</span><span class="sxs-lookup"><span data-stu-id="f2c33-206">Our conversion cut that process down from over 12 minutes to under four minutes.</span></span>

### <a name="hybrid-modules"></a><span data-ttu-id="f2c33-207">Modules hybrides</span><span class="sxs-lookup"><span data-stu-id="f2c33-207">Hybrid modules</span></span>

<span data-ttu-id="f2c33-208">Vous pouvez combiner des applets de commande binaires avec des fonctions avancées PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f2c33-208">You can mix binary Cmdlets with PowerShell advanced functions.</span></span> <span data-ttu-id="f2c33-209">C’est exactement ce que je fais dans ce guide.</span><span class="sxs-lookup"><span data-stu-id="f2c33-209">That is exactly what I'm doing in this guide.</span></span> <span data-ttu-id="f2c33-210">Vous pouvez prendre tout ce que vous savez sur les modules de script : tout s’applique de la même façon.</span><span class="sxs-lookup"><span data-stu-id="f2c33-210">You can take everything you know about script modules and it all applies the same way.</span></span>
<span data-ttu-id="f2c33-211">Le fichier `psm1` vide que j’ai créé aujourd’hui est là seulement pour vous permettre d’y placer ultérieurement d’autres fonctions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f2c33-211">The empty `psm1` file that I created today is there just so you can drop in other PowerShell functions later.</span></span>

<span data-ttu-id="f2c33-212">Presque toutes les applets de commande compilées que nous avons créées étaient initialement des fonctions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f2c33-212">Almost all of the compiled cmdlets that we created started out as a PowerShell function first.</span></span> <span data-ttu-id="f2c33-213">Tous nos modules binaires sont véritablement des modules hybrides.</span><span class="sxs-lookup"><span data-stu-id="f2c33-213">All of our binary modules are really hybrid modules.</span></span>

### <a name="build-scripts"></a><span data-ttu-id="f2c33-214">Scripts de génération</span><span class="sxs-lookup"><span data-stu-id="f2c33-214">Build scripts</span></span>

<span data-ttu-id="f2c33-215">J’ai veillé ici à ce que le script de génération reste simple.</span><span class="sxs-lookup"><span data-stu-id="f2c33-215">I kept the build script simple here.</span></span> <span data-ttu-id="f2c33-216">J’utilise généralement un long script `Invoke-Build` dans le cadre de mon pipeline CI/CD.</span><span class="sxs-lookup"><span data-stu-id="f2c33-216">I generally use a large `Invoke-Build` script as part of my CI/CD pipeline.</span></span> <span data-ttu-id="f2c33-217">Il en fait beaucoup plus, comme exécuter des tests Pester, exécuter PSScriptAnalyzer, gérer les versions et publier sur PSGallery.</span><span class="sxs-lookup"><span data-stu-id="f2c33-217">It does more magic like running Pester tests, running PSScriptAnalyzer, managing versioning, and publishing to the PSGallery.</span></span> <span data-ttu-id="f2c33-218">Une fois que j’ai commencé à utiliser un script de génération pour mes modules, j’ai pu trouver un grand nombre de choses à y ajouter.</span><span class="sxs-lookup"><span data-stu-id="f2c33-218">Once I started using a build script for my modules, I was able to find lots of things to add to it.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="f2c33-219">Réflexions finales</span><span class="sxs-lookup"><span data-stu-id="f2c33-219">Final thoughts</span></span>

<span data-ttu-id="f2c33-220">Les modules binaires sont faciles à créer.</span><span class="sxs-lookup"><span data-stu-id="f2c33-220">Binary modules are easy to create.</span></span> <span data-ttu-id="f2c33-221">Je n’ai pas touché à la syntaxe C# pour la création d’une applet de commande, mais il y a beaucoup de documentation sur celle-ci dans le [Windows PowerShell SDK][].</span><span class="sxs-lookup"><span data-stu-id="f2c33-221">I didn't touch on the C# syntax for creating a Cmdlet, but there is plenty of documentation on it in the [Windows PowerShell SDK][].</span></span> <span data-ttu-id="f2c33-222">Il est tout à fait intéressant d’expérimenter cela comme un tremplin vers du C# plus complexe.</span><span class="sxs-lookup"><span data-stu-id="f2c33-222">It is definitely something worth experimenting with as a stepping stone into more serious C#.</span></span>

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[original version]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Bibliothèque standard PowerShell]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard Library]: https://github.com/PowerShell/PowerShellStandard
[Création d’un module binaire multiplateforme]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[Creating a cross-platform binary module]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[SDK .NET Core]: https://www.microsoft.com/net/download/core
[dotnet core SDK]: https://www.microsoft.com/net/download/core
[Utilisation d’un serveur NuGet pour un PSRepository]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Using a NuGet server for a PSRepository]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell-reference
[Code Visual Studio]: https://code.visualstudio.com
[VS Code]: https://code.visualstudio.com
[Package NuGet]: https://www.nuget.org/packages/PowerShellStandard.Library/
[nuget package]: https://www.nuget.org/packages/PowerShellStandard.Library/
