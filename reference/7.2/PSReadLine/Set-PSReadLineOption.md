---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: cac2c2bb8ce1f3a28c0d91c7503b3ac4d038ccad
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "99603660"
---
# <span data-ttu-id="14360-102">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="14360-102">Set-PSReadLineOption</span></span>

## <span data-ttu-id="14360-103">Synopsis</span><span class="sxs-lookup"><span data-stu-id="14360-103">Synopsis</span></span>
<span data-ttu-id="14360-104">Personnalise le comportement de la modification de la ligne de commande dans **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="14360-104">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

## <span data-ttu-id="14360-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14360-105">Syntax</span></span>

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func`2[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action`1[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-PredictionSource <PredictionSource>]
 [-PredictionViewStyle <PredictionViewStyle>] [-Colors <Hashtable>] [<CommonParameters>]
```

## <span data-ttu-id="14360-106">Description</span><span class="sxs-lookup"><span data-stu-id="14360-106">Description</span></span>

<span data-ttu-id="14360-107">L' `Set-PSReadLineOption` applet de commande personnalise le comportement du module **PSReadLine** lors de la modification de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="14360-107">The `Set-PSReadLineOption` cmdlet customizes the behavior of the **PSReadLine** module when you're editing the command line.</span></span> <span data-ttu-id="14360-108">Pour afficher les paramètres **PSReadLine** , utilisez `Get-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="14360-108">To view the **PSReadLine** settings, use `Get-PSReadLineOption`.</span></span>

## <span data-ttu-id="14360-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="14360-109">Examples</span></span>

### <span data-ttu-id="14360-110">Exemple 1 : définir les couleurs de premier plan et d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="14360-110">Example 1: Set foreground and background colors</span></span>

<span data-ttu-id="14360-111">Cet exemple définit **PSReadLine** pour afficher le jeton de **Commentaire** avec le texte de premier plan vert sur un arrière-plan gris.</span><span class="sxs-lookup"><span data-stu-id="14360-111">This example sets **PSReadLine** to display the **Comment** token with green foreground text on a gray background.</span></span> <span data-ttu-id="14360-112">Dans la séquence d’échappement utilisée dans l’exemple, **32** représente la couleur de premier plan et **47** représente la couleur d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="14360-112">In the escape sequence used in the example, **32** represents the foreground color and **47** represents the background color.</span></span>

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="`e[32;47m" }
```

<span data-ttu-id="14360-113">Vous pouvez choisir de définir uniquement une couleur de texte de premier plan.</span><span class="sxs-lookup"><span data-stu-id="14360-113">You can choose to set only a foreground text color.</span></span> <span data-ttu-id="14360-114">Par exemple, une couleur de texte de premier plan vert clair pour le jeton de **Commentaire** : ``"Comment"="`e[92m"`` .</span><span class="sxs-lookup"><span data-stu-id="14360-114">For example, a bright green foreground text color for the **Comment** token: ``"Comment"="`e[92m"``.</span></span>

### <span data-ttu-id="14360-115">Exemple 2 : définir le style de cloche</span><span class="sxs-lookup"><span data-stu-id="14360-115">Example 2: Set bell style</span></span>

<span data-ttu-id="14360-116">Dans cet exemple, **PSReadLine** répond aux erreurs ou conditions qui requièrent l’attention de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="14360-116">In this example, **PSReadLine** will respond to errors or conditions that require user attention.</span></span>
<span data-ttu-id="14360-117">Le **BellStyle** est défini pour émettre un signal sonore à 1221 Hz pour 60 ms.</span><span class="sxs-lookup"><span data-stu-id="14360-117">The **BellStyle** is set to emit an audible beep at 1221 Hz for 60 ms.</span></span>

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> <span data-ttu-id="14360-118">Cette fonctionnalité peut ne pas fonctionner sur tous les ordinateurs hôtes sur les plateformes.</span><span class="sxs-lookup"><span data-stu-id="14360-118">This feature may not work in all hosts on platforms.</span></span>

### <span data-ttu-id="14360-119">Exemple 3 : définir plusieurs options</span><span class="sxs-lookup"><span data-stu-id="14360-119">Example 3: Set multiple options</span></span>

<span data-ttu-id="14360-120">`Set-PSReadLineOption` peut définir plusieurs options avec une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="14360-120">`Set-PSReadLineOption` can set multiple options with a hash table.</span></span>

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

<span data-ttu-id="14360-121">La `$PSReadLineOptions` table de hachage définit les clés et les valeurs.</span><span class="sxs-lookup"><span data-stu-id="14360-121">The `$PSReadLineOptions` hash table sets the keys and values.</span></span> <span data-ttu-id="14360-122">`Set-PSReadLineOption` utilise les clés et les valeurs de `@PSReadLineOptions` pour mettre à jour les options **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="14360-122">`Set-PSReadLineOption` uses the keys and values with `@PSReadLineOptions` to update the **PSReadLine** options.</span></span>

<span data-ttu-id="14360-123">Vous pouvez afficher les clés et les valeurs en entrant le nom de la table `$PSReadLineOptions` de hachage dans la ligne de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14360-123">You can view the keys and values entering the hash table name, `$PSReadLineOptions` on the PowerShell command line.</span></span>

### <span data-ttu-id="14360-124">Exemple 4 : définir plusieurs options de couleur</span><span class="sxs-lookup"><span data-stu-id="14360-124">Example 4: Set multiple color options</span></span>

<span data-ttu-id="14360-125">Cet exemple montre comment définir plusieurs valeurs de couleur dans une même commande.</span><span class="sxs-lookup"><span data-stu-id="14360-125">This example shows how to set more than one color value in a single command.</span></span>

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

### <span data-ttu-id="14360-126">Exemple 5 : définir des valeurs de couleur pour plusieurs types</span><span class="sxs-lookup"><span data-stu-id="14360-126">Example 5: Set color values for multiple types</span></span>

<span data-ttu-id="14360-127">Cet exemple montre trois méthodes différentes pour définir la couleur des jetons affichés dans **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="14360-127">This example shows three different methods for how to set the color of tokens displayed in **PSReadLine**.</span></span>

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

### <span data-ttu-id="14360-128">Exemple 6 : utilisation de ViModeChangeHandler pour afficher les modifications du mode VI</span><span class="sxs-lookup"><span data-stu-id="14360-128">Example 6: Use ViModeChangeHandler to display Vi mode changes</span></span>

<span data-ttu-id="14360-129">Cet exemple émet un changement de curseur à l’échappement VT en réponse à une modification du mode **VI** .</span><span class="sxs-lookup"><span data-stu-id="14360-129">This example emits a cursor change VT escape in response to a **Vi** mode change.</span></span>

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

<span data-ttu-id="14360-130">La fonction **OnViModeChange** définit les options de curseur pour les modes **VI** : Insert et Command.</span><span class="sxs-lookup"><span data-stu-id="14360-130">The **OnViModeChange** function sets the cursor options for the **Vi** modes: insert and command.</span></span>
<span data-ttu-id="14360-131">**ViModeChangeHandler** utilise le `Function:` fournisseur pour faire référence à **OnViModeChange** en tant qu’objet de bloc de script.</span><span class="sxs-lookup"><span data-stu-id="14360-131">**ViModeChangeHandler** uses the `Function:` provider to reference **OnViModeChange** as a script block object.</span></span>

<span data-ttu-id="14360-132">Pour plus d'informations, consultez [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).</span><span class="sxs-lookup"><span data-stu-id="14360-132">For more information, see [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).</span></span>

## <span data-ttu-id="14360-133">Paramètres</span><span class="sxs-lookup"><span data-stu-id="14360-133">Parameters</span></span>

### <span data-ttu-id="14360-134">-AddToHistoryHandler</span><span class="sxs-lookup"><span data-stu-id="14360-134">-AddToHistoryHandler</span></span>

<span data-ttu-id="14360-135">Spécifie un **scriptblock** qui contrôle les commandes qui sont ajoutées à l’historique **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="14360-135">Specifies a **ScriptBlock** that controls which commands get added to **PSReadLine** history.</span></span>

<span data-ttu-id="14360-136">Le **scriptblock** reçoit la ligne de commande comme entrée.</span><span class="sxs-lookup"><span data-stu-id="14360-136">The **ScriptBlock** receives the command line as input.</span></span> <span data-ttu-id="14360-137">Si le **scriptblock** retourne `$True` , la ligne de commande est ajoutée à l’historique.</span><span class="sxs-lookup"><span data-stu-id="14360-137">If the **ScriptBlock** returns `$True`, the command line is added to the history.</span></span>

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

### <span data-ttu-id="14360-138">-AnsiEscapeTimeout</span><span class="sxs-lookup"><span data-stu-id="14360-138">-AnsiEscapeTimeout</span></span>

<span data-ttu-id="14360-139">Cette option est spécifique à Windows lorsque l’entrée est redirigée, par exemple, en cas d’exécution sous `tmux` ou `screen` .</span><span class="sxs-lookup"><span data-stu-id="14360-139">This option is specific to Windows when input is redirected, for example, when running under `tmux` or `screen`.</span></span>

<span data-ttu-id="14360-140">Avec l’entrée redirigée sur Windows, de nombreuses clés sont envoyées sous la forme d’une séquence de caractères commençant par le caractère d’échappement.</span><span class="sxs-lookup"><span data-stu-id="14360-140">With redirected input on Windows, many keys are sent as a sequence of characters starting with the escape character.</span></span> <span data-ttu-id="14360-141">Il est impossible de faire la distinction entre un caractère d’échappement unique suivi d’un plus grand nombre de caractères et d’une séquence d’échappement valide.</span><span class="sxs-lookup"><span data-stu-id="14360-141">It's impossible to distinguish between a single escape character followed by more characters and a valid escape sequence.</span></span>

<span data-ttu-id="14360-142">L’hypothèse est que le terminal peut envoyer les caractères plus rapidement qu’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="14360-142">The assumption is that the terminal can send the characters faster than a user types.</span></span> <span data-ttu-id="14360-143">**PSReadLine** attend ce délai d’attente avant de conclure qu’il a reçu une séquence d’échappement complète.</span><span class="sxs-lookup"><span data-stu-id="14360-143">**PSReadLine** waits for this timeout before concluding that it has received a complete escape sequence.</span></span>

<span data-ttu-id="14360-144">Si vous voyez des caractères aléatoires ou inattendus lorsque vous tapez, vous pouvez ajuster ce délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="14360-144">If you see random or unexpected characters when you type, you can adjust this timeout.</span></span>

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

### <span data-ttu-id="14360-145">-BellStyle</span><span class="sxs-lookup"><span data-stu-id="14360-145">-BellStyle</span></span>

<span data-ttu-id="14360-146">Spécifie comment **PSReadLine** répond à différentes erreurs et conditions ambiguës.</span><span class="sxs-lookup"><span data-stu-id="14360-146">Specifies how **PSReadLine** responds to various error and ambiguous conditions.</span></span>

<span data-ttu-id="14360-147">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="14360-147">The valid values are as follows:</span></span>

- <span data-ttu-id="14360-148">**Audible**: un bref signal sonore.</span><span class="sxs-lookup"><span data-stu-id="14360-148">**Audible**: A short beep.</span></span>
- <span data-ttu-id="14360-149">**Visuel**: le texte clignote brièvement.</span><span class="sxs-lookup"><span data-stu-id="14360-149">**Visual**: Text flashes briefly.</span></span>
- <span data-ttu-id="14360-150">**Aucun**: aucun commentaire.</span><span class="sxs-lookup"><span data-stu-id="14360-150">**None**: No feedback.</span></span>

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

### <span data-ttu-id="14360-151">-Couleurs</span><span class="sxs-lookup"><span data-stu-id="14360-151">-Colors</span></span>

<span data-ttu-id="14360-152">Le paramètre **couleurs** spécifie différentes couleurs utilisées par **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="14360-152">The **Colors** parameter specifies various colors used by **PSReadLine**.</span></span>

<span data-ttu-id="14360-153">L’argument est une table de hachage dans laquelle les clés spécifient l’élément et les valeurs spécifient la couleur.</span><span class="sxs-lookup"><span data-stu-id="14360-153">The argument is a hash table where the keys specify which element and the values specify the color.</span></span>
<span data-ttu-id="14360-154">Pour plus d’informations, consultez [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="14360-154">For more information, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="14360-155">Les couleurs peuvent être une valeur de **ConsoleColor**, par exemple `[ConsoleColor]::Red` , ou une séquence d’échappement ANSI valide.</span><span class="sxs-lookup"><span data-stu-id="14360-155">Colors can be either a value from **ConsoleColor**, for example `[ConsoleColor]::Red`, or a valid ANSI escape sequence.</span></span> <span data-ttu-id="14360-156">Les séquences d’échappement valides dépendent de votre terminal.</span><span class="sxs-lookup"><span data-stu-id="14360-156">Valid escape sequences depend on your terminal.</span></span> <span data-ttu-id="14360-157">Dans PowerShell 5,0, un exemple de séquence d’échappement pour le texte en rouge est `$([char]0x1b)[91m` .</span><span class="sxs-lookup"><span data-stu-id="14360-157">In PowerShell 5.0, an example escape sequence for red text is `$([char]0x1b)[91m`.</span></span> <span data-ttu-id="14360-158">Dans PowerShell 6 et versions ultérieures, la même séquence d’échappement est `` `e[91m`` .</span><span class="sxs-lookup"><span data-stu-id="14360-158">In PowerShell 6 and above, the same escape sequence is `` `e[91m``.</span></span> <span data-ttu-id="14360-159">Vous pouvez spécifier d’autres séquences d’échappement, y compris les types suivants :</span><span class="sxs-lookup"><span data-stu-id="14360-159">You can specify other escape sequences including the following types:</span></span>

<span data-ttu-id="14360-160">Deux paramètres de couleur ont été ajoutés pour prendre en charge la personnalisation du `ListView` dans PSReadLine 2.2.0 :</span><span class="sxs-lookup"><span data-stu-id="14360-160">Two color settings were added to support customization of the `ListView` in PSReadLine 2.2.0:</span></span>

- <span data-ttu-id="14360-161">**ListPredictionColor** : définissez la couleur du caractère de début `>` et le nom de la source de fin, par exemple `[History]` .</span><span class="sxs-lookup"><span data-stu-id="14360-161">**ListPredictionColor** - set color for the leading `>` character and the trailing source name, e.g. `[History]`.</span></span> <span data-ttu-id="14360-162">Par défaut, il utilise `DarkYellow` comme couleur de premier plan.</span><span class="sxs-lookup"><span data-stu-id="14360-162">By default, it uses `DarkYellow` as the foreground color.</span></span>
- <span data-ttu-id="14360-163">**ListPredictionSelectedColor** -définit la couleur pour indiquer qu’un élément de liste est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="14360-163">**ListPredictionSelectedColor** - set color for indicating a list item is selected.</span></span> <span data-ttu-id="14360-164">Par défaut, il utilise `DarkBlack` comme couleur d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="14360-164">By default, it uses `DarkBlack` as the background color.</span></span>

- <span data-ttu-id="14360-165">256 couleur</span><span class="sxs-lookup"><span data-stu-id="14360-165">256 color</span></span>
- <span data-ttu-id="14360-166">couleur 24 bits</span><span class="sxs-lookup"><span data-stu-id="14360-166">24-bit color</span></span>
- <span data-ttu-id="14360-167">Premier plan, arrière-plan ou les deux</span><span class="sxs-lookup"><span data-stu-id="14360-167">Foreground, background, or both</span></span>
- <span data-ttu-id="14360-168">Inverse, gras</span><span class="sxs-lookup"><span data-stu-id="14360-168">Inverse, bold</span></span>

<span data-ttu-id="14360-169">Pour plus d’informations sur les codes de couleur ANSI, consultez [Code ANSI Escape](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) dans Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="14360-169">For more information about ANSI color codes, see [ANSI escape code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in Wikipedia.</span></span>

<span data-ttu-id="14360-170">Les clés valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="14360-170">The valid keys include:</span></span>

- <span data-ttu-id="14360-171">**ContinuationPrompt**: couleur de l’invite de continuation.</span><span class="sxs-lookup"><span data-stu-id="14360-171">**ContinuationPrompt**: The color of the continuation prompt.</span></span>
- <span data-ttu-id="14360-172">**Accent**: couleur d’accentuation.</span><span class="sxs-lookup"><span data-stu-id="14360-172">**Emphasis**: The emphasis color.</span></span> <span data-ttu-id="14360-173">Par exemple, le texte correspondant lors de la recherche de l’historique.</span><span class="sxs-lookup"><span data-stu-id="14360-173">For example, the matching text when searching history.</span></span>
- <span data-ttu-id="14360-174">**Erreur**: couleur de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="14360-174">**Error**: The error color.</span></span> <span data-ttu-id="14360-175">Par exemple, dans l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="14360-175">For example, in the prompt.</span></span>
- <span data-ttu-id="14360-176">**Sélection**: couleur pour mettre en surbrillance la sélection de menu ou le texte sélectionné.</span><span class="sxs-lookup"><span data-stu-id="14360-176">**Selection**: The color to highlight the menu selection or selected text.</span></span>
- <span data-ttu-id="14360-177">**Default**: couleur de jeton par défaut.</span><span class="sxs-lookup"><span data-stu-id="14360-177">**Default**: The default token color.</span></span>
- <span data-ttu-id="14360-178">**Comment**: couleur de jeton de commentaire.</span><span class="sxs-lookup"><span data-stu-id="14360-178">**Comment**: The comment token color.</span></span>
- <span data-ttu-id="14360-179">**Mot clé**: la couleur du jeton de mot clé.</span><span class="sxs-lookup"><span data-stu-id="14360-179">**Keyword**: The keyword token color.</span></span>
- <span data-ttu-id="14360-180">**Chaîne**: la couleur du jeton de chaîne.</span><span class="sxs-lookup"><span data-stu-id="14360-180">**String**: The string token color.</span></span>
- <span data-ttu-id="14360-181">**Opérateur**: couleur de jeton de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="14360-181">**Operator**: The operator token color.</span></span>
- <span data-ttu-id="14360-182">**Variable**: couleur du jeton de la variable.</span><span class="sxs-lookup"><span data-stu-id="14360-182">**Variable**: The variable token color.</span></span>
- <span data-ttu-id="14360-183">**Commande**: couleur du jeton de commande.</span><span class="sxs-lookup"><span data-stu-id="14360-183">**Command**: The command token color.</span></span>
- <span data-ttu-id="14360-184">**Paramètre**: couleur du jeton du paramètre.</span><span class="sxs-lookup"><span data-stu-id="14360-184">**Parameter**: The parameter token color.</span></span>
- <span data-ttu-id="14360-185">**Type**: la couleur du jeton de type.</span><span class="sxs-lookup"><span data-stu-id="14360-185">**Type**: The type token color.</span></span>
- <span data-ttu-id="14360-186">**Number**: la couleur du jeton numérique.</span><span class="sxs-lookup"><span data-stu-id="14360-186">**Number**: The number token color.</span></span>
- <span data-ttu-id="14360-187">**Membre**: la couleur du jeton de nom de membre.</span><span class="sxs-lookup"><span data-stu-id="14360-187">**Member**: The member name token color.</span></span>
- <span data-ttu-id="14360-188">**InlinePrediction**: couleur de la vue inline de la suggestion prédictive.</span><span class="sxs-lookup"><span data-stu-id="14360-188">**InlinePrediction**: The color for the inline view of the predictive suggestion.</span></span>

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

### <span data-ttu-id="14360-189">-CommandValidationHandler</span><span class="sxs-lookup"><span data-stu-id="14360-189">-CommandValidationHandler</span></span>

<span data-ttu-id="14360-190">Spécifie un **scriptblock** qui est appelé à partir de **ValidateAndAcceptLine**.</span><span class="sxs-lookup"><span data-stu-id="14360-190">Specifies a **ScriptBlock** that is called from **ValidateAndAcceptLine**.</span></span> <span data-ttu-id="14360-191">Si une exception est levée, la validation échoue et l’erreur est signalée.</span><span class="sxs-lookup"><span data-stu-id="14360-191">If an exception is thrown, validation fails and the error is reported.</span></span>

<span data-ttu-id="14360-192">Avant de lever une exception, le gestionnaire de validation peut placer le curseur au point de l’erreur pour faciliter la résolution.</span><span class="sxs-lookup"><span data-stu-id="14360-192">Before throwing an exception, the validation handler can place the cursor at the point of the error to make it easier to fix.</span></span> <span data-ttu-id="14360-193">Un gestionnaire de validation peut également modifier la ligne de commande, par exemple pour corriger les erreurs typographiques courantes.</span><span class="sxs-lookup"><span data-stu-id="14360-193">A validation handler can also change the command line, such as to correct common typographical errors.</span></span>

<span data-ttu-id="14360-194">**ValidateAndAcceptLine** est utilisé pour éviter d’encombrer votre historique avec des commandes qui ne fonctionnent pas.</span><span class="sxs-lookup"><span data-stu-id="14360-194">**ValidateAndAcceptLine** is used to avoid cluttering your history with commands that can't work.</span></span>

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

### <span data-ttu-id="14360-195">-CompletionQueryItems</span><span class="sxs-lookup"><span data-stu-id="14360-195">-CompletionQueryItems</span></span>

<span data-ttu-id="14360-196">Spécifie le nombre maximal d’éléments de saisie semi-automatique affichés sans invite.</span><span class="sxs-lookup"><span data-stu-id="14360-196">Specifies the maximum number of completion items that are shown without prompting.</span></span>

<span data-ttu-id="14360-197">Si le nombre d’éléments à afficher est supérieur à cette valeur, **PSReadLine** invite **Oui/non** avant d’afficher les éléments de saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="14360-197">If the number of items to show is greater than this value, **PSReadLine** prompts **yes/no** before displaying the completion items.</span></span>

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

### <span data-ttu-id="14360-198">-ContinuationPrompt</span><span class="sxs-lookup"><span data-stu-id="14360-198">-ContinuationPrompt</span></span>

<span data-ttu-id="14360-199">Spécifie la chaîne affichée au début des lignes suivantes lorsque l’entrée multiligne est entrée.</span><span class="sxs-lookup"><span data-stu-id="14360-199">Specifies the string displayed at the beginning of the subsequent lines when multi-line input is entered.</span></span> <span data-ttu-id="14360-200">La valeur par défaut est double signe supérieur à ( `>>` ).</span><span class="sxs-lookup"><span data-stu-id="14360-200">The default is double greater-than signs (`>>`).</span></span> <span data-ttu-id="14360-201">Une chaîne vide est valide.</span><span class="sxs-lookup"><span data-stu-id="14360-201">An empty string is valid.</span></span>

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

### <span data-ttu-id="14360-202">-DingDuration</span><span class="sxs-lookup"><span data-stu-id="14360-202">-DingDuration</span></span>

<span data-ttu-id="14360-203">Spécifie la durée du signal sonore quand **BellStyle** est défini sur **audible**.</span><span class="sxs-lookup"><span data-stu-id="14360-203">Specifies the duration of the beep when **BellStyle** is set to **Audible**.</span></span>

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

### <span data-ttu-id="14360-204">-DingTone</span><span class="sxs-lookup"><span data-stu-id="14360-204">-DingTone</span></span>

<span data-ttu-id="14360-205">Spécifie le ton en Hertz (Hz) du bip quand **BellStyle** est défini sur **audible**.</span><span class="sxs-lookup"><span data-stu-id="14360-205">Specifies the tone in Hertz (Hz) of the beep when **BellStyle** is set to **Audible**.</span></span>

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

### <span data-ttu-id="14360-206">-EditMode</span><span class="sxs-lookup"><span data-stu-id="14360-206">-EditMode</span></span>

<span data-ttu-id="14360-207">Spécifie le mode d’édition de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="14360-207">Specifies the command line editing mode.</span></span> <span data-ttu-id="14360-208">L’utilisation de ce paramètre réinitialise toutes les combinaisons de touches définies par `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="14360-208">Using this parameter resets any key bindings set by `Set-PSReadLineKeyHandler`.</span></span>

<span data-ttu-id="14360-209">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="14360-209">The valid values are as follows:</span></span>

- <span data-ttu-id="14360-210">**Windows**: les combinaisons de touches émulent PowerShell, cmd et Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="14360-210">**Windows**: Key bindings emulate PowerShell, cmd, and Visual Studio.</span></span>
- <span data-ttu-id="14360-211">**Emacs**-les combinaisons de touches émulent bash ou Emacs.</span><span class="sxs-lookup"><span data-stu-id="14360-211">**Emacs**: Key bindings emulate Bash or Emacs.</span></span>
- <span data-ttu-id="14360-212">**VI**: les combinaisons de touches émulent VI.</span><span class="sxs-lookup"><span data-stu-id="14360-212">**Vi**: Key bindings emulate Vi.</span></span>

<span data-ttu-id="14360-213">Utilisez `Get-PSReadLineKeyHandler` pour afficher les combinaisons de touches pour le **EditMode** actuellement configuré.</span><span class="sxs-lookup"><span data-stu-id="14360-213">Use `Get-PSReadLineKeyHandler` to see the key bindings for the currently configured **EditMode**.</span></span>

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

### <span data-ttu-id="14360-214">-ExtraPromptLineCount</span><span class="sxs-lookup"><span data-stu-id="14360-214">-ExtraPromptLineCount</span></span>

<span data-ttu-id="14360-215">Spécifie le nombre de lignes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="14360-215">Specifies the number of extra lines.</span></span>

<span data-ttu-id="14360-216">Si votre invite s’étend sur plusieurs lignes, spécifiez une valeur pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="14360-216">If your prompt spans more than one line, specify a value for this parameter.</span></span> <span data-ttu-id="14360-217">Utilisez cette option lorsque vous souhaitez que des lignes supplémentaires soient disponibles quand **PSReadLine** affiche l’invite après avoir affiché une sortie.</span><span class="sxs-lookup"><span data-stu-id="14360-217">Use this option when you want extra lines to be available when **PSReadLine** displays the prompt after showing some output.</span></span> <span data-ttu-id="14360-218">Par exemple, **PSReadLine** retourne une liste des saisies semi-automatiques.</span><span class="sxs-lookup"><span data-stu-id="14360-218">For example, **PSReadLine** returns a list of completions.</span></span>

<span data-ttu-id="14360-219">Cette option est requise moins que dans les versions précédentes de **PSReadLine**, mais elle est utile lorsque la `InvokePrompt` fonction est utilisée.</span><span class="sxs-lookup"><span data-stu-id="14360-219">This option is needed less than in previous versions of **PSReadLine**, but is useful when the `InvokePrompt` function is used.</span></span>

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

### <span data-ttu-id="14360-220">-HistoryNoDuplicates</span><span class="sxs-lookup"><span data-stu-id="14360-220">-HistoryNoDuplicates</span></span>

<span data-ttu-id="14360-221">Cette option contrôle le comportement de rappel.</span><span class="sxs-lookup"><span data-stu-id="14360-221">This option controls the recall behavior.</span></span> <span data-ttu-id="14360-222">Les commandes dupliquées sont toujours ajoutées au fichier d’historique.</span><span class="sxs-lookup"><span data-stu-id="14360-222">Duplicate commands are still added to the history file.</span></span>
<span data-ttu-id="14360-223">Lorsque cette option est définie, seul l’appel le plus récent s’affiche lorsque vous rappelez des commandes.</span><span class="sxs-lookup"><span data-stu-id="14360-223">When this option is set, only the most recent invocation appears when recalling commands.</span></span> <span data-ttu-id="14360-224">Les commandes répétées sont ajoutées à l’historique pour préserver le classement pendant le rappel.</span><span class="sxs-lookup"><span data-stu-id="14360-224">Repeated commands are added to history to preserve ordering during recall.</span></span> <span data-ttu-id="14360-225">Toutefois, vous ne souhaitez généralement pas voir la commande plusieurs fois lors du rappel ou de la recherche dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="14360-225">However, you typically don't want to see the command multiple times when recalling or searching the history.</span></span>

<span data-ttu-id="14360-226">Par défaut, la propriété **HistoryNoDuplicates** de l’objet global **PSConsoleReadLineOptions** a la valeur `True` .</span><span class="sxs-lookup"><span data-stu-id="14360-226">By default, the **HistoryNoDuplicates** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="14360-227">L’utilisation de cet **Paramètre_Booléen** affecte la valeur à la propriété `True` .</span><span class="sxs-lookup"><span data-stu-id="14360-227">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="14360-228">Pour modifier la valeur de la propriété, vous devez spécifier la valeur de **Paramètre_Booléen** comme suit : `-HistoryNoDuplicates:$False` .</span><span class="sxs-lookup"><span data-stu-id="14360-228">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-HistoryNoDuplicates:$False`.</span></span>

<span data-ttu-id="14360-229">À l’aide de la commande suivante, vous pouvez définir directement la valeur de la propriété :</span><span class="sxs-lookup"><span data-stu-id="14360-229">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="14360-230">-HistorySavePath</span><span class="sxs-lookup"><span data-stu-id="14360-230">-HistorySavePath</span></span>

<span data-ttu-id="14360-231">Spécifie le chemin d’accès au fichier dans lequel l’historique est enregistré.</span><span class="sxs-lookup"><span data-stu-id="14360-231">Specifies the path to the file where history is saved.</span></span> <span data-ttu-id="14360-232">Les ordinateurs exécutant des plates-formes Windows ou non Windows stockent le fichier à différents emplacements.</span><span class="sxs-lookup"><span data-stu-id="14360-232">Computers running Windows or non-Windows platforms store the file in different locations.</span></span> <span data-ttu-id="14360-233">Le nom de fichier est stocké dans une variable `$($host.Name)_history.txt` , par exemple `ConsoleHost_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="14360-233">The filename is stored in a variable `$($host.Name)_history.txt`, for example `ConsoleHost_history.txt`.</span></span>

<span data-ttu-id="14360-234">Si vous n’utilisez pas ce paramètre, le chemin d’accès par défaut est le suivant :</span><span class="sxs-lookup"><span data-stu-id="14360-234">If you don't use this parameter, the default path is as follows:</span></span>

<span data-ttu-id="14360-235">**Windows**</span><span class="sxs-lookup"><span data-stu-id="14360-235">**Windows**</span></span>

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

<span data-ttu-id="14360-236">**non-Windows**</span><span class="sxs-lookup"><span data-stu-id="14360-236">**non-Windows**</span></span>

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

### <span data-ttu-id="14360-237">-HistorySaveStyle</span><span class="sxs-lookup"><span data-stu-id="14360-237">-HistorySaveStyle</span></span>

<span data-ttu-id="14360-238">Spécifie la manière dont **PSReadLine** enregistre l’historique.</span><span class="sxs-lookup"><span data-stu-id="14360-238">Specifies how **PSReadLine** saves history.</span></span>

<span data-ttu-id="14360-239">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="14360-239">Valid values are as follows:</span></span>

- <span data-ttu-id="14360-240">**SaveIncrementally**: enregistrer l’historique après l’exécution de chaque commande et le partage entre plusieurs instances de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14360-240">**SaveIncrementally**: Save history after each command is executed and share across multiple instances of PowerShell.</span></span>
- <span data-ttu-id="14360-241">**SaveAtExit**: ajouter le fichier d’historique à la sortie de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14360-241">**SaveAtExit**: Append history file when PowerShell exits.</span></span>
- <span data-ttu-id="14360-242">**SaveNothing**: n’utilisez pas de fichier d’historique.</span><span class="sxs-lookup"><span data-stu-id="14360-242">**SaveNothing**: Don't use a history file.</span></span>

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

### <span data-ttu-id="14360-243">-HistorySearchCaseSensitive</span><span class="sxs-lookup"><span data-stu-id="14360-243">-HistorySearchCaseSensitive</span></span>

<span data-ttu-id="14360-244">Spécifie que la recherche dans l’historique respecte la casse dans des fonctions telles que **ReverseSearchHistory** ou **HistorySearchBackward**.</span><span class="sxs-lookup"><span data-stu-id="14360-244">Specifies that history searching is case-sensitive in functions like **ReverseSearchHistory** or **HistorySearchBackward**.</span></span>

<span data-ttu-id="14360-245">Par défaut, la propriété **HistorySearchCaseSensitive** de l’objet global **PSConsoleReadLineOptions** a la valeur `False` .</span><span class="sxs-lookup"><span data-stu-id="14360-245">By default, the **HistorySearchCaseSensitive** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="14360-246">L’utilisation de cet **Paramètre_Booléen** affecte la valeur à la propriété `True` .</span><span class="sxs-lookup"><span data-stu-id="14360-246">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="14360-247">Pour modifier la valeur de la propriété, vous devez spécifier la valeur de **Paramètre_Booléen** comme suit : `-HistorySearchCaseSensitive:$False` .</span><span class="sxs-lookup"><span data-stu-id="14360-247">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCaseSensitive:$False`.</span></span>

<span data-ttu-id="14360-248">À l’aide de la commande suivante, vous pouvez définir directement la valeur de la propriété :</span><span class="sxs-lookup"><span data-stu-id="14360-248">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="14360-249">-HistorySearchCursorMovesToEnd</span><span class="sxs-lookup"><span data-stu-id="14360-249">-HistorySearchCursorMovesToEnd</span></span>

<span data-ttu-id="14360-250">Indique que le curseur se déplace vers la fin des commandes que vous chargez à partir de l’historique à l’aide d’une recherche.</span><span class="sxs-lookup"><span data-stu-id="14360-250">Indicates that the cursor moves to the end of commands that you load from history by using a search.</span></span>
<span data-ttu-id="14360-251">Lorsque ce paramètre a la valeur `$False` , le curseur reste à la position où il se trouvait quand vous avez appuyé sur les flèches haut ou bas.</span><span class="sxs-lookup"><span data-stu-id="14360-251">When this parameter is set to `$False`, the cursor remains at the position it was when you pressed the up or down arrows.</span></span>

<span data-ttu-id="14360-252">Par défaut, la propriété **HistorySearchCursorMovesToEnd** de l’objet global **PSConsoleReadLineOptions** a la valeur `False` .</span><span class="sxs-lookup"><span data-stu-id="14360-252">By default, the **HistorySearchCursorMovesToEnd** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="14360-253">À l’aide de cet **Paramètre_Booléen** , affectez la valeur à la propriété `True` .</span><span class="sxs-lookup"><span data-stu-id="14360-253">Using this **SwitchParameter** set the property value to `True`.</span></span> <span data-ttu-id="14360-254">Pour modifier la valeur de la propriété, vous devez spécifier la valeur de **Paramètre_Booléen** comme suit : `-HistorySearchCursorMovesToEnd:$False` .</span><span class="sxs-lookup"><span data-stu-id="14360-254">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCursorMovesToEnd:$False`.</span></span>

<span data-ttu-id="14360-255">À l’aide de la commande suivante, vous pouvez définir directement la valeur de la propriété :</span><span class="sxs-lookup"><span data-stu-id="14360-255">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="14360-256">-MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="14360-256">-MaximumHistoryCount</span></span>

<span data-ttu-id="14360-257">Spécifie le nombre maximal de commandes à enregistrer dans l’historique **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="14360-257">Specifies the maximum number of commands to save in **PSReadLine** history.</span></span>

<span data-ttu-id="14360-258">L’historique de **PSReadLine** est séparé de l’historique PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14360-258">**PSReadLine** history is separate from PowerShell history.</span></span>

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

### <span data-ttu-id="14360-259">-MaximumKillRingCount</span><span class="sxs-lookup"><span data-stu-id="14360-259">-MaximumKillRingCount</span></span>

<span data-ttu-id="14360-260">Spécifie le nombre maximal d’éléments stockés dans l’anneau Kill.</span><span class="sxs-lookup"><span data-stu-id="14360-260">Specifies the maximum number of items stored in the kill ring.</span></span>

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

### <span data-ttu-id="14360-261">-PromptText</span><span class="sxs-lookup"><span data-stu-id="14360-261">-PromptText</span></span>

<span data-ttu-id="14360-262">En cas d’erreur d’analyse, **PSReadLine** modifie une partie de l’invite rouge.</span><span class="sxs-lookup"><span data-stu-id="14360-262">When there's a parse error, **PSReadLine** changes a part of the prompt red.</span></span> <span data-ttu-id="14360-263">**PSReadLine** analyse votre fonction d’invite pour déterminer comment modifier uniquement la couleur d’une partie de votre invite.</span><span class="sxs-lookup"><span data-stu-id="14360-263">**PSReadLine** analyzes your prompt function to determine how to change only the color of part of your prompt.</span></span> <span data-ttu-id="14360-264">Cette analyse n’est pas 100% fiable.</span><span class="sxs-lookup"><span data-stu-id="14360-264">This analysis isn't 100% reliable.</span></span>

<span data-ttu-id="14360-265">Utilisez cette option si **PSReadLine** modifie votre invite de manière inattendue.</span><span class="sxs-lookup"><span data-stu-id="14360-265">Use this option if **PSReadLine** is changing your prompt in unexpected ways.</span></span> <span data-ttu-id="14360-266">Inclut tout espace blanc de fin.</span><span class="sxs-lookup"><span data-stu-id="14360-266">Include any trailing whitespace.</span></span>

<span data-ttu-id="14360-267">Par exemple, si votre fonction d’invite ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="14360-267">For example, if your prompt function looked like the following example:</span></span>

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

<span data-ttu-id="14360-268">Ensuite, définissez :</span><span class="sxs-lookup"><span data-stu-id="14360-268">Then set:</span></span>

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

### <span data-ttu-id="14360-269">-ShowToolTips</span><span class="sxs-lookup"><span data-stu-id="14360-269">-ShowToolTips</span></span>

<span data-ttu-id="14360-270">Lorsque vous affichez les saisies semi-automatiques possibles, les info-bulles sont affichées dans la liste des saisies semi-automatiques.</span><span class="sxs-lookup"><span data-stu-id="14360-270">When displaying possible completions, tooltips are shown in the list of completions.</span></span>

<span data-ttu-id="14360-271">Cette option est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="14360-271">This option is enabled by default.</span></span> <span data-ttu-id="14360-272">Cette option n’a pas été activée par défaut dans les versions antérieures de **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="14360-272">This option wasn't enabled by default in prior versions of **PSReadLine**.</span></span> <span data-ttu-id="14360-273">Pour désactiver, définissez cette option sur `$False` .</span><span class="sxs-lookup"><span data-stu-id="14360-273">To disable, set this option to `$False`.</span></span>

<span data-ttu-id="14360-274">Par défaut, la propriété **ShowToolTips** de l’objet global **PSConsoleReadLineOptions** a la valeur `True` .</span><span class="sxs-lookup"><span data-stu-id="14360-274">By default, the **ShowToolTips** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="14360-275">L’utilisation de cet **Paramètre_Booléen** affecte la valeur à la propriété `True` .</span><span class="sxs-lookup"><span data-stu-id="14360-275">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="14360-276">Pour modifier la valeur de la propriété, vous devez spécifier la valeur de **Paramètre_Booléen** comme suit : `-ShowToolTips:$False` .</span><span class="sxs-lookup"><span data-stu-id="14360-276">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-ShowToolTips:$False`.</span></span>

<span data-ttu-id="14360-277">À l’aide de la commande suivante, vous pouvez définir directement la valeur de la propriété :</span><span class="sxs-lookup"><span data-stu-id="14360-277">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="14360-278">-ViModeChangeHandler</span><span class="sxs-lookup"><span data-stu-id="14360-278">-ViModeChangeHandler</span></span>

<span data-ttu-id="14360-279">Lorsque **ViModeIndicator** a la valeur `Script` , le bloc de script fourni est appelé chaque fois que le mode change.</span><span class="sxs-lookup"><span data-stu-id="14360-279">When the **ViModeIndicator** is set to `Script`, the script block provided will be invoked every time the mode changes.</span></span> <span data-ttu-id="14360-280">Le bloc de script est fourni avec un argument de type `ViMode` .</span><span class="sxs-lookup"><span data-stu-id="14360-280">The script block is provided one argument of type `ViMode`.</span></span>

<span data-ttu-id="14360-281">Ce paramètre a été introduit dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="14360-281">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="14360-282">-ViModeIndicator</span><span class="sxs-lookup"><span data-stu-id="14360-282">-ViModeIndicator</span></span>

<span data-ttu-id="14360-283">Cette option définit l’indication visuelle pour le mode **VI** actuel.</span><span class="sxs-lookup"><span data-stu-id="14360-283">This option sets the visual indication for the current **Vi** mode.</span></span> <span data-ttu-id="14360-284">Mode insertion ou mode commande.</span><span class="sxs-lookup"><span data-stu-id="14360-284">Either insert mode or command mode.</span></span>

<span data-ttu-id="14360-285">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="14360-285">The valid values are as follows:</span></span>

- <span data-ttu-id="14360-286">**None**: il n’existe aucune indication.</span><span class="sxs-lookup"><span data-stu-id="14360-286">**None**: There's no indication.</span></span>
- <span data-ttu-id="14360-287">**Prompt**: l’invite change de couleur.</span><span class="sxs-lookup"><span data-stu-id="14360-287">**Prompt**: The prompt changes color.</span></span>
- <span data-ttu-id="14360-288">**Curseur**: le curseur change de taille.</span><span class="sxs-lookup"><span data-stu-id="14360-288">**Cursor**: The cursor changes size.</span></span>
- <span data-ttu-id="14360-289">**Script**: le texte spécifié par l’utilisateur est imprimé.</span><span class="sxs-lookup"><span data-stu-id="14360-289">**Script**: User-specified text is printed.</span></span>

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

### <span data-ttu-id="14360-290">-WordDelimiters</span><span class="sxs-lookup"><span data-stu-id="14360-290">-WordDelimiters</span></span>

<span data-ttu-id="14360-291">Spécifie les caractères qui délimitent les mots pour des fonctions telles que **ForwardWord** ou **KillWord**.</span><span class="sxs-lookup"><span data-stu-id="14360-291">Specifies the characters that delimit words for functions like **ForwardWord** or **KillWord**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: ;:,.[]{}()/\|^&*-=+'"---
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14360-292">-PredictionSource</span><span class="sxs-lookup"><span data-stu-id="14360-292">-PredictionSource</span></span>

<span data-ttu-id="14360-293">Spécifie la source de PSReadLine pour obtenir des suggestions prédictives.</span><span class="sxs-lookup"><span data-stu-id="14360-293">Specifies the source for PSReadLine to get predictive suggestions.</span></span>

<span data-ttu-id="14360-294">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="14360-294">Valid values are:</span></span>

- <span data-ttu-id="14360-295">**Aucun** : désactive la fonctionnalité IntelliSense prédictive (par défaut).</span><span class="sxs-lookup"><span data-stu-id="14360-295">**None** - disable the predictive IntelliSense feature (default).</span></span>
<span data-ttu-id="14360-296">-\`**Historique** : activez la fonctionnalité IntelliSense prédictive et utilisez l’historique PSReadLine comme seule source.</span><span class="sxs-lookup"><span data-stu-id="14360-296">-\`**History** - enable the predictive IntelliSense feature and use the PSReadLine history as the only source.</span></span>
- <span data-ttu-id="14360-297">**Plug-in** : activez la fonctionnalité IntelliSense prédictive et utilisez les plug-ins ( `CommandPrediction` ) comme seule source.</span><span class="sxs-lookup"><span data-stu-id="14360-297">**Plugin** - enable the predictive IntelliSense feature and use the plugins (`CommandPrediction`) as the only source.</span></span> <span data-ttu-id="14360-298">Cette valeur a été ajoutée dans PSReadLine 2.2.0</span><span class="sxs-lookup"><span data-stu-id="14360-298">This value was added in PSReadLine 2.2.0</span></span>
- <span data-ttu-id="14360-299">**HistoryAndPlugin** : activez la fonctionnalité IntelliSense prédictive et utilisez l’historique et le plug-in comme sources.</span><span class="sxs-lookup"><span data-stu-id="14360-299">**HistoryAndPlugin** - enable the predictive IntelliSense feature and use both history and plugin as the sources.</span></span> <span data-ttu-id="14360-300">Cette valeur a été ajoutée dans PSReadLine 2.2.0</span><span class="sxs-lookup"><span data-stu-id="14360-300">This value was added in PSReadLine 2.2.0</span></span>

```yaml
Type: Microsoft.PowerShell.PredictionSource
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14360-301">-PredictionViewStyle</span><span class="sxs-lookup"><span data-stu-id="14360-301">-PredictionViewStyle</span></span>

<span data-ttu-id="14360-302">Définit le style d’affichage du texte prédictif.</span><span class="sxs-lookup"><span data-stu-id="14360-302">Sets the style for the display of the predictive text.</span></span> <span data-ttu-id="14360-303">La valeur par défaut est **InlineView**.</span><span class="sxs-lookup"><span data-stu-id="14360-303">The default is **InlineView**.</span></span>

- <span data-ttu-id="14360-304">**InlineView** : style actuel actuel, similaire à celui de poisson Shell et zsh.</span><span class="sxs-lookup"><span data-stu-id="14360-304">**InlineView** - the style as existing today, similar as in fish shell and zsh.</span></span> <span data-ttu-id="14360-305">(par défaut)</span><span class="sxs-lookup"><span data-stu-id="14360-305">(default)</span></span>
- <span data-ttu-id="14360-306">**ListView** : les suggestions s’affichent dans une liste déroulante, et les utilisateurs peuvent sélectionner en utilisant les <kbd>flèches haut</kbd> et <kbd>bas</kbd>.</span><span class="sxs-lookup"><span data-stu-id="14360-306">**ListView** - suggestions are rendered in a drop down list, and users can select using <kbd>UpArrow</kbd> and <kbd>DownArrow</kbd>.</span></span>

<span data-ttu-id="14360-307">Ce paramètre a été ajouté dans PSReadLine 2.2.0</span><span class="sxs-lookup"><span data-stu-id="14360-307">This parameter was added in PSReadLine 2.2.0</span></span>

```yaml
Type: Microsoft.PowerShell.PredictionViewStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: InlineView
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14360-308">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="14360-308">CommonParameters</span></span>

<span data-ttu-id="14360-309">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="14360-309">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="14360-310">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="14360-310">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="14360-311">Entrées</span><span class="sxs-lookup"><span data-stu-id="14360-311">Inputs</span></span>

### <span data-ttu-id="14360-312">None</span><span class="sxs-lookup"><span data-stu-id="14360-312">None</span></span>

<span data-ttu-id="14360-313">Vous ne pouvez pas diriger d’objets vers `Set-PSReadLineOption.`</span><span class="sxs-lookup"><span data-stu-id="14360-313">You cannot pipe objects to `Set-PSReadLineOption.`</span></span>

## <span data-ttu-id="14360-314">Sorties</span><span class="sxs-lookup"><span data-stu-id="14360-314">Outputs</span></span>

### <span data-ttu-id="14360-315">None</span><span class="sxs-lookup"><span data-stu-id="14360-315">None</span></span>

<span data-ttu-id="14360-316">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="14360-316">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="14360-317">Notes</span><span class="sxs-lookup"><span data-stu-id="14360-317">Notes</span></span>

## <span data-ttu-id="14360-318">Liens connexes</span><span class="sxs-lookup"><span data-stu-id="14360-318">Related links</span></span>

[<span data-ttu-id="14360-319">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="14360-319">about_PSReadLine</span></span>](./About/about_PSReadLine.md)

[<span data-ttu-id="14360-320">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="14360-320">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="14360-321">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="14360-321">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="14360-322">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="14360-322">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="14360-323">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="14360-323">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
