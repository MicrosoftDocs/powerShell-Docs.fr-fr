---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/get-psreadlinekeyhandler?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSReadLineKeyHandler
ms.openlocfilehash: bb1e92a8f4bca96dc369b5b799c7e89245e432be
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597147"
---
# <span data-ttu-id="b53eb-102">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="b53eb-102">Get-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="b53eb-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b53eb-103">SYNOPSIS</span></span>
<span data-ttu-id="b53eb-104">Obtient les fonctions de clé liées pour le module PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b53eb-104">Gets the bound key functions for the PSReadLine module.</span></span>

## <span data-ttu-id="b53eb-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="b53eb-105">SYNTAX</span></span>

### <span data-ttu-id="b53eb-106">FullListing (par défaut)</span><span class="sxs-lookup"><span data-stu-id="b53eb-106">FullListing (default)</span></span>

```
Get-PSReadLineKeyHandler [-Bound] [-Unbound] [<CommonParameters>]
```

### <span data-ttu-id="b53eb-107">SpecificBindings</span><span class="sxs-lookup"><span data-stu-id="b53eb-107">SpecificBindings</span></span>

```
Get-PSReadLineKeyHandler [-Chord] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="b53eb-108">Description</span><span class="sxs-lookup"><span data-stu-id="b53eb-108">DESCRIPTION</span></span>

<span data-ttu-id="b53eb-109">Si aucun paramètre n’est spécifié, retourne les fonctions de clé actuellement liées pour le module PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b53eb-109">If no parameter is specified, returns the currently bound key functions for the PSReadLine module.</span></span>

<span data-ttu-id="b53eb-110">Si le paramètre **corde** est spécifié, l’applet de commande retourne les clés liées spécifiques.</span><span class="sxs-lookup"><span data-stu-id="b53eb-110">If **Chord** parameter is specified, the cmdlet returns the specific bound keys.</span></span>

## <span data-ttu-id="b53eb-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b53eb-111">EXAMPLES</span></span>

### <span data-ttu-id="b53eb-112">Exemple 1 : récupération de tous les mappages de clés</span><span class="sxs-lookup"><span data-stu-id="b53eb-112">Example 1: Get all key mappings</span></span>

<span data-ttu-id="b53eb-113">Cette commande retourne tous les mappages de clés, liés et non liés.</span><span class="sxs-lookup"><span data-stu-id="b53eb-113">This command returns all key mappings, bound and unbound.</span></span>

```powershell
Get-PSReadLineKeyHandler -Bound -Unbound
```

```Output
Key                   Function                Description
---                   --------                -----------
Enter                 AcceptLine              Accept the input or move to the next line if input is missing a closing token.
Shift+Enter           AddLine                 Move the cursor to the next line without attempting to execute the input
Escape                RevertLine              Equivalent to undo all edits (clears the line except lines imported from history)
LeftArrow             BackwardChar            Move the cursor back one character
RightArrow            ForwardChar             Move the cursor forward one character
Ctrl+LeftArrow        BackwardWord            Move the cursor to the beginning of the current or previous word
Ctrl+RightArrow       NextWord                Move the cursor forward to the start of the next word
Shift+LeftArrow       SelectBackwardChar      Adjust the current selection to include the previous character
Shift+RightArrow      SelectForwardChar       Adjust the current selection to include the next character
Ctrl+Shift+LeftArrow  SelectBackwardWord      Adjust the current selection to include the previous word
Ctrl+Shift+RightArrow SelectNextWord          Adjust the current selection to include the next word
UpArrow               PreviousHistory         Replace the input with the previous item in the history
DownArrow             NextHistory             Replace the input with the next item in the history
Home                  BeginningOfLine         Move the cursor to the beginning of the line
End                   EndOfLine               Move the cursor to the end of the line
Shift+Home            SelectBackwardsLine     Adjust the current selection to include from the cursor to the end of the line
Shift+End             SelectLine              Adjust the current selection to include from the cursor to the start of the line
Delete                DeleteChar              Delete the character under the cursor
Backspace             BackwardDeleteChar      Delete the character before the cursor
Ctrl+Spacebar         MenuComplete            Complete the input if there is a single completion, otherwise complete the input by selecting from a menu o...
Tab                   TabCompleteNext         Complete the input using the next completion
Shift+Tab             TabCompletePrevious     Complete the input using the previous completion
Ctrl+a                SelectAll               Select the entire line. Moves the cursor to the end of the line
Ctrl+c                CopyOrCancelLine        Either copy selected text to the clipboard, or if no text is selected, cancel editing the line with Cancel...
Ctrl+C                Copy                    Copy selected region to the system clipboard.  If no region is selected, copy the whole line
Ctrl+l                ClearScreen             Clear the screen and redraw the current line at the top of the screen
Ctrl+r                ReverseSearchHistory    Search history backwards interactively
...
```

### <span data-ttu-id="b53eb-114">Exemple 2 : afficher les clés liées</span><span class="sxs-lookup"><span data-stu-id="b53eb-114">Example 2: Get bound keys</span></span>

<span data-ttu-id="b53eb-115">Cette commande retourne uniquement les clés liées et les combinaisons de touches.</span><span class="sxs-lookup"><span data-stu-id="b53eb-115">This command returns only bound keys and key combinations.</span></span>

```powershell
Get-PSReadLineKeyHandler
```

```Output
Key                   Function                Description
---                   --------                -----------
Enter                 AcceptLine              Accept the input or move to the next line if input is missing a closing token.
Shift+Enter           AddLine                 Move the cursor to the next line without attempting to execute the input
Escape                RevertLine              Equivalent to undo all edits (clears the line except lines imported from history)
LeftArrow             BackwardChar            Move the cursor back one character
RightArrow            ForwardChar             Move the cursor forward one character
Ctrl+LeftArrow        BackwardWord            Move the cursor to the beginning of the current or previous word
Ctrl+RightArrow       NextWord                Move the cursor forward to the start of the next word
Shift+LeftArrow       SelectBackwardChar      Adjust the current selection to include the previous character
Shift+RightArrow      SelectForwardChar       Adjust the current selection to include the next character
Ctrl+Shift+LeftArrow  SelectBackwardWord      Adjust the current selection to include the previous word
Ctrl+Shift+RightArrow SelectNextWord          Adjust the current selection to include the next word
UpArrow               PreviousHistory         Replace the input with the previous item in the history
DownArrow             NextHistory             Replace the input with the next item in the history
Home                  BeginningOfLine         Move the cursor to the beginning of the line
End                   EndOfLine               Move the cursor to the end of the line
Shift+Home            SelectBackwardsLine     Adjust the current selection to include from the cursor to the end of the line
Shift+End             SelectLine              Adjust the current selection to include from the cursor to the start of the line
Delete                DeleteChar              Delete the character under the cursor
Backspace             BackwardDeleteChar      Delete the character before the cursor
Ctrl+Spacebar         MenuComplete            Complete the input if there is a single completion, otherwise complete the input by selecting from a menu o...
Tab                   TabCompleteNext         Complete the input using the next completion
...
```

### <span data-ttu-id="b53eb-116">Exemple 3 : accéder à des combinaisons de touches spécifiques</span><span class="sxs-lookup"><span data-stu-id="b53eb-116">Example 3: Get specific key bindings</span></span>

<span data-ttu-id="b53eb-117">Cette commande retourne uniquement les liaisons pour les clés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="b53eb-117">This command returns only the bindings for the specified keys.</span></span>

```powershell
Get-PSReadLineKeyHandler -Chord Enter, Shift+Enter
```

```Output
Key         Function   Description
---         --------   -----------
Enter       AcceptLine Accept the input or move to the next line if input is missing a closing token.
Shift+Enter AddLine    Move the cursor to the next line without attempting to execute the input
...
```

## <span data-ttu-id="b53eb-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b53eb-118">PARAMETERS</span></span>

### <span data-ttu-id="b53eb-119">-Lié</span><span class="sxs-lookup"><span data-stu-id="b53eb-119">-Bound</span></span>

<span data-ttu-id="b53eb-120">Indique que cette applet de commande retourne des fonctions liées.</span><span class="sxs-lookup"><span data-stu-id="b53eb-120">Indicates that this cmdlet returns functions that are bound.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FullListing
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b53eb-121">-Indépendant</span><span class="sxs-lookup"><span data-stu-id="b53eb-121">-Unbound</span></span>

<span data-ttu-id="b53eb-122">Indique que cette applet de commande retourne des fonctions qui sont indépendantes.</span><span class="sxs-lookup"><span data-stu-id="b53eb-122">Indicates that this cmdlet returns functions that are unbound.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FullListing
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b53eb-123">-Corde</span><span class="sxs-lookup"><span data-stu-id="b53eb-123">-Chord</span></span>

<span data-ttu-id="b53eb-124">Retourne uniquement les fonctions liées à des séquences ou des clés spécifiques.</span><span class="sxs-lookup"><span data-stu-id="b53eb-124">Return only functions bound to specific keys or sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: SpecificBindings
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b53eb-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b53eb-125">CommonParameters</span></span>

<span data-ttu-id="b53eb-126">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b53eb-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b53eb-127">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b53eb-127">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b53eb-128">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b53eb-128">INPUTS</span></span>

### <span data-ttu-id="b53eb-129">None</span><span class="sxs-lookup"><span data-stu-id="b53eb-129">None</span></span>

<span data-ttu-id="b53eb-130">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b53eb-130">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="b53eb-131">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b53eb-131">OUTPUTS</span></span>

### <span data-ttu-id="b53eb-132">Microsoft. PowerShell. KeyHandler</span><span class="sxs-lookup"><span data-stu-id="b53eb-132">Microsoft.PowerShell.KeyHandler</span></span>

## <span data-ttu-id="b53eb-133">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b53eb-133">NOTES</span></span>

## <span data-ttu-id="b53eb-134">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b53eb-134">RELATED LINKS</span></span>

[<span data-ttu-id="b53eb-135">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="b53eb-135">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="b53eb-136">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="b53eb-136">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="b53eb-137">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="b53eb-137">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="b53eb-138">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="b53eb-138">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)

