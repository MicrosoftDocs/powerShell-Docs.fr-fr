---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet ISEEditor
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62086763"
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="6895e-103">Objet ISEEditor</span><span class="sxs-lookup"><span data-stu-id="6895e-103">The ISEEditor Object</span></span>

<span data-ttu-id="6895e-104">Un objet **ISEEditor** est une instance de la classe Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="6895e-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="6895e-105">Le volet de la console est un objet **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="6895e-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="6895e-106">Chaque objet [ISEFile](The-ISEFile-Object.md) est associé à un objet **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="6895e-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="6895e-107">Les sections suivantes répertorient les méthodes et propriétés d’un objet **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="6895e-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="6895e-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6895e-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="6895e-109">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="6895e-109">Clear\(\)</span></span>

<span data-ttu-id="6895e-110">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6895e-111">Efface le texte affiché dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="6895e-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="6895e-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="6895e-112">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="6895e-113">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6895e-114">Fait défiler l’éditeur pour afficher la ligne qui correspond à la valeur du paramètre **lineNumber** spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6895e-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="6895e-115">Elle lève une exception si le numéro de ligne spécifié est en dehors de la plage 1-dernier numéro de ligne, qui définit les numéros de ligne valides.</span><span class="sxs-lookup"><span data-stu-id="6895e-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="6895e-116">**lineNumber** Numéro de la ligne à afficher.</span><span class="sxs-lookup"><span data-stu-id="6895e-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="6895e-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="6895e-117">Focus\(\)</span></span>

<span data-ttu-id="6895e-118">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6895e-119">Définit le focus sur l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="6895e-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="6895e-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="6895e-120">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="6895e-121">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6895e-122">Obtient la longueur, sous forme d’entier, de la ligne spécifiée par le numéro de ligne.</span><span class="sxs-lookup"><span data-stu-id="6895e-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="6895e-123">**lineNumber** Numéro de la ligne dont la longueur doit être obtenue.</span><span class="sxs-lookup"><span data-stu-id="6895e-123">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="6895e-124">**Returns** Longueur de la ligne correspondant au numéro de ligne spécifié.</span><span class="sxs-lookup"><span data-stu-id="6895e-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="6895e-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="6895e-125">GoToMatch\(\)</span></span>

<span data-ttu-id="6895e-126">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="6895e-127">Déplace le point d’insertion vers le caractère correspondant si la propriété **CanGoToMatch** de l’objet editor a la valeur **$true**. Ceci se produit quand le point d’insertion se situe juste avant une parenthèse ouvrante, un crochet ouvrant ou une accolade ouvrante \( \[,{ - ou juste après une parenthèse fermante, un crochet fermant ou une accolade fermante -\),\],}.</span><span class="sxs-lookup"><span data-stu-id="6895e-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="6895e-128">Le point d’insertion se trouve avant un caractère ouvrant ou après un caractère fermant.</span><span class="sxs-lookup"><span data-stu-id="6895e-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="6895e-129">Si la propriété **CanGoToMatch** a la valeur **$false**, cette méthode n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="6895e-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="6895e-130">InsertText\( text \)</span><span class="sxs-lookup"><span data-stu-id="6895e-130">InsertText\( text \)</span></span>

<span data-ttu-id="6895e-131">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6895e-132">Remplace la sélection par du texte ou insère du texte à la position actuelle du point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="6895e-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="6895e-133">**text** : chaîne Texte à insérer.</span><span class="sxs-lookup"><span data-stu-id="6895e-133">**text** - String The text to insert.</span></span>

<span data-ttu-id="6895e-134">Consultez l’[exemple de script](#scripting-example) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="6895e-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="6895e-135">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="6895e-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="6895e-136">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6895e-137">Sélectionne le texte spécifié par les paramètres **startLine**, **startColumn**, **endLine** et **endColumn**.</span><span class="sxs-lookup"><span data-stu-id="6895e-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

<span data-ttu-id="6895e-138">**startLine** : entier Ligne où commence la sélection.</span><span class="sxs-lookup"><span data-stu-id="6895e-138">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="6895e-139">**startColumn** : entier Colonne dans la ligne de début où commence la sélection.</span><span class="sxs-lookup"><span data-stu-id="6895e-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="6895e-140">**endLine** : entier Ligne où se termine la sélection.</span><span class="sxs-lookup"><span data-stu-id="6895e-140">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="6895e-141">**endColumn** : entier Colonne dans la ligne de fin où se termine la sélection.</span><span class="sxs-lookup"><span data-stu-id="6895e-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="6895e-142">Consultez l’[exemple de script](#scripting-example) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="6895e-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="6895e-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="6895e-143">SelectCaretLine\(\)</span></span>

<span data-ttu-id="6895e-144">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6895e-145">Sélectionne la ligne entière de texte où se trouve actuellement le point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="6895e-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="6895e-146">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="6895e-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="6895e-147">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6895e-148">Définit la position du point d’insertion en fonction du numéro de ligne et du numéro de colonne spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6895e-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="6895e-149">Elle lève une exception si le numéro de ligne du point d’insertion ou le numéro de colonne du point d’insertion sont en dehors de leurs plages valides respectives.</span><span class="sxs-lookup"><span data-stu-id="6895e-149">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

<span data-ttu-id="6895e-150">**lineNumber** : entier Numéro de ligne du point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="6895e-150">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="6895e-151">**columnNumber** : entier Numéro de colonne du point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="6895e-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="6895e-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="6895e-152">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="6895e-153">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="6895e-154">Développe ou réduit toutes les sections de plan.</span><span class="sxs-lookup"><span data-stu-id="6895e-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="6895e-155">Propriétés</span><span class="sxs-lookup"><span data-stu-id="6895e-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="6895e-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="6895e-156">CanGoToMatch</span></span>

<span data-ttu-id="6895e-157">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="6895e-158">La propriété booléenne en lecture seule indique si le point d’insertion se trouve à côté d’une parenthèse, d’un crochet ou d’une accolade - \(\), \[\], {}.</span><span class="sxs-lookup"><span data-stu-id="6895e-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="6895e-159">Si le point d’insertion est situé juste avant le caractère ouvrant ou juste après le caractère fermant d’une paire, cette propriété a la valeur **$true**.</span><span class="sxs-lookup"><span data-stu-id="6895e-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="6895e-160">Sinon, elle a la valeur **$false**.</span><span class="sxs-lookup"><span data-stu-id="6895e-160">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="6895e-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="6895e-161">CaretColumn</span></span>

<span data-ttu-id="6895e-162">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6895e-163">Propriété en lecture seule qui obtient le numéro de colonne correspondant à la position du point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="6895e-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="6895e-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="6895e-164">CaretLine</span></span>

<span data-ttu-id="6895e-165">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6895e-166">Propriété en lecture seule qui obtient le numéro de la ligne où se trouve le point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="6895e-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="6895e-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="6895e-167">CaretLineText</span></span>

<span data-ttu-id="6895e-168">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6895e-169">Propriété en lecture seule qui obtient la ligne entière de texte où se trouve le point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="6895e-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="6895e-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="6895e-170">LineCount</span></span>

<span data-ttu-id="6895e-171">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6895e-172">Propriété en lecture seule qui obtient le nombre de lignes affichées dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="6895e-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="6895e-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="6895e-173">SelectedText</span></span>

<span data-ttu-id="6895e-174">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6895e-175">Propriété en lecture seule qui obtient le texte sélectionné dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="6895e-175">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="6895e-176">Consultez l’[exemple de script](#scripting-example) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="6895e-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="6895e-177">Texte</span><span class="sxs-lookup"><span data-stu-id="6895e-177">Text</span></span>

<span data-ttu-id="6895e-178">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6895e-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6895e-179">Propriété en lecture\/écriture qui obtient ou définit le texte dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="6895e-179">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="6895e-180">Consultez l’[exemple de script](#scripting-example) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="6895e-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="6895e-181">Exemple de script</span><span class="sxs-lookup"><span data-stu-id="6895e-181">Scripting Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6895e-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6895e-182">See Also</span></span>

- [<span data-ttu-id="6895e-183">Objet ISEFile</span><span class="sxs-lookup"><span data-stu-id="6895e-183">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="6895e-184">Objet PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="6895e-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="6895e-185">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="6895e-185">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="6895e-186">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="6895e-186">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)