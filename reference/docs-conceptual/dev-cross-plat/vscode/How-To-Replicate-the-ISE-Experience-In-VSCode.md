---
title: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
description: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 899e1c393fd49b0659631b88d610e80ec885e69e
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809595"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="67931-103">Guide pratique de réplication de l’expérience ISE dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="67931-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="67931-104">Bien que l’extension PowerShell pour VS Code ne vise pas une parité complète des fonctionnalités avec PowerShell ISE, il existe des fonctionnalités qui rendent l’expérience offerte par VS Code plus naturelle pour les utilisateurs d’ISE.</span><span class="sxs-lookup"><span data-stu-id="67931-104">While the PowerShell extension for VS Code doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VS Code experience more natural for users of the ISE.</span></span>

<span data-ttu-id="67931-105">Ce document vise à lister les paramètres configurables dans VS Code pour rendre l’expérience utilisateur plus proche d’ISE.</span><span class="sxs-lookup"><span data-stu-id="67931-105">This document tries to list settings you can configure in VS Code to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="ise-mode"></a><span data-ttu-id="67931-106">Mode ISE</span><span class="sxs-lookup"><span data-stu-id="67931-106">ISE Mode</span></span>

> [!NOTE]
> <span data-ttu-id="67931-107">Cette fonctionnalité est disponible dans l’extension PowerShell Preview à partir de la version 2019.12.0 et dans l’extension PowerShell à partir de la version 2020.3.0.</span><span class="sxs-lookup"><span data-stu-id="67931-107">This feature is available in the PowerShell Preview extension since version 2019.12.0 and in the PowerShell extension since version 2020.3.0.</span></span>

<span data-ttu-id="67931-108">Le moyen le plus simple de répliquer l’expérience ISE dans Visual Studio Code consiste à activer le « Mode ISE ».</span><span class="sxs-lookup"><span data-stu-id="67931-108">The easiest way to replicate the ISE experience in Visual Studio Code is by turning on "ISE Mode".</span></span>
<span data-ttu-id="67931-109">Pour cela, ouvrez la palette de commandes (<kbd>F1</kbd> ou <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> ou <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> sur macOS) et tapez « Mode ISE ».</span><span class="sxs-lookup"><span data-stu-id="67931-109">To do this, open the command palette (<kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS) and type in "ISE Mode".</span></span> <span data-ttu-id="67931-110">Sélectionnez « PowerShell : Activer le mode ISE » dans la liste.</span><span class="sxs-lookup"><span data-stu-id="67931-110">Select "PowerShell: Enable ISE Mode" from the list.</span></span>

<span data-ttu-id="67931-111">Cette commande applique automatiquement les paramètres décrits ci-dessous. Le résultat ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="67931-111">This command automatically applies the settings described below The result looks like this:</span></span>

![Mode ISE](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

## <a name="ise-mode-configuration-settings"></a><span data-ttu-id="67931-113">Paramètres de configuration du mode ISE</span><span class="sxs-lookup"><span data-stu-id="67931-113">ISE Mode configuration settings</span></span>

<span data-ttu-id="67931-114">Le mode ISE apporte les modifications suivantes aux paramètres de VS Code.</span><span class="sxs-lookup"><span data-stu-id="67931-114">ISE Mode makes the following changes to VS Code settings.</span></span>

- <span data-ttu-id="67931-115">Combinaisons de touches</span><span class="sxs-lookup"><span data-stu-id="67931-115">Key bindings</span></span>

  |               <span data-ttu-id="67931-116">Fonction</span><span class="sxs-lookup"><span data-stu-id="67931-116">Function</span></span>                |         <span data-ttu-id="67931-117">Combinaison ISE</span><span class="sxs-lookup"><span data-stu-id="67931-117">ISE Binding</span></span>          |              <span data-ttu-id="67931-118">Liaison de VS Code</span><span class="sxs-lookup"><span data-stu-id="67931-118">VS Code Binding</span></span>                |
  | ------------------------------------- | ---------------------------- | ------------------------------------------- |
  | <span data-ttu-id="67931-119">Interrompre et arrêter le débogueur</span><span class="sxs-lookup"><span data-stu-id="67931-119">Interrupt and break debugger</span></span>          | <span data-ttu-id="67931-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="67931-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="67931-121"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="67931-121"><kbd>F6</kbd></span></span>                               |
  | <span data-ttu-id="67931-122">Exécuter la ligne active/le texte mis en surbrillance</span><span class="sxs-lookup"><span data-stu-id="67931-122">Execute current line/highlighted text</span></span> | <span data-ttu-id="67931-123"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="67931-123"><kbd>F8</kbd></span></span>                | <span data-ttu-id="67931-124"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="67931-124"><kbd>F8</kbd></span></span>                               |
  | <span data-ttu-id="67931-125">Lister les extraits de code disponibles</span><span class="sxs-lookup"><span data-stu-id="67931-125">List available snippets</span></span>               | <span data-ttu-id="67931-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="67931-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="67931-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="67931-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

  > [!NOTE]
  > <span data-ttu-id="67931-128">Vous pouvez également [configurer vos propres combinaisons de touches](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) dans VS Code.</span><span class="sxs-lookup"><span data-stu-id="67931-128">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VS Code as well.</span></span>

- <span data-ttu-id="67931-129">Interface utilisateur de type ISE simplifiée</span><span class="sxs-lookup"><span data-stu-id="67931-129">Simplified ISE-like UI</span></span>

  <span data-ttu-id="67931-130">Si vous envisagez de simplifier l’interface utilisateur Visual Studio Code pour vous rapprocher de l’interface utilisateur de l’environnement ISE, appliquez les deux paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="67931-130">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

  ```json
  "workbench.activityBar.visible": false,
  "debug.openDebug": "neverOpen",
  ```

  <span data-ttu-id="67931-131">Ces paramètres masquent les sections « Barre d’activité » et « Barre latérale de débogage » indiquées ci-dessous dans l’encadré rouge :</span><span class="sxs-lookup"><span data-stu-id="67931-131">These settings hide the "Activity Bar" and the "Debug Side Bar" sections shown inside the red box below:</span></span>

  ![la section en surbrillance comprend une barre d’activité et une barre latérale de débogage](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

  <span data-ttu-id="67931-133">Le résultat final ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="67931-133">The end result looks like this:</span></span>

  ![Vue simplifiée de VS Code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

- <span data-ttu-id="67931-135">Saisie semi-automatique via la touche Tab</span><span class="sxs-lookup"><span data-stu-id="67931-135">Tab completion</span></span>

  <span data-ttu-id="67931-136">Pour activer une autocomplétion semblable à ISE, ajoutez ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="67931-136">To enable more ISE-like tab completion, add this setting:</span></span>

  ```json
  "editor.tabCompletion": "on",
  ```

- <span data-ttu-id="67931-137">Aucun focus sur la console lors de l'exécution</span><span class="sxs-lookup"><span data-stu-id="67931-137">No focus on console when executing</span></span>

  <span data-ttu-id="67931-138">Pour maintenir le focus dans l’éditeur lors des exécutions avec <kbd>F8</kbd> :</span><span class="sxs-lookup"><span data-stu-id="67931-138">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

  ```json
  "powershell.integratedConsole.focusConsoleOnExecute": false
  ```

  <span data-ttu-id="67931-139">La valeur par défaut est `true` pour des raisons d'accessibilité.</span><span class="sxs-lookup"><span data-stu-id="67931-139">The default is `true` for accessibility purposes.</span></span>

- <span data-ttu-id="67931-140">Ne pas lancer la console intégrée au démarrage</span><span class="sxs-lookup"><span data-stu-id="67931-140">Don't start integrated console on startup</span></span>

  <span data-ttu-id="67931-141">Pour arrêter la console intégrée au démarrage, définissez :</span><span class="sxs-lookup"><span data-stu-id="67931-141">To stop the integrated console on startup, set:</span></span>

  ```json
  "powershell.integratedConsole.showOnStartup": false
  ```

  > [!NOTE]
  > <span data-ttu-id="67931-142">Le processus PowerShell en arrière-plan démarre toujours pour fournir IntelliSense, l’analyse de script, la navigation dans les symboles, etc., mais la console ne s’affiche pas.</span><span class="sxs-lookup"><span data-stu-id="67931-142">The background PowerShell process still starts to provide IntelliSense, script analysis, symbol navigation, etc., but the console won't be shown.</span></span>

- <span data-ttu-id="67931-143">Considérer par défaut les fichiers comme PowerShell</span><span class="sxs-lookup"><span data-stu-id="67931-143">Assume files are PowerShell by default</span></span>

  <span data-ttu-id="67931-144">Pour que les nouveaux fichiers et les fichiers sans titre soient par défaut inscrits comme PowerShell :</span><span class="sxs-lookup"><span data-stu-id="67931-144">To make new/untitled files, register as PowerShell by default:</span></span>

  ```json
  "files.defaultLanguage": "powershell",
  ```

- <span data-ttu-id="67931-145">Modèle de couleurs</span><span class="sxs-lookup"><span data-stu-id="67931-145">Color scheme</span></span>

  <span data-ttu-id="67931-146">De nombreux thèmes ISE, qui font ressembler l’éditeur à ISE, sont disponibles pour VS Code.</span><span class="sxs-lookup"><span data-stu-id="67931-146">There are a number of ISE themes available for VS Code to make the editor look much more like the ISE.</span></span>

  <span data-ttu-id="67931-147">Dans la [palette de commandes][], tapez `theme` pour obtenir `Preferences: Color Theme` et appuyez sur <kbd>Entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="67931-147">In the [Command Palette][] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span> <span data-ttu-id="67931-148">Dans la liste déroulante, sélectionnez `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="67931-148">In the drop-down list, select `PowerShell ISE`.</span></span>

  <span data-ttu-id="67931-149">Pour définir ce thème dans les paramètres :</span><span class="sxs-lookup"><span data-stu-id="67931-149">You can set this theme in the settings with:</span></span>

  ```json
  "workbench.colorTheme": "PowerShell ISE",
  ```

- <span data-ttu-id="67931-150">Explorateur de commandes PowerShell</span><span class="sxs-lookup"><span data-stu-id="67931-150">PowerShell Command Explorer</span></span>

  <span data-ttu-id="67931-151">Grâce au travail de [@corbob](https://github.com/corbob), l’extension PowerShell a un début d’explorateur de commandes.</span><span class="sxs-lookup"><span data-stu-id="67931-151">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

  <span data-ttu-id="67931-152">Dans la [palette de commandes][], entrez `PowerShell Command Explorer` et appuyez sur <kbd>Entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="67931-152">In the [Command Palette][], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

- <span data-ttu-id="67931-153">Ouvrir dans ISE</span><span class="sxs-lookup"><span data-stu-id="67931-153">Open in the ISE</span></span>

  <span data-ttu-id="67931-154">Si vous souhaitez quand même ouvrir un fichier dans l’ISE Windows PowerShell, ouvrez la [Palette de commandes][], recherchez « ouvrir dans ISE », puis sélectionnez **PowerShell : Ouvre le fichier actif dans l’ISE PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="67931-154">If you want to open a file in the Windows PowerShell ISE anyway, open the [Command Palette][], search for "open in ise", then select **PowerShell: Open Current File in PowerShell ISE**.</span></span>

## <a name="other-resources"></a><span data-ttu-id="67931-155">Autres ressources</span><span class="sxs-lookup"><span data-stu-id="67931-155">Other resources</span></span>

- <span data-ttu-id="67931-156">4sysops propose un [excellent article][4sysops] qui explique comment configurer VS Code comme ISE.</span><span class="sxs-lookup"><span data-stu-id="67931-156">4sysops has [a great article][4sysops] on configuring VS Code to be more like the ISE.</span></span>
- <span data-ttu-id="67931-157">Mike F Robbins a publié un [remarquable billet][mikefrobbins] sur la configuration de VS Code.</span><span class="sxs-lookup"><span data-stu-id="67931-157">Mike F Robbins has [a great post][mikefrobbins] on setting up VS Code.</span></span>
- <span data-ttu-id="67931-158">Learn PowerShell fait un [compte rendu brillant][learnpwsh] de la configuration pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67931-158">Learn PowerShell has [an excellent write up][learnpwsh] setup for PowerShell.</span></span>

## <a name="vs-code-tips"></a><span data-ttu-id="67931-159">Conseils relatifs à VS Code</span><span class="sxs-lookup"><span data-stu-id="67931-159">VS Code Tips</span></span>

- <span data-ttu-id="67931-160">Palette de commandes</span><span class="sxs-lookup"><span data-stu-id="67931-160">Command Palette</span></span>

  <span data-ttu-id="67931-161">La Palette de commandes est un moyen pratique d’exécuter des commandes dans VS Code.</span><span class="sxs-lookup"><span data-stu-id="67931-161">The Command Palette is handy way of executing commands in VS Code.</span></span> <span data-ttu-id="67931-162">Ouvrez la palette de commandes à l’aide de <kbd>F1</kbd> OU <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> OU <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> sur macOS.</span><span class="sxs-lookup"><span data-stu-id="67931-162">Open the command palette using <kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS.</span></span>

  <span data-ttu-id="67931-163">Pour plus d’informations, consultez la [documentation VS Code][vsc-docs].</span><span class="sxs-lookup"><span data-stu-id="67931-163">For more information, see [the VS Code documentation][vsc-docs].</span></span>

- <span data-ttu-id="67931-164">Désactiver la console de débogage</span><span class="sxs-lookup"><span data-stu-id="67931-164">Disable the Debug Console</span></span>

  <span data-ttu-id="67931-165">Si vous planifiez uniquement l’utilisation de VS Code pour les scripts PowerShell, vous pouvez masquer la **Console de débogage**, car elle n’est pas utilisée par l’extension PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67931-165">If you only plan on using VS Code for PowerShell scripting, you can hide the **Debug Console** since it is not used by the PowerShell extension.</span></span> <span data-ttu-id="67931-166">Pour ce faire, cliquez avec le bouton droit sur **Console de débogage** puis cliquez sur la coche pour la masquer.</span><span class="sxs-lookup"><span data-stu-id="67931-166">To do so, right click on **Debug Console** then click on the check mark to hide it.</span></span>

## <a name="more-settings"></a><span data-ttu-id="67931-167">Paramètres supplémentaires</span><span class="sxs-lookup"><span data-stu-id="67931-167">More settings</span></span>

<span data-ttu-id="67931-168">Si vous connaissez d’autres moyens de rendre VS Code plus intuitif pour les utilisateurs d’ISE, contribuez à ce document. Si vous êtes à la recherche d’une configuration de compatibilité, mais que vous ne trouvez aucun moyen de l’activer, [signalez le problème][] !</span><span class="sxs-lookup"><span data-stu-id="67931-168">If you know of more ways to make VS Code feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue][] and ask away!</span></span>

<span data-ttu-id="67931-169">Les PR et les contributions sont également les bienvenues, comme toujours !</span><span class="sxs-lookup"><span data-stu-id="67931-169">We're always happy to accept PRs and contributions as well!</span></span>

<!-- link references -->
[vsc-docs]: https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette
[Palette de commandes]: #vs-code-tips
[Command Palette]: #vs-code-tips
[signalez le problème]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose
[open an issue]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose

[4sysops]: https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/
[mikefrobbins]: https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/
[learnpwsh]: https://www.learnpwsh.com/setup-vs-code-for-powershell/
