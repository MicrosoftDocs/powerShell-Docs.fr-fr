---
description: Explique comment utiliser l’opérateur Split pour fractionner une ou plusieurs chaînes en sous-chaînes.
Locale: en-US
ms.date: 03/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_split?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Split
ms.openlocfilehash: c7944c710ae3b6803772de77f50b639de4953340
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596130"
---
# <a name="about-split"></a><span data-ttu-id="bda27-103">À propos du fractionnement</span><span class="sxs-lookup"><span data-stu-id="bda27-103">About Split</span></span>

## <a name="short-description"></a><span data-ttu-id="bda27-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="bda27-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="bda27-105">Explique comment utiliser l’opérateur Split pour fractionner une ou plusieurs chaînes en sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="bda27-105">Explains how to use the Split operator to split one or more strings into substrings.</span></span>

## <a name="long-description"></a><span data-ttu-id="bda27-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="bda27-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="bda27-107">L’opérateur split fractionne une ou plusieurs chaînes en sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="bda27-107">The Split operator splits one or more strings into substrings.</span></span> <span data-ttu-id="bda27-108">Vous pouvez modifier les éléments suivants de l’opération de fractionnement :</span><span class="sxs-lookup"><span data-stu-id="bda27-108">You can change the following elements of the Split operation:</span></span>

- <span data-ttu-id="bda27-109">Limite.</span><span class="sxs-lookup"><span data-stu-id="bda27-109">Delimiter.</span></span> <span data-ttu-id="bda27-110">La valeur par défaut est l’espace blanc, mais vous pouvez spécifier des caractères, des chaînes, des modèles ou des blocs de script qui spécifient le délimiteur.</span><span class="sxs-lookup"><span data-stu-id="bda27-110">The default is whitespace, but you can specify characters, strings, patterns, or script blocks that specify the delimiter.</span></span> <span data-ttu-id="bda27-111">L’opérateur split dans PowerShell utilise une expression régulière dans le délimiteur, plutôt qu’un caractère simple.</span><span class="sxs-lookup"><span data-stu-id="bda27-111">The Split operator in PowerShell uses a regular expression in the delimiter, rather than a simple character.</span></span>
- <span data-ttu-id="bda27-112">Nombre maximal de sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="bda27-112">Maximum number of substrings.</span></span> <span data-ttu-id="bda27-113">La valeur par défaut consiste à retourner toutes les sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="bda27-113">The default is to return all substrings.</span></span> <span data-ttu-id="bda27-114">Si vous spécifiez un nombre inférieur au nombre de sous-chaînes, les sous-chaînes restantes sont concaténées dans la dernière sous-chaîne.</span><span class="sxs-lookup"><span data-stu-id="bda27-114">If you specify a number less than the number of substrings, the remaining substrings are concatenated in the last substring.</span></span>
- <span data-ttu-id="bda27-115">Options qui spécifient les conditions sous lesquelles le délimiteur est mis en correspondance, par exemple SimpleMatch et Multiline.</span><span class="sxs-lookup"><span data-stu-id="bda27-115">Options that specify the conditions under which the delimiter is matched, such as SimpleMatch and Multiline.</span></span>

## <a name="syntax"></a><span data-ttu-id="bda27-116">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="bda27-116">SYNTAX</span></span>

<span data-ttu-id="bda27-117">Le diagramme suivant illustre la syntaxe de l’opérateur-Split.</span><span class="sxs-lookup"><span data-stu-id="bda27-117">The following diagram shows the syntax for the -split operator.</span></span>

<span data-ttu-id="bda27-118">Les noms de paramètres n’apparaissent pas dans la commande.</span><span class="sxs-lookup"><span data-stu-id="bda27-118">The parameter names do not appear in the command.</span></span> <span data-ttu-id="bda27-119">N’incluez que les valeurs des paramètres.</span><span class="sxs-lookup"><span data-stu-id="bda27-119">Include only the parameter values.</span></span> <span data-ttu-id="bda27-120">Les valeurs doivent apparaître dans l’ordre spécifié dans le diagramme de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="bda27-120">The values must appear in the order specified in the syntax diagram.</span></span>

```
-Split <String>
-Split (<String[]>)
<String> -Split <Delimiter>[,<Max-substrings>[,"<Options>"]]
<String> -Split {<ScriptBlock>} [,<Max-substrings>]
```

<span data-ttu-id="bda27-121">Vous pouvez remplacer `-iSplit` ou `-cSplit` par `-split` n’importe quelle instruction de fractionnement binaire (instruction Split incluant un délimiteur ou un bloc de script).</span><span class="sxs-lookup"><span data-stu-id="bda27-121">You can substitute `-iSplit` or `-cSplit` for `-split` in any binary Split statement (a Split statement that includes a delimiter or script block).</span></span> <span data-ttu-id="bda27-122">Les `-iSplit` `-split` opérateurs et ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="bda27-122">The `-iSplit` and `-split` operators are case-insensitive.</span></span> <span data-ttu-id="bda27-123">L' `-cSplit` opérateur respecte la casse, ce qui signifie que la casse est prise en compte lors de l’application des règles de délimiteur.</span><span class="sxs-lookup"><span data-stu-id="bda27-123">The `-cSplit` operator is case-sensitive, meaning that case is considered when the delimiter rules are applied.</span></span>

## <a name="parameters"></a><span data-ttu-id="bda27-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bda27-124">PARAMETERS</span></span>

### <a name="string-or-string"></a><span data-ttu-id="bda27-125">\<String\> ou \<String[]\></span><span class="sxs-lookup"><span data-stu-id="bda27-125">\<String\> or \<String[]\></span></span>

<span data-ttu-id="bda27-126">Spécifie une ou plusieurs chaînes à fractionner.</span><span class="sxs-lookup"><span data-stu-id="bda27-126">Specifies one or more strings to be split.</span></span> <span data-ttu-id="bda27-127">Si vous envoyez plusieurs chaînes, toutes les chaînes sont fractionnées à l’aide des mêmes règles de délimiteur.</span><span class="sxs-lookup"><span data-stu-id="bda27-127">If you submit multiple strings, all the strings are split using the same delimiter rules.</span></span>

<span data-ttu-id="bda27-128">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bda27-128">Example:</span></span>

```
-split "red yellow blue green"
red
yellow
blue
green
```

### \<Delimiter\>

<span data-ttu-id="bda27-129">Caractères qui identifient la fin d’une sous-chaîne.</span><span class="sxs-lookup"><span data-stu-id="bda27-129">The characters that identify the end of a substring.</span></span> <span data-ttu-id="bda27-130">Le délimiteur par défaut est l’espace blanc, y compris les espaces et les caractères non imprimables, tels que les sauts de ligne ( \` n) et TAB ( \` t).</span><span class="sxs-lookup"><span data-stu-id="bda27-130">The default delimiter is whitespace, including spaces and non-printable characters, such as newline (\`n) and tab (\`t).</span></span> <span data-ttu-id="bda27-131">Lorsque les chaînes sont fractionnées, le délimiteur est omis dans toutes les sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="bda27-131">When the strings are split, the delimiter is omitted from all the substrings.</span></span> <span data-ttu-id="bda27-132">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bda27-132">Example:</span></span>

```
"Lastname:FirstName:Address" -split ":"
Lastname
FirstName
Address
```

<span data-ttu-id="bda27-133">Par défaut, le délimiteur est omis des résultats.</span><span class="sxs-lookup"><span data-stu-id="bda27-133">By default, the delimiter is omitted from the results.</span></span> <span data-ttu-id="bda27-134">Pour conserver tout ou partie du délimiteur, mettez entre parenthèses le composant que vous souhaitez conserver.</span><span class="sxs-lookup"><span data-stu-id="bda27-134">To preserve all or part of the delimiter, enclose in parentheses the part that you want to preserve.</span></span>
<span data-ttu-id="bda27-135">Si le \<Max-substrings\> paramètre est ajouté, il est prioritaire lorsque votre commande fractionne la collection.</span><span class="sxs-lookup"><span data-stu-id="bda27-135">If the \<Max-substrings\> parameter is added, this takes precedence when your command splits up the collection.</span></span> <span data-ttu-id="bda27-136">Si vous choisissez d’inclure un délimiteur dans le cadre de la sortie, la commande renvoie le délimiteur dans le cadre de la sortie ; Toutefois, le fractionnement de la chaîne pour retourner le délimiteur dans le cadre de la sortie n’est pas compté comme une division.</span><span class="sxs-lookup"><span data-stu-id="bda27-136">If you opt to include a delimiter as part of the output, the command returns the delimiter as part of the output; however, splitting the string to return the delimiter as part of output does not count as a split.</span></span>

<span data-ttu-id="bda27-137">Exemples :</span><span class="sxs-lookup"><span data-stu-id="bda27-137">Examples:</span></span>

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

<span data-ttu-id="bda27-138">Dans l’exemple suivant, \<Max-substrings\> a la valeur 3.</span><span class="sxs-lookup"><span data-stu-id="bda27-138">In the following example, \<Max-substrings\> is set to 3.</span></span> <span data-ttu-id="bda27-139">Il en résulte trois fractionnements des valeurs de chaîne, mais un total de cinq chaînes dans le résultat obtenu ; le délimiteur est inclus après les fractionnements, jusqu’à ce que le nombre maximal de trois sous-chaînes soit atteint.</span><span class="sxs-lookup"><span data-stu-id="bda27-139">This results in three splits of the string values, but a total of five strings in the resulting output; the delimiter is included after the splits, until the maximum of three substrings is reached.</span></span> <span data-ttu-id="bda27-140">Les délimiteurs supplémentaires dans la sous-chaîne finale deviennent partie intégrante de la sous-chaîne.</span><span class="sxs-lookup"><span data-stu-id="bda27-140">Additional delimiters in the final substring become part of the substring.</span></span>

```powershell
'Chocolate-Vanilla-Strawberry-Blueberry' -split '(-)', 3
```

```Output
Chocolate
-
Vanilla
-
Strawberry-Blueberry
```

### \<Max-substrings\>

<span data-ttu-id="bda27-141">Spécifie le nombre maximal de fois où une chaîne est fractionnée.</span><span class="sxs-lookup"><span data-stu-id="bda27-141">Specifies the maximum number of times that a string is split.</span></span> <span data-ttu-id="bda27-142">La valeur par défaut est toutes les sous-chaînes fractionnées par le délimiteur.</span><span class="sxs-lookup"><span data-stu-id="bda27-142">The default is all the substrings split by the delimiter.</span></span> <span data-ttu-id="bda27-143">S’il y a plus de sous-chaînes, elles sont concaténées à la sous-chaîne finale.</span><span class="sxs-lookup"><span data-stu-id="bda27-143">If there are more substrings, they are concatenated to the final substring.</span></span> <span data-ttu-id="bda27-144">S’il y a moins de sous-chaînes, toutes les sous-chaînes sont retournées.</span><span class="sxs-lookup"><span data-stu-id="bda27-144">If there are fewer substrings, all the substrings are returned.</span></span> <span data-ttu-id="bda27-145">La valeur 0 retourne toutes les sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="bda27-145">A value of 0 returns all the substrings.</span></span> <span data-ttu-id="bda27-146">Les valeurs négatives retournent la quantité de sous-chaînes demandée à partir de la fin de la chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="bda27-146">Negative values return the amount of substrings requested starting from the end of the input string.</span></span>

> [!NOTE]
> <span data-ttu-id="bda27-147">La prise en charge des valeurs négatives a été ajoutée dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="bda27-147">Support for negative values was added in PowerShell 7.</span></span>

<span data-ttu-id="bda27-148">**Max-substrings** ne spécifie pas le nombre maximal d’objets retournés.</span><span class="sxs-lookup"><span data-stu-id="bda27-148">**Max-substrings** does not specify the maximum number of objects that are returned.</span></span> <span data-ttu-id="bda27-149">Sa valeur est égale au nombre maximal de fois où une chaîne est fractionnée.</span><span class="sxs-lookup"><span data-stu-id="bda27-149">Its value equals the maximum number of times that a string is split.</span></span>
<span data-ttu-id="bda27-150">Si vous envoyez plusieurs chaînes (un tableau de chaînes) à l' `-split` opérateur, la limite de la sous **-chaîne Max** est appliquée séparément à chaque chaîne.</span><span class="sxs-lookup"><span data-stu-id="bda27-150">If you submit more than one string (an array of strings) to the `-split` operator, the **Max-substrings** limit is applied to each string separately.</span></span>

<span data-ttu-id="bda27-151">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bda27-151">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", 5
```

```Output
Mercury
Venus
Earth
Mars
Jupiter,Saturn,Uranus,Neptune
```

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", -5
```

```Output
Mercury,Venus,Earth,Mars
Jupiter
Saturn
Uranus
Neptune
```

### \<ScriptBlock\>

<span data-ttu-id="bda27-152">Expression qui spécifie les règles d’application du délimiteur.</span><span class="sxs-lookup"><span data-stu-id="bda27-152">An expression that specifies rules for applying the delimiter.</span></span> <span data-ttu-id="bda27-153">L’expression doit prendre la valeur $true ou $false.</span><span class="sxs-lookup"><span data-stu-id="bda27-153">The expression must evaluate to $true or $false.</span></span> <span data-ttu-id="bda27-154">Placez le bloc de script entre accolades.</span><span class="sxs-lookup"><span data-stu-id="bda27-154">Enclose the script block in braces.</span></span>

<span data-ttu-id="bda27-155">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bda27-155">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split {$_ -eq "e" -or $_ -eq "p"}
```

```Output
M
rcury,V
nus,
arth,Mars,Ju
it
r,Saturn,Uranus,N

tun
```

### \<Options\>

<span data-ttu-id="bda27-156">Placez le nom de l’option entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="bda27-156">Enclose the option name in quotation marks.</span></span> <span data-ttu-id="bda27-157">Les options ne sont valides que lorsque le \<Max-substrings\> paramètre est utilisé dans l’instruction.</span><span class="sxs-lookup"><span data-stu-id="bda27-157">Options are valid only when the \<Max-substrings\> parameter is used in the statement.</span></span>

<span data-ttu-id="bda27-158">La syntaxe du paramètre options est la suivante :</span><span class="sxs-lookup"><span data-stu-id="bda27-158">The syntax for the Options parameter is:</span></span>

```
"SimpleMatch [,IgnoreCase]"

"[RegexMatch] [,IgnoreCase] [,CultureInvariant]
[,IgnorePatternWhitespace] [,ExplicitCapture]
[,Singleline | ,Multiline]"
```

<span data-ttu-id="bda27-159">Les options SimpleMatch sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bda27-159">The SimpleMatch options are:</span></span>

- <span data-ttu-id="bda27-160">**SimpleMatch**: utilisez une comparaison de chaînes simple lors de l’évaluation du délimiteur.</span><span class="sxs-lookup"><span data-stu-id="bda27-160">**SimpleMatch**: Use simple string comparison when evaluating the delimiter.</span></span> <span data-ttu-id="bda27-161">Ne peut pas être utilisé avec RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="bda27-161">Cannot be used with RegexMatch.</span></span>
- <span data-ttu-id="bda27-162">**IgnoreCase**: force la correspondance qui ne respecte pas la casse, même si l’opérateur-cSplit est spécifié.</span><span class="sxs-lookup"><span data-stu-id="bda27-162">**IgnoreCase**: Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>

<span data-ttu-id="bda27-163">Les options RegexMatch sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bda27-163">The RegexMatch options are:</span></span>

- <span data-ttu-id="bda27-164">**RegexMatch**: utilisez la correspondance d’expression régulière pour évaluer le délimiteur.</span><span class="sxs-lookup"><span data-stu-id="bda27-164">**RegexMatch**: Use regular expression matching to evaluate the delimiter.</span></span> <span data-ttu-id="bda27-165">Il s'agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="bda27-165">This is the default behavior.</span></span> <span data-ttu-id="bda27-166">Ne peut pas être utilisé avec SimpleMatch.</span><span class="sxs-lookup"><span data-stu-id="bda27-166">Cannot be used with SimpleMatch.</span></span>
- <span data-ttu-id="bda27-167">**IgnoreCase**: force la correspondance qui ne respecte pas la casse, même si l’opérateur-cSplit est spécifié.</span><span class="sxs-lookup"><span data-stu-id="bda27-167">**IgnoreCase**: Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>
- <span data-ttu-id="bda27-168">**CultureInvariant**: ignore les différences culturelles dans la langue lorsque vous permettant évaluer le délimiteur.</span><span class="sxs-lookup"><span data-stu-id="bda27-168">**CultureInvariant**: Ignores cultural differences in language when evaluting the delimiter.</span></span> <span data-ttu-id="bda27-169">Valide uniquement avec RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="bda27-169">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="bda27-170">**IgnorePatternWhitespace**: ignore les espaces blancs sans séquence d’échappement et les commentaires marqués avec le signe dièse (#).</span><span class="sxs-lookup"><span data-stu-id="bda27-170">**IgnorePatternWhitespace**: Ignores unescaped whitespace and comments marked with the number sign (#).</span></span> <span data-ttu-id="bda27-171">Valide uniquement avec RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="bda27-171">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="bda27-172">**Multiligne**: le mode multiligne force `^` et `$` correspond à la fin de chaque ligne au lieu du début et de la fin de la chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="bda27-172">**Multiline**: Multiline mode forces `^` and `$` to match the beginning end of every line instead of the beginning and end of the input string.</span></span>
- <span data-ttu-id="bda27-173">**Singleline**: le mode Singleline traite la chaîne d’entrée comme un *Singleline*.</span><span class="sxs-lookup"><span data-stu-id="bda27-173">**Singleline**: Singleline mode treats the input string as a *SingleLine*.</span></span>
  <span data-ttu-id="bda27-174">Elle force le `.` caractère à correspondre à chaque caractère (y compris les nouvelles lignes), au lieu de faire correspondre tous les caractères à l’exception du saut de ligne `\n` .</span><span class="sxs-lookup"><span data-stu-id="bda27-174">It forces the `.` character to match every character (including newlines), instead of matching every character EXCEPT the newline `\n`.</span></span>
- <span data-ttu-id="bda27-175">**ExplicitCapture**: ignore les groupes de correspondances sans nom afin que seuls les groupes de capture explicites soient retournés dans la liste de résultats.</span><span class="sxs-lookup"><span data-stu-id="bda27-175">**ExplicitCapture**: Ignores non-named match groups so that only explicit capture groups are returned in the result list.</span></span> <span data-ttu-id="bda27-176">Valide uniquement avec RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="bda27-176">Valid only with RegexMatch.</span></span>

## <a name="unary-and-binary-split-operators"></a><span data-ttu-id="bda27-177">OPÉRATEURS unaires et de FRACTIONNEment binaire</span><span class="sxs-lookup"><span data-stu-id="bda27-177">UNARY and BINARY SPLIT OPERATORS</span></span>

<span data-ttu-id="bda27-178">L’opérateur de fractionnement unaire ( `-split <string>` ) a une priorité plus élevée qu’une virgule.</span><span class="sxs-lookup"><span data-stu-id="bda27-178">The unary split operator (`-split <string>`) has higher precedence than a comma.</span></span> <span data-ttu-id="bda27-179">Par conséquent, si vous soumettez une liste de chaînes séparées par des virgules à l’opérateur de fractionnement unaire, seule la première chaîne (avant la première virgule) est fractionnée.</span><span class="sxs-lookup"><span data-stu-id="bda27-179">As a result, if you submit a comma-separated list of strings to the unary split operator, only the first string (before the first comma) is split.</span></span>

<span data-ttu-id="bda27-180">Utilisez l’un des modèles suivants pour fractionner plus d’une chaîne :</span><span class="sxs-lookup"><span data-stu-id="bda27-180">Use one of the following patterns to split more than one string:</span></span>

- <span data-ttu-id="bda27-181">Utiliser l’opérateur de fractionnement binaire ( \<string[]\> -Split \<delimiter\> )</span><span class="sxs-lookup"><span data-stu-id="bda27-181">Use the binary split operator (\<string[]\> -split \<delimiter\>)</span></span>
- <span data-ttu-id="bda27-182">Placez toutes les chaînes entre parenthèses</span><span class="sxs-lookup"><span data-stu-id="bda27-182">Enclose all the strings in parentheses</span></span>
- <span data-ttu-id="bda27-183">Stocke les chaînes dans une variable, puis soumet la variable à l’opérateur Split</span><span class="sxs-lookup"><span data-stu-id="bda27-183">Store the strings in a variable then submit the variable to the split operator</span></span>

<span data-ttu-id="bda27-184">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="bda27-184">Consider the following example:</span></span>

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

## <a name="examples"></a><span data-ttu-id="bda27-185">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="bda27-185">EXAMPLES</span></span>

<span data-ttu-id="bda27-186">L’instruction suivante fractionne la chaîne à l’espace blanc.</span><span class="sxs-lookup"><span data-stu-id="bda27-186">The following statement splits the string at whitespace.</span></span>

```powershell
-split "Windows PowerShell 2.0`nWindows PowerShell with remoting"
```

```Output

Windows
PowerShell
2.0
Windows
PowerShell
with
remoting
```

<span data-ttu-id="bda27-187">L’instruction suivante fractionne la chaîne à n’importe quelle virgule.</span><span class="sxs-lookup"><span data-stu-id="bda27-187">The following statement splits the string at any comma.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split ','
```

```Output
Mercury
Venus
Earth
Mars
Jupiter
Saturn
Uranus
Neptune
```

<span data-ttu-id="bda27-188">L’instruction suivante fractionne la chaîne au modèle « er ».</span><span class="sxs-lookup"><span data-stu-id="bda27-188">The following statement splits the string at the pattern "er".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split 'er'
```

```Output
M
cury,Venus,Earth,Mars,Jupit
,Saturn,Uranus,Neptune
```

<span data-ttu-id="bda27-189">L’instruction suivante effectue un fractionnement sensible à la casse à la lettre « N ».</span><span class="sxs-lookup"><span data-stu-id="bda27-189">The following statement performs a case-sensitive split at the letter "N".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -cSplit 'N'
```

```Output
Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,
eptune
```

<span data-ttu-id="bda27-190">L’instruction suivante fractionne la chaîne à « e » et « t ».</span><span class="sxs-lookup"><span data-stu-id="bda27-190">The following statement splits the string at "e" and "t".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[et]'
```

```Output
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

<span data-ttu-id="bda27-191">L’instruction suivante fractionne la chaîne à « e » et « r », mais limite les sous-chaînes résultantes à six sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="bda27-191">The following statement splits the string at "e" and "r", but limits the resulting substrings to six substrings.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[er]', 6
```

```Output
M

cu
y,V
nus,
arth,Mars,Jupiter,Saturn,Uranus,Neptune
```

<span data-ttu-id="bda27-192">L’instruction suivante fractionne une chaîne en trois sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="bda27-192">The following statement splits a string into three substrings.</span></span>

```powershell
"a,b,c,d,e,f,g,h" -split ",", 3
```

```Output
a
b
c,d,e,f,g,h
```

<span data-ttu-id="bda27-193">L’instruction suivante fractionne une chaîne en trois sous-chaînes à partir de la fin de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="bda27-193">The following statement splits a string into three substrings starting from the end of the string.</span></span>

```powershell
"a,b,c,d,e,f,g,h" -split ",", -3
```

```Output
a,b,c,d,e,f
g
h
```

<span data-ttu-id="bda27-194">L’instruction suivante fractionne deux chaînes en trois sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="bda27-194">The following statement splits two strings into three substrings.</span></span>
<span data-ttu-id="bda27-195">(La limite est appliquée indépendamment à chaque chaîne.)</span><span class="sxs-lookup"><span data-stu-id="bda27-195">(The limit is applied to each string independently.)</span></span>

```powershell
"a,b,c,d", "e,f,g,h" -split ",", 3
```

```Output
a
b
c,d
e
f
g,h
```

<span data-ttu-id="bda27-196">L’instruction suivante fractionne chaque ligne de la chaîne ici au premier chiffre.</span><span class="sxs-lookup"><span data-stu-id="bda27-196">The following statement splits each line in the here-string at the first digit.</span></span> <span data-ttu-id="bda27-197">Elle utilise l’option Multiline pour reconnaître le début de chaque ligne et chaîne.</span><span class="sxs-lookup"><span data-stu-id="bda27-197">It uses the Multiline option to recognize the beginning of each line and string.</span></span>

<span data-ttu-id="bda27-198">Le 0 représente la valeur « Return All » du paramètre Max-substrings.</span><span class="sxs-lookup"><span data-stu-id="bda27-198">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="bda27-199">Vous pouvez utiliser des options, telles que Multiline, uniquement lorsque la valeur Max-substrings est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bda27-199">You can use options, such as Multiline, only when the Max-substrings value is specified.</span></span>

```powershell
$a = @'
1The first line.
2The second line.
3The third of three lines.
'@
$a -split "^\d", 0, "multiline"
```

```Output

The first line.

The second line.

The third of three lines.
```

<span data-ttu-id="bda27-200">L’instruction suivante utilise la barre oblique inverse pour échapper le séparateur de points (.).</span><span class="sxs-lookup"><span data-stu-id="bda27-200">The following statement uses the backslash character to escape the dot (.) delimiter.</span></span>

<span data-ttu-id="bda27-201">Avec la valeur par défaut, RegexMatch, le point placé entre guillemets (".") est interprété pour correspondre à n’importe quel caractère, à l’exception d’un caractère de saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="bda27-201">With the default, RegexMatch, the dot enclosed in quotation marks (".") is interpreted to match any character except for a newline character.</span></span> <span data-ttu-id="bda27-202">Par conséquent, l’instruction Split retourne une ligne vide pour chaque caractère à l’exception de NewLine.</span><span class="sxs-lookup"><span data-stu-id="bda27-202">As a result, the Split statement returns a blank line for every character except newline.</span></span>

```powershell
"This.is.a.test" -split "\."
```

```Output
This
is
a
test
```

<span data-ttu-id="bda27-203">L’instruction suivante utilise l’option SimpleMatch pour indiquer à l’opérateur-split d’interpréter le délimiteur de point (.) littéralement.</span><span class="sxs-lookup"><span data-stu-id="bda27-203">The following statement uses the SimpleMatch option to direct the -split operator to interpret the dot (.) delimiter literally.</span></span>

<span data-ttu-id="bda27-204">Le 0 représente la valeur « Return All » du paramètre Max-substrings.</span><span class="sxs-lookup"><span data-stu-id="bda27-204">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="bda27-205">Vous pouvez utiliser des options, telles que SimpleMatch, uniquement lorsque la valeur Max-substrings est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bda27-205">You can use options, such as SimpleMatch, only when the Max-substrings value is specified.</span></span>

```powershell
"This.is.a.test" -split ".", 0, "simplematch"
```

```Output
This
is
a
test
```

<span data-ttu-id="bda27-206">L’instruction suivante fractionne la chaîne à l’un des deux délimiteurs, en fonction de la valeur d’une variable.</span><span class="sxs-lookup"><span data-stu-id="bda27-206">The following statement splits the string at one of two delimiters, depending on the value of a variable.</span></span>

```powershell
$i = 1
$c = "LastName, FirstName; Address, City, State, Zip"
$c -split $(if ($i -lt 1) {","} else {";"})
```

```Output
LastName, FirstName
 Address, City, State, Zip
```

## <a name="see-also"></a><span data-ttu-id="bda27-207">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="bda27-207">SEE ALSO</span></span>

[<span data-ttu-id="bda27-208">Split-Path</span><span class="sxs-lookup"><span data-stu-id="bda27-208">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)

[<span data-ttu-id="bda27-209">about_Operators</span><span class="sxs-lookup"><span data-stu-id="bda27-209">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="bda27-210">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="bda27-210">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="bda27-211">about_Join</span><span class="sxs-lookup"><span data-stu-id="bda27-211">about_Join</span></span>](about_Join.md)

