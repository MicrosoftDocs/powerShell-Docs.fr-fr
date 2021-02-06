---
description: Explique comment créer un personnaliser la manière dont PowerShell lit les entrées à l’invite de la console.
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_psconsolehostreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSConsoleHostReadLine
ms.openlocfilehash: 2f69cd4c0c8f65f4a963eae561647d6de30a067e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602912"
---
# <a name="about_psconsolehostreadline"></a><span data-ttu-id="428dc-103">about_PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="428dc-103">about_PSConsoleHostReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="428dc-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="428dc-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="428dc-105">Explique comment créer un personnaliser la manière dont PowerShell lit les entrées à l’invite de la console.</span><span class="sxs-lookup"><span data-stu-id="428dc-105">Explains how to create a customize how PowerShell reads input at the console prompt.</span></span>

## <a name="long-description"></a><span data-ttu-id="428dc-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="428dc-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="428dc-107">À compter de Windows PowerShell 3,0, vous pouvez écrire une fonction nommée PSConsoleHostReadLine qui remplace la méthode par défaut utilisée pour le traitement de l’entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="428dc-107">Starting in Windows PowerShell 3.0, you can write a function named PSConsoleHostReadLine that overrides the default way that console input is processed.</span></span>

### <a name="examples"></a><span data-ttu-id="428dc-108">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="428dc-108">EXAMPLES</span></span>

<span data-ttu-id="428dc-109">L’exemple suivant lance le bloc-notes et obtient l’entrée à partir d’un fichier texte créé par l’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="428dc-109">The following example launches Notepad and gets input from a text File that the user creates:</span></span>

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

### <a name="remarks"></a><span data-ttu-id="428dc-110">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="428dc-110">REMARKS</span></span>

<span data-ttu-id="428dc-111">Par défaut, PowerShell lit les entrées à partir de la console dans ce qui est connu sous le nom de « mode cuisiné », dans lequel le sous-système de la console Windows gère tous les frappes de touches, les menus F7 et d’autres entrées.</span><span class="sxs-lookup"><span data-stu-id="428dc-111">By default, PowerShell reads input from the console in what is known as "Cooked Mode" -- in which the Windows console subsystem handles all the keypresses, F7 menus, and other input.</span></span> <span data-ttu-id="428dc-112">Lorsque vous appuyez sur entrée ou Tab, PowerShell obtient le texte que vous avez tapé jusqu’à ce point.</span><span class="sxs-lookup"><span data-stu-id="428dc-112">When you press Enter or Tab, PowerShell gets the text that you have typed up to that point.</span></span> <span data-ttu-id="428dc-113">Il n’existe aucun moyen de savoir que vous avez appuyé sur Ctrl-R, Ctrl-A, Ctrl + E ou toute autre touche avant d’appuyer sur entrée ou Tab. Dans Windows PowerShell 3,0, la fonction PSConsoleHostReadLine résout ce problème.</span><span class="sxs-lookup"><span data-stu-id="428dc-113">There is no way for it to know that you pressed Ctrl-R, Ctrl-A, Ctrl-E, or any other keys before pressing Enter or Tab. In Windows PowerShell 3.0, the PSConsoleHostReadLine function solves this issue.</span></span> <span data-ttu-id="428dc-114">Lorsque vous définissez une fonction nommée PSConsoleHostReadline dans l’hôte de la console PowerShell, PowerShell appelle cette fonction au lieu du mécanisme d’entrée « mode cuisin ».</span><span class="sxs-lookup"><span data-stu-id="428dc-114">When you define a function named PSConsoleHostReadline in the PowerShell console host, PowerShell calls that function instead of the "Cooked Mode" input mechanism.</span></span>

### <a name="see-also"></a><span data-ttu-id="428dc-115">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="428dc-115">SEE ALSO</span></span>

[<span data-ttu-id="428dc-116">about_Prompts</span><span class="sxs-lookup"><span data-stu-id="428dc-116">about_Prompts</span></span>](about_Prompts.md)

