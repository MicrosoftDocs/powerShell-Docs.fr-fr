---
ms.date: 12/31/2019
keywords: powershell,applet de commande
title: Objet ISEEditor
ms.openlocfilehash: cb63acebc1a8bb9fa6cc07199088ae0d5441bc91
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736187"
---
# <a name="the-iseeditor-object"></a>Objet ISEEditor

Un objet **ISEEditor** est une instance de la classe Microsoft.PowerShell.Host.ISE.ISEEditor. Le volet de la console est un objet **ISEEditor**. Chaque objet [ISEFile](The-ISEFile-Object.md) est associé à un objet **ISEEditor**. Les sections suivantes répertorient les méthodes et propriétés d’un objet **ISEEditor**.

## <a name="methods"></a>Méthodes

### <a name="clear"></a>Clear\(\)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Efface le texte affiché dans l’éditeur.

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible\(int lineNumber\)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Fait défiler l’éditeur pour afficher la ligne qui correspond à la valeur du paramètre **lineNumber** spécifiée. Elle lève une exception si le numéro de ligne spécifié est en dehors de la plage 1-dernier numéro de ligne, qui définit les numéros de ligne valides.

**lineNumber** Numéro de la ligne à afficher.

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Focus\(\)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Définit le focus sur l’éditeur.

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength\(int lineNumber \)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Obtient la longueur, sous forme d’entier, de la ligne spécifiée par le numéro de ligne.

**lineNumber** Numéro de la ligne dont la longueur doit être obtenue.

**Returns** Longueur de la ligne correspondant au numéro de ligne spécifié.

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Déplace le point d’insertion vers le caractère correspondant si la propriété **CanGoToMatch** de l’objet d’éditeur a la valeur `$true`. Ceci se produit quand le point d’insertion se situe juste avant une parenthèse ouvrante, un crochet ouvrant ou une accolade ouvrante `(`,`[`,`{` - ou juste après une parenthèse fermante, un crochet fermant ou une accolade fermante -`)`,`]`,`}`. Le point d’insertion se trouve avant un caractère ouvrant ou après un caractère fermant. Si la propriété **CanGoToMatch** a la valeur `$false`, cette méthode n’a aucun effet.

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a>InsertText\( text \)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Remplace la sélection par du texte ou insère du texte à la position actuelle du point d’insertion.

**text** : chaîne Texte à insérer.

Consultez l’[exemple de script](#scripting-example) plus loin dans cette rubrique.

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Select\( startLine, startColumn, endLine, endColumn \)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Sélectionne le texte spécifié par les paramètres **startLine**, **startColumn**, **endLine** et **endColumn**.

**startLine** : entier Ligne où commence la sélection.

**startColumn** : entier Colonne dans la ligne de début où commence la sélection.

**endLine** : entier Ligne où se termine la sélection.

**endColumn** : entier Colonne dans la ligne de fin où se termine la sélection.

Consultez l’[exemple de script](#scripting-example) plus loin dans cette rubrique.

### <a name="selectcaretline"></a>SelectCaretLine\(\)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Sélectionne la ligne entière de texte où se trouve actuellement le point d’insertion.

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition\( lineNumber, columnNumber \)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Définit la position du point d’insertion en fonction du numéro de ligne et du numéro de colonne spécifiés. Elle lève une exception si le numéro de ligne du point d’insertion ou le numéro de colonne du point d’insertion sont en dehors de leurs plages valides respectives.

**lineNumber** : entier Numéro de ligne du point d’insertion.

**columnNumber** : entier Numéro de colonne du point d’insertion.

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a>ToggleOutliningExpansion\(\)

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Développe ou réduit toutes les sections de plan.

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a>Propriétés

### <a name="cangotomatch"></a>CanGoToMatch

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

La propriété booléenne en lecture seule indique si le point d’insertion se trouve à côté d’une parenthèse, d’un crochet ou d’une accolade - `()`, `[]`, `{}`. Si le point d’insertion est situé juste avant le caractère ouvrant ou juste après le caractère fermant d’une paire, cette propriété a la valeur `$true`. Sinon, c’est `$false`.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient le numéro de colonne correspondant à la position du point d’insertion.

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient le numéro de la ligne où se trouve le point d’insertion.

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient la ligne entière de texte où se trouve le point d’insertion.

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a>LineCount

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient le nombre de lignes affichées dans l’éditeur.

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a>SelectedText

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient le texte sélectionné dans l’éditeur.

Consultez l’[exemple de script](#scripting-example) plus loin dans cette rubrique.

### <a name="text"></a>Texte

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture\/écriture qui obtient ou définit le texte dans l’éditeur.

Consultez l’[exemple de script](#scripting-example) plus loin dans cette rubrique.

## <a name="scripting-example"></a>Exemple de script

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

## <a name="see-also"></a>Voir aussi

- [Objet ISEFile](The-ISEFile-Object.md)
- [Objet PowerShellTab](The-PowerShellTab-Object.md)
- [Objectif du modèle objet de script Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)
