---
description: Décrit les séquences de caractères spéciaux qui contrôlent la façon dont PowerShell interprète les caractères suivants dans la séquence.
Locale: en-US
ms.date: 04/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_special_characters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Special_Characters
ms.openlocfilehash: c642bc69d9e67bd945e5687d7f7c35e039062194
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598166"
---
# <a name="about-special-characters"></a><span data-ttu-id="717d0-103">À propos des caractères spéciaux</span><span class="sxs-lookup"><span data-stu-id="717d0-103">About Special Characters</span></span>

## <a name="short-description"></a><span data-ttu-id="717d0-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="717d0-104">Short description</span></span>

<span data-ttu-id="717d0-105">Décrit les séquences de caractères spéciaux qui contrôlent la façon dont PowerShell interprète les caractères suivants dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="717d0-105">Describes the special character sequences that control how PowerShell interprets the next characters in the sequence.</span></span>

## <a name="long-description"></a><span data-ttu-id="717d0-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="717d0-106">Long description</span></span>

<span data-ttu-id="717d0-107">PowerShell prend en charge un ensemble de séquences de caractères spéciaux utilisés pour représenter des caractères qui ne font pas partie du jeu de caractères standard.</span><span class="sxs-lookup"><span data-stu-id="717d0-107">PowerShell supports a set of special character sequences that are used to represent characters that aren't part of the standard character set.</span></span> <span data-ttu-id="717d0-108">Les séquences sont communément appelées _séquences d’échappement_.</span><span class="sxs-lookup"><span data-stu-id="717d0-108">The sequences are commonly known as _escape sequences_.</span></span>

<span data-ttu-id="717d0-109">Les séquences d’échappement commencent par le caractère « accent grave » (ASCII 96) et respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="717d0-109">Escape sequences begin with the backtick character, known as the grave accent (ASCII 96), and are case-sensitive.</span></span> <span data-ttu-id="717d0-110">Le caractère d’échappement est également appelé _caractère d’échappement_.</span><span class="sxs-lookup"><span data-stu-id="717d0-110">The backtick character can also be referred to as the _escape character_.</span></span>

<span data-ttu-id="717d0-111">Les séquences d’échappement sont interprétées uniquement lorsqu’elles sont contenues dans des chaînes entre guillemets ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="717d0-111">Escape sequences are only interpreted when contained in double-quoted (`"`) strings.</span></span>

<span data-ttu-id="717d0-112">PowerShell reconnaît ces séquences d’échappement :</span><span class="sxs-lookup"><span data-stu-id="717d0-112">PowerShell recognizes these escape sequences:</span></span>

|  <span data-ttu-id="717d0-113">Séquence</span><span class="sxs-lookup"><span data-stu-id="717d0-113">Sequence</span></span>   |       <span data-ttu-id="717d0-114">Description</span><span class="sxs-lookup"><span data-stu-id="717d0-114">Description</span></span>       |
| ----------- | ----------------------- |
| `` `0 ``    | <span data-ttu-id="717d0-115">Null</span><span class="sxs-lookup"><span data-stu-id="717d0-115">Null</span></span>                    |
| `` `a ``    | <span data-ttu-id="717d0-116">Alerte</span><span class="sxs-lookup"><span data-stu-id="717d0-116">Alert</span></span>                   |
| `` `b ``    | <span data-ttu-id="717d0-117">Retour arrière</span><span class="sxs-lookup"><span data-stu-id="717d0-117">Backspace</span></span>               |
| `` `e ``    | <span data-ttu-id="717d0-118">Caractère d'échappement</span><span class="sxs-lookup"><span data-stu-id="717d0-118">Escape</span></span>                  |
| `` `f ``    | <span data-ttu-id="717d0-119">Saut de page</span><span class="sxs-lookup"><span data-stu-id="717d0-119">Form feed</span></span>               |
| `` `n ``    | <span data-ttu-id="717d0-120">Nouvelle ligne</span><span class="sxs-lookup"><span data-stu-id="717d0-120">New line</span></span>                |
| `` `r ``    | <span data-ttu-id="717d0-121">Retour chariot</span><span class="sxs-lookup"><span data-stu-id="717d0-121">Carriage return</span></span>         |
| `` `t ``    | <span data-ttu-id="717d0-122">Tabulation horizontale</span><span class="sxs-lookup"><span data-stu-id="717d0-122">Horizontal tab</span></span>          |
| `` `u{x} `` | <span data-ttu-id="717d0-123">Séquence d’échappement Unicode</span><span class="sxs-lookup"><span data-stu-id="717d0-123">Unicode escape sequence</span></span> |
| `` `v ``    | <span data-ttu-id="717d0-124">Tabulation verticale</span><span class="sxs-lookup"><span data-stu-id="717d0-124">Vertical tab</span></span>            |

<span data-ttu-id="717d0-125">PowerShell a également un jeton spécial pour marquer l’endroit où vous souhaitez que l’analyse s’arrête.</span><span class="sxs-lookup"><span data-stu-id="717d0-125">PowerShell also has a special token to mark where you want parsing to stop.</span></span> <span data-ttu-id="717d0-126">Tous les caractères qui suivent ce jeton sont utilisés comme valeurs littérales qui ne sont pas interprétées.</span><span class="sxs-lookup"><span data-stu-id="717d0-126">All characters that follow this token are used as literal values that aren't interpreted.</span></span>

<span data-ttu-id="717d0-127">Jeton d’analyse spécial :</span><span class="sxs-lookup"><span data-stu-id="717d0-127">Special parsing token:</span></span>

| <span data-ttu-id="717d0-128">Séquence</span><span class="sxs-lookup"><span data-stu-id="717d0-128">Sequence</span></span> |            <span data-ttu-id="717d0-129">Description</span><span class="sxs-lookup"><span data-stu-id="717d0-129">Description</span></span>             |
| -------- | ---------------------------------- |
| `--%`    | <span data-ttu-id="717d0-130">Arrêter l’analyse de tout ce qui suit</span><span class="sxs-lookup"><span data-stu-id="717d0-130">Stop parsing anything that follows</span></span> |

## <a name="null-0"></a><span data-ttu-id="717d0-131">Null (' 0)</span><span class="sxs-lookup"><span data-stu-id="717d0-131">Null (\`0)</span></span>

<span data-ttu-id="717d0-132">Le caractère null ( `` `0 `` ) apparaît comme un espace vide dans la sortie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="717d0-132">The null (`` `0 ``) character appears as an empty space in PowerShell output.</span></span>
<span data-ttu-id="717d0-133">Cette fonctionnalité vous permet d’utiliser PowerShell pour lire et traiter des fichiers texte qui utilisent des caractères null, tels que la terminaison de chaîne ou les indicateurs de fin d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="717d0-133">This functionality allows you to use PowerShell to read and process text files that use null characters, such as string termination or record termination indicators.</span></span> <span data-ttu-id="717d0-134">Le caractère spécial NULL n’est pas équivalent à la `$null` variable, qui stocke une valeur **null** .</span><span class="sxs-lookup"><span data-stu-id="717d0-134">The null special character isn't equivalent to the `$null` variable, which stores a **null** value.</span></span>

## <a name="alert-a"></a><span data-ttu-id="717d0-135">Alerte ('a')</span><span class="sxs-lookup"><span data-stu-id="717d0-135">Alert (\`a)</span></span>

<span data-ttu-id="717d0-136">Le caractère alerte ( `` `a `` ) envoie un signal sonore au haut-parleur de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="717d0-136">The alert (`` `a ``) character sends a beep signal to the computer's speaker.</span></span>
<span data-ttu-id="717d0-137">Vous pouvez utiliser ce caractère pour avertir l’utilisateur d’une action imminente.</span><span class="sxs-lookup"><span data-stu-id="717d0-137">You can use this character to warn a user about an impending action.</span></span> <span data-ttu-id="717d0-138">L’exemple suivant envoie deux signaux sonores au haut-parleur de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="717d0-138">The following example sends two beep signals to the local computer's speaker.</span></span>

```powershell
for ($i = 0; $i -le 1; $i++){"`a"}
```

## <a name="backspace-b"></a><span data-ttu-id="717d0-139">Retour arrière ('b)</span><span class="sxs-lookup"><span data-stu-id="717d0-139">Backspace (\`b)</span></span>

<span data-ttu-id="717d0-140">Le `` `b `` caractère retour arrière () déplace le curseur d’un caractère vers l’arrière, mais il ne supprime aucun caractère.</span><span class="sxs-lookup"><span data-stu-id="717d0-140">The backspace (`` `b ``) character moves the cursor back one character, but it doesn't delete any characters.</span></span>

<span data-ttu-id="717d0-141">L’exemple écrit le mot **sauvegarde** , puis replace le curseur à deux reprises.</span><span class="sxs-lookup"><span data-stu-id="717d0-141">The example writes the word **backup** and then moves the cursor back twice.</span></span>
<span data-ttu-id="717d0-142">Ensuite, à la nouvelle position, écrit un espace suivi du mot **out**.</span><span class="sxs-lookup"><span data-stu-id="717d0-142">Then, at the new position, writes a space followed by the word **out**.</span></span>

```powershell
"backup`b`b out"
```

```Output
back out
```

## <a name="escape-e"></a><span data-ttu-id="717d0-143">Escape ('e)</span><span class="sxs-lookup"><span data-stu-id="717d0-143">Escape (\`e)</span></span>

<span data-ttu-id="717d0-144">Le `` `e `` caractère d’échappement () est le plus souvent utilisé pour spécifier une séquence de terminaux virtuels (séquence d’échappement ANSI) qui modifie la couleur du texte et d’autres attributs de texte tels que le gras et le soulignement.</span><span class="sxs-lookup"><span data-stu-id="717d0-144">The escape (`` `e ``) character is most commonly used to specify a virtual terminal sequence (ANSI escape sequence) that modifies the color of text and other text attributes such as bolding and underlining.</span></span> <span data-ttu-id="717d0-145">Ces séquences peuvent également être utilisées pour le positionnement et le défilement des curseurs.</span><span class="sxs-lookup"><span data-stu-id="717d0-145">These sequences can also be used for cursor positioning and scrolling.</span></span> <span data-ttu-id="717d0-146">L’hôte PowerShell doit prendre en charge les séquences de terminaux virtuels.</span><span class="sxs-lookup"><span data-stu-id="717d0-146">The PowerShell host must support virtual terminal sequences.</span></span> <span data-ttu-id="717d0-147">Vous pouvez vérifier la valeur booléenne de `$Host.UI.SupportsVirtualTerminal` pour déterminer si ces séquences ANSI sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="717d0-147">You can check the boolean value of `$Host.UI.SupportsVirtualTerminal` to determine if these ANSI sequences are supported.</span></span>

<span data-ttu-id="717d0-148">Pour plus d’informations sur les séquences d’échappement ANSI, consultez [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span><span class="sxs-lookup"><span data-stu-id="717d0-148">For more information about ANSI escape sequences, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

<span data-ttu-id="717d0-149">L’exemple suivant génère le texte avec une couleur de premier plan verte.</span><span class="sxs-lookup"><span data-stu-id="717d0-149">The following example outputs text with a green foreground color.</span></span>

```powershell
$fgColor = 32 # green
"`e[${fgColor}mGreen text`e[0m"
```

```Output
Green text
```

## <a name="form-feed-f"></a><span data-ttu-id="717d0-150">Flux de formulaire ('f')</span><span class="sxs-lookup"><span data-stu-id="717d0-150">Form feed (\`f)</span></span>

<span data-ttu-id="717d0-151">Le caractère de saut de `` `f `` page () est une instruction d’impression qui éjecte la page actuelle et poursuit l’impression sur la page suivante.</span><span class="sxs-lookup"><span data-stu-id="717d0-151">The form feed (`` `f ``) character is a print instruction that ejects the current page and continues printing on the next page.</span></span> <span data-ttu-id="717d0-152">Le caractère de saut de formulaire affecte uniquement les documents imprimés.</span><span class="sxs-lookup"><span data-stu-id="717d0-152">The form feed character only affects printed documents.</span></span> <span data-ttu-id="717d0-153">Elle n’affecte pas la sortie écran.</span><span class="sxs-lookup"><span data-stu-id="717d0-153">It doesn't affect screen output.</span></span>

## <a name="new-line-n"></a><span data-ttu-id="717d0-154">Nouvelle ligne ('n)</span><span class="sxs-lookup"><span data-stu-id="717d0-154">New line (\`n)</span></span>

<span data-ttu-id="717d0-155">Le caractère de nouvelle ligne ( `` `n `` ) insère un saut de ligne immédiatement après le caractère.</span><span class="sxs-lookup"><span data-stu-id="717d0-155">The new line (`` `n ``) character inserts a line break immediately after the character.</span></span>

<span data-ttu-id="717d0-156">Cet exemple montre comment utiliser le caractère de nouvelle ligne pour créer des sauts de ligne dans une `Write-Host` commande.</span><span class="sxs-lookup"><span data-stu-id="717d0-156">This example shows how to use the new line character to create line breaks in a `Write-Host` command.</span></span>

```powershell
"There are two line breaks to create a blank line`n`nbetween the words."
```

```Output
There are two line breaks to create a blank line

between the words.
```

## <a name="carriage-return-r"></a><span data-ttu-id="717d0-157">Retour chariot ('r)</span><span class="sxs-lookup"><span data-stu-id="717d0-157">Carriage return (\`r)</span></span>

<span data-ttu-id="717d0-158">Le caractère retour chariot ( `` `r `` ) déplace le curseur de sortie au début de la ligne active et poursuit l’écriture.</span><span class="sxs-lookup"><span data-stu-id="717d0-158">The carriage return (`` `r ``) character moves the output cursor to the beginning of the current line and continues writing.</span></span> <span data-ttu-id="717d0-159">Tous les caractères de la ligne active sont remplacés.</span><span class="sxs-lookup"><span data-stu-id="717d0-159">Any characters on the current line are overwritten.</span></span>

<span data-ttu-id="717d0-160">Dans cet exemple, le texte avant le retour chariot est remplacé.</span><span class="sxs-lookup"><span data-stu-id="717d0-160">In this example, the text before the carriage return is overwritten.</span></span>

```powershell
Write-Host "These characters are overwritten.`rI want this text instead "
```

<span data-ttu-id="717d0-161">Notez que le texte avant le `` `r `` caractère n’est pas supprimé, il est remplacé.</span><span class="sxs-lookup"><span data-stu-id="717d0-161">Notice that the text before the `` `r `` character is not deleted, it is overwritten.</span></span>

```Output
I want this text instead written.
```

## <a name="horizontal-tab-t"></a><span data-ttu-id="717d0-162">Tabulation horizontale (t)</span><span class="sxs-lookup"><span data-stu-id="717d0-162">Horizontal tab (\`t)</span></span>

<span data-ttu-id="717d0-163">Le caractère de tabulation horizontale ( `` `t `` ) passe au taquet de tabulation suivant et poursuit l’écriture à ce stade.</span><span class="sxs-lookup"><span data-stu-id="717d0-163">The horizontal tab (`` `t ``) character advances to the next tab stop and continues writing at that point.</span></span> <span data-ttu-id="717d0-164">Par défaut, la console PowerShell a un taquet de tabulation à chaque huitième espace.</span><span class="sxs-lookup"><span data-stu-id="717d0-164">By default, the PowerShell console has a tab stop at every eighth space.</span></span>

<span data-ttu-id="717d0-165">Cet exemple insère deux onglets entre chaque colonne.</span><span class="sxs-lookup"><span data-stu-id="717d0-165">This example inserts two tabs between each column.</span></span>

```powershell
"Column1`t`tColumn2`t`tColumn3"
```

```Output
Column1         Column2         Column3
```

## <a name="unicode-character-ux"></a><span data-ttu-id="717d0-166">Caractère Unicode ('u {x}]</span><span class="sxs-lookup"><span data-stu-id="717d0-166">Unicode character (\`u{x})</span></span>

<span data-ttu-id="717d0-167">La séquence d’échappement Unicode ( `` `u{x} `` ) vous permet de spécifier n’importe quel caractère Unicode à l’aide de la représentation hexadécimale de son point de code.</span><span class="sxs-lookup"><span data-stu-id="717d0-167">The Unicode escape sequence (`` `u{x} ``) allows you to specify any Unicode character by the hexadecimal representation of its code point.</span></span> <span data-ttu-id="717d0-168">Cela comprend les caractères Unicode au-dessus du plan multilingue de base (>), y `0xFFFF` compris les caractères Emoji tels que le caractère **pouce** ( `` `u{1F44D} `` ).</span><span class="sxs-lookup"><span data-stu-id="717d0-168">This includes Unicode characters above the Basic Multilingual Plane (> `0xFFFF`) which includes emoji characters such as the **thumbs up** (`` `u{1F44D} ``) character.</span></span> <span data-ttu-id="717d0-169">La séquence d’échappement Unicode requiert au moins un chiffre hexadécimal et prend en charge jusqu’à six chiffres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="717d0-169">The Unicode escape sequence requires at least one hexadecimal digit and supports up to six hexadecimal digits.</span></span> <span data-ttu-id="717d0-170">La valeur hexadécimale maximale pour la séquence est `10FFFF` .</span><span class="sxs-lookup"><span data-stu-id="717d0-170">The maximum hexadecimal value for the sequence is `10FFFF`.</span></span>

<span data-ttu-id="717d0-171">Cet exemple génère le symbole de **flèche vers le bas** (&#x2195;).</span><span class="sxs-lookup"><span data-stu-id="717d0-171">This example outputs the **up down arrow** (&#x2195;) symbol.</span></span>

```powershell
"`u{2195}"
```

## <a name="vertical-tab-v"></a><span data-ttu-id="717d0-172">Tabulation verticale ('v)</span><span class="sxs-lookup"><span data-stu-id="717d0-172">Vertical tab (\`v)</span></span>

<span data-ttu-id="717d0-173">Le caractère de tabulation horizontale ( `` `v `` ) passe au taquet de tabulation vertical suivant et écrit la sortie restante à ce stade.</span><span class="sxs-lookup"><span data-stu-id="717d0-173">The horizontal tab (`` `v ``) character advances to the next vertical tab stop and writes the remaining output at that point.</span></span> <span data-ttu-id="717d0-174">Cela n’a aucun effet dans la console Windows par défaut.</span><span class="sxs-lookup"><span data-stu-id="717d0-174">This has no effect in the default Windows console.</span></span>

```powershell
Write-Host "There is a vertical tab`vbetween the words."
```

<span data-ttu-id="717d0-175">L’exemple suivant illustre la sortie que vous obtiendriez sur une imprimante ou dans un autre hôte de console.</span><span class="sxs-lookup"><span data-stu-id="717d0-175">The following example shows the output you would get on a printer or in a different console host.</span></span>

```Output
There is a vertical tab
                       between the words.
```

## <a name="stop-parsing-token---"></a><span data-ttu-id="717d0-176">Jeton d’analyse d’arrêt (--%)</span><span class="sxs-lookup"><span data-stu-id="717d0-176">Stop-parsing token (--%)</span></span>

<span data-ttu-id="717d0-177">Le jeton Stop-Analysing ( `--%` ) empêche PowerShell d’interpréter les chaînes comme des commandes et des expressions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="717d0-177">The stop-parsing (`--%`) token prevents PowerShell from interpreting strings as PowerShell commands and expressions.</span></span> <span data-ttu-id="717d0-178">Cela permet de transmettre ces chaînes à d’autres programmes pour les interpréter.</span><span class="sxs-lookup"><span data-stu-id="717d0-178">This allows those strings to be passed to other programs for interpretation.</span></span>

<span data-ttu-id="717d0-179">Placez le jeton d’analyse d’arrêt après le nom du programme et avant les arguments du programme qui peuvent provoquer des erreurs.</span><span class="sxs-lookup"><span data-stu-id="717d0-179">Place the stop-parsing token after the program name and before program arguments that might cause errors.</span></span>

<span data-ttu-id="717d0-180">Dans cet exemple, la `Icacls` commande utilise le jeton d’analyse d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="717d0-180">In this example, the `Icacls` command uses the stop-parsing token.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="717d0-181">PowerShell envoie la chaîne suivante à `Icacls` .</span><span class="sxs-lookup"><span data-stu-id="717d0-181">PowerShell sends the following string to `Icacls`.</span></span>

```
X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="717d0-182">Voici un autre exemple.</span><span class="sxs-lookup"><span data-stu-id="717d0-182">Here is another example.</span></span> <span data-ttu-id="717d0-183">La fonction **showArgs** génère les valeurs qui lui sont passées.</span><span class="sxs-lookup"><span data-stu-id="717d0-183">The **showArgs** function outputs the values passed to it.</span></span> <span data-ttu-id="717d0-184">Dans cet exemple, nous passons `$HOME` à deux fois la variable nommée à la fonction.</span><span class="sxs-lookup"><span data-stu-id="717d0-184">In this example, we pass the variable named `$HOME` to the function twice.</span></span>

```powershell
function showArgs {
  "`$args = " + ($args -join '|')
}

showArgs $HOME --% $HOME
```

Dans la sortie, vous pouvez voir que, pour le premier paramètre, la variable `$HOME` est interprétée par PowerShell afin que la valeur de la variable soit transmise à la fonction. <span data-ttu-id="717d0-186">La deuxième utilisation de `$HOME` vient après le jeton d’analyse d’arrêt, donc la chaîne « $Home » est transmise à la fonction sans interprétation.</span><span class="sxs-lookup"><span data-stu-id="717d0-186">The second use of `$HOME` comes after the stop-parsing token, so the string "$HOME" is passed to the function without interpretation.</span></span>

```Output
$args = C:\Users\username|--%|$HOME
```

<span data-ttu-id="717d0-187">Pour plus d’informations sur le jeton d’analyse d’arrêt, consultez [about_Parsing](about_Parsing.md).</span><span class="sxs-lookup"><span data-stu-id="717d0-187">For more information about the stop-parsing token, see [about_Parsing](about_Parsing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="717d0-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="717d0-188">See also</span></span>

[<span data-ttu-id="717d0-189">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="717d0-189">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

