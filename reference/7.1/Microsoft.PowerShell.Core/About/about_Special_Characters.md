---
description: Décrit les séquences de caractères spéciaux qui contrôlent la façon dont PowerShell interprète les caractères suivants dans la séquence.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_special_characters?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Special_Characters
ms.openlocfilehash: 6856d903276f5cbe4db222ac4c5d64ce6939413e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207806"
---
# <a name="about-special-characters"></a><span data-ttu-id="1e804-104">À propos des caractères spéciaux</span><span class="sxs-lookup"><span data-stu-id="1e804-104">About Special Characters</span></span>

## <a name="short-description"></a><span data-ttu-id="1e804-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="1e804-105">Short description</span></span>

<span data-ttu-id="1e804-106">Décrit les séquences de caractères spéciaux qui contrôlent la façon dont PowerShell interprète les caractères suivants dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="1e804-106">Describes the special character sequences that control how PowerShell interprets the next characters in the sequence.</span></span>

## <a name="long-description"></a><span data-ttu-id="1e804-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="1e804-107">Long description</span></span>

<span data-ttu-id="1e804-108">PowerShell prend en charge un ensemble de séquences de caractères spéciaux utilisés pour représenter des caractères qui ne font pas partie du jeu de caractères standard.</span><span class="sxs-lookup"><span data-stu-id="1e804-108">PowerShell supports a set of special character sequences that are used to represent characters that aren't part of the standard character set.</span></span> <span data-ttu-id="1e804-109">Les séquences sont communément appelées _séquences d’échappement_ .</span><span class="sxs-lookup"><span data-stu-id="1e804-109">The sequences are commonly known as _escape sequences_ .</span></span>

<span data-ttu-id="1e804-110">Les séquences d’échappement commencent par le caractère « accent grave » (ASCII 96) et respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="1e804-110">Escape sequences begin with the backtick character, known as the grave accent (ASCII 96), and are case-sensitive.</span></span> <span data-ttu-id="1e804-111">Le caractère d’échappement est également appelé _caractère d’échappement_ .</span><span class="sxs-lookup"><span data-stu-id="1e804-111">The backtick character can also be referred to as the _escape character_ .</span></span>

<span data-ttu-id="1e804-112">Les séquences d’échappement sont interprétées uniquement lorsqu’elles sont contenues dans des chaînes entre guillemets ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="1e804-112">Escape sequences are only interpreted when contained in double-quoted (`"`) strings.</span></span>

<span data-ttu-id="1e804-113">PowerShell reconnaît ces séquences d’échappement :</span><span class="sxs-lookup"><span data-stu-id="1e804-113">PowerShell recognizes these escape sequences:</span></span>

|  <span data-ttu-id="1e804-114">Séquence</span><span class="sxs-lookup"><span data-stu-id="1e804-114">Sequence</span></span>   |       <span data-ttu-id="1e804-115">Description</span><span class="sxs-lookup"><span data-stu-id="1e804-115">Description</span></span>       |
| ----------- | ----------------------- |
| `` `0 ``    | <span data-ttu-id="1e804-116">Null</span><span class="sxs-lookup"><span data-stu-id="1e804-116">Null</span></span>                    |
| `` `a ``    | <span data-ttu-id="1e804-117">Alerte</span><span class="sxs-lookup"><span data-stu-id="1e804-117">Alert</span></span>                   |
| `` `b ``    | <span data-ttu-id="1e804-118">Retour arrière</span><span class="sxs-lookup"><span data-stu-id="1e804-118">Backspace</span></span>               |
| `` `e ``    | <span data-ttu-id="1e804-119">Caractère d'échappement</span><span class="sxs-lookup"><span data-stu-id="1e804-119">Escape</span></span>                  |
| `` `f ``    | <span data-ttu-id="1e804-120">Saut de page</span><span class="sxs-lookup"><span data-stu-id="1e804-120">Form feed</span></span>               |
| `` `n ``    | <span data-ttu-id="1e804-121">Nouvelle ligne</span><span class="sxs-lookup"><span data-stu-id="1e804-121">New line</span></span>                |
| `` `r ``    | <span data-ttu-id="1e804-122">Retour chariot</span><span class="sxs-lookup"><span data-stu-id="1e804-122">Carriage return</span></span>         |
| `` `t ``    | <span data-ttu-id="1e804-123">Tabulation horizontale</span><span class="sxs-lookup"><span data-stu-id="1e804-123">Horizontal tab</span></span>          |
| `` `u{x} `` | <span data-ttu-id="1e804-124">Séquence d’échappement Unicode</span><span class="sxs-lookup"><span data-stu-id="1e804-124">Unicode escape sequence</span></span> |
| `` `v ``    | <span data-ttu-id="1e804-125">Tabulation verticale</span><span class="sxs-lookup"><span data-stu-id="1e804-125">Vertical tab</span></span>            |

<span data-ttu-id="1e804-126">PowerShell a également un jeton spécial pour marquer l’endroit où vous souhaitez que l’analyse s’arrête.</span><span class="sxs-lookup"><span data-stu-id="1e804-126">PowerShell also has a special token to mark where you want parsing to stop.</span></span> <span data-ttu-id="1e804-127">Tous les caractères qui suivent ce jeton sont utilisés comme valeurs littérales qui ne sont pas interprétées.</span><span class="sxs-lookup"><span data-stu-id="1e804-127">All characters that follow this token are used as literal values that aren't interpreted.</span></span>

<span data-ttu-id="1e804-128">Jeton d’analyse spécial :</span><span class="sxs-lookup"><span data-stu-id="1e804-128">Special parsing token:</span></span>

| <span data-ttu-id="1e804-129">Séquence</span><span class="sxs-lookup"><span data-stu-id="1e804-129">Sequence</span></span> |            <span data-ttu-id="1e804-130">Description</span><span class="sxs-lookup"><span data-stu-id="1e804-130">Description</span></span>             |
| -------- | ---------------------------------- |
| `--%`    | <span data-ttu-id="1e804-131">Arrêter l’analyse de tout ce qui suit</span><span class="sxs-lookup"><span data-stu-id="1e804-131">Stop parsing anything that follows</span></span> |

## <a name="null-0"></a><span data-ttu-id="1e804-132">Null (' 0)</span><span class="sxs-lookup"><span data-stu-id="1e804-132">Null (\`0)</span></span>

<span data-ttu-id="1e804-133">Le caractère null ( `` `0 `` ) apparaît comme un espace vide dans la sortie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1e804-133">The null (`` `0 ``) character appears as an empty space in PowerShell output.</span></span>
<span data-ttu-id="1e804-134">Cette fonctionnalité vous permet d’utiliser PowerShell pour lire et traiter des fichiers texte qui utilisent des caractères null, tels que la terminaison de chaîne ou les indicateurs de fin d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="1e804-134">This functionality allows you to use PowerShell to read and process text files that use null characters, such as string termination or record termination indicators.</span></span> <span data-ttu-id="1e804-135">Le caractère spécial NULL n’est pas équivalent à la `$null` variable, qui stocke une valeur **null** .</span><span class="sxs-lookup"><span data-stu-id="1e804-135">The null special character isn't equivalent to the `$null` variable, which stores a **null** value.</span></span>

## <a name="alert-a"></a><span data-ttu-id="1e804-136">Alerte ('a')</span><span class="sxs-lookup"><span data-stu-id="1e804-136">Alert (\`a)</span></span>

<span data-ttu-id="1e804-137">Le caractère alerte ( `` `a `` ) envoie un signal sonore au haut-parleur de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1e804-137">The alert (`` `a ``) character sends a beep signal to the computer's speaker.</span></span>
<span data-ttu-id="1e804-138">Vous pouvez utiliser ce caractère pour avertir l’utilisateur d’une action imminente.</span><span class="sxs-lookup"><span data-stu-id="1e804-138">You can use this character to warn a user about an impending action.</span></span> <span data-ttu-id="1e804-139">L’exemple suivant envoie deux signaux sonores au haut-parleur de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1e804-139">The following example sends two beep signals to the local computer's speaker.</span></span>

```powershell
for ($i = 0; $i -le 1; $i++){"`a"}
```

## <a name="backspace-b"></a><span data-ttu-id="1e804-140">Retour arrière ('b)</span><span class="sxs-lookup"><span data-stu-id="1e804-140">Backspace (\`b)</span></span>

<span data-ttu-id="1e804-141">Le `` `b `` caractère retour arrière () déplace le curseur d’un caractère vers l’arrière, mais il ne supprime aucun caractère.</span><span class="sxs-lookup"><span data-stu-id="1e804-141">The backspace (`` `b ``) character moves the cursor back one character, but it doesn't delete any characters.</span></span>

<span data-ttu-id="1e804-142">L’exemple écrit le mot **sauvegarde** , puis replace le curseur à deux reprises.</span><span class="sxs-lookup"><span data-stu-id="1e804-142">The example writes the word **backup** and then moves the cursor back twice.</span></span>
<span data-ttu-id="1e804-143">Ensuite, à la nouvelle position, écrit un espace suivi du mot **out** .</span><span class="sxs-lookup"><span data-stu-id="1e804-143">Then, at the new position, writes a space followed by the word **out** .</span></span>

```powershell
"backup`b`b out"
```

```Output
back out
```

## <a name="escape-e"></a><span data-ttu-id="1e804-144">Escape ('e)</span><span class="sxs-lookup"><span data-stu-id="1e804-144">Escape (\`e)</span></span>

<span data-ttu-id="1e804-145">Le `` `e `` caractère d’échappement () est le plus souvent utilisé pour spécifier une séquence de terminaux virtuels (séquence d’échappement ANSI) qui modifie la couleur du texte et d’autres attributs de texte tels que le gras et le soulignement.</span><span class="sxs-lookup"><span data-stu-id="1e804-145">The escape (`` `e ``) character is most commonly used to specify a virtual terminal sequence (ANSI escape sequence) that modifies the color of text and other text attributes such as bolding and underlining.</span></span> <span data-ttu-id="1e804-146">Ces séquences peuvent également être utilisées pour le positionnement et le défilement des curseurs.</span><span class="sxs-lookup"><span data-stu-id="1e804-146">These sequences can also be used for cursor positioning and scrolling.</span></span> <span data-ttu-id="1e804-147">L’hôte PowerShell doit prendre en charge les séquences de terminaux virtuels.</span><span class="sxs-lookup"><span data-stu-id="1e804-147">The PowerShell host must support virtual terminal sequences.</span></span> <span data-ttu-id="1e804-148">Vous pouvez vérifier la valeur booléenne de `$Host.UI.SupportsVirtualTerminal` pour déterminer si ces séquences ANSI sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="1e804-148">You can check the boolean value of `$Host.UI.SupportsVirtualTerminal` to determine if these ANSI sequences are supported.</span></span>

<span data-ttu-id="1e804-149">Pour plus d’informations sur les séquences d’échappement ANSI, consultez [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span><span class="sxs-lookup"><span data-stu-id="1e804-149">For more information about ANSI escape sequences, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

<span data-ttu-id="1e804-150">L’exemple suivant génère le texte avec une couleur de premier plan verte.</span><span class="sxs-lookup"><span data-stu-id="1e804-150">The following example outputs text with a green foreground color.</span></span>

```powershell
$fgColor = 32 # green
"`e[${fgColor}mGreen text`e[0m"
```

```Output
Green text
```

## <a name="form-feed-f"></a><span data-ttu-id="1e804-151">Flux de formulaire ('f')</span><span class="sxs-lookup"><span data-stu-id="1e804-151">Form feed (\`f)</span></span>

<span data-ttu-id="1e804-152">Le caractère de saut de `` `f `` page () est une instruction d’impression qui éjecte la page actuelle et poursuit l’impression sur la page suivante.</span><span class="sxs-lookup"><span data-stu-id="1e804-152">The form feed (`` `f ``) character is a print instruction that ejects the current page and continues printing on the next page.</span></span> <span data-ttu-id="1e804-153">Le caractère de saut de formulaire affecte uniquement les documents imprimés.</span><span class="sxs-lookup"><span data-stu-id="1e804-153">The form feed character only affects printed documents.</span></span> <span data-ttu-id="1e804-154">Elle n’affecte pas la sortie écran.</span><span class="sxs-lookup"><span data-stu-id="1e804-154">It doesn't affect screen output.</span></span>

## <a name="new-line-n"></a><span data-ttu-id="1e804-155">Nouvelle ligne ('n)</span><span class="sxs-lookup"><span data-stu-id="1e804-155">New line (\`n)</span></span>

<span data-ttu-id="1e804-156">Le caractère de nouvelle ligne ( `` `n `` ) insère un saut de ligne immédiatement après le caractère.</span><span class="sxs-lookup"><span data-stu-id="1e804-156">The new line (`` `n ``) character inserts a line break immediately after the character.</span></span>

<span data-ttu-id="1e804-157">Cet exemple montre comment utiliser le caractère de nouvelle ligne pour créer des sauts de ligne dans une `Write-Host` commande.</span><span class="sxs-lookup"><span data-stu-id="1e804-157">This example shows how to use the new line character to create line breaks in a `Write-Host` command.</span></span>

```powershell
"There are two line breaks to create a blank line`n`nbetween the words."
```

```Output
There are two line breaks to create a blank line

between the words.
```

## <a name="carriage-return-r"></a><span data-ttu-id="1e804-158">Retour chariot ('r)</span><span class="sxs-lookup"><span data-stu-id="1e804-158">Carriage return (\`r)</span></span>

<span data-ttu-id="1e804-159">Le caractère retour chariot ( `` `r `` ) déplace le curseur de sortie au début de la ligne active et poursuit l’écriture.</span><span class="sxs-lookup"><span data-stu-id="1e804-159">The carriage return (`` `r ``) character moves the output cursor to the beginning of the current line and continues writing.</span></span> <span data-ttu-id="1e804-160">Tous les caractères de la ligne active sont remplacés.</span><span class="sxs-lookup"><span data-stu-id="1e804-160">Any characters on the current line are overwritten.</span></span>

<span data-ttu-id="1e804-161">Dans cet exemple, le texte avant le retour chariot est remplacé.</span><span class="sxs-lookup"><span data-stu-id="1e804-161">In this example, the text before the carriage return is overwritten.</span></span>

```powershell
Write-Host "These characters are overwritten.`rI want this text instead "
```

<span data-ttu-id="1e804-162">Notez que le texte avant le `` `r `` caractère n’est pas supprimé, il est remplacé.</span><span class="sxs-lookup"><span data-stu-id="1e804-162">Notice that the text before the `` `r `` character is not deleted, it is overwritten.</span></span>

```Output
I want this text instead written.
```

## <a name="horizontal-tab-t"></a><span data-ttu-id="1e804-163">Tabulation horizontale (t)</span><span class="sxs-lookup"><span data-stu-id="1e804-163">Horizontal tab (\`t)</span></span>

<span data-ttu-id="1e804-164">Le caractère de tabulation horizontale ( `` `t `` ) passe au taquet de tabulation suivant et poursuit l’écriture à ce stade.</span><span class="sxs-lookup"><span data-stu-id="1e804-164">The horizontal tab (`` `t ``) character advances to the next tab stop and continues writing at that point.</span></span> <span data-ttu-id="1e804-165">Par défaut, la console PowerShell a un taquet de tabulation à chaque huitième espace.</span><span class="sxs-lookup"><span data-stu-id="1e804-165">By default, the PowerShell console has a tab stop at every eighth space.</span></span>

<span data-ttu-id="1e804-166">Cet exemple insère deux onglets entre chaque colonne.</span><span class="sxs-lookup"><span data-stu-id="1e804-166">This example inserts two tabs between each column.</span></span>

```powershell
"Column1`t`tColumn2`t`tColumn3"
```

```Output
Column1         Column2         Column3
```

## <a name="unicode-character-ux"></a><span data-ttu-id="1e804-167">Caractère Unicode ('u {x}]</span><span class="sxs-lookup"><span data-stu-id="1e804-167">Unicode character (\`u{x})</span></span>

<span data-ttu-id="1e804-168">La séquence d’échappement Unicode ( `` `u{x} `` ) vous permet de spécifier n’importe quel caractère Unicode à l’aide de la représentation hexadécimale de son point de code.</span><span class="sxs-lookup"><span data-stu-id="1e804-168">The Unicode escape sequence (`` `u{x} ``) allows you to specify any Unicode character by the hexadecimal representation of its code point.</span></span> <span data-ttu-id="1e804-169">Cela comprend les caractères Unicode au-dessus du plan multilingue de base (>), y `0xFFFF` compris les caractères Emoji tels que le caractère **pouce** ( `` `u{1F44D} `` ).</span><span class="sxs-lookup"><span data-stu-id="1e804-169">This includes Unicode characters above the Basic Multilingual Plane (> `0xFFFF`) which includes emoji characters such as the **thumbs up** (`` `u{1F44D} ``) character.</span></span> <span data-ttu-id="1e804-170">La séquence d’échappement Unicode requiert au moins un chiffre hexadécimal et prend en charge jusqu’à six chiffres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="1e804-170">The Unicode escape sequence requires at least one hexadecimal digit and supports up to six hexadecimal digits.</span></span> <span data-ttu-id="1e804-171">La valeur hexadécimale maximale pour la séquence est `10FFFF` .</span><span class="sxs-lookup"><span data-stu-id="1e804-171">The maximum hexadecimal value for the sequence is `10FFFF`.</span></span>

<span data-ttu-id="1e804-172">Cet exemple génère le symbole de **flèche vers le bas** (&#x2195;).</span><span class="sxs-lookup"><span data-stu-id="1e804-172">This example outputs the **up down arrow** (&#x2195;) symbol.</span></span>

```powershell
"`u{2195}"
```

## <a name="vertical-tab-v"></a><span data-ttu-id="1e804-173">Tabulation verticale ('v)</span><span class="sxs-lookup"><span data-stu-id="1e804-173">Vertical tab (\`v)</span></span>

<span data-ttu-id="1e804-174">Le caractère de tabulation horizontale ( `` `v `` ) passe au taquet de tabulation vertical suivant et écrit la sortie restante à ce stade.</span><span class="sxs-lookup"><span data-stu-id="1e804-174">The horizontal tab (`` `v ``) character advances to the next vertical tab stop and writes the remaining output at that point.</span></span> <span data-ttu-id="1e804-175">Cela n’a aucun effet dans la console Windows par défaut.</span><span class="sxs-lookup"><span data-stu-id="1e804-175">This has no effect in the default Windows console.</span></span>

```powershell
Write-Host "There is a vertical tab`vbetween the words."
```

<span data-ttu-id="1e804-176">L’exemple suivant illustre la sortie que vous obtiendriez sur une imprimante ou dans un autre hôte de console.</span><span class="sxs-lookup"><span data-stu-id="1e804-176">The following example shows the output you would get on a printer or in a different console host.</span></span>

```Output
There is a vertical tab
                       between the words.
```

## <a name="stop-parsing-token---"></a><span data-ttu-id="1e804-177">Jeton d’analyse d’arrêt (--%)</span><span class="sxs-lookup"><span data-stu-id="1e804-177">Stop-parsing token (--%)</span></span>

<span data-ttu-id="1e804-178">Le jeton Stop-Analysing ( `--%` ) empêche PowerShell d’interpréter les chaînes comme des commandes et des expressions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1e804-178">The stop-parsing (`--%`) token prevents PowerShell from interpreting strings as PowerShell commands and expressions.</span></span> <span data-ttu-id="1e804-179">Cela permet de transmettre ces chaînes à d’autres programmes pour les interpréter.</span><span class="sxs-lookup"><span data-stu-id="1e804-179">This allows those strings to be passed to other programs for interpretation.</span></span>

<span data-ttu-id="1e804-180">Placez le jeton d’analyse d’arrêt après le nom du programme et avant les arguments du programme qui peuvent provoquer des erreurs.</span><span class="sxs-lookup"><span data-stu-id="1e804-180">Place the stop-parsing token after the program name and before program arguments that might cause errors.</span></span>

<span data-ttu-id="1e804-181">Dans cet exemple, la `Icacls` commande utilise le jeton d’analyse d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="1e804-181">In this example, the `Icacls` command uses the stop-parsing token.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="1e804-182">PowerShell envoie la chaîne suivante à `Icacls` .</span><span class="sxs-lookup"><span data-stu-id="1e804-182">PowerShell sends the following string to `Icacls`.</span></span>

```
X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="1e804-183">Voici un autre exemple.</span><span class="sxs-lookup"><span data-stu-id="1e804-183">Here is another example.</span></span> <span data-ttu-id="1e804-184">La fonction **showArgs** génère les valeurs qui lui sont passées.</span><span class="sxs-lookup"><span data-stu-id="1e804-184">The **showArgs** function outputs the values passed to it.</span></span> <span data-ttu-id="1e804-185">Dans cet exemple, nous passons `$HOME` à deux fois la variable nommée à la fonction.</span><span class="sxs-lookup"><span data-stu-id="1e804-185">In this example, we pass the variable named `$HOME` to the function twice.</span></span>

```powershell
function showArgs {
  "`$args = " + ($args -join '|')
}

showArgs $HOME --% $HOME
```

Dans la sortie, vous pouvez voir que, pour le premier paramètre, la variable `$HOME` est interprétée par PowerShell afin que la valeur de la variable soit transmise à la fonction. <span data-ttu-id="1e804-187">La deuxième utilisation de `$HOME` vient après le jeton d’analyse d’arrêt, donc la chaîne « $Home » est transmise à la fonction sans interprétation.</span><span class="sxs-lookup"><span data-stu-id="1e804-187">The second use of `$HOME` comes after the stop-parsing token, so the string "$HOME" is passed to the function without interpretation.</span></span>

```Output
$args = C:\Users\username|--%|$HOME
```

<span data-ttu-id="1e804-188">Pour plus d’informations sur le jeton d’analyse d’arrêt, consultez [about_Parsing](about_Parsing.md).</span><span class="sxs-lookup"><span data-stu-id="1e804-188">For more information about the stop-parsing token, see [about_Parsing](about_Parsing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1e804-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e804-189">See also</span></span>

[<span data-ttu-id="1e804-190">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="1e804-190">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
