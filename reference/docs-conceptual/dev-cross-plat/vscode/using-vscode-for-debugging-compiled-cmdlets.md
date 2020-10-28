---
ms.date: 10/19/2020
keywords: powershell,applet de commande,débogage
title: Utilisation de Visual Studio Code pour déboguer des applets de commande compilées
description: Explique comment définir une tâche de génération et lancer la configuration d’un projet PSModule dans .NET Core
ms.openlocfilehash: b51a69110c64b386f5c3ccf2527d1e184ef89257
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501641"
---
# <a name="using-visual-studio-code-to-debug-compiled-cmdlets"></a><span data-ttu-id="23adf-104">Utilisation de Visual Studio Code pour déboguer des applets de commande compilées</span><span class="sxs-lookup"><span data-stu-id="23adf-104">Using Visual Studio Code to debug compiled cmdlets</span></span>

<span data-ttu-id="23adf-105">Ce guide vous montre comment déboguer de manière interactive du code source C# appartenant à un module PowerShell compilé à l’aide de Visual Studio Code (VS Code) et de l’extension C#.</span><span class="sxs-lookup"><span data-stu-id="23adf-105">This guide shows you how to interactively debug C# source code for a compiled PowerShell module using Visual Studio Code (VS Code) and the C# extension.</span></span>

<span data-ttu-id="23adf-106">Cet article suppose que vous êtes familiarisé avec le débogueur Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="23adf-106">Some familiarity with the Visual Studio Code debugger is assumed.</span></span>

- <span data-ttu-id="23adf-107">Pour une présentation générale du débogueur VS Code, consultez [Débogage dans Visual Studio Code][].</span><span class="sxs-lookup"><span data-stu-id="23adf-107">For a general introduction to the VS Code debugger, see [Debugging in Visual Studio Code][].</span></span>

- <span data-ttu-id="23adf-108">Pour obtenir des exemples de débogage de modules et de fichiers de script PowerShell, consultez [Utilisation de Visual Studio Code pour le débogage et l’édition à distance][].</span><span class="sxs-lookup"><span data-stu-id="23adf-108">For examples of debugging PowerShell script files and modules, see [Using Visual Studio Code for remote editing and debugging][].</span></span>

<span data-ttu-id="23adf-109">Ce guide suppose que vous avez lu et suivi les instructions du guide [Écriture de modules portables][].</span><span class="sxs-lookup"><span data-stu-id="23adf-109">This guide assumes you have read and followed the instructions in the [Writing Portable Modules][] guide.</span></span>

## <a name="creating-a-build-task"></a><span data-ttu-id="23adf-110">Création d’une tâche de génération</span><span class="sxs-lookup"><span data-stu-id="23adf-110">Creating a build task</span></span>

<span data-ttu-id="23adf-111">Générez automatiquement votre projet avant de lancer une session de débogage.</span><span class="sxs-lookup"><span data-stu-id="23adf-111">Build your project automatically before launching a debugging session.</span></span> <span data-ttu-id="23adf-112">Le fait de regénérer le projet vous permet de déboguer la version la plus récente de votre code.</span><span class="sxs-lookup"><span data-stu-id="23adf-112">Rebuilding ensures that you debug the latest version of your code.</span></span>

<span data-ttu-id="23adf-113">Configurez une tâche de génération :</span><span class="sxs-lookup"><span data-stu-id="23adf-113">Configure a build task:</span></span>

1. <span data-ttu-id="23adf-114">Dans la **palette de commandes** , exécutez la commande **Configurer la tâche de génération par défaut** .</span><span class="sxs-lookup"><span data-stu-id="23adf-114">In the **Command Palette** , run the **Configure Default Build Task** command.</span></span>

   ![Exécution de la commande Configurer la tâche de génération par défaut](media/using-vscode-for-debugging-compiled-cmdlets/configure-default-build-task.png)

1. <span data-ttu-id="23adf-116">Dans la boîte de dialogue **Sélectionner une tâche à configurer** , choisissez **Créer le fichier tasks.json à partir d’un modèle** .</span><span class="sxs-lookup"><span data-stu-id="23adf-116">In the **Select a task to configure** dialog, choose **Create tasks.json file from template** .</span></span>

1. <span data-ttu-id="23adf-117">Dans la boîte de dialogue **Sélectionner un modèle de tâche** , choisissez **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="23adf-117">In the **Select a Task Template** dialog, choose **.NET Core** .</span></span>

<span data-ttu-id="23adf-118">S’il n’existe pas déjà, le fichier `tasks.json` est créé.</span><span class="sxs-lookup"><span data-stu-id="23adf-118">A new `tasks.json` file is created if one doesn't exist yet.</span></span>

<span data-ttu-id="23adf-119">Pour tester votre tâche de génération :</span><span class="sxs-lookup"><span data-stu-id="23adf-119">To test your build task:</span></span>

1. <span data-ttu-id="23adf-120">Dans la **palette de commandes** , exécutez la commande **Exécuter la tâche de build** .</span><span class="sxs-lookup"><span data-stu-id="23adf-120">In the **Command Palette** , run the **Run Build Task** command.</span></span>

1. <span data-ttu-id="23adf-121">Dans la boîte de dialogue **Sélectionner la tâche de génération à exécuter** , choisissez **build** .</span><span class="sxs-lookup"><span data-stu-id="23adf-121">In the **Select the build task to run** dialog, choose **build** .</span></span>

### <a name="information-about-dll-files-being-locked"></a><span data-ttu-id="23adf-122">Informations sur les fichiers DLL verrouillés</span><span class="sxs-lookup"><span data-stu-id="23adf-122">Information about DLL files being locked</span></span>

<span data-ttu-id="23adf-123">Par défaut, une tâche de génération réussie n’affiche pas de sortie dans le volet Terminal.</span><span class="sxs-lookup"><span data-stu-id="23adf-123">By default, a successful build doesn't show output in the terminal pane.</span></span> <span data-ttu-id="23adf-124">Si vous voyez une sortie qui contient le texte **Project file doesn’t exist** (Le fichier projet n’existe pas), vous devez modifier le fichier `tasks.json`.</span><span class="sxs-lookup"><span data-stu-id="23adf-124">If you see output that contains the text **Project file doesn't exist** , you should edit the `tasks.json` file.</span></span> <span data-ttu-id="23adf-125">Ajoutez le chemin explicite au projet C# au format suivant : `"${workspaceFolder}/myModule"`.</span><span class="sxs-lookup"><span data-stu-id="23adf-125">Include the explicit path to the C# project expressed as `"${workspaceFolder}/myModule"`.</span></span> <span data-ttu-id="23adf-126">Dans cet exemple, `myModule` est le nom du dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="23adf-126">In this example, `myModule` is the name of the project folder.</span></span> <span data-ttu-id="23adf-127">Cette entrée doit être placée après l’entrée `build` de la liste `args` :</span><span class="sxs-lookup"><span data-stu-id="23adf-127">This entry must go after the `build` entry in the `args` list as follows:</span></span>

```json
    {
        "label": "build",
        "command": "dotnet",
        "type": "shell",
        "args": [
            "build",
            "${workspaceFolder}/myModule",
            // Ask dotnet build to generate full paths for file names.
            "/property:GenerateFullPaths=true",
            // Do not generate summary otherwise it leads to duplicate errors in Problems panel
            "/consoleloggerparameters:NoSummary",
        ],
        "group": "build",
        "presentation": {
            "reveal": "silent"
        },
        "problemMatcher": "$msCompile"
    }
```

<span data-ttu-id="23adf-128">Lors du débogage, votre module DLL est importé dans la session PowerShell, dans le terminal VS Code.</span><span class="sxs-lookup"><span data-stu-id="23adf-128">When debugging, your module DLL is imported into the PowerShell session in the VS Code terminal.</span></span> <span data-ttu-id="23adf-129">La DLL est alors verrouillée.</span><span class="sxs-lookup"><span data-stu-id="23adf-129">The DLL becomes locked.</span></span> <span data-ttu-id="23adf-130">Le message suivant s’affiche lorsque vous exécutez la tâche de génération sans fermer la session de terminal :</span><span class="sxs-lookup"><span data-stu-id="23adf-130">The following message is displayed when you run the build task without closing the terminal session:</span></span>

```Output
Could not copy "obj\Debug\netstandard2.0\myModule.dll" to "bin\Debug\netstandard2.0\myModule.dll"`.
```

<span data-ttu-id="23adf-131">Vous devez fermer les sessions de terminal Server avant de procéder à la regénération.</span><span class="sxs-lookup"><span data-stu-id="23adf-131">Terminal sessions must be closed before you rebuild.</span></span>

## <a name="setting-up-the-debugger"></a><span data-ttu-id="23adf-132">Configuration du débogueur</span><span class="sxs-lookup"><span data-stu-id="23adf-132">Setting up the debugger</span></span>

<span data-ttu-id="23adf-133">Pour déboguer l’applet de commande PowerShell, vous devez configurer une configuration de lancement personnalisée.</span><span class="sxs-lookup"><span data-stu-id="23adf-133">To debug the PowerShell cmdlet, you need to set up a custom launch configuration.</span></span> <span data-ttu-id="23adf-134">Cette configuration permet d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="23adf-134">This configuration is used to:</span></span>

- <span data-ttu-id="23adf-135">Exécuter votre code source</span><span class="sxs-lookup"><span data-stu-id="23adf-135">Build your source code</span></span>
- <span data-ttu-id="23adf-136">Démarrer PowerShell avec votre module chargé</span><span class="sxs-lookup"><span data-stu-id="23adf-136">Start PowerShell with your module loaded</span></span>
- <span data-ttu-id="23adf-137">Laisser PowerShell ouvert dans le volet du terminal</span><span class="sxs-lookup"><span data-stu-id="23adf-137">Leave PowerShell open in the terminal pane</span></span>

<span data-ttu-id="23adf-138">Quand vous appelez votre applet de commande dans la session de terminal, le débogueur s’arrête à tous les points d’arrêt définis dans votre code source.</span><span class="sxs-lookup"><span data-stu-id="23adf-138">When you invoke your cmdlet in the terminal session, the debugger stops at any breakpoints set in your source code.</span></span>

### <a name="configuring-launchjson-for-powershell-core"></a><span data-ttu-id="23adf-139">Configuration de launch.json pour PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="23adf-139">Configuring launch.json for PowerShell Core</span></span>

1. <span data-ttu-id="23adf-140">Installer l’extension [C# pour Visual Studio Code][]</span><span class="sxs-lookup"><span data-stu-id="23adf-140">Install the [C# for Visual Studio Code][] extension</span></span>

1. <span data-ttu-id="23adf-141">Dans le volet de débogage, ajoutez une configuration de débogage.</span><span class="sxs-lookup"><span data-stu-id="23adf-141">In the Debug pane, add a debug configuration</span></span>

1. <span data-ttu-id="23adf-142">Dans la boîte de dialogue `Select environment`, choisissez `.NET Core`.</span><span class="sxs-lookup"><span data-stu-id="23adf-142">In the `Select environment` dialog, choose `.NET Core`</span></span>

1. <span data-ttu-id="23adf-143">Le fichier `launch.json` s’ouvre dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="23adf-143">The `launch.json` file is opened in the editor.</span></span> <span data-ttu-id="23adf-144">Lorsque vous placez votre curseur à l’intérieur du tableau `configurations`, vous voyez le sélecteur `configuration`.</span><span class="sxs-lookup"><span data-stu-id="23adf-144">With your cursor inside the `configurations` array, you see the `configuration` picker.</span></span> <span data-ttu-id="23adf-145">Si vous ne voyez pas cette liste, sélectionnez **Ajouter une configuration** .</span><span class="sxs-lookup"><span data-stu-id="23adf-145">If you don't see this list, select **Add Configuration** .</span></span>

1. <span data-ttu-id="23adf-146">Pour créer une configuration de débogage par défaut, sélectionnez **Lancer l’application console .NET Core**  :</span><span class="sxs-lookup"><span data-stu-id="23adf-146">To create a default debug configuration, select **Launch .NET Core Console App** :</span></span>

   ![Lancer l’application console .NET Core](media/using-vscode-for-debugging-compiled-cmdlets/add-configuration-dialog.png)

1. <span data-ttu-id="23adf-148">Modifiez les champs `name`, `program`, `args` et `console` de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="23adf-148">Edit the `name`, `program`, `args`, and `console` fields as follows:</span></span>

   ```json
    {
        "name": "PowerShell cmdlets: pwsh",
        "type": "coreclr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "pwsh",
        "args": [
            "-NoExit",
            "-NoProfile",
            "-Command",
            "Import-Module ${workspaceFolder}/myModule/bin/Debug/netstandard2.0/myModule.dll",
        ],
        "cwd": "${workspaceFolder}",
        "stopAtEntry": false,
        "console": "integratedTerminal"
    }
   ```

<span data-ttu-id="23adf-149">Le champ `program` est utilisé pour lancer `pwsh` afin que l’applet de commande en cours de débogage puisse être exécutée.</span><span class="sxs-lookup"><span data-stu-id="23adf-149">The `program` field is used to launch `pwsh` so that the cmdlet being debugged can be run.</span></span> <span data-ttu-id="23adf-150">L’argument `-NoExit` empêche la session PowerShell de se fermer dès que le module est importé.</span><span class="sxs-lookup"><span data-stu-id="23adf-150">The `-NoExit` argument prevents the PowerShell session from exiting as soon as the module is imported.</span></span>
<span data-ttu-id="23adf-151">Le chemin dans l’argument `Import-Module` est le chemin de sortie de génération par défaut, lorsque vous avez suivi le guide [Écriture de modules portables][].</span><span class="sxs-lookup"><span data-stu-id="23adf-151">The path in the `Import-Module` argument is the default build output path when you've followed the [Writing Portable Modules][] guide.</span></span> <span data-ttu-id="23adf-152">Si vous avez créé un manifeste de module (fichier `.psd1`), vous devez utiliser le chemin de ce fichier à la place.</span><span class="sxs-lookup"><span data-stu-id="23adf-152">If you've created a module manifest (`.psd1` file), you should use the path to that instead.</span></span> <span data-ttu-id="23adf-153">Le séparateur de chemin `/` fonctionne sur Windows, Linux et macOS.</span><span class="sxs-lookup"><span data-stu-id="23adf-153">The `/` path separator works on Windows, Linux, and macOS.</span></span> <span data-ttu-id="23adf-154">Vous devez utiliser le terminal intégré pour exécuter les commandes PowerShell que vous souhaitez déboguer.</span><span class="sxs-lookup"><span data-stu-id="23adf-154">You must use the integrated terminal to run the PowerShell commands you want to debug.</span></span>

> [!NOTE]
> <span data-ttu-id="23adf-155">Si le débogueur ne s’arrête pas aux points d’arrêt, dans la Console de débogage Visual Studio Code, recherchez une ligne indiquant ceci :</span><span class="sxs-lookup"><span data-stu-id="23adf-155">If the debugger doesn't stop at any breakpoints, look in the Visual Studio Code Debug Console for a line that says:</span></span>
>
> ```
> Loaded '/path/to/myModule.dll'. Skipped loading symbols. Module is optimized and the debugger option 'Just My Code' is enabled.
> ```
>
> <span data-ttu-id="23adf-156">Si vous voyez cette ligne, ajoutez `"justMyCode": false` à votre configuration de lancement au même niveau que `"console": "integratedTerminal"`.</span><span class="sxs-lookup"><span data-stu-id="23adf-156">If you see this, add `"justMyCode": false` to your launch config (at the same level as `"console": "integratedTerminal"`.</span></span>

### <a name="configuring-launchjson-for-windows-powershell"></a><span data-ttu-id="23adf-157">Configuration de launch.json pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="23adf-157">Configuring launch.json for Windows PowerShell</span></span>

<span data-ttu-id="23adf-158">Cette configuration de lancement fonctionne pour le test de vos applets de commande dans Windows PowerShell (`powershell.exe`).</span><span class="sxs-lookup"><span data-stu-id="23adf-158">This launch configuration works for testing your cmdlets in Windows PowerShell (`powershell.exe`).</span></span>
<span data-ttu-id="23adf-159">Créez une deuxième configuration de lancement avec les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="23adf-159">Create a second launch configuration with the following changes:</span></span>

1. <span data-ttu-id="23adf-160">`name` doit avoir la valeur `PowerShell cmdlets: powershell`</span><span class="sxs-lookup"><span data-stu-id="23adf-160">`name` should be `PowerShell cmdlets: powershell`</span></span>

1. <span data-ttu-id="23adf-161">`type` doit avoir la valeur `clr`</span><span class="sxs-lookup"><span data-stu-id="23adf-161">`type` should be `clr`</span></span>

1. <span data-ttu-id="23adf-162">`program` doit avoir la valeur `powershell`</span><span class="sxs-lookup"><span data-stu-id="23adf-162">`program` should be `powershell`</span></span>

   <span data-ttu-id="23adf-163">Il doit se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="23adf-163">It should look like this:</span></span>

   ```json
    {
        "name": "PowerShell cmdlets: powershell",
        "type": "clr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "powershell",
        "args": [
            "-NoExit",
            "-NoProfile",
            "-Command",
            "Import-Module ${workspaceFolder}/myModule/bin/Debug/netstandard2.0/myModule.dll",
        ],
        "cwd": "${workspaceFolder}",
        "stopAtEntry": false,
        "console": "integratedTerminal"
    }
   ```

## <a name="launching-a-debugging-session"></a><span data-ttu-id="23adf-164">Lancement d’une session de débogage</span><span class="sxs-lookup"><span data-stu-id="23adf-164">Launching a debugging session</span></span>

<span data-ttu-id="23adf-165">À présent, tout est prêt pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="23adf-165">Now everything is ready to begin debugging.</span></span>

- <span data-ttu-id="23adf-166">Placez un point d’arrêt dans le code source de l’applet de commande que vous souhaitez déboguer :</span><span class="sxs-lookup"><span data-stu-id="23adf-166">Place a breakpoint in the source code for the cmdlet you want to debug:</span></span>

  ![Un point d’arrêt s’affiche sous la forme d’un point rouge dans la marge.](media/using-vscode-for-debugging-compiled-cmdlets/set-breakpoint.png)

- <span data-ttu-id="23adf-168">Vérifiez qu’une configuration d’ **applets de commande PowerShell** adaptée est sélectionnée dans le menu déroulant configuration de la vue **Débogage**  :</span><span class="sxs-lookup"><span data-stu-id="23adf-168">Ensure that the relevant **PowerShell cmdlets** configuration is selected in the configuration drop-down menu in the **Debug** view:</span></span>

  ![Sélectionner la configuration du lancement](media/using-vscode-for-debugging-compiled-cmdlets/select-launch-configuration.png)

- <span data-ttu-id="23adf-170">Appuyez sur <kbd>F5</kbd> ou cliquez sur le bouton **Démarrer le débogage** .</span><span class="sxs-lookup"><span data-stu-id="23adf-170">Press <kbd>F5</kbd> or click on the **Start Debugging** button</span></span>

- <span data-ttu-id="23adf-171">Basculez vers le volet du terminal et appelez votre applet de commande :</span><span class="sxs-lookup"><span data-stu-id="23adf-171">Switch to the terminal pane and invoke your cmdlet:</span></span>

  ![Appeler l’applet de commande](media/using-vscode-for-debugging-compiled-cmdlets/invoke-the-cmdlet.png)

- <span data-ttu-id="23adf-173">L’exécution s’arrête au point d’arrêt :</span><span class="sxs-lookup"><span data-stu-id="23adf-173">Execution stops at the breakpoint:</span></span>

  ![L’exécution s’arrête au point d’arrêt](media/using-vscode-for-debugging-compiled-cmdlets/stopped-at-breakpoint.png)

<span data-ttu-id="23adf-175">Vous pouvez effectuer un pas à pas détaillé dans le code source, inspecter les variables et inspecter la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="23adf-175">You can step through the source code, inspect variables, and inspect the call stack.</span></span>

<span data-ttu-id="23adf-176">Pour terminer le débogage, cliquez sur **Arrêter** dans la barre d’outils de débogage ou appuyez sur <kbd>Maj</kbd>-<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="23adf-176">To end debugging, click **Stop** in the debug toolbar or press <kbd>Shift</kbd>-<kbd>F5</kbd>.</span></span> <span data-ttu-id="23adf-177">L’interpréteur de commandes utilisé pour le débogage se ferme et retire le verrou appliqué au fichier DLL compilé.</span><span class="sxs-lookup"><span data-stu-id="23adf-177">The shell used for debugging exits and releases the lock on the compiled DLL file.</span></span>

<!-- reference links -->
[Débogage dans Visual Studio Code]: https://code.visualstudio.com/docs/editor/debugging
[Debugging in Visual Studio Code]: https://code.visualstudio.com/docs/editor/debugging
[Utilisation de Visual Studio Code pour le débogage et l’édition à distance]: using-vscode-for-remote-editing-and-debugging.md
[Using Visual Studio Code for remote editing and debugging]: using-vscode-for-remote-editing-and-debugging.md
[Écriture de modules portables]: ../writing-portable-modules.md
[Writing Portable Modules]: ../writing-portable-modules.md
[C# pour Visual Studio Code]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
[C# for Visual Studio Code]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
