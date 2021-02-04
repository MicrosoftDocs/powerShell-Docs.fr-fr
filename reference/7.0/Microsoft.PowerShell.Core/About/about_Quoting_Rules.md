---
description: Décrit les règles d’utilisation des guillemets simples et doubles dans PowerShell.
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: 27d5909c1381c0d221690b353a308680643ecad5
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490752"
---
# <a name="about-quoting-rules"></a><span data-ttu-id="515d2-103">À propos des règles de Quotation</span><span class="sxs-lookup"><span data-stu-id="515d2-103">About Quoting Rules</span></span>

## <a name="short-description"></a><span data-ttu-id="515d2-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="515d2-104">Short description</span></span>
<span data-ttu-id="515d2-105">Décrit les règles d’utilisation des guillemets simples et doubles dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="515d2-105">Describes rules for using single and double quotation marks in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="515d2-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="515d2-106">Long description</span></span>

<span data-ttu-id="515d2-107">Des guillemets sont utilisés pour spécifier une chaîne littérale.</span><span class="sxs-lookup"><span data-stu-id="515d2-107">Quotation marks are used to specify a literal string.</span></span> <span data-ttu-id="515d2-108">Vous pouvez placer une chaîne entre guillemets simples ( `'` ) ou guillemets doubles ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="515d2-108">You can enclose a string in single quotation marks (`'`) or double quotation marks (`"`).</span></span>

<span data-ttu-id="515d2-109">Des guillemets sont également utilisés pour créer une _chaîne ici-_.</span><span class="sxs-lookup"><span data-stu-id="515d2-109">Quotation marks are also used to create a _here-string_.</span></span> <span data-ttu-id="515d2-110">Une chaîne ici est une chaîne entre guillemets simples ou entre guillemets, dans laquelle les guillemets sont interprétés littéralement.</span><span class="sxs-lookup"><span data-stu-id="515d2-110">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="515d2-111">Une chaîne ici peut s’étendre sur plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="515d2-111">A here-string can span multiple lines.</span></span> <span data-ttu-id="515d2-112">Toutes les lignes d’une chaîne ici sont interprétées comme des chaînes, même si elles ne sont pas placées entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="515d2-112">All the lines in a here-string are interpreted as strings, even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="515d2-113">Dans les commandes des ordinateurs distants, les guillemets définissent les parties de la commande qui sont exécutées sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="515d2-113">In commands to remote computers, quotation marks define the parts of the command that are run on the remote computer.</span></span> <span data-ttu-id="515d2-114">Dans une session à distance, les guillemets déterminent également si les variables d’une commande sont d’abord interprétées sur l’ordinateur local ou sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="515d2-114">In a remote session, quotation marks also determine whether the variables in a command are interpreted first on the local computer or on the remote computer.</span></span>

## <a name="single-and-double-quoted-strings"></a><span data-ttu-id="515d2-115">Chaînes entre guillemets simples et doubles</span><span class="sxs-lookup"><span data-stu-id="515d2-115">Single and double-quoted strings</span></span>

<span data-ttu-id="515d2-116">Une chaîne placée entre guillemets doubles est une chaîne _pouvant être développée_ .</span><span class="sxs-lookup"><span data-stu-id="515d2-116">A string enclosed in double quotation marks is an _expandable_ string.</span></span> <span data-ttu-id="515d2-117">Les noms de variables précédés d’un signe dollar ( `$` ) sont remplacés par la valeur de la variable avant que la chaîne soit transmise à la commande à des fins de traitement.</span><span class="sxs-lookup"><span data-stu-id="515d2-117">Variable names preceded by a dollar sign (`$`) are replaced with the variable's value before the string is passed to the command for processing.</span></span>

<span data-ttu-id="515d2-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="515d2-118">For example:</span></span>

```powershell
$i = 5
"The value of $i is $i."
```

<span data-ttu-id="515d2-119">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="515d2-119">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="515d2-120">En outre, dans une chaîne entre guillemets doubles, les expressions sont évaluées et le résultat est inséré dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="515d2-120">Also, in a double-quoted string, expressions are evaluated, and the result is inserted in the string.</span></span> <span data-ttu-id="515d2-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="515d2-121">For example:</span></span>

```powershell
"The value of $(2+3) is 5."
```

<span data-ttu-id="515d2-122">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="515d2-122">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="515d2-123">Une chaîne placée entre guillemets simples est une chaîne _textuelle_ .</span><span class="sxs-lookup"><span data-stu-id="515d2-123">A string enclosed in single-quotation marks is a _verbatim_ string.</span></span> <span data-ttu-id="515d2-124">La chaîne est passée à la commande exactement telle que vous la tapez.</span><span class="sxs-lookup"><span data-stu-id="515d2-124">The string is passed to the command exactly as you type it.</span></span> <span data-ttu-id="515d2-125">Aucune substitution n’est effectuée.</span><span class="sxs-lookup"><span data-stu-id="515d2-125">No substitution is performed.</span></span>
<span data-ttu-id="515d2-126">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="515d2-126">For example:</span></span>

```powershell
$i = 5
'The value of $i is $i.'
```

<span data-ttu-id="515d2-127">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="515d2-127">The output of this command is:</span></span>

```Output
The value $i is $i.
```

<span data-ttu-id="515d2-128">De même, les expressions des chaînes entre guillemets simples ne sont pas évaluées.</span><span class="sxs-lookup"><span data-stu-id="515d2-128">Similarly, expressions in single-quoted strings are not evaluated.</span></span> <span data-ttu-id="515d2-129">Ils sont interprétés comme des littéraux.</span><span class="sxs-lookup"><span data-stu-id="515d2-129">They are interpreted as literals.</span></span> <span data-ttu-id="515d2-130">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="515d2-130">For example:</span></span>

```powershell
'The value of $(2+3) is 5.'
```

<span data-ttu-id="515d2-131">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="515d2-131">The output of this command is:</span></span>

```Output
The value of $(2+3) is 5.
```

<span data-ttu-id="515d2-132">Pour empêcher la substitution d’une valeur de variable dans une chaîne entre guillemets doubles, utilisez le caractère de soulignement ( `` ` `` ) (ASCII 96), qui est le caractère d’échappement PowerShell.</span><span class="sxs-lookup"><span data-stu-id="515d2-132">To prevent the substitution of a variable value in a double-quoted string, use the backtick character (`` ` ``)(ASCII 96), which is the PowerShell escape character.</span></span>

<span data-ttu-id="515d2-133">Dans l’exemple suivant, le caractère d’impulsion qui précède la première `$i` variable empêche PowerShell de remplacer le nom de la variable par sa valeur.</span><span class="sxs-lookup"><span data-stu-id="515d2-133">In the following example, the backtick character that precedes the first `$i` variable prevents PowerShell from replacing the variable name with its value.</span></span>
<span data-ttu-id="515d2-134">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="515d2-134">For example:</span></span>

```powershell
$i = 5
"The value of `$i is $i."
```

<span data-ttu-id="515d2-135">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="515d2-135">The output of this command is:</span></span>

```Output
The value $i is 5.
```

<span data-ttu-id="515d2-136">Pour faire apparaître les guillemets doubles dans une chaîne, placez la totalité de la chaîne entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="515d2-136">To make double-quotation marks appear in a string, enclose the entire string in single quotation marks.</span></span> <span data-ttu-id="515d2-137">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="515d2-137">For example:</span></span>

```powershell
'As they say, "live and learn."'
```

<span data-ttu-id="515d2-138">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="515d2-138">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="515d2-139">Vous pouvez également placer une chaîne entre guillemets simples dans une chaîne entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="515d2-139">You can also enclose a single-quoted string in a double-quoted string.</span></span> <span data-ttu-id="515d2-140">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="515d2-140">For example:</span></span>

```powershell
"As they say, 'live and learn.'"
```

<span data-ttu-id="515d2-141">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="515d2-141">The output of this command is:</span></span>

```Output
As they say, 'live and learn.'
```

<span data-ttu-id="515d2-142">Ou, doublez les guillemets autour d’une expression entre guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="515d2-142">Or, double the quotation marks around a double-quoted phrase.</span></span> <span data-ttu-id="515d2-143">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="515d2-143">For example:</span></span>

```powershell
"As they say, ""live and learn."""
```

<span data-ttu-id="515d2-144">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="515d2-144">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="515d2-145">Pour inclure un guillemet simple dans une chaîne entre guillemets simples, utilisez un deuxième guillemet simple consécutif.</span><span class="sxs-lookup"><span data-stu-id="515d2-145">To include a single quotation mark in a single-quoted string, use a second consecutive single quote.</span></span> <span data-ttu-id="515d2-146">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="515d2-146">For example:</span></span>

```powershell
'don''t'
```

<span data-ttu-id="515d2-147">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="515d2-147">The output of this command is:</span></span>

```Output
don't
```

<span data-ttu-id="515d2-148">Pour forcer PowerShell à interpréter littéralement un guillemet double, utilisez un caractère de soulignement.</span><span class="sxs-lookup"><span data-stu-id="515d2-148">To force PowerShell to interpret a double quotation mark literally, use a backtick character.</span></span> <span data-ttu-id="515d2-149">Cela empêche PowerShell d’interpréter le guillemet comme un délimiteur de chaîne.</span><span class="sxs-lookup"><span data-stu-id="515d2-149">This prevents PowerShell from interpreting the quotation mark as a string delimiter.</span></span> <span data-ttu-id="515d2-150">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="515d2-150">For example:</span></span>

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

<span data-ttu-id="515d2-151">Étant donné que le contenu des chaînes entre guillemets simples est interprété littéralement, vous êtes considéré comme un caractère littéral et affiché dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="515d2-151">Because the contents of single-quoted strings are interpreted literally, you the backtick character is treated as a literal character and displayed in the output.</span></span>

## <a name="here-strings"></a><span data-ttu-id="515d2-152">Ici-chaînes</span><span class="sxs-lookup"><span data-stu-id="515d2-152">Here-strings</span></span>

<span data-ttu-id="515d2-153">Les règles de quotation pour les chaînes ici sont légèrement différentes.</span><span class="sxs-lookup"><span data-stu-id="515d2-153">The quotation rules for here-strings are slightly different.</span></span>

<span data-ttu-id="515d2-154">Une chaîne ici est une chaîne entre guillemets simples ou entre guillemets, dans laquelle les guillemets sont interprétés littéralement.</span><span class="sxs-lookup"><span data-stu-id="515d2-154">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="515d2-155">Une chaîne ici peut s’étendre sur plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="515d2-155">A here-string can span multiple lines.</span></span> <span data-ttu-id="515d2-156">Toutes les lignes d’une chaîne ici sont interprétées comme des chaînes même si elles ne sont pas placées entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="515d2-156">All the lines in a here-string are interpreted as strings even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="515d2-157">À l’instar des chaînes régulières, les variables sont remplacées par leurs valeurs dans des chaînes here à deux guillemets.</span><span class="sxs-lookup"><span data-stu-id="515d2-157">Like regular strings, variables are replaced by their values in double-quoted here-strings.</span></span> <span data-ttu-id="515d2-158">Dans les chaînes ici à guillemets simples, les variables ne sont pas remplacées par leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="515d2-158">In single-quoted here-strings, variables are not replaced by their values.</span></span>

<span data-ttu-id="515d2-159">Vous pouvez utiliser des chaînes here pour tout texte, mais elles sont particulièrement utiles pour les genres de texte suivants :</span><span class="sxs-lookup"><span data-stu-id="515d2-159">You can use here-strings for any text, but they are particularly useful for the following kinds of text:</span></span>

- <span data-ttu-id="515d2-160">Texte qui contient des guillemets littéraux</span><span class="sxs-lookup"><span data-stu-id="515d2-160">Text that contains literal quotation marks</span></span>
- <span data-ttu-id="515d2-161">Plusieurs lignes de texte, telles que le texte dans un fichier HTML ou XML</span><span class="sxs-lookup"><span data-stu-id="515d2-161">Multiple lines of text, such as the text in an HTML or XML</span></span>
- <span data-ttu-id="515d2-162">Texte d’aide d’un script ou d’un document de fonction</span><span class="sxs-lookup"><span data-stu-id="515d2-162">The Help text for a script or function document</span></span>

<span data-ttu-id="515d2-163">Une chaîne « here » peut avoir l’un des formats suivants, où `<Enter>` représente le caractère masqué de saut de ligne ou de saut de ligne qui est ajouté lorsque vous appuyez sur la touche <kbd>entrée</kbd> .</span><span class="sxs-lookup"><span data-stu-id="515d2-163">A here-string can have either of the following formats, where `<Enter>` represents the linefeed or newline hidden character that is added when you press the <kbd>ENTER</kbd> key.</span></span>

<span data-ttu-id="515d2-164">Guillemets doubles :</span><span class="sxs-lookup"><span data-stu-id="515d2-164">Double-quotes:</span></span>

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

<span data-ttu-id="515d2-165">Guillemets simples :</span><span class="sxs-lookup"><span data-stu-id="515d2-165">Single-quotes:</span></span>

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

<span data-ttu-id="515d2-166">Dans les deux formats, le guillemet fermant doit être le premier caractère de la ligne.</span><span class="sxs-lookup"><span data-stu-id="515d2-166">In either format, the closing quotation mark must be the first character in the line.</span></span>

<span data-ttu-id="515d2-167">Une chaîne ici contient tout le texte entre les deux caractères masqués.</span><span class="sxs-lookup"><span data-stu-id="515d2-167">A here-string contains all the text between the two hidden characters.</span></span> <span data-ttu-id="515d2-168">Dans la chaîne here, tous les guillemets sont interprétés littéralement.</span><span class="sxs-lookup"><span data-stu-id="515d2-168">In the here-string, all quotation marks are interpreted literally.</span></span> <span data-ttu-id="515d2-169">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="515d2-169">For example:</span></span>

```powershell
@"
For help, type "get-help"
"@
```

<span data-ttu-id="515d2-170">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="515d2-170">The output of this command is:</span></span>

```Output
For help, type "get-help"
```

<span data-ttu-id="515d2-171">L’utilisation d’une chaîne « here » peut simplifier l’utilisation d’une chaîne dans une commande.</span><span class="sxs-lookup"><span data-stu-id="515d2-171">Using a here-string can simplify using a string in a command.</span></span> <span data-ttu-id="515d2-172">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="515d2-172">For example:</span></span>

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

<span data-ttu-id="515d2-173">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="515d2-173">The output of this command is:</span></span>

```Output
Use a quotation mark (') to begin a string.
```

<span data-ttu-id="515d2-174">Dans les chaînes ici à guillemets simples, les variables sont interprétées littéralement et reproduites exactement.</span><span class="sxs-lookup"><span data-stu-id="515d2-174">In single-quoted here-strings, variables are interpreted literally and reproduced exactly.</span></span> <span data-ttu-id="515d2-175">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="515d2-175">For example:</span></span>

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

<span data-ttu-id="515d2-176">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="515d2-176">The output of this command is:</span></span>

```Output
The $profile variable contains the path
of your PowerShell profile.
```

<span data-ttu-id="515d2-177">Dans les chaînes à deux guillemets (), les variables sont remplacées par leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="515d2-177">In double-quoted here-strings, variables are replaced by their values.</span></span> <span data-ttu-id="515d2-178">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="515d2-178">For example:</span></span>

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

<span data-ttu-id="515d2-179">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="515d2-179">The output of this command is:</span></span>

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

<span data-ttu-id="515d2-180">Ici-les chaînes sont généralement utilisées pour assigner plusieurs lignes à une variable.</span><span class="sxs-lookup"><span data-stu-id="515d2-180">Here-strings are typically used to assign multiple lines to a variable.</span></span> <span data-ttu-id="515d2-181">Par exemple, le texte suivant-String affecte une page XML à la variable $page.</span><span class="sxs-lookup"><span data-stu-id="515d2-181">For example, the following here-string assigns a page of XML to the $page variable.</span></span>

```powershell
$page = [XML] @"
<command:command xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
<command:details>
        <command:name>
               Format-Table
        </command:name>
        <maml:description>
            <maml:para>Formats the output as a table.</maml:para>
        </maml:description>
        <command:verb>format</command:verb>
        <command:noun>table</command:noun>
        <dev:version></dev:version>
</command:details>
...
</command:command>
"@
```

<span data-ttu-id="515d2-182">Ici-les chaînes sont également un format pratique pour l’entrée de l’applet de commande `ConvertFrom-StringData` , qui convertit les chaînes ici en tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="515d2-182">Here-strings are also a convenient format for input to the `ConvertFrom-StringData` cmdlet, which converts here-strings to hash tables.</span></span>
<span data-ttu-id="515d2-183">Pour plus d’informations, consultez `ConvertFrom-StringData`.</span><span class="sxs-lookup"><span data-stu-id="515d2-183">For more information, see `ConvertFrom-StringData`.</span></span>

## <a name="see-also"></a><span data-ttu-id="515d2-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="515d2-184">See also</span></span>

[<span data-ttu-id="515d2-185">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="515d2-185">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="515d2-186">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="515d2-186">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
