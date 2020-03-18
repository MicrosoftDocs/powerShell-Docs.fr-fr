---
ms.date: 01/02/2020
keywords: powershell,applet de commande
title: Comment écrire et exécuter des scripts dans Windows PowerShell ISE
ms.openlocfilehash: 2e3122a3b436ba878d2c5f9d72d4f9e024d4d031
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402526"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="fa1d8-103">Comment écrire et exécuter des scripts dans Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="fa1d8-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="fa1d8-104">Cet article décrit comment créer, modifier, exécuter et enregistrer des scripts dans le volet Script.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-104">This article describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="fa1d8-105">Comment créer et exécuter des scripts</span><span class="sxs-lookup"><span data-stu-id="fa1d8-105">How to create and run scripts</span></span>

<span data-ttu-id="fa1d8-106">Vous pouvez ouvrir et modifier des fichiers Windows PowerShell dans le volet Script.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="fa1d8-107">Les types de fichiers spécifiques intéressants dans Windows PowerShell sont les fichiers de script (`.ps1`), les fichiers de données de script (`.psd1`) et les fichiers de module de script (`.psm1`).</span><span class="sxs-lookup"><span data-stu-id="fa1d8-107">Specific file types of interest in Windows PowerShell are script files (`.ps1`), script data files (`.psd1`), and script module files (`.psm1`).</span></span> <span data-ttu-id="fa1d8-108">Ces types de fichiers font l’objet d’une coloration de la syntaxe dans l’éditeur du volet Script.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="fa1d8-109">D’autres types de fichiers courants que vous pouvez ouvrir dans le volet Script sont les fichiers config (`.ps1xml`), les fichiers XML et les fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-109">Other common file types you may open in the Script Pane are configuration files (`.ps1xml`), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="fa1d8-110">La stratégie d’exécution de Windows PowerShell détermine si vous pouvez exécuter des scripts et charger des fichiers de configuration et des profils Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="fa1d8-111">La stratégie d’exécution par défaut, restreinte, empêche l’exécution de tous les scripts et le chargement de profils.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="fa1d8-112">Pour savoir comment modifier la stratégie d’exécution afin d’autoriser le chargement et l’utilisation de profils, consultez [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) et [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span><span class="sxs-lookup"><span data-stu-id="fa1d8-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) and [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="fa1d8-113">Pour créer un fichier de script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-113">To create a new script file</span></span>

<span data-ttu-id="fa1d8-114">Dans la barre d’outils, cliquez sur **Nouveau** ou, dans le menu **Fichier**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-114">On the toolbar, click **New**, or on the **File** menu, click **New**.</span></span> <span data-ttu-id="fa1d8-115">Le fichier créé s’affiche dans un nouvel onglet de fichier sous l’onglet PowerShell actif. N’oubliez pas que les onglets PowerShell sont visibles uniquement quand il y en a plusieurs.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="fa1d8-116">Par défaut, un fichier de script type (`.ps1`) est créé, mais il peut être enregistré avec un nouveau nom et une nouvelle extension.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-116">By default a file of type script (`.ps1`) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="fa1d8-117">Plusieurs fichiers de script peuvent être créés sous le même onglet PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="fa1d8-118">Pour ouvrir un script existant</span><span class="sxs-lookup"><span data-stu-id="fa1d8-118">To open an existing script</span></span>

<span data-ttu-id="fa1d8-119">Dans la barre d’outils, cliquez sur **Ouvrir** ou, dans le menu **Fichier**, cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="fa1d8-120">Dans la boîte de dialogue **Ouvrir**, sélectionnez le fichier à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="fa1d8-121">Le fichier ouvert s’affiche dans un nouvel onglet.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="fa1d8-122">Pour fermer un onglet de script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-122">To close a script tab</span></span>

<span data-ttu-id="fa1d8-123">Cliquez sur l’icône **Fermer** (**X**) de l’onglet de fichier que vous voulez fermer ou sélectionnez le menu **Fichier** et cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-123">Click the **Close** icon (**X**) of the file tab you want to close or select the **File** menu and click **Close**.</span></span>

<span data-ttu-id="fa1d8-124">Si le fichier a été modifié depuis son dernier enregistrement, vous êtes invité à l’enregistrer ou à l’ignorer.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-124">If the file has been altered since it was last saved, you're prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="fa1d8-125">Pour afficher le chemin d’accès du fichier</span><span class="sxs-lookup"><span data-stu-id="fa1d8-125">To display the file path</span></span>

<span data-ttu-id="fa1d8-126">Sous l’onglet Fichier, pointez sur le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-126">On the file tab, point to the file name.</span></span> <span data-ttu-id="fa1d8-127">Le chemin d’accès complet au fichier de script s’affiche dans une info-bulle.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-127">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="fa1d8-128">Pour exécuter un script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-128">To run a script</span></span>

<span data-ttu-id="fa1d8-129">Dans la barre d’outils, cliquez sur **Exécuter le Script** ou, dans le menu **Fichier**, cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-129">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="fa1d8-130">Pour exécuter une partie d’un script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-130">To run a portion of a script</span></span>

1. <span data-ttu-id="fa1d8-131">Dans le volet Script, sélectionnez une partie d’un script.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-131">In the Script Pane, select a portion of a script.</span></span>
2. <span data-ttu-id="fa1d8-132">Dans le menu **Fichier**, cliquez sur **Exécuter la sélection** ou, dans la barre d’outils, cliquez sur **Exécuter la sélection**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-132">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="fa1d8-133">Pour arrêter un script en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="fa1d8-133">To stop a running script</span></span>

<span data-ttu-id="fa1d8-134">Il existe plusieurs façons de suspendre un script en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-134">There are several ways to stop a running script.</span></span>

- <span data-ttu-id="fa1d8-135">Cliquez sur **Arrêter l’opération** sur la barre d’outils</span><span class="sxs-lookup"><span data-stu-id="fa1d8-135">Click **Stop Operation** on the toolbar</span></span>
- <span data-ttu-id="fa1d8-136">Appuyez sur <kbd>CTRL</kbd>+<kbd>ARRÊT</kbd></span><span class="sxs-lookup"><span data-stu-id="fa1d8-136">Press <kbd>CTRL</kbd>+<kbd>BREAK</kbd></span></span>
- <span data-ttu-id="fa1d8-137">Sélectionnez le menu **Fichier** et cliquez sur **Arrêter l’opération**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-137">Select the **File** menu and click **Stop Operation**.</span></span>

<span data-ttu-id="fa1d8-138">Vous pouvez également appuyer sur <kbd>CTRL</kbd>+<kbd>C</kbd>, sauf si du texte est sélectionné, auquel cas <kbd>CTRL</kbd>+<kbd>C</kbd> mappe à la fonction de copie pour le texte sélectionné.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-138">Pressing <kbd>CTRL</kbd>+<kbd>C</kbd> also works unless some text is currently selected, in which case <kbd>CTRL</kbd>+<kbd>C</kbd> maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="fa1d8-139">Comment écrire et modifier du texte dans le volet Script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-139">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="fa1d8-140">Vous pouvez copier, couper, coller, rechercher et remplacer du texte dans le volet Script.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-140">You can copy, cut, paste, find, and replace text in the Script Pane.</span></span> <span data-ttu-id="fa1d8-141">Vous pouvez également annuler et rétablir la dernière action exécutée.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="fa1d8-142">Les raccourcis clavier pour ces actions sont les mêmes que ceux utilisés pour toutes les applications Windows.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-142">The keyboard shortcuts for these actions are the same shortcuts used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="fa1d8-143">Pour entrer du texte dans le volet Script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="fa1d8-144">Déplacez le curseur vers le volet Script en cliquant n’importe où dans celui-ci, ou en cliquant sur **Atteindre le volet Script** dans le menu **Affichage**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>
2. <span data-ttu-id="fa1d8-145">Créez un script.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-145">Create a script.</span></span> <span data-ttu-id="fa1d8-146">La coloration de la syntaxe et la saisie semi-automatique par le biais de la touche Tab enrichissent cette expérience dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-146">Syntax coloring and tab completion provide a richer editing experience in Windows PowerShell ISE.</span></span>
3. <span data-ttu-id="fa1d8-147">Pour plus d’informations sur l’utilisation de la fonctionnalité de saisie semi-automatique via la touche Tab pour faciliter la frappe, voir [Comment utiliser la saisie semi-automatique via la touche Tab dans le volet Script et le volet Console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).</span><span class="sxs-lookup"><span data-stu-id="fa1d8-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="fa1d8-148">Pour rechercher du texte dans le volet Script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="fa1d8-149">Pour rechercher du texte n’importe où, appuyez sur <kbd>CTRL</kbd>+<kbd>F</kbd> ou, dans le menu **Modifier**, cliquez sur **Rechercher dans le script**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-149">To find text anywhere, press <kbd>CTRL</kbd>+<kbd>F</kbd> or, on the **Edit** menu, click **Find in Script**.</span></span>
2. <span data-ttu-id="fa1d8-150">Pour rechercher du texte situé après le curseur, appuyez sur <kbd>F3</kbd> ou, dans le menu **Modifier**, cliquez sur **Rechercher suivant dans le script**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-150">To find text after the cursor, press <kbd>F3</kbd> or, on the **Edit** menu, click **Find Next in Script**.</span></span>
3. <span data-ttu-id="fa1d8-151">Pour rechercher du texte devant le curseur, appuyez sur <kbd>MAJ</kbd>+<kbd>F3</kbd> ou, dans le menu **Modifier**, cliquez sur **Rechercher précédent dans le script**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-151">To find text before the cursor, press <kbd>SHIFT</kbd>+<kbd>F3</kbd> or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="fa1d8-152">Pour rechercher et remplacer du texte dans le volet Script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="fa1d8-153">Appuyez sur <kbd>CTRL</kbd>+<kbd>H</kbd> ou, dans le menu **Modifier**, cliquez sur **Remplacer dans le script**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-153">Press <kbd>CTRL</kbd>+<kbd>H</kbd> or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="fa1d8-154">Entrez le texte que vous souhaitez rechercher et le texte de remplacement, puis appuyez sur <kbd>ENTRÉE</kbd>.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-154">Enter the text you want to find and the replacement text, then press <kbd>ENTER</kbd>.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="fa1d8-155">Pour accéder à une ligne particulière du texte dans le volet Script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="fa1d8-156">Dans le volet Script, appuyez sur <kbd>CTRL</kbd>+<kbd>G</kbd> ou, dans le menu **Modifier**, cliquez sur **Atteindre la ligne**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-156">In the Script Pane, press <kbd>CTRL</kbd>+<kbd>G</kbd> or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="fa1d8-157">Entrez un numéro de ligne.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="fa1d8-158">Pour copier du texte dans le volet Script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="fa1d8-159">Dans le volet Script, sélectionnez le texte à copier.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="fa1d8-160">Appuyez sur <kbd>CTRL</kbd>+<kbd>C</kbd> ou, dans la barre d’outils, cliquez sur l’icône **Copier** ou encore, dans le menu **Modifier**, cliquez sur **Copier**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-160">Press <kbd>CTRL</kbd>+<kbd>C</kbd> or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="fa1d8-161">Pour couper du texte dans le volet Script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="fa1d8-162">Dans le volet Script, sélectionnez le texte à couper.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-162">In the Script Pane, select the text that you want to cut.</span></span>
2. <span data-ttu-id="fa1d8-163">Appuyez sur <kbd>CTRL</kbd>+<kbd>X</kbd> ou, dans la barre d’outils, cliquez sur l’icône **Couper** ou encore, dans le menu **Modifier**, cliquez sur **Couper**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-163">Press <kbd>CTRL</kbd>+<kbd>X</kbd> or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="fa1d8-164">Pour coller du texte dans le volet Script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="fa1d8-165">Appuyez sur <kbd>CTRL</kbd>+<kbd>V</kbd> ou, dans la barre d’outils, cliquez sur l’icône **Coller** ou encore, dans le menu **Modifier**, cliquez sur **Coller**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-165">Press <kbd>CTRL</kbd>+<kbd>V</kbd> or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="fa1d8-166">Pour annuler une action dans le volet Script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="fa1d8-167">Appuyez sur <kbd>CTRL</kbd>+<kbd>Z</kbd> ou, dans la barre d’outils, cliquez sur l’icône **Annuler** ou encore, dans le menu **Modifier**, cliquez sur **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-167">Press <kbd>CTRL</kbd>+<kbd>Z</kbd> or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="fa1d8-168">Pour rétablir une action dans le volet Script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="fa1d8-169">Appuyez sur <kbd>CTRL</kbd>+<kbd>Y</kbd> ou, dans la barre d’outils, cliquez sur l’icône **Phase de restauration par progression** ou encore, dans le menu **Modifier**, cliquez sur **Phase de restauration par progression**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-169">Press <kbd>CTRL</kbd>+<kbd>Y</kbd> or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="fa1d8-170">Comment enregistrer un script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-170">How to save a script</span></span>

<span data-ttu-id="fa1d8-171">Un astérisque apparaît en regard du nom de script pour marquer un fichier qui n’a pas été enregistré depuis sa modification.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-171">An asterisk appears next to the script name to mark a file that hasn't been saved since it was changed.</span></span> <span data-ttu-id="fa1d8-172">L’astérisque disparaît lors de l’enregistrement du fichier.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-172">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="fa1d8-173">Pour enregistrer un script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-173">To save a script</span></span>

<span data-ttu-id="fa1d8-174">Appuyez sur <kbd>CTRL</kbd>+<kbd>S</kbd> ou, dans la barre d’outils, cliquez sur l’icône **Enregistrer** ou encore, dans le menu **Fichier**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-174">Press <kbd>CTRL</kbd>+<kbd>S</kbd> or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="fa1d8-175">Pour enregistrer et nommer un script</span><span class="sxs-lookup"><span data-stu-id="fa1d8-175">To save and name a script</span></span>

1. <span data-ttu-id="fa1d8-176">Dans le menu **Fichier**, cliquez sur **Enregistrer sous**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-176">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="fa1d8-177">La boîte de dialogue **Enregistrer sous** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-177">The **Save As** dialog box will appear.</span></span>
2. <span data-ttu-id="fa1d8-178">Dans le champ **Nom de fichier**, entrez un nom pour le fichier.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-178">In the **File name** box, enter a name for the file.</span></span>
3. <span data-ttu-id="fa1d8-179">Dans le champ **Type de fichier**, sélectionnez un type de fichier.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-179">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="fa1d8-180">Par exemple, dans le champ **Type de fichier**, sélectionnez « Scripts PowerShell (`*.ps1`) ».</span><span class="sxs-lookup"><span data-stu-id="fa1d8-180">For example, in the **Save as type** box, select 'PowerShell Scripts (`*.ps1`)'.</span></span>
4. <span data-ttu-id="fa1d8-181">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-181">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="fa1d8-182">Pour enregistrer un script en encodage ASCII</span><span class="sxs-lookup"><span data-stu-id="fa1d8-182">To save a script in ASCII encoding</span></span>

<span data-ttu-id="fa1d8-183">Par défaut, Windows PowerShell ISE enregistre les nouveaux fichiers de script (`.ps1`), les fichiers de données de script (`.psd1`) et les fichiers de module de script (`.psm1`) au format Unicode (BigEndianUnicode).</span><span class="sxs-lookup"><span data-stu-id="fa1d8-183">By default, Windows PowerShell ISE saves new script files (`.ps1`), script data files (`.psd1`), and script module files (`.psm1`) as Unicode (BigEndianUnicode) by default.</span></span> <span data-ttu-id="fa1d8-184">Pour enregistrer un script dans un autre encodage, tel ASCII (ANSI), utilisez les méthodes **Save** ou **SaveAs** sur l’objet [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="fa1d8-184">To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.</span></span>

<span data-ttu-id="fa1d8-185">La commande suivante enregistre un nouveau script sous MyScript.ps1 avec un encodage ASCII.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-185">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="fa1d8-186">La commande suivante remplace le fichier de script actuel par un fichier du même nom, mais avec un encodage ASCII.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-186">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="fa1d8-187">La commande suivante obtient l’encodage du fichier actuel.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-187">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="fa1d8-188">Windows PowerShell ISE prend en charge les options d’encodage suivantes : ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 et Default.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-188">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8, and Default.</span></span> <span data-ttu-id="fa1d8-189">La valeur de l’option Default varie selon le système.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-189">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="fa1d8-190">Windows PowerShell ISE ne change pas l’encodage des fichiers de script lorsque vous utilisez les commandes Enregistrer ou Enregistrer sous.</span><span class="sxs-lookup"><span data-stu-id="fa1d8-190">Windows PowerShell ISE doesn't change the encoding of script files when you use the Save or Save As commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa1d8-191">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa1d8-191">See Also</span></span>

- [<span data-ttu-id="fa1d8-192">Exploration de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="fa1d8-192">Exploring the Windows PowerShell ISE</span></span>](exploring-the-windows-powershell-ise.md)
