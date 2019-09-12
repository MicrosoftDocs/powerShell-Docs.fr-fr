---
ms.date: 09/06/2019
keywords: powershell,applet de commande
title: Nouveautés de PowerShell 5.0 ISE
ms.openlocfilehash: a719baef0da1600f0a5377e1b72c81b67e37eef2
ms.sourcegitcommit: a74ae7ed089301992fed201fbe55d827a622afa0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70746219"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a><span data-ttu-id="0f52c-103">Nouveauté de Windows PowerShell 5.0 ISE</span><span class="sxs-lookup"><span data-stu-id="0f52c-103">What's New in the Windows PowerShell 5.0 ISE</span></span>

<span data-ttu-id="0f52c-104">Cette rubrique décrit les fonctionnalités nouvelles et mises à jour qui ont été introduites dans les versions de l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f52c-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="0f52c-105">Description de la fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="0f52c-105">Feature description</span></span>

<span data-ttu-id="0f52c-106">Windows PowerShell ISE est une application hôte qui permet d’écrire, d’exécuter et de tester des scripts et des modules dans un environnement graphique et intuitif.</span><span class="sxs-lookup"><span data-stu-id="0f52c-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="0f52c-107">Ses fonctionnalités clés, telles que la coloration de syntaxe, la saisie automatique par tabulation, le débogage visuel, la compatibilité avec Unicode et l’aide contextuelle, fournissent une riche expérience d’écriture de scripts.</span><span class="sxs-lookup"><span data-stu-id="0f52c-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="0f52c-108">Pour plus d'informations, consultez [Présentation de Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span><span class="sxs-lookup"><span data-stu-id="0f52c-108">For more information, see [Introducing the Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span></span>

<span data-ttu-id="0f52c-109">Le tableau suivant répertorie les fonctionnalités nouvelles et modifiées pour cette version de Windows PowerShell ISE dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f52c-109">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

## <a name="intellisense"></a><span data-ttu-id="0f52c-110">Intellisense</span><span class="sxs-lookup"><span data-stu-id="0f52c-110">IntelliSense</span></span>

> <span data-ttu-id="0f52c-111">Ajoutés dans ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="0f52c-111">Added in ISE 3.0</span></span>

<span data-ttu-id="0f52c-112">IntelliSense est une fonctionnalité d’assistance de saisie semi-automatique qui fait partie de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="0f52c-112">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span>
<span data-ttu-id="0f52c-113">Au fur et à mesure de la saisie, IntelliSense affiche des menus interactifs suggérant des applets de commande, des paramètres, des valeurs de paramètre, des fichiers ou des dossiers potentiellement appropriés.</span><span class="sxs-lookup"><span data-stu-id="0f52c-113">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="0f52c-114">**Quels avantages cette modification procure-t-elle ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-114">**What value does this change add?**</span></span>

<span data-ttu-id="0f52c-115">L’ajout d’IntelliSense facilite la découverte d’applets de commande et de syntaxe quand vous utilisez Windows PowerShell ISE pour créer des scripts.</span><span class="sxs-lookup"><span data-stu-id="0f52c-115">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="0f52c-116">Vous pouvez également utiliser Windows PowerShell ISE pour apprendre le fonctionnement de Windows PowerShell quand vous créez des scripts.</span><span class="sxs-lookup"><span data-stu-id="0f52c-116">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="0f52c-117">**En quoi le fonctionnement est-il différent ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-117">**What works differently?**</span></span>

<span data-ttu-id="0f52c-118">Quand vous tapez des applets de commande dans Windows PowerShell ISE, un menu déroulant interactif s’affiche, dans lequel vous pouvez parcourir et sélectionner les commandes appropriées.</span><span class="sxs-lookup"><span data-stu-id="0f52c-118">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

## <a name="snippets"></a><span data-ttu-id="0f52c-119">Extraits de code</span><span class="sxs-lookup"><span data-stu-id="0f52c-119">Snippets</span></span>

> <span data-ttu-id="0f52c-120">Ajoutés dans ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="0f52c-120">Added in ISE 3.0</span></span>

<span data-ttu-id="0f52c-121">Les *extraits de code* sont de courtes sections de code Windows PowerShell que vous pouvez insérer dans les scripts que vous créez dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="0f52c-121">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="0f52c-122">Windows PowerShell ISE est fourni avec un ensemble par défaut d’extraits de code.</span><span class="sxs-lookup"><span data-stu-id="0f52c-122">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="0f52c-123">Vous pouvez ajouter des extraits de code en utilisant l’applet de commande `New-Snippet` tout en travaillant dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="0f52c-123">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="0f52c-124">**Quels avantages cette modification procure-t-elle ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-124">**What value does this change add?**</span></span>

<span data-ttu-id="0f52c-125">Les extraits de code vous permettent d’assembler et de créer rapidement des scripts pour automatiser votre environnement.</span><span class="sxs-lookup"><span data-stu-id="0f52c-125">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="0f52c-126">**En quoi le fonctionnement est-il différent ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-126">**What works differently?**</span></span>

<span data-ttu-id="0f52c-127">Pour utiliser des extraits de code dans Windows PowerShell 3.0 ou version ultérieure, dans le menu **Modifier**, cliquez sur **Démarrer les extraits** ou appuyez sur <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0f52c-127">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

## <a name="add-on-tools"></a><span data-ttu-id="0f52c-128">Outils complémentaires</span><span class="sxs-lookup"><span data-stu-id="0f52c-128">Add-on tools</span></span>

> <span data-ttu-id="0f52c-129">Ajout dans PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="0f52c-129">Added in PowerShell 3.0</span></span>

<span data-ttu-id="0f52c-130">Windows PowerShell ISE prend désormais en charge les outils complémentaires à l’aide du modèle objet.</span><span class="sxs-lookup"><span data-stu-id="0f52c-130">Windows PowerShell ISE now supports add-on tools using the object model.</span></span> <span data-ttu-id="0f52c-131">Ces outils complémentaires sont des contrôles Windows Presentation Foundation (WPF) qui s’affichent sous la forme d’un volet vertical ou horizontal dans la console.</span><span class="sxs-lookup"><span data-stu-id="0f52c-131">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="0f52c-132">Plusieurs outils complémentaires dans un volet sont affichés sous la forme d’un contrôle à onglets.</span><span class="sxs-lookup"><span data-stu-id="0f52c-132">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="0f52c-133">Vous pouvez également ajouter ou supprimer des outils complémentaires produits par des éditeurs non-Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0f52c-133">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="0f52c-134">Pour plus d’informations, consultez [Objectif du modèle objet de script Windows PowerShell ISE](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span><span class="sxs-lookup"><span data-stu-id="0f52c-134">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span></span>

<span data-ttu-id="0f52c-135">**Quels avantages cette modification procure-t-elle ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-135">**What value does this change add?**</span></span>

<span data-ttu-id="0f52c-136">Les modules complémentaires vous permettent d’étendre et de personnaliser Windows PowerShell ISE avec des outils pouvant améliorer votre expérience de création de scripts ou ajouter des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="0f52c-136">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span></span>

<span data-ttu-id="0f52c-137">**En quoi le fonctionnement est-il différent ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-137">**What works differently?**</span></span>

<span data-ttu-id="0f52c-138">Windows PowerShell ISE 3.0 et versions ultérieures sont fournis avec le module complémentaire **Commandes**.</span><span class="sxs-lookup"><span data-stu-id="0f52c-138">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="0f52c-139">Le module complémentaire **Commandes** permet de parcourir les applets de commande et d’accéder à l’aide sur les applets de commande, conjointement avec les volets **Script** et **Console**.</span><span class="sxs-lookup"><span data-stu-id="0f52c-139">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="0f52c-140">D’autres modules complémentaires sont accessibles via la commande **Ouvrir le site web des outils additionnels** du menu **Modules complémentaires**.</span><span class="sxs-lookup"><span data-stu-id="0f52c-140">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

## <a name="restart-manager-and-auto-save"></a><span data-ttu-id="0f52c-141">Gestionnaire de démarrage et enregistrement automatique</span><span class="sxs-lookup"><span data-stu-id="0f52c-141">Restart manager and auto-save</span></span>

> <span data-ttu-id="0f52c-142">Ajout dans PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="0f52c-142">Added in PowerShell 3.0</span></span>

<span data-ttu-id="0f52c-143">Désormais, Windows PowerShell ISE enregistre automatiquement vos scripts ouverts toutes les deux minutes dans un emplacement distinct.</span><span class="sxs-lookup"><span data-stu-id="0f52c-143">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span> <span data-ttu-id="0f52c-144">Lorsque Windows PowerShell ISE redémarre après un incident ou une panne inattendue, il récupère les scripts qui étaient ouverts dans la dernière session, même si les scripts n’ont pas été enregistrés.</span><span class="sxs-lookup"><span data-stu-id="0f52c-144">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span></span>

<span data-ttu-id="0f52c-145">Pour modifier l’intervalle d’enregistrement automatique, exécutez la commande suivante dans le volet de la console : `$psise.Options.AutoSaveMinuteInterval`.</span><span class="sxs-lookup"><span data-stu-id="0f52c-145">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span></span>

<span data-ttu-id="0f52c-146">**Quels avantages cette modification procure-t-elle ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-146">**What value does this change add?**</span></span>

<span data-ttu-id="0f52c-147">Vous pouvez désormais travailler dans Windows PowerShell ISE, en sachant que vos scripts ouverts seront automatiquement enregistrés.</span><span class="sxs-lookup"><span data-stu-id="0f52c-147">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span></span>

<span data-ttu-id="0f52c-148">**En quoi le fonctionnement est-il différent ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-148">**What works differently?**</span></span>

<span data-ttu-id="0f52c-149">Windows PowerShell ISE 2.0 n’enregistre pas automatiquement les scripts.</span><span class="sxs-lookup"><span data-stu-id="0f52c-149">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span></span>

## <a name="most-recently-used-list"></a><span data-ttu-id="0f52c-150">Liste Utilisé(s) récemment</span><span class="sxs-lookup"><span data-stu-id="0f52c-150">Most-recently used list</span></span>

> <span data-ttu-id="0f52c-151">Ajout dans PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="0f52c-151">Added in PowerShell 3.0</span></span>

<span data-ttu-id="0f52c-152">Windows PowerShell ISE offre désormais une liste des derniers fichiers utilisés.</span><span class="sxs-lookup"><span data-stu-id="0f52c-152">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="0f52c-153">Quand vous ouvrez un fichier dans Windows PowerShell ISE, celui-ci est ajouté à cette liste dans le menu **Fichier**.</span><span class="sxs-lookup"><span data-stu-id="0f52c-153">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="0f52c-154">Pour modifier le nombre par défaut de fichiers répertoriés dans la liste des derniers fichiers utilisés, exécutez la commande suivante dans le volet de la console : `$psise.Options.MruCount`.</span><span class="sxs-lookup"><span data-stu-id="0f52c-154">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span></span>

<span data-ttu-id="0f52c-155">**Quels avantages cette modification procure-t-elle ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-155">**What value does this change add?**</span></span>

<span data-ttu-id="0f52c-156">Vous pouvez désormais utiliser la liste des derniers fichiers utilisés pour accéder facilement aux fichiers que vous utilisez fréquemment.</span><span class="sxs-lookup"><span data-stu-id="0f52c-156">You can now use the most-recently used list to easily access your frequently used files.</span></span>

<span data-ttu-id="0f52c-157">**En quoi le fonctionnement est-il différent ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-157">**What works differently?**</span></span>

<span data-ttu-id="0f52c-158">Windows PowerShell ISE 2.0 n’offre pas de liste des derniers fichiers utilisés.</span><span class="sxs-lookup"><span data-stu-id="0f52c-158">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span></span>

## <a name="console-pane"></a><span data-ttu-id="0f52c-159">Volet de la console</span><span class="sxs-lookup"><span data-stu-id="0f52c-159">Console Pane</span></span>

> <span data-ttu-id="0f52c-160">Ajout dans PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="0f52c-160">Added in PowerShell 3.0</span></span>

<span data-ttu-id="0f52c-161">Les volets de commande et de sortie distincts qui étaient disponibles dans la première version de Windows PowerShell ISE ont été combinés en un volet de console unique.</span><span class="sxs-lookup"><span data-stu-id="0f52c-161">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="0f52c-162">Le volet de la console est similaire dans sa fonction et son apparence à une console Windows PowerShell standard, mais il inclut les améliorations ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="0f52c-162">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span></span>

- <span data-ttu-id="0f52c-163">Coloration de la syntaxe pour le texte d’entrée (pas le texte de sortie), incluant la syntaxe XML</span><span class="sxs-lookup"><span data-stu-id="0f52c-163">Syntax coloring for input text (not output text), including XML syntax</span></span>
- <span data-ttu-id="0f52c-164">Intellisense</span><span class="sxs-lookup"><span data-stu-id="0f52c-164">IntelliSense</span></span>
- <span data-ttu-id="0f52c-165">Accolades correspondantes</span><span class="sxs-lookup"><span data-stu-id="0f52c-165">Brace matching</span></span>
- <span data-ttu-id="0f52c-166">Indication des erreurs</span><span class="sxs-lookup"><span data-stu-id="0f52c-166">Error indication</span></span>
- <span data-ttu-id="0f52c-167">Prise en charge complète d’Unicode</span><span class="sxs-lookup"><span data-stu-id="0f52c-167">Full Unicode support</span></span>
- <span data-ttu-id="0f52c-168">Aide contextuelle accessible via la touche <kbd>F1</kbd></span><span class="sxs-lookup"><span data-stu-id="0f52c-168"><kbd>F1</kbd> context-sensitive help</span></span>
- <span data-ttu-id="0f52c-169">Fonctionnalité Show-Command contextuelle accessible via <kbd>Ctrl</kbd>+<kbd>F1</kbd></span><span class="sxs-lookup"><span data-stu-id="0f52c-169"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span></span>
- <span data-ttu-id="0f52c-170">Scripts complexes et prise en charge de la saisie de droite à gauche</span><span class="sxs-lookup"><span data-stu-id="0f52c-170">Complex script and right-to-left support</span></span>
- <span data-ttu-id="0f52c-171">Prise en charge des polices</span><span class="sxs-lookup"><span data-stu-id="0f52c-171">Font support</span></span>
- <span data-ttu-id="0f52c-172">Zoom</span><span class="sxs-lookup"><span data-stu-id="0f52c-172">Zoom</span></span>
- <span data-ttu-id="0f52c-173">Modes de sélection de ligne et de sélection de bloc</span><span class="sxs-lookup"><span data-stu-id="0f52c-173">Line-select and block-select modes</span></span>
- <span data-ttu-id="0f52c-174">Préservation du contenu saisi dans la ligne de commande lorsque vous appuyez sur la touche <kbd>Haut</kbd> pour afficher l’historique dans la console</span><span class="sxs-lookup"><span data-stu-id="0f52c-174">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span></span>

<span data-ttu-id="0f52c-175">**Quels avantages cette modification procure-t-elle ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-175">**What value does this change add?**</span></span>

<span data-ttu-id="0f52c-176">L’apport de ces modifications au volet de la console offre une expérience de création de scripts plus cohérente avec l’interface de la console.</span><span class="sxs-lookup"><span data-stu-id="0f52c-176">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="0f52c-177">**En quoi le fonctionnement est-il différent ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-177">**What works differently?**</span></span>

<span data-ttu-id="0f52c-178">Windows PowerShell ISE 2.0 offre des volets de commande et de sortie distincts.</span><span class="sxs-lookup"><span data-stu-id="0f52c-178">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

## <a name="command-line-switches"></a><span data-ttu-id="0f52c-179">Commutateurs de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="0f52c-179">Command-line switches</span></span>

> <span data-ttu-id="0f52c-180">Ajout dans PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="0f52c-180">Added in PowerShell 3.0</span></span>

<span data-ttu-id="0f52c-181">Si vous démarrez Windows PowerShell ISE à partir de la ligne de commande (en tapant **Powershell_ise.exe**), vous pouvez ajouter les nouveaux commutateurs de ligne de commande suivants.</span><span class="sxs-lookup"><span data-stu-id="0f52c-181">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="0f52c-182">`-NoProfile` : démarre Windows PowerShell ISE sans exécuter `$profile`</span><span class="sxs-lookup"><span data-stu-id="0f52c-182">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span></span>
- <span data-ttu-id="0f52c-183">`-Help` : affiche une fenêtre d’aide</span><span class="sxs-lookup"><span data-stu-id="0f52c-183">`-Help`: Displays a Help window</span></span>
- <span data-ttu-id="0f52c-184">`-mta` : démarre Windows PowerShell ISE en mode multithread cloisonné.</span><span class="sxs-lookup"><span data-stu-id="0f52c-184">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="0f52c-185">Le mode d’opération par défaut pour Windows PowerShell ISE est un mode à thread unique cloisonné, ou `-sta`.</span><span class="sxs-lookup"><span data-stu-id="0f52c-185">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span></span>

<span data-ttu-id="0f52c-186">**Quels avantages cette modification procure-t-elle ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-186">**What value does this change add?**</span></span>

<span data-ttu-id="0f52c-187">L’ajout de ces commutateurs de ligne de commande permet de contrôler l’environnement dans lequel Windows PowerShell ISE s’exécute.</span><span class="sxs-lookup"><span data-stu-id="0f52c-187">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="0f52c-188">**En quoi le fonctionnement est-il différent ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-188">**What works differently?**</span></span>

<span data-ttu-id="0f52c-189">Windows PowerShell ISE 2.0 ne reconnaît pas ces commutateurs de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="0f52c-189">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span></span>

## <a name="new-editor-features"></a><span data-ttu-id="0f52c-190">Nouvelles fonctionnalités de l’éditeur</span><span class="sxs-lookup"><span data-stu-id="0f52c-190">New editor features</span></span>

> <span data-ttu-id="0f52c-191">Ajout dans PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="0f52c-191">Added in PowerShell 3.0</span></span>

<span data-ttu-id="0f52c-192">Les autres fonctionnalités d’édition de Windows PowerShell ISE sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0f52c-192">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="0f52c-193">**Coloration de la syntaxe XML** : Windows PowerShell ISE colore désormais la syntaxe XML de la même façon que la syntaxe Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f52c-193">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>
- <span data-ttu-id="0f52c-194">**Correspondance d’accolade** : Windows PowerShell ISE inclut des fonctions de correspondance et de mise en surbrillance des accolades, utilisables comme suit : par exemple, la commande **Accéder à Match** ou la combinaison de touches <kbd>Ctrl</kbd>+<kbd>]</kbd> permettent de localiser l’accolade fermante, si une accolade ouvrante est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="0f52c-194">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span></span>
- <span data-ttu-id="0f52c-195">**Mode Plan** Le volet Script prend en charge le mode Plan qui permet de réduire ou de développer des sections de code en cliquant sur les signes plus ou moins dans la marge gauche.</span><span class="sxs-lookup"><span data-stu-id="0f52c-195">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="0f52c-196">Vous pouvez utiliser des accolades ou les balises `#region` et `#endregion` pour marquer le début ou la fin d’une section réductible.</span><span class="sxs-lookup"><span data-stu-id="0f52c-196">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="0f52c-197">Pour développer ou réduire toutes les régions, appuyez sur <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0f52c-197">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span></span>
- <span data-ttu-id="0f52c-198">**Édition du texte par glisser-déplacer** - Désormais, Windows PowerShell ISE prend en charge l’édition de texte par glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="0f52c-198">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="0f52c-199">Vous pouvez sélectionner un bloc de texte et faire glisser ce texte vers un autre emplacement dans l’éditeur ou la console afin de le déplacer.</span><span class="sxs-lookup"><span data-stu-id="0f52c-199">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="0f52c-200">Si vous maintenez la touche <kbd>Ctrl</kbd> enfoncée pendant que vous faites glisser le texte sélectionné, lorsque vous relâchez le bouton de la souris, le texte est copié dans le nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="0f52c-200">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="0f52c-201">Dans cette version de Windows PowerShell ISE, quand vous glissez-déplacez un fichier vers Windows PowerShell ISE, ce dernier ouvre le fichier.</span><span class="sxs-lookup"><span data-stu-id="0f52c-201">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>
- <span data-ttu-id="0f52c-202">**Affichage des erreurs d’analyse** - Les erreurs d’analyse sont indiquées par des soulignements rouges.</span><span class="sxs-lookup"><span data-stu-id="0f52c-202">**Parse error display** - Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="0f52c-203">Lorsque vous pointez sur une erreur indiquée, le texte d’info-bulle affiche le problème détecté dans le code.</span><span class="sxs-lookup"><span data-stu-id="0f52c-203">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>
- <span data-ttu-id="0f52c-204">**Zoom** - Le pourcentage de zoom du contenu de la console peut être défini à l’aide du curseur de zoom (dans le coin inférieur droit de la fenêtre Windows PowerShell ISE) ou en tapant la commande `$psise.options.Zoom`dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="0f52c-204">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span></span>
- <span data-ttu-id="0f52c-205">**Copie et collage de texte enrichi** - La copie dans le Presse-papiers dans Windows PowerShell ISE préserve les informations de police, de taille et de couleur de la sélection d’origine.</span><span class="sxs-lookup"><span data-stu-id="0f52c-205">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>
- <span data-ttu-id="0f52c-206">**Sélection de bloc** - Vous pouvez sélectionner un bloc de texte en maintenant la touche <kbd>Alt</kbd> enfoncée tout en sélectionnant du texte dans le volet Script à l’aide de la souris, ou en appuyant sur <kbd>Alt</kbd>+<kbd>Maj</kbd>+<kbd>Flèche</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0f52c-206">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span></span>

<span data-ttu-id="0f52c-207">**Quels avantages cette modification procure-t-elle ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-207">**What value does this change add?**</span></span>

<span data-ttu-id="0f52c-208">Les fonctionnalités d’édition supplémentaires renforcent la cohérence et la puissance de l’environnement d’édition.</span><span class="sxs-lookup"><span data-stu-id="0f52c-208">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="0f52c-209">**En quoi le fonctionnement est-il différent ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-209">**What works differently?**</span></span>

<span data-ttu-id="0f52c-210">Ces améliorations des fonctionnalités d’édition ne figuraient pas dans Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="0f52c-210">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span></span>

## <a name="new-help-viewer-window"></a><span data-ttu-id="0f52c-211">Nouvelle fenêtre de visionneuse d’aide</span><span class="sxs-lookup"><span data-stu-id="0f52c-211">New Help viewer window</span></span>

> <span data-ttu-id="0f52c-212">Ajout dans PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="0f52c-212">Added in PowerShell 3.0</span></span>

<span data-ttu-id="0f52c-213">Si vous appuyez sur <kbd>F1</kbd> quand le curseur est dans une applet de commande ou si une partie d’une applet de commande est en surbrillance, la nouvelle visionneuse d’aide ouvre une aide contextuelle sur l’applet de commande en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="0f52c-213">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="0f52c-214">Pour afficher les rubriques d’aide **conceptuelle** de Windows PowerShell, tapez `operators` dans le volet de la console, puis appuyez sur <kbd>F1</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0f52c-214">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span></span>

<span data-ttu-id="0f52c-215">Avant d’utiliser cette fonctionnalité, téléchargez la dernière version des rubriques d’aide de Windows PowerShell à partir du site web de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0f52c-215">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="0f52c-216">La méthode la plus simple pour télécharger les rubriques d’aide consiste à exécuter l’applet de commande `Update-Help` dans le volet de la console durant l’exécution de Windows PowerShell ISE en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="0f52c-216">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="0f52c-217">Vous pouvez modifier l’emplacement dans lequel la touche <kbd>F1</kbd> recherche de l’aide.</span><span class="sxs-lookup"><span data-stu-id="0f52c-217">You can alter where the <kbd>F1</kbd> key looks for Help.</span></span> <span data-ttu-id="0f52c-218">Dans le menu **Outils**/**Options**, sous l’onglet **Paramètres généraux**, sous **Autres paramètres**, vous pouvez cocher ou décocher la case **Utiliser le contenu de l’aide locale au lieu du contenu en ligne**.</span><span class="sxs-lookup"><span data-stu-id="0f52c-218">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="0f52c-219">Si la case à cocher est activée, le client recherche de l’aide sur l’applet de commande dans l’aide téléchargée figurant dans le dossier modules.</span><span class="sxs-lookup"><span data-stu-id="0f52c-219">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span> <span data-ttu-id="0f52c-220">Si la case à cocher est désactivée, le client recherche de l’aide en ligne.</span><span class="sxs-lookup"><span data-stu-id="0f52c-220">If the checkbox is cleared, the client looks for help online.</span></span>

<span data-ttu-id="0f52c-221">**Quels avantages cette modification procure-t-elle ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-221">**What value does this change add?**</span></span>

<span data-ttu-id="0f52c-222">L’aide contextuelle accessible sans quitter votre applet de commande ou script actifs vous permet de bénéficier d’une expérience d’apprentissage intégrée.</span><span class="sxs-lookup"><span data-stu-id="0f52c-222">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span></span>

<span data-ttu-id="0f52c-223">**En quoi le fonctionnement est-il différent ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-223">**What works differently?**</span></span>

<span data-ttu-id="0f52c-224">Dans les versions précédentes de Windows PowerShell ISE, l’appui sur la touche <kbd>F1</kbd> ouvrait le fichier d’aide sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="0f52c-224">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="0f52c-225">Dans Windows PowerShell ISE 3.0 et versions ultérieures, une fenêtre s’ouvre, affichant l’aide sur l’applet de commande, qui est consultable et configurable.</span><span class="sxs-lookup"><span data-stu-id="0f52c-225">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="0f52c-226">Cette expérience d’aide est une nouveauté pour Windows PowerShell ISE 3.0, et l’aide actualisable est une nouveauté pour Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="0f52c-226">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

## <a name="show-command-cmdlet"></a><span data-ttu-id="0f52c-227">Applet de commande Show-Command</span><span class="sxs-lookup"><span data-stu-id="0f52c-227">Show-Command cmdlet</span></span>

> <span data-ttu-id="0f52c-228">Ajout dans PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="0f52c-228">Added in PowerShell 3.0</span></span>

<span data-ttu-id="0f52c-229">L’applet de commande `Show-Command` permet de composer ou d’exécuter une applet de commande ou une fonction en remplissant un formulaire graphique.</span><span class="sxs-lookup"><span data-stu-id="0f52c-229">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="0f52c-230">Le formulaire permet aux utilisateurs d’utiliser Windows PowerShell dans un environnement graphique.</span><span class="sxs-lookup"><span data-stu-id="0f52c-230">The form lets users work with Windows PowerShell in a graphical environment.</span></span>
<span data-ttu-id="0f52c-231">`Show-Command` permet également aux créateurs de scripts chevronnés de créer une interface utilisateur graphique rapide basée sur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f52c-231">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="0f52c-232">**Quels avantages cette modification procure-t-elle ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-232">**What value does this change add?**</span></span>

<span data-ttu-id="0f52c-233">En utilisant `Show-Command` dans vos scripts Windows PowerShell, vous pouvez fournir à vos utilisateurs un environnement graphique familier.</span><span class="sxs-lookup"><span data-stu-id="0f52c-233">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span></span> <span data-ttu-id="0f52c-234">`Show-Command` peut également faciliter l’apprentissage de Windows PowerShell pour des utilisateurs débutants.</span><span class="sxs-lookup"><span data-stu-id="0f52c-234">`Show-Command` can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="0f52c-235">**En quoi le fonctionnement est-il différent ?**</span><span class="sxs-lookup"><span data-stu-id="0f52c-235">**What works differently?**</span></span>

<span data-ttu-id="0f52c-236">`Show-Command` est nouveau dans Windows PowerShell ISE 3.0.</span><span class="sxs-lookup"><span data-stu-id="0f52c-236">`Show-Command` is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f52c-237">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f52c-237">See also</span></span>

<span data-ttu-id="0f52c-238">Pour plus d’informations sur l’utilisation de Windows PowerShell ISE, consultez [Explorer l’environnement d’écriture de scripts intégré de Windows PowerShell](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).</span><span class="sxs-lookup"><span data-stu-id="0f52c-238">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).</span></span>
