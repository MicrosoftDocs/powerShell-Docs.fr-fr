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
# <a name="using-visual-studio-code-to-debug-compiled-cmdlets"></a>Utilisation de Visual Studio Code pour déboguer des applets de commande compilées

Ce guide vous montre comment déboguer de manière interactive du code source C# appartenant à un module PowerShell compilé à l’aide de Visual Studio Code (VS Code) et de l’extension C#.

Cet article suppose que vous êtes familiarisé avec le débogueur Visual Studio Code.

- Pour une présentation générale du débogueur VS Code, consultez [Débogage dans Visual Studio Code][].

- Pour obtenir des exemples de débogage de modules et de fichiers de script PowerShell, consultez [Utilisation de Visual Studio Code pour le débogage et l’édition à distance][].

Ce guide suppose que vous avez lu et suivi les instructions du guide [Écriture de modules portables][].

## <a name="creating-a-build-task"></a>Création d’une tâche de génération

Générez automatiquement votre projet avant de lancer une session de débogage. Le fait de regénérer le projet vous permet de déboguer la version la plus récente de votre code.

Configurez une tâche de génération :

1. Dans la **palette de commandes** , exécutez la commande **Configurer la tâche de génération par défaut** .

   ![Exécution de la commande Configurer la tâche de génération par défaut](media/using-vscode-for-debugging-compiled-cmdlets/configure-default-build-task.png)

1. Dans la boîte de dialogue **Sélectionner une tâche à configurer** , choisissez **Créer le fichier tasks.json à partir d’un modèle** .

1. Dans la boîte de dialogue **Sélectionner un modèle de tâche** , choisissez **.NET Core** .

S’il n’existe pas déjà, le fichier `tasks.json` est créé.

Pour tester votre tâche de génération :

1. Dans la **palette de commandes** , exécutez la commande **Exécuter la tâche de build** .

1. Dans la boîte de dialogue **Sélectionner la tâche de génération à exécuter** , choisissez **build** .

### <a name="information-about-dll-files-being-locked"></a>Informations sur les fichiers DLL verrouillés

Par défaut, une tâche de génération réussie n’affiche pas de sortie dans le volet Terminal. Si vous voyez une sortie qui contient le texte **Project file doesn’t exist** (Le fichier projet n’existe pas), vous devez modifier le fichier `tasks.json`. Ajoutez le chemin explicite au projet C# au format suivant : `"${workspaceFolder}/myModule"`. Dans cet exemple, `myModule` est le nom du dossier du projet. Cette entrée doit être placée après l’entrée `build` de la liste `args` :

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

Lors du débogage, votre module DLL est importé dans la session PowerShell, dans le terminal VS Code. La DLL est alors verrouillée. Le message suivant s’affiche lorsque vous exécutez la tâche de génération sans fermer la session de terminal :

```Output
Could not copy "obj\Debug\netstandard2.0\myModule.dll" to "bin\Debug\netstandard2.0\myModule.dll"`.
```

Vous devez fermer les sessions de terminal Server avant de procéder à la regénération.

## <a name="setting-up-the-debugger"></a>Configuration du débogueur

Pour déboguer l’applet de commande PowerShell, vous devez configurer une configuration de lancement personnalisée. Cette configuration permet d’effectuer les opérations suivantes :

- Exécuter votre code source
- Démarrer PowerShell avec votre module chargé
- Laisser PowerShell ouvert dans le volet du terminal

Quand vous appelez votre applet de commande dans la session de terminal, le débogueur s’arrête à tous les points d’arrêt définis dans votre code source.

### <a name="configuring-launchjson-for-powershell-core"></a>Configuration de launch.json pour PowerShell Core

1. Installer l’extension [C# pour Visual Studio Code][]

1. Dans le volet de débogage, ajoutez une configuration de débogage.

1. Dans la boîte de dialogue `Select environment`, choisissez `.NET Core`.

1. Le fichier `launch.json` s’ouvre dans l’éditeur. Lorsque vous placez votre curseur à l’intérieur du tableau `configurations`, vous voyez le sélecteur `configuration`. Si vous ne voyez pas cette liste, sélectionnez **Ajouter une configuration** .

1. Pour créer une configuration de débogage par défaut, sélectionnez **Lancer l’application console .NET Core**  :

   ![Lancer l’application console .NET Core](media/using-vscode-for-debugging-compiled-cmdlets/add-configuration-dialog.png)

1. Modifiez les champs `name`, `program`, `args` et `console` de la façon suivante :

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

Le champ `program` est utilisé pour lancer `pwsh` afin que l’applet de commande en cours de débogage puisse être exécutée. L’argument `-NoExit` empêche la session PowerShell de se fermer dès que le module est importé.
Le chemin dans l’argument `Import-Module` est le chemin de sortie de génération par défaut, lorsque vous avez suivi le guide [Écriture de modules portables][]. Si vous avez créé un manifeste de module (fichier `.psd1`), vous devez utiliser le chemin de ce fichier à la place. Le séparateur de chemin `/` fonctionne sur Windows, Linux et macOS. Vous devez utiliser le terminal intégré pour exécuter les commandes PowerShell que vous souhaitez déboguer.

> [!NOTE]
> Si le débogueur ne s’arrête pas aux points d’arrêt, dans la Console de débogage Visual Studio Code, recherchez une ligne indiquant ceci :
>
> ```
> Loaded '/path/to/myModule.dll'. Skipped loading symbols. Module is optimized and the debugger option 'Just My Code' is enabled.
> ```
>
> Si vous voyez cette ligne, ajoutez `"justMyCode": false` à votre configuration de lancement au même niveau que `"console": "integratedTerminal"`.

### <a name="configuring-launchjson-for-windows-powershell"></a>Configuration de launch.json pour Windows PowerShell

Cette configuration de lancement fonctionne pour le test de vos applets de commande dans Windows PowerShell (`powershell.exe`).
Créez une deuxième configuration de lancement avec les modifications suivantes :

1. `name` doit avoir la valeur `PowerShell cmdlets: powershell`

1. `type` doit avoir la valeur `clr`

1. `program` doit avoir la valeur `powershell`

   Il doit se présenter comme suit :

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

## <a name="launching-a-debugging-session"></a>Lancement d’une session de débogage

À présent, tout est prêt pour le débogage.

- Placez un point d’arrêt dans le code source de l’applet de commande que vous souhaitez déboguer :

  ![Un point d’arrêt s’affiche sous la forme d’un point rouge dans la marge.](media/using-vscode-for-debugging-compiled-cmdlets/set-breakpoint.png)

- Vérifiez qu’une configuration d’ **applets de commande PowerShell** adaptée est sélectionnée dans le menu déroulant configuration de la vue **Débogage**  :

  ![Sélectionner la configuration du lancement](media/using-vscode-for-debugging-compiled-cmdlets/select-launch-configuration.png)

- Appuyez sur <kbd>F5</kbd> ou cliquez sur le bouton **Démarrer le débogage** .

- Basculez vers le volet du terminal et appelez votre applet de commande :

  ![Appeler l’applet de commande](media/using-vscode-for-debugging-compiled-cmdlets/invoke-the-cmdlet.png)

- L’exécution s’arrête au point d’arrêt :

  ![L’exécution s’arrête au point d’arrêt](media/using-vscode-for-debugging-compiled-cmdlets/stopped-at-breakpoint.png)

Vous pouvez effectuer un pas à pas détaillé dans le code source, inspecter les variables et inspecter la pile des appels.

Pour terminer le débogage, cliquez sur **Arrêter** dans la barre d’outils de débogage ou appuyez sur <kbd>Maj</kbd>-<kbd>F5</kbd>. L’interpréteur de commandes utilisé pour le débogage se ferme et retire le verrou appliqué au fichier DLL compilé.

<!-- reference links -->
[Débogage dans Visual Studio Code]: https://code.visualstudio.com/docs/editor/debugging
[Utilisation de Visual Studio Code pour le débogage et l’édition à distance]: using-vscode-for-remote-editing-and-debugging.md
[Écriture de modules portables]: ../writing-portable-modules.md
[C# pour Visual Studio Code]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
