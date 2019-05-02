---
title: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
description: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058503"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="e02fa-103">Guide pratique de réplication de l’expérience ISE dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e02fa-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="e02fa-104">Bien que l’extension PowerShell pour VSCode ne vise pas une parité complète des fonctionnalités avec PowerShell ISE, il existe des fonctionnalités qui rendent l’expérience offerte par VSCode plus naturelle pour les utilisateurs d’ISE.</span><span class="sxs-lookup"><span data-stu-id="e02fa-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="e02fa-105">Ce document vise à lister les paramètres configurables dans VSCode pour rendre l’expérience utilisateur plus proche d’ISE.</span><span class="sxs-lookup"><span data-stu-id="e02fa-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="e02fa-106">Combinaisons de touches</span><span class="sxs-lookup"><span data-stu-id="e02fa-106">Key bindings</span></span>

| <span data-ttu-id="e02fa-107">Fonction</span><span class="sxs-lookup"><span data-stu-id="e02fa-107">Function</span></span>                              | <span data-ttu-id="e02fa-108">Combinaison ISE</span><span class="sxs-lookup"><span data-stu-id="e02fa-108">ISE Binding</span></span>                  | <span data-ttu-id="e02fa-109">Combinaison VSCode</span><span class="sxs-lookup"><span data-stu-id="e02fa-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="e02fa-110">Interrompre et arrêter le débogueur</span><span class="sxs-lookup"><span data-stu-id="e02fa-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="e02fa-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="e02fa-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="e02fa-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="e02fa-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="e02fa-113">Exécuter la ligne active/le texte mis en surbrillance</span><span class="sxs-lookup"><span data-stu-id="e02fa-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="e02fa-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="e02fa-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="e02fa-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="e02fa-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="e02fa-116">Lister les extraits de code disponibles</span><span class="sxs-lookup"><span data-stu-id="e02fa-116">List available snippets</span></span>               | <span data-ttu-id="e02fa-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="e02fa-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="e02fa-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="e02fa-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="e02fa-119">Combinaisons de touches personnalisées</span><span class="sxs-lookup"><span data-stu-id="e02fa-119">Custom Key bindings</span></span>

<span data-ttu-id="e02fa-120">Vous pouvez également [configurer vos propres combinaisons de touches](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) dans VSCode.</span><span class="sxs-lookup"><span data-stu-id="e02fa-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="e02fa-121">Saisie semi-automatique via la touche Tab</span><span class="sxs-lookup"><span data-stu-id="e02fa-121">Tab completion</span></span>

<span data-ttu-id="e02fa-122">Pour activer une autocomplétion semblable à ISE, ajoutez ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="e02fa-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="e02fa-123">Ce paramètre a été ajouté directement à VSCode (et non dans l’extension).</span><span class="sxs-lookup"><span data-stu-id="e02fa-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="e02fa-124">Son comportement, déterminé par VSCode, n’est pas modifiable par l’extension.</span><span class="sxs-lookup"><span data-stu-id="e02fa-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="e02fa-125">Pas de focus sur la console lors de l’exécution</span><span class="sxs-lookup"><span data-stu-id="e02fa-125">No focus on console when executing</span></span>

<span data-ttu-id="e02fa-126">Pour maintenir le focus dans l’éditeur lors des exécutions avec <kbd>F8</kbd> :</span><span class="sxs-lookup"><span data-stu-id="e02fa-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="e02fa-127">La valeur par défaut est `true` à des fins d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="e02fa-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="e02fa-128">Ne pas lancer la console intégrée au démarrage</span><span class="sxs-lookup"><span data-stu-id="e02fa-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="e02fa-129">Pour arrêter la console intégrée au démarrage, définissez :</span><span class="sxs-lookup"><span data-stu-id="e02fa-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="e02fa-130">Le processus PowerShell en arrière-plan démarrera toujours, dans la mesure où il apporte IntelliSense, l’analyse de script, la navigation dans les symboles, etc. La console, en revanche, ne s’affichera pas.</span><span class="sxs-lookup"><span data-stu-id="e02fa-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="e02fa-131">Considérer par défaut les fichiers comme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e02fa-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="e02fa-132">Pour que les nouveaux fichiers et les fichiers sans titre soient par défaut inscrits comme PowerShell :</span><span class="sxs-lookup"><span data-stu-id="e02fa-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="e02fa-133">Modèle de couleurs</span><span class="sxs-lookup"><span data-stu-id="e02fa-133">Color scheme</span></span>

<span data-ttu-id="e02fa-134">De nombreux thèmes ISE, qui font ressembler l’éditeur à ISE, sont disponibles pour VSCode.</span><span class="sxs-lookup"><span data-stu-id="e02fa-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="e02fa-135">Dans la [palette de commandes], tapez `theme` pour obtenir `Preferences: Color Theme` et appuyez sur <kbd>Entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e02fa-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="e02fa-136">Dans la liste déroulante, sélectionnez `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="e02fa-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="e02fa-137">Pour définir ce thème dans les paramètres :</span><span class="sxs-lookup"><span data-stu-id="e02fa-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="e02fa-138">Explorateur de commandes PowerShell</span><span class="sxs-lookup"><span data-stu-id="e02fa-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="e02fa-139">Grâce au travail de [@corbob](https://github.com/corbob), l’extension PowerShell a un début d’explorateur de commandes.</span><span class="sxs-lookup"><span data-stu-id="e02fa-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="e02fa-140">Dans la [palette de commandes], entrez `PowerShell Command Explorer` et appuyez sur <kbd>Entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e02fa-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="e02fa-141">Ouvrir dans ISE</span><span class="sxs-lookup"><span data-stu-id="e02fa-141">Open in the ISE</span></span>

<span data-ttu-id="e02fa-142">Si vous souhaitez quand même ouvrir un fichier dans ISE, vous pouvez utiliser <kbd>Maj</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e02fa-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="e02fa-143">Autres ressources</span><span class="sxs-lookup"><span data-stu-id="e02fa-143">Other resources</span></span>

- <span data-ttu-id="e02fa-144">4sysops propose un [excellent article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) qui explique comment configurer VSCode comme ISE.</span><span class="sxs-lookup"><span data-stu-id="e02fa-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="e02fa-145">Mike F Robbins a publié un [remarquable billet](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) sur la configuration de VSCode.</span><span class="sxs-lookup"><span data-stu-id="e02fa-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="e02fa-146">Learn PowerShell fait un [compte rendu brillant](https://www.learnpwsh.com/setup-vs-code-for-powershell/) de la configuration de VSCode pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e02fa-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="e02fa-147">Paramètres supplémentaires</span><span class="sxs-lookup"><span data-stu-id="e02fa-147">More settings</span></span>

<span data-ttu-id="e02fa-148">Si vous connaissez d’autres moyens de rendre VSCode plus intuitif pour les utilisateurs d’ISE, contribuez à ce document. Si vous êtes à la recherche d’une configuration de compatibilité, mais que vous ne trouvez aucun moyen de l’activer, [signalez le problème](https://github.com/PowerShell/vscode-powershell/issues/new/choose) !</span><span class="sxs-lookup"><span data-stu-id="e02fa-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="e02fa-149">Les PR et les contributions sont également les bienvenues, comme toujours !</span><span class="sxs-lookup"><span data-stu-id="e02fa-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="e02fa-150">Conseils VSCode</span><span class="sxs-lookup"><span data-stu-id="e02fa-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="e02fa-151">Palette de commandes</span><span class="sxs-lookup"><span data-stu-id="e02fa-151">Command Palette</span></span>

<span data-ttu-id="e02fa-152"><kbd>F1</kbd> OU <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> sur macOS)</span><span class="sxs-lookup"><span data-stu-id="e02fa-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="e02fa-153">Un moyen pratique d’exécuter des commandes dans VSCode.</span><span class="sxs-lookup"><span data-stu-id="e02fa-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="e02fa-154">Pour plus d’informations, voir les [documents VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="e02fa-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Palette de commandes]: #command-palette
[Command Palette]: #command-palette
