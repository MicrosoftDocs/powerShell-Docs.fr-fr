---
title: Utilisation de Visual Studio Code pour le développement PowerShell
description: Utilisation de Visual Studio Code pour le développement PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 1e9b9d811a39656327af2810bd6dc8aaf3fde3a4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086718"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="57520-103">Utilisation de Visual Studio Code pour le développement PowerShell</span><span class="sxs-lookup"><span data-stu-id="57520-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="57520-104">En plus de [PowerShell ISE][ise], PowerShell est également bien pris en charge dans Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="57520-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="57520-105">De plus, l’environnement ISE n’est pas pris en charge avec PowerShell Core, alors que Visual Studio Code est pris en charge pour PowerShell Core sur toutes les plateformes (macOS, Windows et Linux)</span><span class="sxs-lookup"><span data-stu-id="57520-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="57520-106">Vous pouvez utiliser Visual Studio Code sur Windows avec PowerShell version 5 avec Windows 10 ou en installant [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) pour les systèmes d’exploitation Windows d’une version antérieure (par exemple Windows 8.1, etc.).</span><span class="sxs-lookup"><span data-stu-id="57520-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="57520-107">Avant de le démarrer, vérifiez que PowerShell est présent sur votre système.</span><span class="sxs-lookup"><span data-stu-id="57520-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="57520-108">Pour les charges de travail modernes sur Windows, macOS et Linux, consultez :</span><span class="sxs-lookup"><span data-stu-id="57520-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="57520-109">[Installation de PowerShell Core sous Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="57520-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="57520-110">[Installation de PowerShell Core sous macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="57520-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="57520-111">[Installation de PowerShell Core sur Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="57520-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="57520-112">Pour les charges de travail Windows PowerShell classiques, consultez [Installation de Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="57520-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="57520-113">Édition avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="57520-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="57520-114">1. Installation de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="57520-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="57520-115">**Linux** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur Linux](https://code.visualstudio.com/docs/setup/linux)</span><span class="sxs-lookup"><span data-stu-id="57520-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="57520-116">**macOS** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur macOS](https://code.visualstudio.com/docs/setup/mac)</span><span class="sxs-lookup"><span data-stu-id="57520-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="57520-117">Sur macOS, vous devez installer OpenSSL pour que l’extension PowerShell fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="57520-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="57520-118">Le moyen le plus simple de le faire est d’installer [Homebrew](https://brew.sh/), puis d’exécuter `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="57520-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="57520-119">VS Code peut désormais charger l’extension de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57520-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="57520-120">**Windows** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur Windows](https://code.visualstudio.com/docs/setup/windows)</span><span class="sxs-lookup"><span data-stu-id="57520-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="57520-121">2. Installation de l’extension PowerShell</span><span class="sxs-lookup"><span data-stu-id="57520-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="57520-122">Lancez l’application Visual Studio Code comme suit :</span><span class="sxs-lookup"><span data-stu-id="57520-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="57520-123">**Windows** : en tapant `code` dans votre session PowerShell</span><span class="sxs-lookup"><span data-stu-id="57520-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="57520-124">**Linux** : en tapant `code` dans votre terminal</span><span class="sxs-lookup"><span data-stu-id="57520-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="57520-125">**macOS** : en tapant `code` dans votre terminal</span><span class="sxs-lookup"><span data-stu-id="57520-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="57520-126">Lancez **Quick Open** en appuyant sur **Ctrl+P** (**Cmd+P** sur Mac).</span><span class="sxs-lookup"><span data-stu-id="57520-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="57520-127">Dans Quick Open, tapez `ext install powershell`, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="57520-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="57520-128">La vue **Extensions** s’ouvre dans la barre latérale.</span><span class="sxs-lookup"><span data-stu-id="57520-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="57520-129">Sélectionnez l’extension de PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="57520-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="57520-130">Vous devez voir quelque chose semblable à ce qui présenté ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="57520-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="57520-132">Cliquez sur le bouton **Installer** sur l’extension PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="57520-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="57520-133">Après l’installation, vous voyez le bouton **Installer** se changer en **Recharger**.</span><span class="sxs-lookup"><span data-stu-id="57520-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="57520-134">Cliquez sur **Recharger**.</span><span class="sxs-lookup"><span data-stu-id="57520-134">Click on **Reload**.</span></span>
- <span data-ttu-id="57520-135">Une fois Visual Studio Code rechargé, vous êtes prêt pour l’édition.</span><span class="sxs-lookup"><span data-stu-id="57520-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="57520-136">Par exemple, pour créer un fichier, cliquez sur **Fichier->Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="57520-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="57520-137">Pour l’enregistrer, cliquez sur **Fichier->Enregistrer**, puis indiquez un nom de fichier, disons `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="57520-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="57520-138">Pour fermer le fichier, cliquez sur « x » en regard du nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="57520-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="57520-139">Pour quitter Visual Studio Code, cliquez sur **Fichier->Quitter**.</span><span class="sxs-lookup"><span data-stu-id="57520-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="57520-140">Installation de l’extension PowerShell sur des systèmes restreints</span><span class="sxs-lookup"><span data-stu-id="57520-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="57520-141">Certains systèmes sont configurés pour nécessiter la vérification de toutes les signatures de code et PowerShell Editor Services doit donc être manuellement approuvé pour s’exécuter sur le système.</span><span class="sxs-lookup"><span data-stu-id="57520-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="57520-142">Une mise à jour de la stratégie de groupe qui modifie la stratégie d’exécution est une cause probable si vous avez installé l’extension PowerShell mais recevez une erreur telle que :</span><span class="sxs-lookup"><span data-stu-id="57520-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="57520-143">Pour approuver manuellement PowerShell Editor Services et, par conséquent, l’extension PowerShell pour VSCode, ouvrez une invite PowerShell et exécutez :</span><span class="sxs-lookup"><span data-stu-id="57520-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="57520-144">Le message « Voulez-vous exécuter le logiciel de cet éditeur non approuvé ? » apparaît.</span><span class="sxs-lookup"><span data-stu-id="57520-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="57520-145">Tapez `R` pour exécuter le fichier.</span><span class="sxs-lookup"><span data-stu-id="57520-145">Type `R` to run the file.</span></span> <span data-ttu-id="57520-146">Ouvrez ensuite Visual Studio Code et vérifiez que l’extension PowerShell fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="57520-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="57520-147">Si vous rencontrez toujours des problèmes de mise en route, faites-le-nous savoir sur [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="57520-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="57520-148">Utilisation d’une version installée spécifique de PowerShell</span><span class="sxs-lookup"><span data-stu-id="57520-148">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="57520-149">Si vous voulez utiliser une installation spécifique de PowerShell avec Visual Studio Code, vous devez ajouter une nouvelle variable à votre fichier de paramètres utilisateur.</span><span class="sxs-lookup"><span data-stu-id="57520-149">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="57520-150">Cliquez sur **Fichier -> Préférences -> Paramètres**</span><span class="sxs-lookup"><span data-stu-id="57520-150">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="57520-151">Deux volets de l’éditeur apparaissent.</span><span class="sxs-lookup"><span data-stu-id="57520-151">Two editor panes appear.</span></span>
   <span data-ttu-id="57520-152">Dans le volet le plus à droite (`settings.json`), insérez le paramètre ci-dessous approprié pour votre système d’exploitation quelque part entre les deux accolades (`{` et `}`) et remplacez **\<la version \>** par la version installée de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="57520-152">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace **\<version\>** with the installed PowerShell version:</span></span>

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. <span data-ttu-id="57520-153">Remplacez le paramètre par le chemin vers l’exécutable PowerShell souhaité</span><span class="sxs-lookup"><span data-stu-id="57520-153">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="57520-154">Enregistrez le fichier de paramètres et redémarrez Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="57520-154">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="57520-155">Paramètres de configuration de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="57520-155">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="57520-156">En suivant la procédure décrite dans le paragraphe précédent, vous pouvez ajouter des paramètres de configuration dans `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="57520-156">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="57520-157">Nous recommandons les paramètres de configuration suivants pour Visual Studio Code :</span><span class="sxs-lookup"><span data-stu-id="57520-157">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="57520-158">Si vous ne souhaitez pas que ces paramètres affectent tous les types de fichiers, VSCode autorise également les configurations propres à un langage.</span><span class="sxs-lookup"><span data-stu-id="57520-158">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="57520-159">Vous pouvez créer un paramètre propre au langage en plaçant des paramètres dans un champ `[<language-name>]`.</span><span class="sxs-lookup"><span data-stu-id="57520-159">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="57520-160">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="57520-160">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="57520-161">Pour plus d’informations sur l’encodage de fichier dans VS Code, consultez [Présentation de l’encodage de fichier](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="57520-161">For more information about file encoding in VS Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="57520-162">Débogage avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="57520-162">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="57520-163">Débogage sans espace de travail</span><span class="sxs-lookup"><span data-stu-id="57520-163">No-workspace debugging</span></span>

<span data-ttu-id="57520-164">À compter de Visual Studio Code version 1.9, vous pouvez déboguer des scripts PowerShell sans avoir à ouvrir le dossier contenant le script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57520-164">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="57520-165">Ouvrez le fichier de script PowerShell avec **Fichier->Ouvrir un fichier...**, définissez un point d’arrêt sur une ligne (appuyez sur F9), puis appuyez sur F5 pour démarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="57520-165">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span> <span data-ttu-id="57520-166">Vous voyez apparaître le volet Actions de débogage, qui vous permet de vous arrêter dans le débogueur, d’effectuer un pas à pas détaillé, de reprendre et d’arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="57520-166">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="57520-167">Débogage d’espace de travail</span><span class="sxs-lookup"><span data-stu-id="57520-167">Workspace debugging</span></span>

<span data-ttu-id="57520-168">Le débogage d’espace de travail fait référence au débogage dans le contexte d’un dossier que vous avez ouvert dans Visual Studio Code en utilisant **Ouvrir un dossier...**  à partir du menu **Fichier**.</span><span class="sxs-lookup"><span data-stu-id="57520-168">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="57520-169">Le dossier que vous ouvrez est généralement votre dossier de projet PowerShell et/ou la racine de votre dépôt Git.</span><span class="sxs-lookup"><span data-stu-id="57520-169">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="57520-170">Même dans ce mode, vous pouvez démarrer le débogage du script PowerShell actuellement sélectionné en appuyant simplement sur F5.</span><span class="sxs-lookup"><span data-stu-id="57520-170">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="57520-171">Cependant, le débogage d’espace de travail vous permet de définir plusieurs configurations de débogage autres que simplement déboguer le fichier actuellement ouvert.</span><span class="sxs-lookup"><span data-stu-id="57520-171">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="57520-172">Par exemple, vous pouvez ajouter des configurations pour :</span><span class="sxs-lookup"><span data-stu-id="57520-172">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="57520-173">Lancer des tests Pester dans le débogueur</span><span class="sxs-lookup"><span data-stu-id="57520-173">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="57520-174">Lancer un fichier spécifique avec des arguments dans le débogueur</span><span class="sxs-lookup"><span data-stu-id="57520-174">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="57520-175">Lancer une session interactive dans le débogueur</span><span class="sxs-lookup"><span data-stu-id="57520-175">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="57520-176">Attacher le débogueur à un processus hôte PowerShell</span><span class="sxs-lookup"><span data-stu-id="57520-176">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="57520-177">Suivez ces étapes pour créer votre fichier de configuration de débogage :</span><span class="sxs-lookup"><span data-stu-id="57520-177">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="57520-178">Ouvrez la vue **Déboguer** en appuyant sur **Ctrl+Maj+D** (**Cmd+Maj+D** sur Mac).</span><span class="sxs-lookup"><span data-stu-id="57520-178">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="57520-179">Appuyez sur l’icône d’engrenage **Configurer** dans la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="57520-179">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="57520-180">Visual Studio Code vous invite à **Sélectionner un environnement**.</span><span class="sxs-lookup"><span data-stu-id="57520-180">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="57520-181">Choisissez **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="57520-181">Choose **PowerShell**.</span></span>

  <span data-ttu-id="57520-182">Dans ce cas, Visual Studio Code crée un répertoire et un fichier «.vscode\launch.json » à la racine du dossier de votre espace de travail.</span><span class="sxs-lookup"><span data-stu-id="57520-182">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="57520-183">C’est là que votre configuration de débogage est stockée.</span><span class="sxs-lookup"><span data-stu-id="57520-183">This is where your debug configuration is stored.</span></span> <span data-ttu-id="57520-184">Si vos fichiers sont dans un dépôt Git, vous souhaitez généralement valider le fichier launch.json.</span><span class="sxs-lookup"><span data-stu-id="57520-184">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="57520-185">Le contenu du fichier launch.json est :</span><span class="sxs-lookup"><span data-stu-id="57520-185">The contents of the launch.json file are:</span></span>

  ```json
  {
    "version": "0.2.0",
    "configurations": [
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Launch (current file)",
            "script": "${file}",
            "args": [],
            "cwd": "${file}"
        },
        {
            "type": "PowerShell",
            "request": "attach",
            "name": "PowerShell Attach to Host Process",
            "processId": "${command.PickPSHostProcess}",
            "runspaceId": 1
        },
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Interactive Session",
            "cwd": "${workspaceRoot}"
        }
    ]
  }
  ```

  <span data-ttu-id="57520-186">Ceci représente les scénarios de débogage courants.</span><span class="sxs-lookup"><span data-stu-id="57520-186">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="57520-187">Cependant, quand vous ouvrez ce fichier dans l’éditeur, vous voyez un bouton **Ajouter une configuration**.</span><span class="sxs-lookup"><span data-stu-id="57520-187">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="57520-188">Vous pouvez appuyer sur ce bouton pour ajouter d’autres configurations de débogage PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57520-188">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="57520-189">Vous pouvez aussi ajouter la configuration très pratique **PowerShell : Lancer un script**.</span><span class="sxs-lookup"><span data-stu-id="57520-189">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="57520-190">Avec cette configuration, vous pouvez spécifier un fichier spécifique avec des arguments facultatifs, qui doit être lancé quand vous appuyez sur F5, quel que soit le fichier actif dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="57520-190">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="57520-191">Une fois établie la configuration de débogage, vous pouvez choisir la configuration à utiliser pendant une session de débogage en la sélectionnant dans la liste déroulante des configurations de débogage de la barre d’outils de la vue **Déboguer**.</span><span class="sxs-lookup"><span data-stu-id="57520-191">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="57520-192">Quelques blogs peuvent être utiles pour bien démarrer avec l’extension PowerShell pour Visual Studio Code :</span><span class="sxs-lookup"><span data-stu-id="57520-192">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="57520-193">[Extension PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="57520-193">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="57520-194">[Écrire et déboguer des scripts PowerShell dans Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="57520-194">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="57520-195">[Aide sur le débogage avec Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="57520-195">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="57520-196">[Débogage de PowerShell dans Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="57520-196">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="57520-197">[Guide pratique pour le développement avec PowerShell dans Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="57520-197">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="57520-198">[Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="57520-198">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="57520-199">[Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="57520-199">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="57520-200">[Débogage des scripts PowerShell dans Visual Studio Code – Partie 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="57520-200">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="57520-201">[Débogage des scripts PowerShell dans Visual Studio Code – Partie 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="57520-201">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="57520-202">Extension PowerShell pour Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="57520-202">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="57520-203">Vous trouverez le code source de l’extension PowerShell sur [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="57520-203">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
