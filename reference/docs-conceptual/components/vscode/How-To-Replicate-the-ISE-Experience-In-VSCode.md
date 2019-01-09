---
title: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
description: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012481"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="ffd5e-103">Guide pratique de réplication de l’expérience ISE dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ffd5e-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="ffd5e-104">Bien que l’extension PowerShell pour VSCode ne recherche une parité complète avec PowerShell ISE, il existe des fonctionnalités en place pour rendre l’expérience VSCode plus naturel pour les utilisateurs de l’environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="ffd5e-105">Ce document tente de paramètres de la liste que vous pouvez configurer dans VSCode pour faciliter l’expérience d’un peu plus connue par rapport à l’environnement ISE utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="ffd5e-106">Combinaisons de touches</span><span class="sxs-lookup"><span data-stu-id="ffd5e-106">Key bindings</span></span>

| <span data-ttu-id="ffd5e-107">Fonction</span><span class="sxs-lookup"><span data-stu-id="ffd5e-107">Function</span></span>                              | <span data-ttu-id="ffd5e-108">Liaison de l’ISE</span><span class="sxs-lookup"><span data-stu-id="ffd5e-108">ISE Binding</span></span>                  | <span data-ttu-id="ffd5e-109">Liaison de VSCode</span><span class="sxs-lookup"><span data-stu-id="ffd5e-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="ffd5e-110">Interrompre et arrêter le débogueur</span><span class="sxs-lookup"><span data-stu-id="ffd5e-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="ffd5e-111"><kbd>CTRL</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="ffd5e-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="ffd5e-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="ffd5e-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="ffd5e-113">Exécuter le texte de ligne/la mise en surbrillance en cours</span><span class="sxs-lookup"><span data-stu-id="ffd5e-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="ffd5e-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="ffd5e-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="ffd5e-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="ffd5e-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="ffd5e-116">Liste des extraits de code disponibles</span><span class="sxs-lookup"><span data-stu-id="ffd5e-116">List available snippets</span></span>               | <span data-ttu-id="ffd5e-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="ffd5e-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="ffd5e-118"><kbd>CTRL</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="ffd5e-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="ffd5e-119">Combinaisons de touches personnalisées</span><span class="sxs-lookup"><span data-stu-id="ffd5e-119">Custom Key bindings</span></span>

<span data-ttu-id="ffd5e-120">Vous pouvez [configurer vos propres combinaisons de touches](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) dans VSCode également.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="ffd5e-121">Saisie semi-automatique via la touche Tab</span><span class="sxs-lookup"><span data-stu-id="ffd5e-121">Tab completion</span></span>

<span data-ttu-id="ffd5e-122">Pour activer plus ISE semblable à la touche TAB, ajoutez ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="ffd5e-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="ffd5e-123">Ce paramètre a été ajouté directement à VSCode (et non dans l’extension).</span><span class="sxs-lookup"><span data-stu-id="ffd5e-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="ffd5e-124">Son comportement est déterminé par VSCode directement et ne peut pas être modifié par l’extension.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="ffd5e-125">Sans le focus sur la console lors de l’exécution</span><span class="sxs-lookup"><span data-stu-id="ffd5e-125">No focus on console when executing</span></span>

<span data-ttu-id="ffd5e-126">Pour conserver le focus dans l’éditeur lorsque vous exécutez avec <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="ffd5e-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="ffd5e-127">La valeur par défaut est `true` à des fins d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="ffd5e-128">Ne démarrent pas console intégrée au démarrage</span><span class="sxs-lookup"><span data-stu-id="ffd5e-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="ffd5e-129">Pour arrêter la console intégrée au démarrage, définissez :</span><span class="sxs-lookup"><span data-stu-id="ffd5e-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="ffd5e-130">Le processus PowerShell en arrière-plan démarre toujours dans la mesure où qui fournit IntelliSense, analyse de script, navigation dans les symboles, etc.. Mais la console ne sera pas affichée.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="ffd5e-131">Supposons que les fichiers sont PowerShell par défaut</span><span class="sxs-lookup"><span data-stu-id="ffd5e-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="ffd5e-132">Pour rendre les fichiers de nouveau/sans titre, inscrire en tant que PowerShell par défaut :</span><span class="sxs-lookup"><span data-stu-id="ffd5e-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="ffd5e-133">Modèle de couleurs</span><span class="sxs-lookup"><span data-stu-id="ffd5e-133">Color scheme</span></span>

<span data-ttu-id="ffd5e-134">Il existe un nombre de thèmes de l’ISE pour VSCode rendre l’éditeur ressemble beaucoup plus à l’environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="ffd5e-135">Dans le [Palette de commandes] type `theme` pour obtenir `Preferences: Color Theme` et appuyez sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="ffd5e-136">Dans la liste déroulante, sélectionnez `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="ffd5e-137">Vous pouvez définir ce thème dans les paramètres avec :</span><span class="sxs-lookup"><span data-stu-id="ffd5e-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="ffd5e-138">Explorateur de commande PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffd5e-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="ffd5e-139">Grâce à des travaux de [ @corbob ](https://github.com/corbob), l’extension PowerShell a les débuts de son propre Explorateur de commande.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="ffd5e-140">Dans le [Palette de commandes], entrez `PowerShell Command Explorer` et appuyez sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="ffd5e-141">Ouvrir dans l’environnement ISE</span><span class="sxs-lookup"><span data-stu-id="ffd5e-141">Open in the ISE</span></span>

<span data-ttu-id="ffd5e-142">Si vous vous retrouvez souhaite ouvrir un fichier dans l’environnement ISE en tout cas, vous pouvez utiliser <kbd>MAJ</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="ffd5e-143">Autres ressources</span><span class="sxs-lookup"><span data-stu-id="ffd5e-143">Other resources</span></span>

- <span data-ttu-id="ffd5e-144">4sysops a [un excellent article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sur la configuration de VSCode pour être plus comme l’environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="ffd5e-145">Mike F Robbins a [un billet excellent](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) sur la configuration de VSCode.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="ffd5e-146">Découvrez PowerShell a [une excellente écriture des](https://www.learnpwsh.com/setup-vs-code-for-powershell/) sur l’obtention de VSCode d’installation pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="ffd5e-147">Paramètres supplémentaires</span><span class="sxs-lookup"><span data-stu-id="ffd5e-147">More settings</span></span>

<span data-ttu-id="ffd5e-148">Si vous connaissez d’autres moyens de rendre VSCode environnement plus familier pour les utilisateurs ISE, contribuent à ce document. S’il existe une configuration de compatibilité que vous recherchez, mais vous ne trouvez aucun moyen de l’activer, [de signaler un problème](https://github.com/PowerShell/vscode-powershell/issues/new/choose) et demandez !</span><span class="sxs-lookup"><span data-stu-id="ffd5e-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="ffd5e-149">Nous sommes toujours heureux d’accepter les demandes de tirage et les contributions également !</span><span class="sxs-lookup"><span data-stu-id="ffd5e-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="ffd5e-150">Conseils de VSCode</span><span class="sxs-lookup"><span data-stu-id="ffd5e-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="ffd5e-151">Palette de commandes</span><span class="sxs-lookup"><span data-stu-id="ffd5e-151">Command Palette</span></span>

<span data-ttu-id="ffd5e-152"><kbd>F1</kbd> ou <kbd>Ctrl</kbd>+<kbd>MAJ</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Shift</kbd>+<kbd>P</kbd> sur macOS)</span><span class="sxs-lookup"><span data-stu-id="ffd5e-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="ffd5e-153">Un moyen pratique de l’exécution de commandes dans VSCode.</span><span class="sxs-lookup"><span data-stu-id="ffd5e-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="ffd5e-154">Pour plus d’informations, consultez [les documents VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="ffd5e-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Palette de commandes]: #command-palette
[Command Palette]: #command-palette
