---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSReadLine
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: ce5941787120988a3352153497c9a6df06ee9d89
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208810"
---
# <span data-ttu-id="c1e31-103">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="c1e31-103">Set-PSReadLineOption</span></span>

## <span data-ttu-id="c1e31-104">Synopsis</span><span class="sxs-lookup"><span data-stu-id="c1e31-104">Synopsis</span></span>
<span data-ttu-id="c1e31-105">Personnalise le comportement de la modification de la ligne de commande dans **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="c1e31-105">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

## <span data-ttu-id="c1e31-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1e31-106">Syntax</span></span>

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-Colors <Hashtable>] [<CommonParameters>]
```

## <span data-ttu-id="c1e31-107">Description</span><span class="sxs-lookup"><span data-stu-id="c1e31-107">Description</span></span>

<span data-ttu-id="c1e31-108">L' `Set-PSReadLineOption` applet de commande personnalise le comportement du module **PSReadLine** lors de la modification de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c1e31-108">The `Set-PSReadLineOption` cmdlet customizes the behavior of the **PSReadLine** module when you're editing the command line.</span></span> <span data-ttu-id="c1e31-109">Pour afficher les paramètres **PSReadLine** , utilisez `Get-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-109">To view the **PSReadLine** settings, use `Get-PSReadLineOption`.</span></span>

## <span data-ttu-id="c1e31-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="c1e31-110">Examples</span></span>

### <span data-ttu-id="c1e31-111">Exemple 1 : définir les couleurs de premier plan et d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="c1e31-111">Example 1: Set foreground and background colors</span></span>

<span data-ttu-id="c1e31-112">Cet exemple définit **PSReadLine** pour afficher le jeton de **Commentaire** avec le texte de premier plan vert sur un arrière-plan gris.</span><span class="sxs-lookup"><span data-stu-id="c1e31-112">This example sets **PSReadLine** to display the **Comment** token with green foreground text on a gray background.</span></span> <span data-ttu-id="c1e31-113">Dans la séquence d’échappement utilisée dans l’exemple, **32** représente la couleur de premier plan et **47** représente la couleur d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="c1e31-113">In the escape sequence used in the example, **32** represents the foreground color and **47** represents the background color.</span></span>

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="`e[32;47m" }
```

<span data-ttu-id="c1e31-114">Vous pouvez choisir de définir uniquement une couleur de texte de premier plan.</span><span class="sxs-lookup"><span data-stu-id="c1e31-114">You can choose to set only a foreground text color.</span></span> <span data-ttu-id="c1e31-115">Par exemple, une couleur de texte de premier plan vert clair pour le jeton de **Commentaire** : ``"Comment"="`e[92m"`` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-115">For example, a bright green foreground text color for the **Comment** token: ``"Comment"="`e[92m"``.</span></span>

### <span data-ttu-id="c1e31-116">Exemple 2 : définir le style de cloche</span><span class="sxs-lookup"><span data-stu-id="c1e31-116">Example 2: Set bell style</span></span>

<span data-ttu-id="c1e31-117">Dans cet exemple, **PSReadLine** répond aux erreurs ou conditions qui requièrent l’attention de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c1e31-117">In this example, **PSReadLine** will respond to errors or conditions that require user attention.</span></span>
<span data-ttu-id="c1e31-118">Le **BellStyle** est défini pour émettre un signal sonore à 1221 Hz pour 60 ms.</span><span class="sxs-lookup"><span data-stu-id="c1e31-118">The **BellStyle** is set to emit an audible beep at 1221 Hz for 60 ms.</span></span>

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> <span data-ttu-id="c1e31-119">Cette fonctionnalité peut ne pas fonctionner sur tous les ordinateurs hôtes sur les plateformes.</span><span class="sxs-lookup"><span data-stu-id="c1e31-119">This feature may not work in all hosts on platforms.</span></span>

### <span data-ttu-id="c1e31-120">Exemple 3 : définir plusieurs options</span><span class="sxs-lookup"><span data-stu-id="c1e31-120">Example 3: Set multiple options</span></span>

<span data-ttu-id="c1e31-121">`Set-PSReadLineOption` peut définir plusieurs options avec une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="c1e31-121">`Set-PSReadLineOption` can set multiple options with a hash table.</span></span>

```powershell
$PSReadLineOptions = @{
    EditMode = "Emacs"
    HistoryNoDuplicates = $true
    HistorySearchCursorMovesToEnd = $true
    Colors = @{
        "Command" = "#8181f7"
    }
}
Set-PSReadLineOption @PSReadLineOptions
```

<span data-ttu-id="c1e31-122">La `$PSReadLineOptions` table de hachage définit les clés et les valeurs.</span><span class="sxs-lookup"><span data-stu-id="c1e31-122">The `$PSReadLineOptions` hash table sets the keys and values.</span></span> <span data-ttu-id="c1e31-123">`Set-PSReadLineOption` utilise les clés et les valeurs de `@PSReadLineOptions` pour mettre à jour les options **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="c1e31-123">`Set-PSReadLineOption` uses the keys and values with `@PSReadLineOptions` to update the **PSReadLine** options.</span></span>

<span data-ttu-id="c1e31-124">Vous pouvez afficher les clés et les valeurs en entrant le nom de la table `$PSReadLineOptions` de hachage dans la ligne de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1e31-124">You can view the keys and values entering the hash table name, `$PSReadLineOptions` on the PowerShell command line.</span></span>

### <span data-ttu-id="c1e31-125">Exemple 4 : définir plusieurs options de couleur</span><span class="sxs-lookup"><span data-stu-id="c1e31-125">Example 4: Set multiple color options</span></span>

<span data-ttu-id="c1e31-126">Cet exemple montre comment définir plusieurs valeurs de couleur dans une même commande.</span><span class="sxs-lookup"><span data-stu-id="c1e31-126">This example shows how to set more than one color value in a single command.</span></span>

```powershell
Set-PSReadLineOption -Colors @{
  Command            = 'Magenta'
  Number             = 'DarkGray'
  Member             = 'DarkGray'
  Operator           = 'DarkGray'
  Type               = 'DarkGray'
  Variable           = 'DarkGreen'
  Parameter          = 'DarkGreen'
  ContinuationPrompt = 'DarkGray'
  Default            = 'DarkGray'
}
```

### <span data-ttu-id="c1e31-127">Exemple 5 : définir des valeurs de couleur pour plusieurs types</span><span class="sxs-lookup"><span data-stu-id="c1e31-127">Example 5: Set color values for multiple types</span></span>

<span data-ttu-id="c1e31-128">Cet exemple montre trois méthodes différentes pour définir la couleur des jetons affichés dans **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="c1e31-128">This example shows three different methods for how to set the color of tokens displayed in **PSReadLine**.</span></span>

```powershell
Set-PSReadLineOption -Colors @{
 # Use a ConsoleColor enum
 "Error" = [ConsoleColor]::DarkRed

 # 24 bit color escape sequence
 "String" = "$([char]0x1b)[38;5;100m"

 # RGB value
 "Command" = "#8181f7"
}
```

### <span data-ttu-id="c1e31-129">Exemple 6 : utilisation de ViModeChangeHandler pour afficher les modifications du mode VI</span><span class="sxs-lookup"><span data-stu-id="c1e31-129">Example 6: Use ViModeChangeHandler to display Vi mode changes</span></span>

<span data-ttu-id="c1e31-130">Cet exemple émet un changement de curseur à l’échappement VT en réponse à une modification du mode **VI** .</span><span class="sxs-lookup"><span data-stu-id="c1e31-130">This example emits a cursor change VT escape in response to a **Vi** mode change.</span></span>

```powershell
function OnViModeChange {
    if ($args[0] -eq 'Command') {
        # Set the cursor to a blinking block.
        Write-Host -NoNewLine "`e[1 q"
    } else {
        # Set the cursor to a blinking line.
        Write-Host -NoNewLine "`e[5 q"
    }
}
Set-PSReadLineOption -ViModeIndicator Script -ViModeChangeHandler $Function:OnViModeChange
```

<span data-ttu-id="c1e31-131">La fonction **OnViModeChange** définit les options de curseur pour les modes **VI** : Insert et Command.</span><span class="sxs-lookup"><span data-stu-id="c1e31-131">The **OnViModeChange** function sets the cursor options for the **Vi** modes: insert and command.</span></span>
<span data-ttu-id="c1e31-132">**ViModeChangeHandler** utilise le `Function:` fournisseur pour faire référence à **OnViModeChange** en tant qu’objet de bloc de script.</span><span class="sxs-lookup"><span data-stu-id="c1e31-132">**ViModeChangeHandler** uses the `Function:` provider to reference **OnViModeChange** as a script block object.</span></span>

<span data-ttu-id="c1e31-133">Pour plus d'informations, consultez [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).</span><span class="sxs-lookup"><span data-stu-id="c1e31-133">For more information, see [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).</span></span>

## <span data-ttu-id="c1e31-134">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c1e31-134">Parameters</span></span>

### <span data-ttu-id="c1e31-135">-AddToHistoryHandler</span><span class="sxs-lookup"><span data-stu-id="c1e31-135">-AddToHistoryHandler</span></span>

<span data-ttu-id="c1e31-136">Spécifie un **scriptblock** qui contrôle les commandes qui sont ajoutées à l’historique **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="c1e31-136">Specifies a **ScriptBlock** that controls which commands get added to **PSReadLine** history.</span></span>

<span data-ttu-id="c1e31-137">Le **scriptblock** reçoit la ligne de commande comme entrée.</span><span class="sxs-lookup"><span data-stu-id="c1e31-137">The **ScriptBlock** receives the command line as input.</span></span> <span data-ttu-id="c1e31-138">Si le **scriptblock** retourne `$True` , la ligne de commande est ajoutée à l’historique.</span><span class="sxs-lookup"><span data-stu-id="c1e31-138">If the **ScriptBlock** returns `$True`, the command line is added to the history.</span></span>

```yaml
Type: System.Func`2[System.String,System.Object]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-139">-AnsiEscapeTimeout</span><span class="sxs-lookup"><span data-stu-id="c1e31-139">-AnsiEscapeTimeout</span></span>

<span data-ttu-id="c1e31-140">Cette option est spécifique à Windows lorsque l’entrée est redirigée, par exemple, en cas d’exécution sous `tmux` ou `screen` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-140">This option is specific to Windows when input is redirected, for example, when running under `tmux` or `screen`.</span></span>

<span data-ttu-id="c1e31-141">Avec l’entrée redirigée sur Windows, de nombreuses clés sont envoyées sous la forme d’une séquence de caractères commençant par le caractère d’échappement.</span><span class="sxs-lookup"><span data-stu-id="c1e31-141">With redirected input on Windows, many keys are sent as a sequence of characters starting with the escape character.</span></span> <span data-ttu-id="c1e31-142">Il est impossible de faire la distinction entre un caractère d’échappement unique suivi d’un plus grand nombre de caractères et d’une séquence d’échappement valide.</span><span class="sxs-lookup"><span data-stu-id="c1e31-142">It's impossible to distinguish between a single escape character followed by more characters and a valid escape sequence.</span></span>

<span data-ttu-id="c1e31-143">L’hypothèse est que le terminal peut envoyer les caractères plus rapidement qu’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c1e31-143">The assumption is that the terminal can send the characters faster than a user types.</span></span> <span data-ttu-id="c1e31-144">**PSReadLine** attend ce délai d’attente avant de conclure qu’il a reçu une séquence d’échappement complète.</span><span class="sxs-lookup"><span data-stu-id="c1e31-144">**PSReadLine** waits for this timeout before concluding that it has received a complete escape sequence.</span></span>

<span data-ttu-id="c1e31-145">Si vous voyez des caractères aléatoires ou inattendus lorsque vous tapez, vous pouvez ajuster ce délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="c1e31-145">If you see random or unexpected characters when you type, you can adjust this timeout.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-146">-BellStyle</span><span class="sxs-lookup"><span data-stu-id="c1e31-146">-BellStyle</span></span>

<span data-ttu-id="c1e31-147">Spécifie comment **PSReadLine** répond à différentes erreurs et conditions ambiguës.</span><span class="sxs-lookup"><span data-stu-id="c1e31-147">Specifies how **PSReadLine** responds to various error and ambiguous conditions.</span></span>

<span data-ttu-id="c1e31-148">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c1e31-148">The valid values are as follows:</span></span>

- <span data-ttu-id="c1e31-149">**Audible** : un bref signal sonore.</span><span class="sxs-lookup"><span data-stu-id="c1e31-149">**Audible** : A short beep.</span></span>
- <span data-ttu-id="c1e31-150">**Visuel** : le texte clignote brièvement.</span><span class="sxs-lookup"><span data-stu-id="c1e31-150">**Visual** : Text flashes briefly.</span></span>
- <span data-ttu-id="c1e31-151">**Aucun** : aucun commentaire.</span><span class="sxs-lookup"><span data-stu-id="c1e31-151">**None** : No feedback.</span></span>

```yaml
Type: Microsoft.PowerShell.BellStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Audible
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-152">-Couleurs</span><span class="sxs-lookup"><span data-stu-id="c1e31-152">-Colors</span></span>

<span data-ttu-id="c1e31-153">Le paramètre **couleurs** spécifie différentes couleurs utilisées par **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="c1e31-153">The **Colors** parameter specifies various colors used by **PSReadLine**.</span></span>

<span data-ttu-id="c1e31-154">L’argument est une table de hachage dans laquelle les clés spécifient l’élément et les valeurs spécifient la couleur.</span><span class="sxs-lookup"><span data-stu-id="c1e31-154">The argument is a hash table where the keys specify which element and the values specify the color.</span></span>
<span data-ttu-id="c1e31-155">Pour plus d’informations, consultez [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="c1e31-155">For more information, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="c1e31-156">Les couleurs peuvent être une valeur de **ConsoleColor** , par exemple `[ConsoleColor]::Red` , ou une séquence d’échappement ANSI valide.</span><span class="sxs-lookup"><span data-stu-id="c1e31-156">Colors can be either a value from **ConsoleColor** , for example `[ConsoleColor]::Red`, or a valid ANSI escape sequence.</span></span> <span data-ttu-id="c1e31-157">Les séquences d’échappement valides dépendent de votre terminal.</span><span class="sxs-lookup"><span data-stu-id="c1e31-157">Valid escape sequences depend on your terminal.</span></span> <span data-ttu-id="c1e31-158">Dans PowerShell 5,0, un exemple de séquence d’échappement pour le texte en rouge est `$([char]0x1b)[91m` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-158">In PowerShell 5.0, an example escape sequence for red text is `$([char]0x1b)[91m`.</span></span> <span data-ttu-id="c1e31-159">Dans PowerShell 6 et versions ultérieures, la même séquence d’échappement est `` `e[91m`` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-159">In PowerShell 6 and above, the same escape sequence is `` `e[91m``.</span></span> <span data-ttu-id="c1e31-160">Vous pouvez spécifier d’autres séquences d’échappement, y compris les types suivants :</span><span class="sxs-lookup"><span data-stu-id="c1e31-160">You can specify other escape sequences including the following types:</span></span>

- <span data-ttu-id="c1e31-161">256 couleur</span><span class="sxs-lookup"><span data-stu-id="c1e31-161">256 color</span></span>
- <span data-ttu-id="c1e31-162">couleur 24 bits</span><span class="sxs-lookup"><span data-stu-id="c1e31-162">24-bit color</span></span>
- <span data-ttu-id="c1e31-163">Premier plan, arrière-plan ou les deux</span><span class="sxs-lookup"><span data-stu-id="c1e31-163">Foreground, background, or both</span></span>
- <span data-ttu-id="c1e31-164">Inverse, gras</span><span class="sxs-lookup"><span data-stu-id="c1e31-164">Inverse, bold</span></span>

<span data-ttu-id="c1e31-165">Pour plus d’informations sur les codes de couleur ANSI, consultez [Code ANSI Escape](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) dans Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="c1e31-165">For more information about ANSI color codes, see [ANSI escape code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in Wikipedia.</span></span>

<span data-ttu-id="c1e31-166">Les clés valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c1e31-166">The valid keys include:</span></span>

- <span data-ttu-id="c1e31-167">**ContinuationPrompt** : couleur de l’invite de continuation.</span><span class="sxs-lookup"><span data-stu-id="c1e31-167">**ContinuationPrompt** : The color of the continuation prompt.</span></span>
- <span data-ttu-id="c1e31-168">**Accent** : couleur d’accentuation.</span><span class="sxs-lookup"><span data-stu-id="c1e31-168">**Emphasis** : The emphasis color.</span></span> <span data-ttu-id="c1e31-169">Par exemple, le texte correspondant lors de la recherche de l’historique.</span><span class="sxs-lookup"><span data-stu-id="c1e31-169">For example, the matching text when searching history.</span></span>
- <span data-ttu-id="c1e31-170">**Erreur** : couleur de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="c1e31-170">**Error** : The error color.</span></span> <span data-ttu-id="c1e31-171">Par exemple, dans l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="c1e31-171">For example, in the prompt.</span></span>
- <span data-ttu-id="c1e31-172">**Sélection** : couleur pour mettre en surbrillance la sélection de menu ou le texte sélectionné.</span><span class="sxs-lookup"><span data-stu-id="c1e31-172">**Selection** : The color to highlight the menu selection or selected text.</span></span>
- <span data-ttu-id="c1e31-173">**Default** : couleur de jeton par défaut.</span><span class="sxs-lookup"><span data-stu-id="c1e31-173">**Default** : The default token color.</span></span>
- <span data-ttu-id="c1e31-174">**Comment** : couleur de jeton de commentaire.</span><span class="sxs-lookup"><span data-stu-id="c1e31-174">**Comment** : The comment token color.</span></span>
- <span data-ttu-id="c1e31-175">**Mot clé** : la couleur du jeton de mot clé.</span><span class="sxs-lookup"><span data-stu-id="c1e31-175">**Keyword** : The keyword token color.</span></span>
- <span data-ttu-id="c1e31-176">**Chaîne** : la couleur du jeton de chaîne.</span><span class="sxs-lookup"><span data-stu-id="c1e31-176">**String** : The string token color.</span></span>
- <span data-ttu-id="c1e31-177">**Opérateur** : couleur de jeton de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="c1e31-177">**Operator** : The operator token color.</span></span>
- <span data-ttu-id="c1e31-178">**Variable** : couleur du jeton de la variable.</span><span class="sxs-lookup"><span data-stu-id="c1e31-178">**Variable** : The variable token color.</span></span>
- <span data-ttu-id="c1e31-179">**Commande** : couleur du jeton de commande.</span><span class="sxs-lookup"><span data-stu-id="c1e31-179">**Command** : The command token color.</span></span>
- <span data-ttu-id="c1e31-180">**Paramètre** : couleur du jeton du paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1e31-180">**Parameter** : The parameter token color.</span></span>
- <span data-ttu-id="c1e31-181">**Type** : la couleur du jeton de type.</span><span class="sxs-lookup"><span data-stu-id="c1e31-181">**Type** : The type token color.</span></span>
- <span data-ttu-id="c1e31-182">**Number** : la couleur du jeton numérique.</span><span class="sxs-lookup"><span data-stu-id="c1e31-182">**Number** : The number token color.</span></span>
- <span data-ttu-id="c1e31-183">**Membre** : la couleur du jeton de nom de membre.</span><span class="sxs-lookup"><span data-stu-id="c1e31-183">**Member** : The member name token color.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-184">-CommandValidationHandler</span><span class="sxs-lookup"><span data-stu-id="c1e31-184">-CommandValidationHandler</span></span>

<span data-ttu-id="c1e31-185">Spécifie un **scriptblock** qui est appelé à partir de **ValidateAndAcceptLine**.</span><span class="sxs-lookup"><span data-stu-id="c1e31-185">Specifies a **ScriptBlock** that is called from **ValidateAndAcceptLine**.</span></span> <span data-ttu-id="c1e31-186">Si une exception est levée, la validation échoue et l’erreur est signalée.</span><span class="sxs-lookup"><span data-stu-id="c1e31-186">If an exception is thrown, validation fails and the error is reported.</span></span>

<span data-ttu-id="c1e31-187">Avant de lever une exception, le gestionnaire de validation peut placer le curseur au point de l’erreur pour faciliter la résolution.</span><span class="sxs-lookup"><span data-stu-id="c1e31-187">Before throwing an exception, the validation handler can place the cursor at the point of the error to make it easier to fix.</span></span> <span data-ttu-id="c1e31-188">Un gestionnaire de validation peut également modifier la ligne de commande, par exemple pour corriger les erreurs typographiques courantes.</span><span class="sxs-lookup"><span data-stu-id="c1e31-188">A validation handler can also change the command line, such as to correct common typographical errors.</span></span>

<span data-ttu-id="c1e31-189">**ValidateAndAcceptLine** est utilisé pour éviter d’encombrer votre historique avec des commandes qui ne fonctionnent pas.</span><span class="sxs-lookup"><span data-stu-id="c1e31-189">**ValidateAndAcceptLine** is used to avoid cluttering your history with commands that can't work.</span></span>

```yaml
Type: System.Action`1[System.Management.Automation.Language.CommandAst]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-190">-CompletionQueryItems</span><span class="sxs-lookup"><span data-stu-id="c1e31-190">-CompletionQueryItems</span></span>

<span data-ttu-id="c1e31-191">Spécifie le nombre maximal d’éléments de saisie semi-automatique affichés sans invite.</span><span class="sxs-lookup"><span data-stu-id="c1e31-191">Specifies the maximum number of completion items that are shown without prompting.</span></span>

<span data-ttu-id="c1e31-192">Si le nombre d’éléments à afficher est supérieur à cette valeur, **PSReadLine** invite **Oui/non** avant d’afficher les éléments de saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="c1e31-192">If the number of items to show is greater than this value, **PSReadLine** prompts **yes/no** before displaying the completion items.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-193">-ContinuationPrompt</span><span class="sxs-lookup"><span data-stu-id="c1e31-193">-ContinuationPrompt</span></span>

<span data-ttu-id="c1e31-194">Spécifie la chaîne affichée au début des lignes suivantes lorsque l’entrée multiligne est entrée.</span><span class="sxs-lookup"><span data-stu-id="c1e31-194">Specifies the string displayed at the beginning of the subsequent lines when multi-line input is entered.</span></span> <span data-ttu-id="c1e31-195">La valeur par défaut est double signe supérieur à ( `>>` ).</span><span class="sxs-lookup"><span data-stu-id="c1e31-195">The default is double greater-than signs (`>>`).</span></span> <span data-ttu-id="c1e31-196">Une chaîne vide est valide.</span><span class="sxs-lookup"><span data-stu-id="c1e31-196">An empty string is valid.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-197">-DingDuration</span><span class="sxs-lookup"><span data-stu-id="c1e31-197">-DingDuration</span></span>

<span data-ttu-id="c1e31-198">Spécifie la durée du signal sonore quand **BellStyle** est défini sur **audible**.</span><span class="sxs-lookup"><span data-stu-id="c1e31-198">Specifies the duration of the beep when **BellStyle** is set to **Audible**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 50ms
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-199">-DingTone</span><span class="sxs-lookup"><span data-stu-id="c1e31-199">-DingTone</span></span>

<span data-ttu-id="c1e31-200">Spécifie le ton en Hertz (Hz) du bip quand **BellStyle** est défini sur **audible**.</span><span class="sxs-lookup"><span data-stu-id="c1e31-200">Specifies the tone in Hertz (Hz) of the beep when **BellStyle** is set to **Audible**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1221
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-201">-EditMode</span><span class="sxs-lookup"><span data-stu-id="c1e31-201">-EditMode</span></span>

<span data-ttu-id="c1e31-202">Spécifie le mode d’édition de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c1e31-202">Specifies the command line editing mode.</span></span> <span data-ttu-id="c1e31-203">L’utilisation de ce paramètre réinitialise toutes les combinaisons de touches définies par `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-203">Using this parameter resets any key bindings set by `Set-PSReadLineKeyHandler`.</span></span>

<span data-ttu-id="c1e31-204">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c1e31-204">The valid values are as follows:</span></span>

- <span data-ttu-id="c1e31-205">**Windows** : les combinaisons de touches émulent PowerShell, cmd et Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c1e31-205">**Windows** : Key bindings emulate PowerShell, cmd, and Visual Studio.</span></span>
- <span data-ttu-id="c1e31-206">**Emacs** -les combinaisons de touches émulent bash ou Emacs.</span><span class="sxs-lookup"><span data-stu-id="c1e31-206">**Emacs** : Key bindings emulate Bash or Emacs.</span></span>
- <span data-ttu-id="c1e31-207">**VI** : les combinaisons de touches émulent VI.</span><span class="sxs-lookup"><span data-stu-id="c1e31-207">**Vi** : Key bindings emulate Vi.</span></span>

<span data-ttu-id="c1e31-208">Utilisez `Get-PSReadLineKeyHandler` pour afficher les combinaisons de touches pour le **EditMode** actuellement configuré.</span><span class="sxs-lookup"><span data-stu-id="c1e31-208">Use `Get-PSReadLineKeyHandler` to see the key bindings for the currently configured **EditMode**.</span></span>

```yaml
Type: Microsoft.PowerShell.EditMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-209">-ExtraPromptLineCount</span><span class="sxs-lookup"><span data-stu-id="c1e31-209">-ExtraPromptLineCount</span></span>

<span data-ttu-id="c1e31-210">Spécifie le nombre de lignes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="c1e31-210">Specifies the number of extra lines.</span></span>

<span data-ttu-id="c1e31-211">Si votre invite s’étend sur plusieurs lignes, spécifiez une valeur pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1e31-211">If your prompt spans more than one line, specify a value for this parameter.</span></span> <span data-ttu-id="c1e31-212">Utilisez cette option lorsque vous souhaitez que des lignes supplémentaires soient disponibles quand **PSReadLine** affiche l’invite après avoir affiché une sortie.</span><span class="sxs-lookup"><span data-stu-id="c1e31-212">Use this option when you want extra lines to be available when **PSReadLine** displays the prompt after showing some output.</span></span> <span data-ttu-id="c1e31-213">Par exemple, **PSReadLine** retourne une liste des saisies semi-automatiques.</span><span class="sxs-lookup"><span data-stu-id="c1e31-213">For example, **PSReadLine** returns a list of completions.</span></span>

<span data-ttu-id="c1e31-214">Cette option est requise moins que dans les versions précédentes de **PSReadLine** , mais elle est utile lorsque la `InvokePrompt` fonction est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c1e31-214">This option is needed less than in previous versions of **PSReadLine** , but is useful when the `InvokePrompt` function is used.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-215">-HistoryNoDuplicates</span><span class="sxs-lookup"><span data-stu-id="c1e31-215">-HistoryNoDuplicates</span></span>

<span data-ttu-id="c1e31-216">Cette option contrôle le comportement de rappel.</span><span class="sxs-lookup"><span data-stu-id="c1e31-216">This option controls the recall behavior.</span></span> <span data-ttu-id="c1e31-217">Les commandes dupliquées sont toujours ajoutées au fichier d’historique.</span><span class="sxs-lookup"><span data-stu-id="c1e31-217">Duplicate commands are still added to the history file.</span></span>
<span data-ttu-id="c1e31-218">Lorsque cette option est définie, seul l’appel le plus récent s’affiche lorsque vous rappelez des commandes.</span><span class="sxs-lookup"><span data-stu-id="c1e31-218">When this option is set, only the most recent invocation appears when recalling commands.</span></span> <span data-ttu-id="c1e31-219">Les commandes répétées sont ajoutées à l’historique pour préserver le classement pendant le rappel.</span><span class="sxs-lookup"><span data-stu-id="c1e31-219">Repeated commands are added to history to preserve ordering during recall.</span></span> <span data-ttu-id="c1e31-220">Toutefois, vous ne souhaitez généralement pas voir la commande plusieurs fois lors du rappel ou de la recherche dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="c1e31-220">However, you typically don't want to see the command multiple times when recalling or searching the history.</span></span>

<span data-ttu-id="c1e31-221">Par défaut, la propriété **HistoryNoDuplicates** de l’objet global **PSConsoleReadLineOptions** a la valeur `True` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-221">By default, the **HistoryNoDuplicates** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="c1e31-222">L’utilisation de cet **Paramètre_Booléen** affecte la valeur à la propriété `True` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-222">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="c1e31-223">Pour modifier la valeur de la propriété, vous devez spécifier la valeur de **Paramètre_Booléen** comme suit : `-HistoryNoDuplicates:$False` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-223">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-HistoryNoDuplicates:$False`.</span></span>

<span data-ttu-id="c1e31-224">À l’aide de la commande suivante, vous pouvez définir directement la valeur de la propriété :</span><span class="sxs-lookup"><span data-stu-id="c1e31-224">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistoryNoDuplicates = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-225">-HistorySavePath</span><span class="sxs-lookup"><span data-stu-id="c1e31-225">-HistorySavePath</span></span>

<span data-ttu-id="c1e31-226">Spécifie le chemin d’accès au fichier dans lequel l’historique est enregistré.</span><span class="sxs-lookup"><span data-stu-id="c1e31-226">Specifies the path to the file where history is saved.</span></span> <span data-ttu-id="c1e31-227">Les ordinateurs exécutant des plates-formes Windows ou non Windows stockent le fichier à différents emplacements.</span><span class="sxs-lookup"><span data-stu-id="c1e31-227">Computers running Windows or non-Windows platforms store the file in different locations.</span></span> <span data-ttu-id="c1e31-228">Le nom de fichier est stocké dans une variable `$($host.Name)_history.txt` , par exemple `ConsoleHost_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-228">The filename is stored in a variable `$($host.Name)_history.txt`, for example `ConsoleHost_history.txt`.</span></span>

<span data-ttu-id="c1e31-229">Si vous n’utilisez pas ce paramètre, le chemin d’accès par défaut est le suivant :</span><span class="sxs-lookup"><span data-stu-id="c1e31-229">If you don't use this parameter, the default path is as follows:</span></span>

<span data-ttu-id="c1e31-230">**Windows**</span><span class="sxs-lookup"><span data-stu-id="c1e31-230">**Windows**</span></span>

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

<span data-ttu-id="c1e31-231">**non-Windows**</span><span class="sxs-lookup"><span data-stu-id="c1e31-231">**non-Windows**</span></span>

`$env:XDG_DATA_HOME/powershell/PSReadLine\$($host.Name)_history.txt`

`$env:HOME/.local/share/powershell/PSReadLine\$($host.Name)_history.txt`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A file named $($host.Name)_history.txt in $env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine on Windows and $env:XDG_DATA_HOME/powershell/PSReadLine or $env:HOME/.local/share/powershell/PSReadLine on non-Windows platforms
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-232">-HistorySaveStyle</span><span class="sxs-lookup"><span data-stu-id="c1e31-232">-HistorySaveStyle</span></span>

<span data-ttu-id="c1e31-233">Spécifie la manière dont **PSReadLine** enregistre l’historique.</span><span class="sxs-lookup"><span data-stu-id="c1e31-233">Specifies how **PSReadLine** saves history.</span></span>

<span data-ttu-id="c1e31-234">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c1e31-234">Valid values are as follows:</span></span>

- <span data-ttu-id="c1e31-235">**SaveIncrementally** : enregistrer l’historique après l’exécution de chaque commande et le partage entre plusieurs instances de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1e31-235">**SaveIncrementally** : Save history after each command is executed and share across multiple instances of PowerShell.</span></span>
- <span data-ttu-id="c1e31-236">**SaveAtExit** : ajouter le fichier d’historique à la sortie de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1e31-236">**SaveAtExit** : Append history file when PowerShell exits.</span></span>
- <span data-ttu-id="c1e31-237">**SaveNothing** : n’utilisez pas de fichier d’historique.</span><span class="sxs-lookup"><span data-stu-id="c1e31-237">**SaveNothing** : Don't use a history file.</span></span>

```yaml
Type: Microsoft.PowerShell.HistorySaveStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SaveIncrementally
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-238">-HistorySearchCaseSensitive</span><span class="sxs-lookup"><span data-stu-id="c1e31-238">-HistorySearchCaseSensitive</span></span>

<span data-ttu-id="c1e31-239">Spécifie que la recherche dans l’historique respecte la casse dans des fonctions telles que **ReverseSearchHistory** ou **HistorySearchBackward**.</span><span class="sxs-lookup"><span data-stu-id="c1e31-239">Specifies that history searching is case-sensitive in functions like **ReverseSearchHistory** or **HistorySearchBackward**.</span></span>

<span data-ttu-id="c1e31-240">Par défaut, la propriété **HistorySearchCaseSensitive** de l’objet global **PSConsoleReadLineOptions** a la valeur `False` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-240">By default, the **HistorySearchCaseSensitive** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="c1e31-241">L’utilisation de cet **Paramètre_Booléen** affecte la valeur à la propriété `True` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-241">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="c1e31-242">Pour modifier la valeur de la propriété, vous devez spécifier la valeur de **Paramètre_Booléen** comme suit : `-HistorySearchCaseSensitive:$False` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-242">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCaseSensitive:$False`.</span></span>

<span data-ttu-id="c1e31-243">À l’aide de la commande suivante, vous pouvez définir directement la valeur de la propriété :</span><span class="sxs-lookup"><span data-stu-id="c1e31-243">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistorySearchCaseSensitive = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-244">-HistorySearchCursorMovesToEnd</span><span class="sxs-lookup"><span data-stu-id="c1e31-244">-HistorySearchCursorMovesToEnd</span></span>

<span data-ttu-id="c1e31-245">Indique que le curseur se déplace vers la fin des commandes que vous chargez à partir de l’historique à l’aide d’une recherche.</span><span class="sxs-lookup"><span data-stu-id="c1e31-245">Indicates that the cursor moves to the end of commands that you load from history by using a search.</span></span>
<span data-ttu-id="c1e31-246">Lorsque ce paramètre a la valeur `$False` , le curseur reste à la position où il se trouvait quand vous avez appuyé sur les flèches haut ou bas.</span><span class="sxs-lookup"><span data-stu-id="c1e31-246">When this parameter is set to `$False`, the cursor remains at the position it was when you pressed the up or down arrows.</span></span>

<span data-ttu-id="c1e31-247">Par défaut, la propriété **HistorySearchCursorMovesToEnd** de l’objet global **PSConsoleReadLineOptions** a la valeur `False` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-247">By default, the **HistorySearchCursorMovesToEnd** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="c1e31-248">À l’aide de cet **Paramètre_Booléen** , affectez la valeur à la propriété `True` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-248">Using this **SwitchParameter** set the property value to `True`.</span></span> <span data-ttu-id="c1e31-249">Pour modifier la valeur de la propriété, vous devez spécifier la valeur de **Paramètre_Booléen** comme suit : `-HistorySearchCursorMovesToEnd:$False` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-249">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCursorMovesToEnd:$False`.</span></span>

<span data-ttu-id="c1e31-250">À l’aide de la commande suivante, vous pouvez définir directement la valeur de la propriété :</span><span class="sxs-lookup"><span data-stu-id="c1e31-250">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistorySearchCursorMovesToEnd = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-251">-MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="c1e31-251">-MaximumHistoryCount</span></span>

<span data-ttu-id="c1e31-252">Spécifie le nombre maximal de commandes à enregistrer dans l’historique **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="c1e31-252">Specifies the maximum number of commands to save in **PSReadLine** history.</span></span>

<span data-ttu-id="c1e31-253">L’historique de **PSReadLine** est séparé de l’historique PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1e31-253">**PSReadLine** history is separate from PowerShell history.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-254">-MaximumKillRingCount</span><span class="sxs-lookup"><span data-stu-id="c1e31-254">-MaximumKillRingCount</span></span>

<span data-ttu-id="c1e31-255">Spécifie le nombre maximal d’éléments stockés dans l’anneau Kill.</span><span class="sxs-lookup"><span data-stu-id="c1e31-255">Specifies the maximum number of items stored in the kill ring.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-256">-PromptText</span><span class="sxs-lookup"><span data-stu-id="c1e31-256">-PromptText</span></span>

<span data-ttu-id="c1e31-257">En cas d’erreur d’analyse, **PSReadLine** modifie une partie de l’invite rouge.</span><span class="sxs-lookup"><span data-stu-id="c1e31-257">When there's a parse error, **PSReadLine** changes a part of the prompt red.</span></span> <span data-ttu-id="c1e31-258">**PSReadLine** analyse votre fonction d’invite pour déterminer comment modifier uniquement la couleur d’une partie de votre invite.</span><span class="sxs-lookup"><span data-stu-id="c1e31-258">**PSReadLine** analyzes your prompt function to determine how to change only the color of part of your prompt.</span></span> <span data-ttu-id="c1e31-259">Cette analyse n’est pas 100% fiable.</span><span class="sxs-lookup"><span data-stu-id="c1e31-259">This analysis isn't 100% reliable.</span></span>

<span data-ttu-id="c1e31-260">Utilisez cette option si **PSReadLine** modifie votre invite de manière inattendue.</span><span class="sxs-lookup"><span data-stu-id="c1e31-260">Use this option if **PSReadLine** is changing your prompt in unexpected ways.</span></span> <span data-ttu-id="c1e31-261">Inclut tout espace blanc de fin.</span><span class="sxs-lookup"><span data-stu-id="c1e31-261">Include any trailing whitespace.</span></span>

<span data-ttu-id="c1e31-262">Par exemple, si votre fonction d’invite ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c1e31-262">For example, if your prompt function looked like the following example:</span></span>

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

<span data-ttu-id="c1e31-263">Ensuite, définissez :</span><span class="sxs-lookup"><span data-stu-id="c1e31-263">Then set:</span></span>

`Set-PSReadLineOption -PromptText "# "`

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-264">-ShowToolTips</span><span class="sxs-lookup"><span data-stu-id="c1e31-264">-ShowToolTips</span></span>

<span data-ttu-id="c1e31-265">Lorsque vous affichez les saisies semi-automatiques possibles, les info-bulles sont affichées dans la liste des saisies semi-automatiques.</span><span class="sxs-lookup"><span data-stu-id="c1e31-265">When displaying possible completions, tooltips are shown in the list of completions.</span></span>

<span data-ttu-id="c1e31-266">Cette option est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="c1e31-266">This option is enabled by default.</span></span> <span data-ttu-id="c1e31-267">Cette option n’a pas été activée par défaut dans les versions antérieures de **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="c1e31-267">This option wasn't enabled by default in prior versions of **PSReadLine**.</span></span> <span data-ttu-id="c1e31-268">Pour désactiver, définissez cette option sur `$False` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-268">To disable, set this option to `$False`.</span></span>

<span data-ttu-id="c1e31-269">Par défaut, la propriété **ShowToolTips** de l’objet global **PSConsoleReadLineOptions** a la valeur `True` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-269">By default, the **ShowToolTips** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="c1e31-270">L’utilisation de cet **Paramètre_Booléen** affecte la valeur à la propriété `True` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-270">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="c1e31-271">Pour modifier la valeur de la propriété, vous devez spécifier la valeur de **Paramètre_Booléen** comme suit : `-ShowToolTips:$False` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-271">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-ShowToolTips:$False`.</span></span>

<span data-ttu-id="c1e31-272">À l’aide de la commande suivante, vous pouvez définir directement la valeur de la propriété :</span><span class="sxs-lookup"><span data-stu-id="c1e31-272">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).ShowToolTips = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-273">-ViModeChangeHandler</span><span class="sxs-lookup"><span data-stu-id="c1e31-273">-ViModeChangeHandler</span></span>

<span data-ttu-id="c1e31-274">Lorsque **ViModeIndicator** a la valeur `Script` , le bloc de script fourni est appelé chaque fois que le mode change.</span><span class="sxs-lookup"><span data-stu-id="c1e31-274">When the **ViModeIndicator** is set to `Script`, the script block provided will be invoked every time the mode changes.</span></span> <span data-ttu-id="c1e31-275">Le bloc de script est fourni avec un argument de type `ViMode` .</span><span class="sxs-lookup"><span data-stu-id="c1e31-275">The script block is provided one argument of type `ViMode`.</span></span>

<span data-ttu-id="c1e31-276">Ce paramètre a été introduit dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="c1e31-276">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-277">-ViModeIndicator</span><span class="sxs-lookup"><span data-stu-id="c1e31-277">-ViModeIndicator</span></span>

<span data-ttu-id="c1e31-278">Cette option définit l’indication visuelle pour le mode **VI** actuel.</span><span class="sxs-lookup"><span data-stu-id="c1e31-278">This option sets the visual indication for the current **Vi** mode.</span></span> <span data-ttu-id="c1e31-279">Mode insertion ou mode commande.</span><span class="sxs-lookup"><span data-stu-id="c1e31-279">Either insert mode or command mode.</span></span>

<span data-ttu-id="c1e31-280">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c1e31-280">The valid values are as follows:</span></span>

- <span data-ttu-id="c1e31-281">**None** : il n’existe aucune indication.</span><span class="sxs-lookup"><span data-stu-id="c1e31-281">**None** : There's no indication.</span></span>
- <span data-ttu-id="c1e31-282">**Prompt** : l’invite change de couleur.</span><span class="sxs-lookup"><span data-stu-id="c1e31-282">**Prompt** : The prompt changes color.</span></span>
- <span data-ttu-id="c1e31-283">**Curseur** : le curseur change de taille.</span><span class="sxs-lookup"><span data-stu-id="c1e31-283">**Cursor** : The cursor changes size.</span></span>
- <span data-ttu-id="c1e31-284">**Script** : le texte spécifié par l’utilisateur est imprimé.</span><span class="sxs-lookup"><span data-stu-id="c1e31-284">**Script** : User-specified text is printed.</span></span>

```yaml
Type: Microsoft.PowerShell.ViModeStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-285">-WordDelimiters</span><span class="sxs-lookup"><span data-stu-id="c1e31-285">-WordDelimiters</span></span>

<span data-ttu-id="c1e31-286">Spécifie les caractères qui délimitent les mots pour des fonctions telles que **ForwardWord** ou **KillWord**.</span><span class="sxs-lookup"><span data-stu-id="c1e31-286">Specifies the characters that delimit words for functions like **ForwardWord** or **KillWord**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: ;:,.[]{}()/\|^&*-=+'"–—―
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1e31-287">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c1e31-287">CommonParameters</span></span>

<span data-ttu-id="c1e31-288">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c1e31-288">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c1e31-289">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c1e31-289">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c1e31-290">Entrées</span><span class="sxs-lookup"><span data-stu-id="c1e31-290">Inputs</span></span>

### <span data-ttu-id="c1e31-291">None</span><span class="sxs-lookup"><span data-stu-id="c1e31-291">None</span></span>

<span data-ttu-id="c1e31-292">Vous ne pouvez pas diriger d’objets vers `Set-PSReadLineOption.`</span><span class="sxs-lookup"><span data-stu-id="c1e31-292">You cannot pipe objects to `Set-PSReadLineOption.`</span></span>

## <span data-ttu-id="c1e31-293">Sorties</span><span class="sxs-lookup"><span data-stu-id="c1e31-293">Outputs</span></span>

### <span data-ttu-id="c1e31-294">Aucun</span><span class="sxs-lookup"><span data-stu-id="c1e31-294">None</span></span>

<span data-ttu-id="c1e31-295">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="c1e31-295">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c1e31-296">Notes</span><span class="sxs-lookup"><span data-stu-id="c1e31-296">Notes</span></span>

## <span data-ttu-id="c1e31-297">Liens connexes</span><span class="sxs-lookup"><span data-stu-id="c1e31-297">Related links</span></span>

[<span data-ttu-id="c1e31-298">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="c1e31-298">about_PSReadLine</span></span>](./About/about_PSReadLine.md)

[<span data-ttu-id="c1e31-299">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="c1e31-299">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="c1e31-300">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="c1e31-300">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="c1e31-301">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="c1e31-301">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="c1e31-302">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="c1e31-302">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
