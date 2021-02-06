---
description: Décrit les expressions régulières dans PowerShell.
Locale: en-US
ms.date: 03/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_regular_expressions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Regular_Expressions
ms.openlocfilehash: 4dc6ac670a31cbea4c35ee6540ce3368ad9b02ca
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599133"
---
# <a name="about-regular-expressions"></a><span data-ttu-id="5b4fb-103">À propos des expressions régulières</span><span class="sxs-lookup"><span data-stu-id="5b4fb-103">About Regular Expressions</span></span>

## <a name="short-description"></a><span data-ttu-id="5b4fb-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="5b4fb-104">Short description</span></span>
<span data-ttu-id="5b4fb-105">Décrit les expressions régulières dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-105">Describes regular expressions in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="5b4fb-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="5b4fb-106">Long description</span></span>

> [!NOTE]
> <span data-ttu-id="5b4fb-107">Cet article vous montrera la syntaxe et les méthodes d’utilisation des expressions régulières dans PowerShell, mais pas toutes les syntaxes.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-107">This article will show you the syntax and methods for using regular expressions in PowerShell, not all syntax is discussed.</span></span> <span data-ttu-id="5b4fb-108">Pour obtenir une référence plus complète, consultez le [langage des expressions régulières-aide-mémoire](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span><span class="sxs-lookup"><span data-stu-id="5b4fb-108">For a more complete reference, see the [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span></span>

<span data-ttu-id="5b4fb-109">Une expression régulière est un modèle utilisé pour faire correspondre du texte.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-109">A regular expression is a pattern used to match text.</span></span> <span data-ttu-id="5b4fb-110">Il peut être constitué de caractères littéraux, d’opérateurs et d’autres constructions.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-110">It can be made up of literal characters, operators, and other constructs.</span></span>

<span data-ttu-id="5b4fb-111">Cet article décrit la syntaxe des expressions régulières dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-111">This article demonstrates regular expression syntax in PowerShell.</span></span> <span data-ttu-id="5b4fb-112">PowerShell possède plusieurs opérateurs et applets de commande qui utilisent des expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-112">PowerShell has several operators and cmdlets that use regular expressions.</span></span> <span data-ttu-id="5b4fb-113">Pour plus d’informations sur la syntaxe et l’utilisation, consultez les liens ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-113">You can read more about their syntax and usage at the links below.</span></span>

- [<span data-ttu-id="5b4fb-114">Select-String</span><span class="sxs-lookup"><span data-stu-id="5b4fb-114">Select-String</span></span>](xref:Microsoft.PowerShell.Utility.Select-String)
- [<span data-ttu-id="5b4fb-115">-match et-Replace, opérateurs</span><span class="sxs-lookup"><span data-stu-id="5b4fb-115">-match and -replace operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="5b4fb-116">-Split</span><span class="sxs-lookup"><span data-stu-id="5b4fb-116">-split</span></span>](about_Split.md)
- [<span data-ttu-id="5b4fb-117">Switch, instruction avec l’option-Regex</span><span class="sxs-lookup"><span data-stu-id="5b4fb-117">switch statement with -regex option</span></span>](about_Switch.md)

<span data-ttu-id="5b4fb-118">Par défaut, les expressions régulières PowerShell ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-118">PowerShell regular expressions are case-insensitive by default.</span></span> <span data-ttu-id="5b4fb-119">Chaque méthode présentée ci-dessus a une façon différente de forcer le respect de la casse.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-119">Each method shown above has a different way to force case sensitivity.</span></span>

|       <span data-ttu-id="5b4fb-120">Méthode</span><span class="sxs-lookup"><span data-stu-id="5b4fb-120">Method</span></span>       |                      <span data-ttu-id="5b4fb-121">Respect de la casse</span><span class="sxs-lookup"><span data-stu-id="5b4fb-121">Case Sensitivity</span></span>                      |
| ------------------ | ---------------------------------------------------------- |
| `Select-String`    | <span data-ttu-id="5b4fb-122">utiliser le `-CaseSensitive` commutateur</span><span class="sxs-lookup"><span data-stu-id="5b4fb-122">use `-CaseSensitive` switch</span></span>                                |
| <span data-ttu-id="5b4fb-123">Instruction `switch`</span><span class="sxs-lookup"><span data-stu-id="5b4fb-123">`switch` statement</span></span> | <span data-ttu-id="5b4fb-124">Utilisez l' `-casesensitive` option</span><span class="sxs-lookup"><span data-stu-id="5b4fb-124">use the `-casesensitive` option</span></span>                            |
| <span data-ttu-id="5b4fb-125">opérateurs</span><span class="sxs-lookup"><span data-stu-id="5b4fb-125">operators</span></span>          | <span data-ttu-id="5b4fb-126">préfixe avec **'c'** ( `-cmatch` , `-csplit` ou `-creplace` )</span><span class="sxs-lookup"><span data-stu-id="5b4fb-126">prefix with **'c'** (`-cmatch`, `-csplit`, or `-creplace`)</span></span> |

### <a name="character-literals"></a><span data-ttu-id="5b4fb-127">Littéraux de caractère</span><span class="sxs-lookup"><span data-stu-id="5b4fb-127">Character literals</span></span>

<span data-ttu-id="5b4fb-128">Une expression régulière peut être un caractère littéral ou une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-128">A regular expression can be a literal character or a string.</span></span> <span data-ttu-id="5b4fb-129">L’expression fait en sorte que le moteur corresponde exactement au texte spécifié.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-129">The expression causes the engine to match the text specified exactly.</span></span>

```powershell
# This statement returns true because book contains the string "oo"
'book' -match 'oo'
```

### <a name="character-classes"></a><span data-ttu-id="5b4fb-130">Classes de caractères</span><span class="sxs-lookup"><span data-stu-id="5b4fb-130">Character classes</span></span>

<span data-ttu-id="5b4fb-131">Tandis que les littéraux de caractère fonctionnent si vous connaissez le modèle exact, les classes de caractères vous permettent d’être moins spécifiques.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-131">While character literals work if you know the exact pattern, character classes allow you to be less specific.</span></span>

#### <a name="character-groups"></a><span data-ttu-id="5b4fb-132">Groupes de caractères</span><span class="sxs-lookup"><span data-stu-id="5b4fb-132">Character groups</span></span>

<span data-ttu-id="5b4fb-133">`[character group]` vous permet de faire correspondre un nombre quelconque de caractères une seule fois, tandis que `[^character group]` ne fait correspondre que les caractères qui ne sont pas dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-133">`[character group]` allows you to match any number of characters one time, while `[^character group]` only matches characters NOT in the group.</span></span>

```powershell
# This expression returns true if the pattern matches big, bog, or bug.
'big' -match 'b[iou]g'
```

<span data-ttu-id="5b4fb-134">Si votre liste de caractères à faire correspondre comprend le trait d’Union ( `-` ), il doit se trouver au début ou à la fin de la liste pour le distinguer d’une expression de plage de caractères.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-134">If your list of characters to match includes the hyphen character (`-`), it must be at the beginning or end of the list to distinguish it from a character range expression.</span></span>

#### <a name="character-ranges"></a><span data-ttu-id="5b4fb-135">Plages de caractères</span><span class="sxs-lookup"><span data-stu-id="5b4fb-135">Character ranges</span></span>

<span data-ttu-id="5b4fb-136">Un modèle peut également être une plage de caractères.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-136">A pattern can also be a range of characters.</span></span> <span data-ttu-id="5b4fb-137">Les caractères peuvent être alphabétiques `[A-Z]` , numériques `[0-9]` ou même en ASCII `[ -~]` (tous les caractères imprimables).</span><span class="sxs-lookup"><span data-stu-id="5b4fb-137">The characters can be alphabetic `[A-Z]`, numeric `[0-9]`, or even ASCII-based `[ -~]` (all printable characters).</span></span>

```powershell
# This expression returns true if the pattern matches any 2 digit number.
42 -match '[0-9][0-9]'
```

#### <a name="numbers"></a><span data-ttu-id="5b4fb-138">Nombres</span><span class="sxs-lookup"><span data-stu-id="5b4fb-138">Numbers</span></span>

<span data-ttu-id="5b4fb-139">La `\d` classe de caractères correspond à n’importe quel chiffre décimal.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-139">The `\d` character class will match any decimal digit.</span></span> <span data-ttu-id="5b4fb-140">Inversement, `\D` correspond à n’importe quel chiffre non décimal.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-140">Conversely, `\D` will match any non-decimal digit.</span></span>

```powershell
# This expression returns true if it matches a server name.
# (Server-01 - Server-99).
'Server-01' -match 'Server-\d\d'
```

#### <a name="word-characters"></a><span data-ttu-id="5b4fb-141">Caractères alphabétiques</span><span class="sxs-lookup"><span data-stu-id="5b4fb-141">Word characters</span></span>

<span data-ttu-id="5b4fb-142">La `\w` classe de caractères correspond à n’importe quel caractère de mot `[a-zA-Z_0-9]` .</span><span class="sxs-lookup"><span data-stu-id="5b4fb-142">The `\w` character class will match any word character `[a-zA-Z_0-9]`.</span></span> <span data-ttu-id="5b4fb-143">Pour qu’il corresponde à n’importe quel caractère autre qu’un mot, utilisez `\W` .</span><span class="sxs-lookup"><span data-stu-id="5b4fb-143">To match any non-word character, use `\W`.</span></span>

```powershell
# This expression returns true.
# The pattern matches the first word character 'B'.
'Book' -match '\w'
```

#### <a name="wildcards"></a><span data-ttu-id="5b4fb-144">Caractères génériques</span><span class="sxs-lookup"><span data-stu-id="5b4fb-144">Wildcards</span></span>

<span data-ttu-id="5b4fb-145">Le point ( `.` ) est un caractère générique dans les expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-145">The period (`.`) is a wildcard character in regular expressions.</span></span> <span data-ttu-id="5b4fb-146">Elle correspond à n’importe quel caractère, à l’exception d’un saut de ligne ( `\n` ).</span><span class="sxs-lookup"><span data-stu-id="5b4fb-146">It will match any character except a newline (`\n`).</span></span>

```powershell
# This expression returns true.
# The pattern matches any 4 characters except the newline.
'a1\ ' -match '....'
```

#### <a name="whitespace"></a><span data-ttu-id="5b4fb-147">Espaces</span><span class="sxs-lookup"><span data-stu-id="5b4fb-147">Whitespace</span></span>

<span data-ttu-id="5b4fb-148">L’espace blanc est mis en correspondance à l’aide de la `\s` classe de caractères.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-148">Whitespace is matched using the `\s` character class.</span></span> <span data-ttu-id="5b4fb-149">Tout caractère autre qu’un espace est mis en correspondance à l’aide de `\S` .</span><span class="sxs-lookup"><span data-stu-id="5b4fb-149">Any non-whitespace character is matched using `\S`.</span></span> <span data-ttu-id="5b4fb-150">Les espaces littéraux `' '` peuvent également être utilisés.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-150">Literal space characters `' '` can also be used.</span></span>

```powershell
# This expression returns true.
# The pattern uses both methods to match the space.
' - ' -match '\s- '
```

### <a name="quantifiers"></a><span data-ttu-id="5b4fb-151">Quantificateurs</span><span class="sxs-lookup"><span data-stu-id="5b4fb-151">Quantifiers</span></span>

<span data-ttu-id="5b4fb-152">Les quantificateurs contrôlent le nombre d’instances de chaque élément qui doivent être présentes dans la chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-152">Quantifiers control how many instances of each element should be present in the input string.</span></span>

<span data-ttu-id="5b4fb-153">Voici quelques-uns des quantificateurs disponibles dans PowerShell :</span><span class="sxs-lookup"><span data-stu-id="5b4fb-153">The following are a few of the quantifiers available in PowerShell:</span></span>

| <span data-ttu-id="5b4fb-154">Quantificateur</span><span class="sxs-lookup"><span data-stu-id="5b4fb-154">Quantifier</span></span> |                <span data-ttu-id="5b4fb-155">Description</span><span class="sxs-lookup"><span data-stu-id="5b4fb-155">Description</span></span>                |
| ---------- | ----------------------------------------- |
| `*`        | <span data-ttu-id="5b4fb-156">Zéro, une ou plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-156">Zero or more times.</span></span>                       |
| `+`        | <span data-ttu-id="5b4fb-157">Une ou plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-157">One or more times.</span></span>                        |
| `?`        | <span data-ttu-id="5b4fb-158">Zéro ou une fois.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-158">Zero or one time.</span></span>                         |
| `{n,m}`    | <span data-ttu-id="5b4fb-159">Au moins `n` , mais pas plus de `m` fois.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-159">At least `n`, but no more than `m` times.</span></span> |

<span data-ttu-id="5b4fb-160">L’astérisque ( `*` ) correspond zéro fois ou plus à l’élément précédent.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-160">The asterisk (`*`) matches the previous element zero or more times.</span></span> <span data-ttu-id="5b4fb-161">Le résultat est que même une chaîne d’entrée sans l’élément serait une correspondance.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-161">The result is that even an input string without the element would be a match.</span></span>

```powershell
# This returns true for all account name strings even if the name is absent.
'ACCOUNT NAME:    Administrator' -match 'ACCOUNT NAME:\s*\w*'
```

<span data-ttu-id="5b4fb-162">Le signe plus ( `+` ) correspond une ou plusieurs fois à l’élément précédent.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-162">The plus sign (`+`) matches the previous element one or more times.</span></span>

```powershell
# This returns true if it matches any server name.
'DC-01' -match '[A-Z]+-\d\d'
```

<span data-ttu-id="5b4fb-163">Le point d’interrogation `?` correspond zéro ou une fois à l’élément précédent.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-163">The question mark `?` matches the previous element zero or one time.</span></span> <span data-ttu-id="5b4fb-164">Comme pour `*` les astérisques, elle correspond même aux chaînes où l’élément est absent.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-164">Like asterisk `*`, it will even match strings where the element is absent.</span></span>

```powershell
# This returns true for any server name, even server names without dashes.
'SERVER01' -match '[A-Z]+-?\d\d'
```

<span data-ttu-id="5b4fb-165">Le `{n, m}` quantificateur peut être utilisé de plusieurs façons différentes pour permettre un contrôle granulaire sur le quantificateur.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-165">The `{n, m}` quantifier can be used several different ways to allow granular control over the quantifier.</span></span> <span data-ttu-id="5b4fb-166">Le deuxième élément `m` et la virgule `,` sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-166">The second element `m` and the comma `,` are optional.</span></span>

| <span data-ttu-id="5b4fb-167">Quantificateur</span><span class="sxs-lookup"><span data-stu-id="5b4fb-167">Quantifier</span></span> |                <span data-ttu-id="5b4fb-168">Description</span><span class="sxs-lookup"><span data-stu-id="5b4fb-168">Description</span></span>                 |
| ---------- | ------------------------------------------ |
| `{n}`      | <span data-ttu-id="5b4fb-169">Correspond exactement au `n` nombre de fois.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-169">Match EXACTLY `n` number of times.</span></span>         |
| `{n,}`     | <span data-ttu-id="5b4fb-170">Faire correspondre au moins le `n` nombre de fois.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-170">Match at LEAST `n` number of times.</span></span>        |
| `{n,m}`    | <span data-ttu-id="5b4fb-171">Mise en correspondance entre `n` et `m` nombre de fois.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-171">Match between `n` and `m` number of times.</span></span> |

```powershell
# This returns true if it matches any phone number.
'111-222-3333' -match '\d{3}-\d{3}-\d{4}'
```

### <a name="anchors"></a><span data-ttu-id="5b4fb-172">Ancres</span><span class="sxs-lookup"><span data-stu-id="5b4fb-172">Anchors</span></span>

<span data-ttu-id="5b4fb-173">Les ancres vous permettent de faire en sorte qu’une correspondance réussisse ou échoue en fonction de la position des correspondances dans la chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-173">Anchors allow you to cause a match to succeed or fail based on the matches position within the input string.</span></span>

<span data-ttu-id="5b4fb-174">Les deux ancres couramment utilisées sont `^` et `$` .</span><span class="sxs-lookup"><span data-stu-id="5b4fb-174">The two commonly used anchors are `^` and `$`.</span></span> <span data-ttu-id="5b4fb-175">Le signe insertion `^` correspond au début d’une chaîne, et `$` , qui correspond à la fin d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-175">The caret `^` matches the start of a string, and `$`, which matches the end of a string.</span></span> <span data-ttu-id="5b4fb-176">Les ancres vous permettent de faire correspondre votre texte à une position spécifique tout en ignorant les caractères indésirables.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-176">The anchors allow you to match your text at a specific position while also discarding unwanted characters.</span></span>

```powershell
# The pattern expects the string 'fish' to be the only thing on the line.
# This returns FALSE.
'fishing' -match '^fish$'
```

> [!NOTE]
> <span data-ttu-id="5b4fb-177">Lors de la définition d’une expression régulière contenant une `$` ancre, veillez à placer l’expression régulière à l’aide de guillemets simples ( `'` ) au lieu de guillemets doubles ( `"` ), sinon PowerShell développera l’expression en tant que variable.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-177">When defining a regex containing an `$` anchor, be sure to enclose the regex using single quotes (`'`) instead of double quotes (`"`) or PowerShell will expand the expression as a variable.</span></span>

<span data-ttu-id="5b4fb-178">Lorsque vous utilisez des ancres dans PowerShell, vous devez comprendre la différence entre **Singleline** et les options d’expression régulière **multilignes** .</span><span class="sxs-lookup"><span data-stu-id="5b4fb-178">When using anchors in PowerShell, you should understand the difference between **Singleline** and **Multiline** regular expression options.</span></span>

- <span data-ttu-id="5b4fb-179">**Multiligne**: le mode multiligne force `^` et `$` correspond à la fin de chaque ligne au lieu du début et de la fin de la chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-179">**Multiline**: Multiline mode forces `^` and `$` to match the beginning end of every LINE instead of the beginning and end of the input string.</span></span>
- <span data-ttu-id="5b4fb-180">**Singleline**: le mode Singleline traite la chaîne d’entrée comme un **Singleline**.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-180">**Singleline**: Singleline mode treats the input string as a **SingleLine**.</span></span>
  <span data-ttu-id="5b4fb-181">Elle force le `.` caractère à correspondre à chaque caractère (y compris les nouvelles lignes), au lieu de faire correspondre tous les caractères à l’exception du saut de ligne `\n` .</span><span class="sxs-lookup"><span data-stu-id="5b4fb-181">It forces the `.` character to match every character (including newlines), instead of matching every character EXCEPT the newline `\n`.</span></span>

<span data-ttu-id="5b4fb-182">Pour en savoir plus sur ces options et leur utilisation, consultez le [langage des expressions régulières-aide-mémoire](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span><span class="sxs-lookup"><span data-stu-id="5b4fb-182">To read more about these options and how to use them, visit the [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span></span>

### <a name="escaping-characters"></a><span data-ttu-id="5b4fb-183">Caractères d’échappement</span><span class="sxs-lookup"><span data-stu-id="5b4fb-183">Escaping characters</span></span>

<span data-ttu-id="5b4fb-184">La barre oblique inverse ( `\` ) est utilisée pour échapper les caractères afin qu’ils ne soient pas analysés par le moteur des expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-184">The backslash (`\`) is used to escape characters so they aren't parsed by the regular expression engine.</span></span>

<span data-ttu-id="5b4fb-185">Les caractères suivants sont réservés : `[]().\^$|?*+{}` .</span><span class="sxs-lookup"><span data-stu-id="5b4fb-185">The following characters are reserved: `[]().\^$|?*+{}`.</span></span>

<span data-ttu-id="5b4fb-186">Vous devez placer ces caractères dans une séquence d’échappement dans vos séquences pour les faire correspondre dans vos chaînes d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-186">You'll need to escape these characters in your patterns to match them in your input strings.</span></span>

```powershell
# This returns true and matches numbers with at least 2 digits of precision.
# The decimal point is escaped using the backslash.
'3.141' -match '3\.\d{2,}'
```

<span data-ttu-id="5b4fb-187">Il existe une méthode statique de la classe Regex qui peut échapper du texte à votre place.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-187">There\`s a static method of the regex class that can escape text for you.</span></span>

```powershell
[regex]::escape('3.\d{2,}')
```

```Output
3\.\\d\{2,}
```

> [!NOTE]
> <span data-ttu-id="5b4fb-188">Cela permet d’échapper tous les caractères d’expression régulière réservés, y compris les barres obliques inverses existantes utilisées dans les classes de caractères.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-188">This escapes all reserved regular expression characters, including existing backslashes used in character classes.</span></span> <span data-ttu-id="5b4fb-189">Veillez à l’utiliser uniquement sur la partie de votre modèle que vous devez échapper.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-189">Be sure to only use it on the portion of your pattern that you need to escape.</span></span>

#### <a name="other-character-escapes"></a><span data-ttu-id="5b4fb-190">Autres caractères d’échappement</span><span class="sxs-lookup"><span data-stu-id="5b4fb-190">Other character escapes</span></span>

<span data-ttu-id="5b4fb-191">Il existe également des caractères d’échappement réservés que vous pouvez utiliser pour faire correspondre les types de caractères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-191">There are also reserved character escapes that you can use to match special character types.</span></span>

<span data-ttu-id="5b4fb-192">Voici quelques caractères d’échappement couramment utilisés :</span><span class="sxs-lookup"><span data-stu-id="5b4fb-192">The following are a few commonly used character escapes:</span></span>

|<span data-ttu-id="5b4fb-193">Caractère d’échappement</span><span class="sxs-lookup"><span data-stu-id="5b4fb-193">Character Escape</span></span>  |<span data-ttu-id="5b4fb-194">Description</span><span class="sxs-lookup"><span data-stu-id="5b4fb-194">Description</span></span>  |
|---------|---------|
|`\t`|<span data-ttu-id="5b4fb-195">Correspond à une tabulation</span><span class="sxs-lookup"><span data-stu-id="5b4fb-195">Matches a tab</span></span>|
|`\n`|<span data-ttu-id="5b4fb-196">Correspond à un saut de ligne</span><span class="sxs-lookup"><span data-stu-id="5b4fb-196">Matches a newline</span></span>|
|`\r`|<span data-ttu-id="5b4fb-197">Correspond à un retour chariot</span><span class="sxs-lookup"><span data-stu-id="5b4fb-197">Matches a carriage return</span></span>|

### <a name="groups-captures-and-substitutions"></a><span data-ttu-id="5b4fb-198">Groupes, captures et substitutions</span><span class="sxs-lookup"><span data-stu-id="5b4fb-198">Groups, Captures, and Substitutions</span></span>

<span data-ttu-id="5b4fb-199">Les constructions de regroupement séparent une chaîne d’entrée en sous-chaînes qui peuvent être capturées ou ignorées.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-199">Grouping constructs separate an input string into substrings that can be captured or ignored.</span></span> <span data-ttu-id="5b4fb-200">Les sous-chaînes groupées sont appelées sous-expressions.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-200">Grouped substrings are called subexpressions.</span></span> <span data-ttu-id="5b4fb-201">Par défaut, les sous-expressions sont capturées dans des groupes numérotés, mais vous pouvez également leur attribuer des noms.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-201">By default subexpressions are captured in numbered groups, though you can assign names to them as well.</span></span>

<span data-ttu-id="5b4fb-202">Une construction de regroupement est une expression régulière placée entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-202">A grouping construct is a regular expression surrounded by parentheses.</span></span> <span data-ttu-id="5b4fb-203">Tout texte correspondant à l’expression régulière comprise est capturé.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-203">Any text matched by the enclosed regular expression is captured.</span></span> <span data-ttu-id="5b4fb-204">L’exemple suivant permet de rompre le texte d’entrée en deux groupes de capture.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-204">The following example will break the input text into two capturing groups.</span></span>

```powershell
'The last logged on user was CONTOSO\jsmith' -match '(.+was )(.+)'
```

```Output
True
```

<span data-ttu-id="5b4fb-205">Utilisez la `$Matches` variable automatique **Hashtable** pour récupérer le texte capturé.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-205">Use the `$Matches` **Hashtable** automatic variable to retrieve captured text.</span></span>
<span data-ttu-id="5b4fb-206">Le texte représentant la correspondance entière est stocké à la clé `0` .</span><span class="sxs-lookup"><span data-stu-id="5b4fb-206">The text representing the entire match is stored at key `0`.</span></span>

```powershell
$Matches.0
```

```Output
The last logged on user was CONTOSO\jsmith
```

<span data-ttu-id="5b4fb-207">Les captures sont stockées dans des clés numériques **entières** qui augmentent de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-207">Captures are stored in numeric **Integer** keys that increase from left to right.</span></span> <span data-ttu-id="5b4fb-208">La capture `1` contient tout le texte jusqu’à ce que le nom d’utilisateur, capture `2` contienne simplement le nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-208">Capture `1` contains all the text until the username, capture `2` contains just the username.</span></span>

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
2                              CONTOSO\jsmith
1                              The last logged on user was
0                              The last logged on user was CONTOSO\jsmith
```

> [!IMPORTANT]
> <span data-ttu-id="5b4fb-209">La `0` clé est un **entier**.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-209">The `0` key is an **Integer**.</span></span> <span data-ttu-id="5b4fb-210">Vous pouvez utiliser n’importe quelle méthode **Hashtable** pour accéder à la valeur stockée.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-210">You can use any **Hashtable** method to access the value stored.</span></span>
>
> ```
> PS> 'Good Dog' -match 'Dog'
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

#### <a name="named-captures"></a><span data-ttu-id="5b4fb-211">Captures nommées</span><span class="sxs-lookup"><span data-stu-id="5b4fb-211">Named Captures</span></span>

<span data-ttu-id="5b4fb-212">Par défaut, les captures sont stockées dans l’ordre numérique croissant, de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-212">By default, captures are stored in ascending numeric order, from left to right.</span></span>
<span data-ttu-id="5b4fb-213">Vous pouvez également assigner un **nom** à un groupe de capture.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-213">You can also assign a **name** to a capturing group.</span></span> <span data-ttu-id="5b4fb-214">Ce **nom** devient une clé de la `$Matches` variable automatique **Hashtable** .</span><span class="sxs-lookup"><span data-stu-id="5b4fb-214">This **name** becomes a key on the `$Matches` **Hashtable** automatic variable.</span></span>

<span data-ttu-id="5b4fb-215">À l’intérieur d’un groupe de capture, utilisez `?<keyname>` pour stocker les données capturées sous une clé nommée.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-215">Inside a capturing group, use `?<keyname>` to store captured data under a named key.</span></span>

```
PS> $string = 'The last logged on user was CONTOSO\jsmith'
PS> $string -match 'was (?<domain>.+)\\(?<user>.+)'
True

PS> $Matches

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

PS> $Matches.domain
CONTOSO

PS> $Matches.user
jsmith
```

<span data-ttu-id="5b4fb-216">L’exemple suivant stocke l’entrée de journal la plus récente dans le journal de sécurité Windows.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-216">The following example stores the newest log entry in the Windows Security Log.</span></span>
<span data-ttu-id="5b4fb-217">L’expression régulière fournie extrait le nom d’utilisateur et le domaine du message et les stocke sous les clés :**N** pour le nom et **D** pour le domaine.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-217">The provided regular expression extracts the username and domain from the message and stores them under the keys:**N** for name and **D** for domain.</span></span>

```powershell
$log = (Get-WinEvent -LogName Security -MaxEvents 1).message
$r = '(?s).*Account Name:\s*(?<N>.*).*Account Domain:\s*(?<D>[A-Z,0-9]*)'
$log -match $r
```

```Output
True
```

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
D                              CONTOSO
N                              jsmith
0                              A process has exited....
```

<span data-ttu-id="5b4fb-218">Pour plus d’informations, consultez [constructions de regroupement dans les expressions régulières](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).</span><span class="sxs-lookup"><span data-stu-id="5b4fb-218">For more information, see [Grouping Constructs in Regular Expressions](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).</span></span>

#### <a name="substitutions-in-regular-expressions"></a><span data-ttu-id="5b4fb-219">Substitutions dans les expressions régulières</span><span class="sxs-lookup"><span data-stu-id="5b4fb-219">Substitutions in Regular Expressions</span></span>

<span data-ttu-id="5b4fb-220">L’utilisation des expressions régulières avec l' `-replace` opérateur vous permet de remplacer le texte de manière dynamique à l’aide du texte capturé.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-220">Using the regular expressions with the `-replace` operator allows you to dynamically replace text using captured text.</span></span>

`<input> -replace <original>, <substitute>`

- <span data-ttu-id="5b4fb-221">`<input>`: Chaîne à rechercher</span><span class="sxs-lookup"><span data-stu-id="5b4fb-221">`<input>`: The string to be searched</span></span>
- <span data-ttu-id="5b4fb-222">`<original>`: Expression régulière utilisée pour rechercher la chaîne d’entrée</span><span class="sxs-lookup"><span data-stu-id="5b4fb-222">`<original>`: A regular expression used to search the input string</span></span>
- <span data-ttu-id="5b4fb-223">`<substitute>`: Expression de substitution d’expression régulière pour remplacer les correspondances trouvées dans la chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-223">`<substitute>`: A regular expression substitution expression to replace matches found in the input string.</span></span>

> [!NOTE]
> <span data-ttu-id="5b4fb-224">Les `<original>` `<substitute>` opérandes et sont soumis aux règles du moteur des expressions régulières, telles que la séquence d’échappement des caractères.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-224">The `<original>` and `<substitute>` operands are subject to rules of the regular expression engine such as character escaping.</span></span>

<span data-ttu-id="5b4fb-225">Les groupes de capture peuvent être référencés dans la `<substitute>` chaîne.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-225">Capturing groups can be referenced in the `<substitute>` string.</span></span> <span data-ttu-id="5b4fb-226">La substitution est effectuée en utilisant le `$` caractère qui précède l’identificateur de groupe.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-226">The substitution is done by using the `$` character before the group identifier.</span></span>

<span data-ttu-id="5b4fb-227">Deux méthodes pour référencer des groupes de capture sont par **numéro** et par **nom**.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-227">Two ways to reference capturing groups are by **Number** and by **Name**.</span></span>

- <span data-ttu-id="5b4fb-228">Par **nombre** : les groupes de capture sont numérotés de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-228">By **Number** - Capturing Groups are numbered from left to right.</span></span>

  ```powershell
  'John D. Smith' -replace '(\w+) (\w+)\. (\w+)', '$1.$2.$3@contoso.com'
  ```

  ```Output
  John.D.Smith@contoso.com
  ```

- <span data-ttu-id="5b4fb-229">Par **nom** , les groupes de capture peuvent également être référencés par nom.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-229">By **Name** - Capturing Groups can also be referenced by name.</span></span>

  ```powershell
  'CONTOSO\Administrator' -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  ```

  ```Output
  FABRIKAM\Administrator
  ```

<span data-ttu-id="5b4fb-230">L' `$&` expression représente tout le texte mis en correspondance.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-230">The `$&` expression represents all the text matched.</span></span>

```powershell
'Gobble' -replace 'Gobble', '$& $&'
```

```Output
Gobble Gobble
```

> [!WARNING]
> <span data-ttu-id="5b4fb-231">Étant donné que le `$` caractère est utilisé dans l’extension de chaîne, vous devez utiliser des chaînes littérales avec substitution, ou placer le caractère dans une séquence d’échappement `$` quand vous utilisez des guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-231">Since the `$` character is used in string expansion, you'll need to use literal strings with substitution, or escape the `$` character when using double quotes.</span></span>
>
> ```powershell
> 'Hello World' -replace '(\w+) \w+', '$1 Universe'
> "Hello World" -replace "(\w+) \w+", "`$1 Universe"
> ```
>
> ```Output
> Hello Universe
> Hello Universe
> ```
>
> <span data-ttu-id="5b4fb-232">En outre, si vous souhaitez que le soit `$` un caractère littéral, utilisez à la `$$` place des caractères d’échappement normaux.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-232">Additionally, if you want to have the `$` as a literal character, use `$$` instead of the normal escape characters.</span></span> <span data-ttu-id="5b4fb-233">Quand vous utilisez des guillemets doubles, échapper toujours toutes les instances de `$` pour éviter une substitution incorrecte.</span><span class="sxs-lookup"><span data-stu-id="5b4fb-233">When using double quotes, still escape all instances of `$` to avoid incorrect substitution.</span></span>
>
> ```powershell
> '5.72' -replace '(.+)', '$$$1'
> "5.72" -replace "(.+)", "`$`$`$1"
> ```
>
> ```Output
> $5.72
> $5.72
> ```

<span data-ttu-id="5b4fb-234">Pour plus d’informations, consultez [substitutions dans les expressions régulières](/dotnet/standard/base-types/substitutions-in-regular-expressions).</span><span class="sxs-lookup"><span data-stu-id="5b4fb-234">For more information, see [Substitutions in Regular Expressions](/dotnet/standard/base-types/substitutions-in-regular-expressions).</span></span>

## <a name="see-also"></a><span data-ttu-id="5b4fb-235">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b4fb-235">See also</span></span>

[<span data-ttu-id="5b4fb-236">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="5b4fb-236">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="5b4fb-237">about_Operators</span><span class="sxs-lookup"><span data-stu-id="5b4fb-237">about_Operators</span></span>](about_Operators.md)

