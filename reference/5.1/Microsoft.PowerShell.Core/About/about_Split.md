---
description: Explique comment utiliser l’opérateur Split pour fractionner une ou plusieurs chaînes en sous-chaînes.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 12/20/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_split?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Split
ms.openlocfilehash: e93f68265bf560b03ac503ca914a11dde1f6b061
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207537"
---
# <a name="about-split"></a><span data-ttu-id="be3d8-104">À propos du fractionnement</span><span class="sxs-lookup"><span data-stu-id="be3d8-104">About Split</span></span>

## <a name="short-description"></a><span data-ttu-id="be3d8-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="be3d8-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="be3d8-106">Explique comment utiliser l’opérateur Split pour fractionner une ou plusieurs chaînes en sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="be3d8-106">Explains how to use the Split operator to split one or more strings into substrings.</span></span>

## <a name="long-description"></a><span data-ttu-id="be3d8-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="be3d8-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="be3d8-108">L’opérateur split fractionne une ou plusieurs chaînes en sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="be3d8-108">The Split operator splits one or more strings into substrings.</span></span> <span data-ttu-id="be3d8-109">Vous pouvez modifier les éléments suivants de l’opération de fractionnement :</span><span class="sxs-lookup"><span data-stu-id="be3d8-109">You can change the following elements of the Split operation:</span></span>

- <span data-ttu-id="be3d8-110">Limite.</span><span class="sxs-lookup"><span data-stu-id="be3d8-110">Delimiter.</span></span> <span data-ttu-id="be3d8-111">La valeur par défaut est l’espace blanc, mais vous pouvez spécifier des caractères, des chaînes, des modèles ou des blocs de script qui spécifient le délimiteur.</span><span class="sxs-lookup"><span data-stu-id="be3d8-111">The default is whitespace, but you can specify characters, strings, patterns, or script blocks that specify the delimiter.</span></span> <span data-ttu-id="be3d8-112">L’opérateur split dans Windows PowerShell utilise une expression régulière dans le délimiteur, plutôt qu’un caractère simple.</span><span class="sxs-lookup"><span data-stu-id="be3d8-112">The Split operator in Windows PowerShell uses a regular expression in the delimiter, rather than a simple character.</span></span>
- <span data-ttu-id="be3d8-113">Nombre maximal de sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="be3d8-113">Maximum number of substrings.</span></span> <span data-ttu-id="be3d8-114">La valeur par défaut consiste à retourner toutes les sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="be3d8-114">The default is to return all substrings.</span></span> <span data-ttu-id="be3d8-115">Si vous spécifiez un nombre inférieur au nombre de sous-chaînes, les sous-chaînes restantes sont concaténées dans la dernière sous-chaîne.</span><span class="sxs-lookup"><span data-stu-id="be3d8-115">If you specify a number less than the number of substrings, the remaining substrings are concatenated in the last substring.</span></span>
- <span data-ttu-id="be3d8-116">Options qui spécifient les conditions sous lesquelles le délimiteur est mis en correspondance, par exemple SimpleMatch et Multiline.</span><span class="sxs-lookup"><span data-stu-id="be3d8-116">Options that specify the conditions under which the delimiter is matched, such as SimpleMatch and Multiline.</span></span>

## <a name="syntax"></a><span data-ttu-id="be3d8-117">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="be3d8-117">SYNTAX</span></span>

<span data-ttu-id="be3d8-118">Le diagramme suivant illustre la syntaxe de l’opérateur-Split.</span><span class="sxs-lookup"><span data-stu-id="be3d8-118">The following diagram shows the syntax for the -split operator.</span></span>

<span data-ttu-id="be3d8-119">Les noms de paramètres n’apparaissent pas dans la commande.</span><span class="sxs-lookup"><span data-stu-id="be3d8-119">The parameter names do not appear in the command.</span></span> <span data-ttu-id="be3d8-120">N’incluez que les valeurs des paramètres.</span><span class="sxs-lookup"><span data-stu-id="be3d8-120">Include only the parameter values.</span></span> <span data-ttu-id="be3d8-121">Les valeurs doivent apparaître dans l’ordre spécifié dans le diagramme de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="be3d8-121">The values must appear in the order specified in the syntax diagram.</span></span>

```
-Split <String>
-Split (<String[]>)
<String> -Split <Delimiter>[,<Max-substrings>[,"<Options>"]]
<String> -Split {<ScriptBlock>} [,<Max-substrings>]
```

<span data-ttu-id="be3d8-122">Vous pouvez remplacer `-iSplit` ou `-cSplit` par `-split` n’importe quelle instruction de fractionnement binaire (instruction Split incluant un délimiteur ou un bloc de script).</span><span class="sxs-lookup"><span data-stu-id="be3d8-122">You can substitute `-iSplit` or `-cSplit` for `-split` in any binary Split statement (a Split statement that includes a delimiter or script block).</span></span> <span data-ttu-id="be3d8-123">Les `-iSplit` `-split` opérateurs et ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="be3d8-123">The `-iSplit` and `-split` operators are case-insensitive.</span></span> <span data-ttu-id="be3d8-124">L' `-cSplit` opérateur respecte la casse, ce qui signifie que la casse est prise en compte lors de l’application des règles de délimiteur.</span><span class="sxs-lookup"><span data-stu-id="be3d8-124">The `-cSplit` operator is case-sensitive, meaning that case is considered when the delimiter rules are applied.</span></span>

## <a name="parameters"></a><span data-ttu-id="be3d8-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="be3d8-125">PARAMETERS</span></span>

### <a name="string-or-string"></a><span data-ttu-id="be3d8-126">\<String\> ou \<String[]\></span><span class="sxs-lookup"><span data-stu-id="be3d8-126">\<String\> or \<String[]\></span></span>

<span data-ttu-id="be3d8-127">Spécifie une ou plusieurs chaînes à fractionner.</span><span class="sxs-lookup"><span data-stu-id="be3d8-127">Specifies one or more strings to be split.</span></span> <span data-ttu-id="be3d8-128">Si vous envoyez plusieurs chaînes, toutes les chaînes sont fractionnées à l’aide des mêmes règles de délimiteur.</span><span class="sxs-lookup"><span data-stu-id="be3d8-128">If you submit multiple strings, all the strings are split using the same delimiter rules.</span></span>

<span data-ttu-id="be3d8-129">Exemple :</span><span class="sxs-lookup"><span data-stu-id="be3d8-129">Example:</span></span>

```
-split "red yellow blue green"
red
yellow
blue
green
```

### \<Delimiter\>

<span data-ttu-id="be3d8-130">Caractères qui identifient la fin d’une sous-chaîne.</span><span class="sxs-lookup"><span data-stu-id="be3d8-130">The characters that identify the end of a substring.</span></span> <span data-ttu-id="be3d8-131">Le délimiteur par défaut est l’espace blanc, y compris les espaces et les caractères non imprimables, tels que les sauts de ligne ( \` n) et TAB ( \` t).</span><span class="sxs-lookup"><span data-stu-id="be3d8-131">The default delimiter is whitespace, including spaces and non-printable characters, such as newline (\`n) and tab (\`t).</span></span> <span data-ttu-id="be3d8-132">Lorsque les chaînes sont fractionnées, le délimiteur est omis dans toutes les sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="be3d8-132">When the strings are split, the delimiter is omitted from all the substrings.</span></span> <span data-ttu-id="be3d8-133">Exemple :</span><span class="sxs-lookup"><span data-stu-id="be3d8-133">Example:</span></span>

```
"Lastname:FirstName:Address" -split ":"
Lastname
FirstName
Address
```

<span data-ttu-id="be3d8-134">Par défaut, le délimiteur est omis des résultats.</span><span class="sxs-lookup"><span data-stu-id="be3d8-134">By default, the delimiter is omitted from the results.</span></span> <span data-ttu-id="be3d8-135">Pour conserver tout ou partie du délimiteur, mettez entre parenthèses le composant que vous souhaitez conserver.</span><span class="sxs-lookup"><span data-stu-id="be3d8-135">To preserve all or part of the delimiter, enclose in parentheses the part that you want to preserve.</span></span>
<span data-ttu-id="be3d8-136">Si le \<Max-substrings\> paramètre est ajouté, il est prioritaire lorsque votre commande fractionne la collection.</span><span class="sxs-lookup"><span data-stu-id="be3d8-136">If the \<Max-substrings\> parameter is added, this takes precedence when your command splits up the collection.</span></span> <span data-ttu-id="be3d8-137">Si vous choisissez d’inclure un délimiteur dans le cadre de la sortie, la commande renvoie le délimiteur dans le cadre de la sortie ; Toutefois, le fractionnement de la chaîne pour retourner le délimiteur dans le cadre de la sortie n’est pas compté comme une division.</span><span class="sxs-lookup"><span data-stu-id="be3d8-137">If you opt to include a delimiter as part of the output, the command returns the delimiter as part of the output; however, splitting the string to return the delimiter as part of output does not count as a split.</span></span>

<span data-ttu-id="be3d8-138">Exemples :</span><span class="sxs-lookup"><span data-stu-id="be3d8-138">Examples:</span></span>

```
"Lastname:FirstName:Address" -split "(:)"
Lastname
:
FirstName
:
Address

"Lastname/:/FirstName/:/Address" -split "/(:)/"
Lastname
:
FirstName
:
Address
```

<span data-ttu-id="be3d8-139">Dans l’exemple suivant, \<Max-substrings\> a la valeur 3.</span><span class="sxs-lookup"><span data-stu-id="be3d8-139">In the following example, \<Max-substrings\> is set to 3.</span></span> <span data-ttu-id="be3d8-140">Il en résulte trois fractionnements des valeurs de chaîne, mais un total de cinq chaînes dans le résultat obtenu ; le délimiteur est inclus après les fractionnements, jusqu’à ce que le nombre maximal de trois sous-chaînes soit atteint.</span><span class="sxs-lookup"><span data-stu-id="be3d8-140">This results in three splits of the string values, but a total of five strings in the resulting output; the delimiter is included after the splits, until the maximum of three substrings is reached.</span></span> <span data-ttu-id="be3d8-141">Les délimiteurs supplémentaires dans la sous-chaîne finale deviennent partie intégrante de la sous-chaîne.</span><span class="sxs-lookup"><span data-stu-id="be3d8-141">Additional delimiters in the final substring become part of the substring.</span></span>

```powershell
'Chocolate-Vanilla-Strawberry-Blueberry' -split '(-)', 3
```

```output
Chocolate
-
Vanilla
-
Strawberry-Blueberry
```

### \<Max-substrings\>

<span data-ttu-id="be3d8-142">Spécifie le nombre maximal de fois où une chaîne est fractionnée.</span><span class="sxs-lookup"><span data-stu-id="be3d8-142">Specifies the maximum number of times that a string is split.</span></span> <span data-ttu-id="be3d8-143">La valeur par défaut est toutes les sous-chaînes fractionnées par le délimiteur.</span><span class="sxs-lookup"><span data-stu-id="be3d8-143">The default is all the substrings split by the delimiter.</span></span> <span data-ttu-id="be3d8-144">S’il y a plus de sous-chaînes, elles sont concaténées à la sous-chaîne finale.</span><span class="sxs-lookup"><span data-stu-id="be3d8-144">If there are more substrings, they are concatenated to the final substring.</span></span> <span data-ttu-id="be3d8-145">S’il y a moins de sous-chaînes, toutes les sous-chaînes sont retournées.</span><span class="sxs-lookup"><span data-stu-id="be3d8-145">If there are fewer substrings, all the substrings are returned.</span></span> <span data-ttu-id="be3d8-146">La valeur 0 et les valeurs négatives retournent toutes les sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="be3d8-146">A value of 0 and negative values return all the substrings.</span></span>

<span data-ttu-id="be3d8-147">Max-substrings ne spécifie pas le nombre maximal d’objets retournés ; sa valeur est égale au nombre maximal de fois où une chaîne est fractionnée.</span><span class="sxs-lookup"><span data-stu-id="be3d8-147">Max-substrings does not specify the maximum number of objects that are returned; its value equals the maximum number of times that a string is split.</span></span>
<span data-ttu-id="be3d8-148">Si vous envoyez plusieurs chaînes (un tableau de chaînes) à l’opérateur de fractionnement, la limite de nombre maximal de sous-chaînes est appliquée séparément à chaque chaîne.</span><span class="sxs-lookup"><span data-stu-id="be3d8-148">If you submit more than one string (an array of strings) to the Split operator , the Max-substrings limit is applied to each string separately.</span></span>

<span data-ttu-id="be3d8-149">Exemple :</span><span class="sxs-lookup"><span data-stu-id="be3d8-149">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", 5
```

```output
Mercury
Venus
Earth
Mars
Jupiter,Saturn,Uranus,Neptune
```

### \<ScriptBlock\>

<span data-ttu-id="be3d8-150">Expression qui spécifie les règles d’application du délimiteur.</span><span class="sxs-lookup"><span data-stu-id="be3d8-150">An expression that specifies rules for applying the delimiter.</span></span> <span data-ttu-id="be3d8-151">L’expression doit prendre la valeur $true ou $false.</span><span class="sxs-lookup"><span data-stu-id="be3d8-151">The expression must evaluate to $true or $false.</span></span> <span data-ttu-id="be3d8-152">Placez le bloc de script entre accolades.</span><span class="sxs-lookup"><span data-stu-id="be3d8-152">Enclose the script block in braces.</span></span>

<span data-ttu-id="be3d8-153">Exemple :</span><span class="sxs-lookup"><span data-stu-id="be3d8-153">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split {$_ -eq "e" -or $_ -eq "p"}
```

```output
M
rcury,V
nus,
arth,Mars,Ju
it
r,Saturn,Uranus,N

tun
```

### \<Options\>

<span data-ttu-id="be3d8-154">Placez le nom de l’option entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="be3d8-154">Enclose the option name in quotation marks.</span></span> <span data-ttu-id="be3d8-155">Les options ne sont valides que lorsque le \<Max-substrings\> paramètre est utilisé dans l’instruction.</span><span class="sxs-lookup"><span data-stu-id="be3d8-155">Options are valid only when the \<Max-substrings\> parameter is used in the statement.</span></span>

<span data-ttu-id="be3d8-156">La syntaxe du paramètre options est la suivante :</span><span class="sxs-lookup"><span data-stu-id="be3d8-156">The syntax for the Options parameter is:</span></span>

```
"SimpleMatch [,IgnoreCase]"

"[RegexMatch] [,IgnoreCase] [,CultureInvariant]
[,IgnorePatternWhitespace] [,ExplicitCapture]
[,Singleline | ,Multiline]"
```

<span data-ttu-id="be3d8-157">Les options SimpleMatch sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="be3d8-157">The SimpleMatch options are:</span></span>

- <span data-ttu-id="be3d8-158">**SimpleMatch** : utilisez une comparaison de chaînes simple lors de l’évaluation du délimiteur.</span><span class="sxs-lookup"><span data-stu-id="be3d8-158">**SimpleMatch** : Use simple string comparison when evaluating the delimiter.</span></span> <span data-ttu-id="be3d8-159">Ne peut pas être utilisé avec RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="be3d8-159">Cannot be used with RegexMatch.</span></span>
- <span data-ttu-id="be3d8-160">**IgnoreCase** : force la correspondance qui ne respecte pas la casse, même si l’opérateur-cSplit est spécifié.</span><span class="sxs-lookup"><span data-stu-id="be3d8-160">**IgnoreCase** : Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>

<span data-ttu-id="be3d8-161">Les options RegexMatch sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="be3d8-161">The RegexMatch options are:</span></span>

- <span data-ttu-id="be3d8-162">**RegexMatch** : utilisez la correspondance d’expression régulière pour évaluer le délimiteur.</span><span class="sxs-lookup"><span data-stu-id="be3d8-162">**RegexMatch** : Use regular expression matching to evaluate the delimiter.</span></span> <span data-ttu-id="be3d8-163">Il s'agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="be3d8-163">This is the default behavior.</span></span> <span data-ttu-id="be3d8-164">Ne peut pas être utilisé avec SimpleMatch.</span><span class="sxs-lookup"><span data-stu-id="be3d8-164">Cannot be used with SimpleMatch.</span></span>
- <span data-ttu-id="be3d8-165">**IgnoreCase** : force la correspondance qui ne respecte pas la casse, même si l’opérateur-cSplit est spécifié.</span><span class="sxs-lookup"><span data-stu-id="be3d8-165">**IgnoreCase** : Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>
- <span data-ttu-id="be3d8-166">**CultureInvariant** : ignore les différences culturelles dans la langue lorsque vous permettant évaluer le délimiteur.</span><span class="sxs-lookup"><span data-stu-id="be3d8-166">**CultureInvariant** : Ignores cultural differences in language when evaluting the delimiter.</span></span> <span data-ttu-id="be3d8-167">Valide uniquement avec RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="be3d8-167">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="be3d8-168">**IgnorePatternWhitespace** : ignore les espaces blancs sans séquence d’échappement et les commentaires marqués avec le signe dièse (#).</span><span class="sxs-lookup"><span data-stu-id="be3d8-168">**IgnorePatternWhitespace** : Ignores unescaped whitespace and comments marked with the number sign (#).</span></span> <span data-ttu-id="be3d8-169">Valide uniquement avec RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="be3d8-169">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="be3d8-170">**Multiligne** : le mode multiligne force `^` et `$` correspond à la fin de chaque ligne au lieu du début et de la fin de la chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="be3d8-170">**Multiline** : Multiline mode forces `^` and `$` to match the beginning end of every line instead of the beginning and end of the input string.</span></span>
- <span data-ttu-id="be3d8-171">**Singleline** : le mode Singleline traite la chaîne d’entrée comme un *Singleline* .</span><span class="sxs-lookup"><span data-stu-id="be3d8-171">**Singleline** : Singleline mode treats the input string as a *SingleLine* .</span></span>
  <span data-ttu-id="be3d8-172">Elle force le `.` caractère à correspondre à chaque caractère (y compris les nouvelles lignes), au lieu de faire correspondre tous les caractères à l’exception du saut de ligne `\n` .</span><span class="sxs-lookup"><span data-stu-id="be3d8-172">It forces the `.` character to match every character (including newlines), instead of matching every character EXCEPT the newline `\n`.</span></span>
- <span data-ttu-id="be3d8-173">**ExplicitCapture** : ignore les groupes de correspondances sans nom afin que seuls les groupes de capture explicites soient retournés dans la liste de résultats.</span><span class="sxs-lookup"><span data-stu-id="be3d8-173">**ExplicitCapture** : Ignores non-named match groups so that only explicit capture groups are returned in the result list.</span></span> <span data-ttu-id="be3d8-174">Valide uniquement avec RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="be3d8-174">Valid only with RegexMatch.</span></span>

> [!NOTE]
> <span data-ttu-id="be3d8-175">SingleLine est le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="be3d8-175">SingleLine is the default behavior.</span></span> <span data-ttu-id="be3d8-176">Singleline et Multiline ne peuvent pas être utilisés avec le paramètre options.</span><span class="sxs-lookup"><span data-stu-id="be3d8-176">Singleline and Multiline cannot be used together with the options parameter.</span></span> <span data-ttu-id="be3d8-177">Cela a été résolu dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="be3d8-177">This was resolved in PowerShell 6.0.</span></span>
> <span data-ttu-id="be3d8-178">La solution de contournement consiste à utiliser des *modificateurs de mode* dans votre expression régulière.</span><span class="sxs-lookup"><span data-stu-id="be3d8-178">The work around is by using *Mode-Modifiers* in your regular expression.</span></span>
> <span data-ttu-id="be3d8-179">Vous pouvez en savoir plus sur les modificateurs de mode dans les [Options des expressions régulières](/dotnet/standard/base-types/regular-expression-options)</span><span class="sxs-lookup"><span data-stu-id="be3d8-179">You can read more about mode modifiers in [Regular Expression Options](/dotnet/standard/base-types/regular-expression-options)</span></span>

## <a name="unary-and-binary-split-operators"></a><span data-ttu-id="be3d8-180">OPÉRATEURS unaires et de FRACTIONNEment binaire</span><span class="sxs-lookup"><span data-stu-id="be3d8-180">UNARY and BINARY SPLIT OPERATORS</span></span>

<span data-ttu-id="be3d8-181">L’opérateur de fractionnement unaire ( `-split <string>` ) a une priorité plus élevée qu’une virgule.</span><span class="sxs-lookup"><span data-stu-id="be3d8-181">The unary split operator (`-split <string>`) has higher precedence than a comma.</span></span> <span data-ttu-id="be3d8-182">Par conséquent, si vous soumettez une liste de chaînes séparées par des virgules à l’opérateur de fractionnement unaire, seule la première chaîne (avant la première virgule) est fractionnée.</span><span class="sxs-lookup"><span data-stu-id="be3d8-182">As a result, if you submit a comma-separated list of strings to the unary split operator, only the first string (before the first comma) is split.</span></span>

<span data-ttu-id="be3d8-183">Utilisez l’un des modèles suivants pour fractionner plus d’une chaîne :</span><span class="sxs-lookup"><span data-stu-id="be3d8-183">Use one of the following patterns to split more than one string:</span></span>

- <span data-ttu-id="be3d8-184">Utiliser l’opérateur de fractionnement binaire ( \<string[]\> -Split \<delimiter\> )</span><span class="sxs-lookup"><span data-stu-id="be3d8-184">Use the binary split operator (\<string[]\> -split \<delimiter\>)</span></span>
- <span data-ttu-id="be3d8-185">Placez toutes les chaînes entre parenthèses</span><span class="sxs-lookup"><span data-stu-id="be3d8-185">Enclose all the strings in parentheses</span></span>
- <span data-ttu-id="be3d8-186">Stocke les chaînes dans une variable, puis soumet la variable à l’opérateur Split</span><span class="sxs-lookup"><span data-stu-id="be3d8-186">Store the strings in a variable then submit the variable to the split operator</span></span>

<span data-ttu-id="be3d8-187">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="be3d8-187">Consider the following example:</span></span>

```
PS> -split "1 2", "a b"
1
2
a b
```

```
PS> "1 2", "a b" -split " "
1
2
a
b
```

```
PS> -split ("1 2", "a b")
1
2
a
b
```

```
PS> $a = "1 2", "a b"
PS> -split $a
1
2
a
b
```

## <a name="examples"></a><span data-ttu-id="be3d8-188">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="be3d8-188">EXAMPLES</span></span>

<span data-ttu-id="be3d8-189">L’instruction suivante fractionne la chaîne à l’espace blanc.</span><span class="sxs-lookup"><span data-stu-id="be3d8-189">The following statement splits the string at whitespace.</span></span>

```powershell
-split "Windows PowerShell 2.0`nWindows PowerShell with remoting"
```

```output

Windows
PowerShell
2.0
Windows
PowerShell
with
remoting
```

<span data-ttu-id="be3d8-190">L’instruction suivante fractionne la chaîne à n’importe quelle virgule.</span><span class="sxs-lookup"><span data-stu-id="be3d8-190">The following statement splits the string at any comma.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split ','
```

```output
Mercury
Venus
Earth
Mars
Jupiter
Saturn
Uranus
Neptune
```

<span data-ttu-id="be3d8-191">L’instruction suivante fractionne la chaîne au modèle « er ».</span><span class="sxs-lookup"><span data-stu-id="be3d8-191">The following statement splits the string at the pattern "er".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split 'er'
```

```output
M
cury,Venus,Earth,Mars,Jupit
,Saturn,Uranus,Neptune
```

<span data-ttu-id="be3d8-192">L’instruction suivante effectue un fractionnement sensible à la casse à la lettre « N ».</span><span class="sxs-lookup"><span data-stu-id="be3d8-192">The following statement performs a case-sensitive split at the letter "N".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -cSplit 'N'
```

```output
Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,
eptune
```

<span data-ttu-id="be3d8-193">L’instruction suivante fractionne la chaîne à « e » et « t ».</span><span class="sxs-lookup"><span data-stu-id="be3d8-193">The following statement splits the string at "e" and "t".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[et]'
```

```output
M
rcury,V
nus,
ar
h,Mars,Jupi

r,Sa
urn,Uranus,N
p
un
```

<span data-ttu-id="be3d8-194">L’instruction suivante fractionne la chaîne à « e » et « r », mais limite les sous-chaînes résultantes à six sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="be3d8-194">The following statement splits the string at "e" and "r", but limits the resulting substrings to six substrings.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[er]', 6
```

```output
M

cu
y,V
nus,
arth,Mars,Jupiter,Saturn,Uranus,Neptune
```

<span data-ttu-id="be3d8-195">L’instruction suivante fractionne une chaîne en trois sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="be3d8-195">The following statement splits a string into three substrings.</span></span>

```powershell
"a,b,c,d,e,f,g,h" -split ",", 3
```

```output
a
b
c,d,e,f,g,h
```

<span data-ttu-id="be3d8-196">L’instruction suivante fractionne deux chaînes en trois sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="be3d8-196">The following statement splits two strings into three substrings.</span></span>
<span data-ttu-id="be3d8-197">(La limite est appliquée indépendamment à chaque chaîne.)</span><span class="sxs-lookup"><span data-stu-id="be3d8-197">(The limit is applied to each string independently.)</span></span>

```powershell
"a,b,c,d", "e,f,g,h" -split ",", 3
```

```output
a
b
c,d
e
f
g,h
```

<span data-ttu-id="be3d8-198">L’instruction suivante fractionne chaque ligne de la chaîne ici au premier chiffre.</span><span class="sxs-lookup"><span data-stu-id="be3d8-198">The following statement splits each line in the here-string at the first digit.</span></span> <span data-ttu-id="be3d8-199">Elle utilise l’option Multiline pour reconnaître le début de chaque ligne et chaîne.</span><span class="sxs-lookup"><span data-stu-id="be3d8-199">It uses the Multiline option to recognize the beginning of each line and string.</span></span>

<span data-ttu-id="be3d8-200">Le 0 représente la valeur « Return All » du paramètre Max-substrings.</span><span class="sxs-lookup"><span data-stu-id="be3d8-200">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="be3d8-201">Vous pouvez utiliser des options, telles que Multiline, uniquement lorsque la valeur Max-substrings est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="be3d8-201">You can use options, such as Multiline, only when the Max-substrings value is specified.</span></span>

```powershell
$a = @'
1The first line.
2The second line.
3The third of three lines.
'@
$a -split "^\d", 0, "multiline"
```

```output

The first line.

The second line.

The third of three lines.
```

<span data-ttu-id="be3d8-202">L’instruction suivante utilise la barre oblique inverse pour échapper le séparateur de points (.).</span><span class="sxs-lookup"><span data-stu-id="be3d8-202">The following statement uses the backslash character to escape the dot (.) delimiter.</span></span>

<span data-ttu-id="be3d8-203">Avec la valeur par défaut, RegexMatch, le point placé entre guillemets (".") est interprété pour correspondre à n’importe quel caractère, à l’exception d’un caractère de saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="be3d8-203">With the default, RegexMatch, the dot enclosed in quotation marks (".") is interpreted to match any character except for a newline character.</span></span> <span data-ttu-id="be3d8-204">Par conséquent, l’instruction Split retourne une ligne vide pour chaque caractère à l’exception de NewLine.</span><span class="sxs-lookup"><span data-stu-id="be3d8-204">As a result, the Split statement returns a blank line for every character except newline.</span></span>

```powershell
"This.is.a.test" -split "\."
```

```output
This
is
a
test
```

<span data-ttu-id="be3d8-205">L’instruction suivante utilise l’option SimpleMatch pour indiquer à l’opérateur-split d’interpréter le délimiteur de point (.) littéralement.</span><span class="sxs-lookup"><span data-stu-id="be3d8-205">The following statement uses the SimpleMatch option to direct the -split operator to interpret the dot (.) delimiter literally.</span></span>

<span data-ttu-id="be3d8-206">Le 0 représente la valeur « Return All » du paramètre Max-substrings.</span><span class="sxs-lookup"><span data-stu-id="be3d8-206">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="be3d8-207">Vous pouvez utiliser des options, telles que SimpleMatch, uniquement lorsque la valeur Max-substrings est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="be3d8-207">You can use options, such as SimpleMatch, only when the Max-substrings value is specified.</span></span>

```powershell
"This.is.a.test" -split ".", 0, "simplematch"
```

```output
This
is
a
test
```

<span data-ttu-id="be3d8-208">L’instruction suivante fractionne la chaîne à l’un des deux délimiteurs, en fonction de la valeur d’une variable.</span><span class="sxs-lookup"><span data-stu-id="be3d8-208">The following statement splits the string at one of two delimiters, depending on the value of a variable.</span></span>

```powershell
$i = 1
$c = "LastName, FirstName; Address, City, State, Zip"
$c -split $(if ($i -lt 1) {","} else {";"})
```

```output
LastName, FirstName
 Address, City, State, Zip
```

## <a name="see-also"></a><span data-ttu-id="be3d8-209">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="be3d8-209">SEE ALSO</span></span>

[<span data-ttu-id="be3d8-210">Split-Path</span><span class="sxs-lookup"><span data-stu-id="be3d8-210">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)

[<span data-ttu-id="be3d8-211">about_Operators</span><span class="sxs-lookup"><span data-stu-id="be3d8-211">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="be3d8-212">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="be3d8-212">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="be3d8-213">about_Join</span><span class="sxs-lookup"><span data-stu-id="be3d8-213">about_Join</span></span>](about_Join.md)
