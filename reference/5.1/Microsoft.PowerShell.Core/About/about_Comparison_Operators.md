---
description: Décrit les opérateurs qui comparent des valeurs dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: b6076e20ad3ecbe9f2def157bb20bdb3bee5b7ad
ms.sourcegitcommit: c9e56ec489522c706b8d6b8733f3f015d6d7e893
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208553"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="5ad3d-104">À propos des opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="5ad3d-104">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="5ad3d-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="5ad3d-105">Short description</span></span>
<span data-ttu-id="5ad3d-106">Décrit les opérateurs qui comparent des valeurs dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-106">Describes the operators that compare values in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="5ad3d-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="5ad3d-107">Long description</span></span>

<span data-ttu-id="5ad3d-108">Les opérateurs de comparaison vous permettent de spécifier des conditions pour comparer des valeurs et Rechercher des valeurs qui correspondent aux modèles spécifiés.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-108">Comparison operators let you specify conditions for comparing values and finding values that match specified patterns.</span></span> <span data-ttu-id="5ad3d-109">Pour utiliser un opérateur de comparaison, spécifiez les valeurs que vous souhaitez comparer avec un opérateur qui sépare ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-109">To use a comparison operator, specify the values that you want to compare together with an operator that separates these values.</span></span>

<span data-ttu-id="5ad3d-110">PowerShell comprend les opérateurs de comparaison suivants :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-110">PowerShell includes the following comparison operators:</span></span>

| <span data-ttu-id="5ad3d-111">Type</span><span class="sxs-lookup"><span data-stu-id="5ad3d-111">Type</span></span>        | <span data-ttu-id="5ad3d-112">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="5ad3d-112">Operators</span></span>    | <span data-ttu-id="5ad3d-113">Description</span><span class="sxs-lookup"><span data-stu-id="5ad3d-113">Description</span></span>                                 |
| ----------- | ------------ | --------------------------------------------|
| <span data-ttu-id="5ad3d-114">Égalité</span><span class="sxs-lookup"><span data-stu-id="5ad3d-114">Equality</span></span>    | <span data-ttu-id="5ad3d-115">-eq</span><span class="sxs-lookup"><span data-stu-id="5ad3d-115">-eq</span></span>          | <span data-ttu-id="5ad3d-116">est égal à</span><span class="sxs-lookup"><span data-stu-id="5ad3d-116">equals</span></span>                                      |
|             | <span data-ttu-id="5ad3d-117">-ne</span><span class="sxs-lookup"><span data-stu-id="5ad3d-117">-ne</span></span>          | <span data-ttu-id="5ad3d-118">n’est pas égal à</span><span class="sxs-lookup"><span data-stu-id="5ad3d-118">not equals</span></span>                                  |
|             | <span data-ttu-id="5ad3d-119">-gt</span><span class="sxs-lookup"><span data-stu-id="5ad3d-119">-gt</span></span>          | <span data-ttu-id="5ad3d-120">supérieur à</span><span class="sxs-lookup"><span data-stu-id="5ad3d-120">greater than</span></span>                                |
|             | <span data-ttu-id="5ad3d-121">-ge</span><span class="sxs-lookup"><span data-stu-id="5ad3d-121">-ge</span></span>          | <span data-ttu-id="5ad3d-122">supérieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="5ad3d-122">greater than or equal</span></span>                       |
|             | <span data-ttu-id="5ad3d-123">-lt</span><span class="sxs-lookup"><span data-stu-id="5ad3d-123">-lt</span></span>          | <span data-ttu-id="5ad3d-124">inférieur à</span><span class="sxs-lookup"><span data-stu-id="5ad3d-124">less than</span></span>                                   |
|             | <span data-ttu-id="5ad3d-125">-le</span><span class="sxs-lookup"><span data-stu-id="5ad3d-125">-le</span></span>          | <span data-ttu-id="5ad3d-126">inférieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="5ad3d-126">less than or equal</span></span>                          |
|             |              |                                             |
| <span data-ttu-id="5ad3d-127">Matching</span><span class="sxs-lookup"><span data-stu-id="5ad3d-127">Matching</span></span>    | <span data-ttu-id="5ad3d-128">-like</span><span class="sxs-lookup"><span data-stu-id="5ad3d-128">-like</span></span>        | <span data-ttu-id="5ad3d-129">Retourne la valeur true lorsque la chaîne correspond au caractère générique</span><span class="sxs-lookup"><span data-stu-id="5ad3d-129">Returns true when string matches wildcard</span></span>   |
|             |              | <span data-ttu-id="5ad3d-130">modèle</span><span class="sxs-lookup"><span data-stu-id="5ad3d-130">pattern</span></span>                                     |
|             | <span data-ttu-id="5ad3d-131">-notlike</span><span class="sxs-lookup"><span data-stu-id="5ad3d-131">-notlike</span></span>     | <span data-ttu-id="5ad3d-132">Retourne la valeur true lorsque la chaîne ne correspond pas</span><span class="sxs-lookup"><span data-stu-id="5ad3d-132">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="5ad3d-133">modèle de caractère générique</span><span class="sxs-lookup"><span data-stu-id="5ad3d-133">wildcard pattern</span></span>                            |
|             | <span data-ttu-id="5ad3d-134">-match</span><span class="sxs-lookup"><span data-stu-id="5ad3d-134">-match</span></span>       | <span data-ttu-id="5ad3d-135">Retourne la valeur true lorsque la chaîne correspond à Regex</span><span class="sxs-lookup"><span data-stu-id="5ad3d-135">Returns true when string matches regex</span></span>      |
|             |              | <span data-ttu-id="5ad3d-136">répétition $matches contient des chaînes correspondantes</span><span class="sxs-lookup"><span data-stu-id="5ad3d-136">pattern; $matches contains matching strings</span></span> |
|             | <span data-ttu-id="5ad3d-137">-notmatch</span><span class="sxs-lookup"><span data-stu-id="5ad3d-137">-notmatch</span></span>    | <span data-ttu-id="5ad3d-138">Retourne la valeur true lorsque la chaîne ne correspond pas</span><span class="sxs-lookup"><span data-stu-id="5ad3d-138">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="5ad3d-139">modèle Regex ; $matches contient une correspondance</span><span class="sxs-lookup"><span data-stu-id="5ad3d-139">regex pattern; $matches contains matching</span></span>   |
|             |              | <span data-ttu-id="5ad3d-140">chaînes</span><span class="sxs-lookup"><span data-stu-id="5ad3d-140">strings</span></span>                                     |
|             |              |                                             |
| <span data-ttu-id="5ad3d-141">Containment</span><span class="sxs-lookup"><span data-stu-id="5ad3d-141">Containment</span></span> | <span data-ttu-id="5ad3d-142">-contains</span><span class="sxs-lookup"><span data-stu-id="5ad3d-142">-contains</span></span>    | <span data-ttu-id="5ad3d-143">Retourne la valeur true lorsque la valeur de référence contenue</span><span class="sxs-lookup"><span data-stu-id="5ad3d-143">Returns true when reference value contained</span></span> |
|             |              | <span data-ttu-id="5ad3d-144">dans une collection</span><span class="sxs-lookup"><span data-stu-id="5ad3d-144">in a collection</span></span>                             |
|             | <span data-ttu-id="5ad3d-145">-notcontains</span><span class="sxs-lookup"><span data-stu-id="5ad3d-145">-notcontains</span></span> | <span data-ttu-id="5ad3d-146">Retourne la valeur true lorsque la valeur de référence n’est pas</span><span class="sxs-lookup"><span data-stu-id="5ad3d-146">Returns true when reference value not</span></span>       |
|             |              | <span data-ttu-id="5ad3d-147">contenu dans une collection</span><span class="sxs-lookup"><span data-stu-id="5ad3d-147">contained in a collection</span></span>                   |
|             | <span data-ttu-id="5ad3d-148">-in</span><span class="sxs-lookup"><span data-stu-id="5ad3d-148">-in</span></span>          | <span data-ttu-id="5ad3d-149">Retourne la valeur true lorsque la valeur de test contenue dans un</span><span class="sxs-lookup"><span data-stu-id="5ad3d-149">Returns true when test value contained in a</span></span> |
|             |              | <span data-ttu-id="5ad3d-150">collection</span><span class="sxs-lookup"><span data-stu-id="5ad3d-150">collection</span></span>                                  |
|             | <span data-ttu-id="5ad3d-151">-NOTIN</span><span class="sxs-lookup"><span data-stu-id="5ad3d-151">-notin</span></span>       | <span data-ttu-id="5ad3d-152">Retourne la valeur true lorsque la valeur de test n’est pas contenue</span><span class="sxs-lookup"><span data-stu-id="5ad3d-152">Returns true when test value not contained</span></span>  |
|             |              | <span data-ttu-id="5ad3d-153">dans une collection</span><span class="sxs-lookup"><span data-stu-id="5ad3d-153">in a collection</span></span>                             |
|             |              |                                             |
| <span data-ttu-id="5ad3d-154">Remplacement</span><span class="sxs-lookup"><span data-stu-id="5ad3d-154">Replacement</span></span> | <span data-ttu-id="5ad3d-155">-remplacer</span><span class="sxs-lookup"><span data-stu-id="5ad3d-155">-replace</span></span>     | <span data-ttu-id="5ad3d-156">Remplace un modèle de chaîne</span><span class="sxs-lookup"><span data-stu-id="5ad3d-156">Replaces a string pattern</span></span>                   |
|             |              |                                             |
| <span data-ttu-id="5ad3d-157">Type</span><span class="sxs-lookup"><span data-stu-id="5ad3d-157">Type</span></span>        | <span data-ttu-id="5ad3d-158">-est</span><span class="sxs-lookup"><span data-stu-id="5ad3d-158">-is</span></span>          | <span data-ttu-id="5ad3d-159">Retourne la valeur true si les deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="5ad3d-159">Returns true if both object are the same</span></span>    |
|             |              | <span data-ttu-id="5ad3d-160">type</span><span class="sxs-lookup"><span data-stu-id="5ad3d-160">type</span></span>                                        |
|             | <span data-ttu-id="5ad3d-161">-IsNot</span><span class="sxs-lookup"><span data-stu-id="5ad3d-161">-isnot</span></span>       | <span data-ttu-id="5ad3d-162">Retourne la valeur true si les objets ne sont pas identiques</span><span class="sxs-lookup"><span data-stu-id="5ad3d-162">Returns true if the objects are not the same</span></span>|
|             |              | <span data-ttu-id="5ad3d-163">type</span><span class="sxs-lookup"><span data-stu-id="5ad3d-163">type</span></span>                                        |

<span data-ttu-id="5ad3d-164">Par défaut, tous les opérateurs de comparaison ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-164">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="5ad3d-165">Pour faire en sorte qu’un opérateur de comparaison respecte la casse, faites précéder le nom de l’opérateur d’un `c` .</span><span class="sxs-lookup"><span data-stu-id="5ad3d-165">To make a comparison operator case-sensitive, precede the operator name with a `c`.</span></span> <span data-ttu-id="5ad3d-166">Par exemple, la version qui respecte la casse `-eq` est `-ceq` .</span><span class="sxs-lookup"><span data-stu-id="5ad3d-166">For example, the case-sensitive version of `-eq` is `-ceq`.</span></span> <span data-ttu-id="5ad3d-167">Pour rendre le non-respect de la casse explicite, faites précéder l’opérateur d’un `i` .</span><span class="sxs-lookup"><span data-stu-id="5ad3d-167">To make the case-insensitivity explicit, precede the operator with an `i`.</span></span> <span data-ttu-id="5ad3d-168">Par exemple, la version explicite de la casse de `-eq` est `-ieq` .</span><span class="sxs-lookup"><span data-stu-id="5ad3d-168">For example, the explicitly case-insensitive version of `-eq` is `-ieq`.</span></span>

<span data-ttu-id="5ad3d-169">Lorsque l’entrée d’un opérateur est une valeur scalaire, les opérateurs de comparaison retournent une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-169">When the input to an operator is a scalar value, comparison operators return a Boolean value.</span></span> <span data-ttu-id="5ad3d-170">Lorsque l’entrée est une collection de valeurs, les opérateurs de comparaison retournent toutes les valeurs correspondantes.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-170">When the input is a collection of values, the comparison operators return any matching values.</span></span> <span data-ttu-id="5ad3d-171">S’il n’existe aucune correspondance dans une collection, les opérateurs de comparaison retournent un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-171">If there are no matches in a collection, comparison operators return an empty array.</span></span>

```powershell
PS> (1, 2 -eq 3).GetType().FullName
System.Object[]
```

<span data-ttu-id="5ad3d-172">Les exceptions sont les opérateurs de relation contenant-contenu, les opérateurs in et les opérateurs de type, qui retournent toujours une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="5ad3d-172">The exceptions are the containment operators, the In operators, and the type operators, which always return a **Boolean** value.</span></span>

> [!NOTE]
> <span data-ttu-id="5ad3d-173">Si vous devez comparer une valeur à `$null` , vous devez `$null` la placer sur le côté gauche de la comparaison.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-173">If you need to compare a value to `$null` you should put `$null` on the left-hand side of the comparison.</span></span> <span data-ttu-id="5ad3d-174">Lorsque vous comparez `$null` à un **objet []** , le résultat est **false** , car l’objet de comparaison est un tableau.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-174">When you compare `$null` to an **Object[]** the result is **False** because the comparison object is an array.</span></span> <span data-ttu-id="5ad3d-175">Lorsque vous comparez un tableau à `$null` , la comparaison filtre toutes les `$null` valeurs stockées dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-175">When you compare an array to `$null`, the comparison filters out any `$null` values stored in the array.</span></span> <span data-ttu-id="5ad3d-176">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-176">For example:</span></span>
>
> ```powershell
> PS> $null -ne $null, "hello"
> True
> PS> $null, "hello" -ne $null
> hello
> ```

### <a name="equality-operators"></a><span data-ttu-id="5ad3d-177">Opérateurs d'égalité</span><span class="sxs-lookup"><span data-stu-id="5ad3d-177">Equality Operators</span></span>

<span data-ttu-id="5ad3d-178">Les opérateurs d’égalité ( `-eq` , `-ne` ) retournent une valeur true ou les correspondances lorsqu’une ou plusieurs des valeurs d’entrée sont identiques au modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-178">The equality operators (`-eq`, `-ne`) return a value of TRUE or the matches when one or more of the input values is identical to the specified pattern.</span></span> <span data-ttu-id="5ad3d-179">La totalité du modèle doit correspondre à une valeur entière.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-179">The entire pattern must match an entire value.</span></span>

<span data-ttu-id="5ad3d-180">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-180">Example:</span></span>

#### <a name="-eq"></a><span data-ttu-id="5ad3d-181">-eq</span><span class="sxs-lookup"><span data-stu-id="5ad3d-181">-eq</span></span>

<span data-ttu-id="5ad3d-182">Description : égal à.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-182">Description: Equal to.</span></span> <span data-ttu-id="5ad3d-183">Contient une valeur identique.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-183">Includes an identical value.</span></span>

<span data-ttu-id="5ad3d-184">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-184">Example:</span></span>

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

#### <a name="-ne"></a><span data-ttu-id="5ad3d-185">-ne</span><span class="sxs-lookup"><span data-stu-id="5ad3d-185">-ne</span></span>

<span data-ttu-id="5ad3d-186">Description : différent de.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-186">Description: Not equal to.</span></span> <span data-ttu-id="5ad3d-187">Contient une valeur différente.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-187">Includes a different value.</span></span>

<span data-ttu-id="5ad3d-188">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-188">Example:</span></span>

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

#### <a name="-gt"></a><span data-ttu-id="5ad3d-189">-gt</span><span class="sxs-lookup"><span data-stu-id="5ad3d-189">-gt</span></span>

<span data-ttu-id="5ad3d-190">Description : supérieur à.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-190">Description: Greater-than.</span></span>

<span data-ttu-id="5ad3d-191">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-191">Example:</span></span>

```powershell
PS> 8 -gt 6
True

PS> 7, 8, 9 -gt 8
9
```

> [!NOTE]
> <span data-ttu-id="5ad3d-192">Cela ne doit pas être confondu avec `>` , l’opérateur « supérieur à » dans de nombreux autres langages de programmation.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-192">This should not to be confused with `>`, the greater-than operator in many other programming languages.</span></span> <span data-ttu-id="5ad3d-193">Dans PowerShell, `>` est utilisé pour la redirection.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-193">In PowerShell, `>` is used for redirection.</span></span> <span data-ttu-id="5ad3d-194">Pour plus d’informations, consultez [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).</span><span class="sxs-lookup"><span data-stu-id="5ad3d-194">For more information, see [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).</span></span>

#### <a name="-ge"></a><span data-ttu-id="5ad3d-195">-ge</span><span class="sxs-lookup"><span data-stu-id="5ad3d-195">-ge</span></span>

<span data-ttu-id="5ad3d-196">Description : supérieur ou égal à.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-196">Description: Greater-than or equal to.</span></span>

<span data-ttu-id="5ad3d-197">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-197">Example:</span></span>

```powershell
PS> 8 -ge 8
True

PS> 7, 8, 9 -ge 8
8
9
```

#### <a name="-lt"></a><span data-ttu-id="5ad3d-198">-lt</span><span class="sxs-lookup"><span data-stu-id="5ad3d-198">-lt</span></span>

<span data-ttu-id="5ad3d-199">Description : inférieur à.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-199">Description: Less-than.</span></span>

<span data-ttu-id="5ad3d-200">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-200">Example:</span></span>

```powershell

PS> 8 -lt 6
False

PS> 7, 8, 9 -lt 8
7
```

#### <a name="-le"></a><span data-ttu-id="5ad3d-201">-le</span><span class="sxs-lookup"><span data-stu-id="5ad3d-201">-le</span></span>

<span data-ttu-id="5ad3d-202">Description : inférieur ou égal à.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-202">Description: Less-than or equal to.</span></span>

<span data-ttu-id="5ad3d-203">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-203">Example:</span></span>

```powershell
PS> 6 -le 8
True

PS> 7, 8, 9 -le 8
7
8
```

### <a name="matching-operators"></a><span data-ttu-id="5ad3d-204">Opérateurs correspondants</span><span class="sxs-lookup"><span data-stu-id="5ad3d-204">Matching Operators</span></span>

<span data-ttu-id="5ad3d-205">Les opérateurs like ( `-like` et `-notlike` ) recherchent les éléments qui correspondent ou ne correspondent pas à un modèle spécifié à l’aide d’expressions génériques.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-205">The like operators (`-like` and `-notlike`) find elements that match or do not match a specified pattern using wildcard expressions.</span></span>

<span data-ttu-id="5ad3d-206">La syntaxe est :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-206">The syntax is:</span></span>

```powershell
<string[]> -like <wildcard-expression>
<string[]> -notlike <wildcard-expression>
```

<span data-ttu-id="5ad3d-207">Les opérateurs de correspondance ( `-match` et `-notmatch` ) recherchent les éléments qui correspondent ou ne correspondent pas à un modèle spécifié à l’aide d’expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-207">The match operators (`-match` and `-notmatch`) find elements that match or do not match a specified pattern using regular expressions.</span></span>

<span data-ttu-id="5ad3d-208">Les opérateurs de correspondance remplissent la `$Matches` variable automatique lorsque l’entrée (l’argument côté gauche) de l’opérateur est un objet scalaire unique.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-208">The match operators populate the `$Matches` automatic variable when the input (the left-side argument) to the operator is a single scalar object.</span></span> <span data-ttu-id="5ad3d-209">Quand l’entrée est scalaire, les `-match` `-notmatch` opérateurs et retournent une valeur booléenne et définissent la valeur de la `$Matches` variable automatique sur les composants correspondants de l’argument.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-209">When the input is scalar, the `-match` and `-notmatch` operators return a Boolean value and set the value of the `$Matches` automatic variable to the matched components of the argument.</span></span>

<span data-ttu-id="5ad3d-210">La syntaxe est :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-210">The syntax is:</span></span>

```powershell
<string[]> -match <regular-expression>
<string[]> -notmatch <regular-expression>
```

#### <a name="-like"></a><span data-ttu-id="5ad3d-211">-like</span><span class="sxs-lookup"><span data-stu-id="5ad3d-211">-like</span></span>

<span data-ttu-id="5ad3d-212">Description : correspondance à l’aide du caractère générique ( \* ).</span><span class="sxs-lookup"><span data-stu-id="5ad3d-212">Description: Match using the wildcard character (\*).</span></span>

<span data-ttu-id="5ad3d-213">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-213">Example:</span></span>

```powershell
PS> "PowerShell" -like "*shell"
True

PS> "PowerShell", "Server" -like "*shell"
PowerShell
```

#### <a name="-notlike"></a><span data-ttu-id="5ad3d-214">-notlike</span><span class="sxs-lookup"><span data-stu-id="5ad3d-214">-notlike</span></span>

<span data-ttu-id="5ad3d-215">Description : ne correspond pas à l’aide du caractère générique ( \* ).</span><span class="sxs-lookup"><span data-stu-id="5ad3d-215">Description: Does not match using the wildcard character (\*).</span></span>

<span data-ttu-id="5ad3d-216">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-216">Example:</span></span>

```powershell
PS> "PowerShell" -notlike "*shell"
False

PS> "PowerShell", "Server" -notlike "*shell"
Server
```

### <a name="-match"></a><span data-ttu-id="5ad3d-217">-match</span><span class="sxs-lookup"><span data-stu-id="5ad3d-217">-match</span></span>

<span data-ttu-id="5ad3d-218">Description : correspond à une chaîne à l’aide d’expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-218">Description: Matches a string using regular expressions.</span></span> <span data-ttu-id="5ad3d-219">Quand l’entrée est scalaire, elle remplit la `$Matches` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-219">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="5ad3d-220">Si l’entrée est une collection, les `-match` `-notmatch` opérateurs et retournent les membres correspondants de cette collection, mais l’opérateur ne remplit pas la `$Matches` variable.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-220">If the input is a collection, the `-match` and `-notmatch` operators return the matching members of that collection, but the operator does not populate the `$Matches` variable.</span></span>

<span data-ttu-id="5ad3d-221">Par exemple, la commande suivante envoie une collection de chaînes à l' `-match` opérateur.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-221">For example, the following command submits a collection of strings to the `-match` operator.</span></span> <span data-ttu-id="5ad3d-222">L' `-match` opérateur retourne les éléments de la collection qui correspondent à.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-222">The `-match` operator returns the items in the collection that match.</span></span> <span data-ttu-id="5ad3d-223">Elle ne remplit pas la `$Matches` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-223">It does not populate the `$Matches` automatic variable.</span></span>

```powershell
PS> "Sunday", "Monday", "Tuesday" -match "sun"
Sunday

PS> $Matches
PS>
```

<span data-ttu-id="5ad3d-224">En revanche, la commande suivante envoie une chaîne unique à l' `-match` opérateur.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-224">In contrast, the following command submits a single string to the `-match` operator.</span></span> <span data-ttu-id="5ad3d-225">L' `-match` opérateur retourne une valeur booléenne et remplit la `$Matches` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-225">The `-match` operator returns a Boolean value and populates the `$Matches` automatic variable.</span></span> <span data-ttu-id="5ad3d-226">La `$Matches` variable automatique est une **Hashtable** .</span><span class="sxs-lookup"><span data-stu-id="5ad3d-226">The `$Matches` automatic variable is a **Hashtable** .</span></span> <span data-ttu-id="5ad3d-227">Si aucun regroupement ou capture n’est utilisé, une seule clé est remplie.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-227">If no grouping or capturing is used, only one key is populated.</span></span>
<span data-ttu-id="5ad3d-228">La `0` clé représente tout le texte qui a été mis en correspondance.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-228">The `0` key represents all text that was matched.</span></span> <span data-ttu-id="5ad3d-229">Pour plus d’informations sur le regroupement et la capture à l’aide d’expressions régulières, consultez [about_regular_expressions](about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5ad3d-229">For more information about grouping and capturing using regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

```powershell
PS> "Sunday" -match "sun"
True

PS> $Matches

Name                           Value
----                           -----
0                              Sun
```

<span data-ttu-id="5ad3d-230">Il est important de noter que la `$Matches` Hashtable ne contiendra que la première occurrence d’un modèle correspondant.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-230">It is important to note that the `$Matches` hashtable will only contain the first occurrence of any matching pattern.</span></span>

```powershell
PS> "Banana" -match "na"
True

PS> $Matches

Name                           Value
----                           -----
0                              na
```

> [!IMPORTANT]
> <span data-ttu-id="5ad3d-231">La `0` clé est un **entier** .</span><span class="sxs-lookup"><span data-stu-id="5ad3d-231">The `0` key is an **Integer** .</span></span> <span data-ttu-id="5ad3d-232">Vous pouvez utiliser n’importe quelle méthode **Hashtable** pour accéder à la valeur stockée.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-232">You can use any **Hashtable** method to access the value stored.</span></span>
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

<span data-ttu-id="5ad3d-233">L' `-notmatch` opérateur remplit la `$Matches` variable automatique lorsque l’entrée est scalaire et que le résultat est false, qu’il s’agit de la détection d’une correspondance.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-233">The `-notmatch` operator populates the `$Matches` automatic variable when the input is scalar and the result is False, that it, when it detects a match.</span></span>

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

#### <a name="-notmatch"></a><span data-ttu-id="5ad3d-234">-notmatch</span><span class="sxs-lookup"><span data-stu-id="5ad3d-234">-notmatch</span></span>

<span data-ttu-id="5ad3d-235">Description : ne correspond pas à une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-235">Description: Does not match a string.</span></span> <span data-ttu-id="5ad3d-236">Utilise des expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-236">Uses regular expressions.</span></span> <span data-ttu-id="5ad3d-237">Quand l’entrée est scalaire, elle remplit la `$Matches` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-237">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="5ad3d-238">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-238">Example:</span></span>

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

### <a name="containment-operators"></a><span data-ttu-id="5ad3d-239">Opérateurs de relation contenant-contenu</span><span class="sxs-lookup"><span data-stu-id="5ad3d-239">Containment Operators</span></span>

<span data-ttu-id="5ad3d-240">Les opérateurs de relation contenant-contenu ( `-contains` et `-notcontains` ) sont similaires aux opérateurs d’égalité.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-240">The containment operators (`-contains` and `-notcontains`) are similar to the equality operators.</span></span> <span data-ttu-id="5ad3d-241">Toutefois, les opérateurs de relation contenant-contenu retournent toujours une valeur booléenne, même lorsque l’entrée est une collection.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-241">However, the containment operators always return a Boolean value, even when the input is a collection.</span></span>

<span data-ttu-id="5ad3d-242">En outre, contrairement aux opérateurs d’égalité, les opérateurs de relation contenant-contenu retournent une valeur dès qu’ils détectent la première correspondance.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-242">Also, unlike the equality operators, the containment operators return a value as soon as they detect the first match.</span></span> <span data-ttu-id="5ad3d-243">Les opérateurs d’égalité évaluent toutes les entrées, puis retournent toutes les correspondances dans la collection.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-243">The equality operators evaluate all input and then return all the matches in the collection.</span></span>

#### <a name="-contains"></a><span data-ttu-id="5ad3d-244">-contains</span><span class="sxs-lookup"><span data-stu-id="5ad3d-244">-contains</span></span>

<span data-ttu-id="5ad3d-245">Description : opérateur de relation contenant-contenu.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-245">Description: Containment operator.</span></span> <span data-ttu-id="5ad3d-246">Indique si une collection de valeurs de référence comprend une seule valeur de test.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-246">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="5ad3d-247">Retourne toujours une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-247">Always returns a Boolean value.</span></span> <span data-ttu-id="5ad3d-248">Retourne TRUE uniquement lorsque la valeur de test correspond exactement à au moins une des valeurs de référence.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-248">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="5ad3d-249">Lorsque la valeur de test est une collection, l’opérateur Contains utilise l’égalité des références.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-249">When the test value is a collection, the Contains operator uses reference equality.</span></span> <span data-ttu-id="5ad3d-250">Elle retourne TRUE uniquement lorsque l’une des valeurs de référence est la même instance de l’objet de valeur de test.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-250">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="5ad3d-251">Dans une collection de très grande taille, l' `-contains` opérateur retourne les résultats plus rapidement que l’opérateur égal à.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-251">In a very large collection, the `-contains` operator returns results quicker than the equal to operator.</span></span>

<span data-ttu-id="5ad3d-252">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-252">Syntax:</span></span>

`<Reference-values> -contains <Test-value>`

<span data-ttu-id="5ad3d-253">Exemples :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-253">Examples:</span></span>

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

#### <a name="-notcontains"></a><span data-ttu-id="5ad3d-254">-notcontains</span><span class="sxs-lookup"><span data-stu-id="5ad3d-254">-notcontains</span></span>

<span data-ttu-id="5ad3d-255">Description : opérateur de relation contenant-contenu.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-255">Description: Containment operator.</span></span> <span data-ttu-id="5ad3d-256">Indique si une collection de valeurs de référence comprend une seule valeur de test.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-256">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="5ad3d-257">Retourne toujours une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-257">Always returns a Boolean value.</span></span> <span data-ttu-id="5ad3d-258">Retourne la valeur TRUE lorsque la valeur de test n’est pas une correspondance exacte pour au moins une des valeurs de référence.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-258">Returns TRUE when the test value is not an exact matches for at least one of the reference values.</span></span>

<span data-ttu-id="5ad3d-259">Lorsque la valeur de test est une collection, l’opérateur NotContains utilise l’égalité de référence.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-259">When the test value is a collection, the NotContains operator uses reference equality.</span></span>

<span data-ttu-id="5ad3d-260">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-260">Syntax:</span></span>

`<Reference-values> -notcontains <Test-value>`

<span data-ttu-id="5ad3d-261">Exemples :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-261">Examples:</span></span>

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

#### <a name="-in"></a><span data-ttu-id="5ad3d-262">-in</span><span class="sxs-lookup"><span data-stu-id="5ad3d-262">-in</span></span>

<span data-ttu-id="5ad3d-263">Description : dans l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-263">Description: In operator.</span></span> <span data-ttu-id="5ad3d-264">Indique si une valeur de test apparaît dans une collection de valeurs de référence.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-264">Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="5ad3d-265">Retourne toujours comme valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-265">Always return as Boolean value.</span></span> <span data-ttu-id="5ad3d-266">Retourne TRUE uniquement lorsque la valeur de test correspond exactement à au moins une des valeurs de référence.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-266">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="5ad3d-267">Lorsque la valeur de test est une collection, l’opérateur in utilise l’égalité de référence.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-267">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="5ad3d-268">Elle retourne TRUE uniquement lorsque l’une des valeurs de référence est la même instance de l’objet de valeur de test.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-268">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="5ad3d-269">L' `-in` opérateur a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-269">The `-in` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="5ad3d-270">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-270">Syntax:</span></span>

`<Test-value> -in <Reference-values>`

<span data-ttu-id="5ad3d-271">Exemples :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-271">Examples:</span></span>

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

#### <a name="-notin"></a><span data-ttu-id="5ad3d-272">-NOTIN</span><span class="sxs-lookup"><span data-stu-id="5ad3d-272">-notin</span></span>

<span data-ttu-id="5ad3d-273">Description : indique si une valeur de test apparaît dans une collection de valeurs de référence.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-273">Description: Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="5ad3d-274">Retourne toujours une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-274">Always returns a Boolean value.</span></span> <span data-ttu-id="5ad3d-275">Retourne la valeur TRUE lorsque la valeur de test n’est pas une correspondance exacte pour au moins une des valeurs de référence.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-275">Returns TRUE when the test value is not an exact match for at least one of the reference values.</span></span>

<span data-ttu-id="5ad3d-276">Lorsque la valeur de test est une collection, l’opérateur in utilise l’égalité de référence.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-276">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="5ad3d-277">Elle retourne TRUE uniquement lorsque l’une des valeurs de référence est la même instance de l’objet de valeur de test.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-277">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="5ad3d-278">L' `-notin` opérateur a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-278">The `-notin` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="5ad3d-279">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-279">Syntax:</span></span>

`<Test-value> -notin <Reference-values>`

<span data-ttu-id="5ad3d-280">Exemples :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-280">Examples:</span></span>

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

### <a name="replacement-operator"></a><span data-ttu-id="5ad3d-281">Opérateur de remplacement</span><span class="sxs-lookup"><span data-stu-id="5ad3d-281">Replacement Operator</span></span>

<span data-ttu-id="5ad3d-282">L' `-replace` opérateur remplace tout ou partie d’une valeur par la valeur spécifiée à l’aide d’expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-282">The `-replace` operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="5ad3d-283">Vous pouvez utiliser l' `-replace` opérateur pour de nombreuses tâches administratives, telles que le changement de nom des fichiers.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-283">You can use the `-replace` operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="5ad3d-284">Par exemple, la commande suivante modifie les extensions de nom de fichier de tous les fichiers. txt en. log :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-284">For example, the following command changes the file name extensions of all .txt files to .log:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

<span data-ttu-id="5ad3d-285">La syntaxe de l' `-replace` opérateur est la suivante, où l' `<original>` espace réservé représente les caractères à remplacer, et l' `<substitute>` espace réservé représente les caractères qui les remplacent :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-285">The syntax of the `-replace` operator is as follows, where the `<original>` placeholder represents the characters to be replaced, and the `<substitute>` placeholder represents the characters that will replace them:</span></span>

`<input> <operator> <original>, <substitute>`

<span data-ttu-id="5ad3d-286">Par défaut, l' `-replace` opérateur ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-286">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="5ad3d-287">Pour respecter la casse, utilisez `-creplace` .</span><span class="sxs-lookup"><span data-stu-id="5ad3d-287">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="5ad3d-288">Pour le rendre explicitement non sensible à la casse, utilisez `-ireplace` .</span><span class="sxs-lookup"><span data-stu-id="5ad3d-288">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="5ad3d-289">Penchez-vous sur les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-289">Consider the following examples:</span></span>

```powershell
PS> "book" -replace "B", "C"
```

```Output
Cook
```

```powershell
"book" -ireplace "B", "C"
```

```Output
Cook
```

```powershell
"book" -creplace "B", "C"
```

```Output
book
```

<span data-ttu-id="5ad3d-290">Il est également possible d’utiliser des expressions régulières pour remplacer dynamiquement du texte à l’aide de groupes de capture et de substitutions.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-290">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="5ad3d-291">Pour plus d’informations, consultez [about_regular_expressions](about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5ad3d-291">For more information, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

#### <a name="substitutions-in-regular-expressions"></a><span data-ttu-id="5ad3d-292">Substitutions dans les expressions régulières</span><span class="sxs-lookup"><span data-stu-id="5ad3d-292">Substitutions in Regular Expressions</span></span>

<span data-ttu-id="5ad3d-293">En outre, les groupes de capture peuvent être référencés dans la \<substitute\> chaîne.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-293">Additionally, capturing groups can be referenced in the \<substitute\> string.</span></span>
<span data-ttu-id="5ad3d-294">Pour ce faire, utilisez le `$` caractère qui précède l’identificateur de groupe.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-294">This is done by using the `$` character before the group identifier.</span></span>

<span data-ttu-id="5ad3d-295">Deux des manières de référencer des groupes de capture sont par **nombre** et par **nom**</span><span class="sxs-lookup"><span data-stu-id="5ad3d-295">Two of the ways to reference capturing groups is by **Number** and by **Name**</span></span>

- <span data-ttu-id="5ad3d-296">Par **nombre** , -
   les groupes de capture sont numérotés de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-296">By **Number** -
Capturing Groups are numbered from left to right.</span></span>

  ```powershell
  "John D. Smith" -replace "(\w+) (\w+)\. (\w+)", '$1.$2.$3@contoso.com'
  ```

  ```Output
  John.D.Smith@contoso.com
  ```

- <span data-ttu-id="5ad3d-297">Par **nom** , les -
   groupes de capture peuvent également être référencés par nom.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-297">By **Name** -
Capturing Groups can also be referenced by name.</span></span>

  ```powershell
  "CONTOSO\Administrator" -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  ```

  ```Output
  FABRIKOM\Administrator
  ```

> [!WARNING]
> <span data-ttu-id="5ad3d-298">Étant donné que le `$` caractère est utilisé dans l’extension de chaîne, vous devez utiliser des chaînes littérales avec substitution, ou placer le caractère dans une séquence d’échappement `$` .</span><span class="sxs-lookup"><span data-stu-id="5ad3d-298">Since the `$` character is used in string expansion, you will need to use literal strings with substitution, or escape the `$` character.</span></span>
>
> ```powershell
> 'Hello World' -replace '(\w+) \w+', "`$1 Universe"
> ```
>
> ```Output
> Hello Universe
> ```
>
> <span data-ttu-id="5ad3d-299">En outre, étant donné que le `$` caractère est utilisé dans la substitution, vous devrez placer dans une séquence d’échappement toutes les instances de votre chaîne.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-299">Additionally, since the `$` character is used in substitution, you will need to escape any instances in your string.</span></span>
>
> ```powershell
> '5.72' -replace '(.+)', '$$$1'
> ```
>
> ```Output
> $5.72
> ```

<span data-ttu-id="5ad3d-300">Pour plus d’informations, consultez [about_regular_expressions](about_Regular_Expressions.md) et [substitutions dans les expressions régulières](/dotnet/standard/base-types/substitutions-in-regular-expressions)</span><span class="sxs-lookup"><span data-stu-id="5ad3d-300">To learn more see [about_Regular_Expressions](about_Regular_Expressions.md) and [Substitutions in Regular Expressions](/dotnet/standard/base-types/substitutions-in-regular-expressions)</span></span>

### <a name="type-comparison"></a><span data-ttu-id="5ad3d-301">Comparaison de types</span><span class="sxs-lookup"><span data-stu-id="5ad3d-301">Type comparison</span></span>

<span data-ttu-id="5ad3d-302">Les opérateurs de comparaison de type ( `-is` et `-isnot` ) sont utilisés pour déterminer si un objet est un type spécifique.</span><span class="sxs-lookup"><span data-stu-id="5ad3d-302">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

#### <a name="-is"></a><span data-ttu-id="5ad3d-303">-est</span><span class="sxs-lookup"><span data-stu-id="5ad3d-303">-is</span></span>

<span data-ttu-id="5ad3d-304">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-304">Syntax:</span></span>

`<object> -is <type reference>`

<span data-ttu-id="5ad3d-305">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-305">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -is [int]
True
PS> $a -is $b.GetType()
False
```

#### <a name="-isnot"></a><span data-ttu-id="5ad3d-306">-IsNot</span><span class="sxs-lookup"><span data-stu-id="5ad3d-306">-isnot</span></span>

<span data-ttu-id="5ad3d-307">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-307">Syntax:</span></span>

`<object> -isnot <type reference>`

<span data-ttu-id="5ad3d-308">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5ad3d-308">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -isnot $b.GetType()
True
PS> $b -isnot [int]
True
```

## <a name="see-also"></a><span data-ttu-id="5ad3d-309">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="5ad3d-309">SEE ALSO</span></span>

- [<span data-ttu-id="5ad3d-310">about_Operators</span><span class="sxs-lookup"><span data-stu-id="5ad3d-310">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="5ad3d-311">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="5ad3d-311">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="5ad3d-312">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="5ad3d-312">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="5ad3d-313">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="5ad3d-313">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="5ad3d-314">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="5ad3d-314">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="5ad3d-315">Where-Object</span><span class="sxs-lookup"><span data-stu-id="5ad3d-315">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)