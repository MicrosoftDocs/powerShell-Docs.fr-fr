---
title: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
description: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 193243dc2e3e921b22a6ee068370200ae84ce4ac
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279244"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="d97d7-103">Guide pratique de réplication de l’expérience ISE dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d97d7-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="d97d7-104">Bien que l’extension PowerShell pour VSCode ne vise pas une parité complète des fonctionnalités avec PowerShell ISE, il existe des fonctionnalités qui rendent l’expérience offerte par VSCode plus naturelle pour les utilisateurs d’ISE.</span><span class="sxs-lookup"><span data-stu-id="d97d7-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="d97d7-105">Ce document vise à lister les paramètres configurables dans VSCode pour rendre l’expérience utilisateur plus proche d’ISE.</span><span class="sxs-lookup"><span data-stu-id="d97d7-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="ise-mode"></a><span data-ttu-id="d97d7-106">Mode ISE</span><span class="sxs-lookup"><span data-stu-id="d97d7-106">ISE Mode</span></span>

> [!NOTE]
> <span data-ttu-id="d97d7-107">Cette fonctionnalité est disponible dans l’extension PowerShell Preview à partir de la version 2019.12.0 et dans l’extension PowerShell à partir de la version 2020.3.0.</span><span class="sxs-lookup"><span data-stu-id="d97d7-107">This feature is available in the PowerShell Preview extension since version 2019.12.0 and in the PowerShell extension since version 2020.3.0.</span></span>

<span data-ttu-id="d97d7-108">Le moyen le plus simple de répliquer l’expérience ISE dans Visual Studio Code consiste à activer le « Mode ISE ».</span><span class="sxs-lookup"><span data-stu-id="d97d7-108">The easiest way to replicate the ISE experience in Visual Studio Code is by turning on "ISE Mode".</span></span>
<span data-ttu-id="d97d7-109">Pour cela, ouvrez la palette de commandes (<kbd>F1</kbd> ou <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> ou <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> sur macOS) et tapez « Mode ISE ».</span><span class="sxs-lookup"><span data-stu-id="d97d7-109">To do this, open the command pallet (<kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS) and type in "ISE Mode".</span></span>
<span data-ttu-id="d97d7-110">Sélectionnez « PowerShell : Activer le mode ISE » dans la liste.</span><span class="sxs-lookup"><span data-stu-id="d97d7-110">Select "PowerShell: Enable ISE Mode" from the list.</span></span>

<span data-ttu-id="d97d7-111">Cette commande applique automatiquement la plupart des paramètres figurant dans ce document.</span><span class="sxs-lookup"><span data-stu-id="d97d7-111">This command will apply a lot of the settings found in this document automatically.</span></span>
<span data-ttu-id="d97d7-112">Le résultat ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="d97d7-112">The result looks like this:</span></span>

![Mode ISE](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

<span data-ttu-id="d97d7-114">La suite de cet article contient des informations plus détaillées sur les paramètres du mode ISE et certains paramètres supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="d97d7-114">The rest of this article includes more detailed information on settings in ISE Mode and some additional settings.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="d97d7-115">Combinaisons de touches</span><span class="sxs-lookup"><span data-stu-id="d97d7-115">Key bindings</span></span>

| <span data-ttu-id="d97d7-116">Fonction</span><span class="sxs-lookup"><span data-stu-id="d97d7-116">Function</span></span>                              | <span data-ttu-id="d97d7-117">Combinaison ISE</span><span class="sxs-lookup"><span data-stu-id="d97d7-117">ISE Binding</span></span>                  | <span data-ttu-id="d97d7-118">Combinaison VSCode</span><span class="sxs-lookup"><span data-stu-id="d97d7-118">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="d97d7-119">Interrompre et arrêter le débogueur</span><span class="sxs-lookup"><span data-stu-id="d97d7-119">Interrupt and break debugger</span></span>          | <span data-ttu-id="d97d7-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="d97d7-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="d97d7-121"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="d97d7-121"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="d97d7-122">Exécuter la ligne active/le texte mis en surbrillance</span><span class="sxs-lookup"><span data-stu-id="d97d7-122">Execute current line/highlighted text</span></span> | <span data-ttu-id="d97d7-123"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="d97d7-123"><kbd>F8</kbd></span></span>                | <span data-ttu-id="d97d7-124"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="d97d7-124"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="d97d7-125">Lister les extraits de code disponibles</span><span class="sxs-lookup"><span data-stu-id="d97d7-125">List available snippets</span></span>               | <span data-ttu-id="d97d7-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="d97d7-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="d97d7-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="d97d7-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="d97d7-128">Combinaisons de touches personnalisées</span><span class="sxs-lookup"><span data-stu-id="d97d7-128">Custom Key bindings</span></span>

<span data-ttu-id="d97d7-129">Vous pouvez également [configurer vos propres combinaisons de touches](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) dans VSCode.</span><span class="sxs-lookup"><span data-stu-id="d97d7-129">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="simplified-ise-like-ui"></a><span data-ttu-id="d97d7-130">Interface utilisateur de type ISE simplifiée</span><span class="sxs-lookup"><span data-stu-id="d97d7-130">Simplified ISE-like UI</span></span>

<span data-ttu-id="d97d7-131">Si vous envisagez de simplifier l’interface utilisateur Visual Studio Code pour vous rapprocher de l’interface utilisateur de l’environnement ISE, appliquez les deux paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="d97d7-131">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

> [!NOTE]
> <span data-ttu-id="d97d7-132">Ces paramètres sont inclus dans le [« Mode ISE »](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="d97d7-132">These settings are included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="d97d7-133">Ceci permet de masquer les sections « Barre d’activité » et « Barre latérale de débogage » ci-dessous dans l’encadré rouge :</span><span class="sxs-lookup"><span data-stu-id="d97d7-133">This will hide the "Activity Bar" and the "Debug Side Bar" sections below inside of the red box:</span></span>

![la section en surbrillance comprend une barre d’activité et une barre latérale de débogage](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

<span data-ttu-id="d97d7-135">Le résultat final ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="d97d7-135">The end result looks like this:</span></span>

![Vue simplifiée de VS Code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a><span data-ttu-id="d97d7-137">Saisie semi-automatique via la touche Tab</span><span class="sxs-lookup"><span data-stu-id="d97d7-137">Tab completion</span></span>

<span data-ttu-id="d97d7-138">Pour activer une autocomplétion semblable à ISE, ajoutez ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="d97d7-138">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> <span data-ttu-id="d97d7-139">Ce paramètre a été ajouté directement à VSCode (et non dans l’extension).</span><span class="sxs-lookup"><span data-stu-id="d97d7-139">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="d97d7-140">Son comportement, déterminé par VSCode, n’est pas modifiable par l’extension.</span><span class="sxs-lookup"><span data-stu-id="d97d7-140">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

> [!NOTE]
> <span data-ttu-id="d97d7-141">Ce paramètre est inclus dans le [« Mode ISE »](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="d97d7-141">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="d97d7-142">Aucun focus sur la console lors de l'exécution</span><span class="sxs-lookup"><span data-stu-id="d97d7-142">No focus on console when executing</span></span>

<span data-ttu-id="d97d7-143">Pour maintenir le focus dans l’éditeur lors des exécutions avec <kbd>F8</kbd> :</span><span class="sxs-lookup"><span data-stu-id="d97d7-143">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

> [!NOTE]
> <span data-ttu-id="d97d7-144">Ce paramètre est inclus dans le [« Mode ISE »](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="d97d7-144">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="d97d7-145">La valeur par défaut est `true` pour des raisons d'accessibilité.</span><span class="sxs-lookup"><span data-stu-id="d97d7-145">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="d97d7-146">Ne pas lancer la console intégrée au démarrage</span><span class="sxs-lookup"><span data-stu-id="d97d7-146">Don't start integrated console on startup</span></span>

<span data-ttu-id="d97d7-147">Pour arrêter la console intégrée au démarrage, définissez :</span><span class="sxs-lookup"><span data-stu-id="d97d7-147">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="d97d7-148">Le processus PowerShell en arrière-plan démarrera toujours, dans la mesure où il apporte IntelliSense, l’analyse de script, la navigation dans les symboles, etc. La console, en revanche, ne s’affichera pas.</span><span class="sxs-lookup"><span data-stu-id="d97d7-148">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="d97d7-149">Considérer par défaut les fichiers comme PowerShell</span><span class="sxs-lookup"><span data-stu-id="d97d7-149">Assume files are PowerShell by default</span></span>

<span data-ttu-id="d97d7-150">Pour que les nouveaux fichiers et les fichiers sans titre soient par défaut inscrits comme PowerShell :</span><span class="sxs-lookup"><span data-stu-id="d97d7-150">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell",
```

> [!NOTE]
> <span data-ttu-id="d97d7-151">Ce paramètre est inclus dans le [« Mode ISE »](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="d97d7-151">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="color-scheme"></a><span data-ttu-id="d97d7-152">Modèle de couleurs</span><span class="sxs-lookup"><span data-stu-id="d97d7-152">Color scheme</span></span>

<span data-ttu-id="d97d7-153">De nombreux thèmes ISE, qui font ressembler l’éditeur à ISE, sont disponibles pour VSCode.</span><span class="sxs-lookup"><span data-stu-id="d97d7-153">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="d97d7-154">Dans la [palette de commandes], tapez `theme` pour obtenir `Preferences: Color Theme` et appuyez sur <kbd>Entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d97d7-154">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="d97d7-155">Dans la liste déroulante, sélectionnez `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="d97d7-155">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="d97d7-156">Pour définir ce thème dans les paramètres :</span><span class="sxs-lookup"><span data-stu-id="d97d7-156">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE",
```

> [!NOTE]
> <span data-ttu-id="d97d7-157">Ce paramètre est inclus dans le [« Mode ISE »](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="d97d7-157">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="powershell-command-explorer"></a><span data-ttu-id="d97d7-158">Explorateur de commandes PowerShell</span><span class="sxs-lookup"><span data-stu-id="d97d7-158">PowerShell Command Explorer</span></span>

<span data-ttu-id="d97d7-159">Grâce au travail de [@corbob](https://github.com/corbob), l’extension PowerShell a un début d’explorateur de commandes.</span><span class="sxs-lookup"><span data-stu-id="d97d7-159">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="d97d7-160">Dans la [palette de commandes], entrez `PowerShell Command Explorer` et appuyez sur <kbd>Entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d97d7-160">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

> [!NOTE]
> <span data-ttu-id="d97d7-161">Il s’affiche automatiquement en [« Mode ISE »](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="d97d7-161">This is shown automatically in ["ISE Mode"](#ise-mode).</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="d97d7-162">Ouvrir dans ISE</span><span class="sxs-lookup"><span data-stu-id="d97d7-162">Open in the ISE</span></span>

<span data-ttu-id="d97d7-163">Si vous souhaitez quand même ouvrir un fichier dans ISE, vous pouvez utiliser <kbd>Maj</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d97d7-163">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="d97d7-164">Autres ressources</span><span class="sxs-lookup"><span data-stu-id="d97d7-164">Other resources</span></span>

- <span data-ttu-id="d97d7-165">4sysops propose un [excellent article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) qui explique comment configurer VSCode comme ISE.</span><span class="sxs-lookup"><span data-stu-id="d97d7-165">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="d97d7-166">Mike F Robbins a publié un [remarquable billet](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) sur la configuration de VSCode.</span><span class="sxs-lookup"><span data-stu-id="d97d7-166">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="d97d7-167">Learn PowerShell fait un [compte rendu brillant](https://www.learnpwsh.com/setup-vs-code-for-powershell/) de la configuration de VSCode pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d97d7-167">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="d97d7-168">Paramètres supplémentaires</span><span class="sxs-lookup"><span data-stu-id="d97d7-168">More settings</span></span>

<span data-ttu-id="d97d7-169">Si vous connaissez d’autres moyens de rendre VSCode plus intuitif pour les utilisateurs d’ISE, contribuez à ce document. Si vous êtes à la recherche d’une configuration de compatibilité, mais que vous ne trouvez aucun moyen de l’activer, [signalez le problème](https://github.com/PowerShell/vscode-powershell/issues/new/choose) !</span><span class="sxs-lookup"><span data-stu-id="d97d7-169">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="d97d7-170">Les PR et les contributions sont également les bienvenues, comme toujours !</span><span class="sxs-lookup"><span data-stu-id="d97d7-170">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="d97d7-171">Conseils VSCode</span><span class="sxs-lookup"><span data-stu-id="d97d7-171">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="d97d7-172">Palette de commandes</span><span class="sxs-lookup"><span data-stu-id="d97d7-172">Command Palette</span></span>

<span data-ttu-id="d97d7-173"><kbd>F1</kbd> OU <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> sur macOS)</span><span class="sxs-lookup"><span data-stu-id="d97d7-173"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="d97d7-174">Un moyen pratique d’exécuter des commandes dans VSCode.</span><span class="sxs-lookup"><span data-stu-id="d97d7-174">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="d97d7-175">Pour plus d’informations, voir les [documents VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="d97d7-175">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Palette de commandes]: #command-palette
[Command Palette]: #command-palette
