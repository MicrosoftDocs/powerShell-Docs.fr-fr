---
ms.date: 12/31/2019
title: Objet ISEEditor
description: Un objet ISEEditor est une instance de la classe Microsoft.PowerShell.Host.ISE.ISEEditor. Le volet de la console est un objet ISEEditor.
ms.openlocfilehash: ffcb6e35e1160beab6efb29cc84847fa9ffd012b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654057"
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="bfd52-104">Objet ISEEditor</span><span class="sxs-lookup"><span data-stu-id="bfd52-104">The ISEEditor Object</span></span>

<span data-ttu-id="bfd52-105">Un objet **ISEEditor** est une instance de la classe Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="bfd52-105">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="bfd52-106">Le volet de la console est un objet **ISEEditor** .</span><span class="sxs-lookup"><span data-stu-id="bfd52-106">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="bfd52-107">Chaque objet [ISEFile](The-ISEFile-Object.md) est associé à un objet **ISEEditor** .</span><span class="sxs-lookup"><span data-stu-id="bfd52-107">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="bfd52-108">Les sections suivantes répertorient les méthodes et propriétés d’un objet **ISEEditor** .</span><span class="sxs-lookup"><span data-stu-id="bfd52-108">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="bfd52-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bfd52-109">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="bfd52-110">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="bfd52-110">Clear\(\)</span></span>

<span data-ttu-id="bfd52-111">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bfd52-112">Efface le texte affiché dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="bfd52-112">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="bfd52-113">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="bfd52-113">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="bfd52-114">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bfd52-115">Fait défiler l’éditeur pour afficher la ligne qui correspond à la valeur du paramètre **lineNumber** spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bfd52-115">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="bfd52-116">Elle lève une exception si le numéro de ligne spécifié est en dehors de la plage 1-dernier numéro de ligne, qui définit les numéros de ligne valides.</span><span class="sxs-lookup"><span data-stu-id="bfd52-116">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="bfd52-117">**lineNumber** Numéro de la ligne à afficher.</span><span class="sxs-lookup"><span data-stu-id="bfd52-117">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="bfd52-118">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="bfd52-118">Focus\(\)</span></span>

<span data-ttu-id="bfd52-119">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-119">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bfd52-120">Définit le focus sur l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="bfd52-120">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="bfd52-121">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="bfd52-121">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="bfd52-122">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bfd52-123">Obtient la longueur, sous forme d’entier, de la ligne spécifiée par le numéro de ligne.</span><span class="sxs-lookup"><span data-stu-id="bfd52-123">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="bfd52-124">**lineNumber** Numéro de la ligne dont la longueur doit être obtenue.</span><span class="sxs-lookup"><span data-stu-id="bfd52-124">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="bfd52-125">**Returns** Longueur de la ligne correspondant au numéro de ligne spécifié.</span><span class="sxs-lookup"><span data-stu-id="bfd52-125">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="bfd52-126">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="bfd52-126">GoToMatch\(\)</span></span>

<span data-ttu-id="bfd52-127">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-127">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="bfd52-128">Déplace le point d’insertion vers le caractère correspondant si la propriété **CanGoToMatch** de l’objet d’éditeur a la valeur `$true`. Ceci se produit quand le point d’insertion se situe juste avant une parenthèse ouvrante, un crochet ouvrant ou une accolade ouvrante `(`,`[`,`{` - ou juste après une parenthèse fermante, un crochet fermant ou une accolade fermante -`)`,`]`,`}`.</span><span class="sxs-lookup"><span data-stu-id="bfd52-128">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is `$true`, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - `(`,`[`,`{` - or immediately after a closing parenthesis, bracket, or brace - `)`,`]`,`}`.</span></span> <span data-ttu-id="bfd52-129">Le point d’insertion se trouve avant un caractère ouvrant ou après un caractère fermant.</span><span class="sxs-lookup"><span data-stu-id="bfd52-129">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="bfd52-130">Si la propriété **CanGoToMatch** a la valeur `$false`, cette méthode n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="bfd52-130">If the **CanGoToMatch** property is `$false`, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="bfd52-131">InsertText\( text \)</span><span class="sxs-lookup"><span data-stu-id="bfd52-131">InsertText\( text \)</span></span>

<span data-ttu-id="bfd52-132">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-132">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bfd52-133">Remplace la sélection par du texte ou insère du texte à la position actuelle du point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="bfd52-133">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="bfd52-134">**text**  : chaîne Texte à insérer.</span><span class="sxs-lookup"><span data-stu-id="bfd52-134">**text** - String The text to insert.</span></span>

<span data-ttu-id="bfd52-135">Consultez l’[exemple de script](#scripting-example) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="bfd52-135">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="bfd52-136">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="bfd52-136">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="bfd52-137">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-137">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bfd52-138">Sélectionne le texte spécifié par les paramètres **startLine** , **startColumn** , **endLine** et **endColumn** .</span><span class="sxs-lookup"><span data-stu-id="bfd52-138">Selects the text from the **startLine** , **startColumn** , **endLine** , and **endColumn** parameters.</span></span>

<span data-ttu-id="bfd52-139">**startLine**  : entier Ligne où commence la sélection.</span><span class="sxs-lookup"><span data-stu-id="bfd52-139">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="bfd52-140">**startColumn**  : entier Colonne dans la ligne de début où commence la sélection.</span><span class="sxs-lookup"><span data-stu-id="bfd52-140">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="bfd52-141">**endLine**  : entier Ligne où se termine la sélection.</span><span class="sxs-lookup"><span data-stu-id="bfd52-141">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="bfd52-142">**endColumn**  : entier Colonne dans la ligne de fin où se termine la sélection.</span><span class="sxs-lookup"><span data-stu-id="bfd52-142">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="bfd52-143">Consultez l’[exemple de script](#scripting-example) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="bfd52-143">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="bfd52-144">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="bfd52-144">SelectCaretLine\(\)</span></span>

<span data-ttu-id="bfd52-145">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-145">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bfd52-146">Sélectionne la ligne entière de texte où se trouve actuellement le point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="bfd52-146">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="bfd52-147">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="bfd52-147">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="bfd52-148">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-148">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bfd52-149">Définit la position du point d’insertion en fonction du numéro de ligne et du numéro de colonne spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bfd52-149">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="bfd52-150">Elle lève une exception si le numéro de ligne du point d’insertion ou le numéro de colonne du point d’insertion sont en dehors de leurs plages valides respectives.</span><span class="sxs-lookup"><span data-stu-id="bfd52-150">It throws an exception if either the caret line number or the caret column number are out of their respective valid ranges.</span></span>

<span data-ttu-id="bfd52-151">**lineNumber**  : entier Numéro de ligne du point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="bfd52-151">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="bfd52-152">**columnNumber**  : entier Numéro de colonne du point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="bfd52-152">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="bfd52-153">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="bfd52-153">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="bfd52-154">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="bfd52-155">Développe ou réduit toutes les sections de plan.</span><span class="sxs-lookup"><span data-stu-id="bfd52-155">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="bfd52-156">Propriétés</span><span class="sxs-lookup"><span data-stu-id="bfd52-156">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="bfd52-157">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="bfd52-157">CanGoToMatch</span></span>

<span data-ttu-id="bfd52-158">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-158">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="bfd52-159">La propriété booléenne en lecture seule indique si le point d’insertion se trouve à côté d’une parenthèse, d’un crochet ou d’une accolade - `()`, `[]`, `{}`.</span><span class="sxs-lookup"><span data-stu-id="bfd52-159">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - `()`, `[]`, `{}`.</span></span> <span data-ttu-id="bfd52-160">Si le point d’insertion est situé juste avant le caractère ouvrant ou juste après le caractère fermant d’une paire, cette propriété a la valeur `$true`.</span><span class="sxs-lookup"><span data-stu-id="bfd52-160">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is `$true`.</span></span> <span data-ttu-id="bfd52-161">Sinon, c’est `$false`.</span><span class="sxs-lookup"><span data-stu-id="bfd52-161">Otherwise, it is `$false`.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="bfd52-162">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="bfd52-162">CaretColumn</span></span>

<span data-ttu-id="bfd52-163">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-163">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bfd52-164">Propriété en lecture seule qui obtient le numéro de colonne correspondant à la position du point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="bfd52-164">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="bfd52-165">CaretLine</span><span class="sxs-lookup"><span data-stu-id="bfd52-165">CaretLine</span></span>

<span data-ttu-id="bfd52-166">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-166">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bfd52-167">Propriété en lecture seule qui obtient le numéro de la ligne où se trouve le point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="bfd52-167">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="bfd52-168">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="bfd52-168">CaretLineText</span></span>

<span data-ttu-id="bfd52-169">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bfd52-170">Propriété en lecture seule qui obtient la ligne entière de texte où se trouve le point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="bfd52-170">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="bfd52-171">LineCount</span><span class="sxs-lookup"><span data-stu-id="bfd52-171">LineCount</span></span>

<span data-ttu-id="bfd52-172">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-172">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bfd52-173">Propriété en lecture seule qui obtient le nombre de lignes affichées dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="bfd52-173">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="bfd52-174">SelectedText</span><span class="sxs-lookup"><span data-stu-id="bfd52-174">SelectedText</span></span>

<span data-ttu-id="bfd52-175">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-175">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bfd52-176">Propriété en lecture seule qui obtient le texte sélectionné dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="bfd52-176">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="bfd52-177">Consultez l’[exemple de script](#scripting-example) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="bfd52-177">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="bfd52-178">Texte</span><span class="sxs-lookup"><span data-stu-id="bfd52-178">Text</span></span>

<span data-ttu-id="bfd52-179">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bfd52-179">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bfd52-180">Propriété en lecture\/écriture qui obtient ou définit le texte dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="bfd52-180">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="bfd52-181">Consultez l’[exemple de script](#scripting-example) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="bfd52-181">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="bfd52-182">Exemple de script</span><span class="sxs-lookup"><span data-stu-id="bfd52-182">Scripting Example</span></span>

```powershell
# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase.
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor = $psISE.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line.
$endColumn = $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1, 1, 3, $endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a><span data-ttu-id="bfd52-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfd52-183">See Also</span></span>

- [<span data-ttu-id="bfd52-184">Objet ISEFile</span><span class="sxs-lookup"><span data-stu-id="bfd52-184">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="bfd52-185">Objet PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="bfd52-185">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="bfd52-186">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="bfd52-186">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="bfd52-187">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="bfd52-187">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
