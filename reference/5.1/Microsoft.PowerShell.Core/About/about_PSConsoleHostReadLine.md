---
description: Explique comment créer un personnaliser la manière dont PowerShell lit les entrées à l’invite de la console.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_psconsolehostreadline?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSConsoleHostReadLine
ms.openlocfilehash: 3c5f629471ce2a4315e3e90f2baec86dfda1506b
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208761"
---
# <a name="about_psconsolehostreadline"></a><span data-ttu-id="4727a-104">about_PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="4727a-104">about_PSConsoleHostReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="4727a-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="4727a-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="4727a-106">Explique comment créer un personnaliser la manière dont PowerShell lit les entrées à l’invite de la console.</span><span class="sxs-lookup"><span data-stu-id="4727a-106">Explains how to create a customize how PowerShell reads input at the console prompt.</span></span>

## <a name="long-description"></a><span data-ttu-id="4727a-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="4727a-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="4727a-108">À compter de Windows PowerShell v3, vous pouvez écrire une fonction nommée PSConsoleHostReadLine qui remplace la méthode par défaut utilisée pour le traitement de l’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="4727a-108">Starting in Windows PowerShell V3, you can write a function named PSConsoleHostReadLine that overrides the default way that console input is processed.</span></span>

### <a name="examples"></a><span data-ttu-id="4727a-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4727a-109">EXAMPLES</span></span>

<span data-ttu-id="4727a-110">L’exemple suivant lance le bloc-notes et obtient l’entrée à partir d’un fichier texte créé par l’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="4727a-110">The following example launches Notepad and gets input from a text File that the user creates:</span></span>

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

### <a name="remarks"></a><span data-ttu-id="4727a-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="4727a-111">REMARKS</span></span>

<span data-ttu-id="4727a-112">Par défaut, PowerShell lit les entrées à partir de la console dans ce qui est connu sous le nom de « mode cuisiné », dans lequel le sous-système de la console Windows gère tous les frappes de touches, les menus F7 et d’autres entrées.</span><span class="sxs-lookup"><span data-stu-id="4727a-112">By default, PowerShell reads input from the console in what is known as "Cooked Mode" -- in which the Windows console subsystem handles all the keypresses, F7 menus, and other input.</span></span> <span data-ttu-id="4727a-113">Quand vous appuyez sur entrée ou Tab, Windows PowerShell obtient le texte que vous avez tapé jusqu’à ce point.</span><span class="sxs-lookup"><span data-stu-id="4727a-113">When you press Enter or Tab, Windows PowerShell gets the text that you have typed up to that point.</span></span> <span data-ttu-id="4727a-114">Il n’existe aucun moyen de savoir que vous avez appuyé sur Ctrl-R, Ctrl-A, Ctrl + E ou toute autre touche avant d’appuyer sur entrée ou Tab. Dans Windows PowerShell version 3, la fonction PSConsoleHostReadLine résout ce problème.</span><span class="sxs-lookup"><span data-stu-id="4727a-114">There is no way for it to know that you pressed Ctrl-R, Ctrl-A, Ctrl-E, or any other keys before pressing Enter or Tab. In Windows PowerShell version 3, the PSConsoleHostReadLine function solves this issue.</span></span> <span data-ttu-id="4727a-115">Quand vous définissez une fonction nommée PSConsoleHostReadline dans l’hôte de la console Windows PowerShell, Windows PowerShell appelle cette fonction au lieu du mécanisme d’entrée « mode cuisin ».</span><span class="sxs-lookup"><span data-stu-id="4727a-115">When you define a function named PSConsoleHostReadline in the Windows PowerShell console host, Windows PowerShell calls that function instead of the "Cooked Mode" input mechanism.</span></span>

### <a name="see-also"></a><span data-ttu-id="4727a-116">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="4727a-116">SEE ALSO</span></span>

[<span data-ttu-id="4727a-117">about_Prompts</span><span class="sxs-lookup"><span data-stu-id="4727a-117">about_Prompts</span></span>](about_Prompts.md)
