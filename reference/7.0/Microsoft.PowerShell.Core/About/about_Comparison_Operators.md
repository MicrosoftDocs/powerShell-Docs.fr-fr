---
description: Décrit les opérateurs qui comparent des valeurs dans PowerShell.
Locale: en-US
ms.date: 12/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: dbda5371224345a2e22dd281c17ae0d7c928aad6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090224"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="1694d-103">À propos des opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="1694d-103">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="1694d-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="1694d-104">Short description</span></span>
<span data-ttu-id="1694d-105">Décrit les opérateurs qui comparent des valeurs dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1694d-105">Describes the operators that compare values in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="1694d-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="1694d-106">Long description</span></span>

<span data-ttu-id="1694d-107">Les opérateurs de comparaison vous permettent de spécifier des conditions pour comparer des valeurs et Rechercher des valeurs qui correspondent aux modèles spécifiés.</span><span class="sxs-lookup"><span data-stu-id="1694d-107">Comparison operators let you specify conditions for comparing values and finding values that match specified patterns.</span></span> <span data-ttu-id="1694d-108">Pour utiliser un opérateur de comparaison, spécifiez les valeurs que vous souhaitez comparer avec un opérateur qui sépare ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="1694d-108">To use a comparison operator, specify the values that you want to compare together with an operator that separates these values.</span></span>

<span data-ttu-id="1694d-109">PowerShell comprend les opérateurs de comparaison suivants :</span><span class="sxs-lookup"><span data-stu-id="1694d-109">PowerShell includes the following comparison operators:</span></span>

| <span data-ttu-id="1694d-110">Type</span><span class="sxs-lookup"><span data-stu-id="1694d-110">Type</span></span>        | <span data-ttu-id="1694d-111">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="1694d-111">Operators</span></span>    | <span data-ttu-id="1694d-112">Description</span><span class="sxs-lookup"><span data-stu-id="1694d-112">Description</span></span>                                 |
| ----------- | ------------ | --------------------------------------------|
| <span data-ttu-id="1694d-113">Égalité</span><span class="sxs-lookup"><span data-stu-id="1694d-113">Equality</span></span>    | <span data-ttu-id="1694d-114">-eq</span><span class="sxs-lookup"><span data-stu-id="1694d-114">-eq</span></span>          | <span data-ttu-id="1694d-115">equals</span><span class="sxs-lookup"><span data-stu-id="1694d-115">equals</span></span>                                      |
|             | <span data-ttu-id="1694d-116">-ne</span><span class="sxs-lookup"><span data-stu-id="1694d-116">-ne</span></span>          | <span data-ttu-id="1694d-117">n’est pas égal à</span><span class="sxs-lookup"><span data-stu-id="1694d-117">not equals</span></span>                                  |
|             | <span data-ttu-id="1694d-118">-gt</span><span class="sxs-lookup"><span data-stu-id="1694d-118">-gt</span></span>          | <span data-ttu-id="1694d-119">supérieur à</span><span class="sxs-lookup"><span data-stu-id="1694d-119">greater than</span></span>                                |
|             | <span data-ttu-id="1694d-120">-ge</span><span class="sxs-lookup"><span data-stu-id="1694d-120">-ge</span></span>          | <span data-ttu-id="1694d-121">supérieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="1694d-121">greater than or equal</span></span>                       |
|             | <span data-ttu-id="1694d-122">-lt</span><span class="sxs-lookup"><span data-stu-id="1694d-122">-lt</span></span>          | <span data-ttu-id="1694d-123">inférieur à</span><span class="sxs-lookup"><span data-stu-id="1694d-123">less than</span></span>                                   |
|             | <span data-ttu-id="1694d-124">-le</span><span class="sxs-lookup"><span data-stu-id="1694d-124">-le</span></span>          | <span data-ttu-id="1694d-125">inférieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="1694d-125">less than or equal</span></span>                          |
|             |              |                                             |
| <span data-ttu-id="1694d-126">Matching</span><span class="sxs-lookup"><span data-stu-id="1694d-126">Matching</span></span>    | <span data-ttu-id="1694d-127">-like</span><span class="sxs-lookup"><span data-stu-id="1694d-127">-like</span></span>        | <span data-ttu-id="1694d-128">Retourne la valeur true lorsque la chaîne correspond au caractère générique</span><span class="sxs-lookup"><span data-stu-id="1694d-128">Returns true when string matches wildcard</span></span>   |
|             |              | <span data-ttu-id="1694d-129">modèle</span><span class="sxs-lookup"><span data-stu-id="1694d-129">pattern</span></span>                                     |
|             | <span data-ttu-id="1694d-130">-notlike</span><span class="sxs-lookup"><span data-stu-id="1694d-130">-notlike</span></span>     | <span data-ttu-id="1694d-131">Retourne la valeur true lorsque la chaîne ne correspond pas</span><span class="sxs-lookup"><span data-stu-id="1694d-131">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="1694d-132">modèle de caractère générique</span><span class="sxs-lookup"><span data-stu-id="1694d-132">wildcard pattern</span></span>                            |
|             | <span data-ttu-id="1694d-133">-match</span><span class="sxs-lookup"><span data-stu-id="1694d-133">-match</span></span>       | <span data-ttu-id="1694d-134">Retourne la valeur true lorsque la chaîne correspond à Regex</span><span class="sxs-lookup"><span data-stu-id="1694d-134">Returns true when string matches regex</span></span>      |
|             |              | <span data-ttu-id="1694d-135">répétition $matches contient des chaînes correspondantes</span><span class="sxs-lookup"><span data-stu-id="1694d-135">pattern; $matches contains matching strings</span></span> |
|             | <span data-ttu-id="1694d-136">-notmatch</span><span class="sxs-lookup"><span data-stu-id="1694d-136">-notmatch</span></span>    | <span data-ttu-id="1694d-137">Retourne la valeur true lorsque la chaîne ne correspond pas</span><span class="sxs-lookup"><span data-stu-id="1694d-137">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="1694d-138">modèle Regex ; $matches contient une correspondance</span><span class="sxs-lookup"><span data-stu-id="1694d-138">regex pattern; $matches contains matching</span></span>   |
|             |              | <span data-ttu-id="1694d-139">chaînes</span><span class="sxs-lookup"><span data-stu-id="1694d-139">strings</span></span>                                     |
|             |              |                                             |
| <span data-ttu-id="1694d-140">Containment</span><span class="sxs-lookup"><span data-stu-id="1694d-140">Containment</span></span> | <span data-ttu-id="1694d-141">-contains</span><span class="sxs-lookup"><span data-stu-id="1694d-141">-contains</span></span>    | <span data-ttu-id="1694d-142">Retourne la valeur true lorsque la valeur de référence contenue</span><span class="sxs-lookup"><span data-stu-id="1694d-142">Returns true when reference value contained</span></span> |
|             |              | <span data-ttu-id="1694d-143">dans une collection</span><span class="sxs-lookup"><span data-stu-id="1694d-143">in a collection</span></span>                             |
|             | <span data-ttu-id="1694d-144">-notcontains</span><span class="sxs-lookup"><span data-stu-id="1694d-144">-notcontains</span></span> | <span data-ttu-id="1694d-145">Retourne la valeur true lorsque la valeur de référence n’est pas</span><span class="sxs-lookup"><span data-stu-id="1694d-145">Returns true when reference value not</span></span>       |
|             |              | <span data-ttu-id="1694d-146">contenu dans une collection</span><span class="sxs-lookup"><span data-stu-id="1694d-146">contained in a collection</span></span>                   |
|             | <span data-ttu-id="1694d-147">-in</span><span class="sxs-lookup"><span data-stu-id="1694d-147">-in</span></span>          | <span data-ttu-id="1694d-148">Retourne la valeur true lorsque la valeur de test contenue dans un</span><span class="sxs-lookup"><span data-stu-id="1694d-148">Returns true when test value contained in a</span></span> |
|             |              | <span data-ttu-id="1694d-149">collection</span><span class="sxs-lookup"><span data-stu-id="1694d-149">collection</span></span>                                  |
|             | <span data-ttu-id="1694d-150">-NOTIN</span><span class="sxs-lookup"><span data-stu-id="1694d-150">-notin</span></span>       | <span data-ttu-id="1694d-151">Retourne la valeur true lorsque la valeur de test n’est pas contenue</span><span class="sxs-lookup"><span data-stu-id="1694d-151">Returns true when test value not contained</span></span>  |
|             |              | <span data-ttu-id="1694d-152">dans une collection</span><span class="sxs-lookup"><span data-stu-id="1694d-152">in a collection</span></span>                             |
|             |              |                                             |
| <span data-ttu-id="1694d-153">Remplacement</span><span class="sxs-lookup"><span data-stu-id="1694d-153">Replacement</span></span> | <span data-ttu-id="1694d-154">-remplacer</span><span class="sxs-lookup"><span data-stu-id="1694d-154">-replace</span></span>     | <span data-ttu-id="1694d-155">Remplace un modèle de chaîne</span><span class="sxs-lookup"><span data-stu-id="1694d-155">Replaces a string pattern</span></span>                   |
|             |              |                                             |
| <span data-ttu-id="1694d-156">Type</span><span class="sxs-lookup"><span data-stu-id="1694d-156">Type</span></span>        | <span data-ttu-id="1694d-157">-est</span><span class="sxs-lookup"><span data-stu-id="1694d-157">-is</span></span>          | <span data-ttu-id="1694d-158">Retourne la valeur true si les deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="1694d-158">Returns true if both object are the same</span></span>    |
|             |              | <span data-ttu-id="1694d-159">type</span><span class="sxs-lookup"><span data-stu-id="1694d-159">type</span></span>                                        |
|             | <span data-ttu-id="1694d-160">-IsNot</span><span class="sxs-lookup"><span data-stu-id="1694d-160">-isnot</span></span>       | <span data-ttu-id="1694d-161">Retourne la valeur true si les objets ne sont pas identiques</span><span class="sxs-lookup"><span data-stu-id="1694d-161">Returns true if the objects are not the same</span></span>|
|             |              | <span data-ttu-id="1694d-162">type</span><span class="sxs-lookup"><span data-stu-id="1694d-162">type</span></span>                                        |

<span data-ttu-id="1694d-163">Par défaut, tous les opérateurs de comparaison ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="1694d-163">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="1694d-164">Pour faire en sorte qu’un opérateur de comparaison respecte la casse, faites précéder le nom de l’opérateur d’un `c` .</span><span class="sxs-lookup"><span data-stu-id="1694d-164">To make a comparison operator case-sensitive, precede the operator name with a `c`.</span></span> <span data-ttu-id="1694d-165">Par exemple, la version qui respecte la casse `-eq` est `-ceq` .</span><span class="sxs-lookup"><span data-stu-id="1694d-165">For example, the case-sensitive version of `-eq` is `-ceq`.</span></span> <span data-ttu-id="1694d-166">Pour rendre le non-respect de la casse explicite, faites précéder l’opérateur d’un `i` .</span><span class="sxs-lookup"><span data-stu-id="1694d-166">To make the case-insensitivity explicit, precede the operator with an `i`.</span></span> <span data-ttu-id="1694d-167">Par exemple, la version explicite de la casse de `-eq` est `-ieq` .</span><span class="sxs-lookup"><span data-stu-id="1694d-167">For example, the explicitly case-insensitive version of `-eq` is `-ieq`.</span></span>

<span data-ttu-id="1694d-168">Lorsque l’entrée d’un opérateur est une valeur scalaire, les opérateurs de comparaison retournent une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="1694d-168">When the input to an operator is a scalar value, comparison operators return a Boolean value.</span></span> <span data-ttu-id="1694d-169">Lorsque l’entrée est une collection de valeurs, les opérateurs de comparaison retournent toutes les valeurs correspondantes.</span><span class="sxs-lookup"><span data-stu-id="1694d-169">When the input is a collection of values, the comparison operators return any matching values.</span></span> <span data-ttu-id="1694d-170">S’il n’existe aucune correspondance dans une collection, les opérateurs de comparaison retournent un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="1694d-170">If there are no matches in a collection, comparison operators return an empty array.</span></span>

```powershell
PS> (1, 2 -eq 3).GetType().FullName
System.Object[]
```

<span data-ttu-id="1694d-171">Les exceptions sont les opérateurs de relation contenant-contenu, les opérateurs in et les opérateurs de type, qui retournent toujours une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="1694d-171">The exceptions are the containment operators, the In operators, and the type operators, which always return a **Boolean** value.</span></span>

> [!NOTE]
> <span data-ttu-id="1694d-172">Si vous devez comparer une valeur à `$null` , vous devez `$null` la placer sur le côté gauche de la comparaison.</span><span class="sxs-lookup"><span data-stu-id="1694d-172">If you need to compare a value to `$null` you should put `$null` on the left-hand side of the comparison.</span></span> <span data-ttu-id="1694d-173">Lorsque vous comparez `$null` à un **objet []** , le résultat est **false** , car l’objet de comparaison est un tableau.</span><span class="sxs-lookup"><span data-stu-id="1694d-173">When you compare `$null` to an **Object[]** the result is **False** because the comparison object is an array.</span></span> <span data-ttu-id="1694d-174">Lorsque vous comparez un tableau à `$null` , la comparaison filtre toutes les `$null` valeurs stockées dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="1694d-174">When you compare an array to `$null`, the comparison filters out any `$null` values stored in the array.</span></span> <span data-ttu-id="1694d-175">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1694d-175">For example:</span></span>
>
> ```powershell
> PS> $null -ne $null, "hello"
> True
> PS> $null, "hello" -ne $null
> hello
> ```

## <a name="equality-operators"></a><span data-ttu-id="1694d-176">Opérateurs d'égalité</span><span class="sxs-lookup"><span data-stu-id="1694d-176">Equality operators</span></span>

<span data-ttu-id="1694d-177">Les opérateurs d’égalité ( `-eq` , `-ne` ) retournent une valeur true ou les correspondances lorsqu’une ou plusieurs des valeurs d’entrée sont identiques au modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="1694d-177">The equality operators (`-eq`, `-ne`) return a value of TRUE or the matches when one or more of the input values is identical to the specified pattern.</span></span> <span data-ttu-id="1694d-178">La totalité du modèle doit correspondre à une valeur entière.</span><span class="sxs-lookup"><span data-stu-id="1694d-178">The entire pattern must match an entire value.</span></span>

<span data-ttu-id="1694d-179">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1694d-179">Example:</span></span>

### <a name="-eq"></a><span data-ttu-id="1694d-180">-eq</span><span class="sxs-lookup"><span data-stu-id="1694d-180">-eq</span></span>

<span data-ttu-id="1694d-181">Description : égal à.</span><span class="sxs-lookup"><span data-stu-id="1694d-181">Description: Equal to.</span></span> <span data-ttu-id="1694d-182">Contient une valeur identique.</span><span class="sxs-lookup"><span data-stu-id="1694d-182">Includes an identical value.</span></span>

<span data-ttu-id="1694d-183">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1694d-183">Example:</span></span>

```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2
PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```

### <a name="-ne"></a><span data-ttu-id="1694d-184">-ne</span><span class="sxs-lookup"><span data-stu-id="1694d-184">-ne</span></span>

<span data-ttu-id="1694d-185">Description : différent de.</span><span class="sxs-lookup"><span data-stu-id="1694d-185">Description: Not equal to.</span></span> <span data-ttu-id="1694d-186">Contient une valeur différente.</span><span class="sxs-lookup"><span data-stu-id="1694d-186">Includes a different value.</span></span>

<span data-ttu-id="1694d-187">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1694d-187">Example:</span></span>

```powershell
PS> "abc" -ne "def"
True

PS> "abc" -ne "abc"
False

PS> "abc" -ne "abc", "def"
True

PS> "abc", "def" -ne "abc"
def
```

### <a name="-gt"></a><span data-ttu-id="1694d-188">-gt</span><span class="sxs-lookup"><span data-stu-id="1694d-188">-gt</span></span>

<span data-ttu-id="1694d-189">Description : supérieur à.</span><span class="sxs-lookup"><span data-stu-id="1694d-189">Description: Greater-than.</span></span>

<span data-ttu-id="1694d-190">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1694d-190">Example:</span></span>

```powershell
PS> 8 -gt 6
True

PS> 7, 8, 9 -gt 8
9
```

> [!NOTE]
> <span data-ttu-id="1694d-191">Cela ne doit pas être confondu avec `>` , l’opérateur « supérieur à » dans de nombreux autres langages de programmation.</span><span class="sxs-lookup"><span data-stu-id="1694d-191">This should not to be confused with `>`, the greater-than operator in many other programming languages.</span></span> <span data-ttu-id="1694d-192">Dans PowerShell, `>` est utilisé pour la redirection.</span><span class="sxs-lookup"><span data-stu-id="1694d-192">In PowerShell, `>` is used for redirection.</span></span> <span data-ttu-id="1694d-193">Pour plus d’informations, consultez [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).</span><span class="sxs-lookup"><span data-stu-id="1694d-193">For more information, see [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).</span></span>

### <a name="-ge"></a><span data-ttu-id="1694d-194">-ge</span><span class="sxs-lookup"><span data-stu-id="1694d-194">-ge</span></span>

<span data-ttu-id="1694d-195">Description : supérieur ou égal à.</span><span class="sxs-lookup"><span data-stu-id="1694d-195">Description: Greater-than or equal to.</span></span>

<span data-ttu-id="1694d-196">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1694d-196">Example:</span></span>

```powershell
PS> 8 -ge 8
True

PS> 7, 8, 9 -ge 8
8
9
```

### <a name="-lt"></a><span data-ttu-id="1694d-197">-lt</span><span class="sxs-lookup"><span data-stu-id="1694d-197">-lt</span></span>

<span data-ttu-id="1694d-198">Description : inférieur à.</span><span class="sxs-lookup"><span data-stu-id="1694d-198">Description: Less-than.</span></span>

<span data-ttu-id="1694d-199">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1694d-199">Example:</span></span>

```powershell

PS> 8 -lt 6
False

PS> 7, 8, 9 -lt 8
7
```

### <a name="-le"></a><span data-ttu-id="1694d-200">-le</span><span class="sxs-lookup"><span data-stu-id="1694d-200">-le</span></span>

<span data-ttu-id="1694d-201">Description : inférieur ou égal à.</span><span class="sxs-lookup"><span data-stu-id="1694d-201">Description: Less-than or equal to.</span></span>

<span data-ttu-id="1694d-202">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1694d-202">Example:</span></span>

```powershell
PS> 6 -le 8
True

PS> 7, 8, 9 -le 8
7
8
```

## <a name="matching-operators"></a><span data-ttu-id="1694d-203">Opérateurs correspondants</span><span class="sxs-lookup"><span data-stu-id="1694d-203">Matching operators</span></span>

<span data-ttu-id="1694d-204">Les opérateurs like ( `-like` et `-notlike` ) recherchent les éléments qui correspondent ou ne correspondent pas à un modèle spécifié à l’aide d’expressions génériques.</span><span class="sxs-lookup"><span data-stu-id="1694d-204">The like operators (`-like` and `-notlike`) find elements that match or do not match a specified pattern using wildcard expressions.</span></span>

<span data-ttu-id="1694d-205">La syntaxe est :</span><span class="sxs-lookup"><span data-stu-id="1694d-205">The syntax is:</span></span>

```powershell
<string[]> -like <wildcard-expression>
<string[]> -notlike <wildcard-expression>
```

<span data-ttu-id="1694d-206">Les opérateurs de correspondance ( `-match` et `-notmatch` ) recherchent les éléments qui correspondent ou ne correspondent pas à un modèle spécifié à l’aide d’expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="1694d-206">The match operators (`-match` and `-notmatch`) find elements that match or do not match a specified pattern using regular expressions.</span></span>

<span data-ttu-id="1694d-207">Les opérateurs de correspondance remplissent la `$Matches` variable automatique lorsque l’entrée (l’argument côté gauche) de l’opérateur est un objet scalaire unique.</span><span class="sxs-lookup"><span data-stu-id="1694d-207">The match operators populate the `$Matches` automatic variable when the input (the left-side argument) to the operator is a single scalar object.</span></span> <span data-ttu-id="1694d-208">Quand l’entrée est scalaire, les `-match` `-notmatch` opérateurs et retournent une valeur booléenne et définissent la valeur de la `$Matches` variable automatique sur les composants correspondants de l’argument.</span><span class="sxs-lookup"><span data-stu-id="1694d-208">When the input is scalar, the `-match` and `-notmatch` operators return a Boolean value and set the value of the `$Matches` automatic variable to the matched components of the argument.</span></span>

<span data-ttu-id="1694d-209">La syntaxe est :</span><span class="sxs-lookup"><span data-stu-id="1694d-209">The syntax is:</span></span>

```powershell
<string[]> -match <regular-expression>
<string[]> -notmatch <regular-expression>
```

### <a name="-like"></a><span data-ttu-id="1694d-210">-like</span><span class="sxs-lookup"><span data-stu-id="1694d-210">-like</span></span>

<span data-ttu-id="1694d-211">Description : correspondance à l’aide du caractère générique ( \* ).</span><span class="sxs-lookup"><span data-stu-id="1694d-211">Description: Match using the wildcard character (\*).</span></span>

<span data-ttu-id="1694d-212">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1694d-212">Example:</span></span>

```powershell
PS> "PowerShell" -like "*shell"
True

PS> "PowerShell", "Server" -like "*shell"
PowerShell
```

### <a name="-notlike"></a><span data-ttu-id="1694d-213">-notlike</span><span class="sxs-lookup"><span data-stu-id="1694d-213">-notlike</span></span>

<span data-ttu-id="1694d-214">Description : ne correspond pas à l’aide du caractère générique ( \* ).</span><span class="sxs-lookup"><span data-stu-id="1694d-214">Description: Does not match using the wildcard character (\*).</span></span>

<span data-ttu-id="1694d-215">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1694d-215">Example:</span></span>

```powershell
PS> "PowerShell" -notlike "*shell"
False

PS> "PowerShell", "Server" -notlike "*shell"
Server
```

### <a name="-match"></a><span data-ttu-id="1694d-216">-match</span><span class="sxs-lookup"><span data-stu-id="1694d-216">-match</span></span>

<span data-ttu-id="1694d-217">Description : correspond à une chaîne à l’aide d’expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="1694d-217">Description: Matches a string using regular expressions.</span></span> <span data-ttu-id="1694d-218">Quand l’entrée est scalaire, elle remplit la `$Matches` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="1694d-218">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="1694d-219">Si l’entrée est une collection, les `-match` `-notmatch` opérateurs et retournent les membres correspondants de cette collection, mais l’opérateur ne remplit pas la `$Matches` variable.</span><span class="sxs-lookup"><span data-stu-id="1694d-219">If the input is a collection, the `-match` and `-notmatch` operators return the matching members of that collection, but the operator does not populate the `$Matches` variable.</span></span>

<span data-ttu-id="1694d-220">Par exemple, la commande suivante envoie une collection de chaînes à l' `-match` opérateur.</span><span class="sxs-lookup"><span data-stu-id="1694d-220">For example, the following command submits a collection of strings to the `-match` operator.</span></span> <span data-ttu-id="1694d-221">L' `-match` opérateur retourne les éléments de la collection qui correspondent à.</span><span class="sxs-lookup"><span data-stu-id="1694d-221">The `-match` operator returns the items in the collection that match.</span></span> <span data-ttu-id="1694d-222">Elle ne remplit pas la `$Matches` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="1694d-222">It does not populate the `$Matches` automatic variable.</span></span>

```powershell
PS> "Sunday", "Monday", "Tuesday" -match "sun"
Sunday

PS> $Matches
PS>
```

<span data-ttu-id="1694d-223">En revanche, la commande suivante envoie une chaîne unique à l' `-match` opérateur.</span><span class="sxs-lookup"><span data-stu-id="1694d-223">In contrast, the following command submits a single string to the `-match` operator.</span></span> <span data-ttu-id="1694d-224">L' `-match` opérateur retourne une valeur booléenne et remplit la `$Matches` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="1694d-224">The `-match` operator returns a Boolean value and populates the `$Matches` automatic variable.</span></span> <span data-ttu-id="1694d-225">La `$Matches` variable automatique est une **Hashtable**.</span><span class="sxs-lookup"><span data-stu-id="1694d-225">The `$Matches` automatic variable is a **Hashtable**.</span></span> <span data-ttu-id="1694d-226">Si aucun regroupement ou capture n’est utilisé, une seule clé est remplie.</span><span class="sxs-lookup"><span data-stu-id="1694d-226">If no grouping or capturing is used, only one key is populated.</span></span>
<span data-ttu-id="1694d-227">La `0` clé représente tout le texte qui a été mis en correspondance.</span><span class="sxs-lookup"><span data-stu-id="1694d-227">The `0` key represents all text that was matched.</span></span> <span data-ttu-id="1694d-228">Pour plus d’informations sur le regroupement et la capture à l’aide d’expressions régulières, consultez [about_regular_expressions](about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1694d-228">For more information about grouping and capturing using regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

```powershell
PS> "Sunday" -match "sun"
True

PS> $Matches

Name                           Value
----                           -----
0                              Sun
```

<span data-ttu-id="1694d-229">Il est important de noter que la `$Matches` Hashtable ne contiendra que la première occurrence d’un modèle correspondant.</span><span class="sxs-lookup"><span data-stu-id="1694d-229">It is important to note that the `$Matches` hashtable will only contain the first occurrence of any matching pattern.</span></span>

```powershell
PS> "Banana" -match "na"
True

PS> $Matches

Name                           Value
----                           -----
0                              na
```

> [!IMPORTANT]
> <span data-ttu-id="1694d-230">La `0` clé est un **entier**.</span><span class="sxs-lookup"><span data-stu-id="1694d-230">The `0` key is an **Integer**.</span></span> <span data-ttu-id="1694d-231">Vous pouvez utiliser n’importe quelle méthode **Hashtable** pour accéder à la valeur stockée.</span><span class="sxs-lookup"><span data-stu-id="1694d-231">You can use any **Hashtable** method to access the value stored.</span></span>
>
> ```powershell
> PS> "Good Dog" -match "Dog"
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

<span data-ttu-id="1694d-232">L' `-notmatch` opérateur remplit la `$Matches` variable automatique lorsque l’entrée est scalaire et que le résultat est false, qu’il s’agit de la détection d’une correspondance.</span><span class="sxs-lookup"><span data-stu-id="1694d-232">The `-notmatch` operator populates the `$Matches` automatic variable when the input is scalar and the result is False, that it, when it detects a match.</span></span>

```powershell
PS> "Sunday" -notmatch "rain"
True

PS> $matches
PS>

PS> "Sunday" -notmatch "day"
False

PS> $matches

Name                           Value
----                           -----
0                              day
```

### <a name="-notmatch"></a><span data-ttu-id="1694d-233">-notmatch</span><span class="sxs-lookup"><span data-stu-id="1694d-233">-notmatch</span></span>

<span data-ttu-id="1694d-234">Description : ne correspond pas à une chaîne.</span><span class="sxs-lookup"><span data-stu-id="1694d-234">Description: Does not match a string.</span></span> <span data-ttu-id="1694d-235">Utilise des expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="1694d-235">Uses regular expressions.</span></span> <span data-ttu-id="1694d-236">Quand l’entrée est scalaire, elle remplit la `$Matches` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="1694d-236">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="1694d-237">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1694d-237">Example:</span></span>

```powershell
PS> "Sunday" -notmatch "sun"
False

PS> $matches
Name Value
---- -----
0    sun

PS> "Sunday", "Monday" -notmatch "sun"
Monday
```

## <a name="containment-operators"></a><span data-ttu-id="1694d-238">Opérateurs de relation contenant-contenu</span><span class="sxs-lookup"><span data-stu-id="1694d-238">Containment operators</span></span>

<span data-ttu-id="1694d-239">Les opérateurs de relation contenant-contenu ( `-contains` et `-notcontains` ) sont similaires aux opérateurs d’égalité.</span><span class="sxs-lookup"><span data-stu-id="1694d-239">The containment operators (`-contains` and `-notcontains`) are similar to the equality operators.</span></span> <span data-ttu-id="1694d-240">Toutefois, les opérateurs de relation contenant-contenu retournent toujours une valeur booléenne, même lorsque l’entrée est une collection.</span><span class="sxs-lookup"><span data-stu-id="1694d-240">However, the containment operators always return a Boolean value, even when the input is a collection.</span></span>

<span data-ttu-id="1694d-241">En outre, contrairement aux opérateurs d’égalité, les opérateurs de relation contenant-contenu retournent une valeur dès qu’ils détectent la première correspondance.</span><span class="sxs-lookup"><span data-stu-id="1694d-241">Also, unlike the equality operators, the containment operators return a value as soon as they detect the first match.</span></span> <span data-ttu-id="1694d-242">Les opérateurs d’égalité évaluent toutes les entrées, puis retournent toutes les correspondances dans la collection.</span><span class="sxs-lookup"><span data-stu-id="1694d-242">The equality operators evaluate all input and then return all the matches in the collection.</span></span>

### <a name="-contains"></a><span data-ttu-id="1694d-243">-contains</span><span class="sxs-lookup"><span data-stu-id="1694d-243">-contains</span></span>

<span data-ttu-id="1694d-244">Description : opérateur de relation contenant-contenu.</span><span class="sxs-lookup"><span data-stu-id="1694d-244">Description: Containment operator.</span></span> <span data-ttu-id="1694d-245">Indique si une collection de valeurs de référence comprend une seule valeur de test.</span><span class="sxs-lookup"><span data-stu-id="1694d-245">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="1694d-246">Retourne toujours une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="1694d-246">Always returns a Boolean value.</span></span> <span data-ttu-id="1694d-247">Retourne TRUE uniquement lorsque la valeur de test correspond exactement à au moins une des valeurs de référence.</span><span class="sxs-lookup"><span data-stu-id="1694d-247">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="1694d-248">Lorsque la valeur de test est une collection, l’opérateur Contains utilise l’égalité des références.</span><span class="sxs-lookup"><span data-stu-id="1694d-248">When the test value is a collection, the Contains operator uses reference equality.</span></span> <span data-ttu-id="1694d-249">Elle retourne TRUE uniquement lorsque l’une des valeurs de référence est la même instance de l’objet de valeur de test.</span><span class="sxs-lookup"><span data-stu-id="1694d-249">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="1694d-250">Dans une collection de très grande taille, l' `-contains` opérateur retourne les résultats plus rapidement que l’opérateur égal à.</span><span class="sxs-lookup"><span data-stu-id="1694d-250">In a very large collection, the `-contains` operator returns results quicker than the equal to operator.</span></span>

<span data-ttu-id="1694d-251">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="1694d-251">Syntax:</span></span>

`<Reference-values> -contains <Test-value>`

<span data-ttu-id="1694d-252">Exemples :</span><span class="sxs-lookup"><span data-stu-id="1694d-252">Examples:</span></span>

```powershell
PS> "abc", "def" -contains "def"
True

PS> "Windows", "PowerShell" -contains "Shell"
False  #Not an exact match

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $DomainServers -contains $thisComputer
True

PS> "abc", "def", "ghi" -contains "abc", "def"
False

PS> $a = "abc", "def"
PS> "abc", "def", "ghi" -contains $a
False
PS> $a, "ghi" -contains $a
True
```

### <a name="-notcontains"></a><span data-ttu-id="1694d-253">-notcontains</span><span class="sxs-lookup"><span data-stu-id="1694d-253">-notcontains</span></span>

<span data-ttu-id="1694d-254">Description : opérateur de relation contenant-contenu.</span><span class="sxs-lookup"><span data-stu-id="1694d-254">Description: Containment operator.</span></span> <span data-ttu-id="1694d-255">Indique si une collection de valeurs de référence comprend une seule valeur de test.</span><span class="sxs-lookup"><span data-stu-id="1694d-255">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="1694d-256">Retourne toujours une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="1694d-256">Always returns a Boolean value.</span></span> <span data-ttu-id="1694d-257">Retourne la valeur TRUE lorsque la valeur de test n’est pas une correspondance exacte pour au moins une des valeurs de référence.</span><span class="sxs-lookup"><span data-stu-id="1694d-257">Returns TRUE when the test value is not an exact matches for at least one of the reference values.</span></span>

<span data-ttu-id="1694d-258">Lorsque la valeur de test est une collection, l’opérateur NotContains utilise l’égalité de référence.</span><span class="sxs-lookup"><span data-stu-id="1694d-258">When the test value is a collection, the NotContains operator uses reference equality.</span></span>

<span data-ttu-id="1694d-259">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="1694d-259">Syntax:</span></span>

`<Reference-values> -notcontains <Test-value>`

<span data-ttu-id="1694d-260">Exemples :</span><span class="sxs-lookup"><span data-stu-id="1694d-260">Examples:</span></span>

```powershell
PS> "Windows", "PowerShell" -notcontains "Shell"
True  #Not an exact match

# Get cmdlet parameters, but exclude common parameters
function get-parms ($cmdlet)
{
    $Common = "Verbose", "Debug", "WarningAction", "WarningVariable",
      "ErrorAction", "ErrorVariable", "OutVariable", "OutBuffer"

    $allparms = (Get-Command $Cmdlet).parametersets |
      foreach {$_.Parameters} |
        foreach {$_.Name} | Sort-Object | Get-Unique

    $allparms | where {$Common -notcontains $_ }
}

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $myVerbs = Get-Command -Module MyModule | foreach {$_.verb}
PS> $myVerbs | where {$ApprovedVerbs -notcontains $_}
ForEach
Sort
Tee
Where
```

### <a name="-in"></a><span data-ttu-id="1694d-261">-in</span><span class="sxs-lookup"><span data-stu-id="1694d-261">-in</span></span>

<span data-ttu-id="1694d-262">Description : dans l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="1694d-262">Description: In operator.</span></span> <span data-ttu-id="1694d-263">Indique si une valeur de test apparaît dans une collection de valeurs de référence.</span><span class="sxs-lookup"><span data-stu-id="1694d-263">Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="1694d-264">Retourne toujours comme valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="1694d-264">Always return as Boolean value.</span></span> <span data-ttu-id="1694d-265">Retourne TRUE uniquement lorsque la valeur de test correspond exactement à au moins une des valeurs de référence.</span><span class="sxs-lookup"><span data-stu-id="1694d-265">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="1694d-266">Lorsque la valeur de test est une collection, l’opérateur in utilise l’égalité de référence.</span><span class="sxs-lookup"><span data-stu-id="1694d-266">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="1694d-267">Elle retourne TRUE uniquement lorsque l’une des valeurs de référence est la même instance de l’objet de valeur de test.</span><span class="sxs-lookup"><span data-stu-id="1694d-267">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="1694d-268">L' `-in` opérateur a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1694d-268">The `-in` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="1694d-269">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="1694d-269">Syntax:</span></span>

`<Test-value> -in <Reference-values>`

<span data-ttu-id="1694d-270">Exemples :</span><span class="sxs-lookup"><span data-stu-id="1694d-270">Examples:</span></span>

```powershell
PS> "def" -in "abc", "def"
True

PS> "Shell" -in "Windows", "PowerShell"
False  #Not an exact match

PS> "Windows" -in "Windows", "PowerShell"
True  #An exact match

PS> "Windows", "PowerShell" -in "Windows", "PowerShell", "ServerManager"
False  #Using reference equality

PS> $a = "Windows", "PowerShell"
PS> $a -in $a, "ServerManager"
True  #Using reference equality

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $thisComputer -in  $domainServers
True
```

### <a name="-notin"></a><span data-ttu-id="1694d-271">-NOTIN</span><span class="sxs-lookup"><span data-stu-id="1694d-271">-notin</span></span>

<span data-ttu-id="1694d-272">Description : indique si une valeur de test apparaît dans une collection de valeurs de référence.</span><span class="sxs-lookup"><span data-stu-id="1694d-272">Description: Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="1694d-273">Retourne toujours une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="1694d-273">Always returns a Boolean value.</span></span> <span data-ttu-id="1694d-274">Retourne la valeur TRUE lorsque la valeur de test n’est pas une correspondance exacte pour au moins une des valeurs de référence.</span><span class="sxs-lookup"><span data-stu-id="1694d-274">Returns TRUE when the test value is not an exact match for at least one of the reference values.</span></span>

<span data-ttu-id="1694d-275">Lorsque la valeur de test est une collection, l’opérateur in utilise l’égalité de référence.</span><span class="sxs-lookup"><span data-stu-id="1694d-275">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="1694d-276">Elle retourne TRUE uniquement lorsque l’une des valeurs de référence est la même instance de l’objet de valeur de test.</span><span class="sxs-lookup"><span data-stu-id="1694d-276">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="1694d-277">L' `-notin` opérateur a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1694d-277">The `-notin` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="1694d-278">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="1694d-278">Syntax:</span></span>

`<Test-value> -notin <Reference-values>`

<span data-ttu-id="1694d-279">Exemples :</span><span class="sxs-lookup"><span data-stu-id="1694d-279">Examples:</span></span>

```powershell
PS> "def" -notin "abc", "def"
False

PS> "ghi" -notin "abc", "def"
True

PS> "Shell" -notin "Windows", "PowerShell"
True  #Not an exact match

PS> "Windows" -notin "Windows", "PowerShell"
False  #An exact match

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $MyVerbs = Get-Command -Module MyModule | foreach {$_.verb}

PS> $MyVerbs | where {$_ -notin $ApprovedVerbs}
ForEach
Sort
Tee
Where
```

## <a name="replacement-operator"></a><span data-ttu-id="1694d-280">Opérateur de remplacement</span><span class="sxs-lookup"><span data-stu-id="1694d-280">Replacement Operator</span></span>

<span data-ttu-id="1694d-281">L' `-replace` opérateur a la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="1694d-281">The `-replace` operator has the following syntax:</span></span>

`<input> -replace <original>, <substitute>`

<span data-ttu-id="1694d-282">L' `<original>` espace réservé est une expression régulière qui correspond aux caractères à remplacer.</span><span class="sxs-lookup"><span data-stu-id="1694d-282">The `<original>` placeholder is a regular expression matching the characters to be replaced.</span></span> <span data-ttu-id="1694d-283">L' `<substitute>` espace réservé est une chaîne littérale qui les remplace.</span><span class="sxs-lookup"><span data-stu-id="1694d-283">The `<substitute>` placeholder is a literal string that replaces them.</span></span>

<span data-ttu-id="1694d-284">L’opérateur remplace tout ou partie d’une valeur par la valeur spécifiée à l’aide d’expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="1694d-284">The operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="1694d-285">Vous pouvez utiliser l’opérateur pour de nombreuses tâches administratives, telles que le changement de nom des fichiers.</span><span class="sxs-lookup"><span data-stu-id="1694d-285">You can use the operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="1694d-286">Par exemple, la commande suivante modifie les extensions de nom de fichier de tous les `.txt` fichiers en `.log` :</span><span class="sxs-lookup"><span data-stu-id="1694d-286">For example, the following command changes the file name extensions of all `.txt` files to `.log`:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

### <a name="case-sensitive-matches"></a><span data-ttu-id="1694d-287">Correspondances respectant la casse</span><span class="sxs-lookup"><span data-stu-id="1694d-287">Case-sensitive matches</span></span>

<span data-ttu-id="1694d-288">Par défaut, l' `-replace` opérateur ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="1694d-288">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="1694d-289">Pour respecter la casse, utilisez `-creplace` .</span><span class="sxs-lookup"><span data-stu-id="1694d-289">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="1694d-290">Pour le rendre explicitement non sensible à la casse, utilisez `-ireplace` .</span><span class="sxs-lookup"><span data-stu-id="1694d-290">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="1694d-291">Prenons les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="1694d-291">Consider the following examples:</span></span>

```powershell
PS> "book" -replace "B", "C"
Cook
```

```powershell
PS> "book" -ireplace "B", "C"
Cook
```

```powershell
PS> "book" -creplace "B", "C"
book
```

### <a name="substitutions-in-regular-expressions"></a><span data-ttu-id="1694d-292">Substitutions dans les expressions régulières</span><span class="sxs-lookup"><span data-stu-id="1694d-292">Substitutions in regular expressions</span></span>

<span data-ttu-id="1694d-293">Il est également possible d’utiliser des expressions régulières pour remplacer dynamiquement du texte à l’aide de groupes de capture et de substitutions.</span><span class="sxs-lookup"><span data-stu-id="1694d-293">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="1694d-294">Les groupes de capture peuvent être référencés dans la `<substitute>` chaîne à l’aide du caractère dollar ( `$` ) avant l’identificateur de groupe.</span><span class="sxs-lookup"><span data-stu-id="1694d-294">Capture groups can be referenced in the `<substitute>` string using the dollar sign (`$`) character before the group identifier.</span></span>

<span data-ttu-id="1694d-295">Les groupes de capture peuvent être référencés par **numéro** ou par **nom**</span><span class="sxs-lookup"><span data-stu-id="1694d-295">Capture groups can be referenced by **Number** or **Name**</span></span>

- <span data-ttu-id="1694d-296">Par **nombre** : les groupes de capture sont numérotés de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="1694d-296">By **Number** - Capturing Groups are numbered from left to right.</span></span>

  ```powershell
  PS> "John D. Smith" -replace "(\w+) (\w+)\. (\w+)", '$1.$2.$3@contoso.com'
  John.D.Smith@contoso.com
  ```

- <span data-ttu-id="1694d-297">Par **nom** , les groupes de capture peuvent également être référencés par nom.</span><span class="sxs-lookup"><span data-stu-id="1694d-297">By **Name** - Capturing Groups can also be referenced by name.</span></span>

  ```powershell
  PS> "CONTOSO\Administrator" -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  FABRIKAM\Administrator
  ```

> [!WARNING]
> <span data-ttu-id="1694d-298">Étant donné que le `$` caractère est utilisé dans l’extension de chaîne, vous devez utiliser des chaînes littérales ou placer le caractère dans une séquence d’échappement `$` .</span><span class="sxs-lookup"><span data-stu-id="1694d-298">Since the `$` character is used in string expansion, you will must use literal strings or escape the `$` character.</span></span>
>
> ```powershell
> PS> 'Hello World' -replace '(\w+) \w+', "`$1 Universe"
> Hello Universe
> ```
>
> <span data-ttu-id="1694d-299">En outre, étant donné que le `$` caractère est utilisé dans la substitution, vous devez placer dans une séquence d’échappement toutes les instances de votre chaîne.</span><span class="sxs-lookup"><span data-stu-id="1694d-299">Additionally, since the `$` character is used in substitution, you must escape any instances in your string.</span></span>
>
> ```powershell
> PS> '5.72' -replace '(.+)', '$$$1'
> $5.72
> ```

<span data-ttu-id="1694d-300">Pour plus d’informations, consultez [about_regular_expressions](about_Regular_Expressions.md) et [substitutions dans les expressions régulières](/dotnet/standard/base-types/substitutions-in-regular-expressions)</span><span class="sxs-lookup"><span data-stu-id="1694d-300">To learn more see [about_Regular_Expressions](about_Regular_Expressions.md) and [Substitutions in Regular Expressions](/dotnet/standard/base-types/substitutions-in-regular-expressions)</span></span>

### <a name="substituting-in-a-collection"></a><span data-ttu-id="1694d-301">Substitution d’une collection</span><span class="sxs-lookup"><span data-stu-id="1694d-301">Substituting in a collection</span></span>

<span data-ttu-id="1694d-302">Quand le `<input>` à l' `-replace` opérateur est une collection, PowerShell applique le remplacement à chaque valeur de la collection.</span><span class="sxs-lookup"><span data-stu-id="1694d-302">When the `<input>` to the `-replace` operator is a collection, PowerShell applies the replacement to every value in the collection.</span></span> <span data-ttu-id="1694d-303">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1694d-303">For example:</span></span>

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

### <a name="scriptblock-substitutions"></a><span data-ttu-id="1694d-304">Substitutions ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="1694d-304">ScriptBlock substitutions</span></span>

<span data-ttu-id="1694d-305">À compter de PowerShell 6, vous pouvez utiliser un argument **scriptblock** pour le texte de _substitution_ .</span><span class="sxs-lookup"><span data-stu-id="1694d-305">Beginning in PowerShell 6, you can use a **ScriptBlock** argument for the _Substitution_ text.</span></span> <span data-ttu-id="1694d-306">Le **scriptblock** s’exécute pour chaque correspondance trouvée dans la chaîne _d’entrée_ .</span><span class="sxs-lookup"><span data-stu-id="1694d-306">The **ScriptBlock** will execute for each match found in the _input_ string.</span></span>

<span data-ttu-id="1694d-307">Dans le **scriptblock**, utilisez la `$_` variable automatique pour faire référence à l’objet **System. Text. RegularExpressions. match** actuel.</span><span class="sxs-lookup"><span data-stu-id="1694d-307">Within the **ScriptBlock**, use the `$_` automatic variable to refer to the current **System.Text.RegularExpressions.Match** object.</span></span> <span data-ttu-id="1694d-308">L’objet **match** vous donne accès au texte d’entrée actuel qui est remplacé, ainsi qu’à d’autres informations utiles.</span><span class="sxs-lookup"><span data-stu-id="1694d-308">The **Match** object gives you access to the current input text being replaced, as well as other useful information.</span></span>

<span data-ttu-id="1694d-309">Cet exemple remplace chaque séquence de trois décimales par l’équivalent du caractère.</span><span class="sxs-lookup"><span data-stu-id="1694d-309">This example replaces each sequence of three decimals with the character equivalent.</span></span> <span data-ttu-id="1694d-310">Le **scriptblock** est exécuté pour chaque ensemble de trois décimales qui doit être remplacé.</span><span class="sxs-lookup"><span data-stu-id="1694d-310">The **ScriptBlock** is run for each set of three decimals that needs to be replaced.</span></span>

```powershell
PS> "072101108108111" -replace "\d{3}", {[char][int]$_.Value}
Hello
```

## <a name="type-comparison"></a><span data-ttu-id="1694d-311">Comparaison de types</span><span class="sxs-lookup"><span data-stu-id="1694d-311">Type comparison</span></span>

<span data-ttu-id="1694d-312">Les opérateurs de comparaison de type ( `-is` et `-isnot` ) sont utilisés pour déterminer si un objet est un type spécifique.</span><span class="sxs-lookup"><span data-stu-id="1694d-312">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

### <a name="-is"></a><span data-ttu-id="1694d-313">-est</span><span class="sxs-lookup"><span data-stu-id="1694d-313">-is</span></span>

<span data-ttu-id="1694d-314">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="1694d-314">Syntax:</span></span>

`<object> -is <type reference>`

<span data-ttu-id="1694d-315">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1694d-315">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -is [int]
True
PS> $a -is $b.GetType()
False
```

### <a name="-isnot"></a><span data-ttu-id="1694d-316">-IsNot</span><span class="sxs-lookup"><span data-stu-id="1694d-316">-isnot</span></span>

<span data-ttu-id="1694d-317">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="1694d-317">Syntax:</span></span>

`<object> -isnot <type reference>`

<span data-ttu-id="1694d-318">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1694d-318">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -isnot $b.GetType()
True
PS> $b -isnot [int]
True
```

## <a name="see-also"></a><span data-ttu-id="1694d-319">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1694d-319">See also</span></span>

- [<span data-ttu-id="1694d-320">about_Operators</span><span class="sxs-lookup"><span data-stu-id="1694d-320">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="1694d-321">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="1694d-321">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="1694d-322">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="1694d-322">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="1694d-323">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="1694d-323">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="1694d-324">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="1694d-324">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="1694d-325">Where-Object</span><span class="sxs-lookup"><span data-stu-id="1694d-325">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
