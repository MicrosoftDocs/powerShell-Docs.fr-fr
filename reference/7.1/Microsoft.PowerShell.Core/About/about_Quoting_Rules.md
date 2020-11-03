---
description: Décrit les règles d’utilisation des guillemets simples et doubles dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: 8d09171a1459a8ad03b54f2a4ef7a81c5983f6b8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207742"
---
# <a name="about-quoting-rules"></a><span data-ttu-id="e0f6a-104">À propos des règles de Quotation</span><span class="sxs-lookup"><span data-stu-id="e0f6a-104">About Quoting Rules</span></span>

## <a name="short-description"></a><span data-ttu-id="e0f6a-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="e0f6a-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="e0f6a-106">Décrit les règles d’utilisation des guillemets simples et doubles dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-106">Describes rules for using single and double quotation marks in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="e0f6a-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="e0f6a-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="e0f6a-108">Des guillemets sont utilisés pour spécifier une chaîne littérale.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-108">Quotation marks are used to specify a literal string.</span></span> <span data-ttu-id="e0f6a-109">Vous pouvez placer une chaîne entre guillemets simples ( `'` ) ou guillemets doubles ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="e0f6a-109">You can enclose a string in single quotation marks (`'`) or double quotation marks (`"`).</span></span>

<span data-ttu-id="e0f6a-110">Des guillemets sont également utilisés pour créer une chaîne ici-.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-110">Quotation marks are also used to create a here-string.</span></span> <span data-ttu-id="e0f6a-111">Une chaîne ici est une chaîne entre guillemets simples ou entre guillemets, dans laquelle les guillemets sont interprétés littéralement.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-111">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="e0f6a-112">Une chaîne ici peut s’étendre sur plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-112">A here-string can span multiple lines.</span></span> <span data-ttu-id="e0f6a-113">Toutes les lignes d’une chaîne ici sont interprétées comme des chaînes, même si elles ne sont pas placées entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-113">All the lines in a here-string are interpreted as strings, even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="e0f6a-114">Dans les commandes des ordinateurs distants, les guillemets définissent les parties de la commande qui sont exécutées sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-114">In commands to remote computers, quotation marks define the parts of the command that are run on the remote computer.</span></span> <span data-ttu-id="e0f6a-115">Dans une session à distance, les guillemets déterminent également si les variables d’une commande sont d’abord interprétées sur l’ordinateur local ou sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-115">In a remote session, quotation marks also determine whether the variables in a command are interpreted first on the local computer or on the remote computer.</span></span>

### <a name="single-and-double-quoted-strings"></a><span data-ttu-id="e0f6a-116">CHAÎNES ENTRE GUILLEMETS SIMPLES ET DOUBLES</span><span class="sxs-lookup"><span data-stu-id="e0f6a-116">SINGLE AND DOUBLE-QUOTED STRINGS</span></span>

<span data-ttu-id="e0f6a-117">Lorsque vous placez une chaîne entre guillemets doubles (une chaîne entre guillemets doubles), les noms de variables précédés d’un signe dollar ( `$` ) sont remplacés par la valeur de la variable avant que la chaîne soit transmise à la commande pour traitement.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-117">When you enclose a string in double quotation marks (a double-quoted string), variable names that are preceded by a dollar sign (`$`) are replaced with the variable's value before the string is passed to the command for processing.</span></span>

<span data-ttu-id="e0f6a-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-118">For example:</span></span>

```powershell
$i = 5
"The value of $i is $i."
```

<span data-ttu-id="e0f6a-119">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-119">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="e0f6a-120">En outre, dans une chaîne entre guillemets doubles, les expressions sont évaluées et le résultat est inséré dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-120">Also, in a double-quoted string, expressions are evaluated, and the result is inserted in the string.</span></span> <span data-ttu-id="e0f6a-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-121">For example:</span></span>

```powershell
"The value of $(2+3) is 5."
```

<span data-ttu-id="e0f6a-122">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-122">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="e0f6a-123">Lorsque vous placez une chaîne entre des guillemets simples (une chaîne entre guillemets simples), la chaîne est transmise à la commande exactement telle que vous la tapez.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-123">When you enclose a string in single-quotation marks (a single-quoted string), the string is passed to the command exactly as you type it.</span></span> <span data-ttu-id="e0f6a-124">Aucune substitution n’est effectuée.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-124">No substitution is performed.</span></span> <span data-ttu-id="e0f6a-125">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-125">For example:</span></span>

```powershell
$i = 5
'The value of $i is $i.'
```

<span data-ttu-id="e0f6a-126">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-126">The output of this command is:</span></span>

```Output
The value $i is $i.
```

<span data-ttu-id="e0f6a-127">De même, les expressions des chaînes entre guillemets simples ne sont pas évaluées.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-127">Similarly, expressions in single-quoted strings are not evaluated.</span></span> <span data-ttu-id="e0f6a-128">Ils sont interprétés comme des littéraux.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-128">They are interpreted as literals.</span></span> <span data-ttu-id="e0f6a-129">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-129">For example:</span></span>

```powershell
'The value of $(2+3) is 5.'
```

<span data-ttu-id="e0f6a-130">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-130">The output of this command is:</span></span>

```Output
The value of $(2+3) is 5.
```

<span data-ttu-id="e0f6a-131">Pour empêcher la substitution d’une valeur de variable dans une chaîne entre guillemets doubles, utilisez le caractère de soulignement ( `` ` `` ) (ASCII 96), qui est le caractère d’échappement PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-131">To prevent the substitution of a variable value in a double-quoted string, use the backtick character (`` ` ``)(ASCII 96), which is the PowerShell escape character.</span></span>

<span data-ttu-id="e0f6a-132">Dans l’exemple suivant, le caractère de soulignement qui précède la première variable $i empêche PowerShell de remplacer le nom de la variable par sa valeur.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-132">In the following example, the backtick character that precedes the first $i variable prevents PowerShell from replacing the variable name with its value.</span></span>
<span data-ttu-id="e0f6a-133">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-133">For example:</span></span>

```powershell
$i = 5
"The value of `$i is $i."
```

<span data-ttu-id="e0f6a-134">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-134">The output of this command is:</span></span>

```Output
The value $i is 5.
```

<span data-ttu-id="e0f6a-135">Pour faire apparaître les guillemets doubles dans une chaîne, placez la totalité de la chaîne entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-135">To make double-quotation marks appear in a string, enclose the entire string in single quotation marks.</span></span> <span data-ttu-id="e0f6a-136">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-136">For example:</span></span>

```powershell
'As they say, "live and learn."'
```

<span data-ttu-id="e0f6a-137">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-137">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="e0f6a-138">Vous pouvez également placer une chaîne entre guillemets simples dans une chaîne entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-138">You can also enclose a single-quoted string in a double-quoted string.</span></span> <span data-ttu-id="e0f6a-139">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-139">For example:</span></span>

```powershell
"As they say, 'live and learn.'"
```

<span data-ttu-id="e0f6a-140">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-140">The output of this command is:</span></span>

```Output
As they say, 'live and learn.'
```

<span data-ttu-id="e0f6a-141">Ou, doublez les guillemets autour d’une expression entre guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-141">Or, double the quotation marks around a double-quoted phrase.</span></span> <span data-ttu-id="e0f6a-142">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-142">For example:</span></span>

```powershell
"As they say, ""live and learn."""
```

<span data-ttu-id="e0f6a-143">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-143">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="e0f6a-144">Pour inclure un guillemet simple dans une chaîne entre guillemets simples, utilisez un deuxième guillemet simple consécutif.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-144">To include a single quotation mark in a single-quoted string, use a second consecutive single quote.</span></span> <span data-ttu-id="e0f6a-145">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-145">For example:</span></span>

```powershell
'don''t'
```

<span data-ttu-id="e0f6a-146">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-146">The output of this command is:</span></span>

```Output
don't
```

<span data-ttu-id="e0f6a-147">Pour forcer PowerShell à interpréter littéralement un guillemet double, utilisez un caractère de soulignement.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-147">To force PowerShell to interpret a double quotation mark literally, use a backtick character.</span></span> <span data-ttu-id="e0f6a-148">Cela empêche PowerShell d’interpréter le guillemet comme un délimiteur de chaîne.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-148">This prevents PowerShell from interpreting the quotation mark as a string delimiter.</span></span> <span data-ttu-id="e0f6a-149">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-149">For example:</span></span>

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

<span data-ttu-id="e0f6a-150">Étant donné que le contenu des chaînes entre guillemets simples est interprété littéralement, vous êtes considéré comme un caractère littéral et affiché dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-150">Because the contents of single-quoted strings are interpreted literally, you the backtick character is treated as a literal character and displayed in the output.</span></span>

### <a name="here-strings"></a><span data-ttu-id="e0f6a-151">ICI-CHAÎNES</span><span class="sxs-lookup"><span data-stu-id="e0f6a-151">HERE-STRINGS</span></span>

<span data-ttu-id="e0f6a-152">Les règles de quotation pour les chaînes ici sont légèrement différentes.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-152">The quotation rules for here-strings are slightly different.</span></span>

<span data-ttu-id="e0f6a-153">Une chaîne ici est une chaîne entre guillemets simples ou entre guillemets, dans laquelle les guillemets sont interprétés littéralement.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-153">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="e0f6a-154">Une chaîne ici peut s’étendre sur plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-154">A here-string can span multiple lines.</span></span> <span data-ttu-id="e0f6a-155">Toutes les lignes d’une chaîne ici sont interprétées comme des chaînes même si elles ne sont pas placées entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-155">All the lines in a here-string are interpreted as strings even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="e0f6a-156">À l’instar des chaînes régulières, les variables sont remplacées par leurs valeurs dans des chaînes here à deux guillemets.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-156">Like regular strings, variables are replaced by their values in double-quoted here-strings.</span></span> <span data-ttu-id="e0f6a-157">Dans les chaînes ici à guillemets simples, les variables ne sont pas remplacées par leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-157">In single-quoted here-strings, variables are not replaced by their values.</span></span>

<span data-ttu-id="e0f6a-158">Vous pouvez utiliser des chaînes here pour tout texte, mais elles sont particulièrement utiles pour les genres de texte suivants :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-158">You can use here-strings for any text, but they are particularly useful for the following kinds of text:</span></span>

- <span data-ttu-id="e0f6a-159">Texte qui contient des guillemets littéraux</span><span class="sxs-lookup"><span data-stu-id="e0f6a-159">Text that contains literal quotation marks</span></span>
- <span data-ttu-id="e0f6a-160">Plusieurs lignes de texte, telles que le texte dans un fichier HTML ou XML</span><span class="sxs-lookup"><span data-stu-id="e0f6a-160">Multiple lines of text, such as the text in an HTML or XML</span></span>
- <span data-ttu-id="e0f6a-161">Texte d’aide d’un script ou d’un document de fonction</span><span class="sxs-lookup"><span data-stu-id="e0f6a-161">The Help text for a script or function document</span></span>

<span data-ttu-id="e0f6a-162">Une chaîne « here » peut avoir l’un des formats suivants, où `<Enter>` représente le caractère masqué de saut de ligne ou de saut de ligne qui est ajouté lorsque vous appuyez sur la touche <kbd>entrée</kbd> .</span><span class="sxs-lookup"><span data-stu-id="e0f6a-162">A here-string can have either of the following formats, where `<Enter>` represents the linefeed or newline hidden character that is added when you press the <kbd>ENTER</kbd> key.</span></span>

<span data-ttu-id="e0f6a-163">Guillemets doubles :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-163">Double-quotes:</span></span>

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

<span data-ttu-id="e0f6a-164">Guillemets simples :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-164">Single-quotes:</span></span>

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

<span data-ttu-id="e0f6a-165">Dans les deux formats, le guillemet fermant doit être le premier caractère de la ligne.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-165">In either format, the closing quotation mark must be the first character in the line.</span></span>

<span data-ttu-id="e0f6a-166">Une chaîne ici contient tout le texte entre les deux caractères masqués.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-166">A here-string contains all the text between the two hidden characters.</span></span> <span data-ttu-id="e0f6a-167">Dans la chaîne here, tous les guillemets sont interprétés littéralement.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-167">In the here-string, all quotation marks are interpreted literally.</span></span> <span data-ttu-id="e0f6a-168">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-168">For example:</span></span>

```powershell
@"
For help, type "get-help"
"@
```

<span data-ttu-id="e0f6a-169">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-169">The output of this command is:</span></span>

```Output
For help, type "get-help"
```

<span data-ttu-id="e0f6a-170">L’utilisation d’une chaîne « here » peut simplifier l’utilisation d’une chaîne dans une commande.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-170">Using a here-string can simplify using a string in a command.</span></span> <span data-ttu-id="e0f6a-171">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-171">For example:</span></span>

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

<span data-ttu-id="e0f6a-172">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-172">The output of this command is:</span></span>

```Output
Use a quotation mark (') to begin a string.
```

<span data-ttu-id="e0f6a-173">Dans les chaînes ici à guillemets simples, les variables sont interprétées littéralement et reproduites exactement.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-173">In single-quoted here-strings, variables are interpreted literally and reproduced exactly.</span></span> <span data-ttu-id="e0f6a-174">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-174">For example:</span></span>

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

<span data-ttu-id="e0f6a-175">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-175">The output of this command is:</span></span>

```Output
The $profile variable contains the path
of your PowerShell profile.
```

<span data-ttu-id="e0f6a-176">Dans les chaînes à deux guillemets (), les variables sont remplacées par leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-176">In double-quoted here-strings, variables are replaced by their values.</span></span> <span data-ttu-id="e0f6a-177">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-177">For example:</span></span>

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

<span data-ttu-id="e0f6a-178">La sortie de cette commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e0f6a-178">The output of this command is:</span></span>

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

<span data-ttu-id="e0f6a-179">Ici-les chaînes sont généralement utilisées pour assigner plusieurs lignes à une variable.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-179">Here-strings are typically used to assign multiple lines to a variable.</span></span> <span data-ttu-id="e0f6a-180">Par exemple, le texte suivant-String affecte une page XML à la variable $page.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-180">For example, the following here-string assigns a page of XML to the $page variable.</span></span>

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

<span data-ttu-id="e0f6a-181">Ici-les chaînes sont également un format pratique pour l’entrée de l’applet de commande `ConvertFrom-StringData` , qui convertit les chaînes ici en tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-181">Here-strings are also a convenient format for input to the `ConvertFrom-StringData` cmdlet, which converts here-strings to hash tables.</span></span>
<span data-ttu-id="e0f6a-182">Pour plus d'informations, consultez `ConvertFrom-StringData`.</span><span class="sxs-lookup"><span data-stu-id="e0f6a-182">For more information, see `ConvertFrom-StringData`.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0f6a-183">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="e0f6a-183">SEE ALSO</span></span>

[<span data-ttu-id="e0f6a-184">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="e0f6a-184">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="e0f6a-185">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="e0f6a-185">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
