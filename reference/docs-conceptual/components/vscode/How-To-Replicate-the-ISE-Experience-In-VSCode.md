---
title: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
description: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: d5542e9a3a48b1ae64356309be669418edf6c79e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117482"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="0f7a2-103">Guide pratique de réplication de l’expérience ISE dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="0f7a2-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="0f7a2-104">Bien que l’extension PowerShell pour VSCode ne vise pas une parité complète des fonctionnalités avec PowerShell ISE, il existe des fonctionnalités qui rendent l’expérience offerte par VSCode plus naturelle pour les utilisateurs d’ISE.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="0f7a2-105">Ce document vise à lister les paramètres configurables dans VSCode pour rendre l’expérience utilisateur plus proche d’ISE.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="0f7a2-106">Combinaisons de touches</span><span class="sxs-lookup"><span data-stu-id="0f7a2-106">Key bindings</span></span>

| <span data-ttu-id="0f7a2-107">Fonction</span><span class="sxs-lookup"><span data-stu-id="0f7a2-107">Function</span></span>                              | <span data-ttu-id="0f7a2-108">Combinaison ISE</span><span class="sxs-lookup"><span data-stu-id="0f7a2-108">ISE Binding</span></span>                  | <span data-ttu-id="0f7a2-109">Combinaison VSCode</span><span class="sxs-lookup"><span data-stu-id="0f7a2-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="0f7a2-110">Interrompre et arrêter le débogueur</span><span class="sxs-lookup"><span data-stu-id="0f7a2-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="0f7a2-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="0f7a2-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="0f7a2-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="0f7a2-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="0f7a2-113">Exécuter la ligne active/le texte mis en surbrillance</span><span class="sxs-lookup"><span data-stu-id="0f7a2-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="0f7a2-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="0f7a2-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="0f7a2-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="0f7a2-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="0f7a2-116">Lister les extraits de code disponibles</span><span class="sxs-lookup"><span data-stu-id="0f7a2-116">List available snippets</span></span>               | <span data-ttu-id="0f7a2-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="0f7a2-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="0f7a2-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="0f7a2-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="0f7a2-119">Combinaisons de touches personnalisées</span><span class="sxs-lookup"><span data-stu-id="0f7a2-119">Custom Key bindings</span></span>

<span data-ttu-id="0f7a2-120">Vous pouvez également [configurer vos propres combinaisons de touches](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) dans VSCode.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="simplified-ise-like-ui"></a><span data-ttu-id="0f7a2-121">Interface utilisateur de type ISE simplifiée</span><span class="sxs-lookup"><span data-stu-id="0f7a2-121">Simplified ISE-like UI</span></span>

<span data-ttu-id="0f7a2-122">Si vous envisagez de simplifier l’interface utilisateur Visual Studio Code pour vous rapprocher de l’interface utilisateur de l’environnement ISE, appliquez les deux paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="0f7a2-122">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

<span data-ttu-id="0f7a2-123">Ceci permet de masquer les sections « Barre d’activité » et « Barre latérale de débogage » ci-dessous dans l’encadré rouge :</span><span class="sxs-lookup"><span data-stu-id="0f7a2-123">This will hide the "Activity Bar" and the "Debug Side Bar" sections below inside of the red box:</span></span>

![la section en surbrillance comprend une barre d’activité et une barre latérale de débogage](images/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

<span data-ttu-id="0f7a2-125">Le résultat final ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="0f7a2-125">The end result looks like this:</span></span>

![Vue simplifiée de VS Code](images/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a><span data-ttu-id="0f7a2-127">Saisie semi-automatique via la touche Tab</span><span class="sxs-lookup"><span data-stu-id="0f7a2-127">Tab completion</span></span>

<span data-ttu-id="0f7a2-128">Pour activer une autocomplétion semblable à ISE, ajoutez ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="0f7a2-128">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> <span data-ttu-id="0f7a2-129">Ce paramètre a été ajouté directement à VSCode (et non dans l’extension).</span><span class="sxs-lookup"><span data-stu-id="0f7a2-129">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="0f7a2-130">Son comportement, déterminé par VSCode, n’est pas modifiable par l’extension.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-130">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="0f7a2-131">Pas de focus sur la console lors de l’exécution</span><span class="sxs-lookup"><span data-stu-id="0f7a2-131">No focus on console when executing</span></span>

<span data-ttu-id="0f7a2-132">Pour maintenir le focus dans l’éditeur lors des exécutions avec <kbd>F8</kbd> :</span><span class="sxs-lookup"><span data-stu-id="0f7a2-132">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="0f7a2-133">La valeur par défaut est `true` à des fins d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-133">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="0f7a2-134">Ne pas lancer la console intégrée au démarrage</span><span class="sxs-lookup"><span data-stu-id="0f7a2-134">Don't start integrated console on startup</span></span>

<span data-ttu-id="0f7a2-135">Pour arrêter la console intégrée au démarrage, définissez :</span><span class="sxs-lookup"><span data-stu-id="0f7a2-135">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="0f7a2-136">Le processus PowerShell en arrière-plan démarrera toujours, dans la mesure où il apporte IntelliSense, l’analyse de script, la navigation dans les symboles, etc. La console, en revanche, ne s’affichera pas.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-136">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="0f7a2-137">Considérer par défaut les fichiers comme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f7a2-137">Assume files are PowerShell by default</span></span>

<span data-ttu-id="0f7a2-138">Pour que les nouveaux fichiers et les fichiers sans titre soient par défaut inscrits comme PowerShell :</span><span class="sxs-lookup"><span data-stu-id="0f7a2-138">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell",
```

## <a name="color-scheme"></a><span data-ttu-id="0f7a2-139">Modèle de couleurs</span><span class="sxs-lookup"><span data-stu-id="0f7a2-139">Color scheme</span></span>

<span data-ttu-id="0f7a2-140">De nombreux thèmes ISE, qui font ressembler l’éditeur à ISE, sont disponibles pour VSCode.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-140">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="0f7a2-141">Dans la [palette de commandes], tapez `theme` pour obtenir `Preferences: Color Theme` et appuyez sur <kbd>Entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-141">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="0f7a2-142">Dans la liste déroulante, sélectionnez `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-142">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="0f7a2-143">Pour définir ce thème dans les paramètres :</span><span class="sxs-lookup"><span data-stu-id="0f7a2-143">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE",
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="0f7a2-144">Explorateur de commandes PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f7a2-144">PowerShell Command Explorer</span></span>

<span data-ttu-id="0f7a2-145">Grâce au travail de [@corbob](https://github.com/corbob), l’extension PowerShell a un début d’explorateur de commandes.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-145">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="0f7a2-146">Dans la [palette de commandes], entrez `PowerShell Command Explorer` et appuyez sur <kbd>Entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-146">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="0f7a2-147">Ouvrir dans ISE</span><span class="sxs-lookup"><span data-stu-id="0f7a2-147">Open in the ISE</span></span>

<span data-ttu-id="0f7a2-148">Si vous souhaitez quand même ouvrir un fichier dans ISE, vous pouvez utiliser <kbd>Maj</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-148">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="0f7a2-149">Autres ressources</span><span class="sxs-lookup"><span data-stu-id="0f7a2-149">Other resources</span></span>

- <span data-ttu-id="0f7a2-150">4sysops propose un [excellent article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) qui explique comment configurer VSCode comme ISE.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-150">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="0f7a2-151">Mike F Robbins a publié un [remarquable billet](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) sur la configuration de VSCode.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-151">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="0f7a2-152">Learn PowerShell fait un [compte rendu brillant](https://www.learnpwsh.com/setup-vs-code-for-powershell/) de la configuration de VSCode pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-152">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="0f7a2-153">Paramètres supplémentaires</span><span class="sxs-lookup"><span data-stu-id="0f7a2-153">More settings</span></span>

<span data-ttu-id="0f7a2-154">Si vous connaissez d’autres moyens de rendre VSCode plus intuitif pour les utilisateurs d’ISE, contribuez à ce document. Si vous êtes à la recherche d’une configuration de compatibilité, mais que vous ne trouvez aucun moyen de l’activer, [signalez le problème](https://github.com/PowerShell/vscode-powershell/issues/new/choose) !</span><span class="sxs-lookup"><span data-stu-id="0f7a2-154">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="0f7a2-155">Les PR et les contributions sont également les bienvenues, comme toujours !</span><span class="sxs-lookup"><span data-stu-id="0f7a2-155">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="0f7a2-156">Conseils VSCode</span><span class="sxs-lookup"><span data-stu-id="0f7a2-156">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="0f7a2-157">Palette de commandes</span><span class="sxs-lookup"><span data-stu-id="0f7a2-157">Command Palette</span></span>

<span data-ttu-id="0f7a2-158"><kbd>F1</kbd> OU <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> sur macOS)</span><span class="sxs-lookup"><span data-stu-id="0f7a2-158"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="0f7a2-159">Un moyen pratique d’exécuter des commandes dans VSCode.</span><span class="sxs-lookup"><span data-stu-id="0f7a2-159">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="0f7a2-160">Pour plus d’informations, voir les [documents VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="0f7a2-160">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Palette de commandes]: #command-palette
[Command Palette]: #command-palette
