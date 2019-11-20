---
title: Utilisation de Visual Studio Code pour le développement PowerShell
description: Utilisation de Visual Studio Code pour le développement PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 4f197e71d3b79828f466584f5d862415726818b1
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117386"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="262dc-103">Utilisation de Visual Studio Code pour le développement PowerShell</span><span class="sxs-lookup"><span data-stu-id="262dc-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="262dc-104">En plus de [PowerShell ISE][ise], PowerShell est également bien pris en charge dans Visual Studio Code (VSCode).</span><span class="sxs-lookup"><span data-stu-id="262dc-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code (VSCode).</span></span> <span data-ttu-id="262dc-105">Par ailleurs, l’environnement ISE n’est pas pris en charge avec PowerShell Core, alors que VSCode est pris en charge pour PowerShell Core sur toutes les plateformes : Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="262dc-105">The ISE isn't supported with PowerShell Core, but VSCode is supported for PowerShell Core on all platforms: Windows, macOS, and Linux.</span></span>

<span data-ttu-id="262dc-106">Pour utiliser VSCode sur Windows avec PowerShell version 5, utilisez Windows 10 ou installez Windows Management Framework 5.1 pour les systèmes d’exploitation Windows de bas niveau, comme Windows 8.1.</span><span class="sxs-lookup"><span data-stu-id="262dc-106">You can use VSCode on Windows with PowerShell version 5 by using Windows 10 or by installing Windows Management Framework 5.1 for down-level Windows OSs such as Windows 8.1.</span></span> <span data-ttu-id="262dc-107">Pour plus d’informations, voir [Installer et configurer WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span><span class="sxs-lookup"><span data-stu-id="262dc-107">For more information, see [Install and Configure WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span></span>

<span data-ttu-id="262dc-108">Avant de commencer, vérifiez que PowerShell est présent sur votre système.</span><span class="sxs-lookup"><span data-stu-id="262dc-108">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="262dc-109">Pour les charges de travail modernes sur Windows, macOS et Linux, voir les liens suivants :</span><span class="sxs-lookup"><span data-stu-id="262dc-109">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="262dc-110">[Installation de PowerShell Core sur Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="262dc-110">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="262dc-111">[Installation de PowerShell Core sur macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="262dc-111">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="262dc-112">[Installation de PowerShell Core sur Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="262dc-112">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="262dc-113">Pour les charges de travail Windows PowerShell classiques, consultez [Installation de Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="262dc-113">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-vscode"></a><span data-ttu-id="262dc-114">Édition avec VSCode</span><span class="sxs-lookup"><span data-stu-id="262dc-114">Editing with VSCode</span></span>

1. <span data-ttu-id="262dc-115">Installez VSCode.</span><span class="sxs-lookup"><span data-stu-id="262dc-115">Install VSCode.</span></span> <span data-ttu-id="262dc-116">Pour plus d’informations, voir la vue d’ensemble [Configurer Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span><span class="sxs-lookup"><span data-stu-id="262dc-116">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

   <span data-ttu-id="262dc-117">Les instructions d’installation sont propres à chaque plateforme :</span><span class="sxs-lookup"><span data-stu-id="262dc-117">There are installation instructions for each platform:</span></span>

   - <span data-ttu-id="262dc-118">**Linux** : suivez les instructions d’installation de la page [Exécuter VSCode sur Linux](https://code.visualstudio.com/docs/setup/linux).</span><span class="sxs-lookup"><span data-stu-id="262dc-118">**Linux**: follow the installation instructions on the [Running VSCode on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>
   - <span data-ttu-id="262dc-119">**macOS** : suivez les instructions d’installation de la page [Exécuter VSCode sur macOS](https://code.visualstudio.com/docs/setup/mac).</span><span class="sxs-lookup"><span data-stu-id="262dc-119">**macOS**: follow the installation instructions on the [Running VSCode on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>

     > [!IMPORTANT]
     > <span data-ttu-id="262dc-120">Sur macOS, vous devez installer OpenSSL pour que l’extension PowerShell fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="262dc-120">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span> <span data-ttu-id="262dc-121">Le moyen le plus simple de le faire est d’installer [Homebrew](https://brew.sh/), puis d’exécuter `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="262dc-121">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span> <span data-ttu-id="262dc-122">VSCode peut désormais charger l’extension PowerShell.</span><span class="sxs-lookup"><span data-stu-id="262dc-122">VSCode can now load the PowerShell extension successfully.</span></span>

   - <span data-ttu-id="262dc-123">**Windows** : suivez les instructions d’installation de la page [Exécuter VSCode sur Windows](https://code.visualstudio.com/docs/setup/windows).</span><span class="sxs-lookup"><span data-stu-id="262dc-123">**Windows**: follow the installation instructions on the [Running VSCode on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>

1. <span data-ttu-id="262dc-124">Installez l’extension PowerShell.</span><span class="sxs-lookup"><span data-stu-id="262dc-124">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="262dc-125">Lancez l’application VSCode en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="262dc-125">Launch the VSCode app by:</span></span>
      - <span data-ttu-id="262dc-126">**Windows** : en tapant `code` dans votre session PowerShell</span><span class="sxs-lookup"><span data-stu-id="262dc-126">**Windows**: typing `code` in your PowerShell session</span></span>
      - <span data-ttu-id="262dc-127">**Linux** : en tapant `code` dans votre terminal</span><span class="sxs-lookup"><span data-stu-id="262dc-127">**Linux**: typing `code` in your terminal</span></span>
      - <span data-ttu-id="262dc-128">**macOS** : en tapant `code` dans votre terminal</span><span class="sxs-lookup"><span data-stu-id="262dc-128">**macOS**: typing `code` in your terminal</span></span>
   1. <span data-ttu-id="262dc-129">Lancez **Quick Open** sur Windows ou Linux en appuyant sur <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="262dc-129">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="262dc-130">Sur macOS, appuyez sur <kbd>Cmd</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="262dc-130">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="262dc-131">Dans Quick Open, tapez `ext install powershell`, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="262dc-131">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="262dc-132">La vue **Extensions** s’ouvre dans la barre latérale.</span><span class="sxs-lookup"><span data-stu-id="262dc-132">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="262dc-133">Sélectionnez l’extension de PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="262dc-133">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="262dc-134">Un écran VSCode apparaît :</span><span class="sxs-lookup"><span data-stu-id="262dc-134">You should see a VSCode screen similar to the following image:</span></span>

      ![VSCode](../../images/using-vscode/vscode.png)

   1. <span data-ttu-id="262dc-136">Cliquez sur le bouton **Installer** sur l’extension PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="262dc-136">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="262dc-137">Après l’installation, vous voyez le bouton **Installer** se changer en **Recharger**.</span><span class="sxs-lookup"><span data-stu-id="262dc-137">After the install, you see the **Install** button turns to **Reload**.</span></span> <span data-ttu-id="262dc-138">Cliquez sur **Recharger**.</span><span class="sxs-lookup"><span data-stu-id="262dc-138">Click on **Reload**.</span></span>
   1. <span data-ttu-id="262dc-139">Une fois VSCode rechargé, vous pouvez passer à l’édition.</span><span class="sxs-lookup"><span data-stu-id="262dc-139">After VSCode has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="262dc-140">Par exemple, pour créer un fichier, cliquez sur **Fichier > Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="262dc-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="262dc-141">Pour l’enregistrer, cliquez sur **Fichier > Enregistrer**, puis indiquez un nom de fichier, comme `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="262dc-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="262dc-142">Pour fermer le fichier, cliquez sur `X` à côté du nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="262dc-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="262dc-143">Pour quitter VSCode, **Fichier > Quitter**.</span><span class="sxs-lookup"><span data-stu-id="262dc-143">To exit VSCode, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="262dc-144">Installation de l’extension PowerShell sur des systèmes restreints</span><span class="sxs-lookup"><span data-stu-id="262dc-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="262dc-145">Certains systèmes sont configurés de façon à imposer la vérification de toutes les signatures de code et l’approbation manuelle de PowerShell Editor Services pour qu’il puisse s’exécuter sur le système.</span><span class="sxs-lookup"><span data-stu-id="262dc-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="262dc-146">Une mise à jour de la stratégie de groupe qui modifie la stratégie d’exécution est une cause probable si vous avez installé l’extension PowerShell, mais recevez une erreur de ce type :</span><span class="sxs-lookup"><span data-stu-id="262dc-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="262dc-147">Pour approuver manuellement PowerShell Editor Services et l’extension PowerShell pour VSCode, ouvrez une invite PowerShell et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="262dc-147">To manually approve PowerShell Editor Services and the PowerShell extension for VSCode, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="262dc-148">Le message **Voulez-vous exécuter le logiciel provenant de cet éditeur non approuvé ?** apparaît.</span><span class="sxs-lookup"><span data-stu-id="262dc-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span> <span data-ttu-id="262dc-149">Tapez `A` pour exécuter le fichier.</span><span class="sxs-lookup"><span data-stu-id="262dc-149">Type `A` to run the file.</span></span> <span data-ttu-id="262dc-150">Ouvrez ensuite VSCode et vérifiez que l’extension PowerShell fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="262dc-150">Then, open VSCode and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="262dc-151">Si vous rencontrez toujours des problèmes de mise en route, faites-le-nous savoir sur [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="262dc-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="262dc-152">Choisir la version de PowerShell à utiliser avec l’extension</span><span class="sxs-lookup"><span data-stu-id="262dc-152">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="262dc-153">Maintenant que PowerShell Core peut s’installer côte à côte avec Windows PowerShell, il est possible d’utiliser une version donnée de PowerShell avec l’extension PowerShell.</span><span class="sxs-lookup"><span data-stu-id="262dc-153">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="262dc-154">Suivez les étapes ci-dessous pour choisir la version :</span><span class="sxs-lookup"><span data-stu-id="262dc-154">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="262dc-155">Ouvrez la **Palette de commandes** sous Windows ou Linux avec <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="262dc-155">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="262dc-156">Sur macOS, utilisez <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="262dc-156">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="262dc-157">Recherchez **Session**.</span><span class="sxs-lookup"><span data-stu-id="262dc-157">Search for **Session**.</span></span>
1. <span data-ttu-id="262dc-158">Cliquez sur **PowerShell : Afficher le menu de session**.</span><span class="sxs-lookup"><span data-stu-id="262dc-158">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="262dc-159">Choisissez la version de PowerShell que vous souhaitez utiliser dans la liste, par exemple : **PowerShell Core**.</span><span class="sxs-lookup"><span data-stu-id="262dc-159">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="262dc-160">Cette fonctionnalité examine quelques chemins connus sur différents systèmes d’exploitation pour détecter les emplacements d’installation de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="262dc-160">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="262dc-161">Si vous avez installé PowerShell à un emplacement non standard, il risque de ne pas apparaître d’emblée dans le menu de session.</span><span class="sxs-lookup"><span data-stu-id="262dc-161">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="262dc-162">Pour étendre le menu de session, [ajoutez vos propres chemins personnalisés](#adding-your-own-powershell-paths-to-the-session-menu) en suivant la procédure décrite ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="262dc-162">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="262dc-163">Il existe un autre moyen d’accéder au menu de session.</span><span class="sxs-lookup"><span data-stu-id="262dc-163">There's another way to get to the session menu.</span></span> <span data-ttu-id="262dc-164">Quand un fichier PowerShell est ouvert dans l’éditeur, un numéro de version apparaît en vert en bas à droite.</span><span class="sxs-lookup"><span data-stu-id="262dc-164">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="262dc-165">Cliquez dessus pour accéder au menu de session.</span><span class="sxs-lookup"><span data-stu-id="262dc-165">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="262dc-166">Ajouter ses propres chemins PowerShell au menu de session</span><span class="sxs-lookup"><span data-stu-id="262dc-166">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="262dc-167">Il est possible d’ajouter d’autres chemins d’exécutables PowerShell au menu de session avec un paramètre VSCode.</span><span class="sxs-lookup"><span data-stu-id="262dc-167">You can add other PowerShell executable paths to the session menu through a VSCode setting.</span></span>

<span data-ttu-id="262dc-168">Ajoutez un élément à la liste `powershell.powerShellAdditionalExePaths` ou créez la liste si elle n’existe pas dans `settings.json` :</span><span class="sxs-lookup"><span data-stu-id="262dc-168">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

<span data-ttu-id="262dc-169">Chaque élément doit comporter :</span><span class="sxs-lookup"><span data-stu-id="262dc-169">Each item must have:</span></span>

* <span data-ttu-id="262dc-170">`exePath` : chemin de l’exécutable `pwsh` ou `powershell`.</span><span class="sxs-lookup"><span data-stu-id="262dc-170">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="262dc-171">`versionName` : texte qui s’affichera dans le menu de session.</span><span class="sxs-lookup"><span data-stu-id="262dc-171">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="262dc-172">Vous pouvez définir la version de PowerShell par défaut avec le paramètre `powershell.powerShellDefaultVersion` en le définissant sur le texte qui s’affiche dans le menu de session (soit `versionName` dans le dernier paramètre) :</span><span class="sxs-lookup"><span data-stu-id="262dc-172">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

<span data-ttu-id="262dc-173">Après avoir configuré ce paramètre, redémarrez VSCode ou rechargez la fenêtre VSCode active avec la **Palette de commandes**, puis tapez **Développeur : Recharger la fenêtre**.</span><span class="sxs-lookup"><span data-stu-id="262dc-173">After you've configured this setting, restart VSCode or to reload the current VSCode window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="262dc-174">Si vous ouvrez le menu de session, vous trouvez à présent les versions supplémentaires de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="262dc-174">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="262dc-175">Si vous générez PowerShell à partir de la source, c’est un excellent moyen de tester votre build locale de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="262dc-175">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-vscode"></a><span data-ttu-id="262dc-176">Paramètres de configuration pour VSCode</span><span class="sxs-lookup"><span data-stu-id="262dc-176">Configuration settings for VSCode</span></span>

<span data-ttu-id="262dc-177">En suivant la procédure décrite dans le paragraphe précédent, vous pouvez ajouter des paramètres de configuration dans `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="262dc-177">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="262dc-178">Nous recommandons les paramètres de configuration suivants pour VSCode :</span><span class="sxs-lookup"><span data-stu-id="262dc-178">We recommend the following configuration settings for VSCode:</span></span>

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

<span data-ttu-id="262dc-179">Si vous ne souhaitez pas que ces paramètres affectent tous les types de fichiers, VSCode autorise également les configurations propres à un langage.</span><span class="sxs-lookup"><span data-stu-id="262dc-179">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="262dc-180">Vous pouvez créer un paramètre propre au langage en plaçant des paramètres dans un champ `[<language-name>]`.</span><span class="sxs-lookup"><span data-stu-id="262dc-180">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="262dc-181">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="262dc-181">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="262dc-182">Pour plus d’informations sur l’encodage de fichier dans VSCode, consultez [Compréhension de l’encodage de fichier](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="262dc-182">For more information about file encoding in VSCode, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-vscode"></a><span data-ttu-id="262dc-183">Débogage avec VSCode</span><span class="sxs-lookup"><span data-stu-id="262dc-183">Debugging with VSCode</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="262dc-184">Débogage sans espace de travail</span><span class="sxs-lookup"><span data-stu-id="262dc-184">No-workspace debugging</span></span>

<span data-ttu-id="262dc-185">À partir de VSCode version 1.9, il est possible de déboguer des scripts PowerShell sans avoir à ouvrir le dossier qui les contient.</span><span class="sxs-lookup"><span data-stu-id="262dc-185">As of VSCode version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="262dc-186">Ouvrez un fichier de script PowerShell avec **Fichier > Ouvrir un fichier…** , définissez un point d’arrêt sur une ligne (appuyez sur <kbd>F9</kbd>), puis appuyez sur <kbd>F5</kbd> pour démarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="262dc-186">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="262dc-187">Le volet Actions de débogage apparaît ; il permet de s’arrêter dans le débogueur, d’effectuer un pas à pas détaillé, de reprendre et d’arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="262dc-187">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="262dc-188">Débogage d’espace de travail</span><span class="sxs-lookup"><span data-stu-id="262dc-188">Workspace debugging</span></span>

<span data-ttu-id="262dc-189">Le débogage d’espace de travail fait référence au débogage dans le contexte d’un dossier ouvert dans Visual Studio Code dans le menu **Fichier**  avec **Ouvrir le dossier…** . Le dossier que vous ouvrez est généralement votre dossier de projet PowerShell et/ou la racine de votre dépôt Git.</span><span class="sxs-lookup"><span data-stu-id="262dc-189">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="262dc-190">Même dans ce mode, vous pouvez lancer le débogage du script PowerShell actuellement sélectionné en appuyant sur <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="262dc-190">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="262dc-191">Cependant, le débogage d’espace de travail vous permet de définir plusieurs configurations de débogage autres que simplement déboguer le fichier actuellement ouvert.</span><span class="sxs-lookup"><span data-stu-id="262dc-191">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="262dc-192">Par exemple, vous pouvez ajouter une configuration pour :</span><span class="sxs-lookup"><span data-stu-id="262dc-192">For instance, you can add a configuration to:</span></span>

- <span data-ttu-id="262dc-193">lancer des tests Pester dans le débogueur ;</span><span class="sxs-lookup"><span data-stu-id="262dc-193">Launch Pester tests in the debugger.</span></span>
- <span data-ttu-id="262dc-194">lancer un fichier spécifique avec des arguments dans le débogueur ;</span><span class="sxs-lookup"><span data-stu-id="262dc-194">Launch a specific file with arguments in the debugger.</span></span>
- <span data-ttu-id="262dc-195">lancer une session interactive dans le débogueur ;</span><span class="sxs-lookup"><span data-stu-id="262dc-195">Launch an interactive session in the debugger.</span></span>
- <span data-ttu-id="262dc-196">attacher le débogueur à un processus hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="262dc-196">Attach the debugger to a PowerShell host process.</span></span>

<span data-ttu-id="262dc-197">Suivez ces étapes pour créer votre fichier de configuration de débogage :</span><span class="sxs-lookup"><span data-stu-id="262dc-197">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="262dc-198">Ouvrez la vue **Déboguer** sur Windows ou Linux en appuyant sur <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="262dc-198">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="262dc-199">Sur macOS, appuyez sur <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="262dc-199">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="262dc-200">Cliquez sur l’icône d’engrenage **Configurer** dans la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="262dc-200">Click the **Configure** gear icon in the toolbar.</span></span>
  1. <span data-ttu-id="262dc-201">VSCode vous invite à **Sélectionner un environnement**.</span><span class="sxs-lookup"><span data-stu-id="262dc-201">VSCode prompts you to **Select Environment**.</span></span> <span data-ttu-id="262dc-202">Choisissez **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="262dc-202">Choose **PowerShell**.</span></span>

<span data-ttu-id="262dc-203">VSCode crée alors un répertoire et un fichier `.vscode\launch.json` à la racine du dossier de votre espace de travail.</span><span class="sxs-lookup"><span data-stu-id="262dc-203">The result is that VSCode creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="262dc-204">C’est là que votre configuration de débogage est stockée.</span><span class="sxs-lookup"><span data-stu-id="262dc-204">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="262dc-205">Si vos fichiers se trouvent dans un référentiel Git, il est généralement préférable de valider le fichier `launch.json`.</span><span class="sxs-lookup"><span data-stu-id="262dc-205">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="262dc-206">Le fichier `launch.json` présente le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="262dc-206">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="262dc-207">Ce fichier représente les scénarios de débogage courants.</span><span class="sxs-lookup"><span data-stu-id="262dc-207">This file represents the common debug scenarios.</span></span> <span data-ttu-id="262dc-208">Quand vous ouvrez ce fichier dans l’éditeur, un bouton **Ajouter une configuration…** apparaît.</span><span class="sxs-lookup"><span data-stu-id="262dc-208">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="262dc-209">Vous pouvez cliquer sur ce bouton pour ajouter d’autres configurations de débogage PowerShell.</span><span class="sxs-lookup"><span data-stu-id="262dc-209">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="262dc-210">Il est utile d’ajouter la configuration **PowerShell : Lancer un script**.</span><span class="sxs-lookup"><span data-stu-id="262dc-210">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="262dc-211">Avec cette configuration, vous pouvez spécifier un fichier avec des arguments facultatifs qui doit se lancer quand vous appuyez sur <kbd>F5</kbd>, quel que soit le fichier actuellement actif dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="262dc-211">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="262dc-212">Une fois la configuration de débogage établie, vous pouvez sélectionner la configuration que vous souhaitez utiliser lors d’une session de débogage.</span><span class="sxs-lookup"><span data-stu-id="262dc-212">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="262dc-213">Sélectionnez une configuration dans la liste déroulante de la configuration de débogage, dans la barre d’outils de la vue **Déboguer**.</span><span class="sxs-lookup"><span data-stu-id="262dc-213">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="262dc-214">Quelques blogs peuvent être utiles pour bien démarrer avec l’extension PowerShell pour Visual Studio Code :</span><span class="sxs-lookup"><span data-stu-id="262dc-214">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="262dc-215">[Extension PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="262dc-215">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="262dc-216">[Écrire et déboguer des scripts PowerShell dans Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="262dc-216">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="262dc-217">[Aide sur le débogage avec Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="262dc-217">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="262dc-218">[Débogage de PowerShell dans Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="262dc-218">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="262dc-219">[Guide pratique pour le développement avec PowerShell dans Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="262dc-219">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="262dc-220">[Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="262dc-220">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="262dc-221">[Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="262dc-221">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="262dc-222">[Débogage des scripts PowerShell dans Visual Studio Code – Partie 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="262dc-222">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="262dc-223">[Débogage des scripts PowerShell dans Visual Studio Code – Partie 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="262dc-223">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../install/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-vscode"></a><span data-ttu-id="262dc-224">Extension PowerShell pour VSCode</span><span class="sxs-lookup"><span data-stu-id="262dc-224">PowerShell Extension for VSCode</span></span>

<span data-ttu-id="262dc-225">Vous trouverez le code source de l’extension PowerShell sur [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="262dc-225">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
