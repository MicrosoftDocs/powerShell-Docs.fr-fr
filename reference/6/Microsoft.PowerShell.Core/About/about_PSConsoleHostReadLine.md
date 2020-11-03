---
description: Explique comment créer un personnaliser la manière dont PowerShell lit les entrées à l’invite de la console.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_psconsolehostreadline?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSConsoleHostReadLine
ms.openlocfilehash: 59373f7a69f5a27411c9087bb666929321f654c0
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208617"
---
# <a name="about_psconsolehostreadline"></a>about_PSConsoleHostReadLine

## <a name="short-description"></a>DESCRIPTION COURTE
Explique comment créer un personnaliser la manière dont PowerShell lit les entrées à l’invite de la console.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

À compter de Windows PowerShell 3,0, vous pouvez écrire une fonction nommée PSConsoleHostReadLine qui remplace la méthode par défaut utilisée pour le traitement de l’entrée de la console.

### <a name="examples"></a>EXEMPLES

L’exemple suivant lance le bloc-notes et obtient l’entrée à partir d’un fichier texte créé par l’utilisateur :

```powershell
function PSConsoleHostReadLine
{
  $inputFile = Join-Path $env:TEMP PSConsoleHostReadLine
  Set-Content $inputFile "PS > "

  # Notepad opens. Enter your command in it, save the file, and then exit.
  notepad $inputFile | Out-Null
  $userInput = Get-Content $inputFile
  $resultingCommand = $userInput.Replace("PS >", "")
  $resultingCommand
}
```

### <a name="remarks"></a>Remarques

Par défaut, PowerShell lit les entrées à partir de la console dans ce qui est connu sous le nom de « mode cuisiné », dans lequel le sous-système de la console Windows gère tous les frappes de touches, les menus F7 et d’autres entrées. Lorsque vous appuyez sur entrée ou Tab, PowerShell obtient le texte que vous avez tapé jusqu’à ce point. Il n’existe aucun moyen de savoir que vous avez appuyé sur Ctrl-R, Ctrl-A, Ctrl + E ou toute autre touche avant d’appuyer sur entrée ou Tab. Dans Windows PowerShell 3,0, la fonction PSConsoleHostReadLine résout ce problème. Lorsque vous définissez une fonction nommée PSConsoleHostReadline dans l’hôte de la console PowerShell, PowerShell appelle cette fonction au lieu du mécanisme d’entrée « mode cuisin ».

### <a name="see-also"></a>VOIR AUSSI

[about_Prompts](about_Prompts.md)
