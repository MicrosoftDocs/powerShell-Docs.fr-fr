---
description: Décrit les opérateurs qui comparent des valeurs dans PowerShell.
Locale: en-US
ms.date: 02/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: d99033caac2412852b3f3de0f7a15b74d7ef8e18
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685949"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="18232-103">À propos des opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="18232-103">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="18232-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="18232-104">Short description</span></span>

<span data-ttu-id="18232-105">Les opérateurs de comparaison dans PowerShell peuvent comparer deux valeurs ou filtrer les éléments d’une collection par rapport à une valeur d’entrée.</span><span class="sxs-lookup"><span data-stu-id="18232-105">The comparison operators in PowerShell can either compare two values or filter elements of a collection against an input value.</span></span>

## <a name="long-description"></a><span data-ttu-id="18232-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="18232-106">Long description</span></span>

<span data-ttu-id="18232-107">Les opérateurs de comparaison vous permettent de comparer des valeurs ou de rechercher des valeurs qui correspondent aux modèles spécifiés.</span><span class="sxs-lookup"><span data-stu-id="18232-107">Comparison operators let you compare values or finding values that match specified patterns.</span></span> <span data-ttu-id="18232-108">PowerShell comprend les opérateurs de comparaison suivants :</span><span class="sxs-lookup"><span data-stu-id="18232-108">PowerShell includes the following comparison operators:</span></span>

|    <span data-ttu-id="18232-109">Type</span><span class="sxs-lookup"><span data-stu-id="18232-109">Type</span></span>     |   <span data-ttu-id="18232-110">Opérateur</span><span class="sxs-lookup"><span data-stu-id="18232-110">Operator</span></span>   |              <span data-ttu-id="18232-111">Test de comparaison</span><span class="sxs-lookup"><span data-stu-id="18232-111">Comparison test</span></span>              |
| ----------- | ------------ | ----------------------------------------- |
| <span data-ttu-id="18232-112">Égalité</span><span class="sxs-lookup"><span data-stu-id="18232-112">Equality</span></span>    | <span data-ttu-id="18232-113">-eq</span><span class="sxs-lookup"><span data-stu-id="18232-113">-eq</span></span>          | <span data-ttu-id="18232-114">equals</span><span class="sxs-lookup"><span data-stu-id="18232-114">equals</span></span>                                    |
|             | <span data-ttu-id="18232-115">-ne</span><span class="sxs-lookup"><span data-stu-id="18232-115">-ne</span></span>          | <span data-ttu-id="18232-116">n’est pas égal à</span><span class="sxs-lookup"><span data-stu-id="18232-116">not equals</span></span>                                |
|             | <span data-ttu-id="18232-117">-gt</span><span class="sxs-lookup"><span data-stu-id="18232-117">-gt</span></span>          | <span data-ttu-id="18232-118">supérieur à</span><span class="sxs-lookup"><span data-stu-id="18232-118">greater than</span></span>                              |
|             | <span data-ttu-id="18232-119">-ge</span><span class="sxs-lookup"><span data-stu-id="18232-119">-ge</span></span>          | <span data-ttu-id="18232-120">supérieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="18232-120">greater than or equal</span></span>                     |
|             | <span data-ttu-id="18232-121">-lt</span><span class="sxs-lookup"><span data-stu-id="18232-121">-lt</span></span>          | <span data-ttu-id="18232-122">inférieur à</span><span class="sxs-lookup"><span data-stu-id="18232-122">less than</span></span>                                 |
|             | <span data-ttu-id="18232-123">-le</span><span class="sxs-lookup"><span data-stu-id="18232-123">-le</span></span>          | <span data-ttu-id="18232-124">inférieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="18232-124">less than or equal</span></span>                        |
| <span data-ttu-id="18232-125">Matching</span><span class="sxs-lookup"><span data-stu-id="18232-125">Matching</span></span>    | <span data-ttu-id="18232-126">-like</span><span class="sxs-lookup"><span data-stu-id="18232-126">-like</span></span>        | <span data-ttu-id="18232-127">la chaîne correspond au modèle de caractère générique</span><span class="sxs-lookup"><span data-stu-id="18232-127">string matches wildcard pattern</span></span>           |
|             | <span data-ttu-id="18232-128">-notlike</span><span class="sxs-lookup"><span data-stu-id="18232-128">-notlike</span></span>     | <span data-ttu-id="18232-129">la chaîne ne correspond pas au modèle de caractère générique</span><span class="sxs-lookup"><span data-stu-id="18232-129">string does not match wildcard pattern</span></span>    |
|             | <span data-ttu-id="18232-130">-match</span><span class="sxs-lookup"><span data-stu-id="18232-130">-match</span></span>       | <span data-ttu-id="18232-131">la chaîne correspond au modèle Regex</span><span class="sxs-lookup"><span data-stu-id="18232-131">string matches regex pattern</span></span>              |
|             | <span data-ttu-id="18232-132">-notmatch</span><span class="sxs-lookup"><span data-stu-id="18232-132">-notmatch</span></span>    | <span data-ttu-id="18232-133">la chaîne ne correspond pas au modèle Regex</span><span class="sxs-lookup"><span data-stu-id="18232-133">string does not match regex pattern</span></span>       |
| <span data-ttu-id="18232-134">Remplacement</span><span class="sxs-lookup"><span data-stu-id="18232-134">Replacement</span></span> | <span data-ttu-id="18232-135">-remplacer</span><span class="sxs-lookup"><span data-stu-id="18232-135">-replace</span></span>     | <span data-ttu-id="18232-136">remplace les chaînes correspondant à un modèle Regex</span><span class="sxs-lookup"><span data-stu-id="18232-136">replaces strings matching a regex pattern</span></span> |
| <span data-ttu-id="18232-137">Containment</span><span class="sxs-lookup"><span data-stu-id="18232-137">Containment</span></span> | <span data-ttu-id="18232-138">-contains</span><span class="sxs-lookup"><span data-stu-id="18232-138">-contains</span></span>    | <span data-ttu-id="18232-139">la collection contient une valeur</span><span class="sxs-lookup"><span data-stu-id="18232-139">collection contains a value</span></span>               |
|             | <span data-ttu-id="18232-140">-notcontains</span><span class="sxs-lookup"><span data-stu-id="18232-140">-notcontains</span></span> | <span data-ttu-id="18232-141">la collection ne contient pas de valeur</span><span class="sxs-lookup"><span data-stu-id="18232-141">collection does not contain a value</span></span>       |
|             | <span data-ttu-id="18232-142">-in</span><span class="sxs-lookup"><span data-stu-id="18232-142">-in</span></span>          | <span data-ttu-id="18232-143">la valeur se trouve dans une collection</span><span class="sxs-lookup"><span data-stu-id="18232-143">value is in a collection</span></span>                  |
|             | <span data-ttu-id="18232-144">-NOTIN</span><span class="sxs-lookup"><span data-stu-id="18232-144">-notin</span></span>       | <span data-ttu-id="18232-145">la valeur ne se trouve pas dans une collection</span><span class="sxs-lookup"><span data-stu-id="18232-145">value is not in a collection</span></span>              |
| <span data-ttu-id="18232-146">Type</span><span class="sxs-lookup"><span data-stu-id="18232-146">Type</span></span>        | <span data-ttu-id="18232-147">-est</span><span class="sxs-lookup"><span data-stu-id="18232-147">-is</span></span>          | <span data-ttu-id="18232-148">les deux objets sont du même type</span><span class="sxs-lookup"><span data-stu-id="18232-148">both objects are the same type</span></span>            |
|             | <span data-ttu-id="18232-149">-IsNot</span><span class="sxs-lookup"><span data-stu-id="18232-149">-isnot</span></span>       | <span data-ttu-id="18232-150">les objets ne sont pas du même type</span><span class="sxs-lookup"><span data-stu-id="18232-150">the objects are not the same type</span></span>         |

## <a name="common-features"></a><span data-ttu-id="18232-151">Fonctionnalités communes</span><span class="sxs-lookup"><span data-stu-id="18232-151">Common features</span></span>

<span data-ttu-id="18232-152">Par défaut, tous les opérateurs de comparaison ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="18232-152">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="18232-153">Pour rendre un opérateur de comparaison sensible à la casse, ajoutez un `c` après `-` .</span><span class="sxs-lookup"><span data-stu-id="18232-153">To make a comparison operator case-sensitive, add a `c` after the `-`.</span></span> <span data-ttu-id="18232-154">Par exemple, `-ceq` est la version qui respecte la casse de `-eq` .</span><span class="sxs-lookup"><span data-stu-id="18232-154">For example, `-ceq` is the case-sensitive version of `-eq`.</span></span> <span data-ttu-id="18232-155">Pour rendre le non-respect de la casse explicite, ajoutez un `i` avant `-` .</span><span class="sxs-lookup"><span data-stu-id="18232-155">To make the case-insensitivity explicit, add an `i` before `-`.</span></span> <span data-ttu-id="18232-156">Par exemple, `-ieq` est la version de non-respect de la casse explicite de `-eq` .</span><span class="sxs-lookup"><span data-stu-id="18232-156">For example, `-ieq` is the explicitly case-insensitive version of `-eq`.</span></span>

<span data-ttu-id="18232-157">Lorsque l’entrée d’un opérateur est une valeur scalaire, l’opérateur retourne une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="18232-157">When the input of an operator is a scalar value, the operator returns a **Boolean** value.</span></span> <span data-ttu-id="18232-158">Lorsque l’entrée est une collection, l’opérateur retourne les éléments de la collection qui correspondent à la valeur de droite de l’expression.</span><span class="sxs-lookup"><span data-stu-id="18232-158">When the input is a collection, the operator returns the elements of the collection that match the right-hand value of the expression.</span></span>
<span data-ttu-id="18232-159">S’il n’y a aucune correspondance dans la collection, les opérateurs de comparaison retournent un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="18232-159">If there are no matches in the collection, comparison operators return an empty array.</span></span> <span data-ttu-id="18232-160">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="18232-160">For example:</span></span>

```powershell
$a = (1, 2 -eq 3)
$a.GetType().Name
$a.Count
```

```output
Object[]
0
```

<span data-ttu-id="18232-161">Il existe quelques exceptions :</span><span class="sxs-lookup"><span data-stu-id="18232-161">There are a few exceptions:</span></span>

- <span data-ttu-id="18232-162">Les opérateurs de relation contenant-contenu et type retournent toujours une valeur **booléenne**</span><span class="sxs-lookup"><span data-stu-id="18232-162">The containment and type operators always return a **Boolean** value</span></span>
- <span data-ttu-id="18232-163">L' `-replace` opérateur retourne le résultat de remplacement</span><span class="sxs-lookup"><span data-stu-id="18232-163">The `-replace` operator returns the replacement result</span></span>
- <span data-ttu-id="18232-164">Les `-match` `-notmatch` opérateurs et remplissent également la `$Matches` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="18232-164">The `-match` and `-notmatch` operators also populate the `$Matches` automatic variable</span></span>

## <a name="equality-operators"></a><span data-ttu-id="18232-165">Opérateurs d’égalité</span><span class="sxs-lookup"><span data-stu-id="18232-165">Equality operators</span></span>

### <a name="-eq-and--ne"></a><span data-ttu-id="18232-166">-eq et -ne</span><span class="sxs-lookup"><span data-stu-id="18232-166">-eq and -ne</span></span>

<span data-ttu-id="18232-167">Lorsque la partie gauche est scalaire, `-eq` retourne **true** si le côté droit est une correspondance exacte ; sinon, `-eq` retourne **false**.</span><span class="sxs-lookup"><span data-stu-id="18232-167">When the left-hand side is scalar, `-eq` returns **True** if the right-hand side is an exact match, otherwise, `-eq` returns **False**.</span></span> <span data-ttu-id="18232-168">`-ne` fait l’inverse ; elle retourne **false** lorsque les deux côtés correspondent ; Sinon, `-ne` retourne la valeur true.</span><span class="sxs-lookup"><span data-stu-id="18232-168">`-ne` does the opposite; it returns **False** when both sides match; otherwise, `-ne` returns True.</span></span>

<span data-ttu-id="18232-169">Exemple :</span><span class="sxs-lookup"><span data-stu-id="18232-169">Example:</span></span>

```powershell
2 -eq 2                 # Output: True
2 -eq 3                 # Output: False
"abc" -eq "abc"         # Output: True
"abc" -eq "abc", "def"  # Output: False
"abc" -ne "def"         # Output: True
"abc" -ne "abc"         # Output: False
"abc" -ne "abc", "def"  # Output: True
```

<span data-ttu-id="18232-170">Lorsque la partie gauche est une collection, `-eq` retourne les membres qui correspondent à la partie droite, tout en `-ne` les filtrant.</span><span class="sxs-lookup"><span data-stu-id="18232-170">When the left-hand side is a collection, `-eq` returns those members that match the right-hand side, while `-ne` filters them out.</span></span>

<span data-ttu-id="18232-171">Exemple :</span><span class="sxs-lookup"><span data-stu-id="18232-171">Example:</span></span>

```powershell
1,2,3 -eq 2             # Output: 2
"abc", "def" -eq "abc"  # Output: abc
"abc", "def" -ne "abc"  # Output: def
```

<span data-ttu-id="18232-172">Ces opérateurs traitent tous les éléments de la collection.</span><span class="sxs-lookup"><span data-stu-id="18232-172">These operators process all elements of the collection.</span></span> <span data-ttu-id="18232-173">Exemple :</span><span class="sxs-lookup"><span data-stu-id="18232-173">Example:</span></span>

```powershell
"zzz", "def", "zzz" -eq "zzz"
```

```output
zzz
zzz
```

<span data-ttu-id="18232-174">Les opérateurs d’égalité acceptent deux objets, et pas seulement une collection scalaire ou.</span><span class="sxs-lookup"><span data-stu-id="18232-174">The equality operators accept any two objects, not just a scalar or collection.</span></span>
<span data-ttu-id="18232-175">Mais il n’est pas garanti que le résultat de la comparaison soit significatif pour l’utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="18232-175">But the comparison result is not guaranteed to be meaningful for the end-user.</span></span>
<span data-ttu-id="18232-176">L’exemple suivant illustre le problème.</span><span class="sxs-lookup"><span data-stu-id="18232-176">The following example demonstrates the issue.</span></span>

```powershell
class MyFileInfoSet {
    [String]$File
    [Int64]$Size
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
False
```

<span data-ttu-id="18232-177">Dans cet exemple, nous avons créé deux objets avec des propriétés identiques.</span><span class="sxs-lookup"><span data-stu-id="18232-177">In this example, we created two objects with identical properties.</span></span> <span data-ttu-id="18232-178">Pourtant, le résultat du test d’égalité est **false** , car il s’agit d’objets différents.</span><span class="sxs-lookup"><span data-stu-id="18232-178">Yet, the equality test result is **False** because they are different objects.</span></span> <span data-ttu-id="18232-179">Pour créer des classes comparables, vous devez implémenter [System \<T> . IEquatable][2] dans votre classe.</span><span class="sxs-lookup"><span data-stu-id="18232-179">To create comparable classes, you need to implement [System.IEquatable\<T>][2] in your class.</span></span> <span data-ttu-id="18232-180">L’exemple suivant illustre l’implémentation partielle d’une classe **MyFileInfoSet** qui implémente [System. IEquatable \<T>][2] et a deux propriétés, **file** et **Size**.</span><span class="sxs-lookup"><span data-stu-id="18232-180">The following example demonstrates the partial implementation of a **MyFileInfoSet** class that implements [System.IEquatable\<T>][2] and has two properties, **File** and **Size**.</span></span> <span data-ttu-id="18232-181">La `Equals()` méthode retourne la valeur true si les propriétés de fichier et de taille de deux objets **MyFileInfoSet** sont identiques.</span><span class="sxs-lookup"><span data-stu-id="18232-181">The `Equals()` method returns True if the File and Size properties of two **MyFileInfoSet** objects are the same.</span></span>

```powershell
class MyFileInfoSet : System.IEquatable[Object] {
    [String]$File
    [Int64]$Size

    [bool] Equals([Object] $obj) {
        return ($this.File -eq $obj.File) -and ($this.Size -eq $obj.Size)
    }
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
True
```

<span data-ttu-id="18232-182">Un exemple évident de comparaison d’objets arbitraires consiste à déterminer s’ils ont la valeur null.</span><span class="sxs-lookup"><span data-stu-id="18232-182">A prominent example of comparing arbitrary objects is to find out if they are null.</span></span> <span data-ttu-id="18232-183">Toutefois, si vous devez déterminer si une variable est `$null` , vous devez placer le `$null` côté gauche de l’opérateur d’égalité.</span><span class="sxs-lookup"><span data-stu-id="18232-183">But if you need to determine whether a variable is `$null`, you must put `$null` on the left-hand side of the equality operator.</span></span> <span data-ttu-id="18232-184">Le fait de le placer sur le côté droit ne fait pas ce que vous attendez.</span><span class="sxs-lookup"><span data-stu-id="18232-184">Putting it on the right-hand side does not do what you expect.</span></span>

<span data-ttu-id="18232-185">Prenons l’exemple d' `$a` un tableau contenant des éléments null :</span><span class="sxs-lookup"><span data-stu-id="18232-185">For example, let `$a` be an array containing null elements:</span></span>

```powershell
$a = 1, 2, $null, 4, $null, 6
```

<span data-ttu-id="18232-186">Les tests suivants n' `$a` ont pas la valeur null.</span><span class="sxs-lookup"><span data-stu-id="18232-186">The following tests that `$a` is not null.</span></span>

```powershell
$null -ne $a
```

```output
True
```

<span data-ttu-id="18232-187">Les éléments suivants, cependant, décodent tous les éléments null de `$a` :</span><span class="sxs-lookup"><span data-stu-id="18232-187">The following, however, filers out all null elements from `$a`:</span></span>

```powershell
$a -ne $null # Output: 1, 2, 4, 6
```

```output
1
2
4
6
```

### <a name="-gt--ge--lt-and--le"></a><span data-ttu-id="18232-188">-gt,-GE,-LT et-le</span><span class="sxs-lookup"><span data-stu-id="18232-188">-gt, -ge, -lt, and -le</span></span>

<span data-ttu-id="18232-189">`-gt`, `-ge` , `-lt` et `-le` se comportent de façon très similaire.</span><span class="sxs-lookup"><span data-stu-id="18232-189">`-gt`, `-ge`, `-lt`, and `-le` behave very similarly.</span></span> <span data-ttu-id="18232-190">Lorsque les deux côtés sont scalaires, ils retournent la **valeur true** ou **false** en fonction de la comparaison des deux côtés :</span><span class="sxs-lookup"><span data-stu-id="18232-190">When both sides are scalar they return **True** or **False** depending on how the two sides compare:</span></span>

| <span data-ttu-id="18232-191">Opérateur</span><span class="sxs-lookup"><span data-stu-id="18232-191">Operator</span></span> | <span data-ttu-id="18232-192">Retourne la valeur true lorsque...</span><span class="sxs-lookup"><span data-stu-id="18232-192">Returns True when...</span></span>                   |
| -------- | -------------------------------------- |
| <span data-ttu-id="18232-193">-gt</span><span class="sxs-lookup"><span data-stu-id="18232-193">-gt</span></span>      | <span data-ttu-id="18232-194">La partie gauche est supérieure</span><span class="sxs-lookup"><span data-stu-id="18232-194">The left-hand side is greater</span></span>          |
| <span data-ttu-id="18232-195">-ge</span><span class="sxs-lookup"><span data-stu-id="18232-195">-ge</span></span>      | <span data-ttu-id="18232-196">Le côté gauche est supérieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="18232-196">The left-hand side is greater or equal</span></span> |
| <span data-ttu-id="18232-197">-lt</span><span class="sxs-lookup"><span data-stu-id="18232-197">-lt</span></span>      | <span data-ttu-id="18232-198">La partie gauche est plus petite</span><span class="sxs-lookup"><span data-stu-id="18232-198">The left-hand side is smaller</span></span>          |
| <span data-ttu-id="18232-199">-le</span><span class="sxs-lookup"><span data-stu-id="18232-199">-le</span></span>      | <span data-ttu-id="18232-200">La partie gauche est plus petite ou égale</span><span class="sxs-lookup"><span data-stu-id="18232-200">The left-hand side is smaller or equal</span></span> |

<span data-ttu-id="18232-201">Dans les exemples suivants, toutes les instructions retournent la valeur true.</span><span class="sxs-lookup"><span data-stu-id="18232-201">In the following examples, all statements return True.</span></span>

```powershell
8 -gt 6  # Output: True
8 -ge 8  # Output: True
6 -lt 8  # Output: True
8 -le 8  # Output: True
```

> [!NOTE]
> <span data-ttu-id="18232-202">Dans la plupart des langages de programmation, l’opérateur « supérieur à » est `>` .</span><span class="sxs-lookup"><span data-stu-id="18232-202">In most programming languages the greater-than operator is `>`.</span></span> <span data-ttu-id="18232-203">Dans PowerShell, ce caractère est utilisé pour la redirection.</span><span class="sxs-lookup"><span data-stu-id="18232-203">In PowerShell, this character is used for redirection.</span></span> <span data-ttu-id="18232-204">Pour plus d’informations, consultez [about_Redirection][3].</span><span class="sxs-lookup"><span data-stu-id="18232-204">For details, see [about_Redirection][3].</span></span>

<span data-ttu-id="18232-205">Lorsque la partie gauche est une collection, ces opérateurs comparent chaque membre de la collection avec le côté droit.</span><span class="sxs-lookup"><span data-stu-id="18232-205">When the left-hand side is a collection, these operators compare each member of the collection with the right-hand side.</span></span> <span data-ttu-id="18232-206">En fonction de leur logique, ils conservent ou ignorent le membre.</span><span class="sxs-lookup"><span data-stu-id="18232-206">Depending on their logic, they either keep or discard the member.</span></span>

<span data-ttu-id="18232-207">Exemple :</span><span class="sxs-lookup"><span data-stu-id="18232-207">Example:</span></span>

```powershell
$a=5, 6, 7, 8, 9

Write-Output "Test collection:"
$a

Write-Output "`nMembers greater than 7"
$a -gt 7

Write-Output "`nMembers greater than or equal to 7"
$a -ge 7

Write-Output "`nMembers smaller than 7"
$a -lt 7

Write-Output "`nMembers smaller than or equal to 7"
$a -le 7
```

```output
Test collection:
5
6
7
8
9

Members greater than 7
8
9

Members greater than or equal to 7
7
8
9

Members smaller than 7
5
6

Members smaller than or equal to 7
5
6
7
```

<span data-ttu-id="18232-208">Ces opérateurs fonctionnent avec toute classe qui implémente [System. IComparable][1].</span><span class="sxs-lookup"><span data-stu-id="18232-208">These operators work with any class that implements [System.IComparable][1].</span></span>

<span data-ttu-id="18232-209">Exemples :</span><span class="sxs-lookup"><span data-stu-id="18232-209">Examples:</span></span>

```powershell
# Date comparison
[DateTime]'2001-11-12' -lt [DateTime]'2020-08-01' # True

# Sorting order comparison
'a' -lt 'z'           # True; 'a' comes before 'z'
'macOS' -ilt 'MacOS'  # False
'MacOS' -ilt 'macOS'  # False
'macOS' -clt 'MacOS'  # True; 'm' comes before 'M'
```

<span data-ttu-id="18232-210">L’exemple suivant montre qu’il n’y a aucun symbole sur un clavier américain QWERTY trié après « a ».</span><span class="sxs-lookup"><span data-stu-id="18232-210">The following example demonstrates that there is no symbol on an American QWERTY keyboard that gets sorted after 'a'.</span></span> <span data-ttu-id="18232-211">Il alimente un jeu contenant tous les symboles de ce type à l' `-gt` opérateur pour les comparer à « a ».</span><span class="sxs-lookup"><span data-stu-id="18232-211">It feeds a set containing all such symbols to the `-gt` operator to compare them against 'a'.</span></span> <span data-ttu-id="18232-212">La sortie est un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="18232-212">The output is an empty array.</span></span>

```powershell
$a=' ','`','~','!','@','#','$','%','^','&','*','(',')','_','+','-','=',
   '{','}','[',']',':',';','"','''','\','|','/','?','.','>',',','<'
$a -gt 'a'
# Output: Nothing
```

<span data-ttu-id="18232-213">Si les deux côtés des opérateurs ne sont pas raisonnablement comparables, ces opérateurs déclenchent une erreur sans fin d’achèvement.</span><span class="sxs-lookup"><span data-stu-id="18232-213">If the two sides of the operators are not reasonably comparable, these operators raise a non-terminating error.</span></span>

## <a name="matching-operators"></a><span data-ttu-id="18232-214">Opérateurs correspondants</span><span class="sxs-lookup"><span data-stu-id="18232-214">Matching operators</span></span>

<span data-ttu-id="18232-215">Les opérateurs correspondants ( `-like` , `-notlike` , `-match` et `-notmatch` ) recherchent les éléments qui correspondent ou ne correspondent pas à un modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="18232-215">The matching operators (`-like`, `-notlike`, `-match`, and `-notmatch`) find elements that match or do not match a specified pattern.</span></span> <span data-ttu-id="18232-216">Le modèle pour `-like` et `-notlike` est une expression générique (contenant `*` , `?` et `[ ]` ), tandis que `-match` et `-notmatch` acceptent une expression régulière (Regex).</span><span class="sxs-lookup"><span data-stu-id="18232-216">The pattern for `-like` and `-notlike` is a wildcard expression (containing `*`, `?`, and `[ ]`), while `-match` and `-notmatch` accept a regular expression (Regex).</span></span>

<span data-ttu-id="18232-217">La syntaxe est :</span><span class="sxs-lookup"><span data-stu-id="18232-217">The syntax is:</span></span>

```
<string[]> -like    <wildcard-expression>
<string[]> -notlike <wildcard-expression>
<string[]> -match    <regular-expression>
<string[]> -notmatch <regular-expression>
```

<span data-ttu-id="18232-218">Lorsque l’entrée de ces opérateurs est une valeur scalaire, ils retournent une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="18232-218">When the input of these operators is a scalar value, they return a **Boolean** value.</span></span> <span data-ttu-id="18232-219">Lorsque l’entrée est une collection de valeurs, les opérateurs retournent tous les membres correspondants.</span><span class="sxs-lookup"><span data-stu-id="18232-219">When the input is a collection of values, the operators return any matching members.</span></span> <span data-ttu-id="18232-220">S’il n’existe aucune correspondance dans une collection, les opérateurs retournent un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="18232-220">If there are no matches in a collection, the operators return an empty array.</span></span>

### <a name="-like-and--notlike"></a><span data-ttu-id="18232-221">-like et-NOTLIKE</span><span class="sxs-lookup"><span data-stu-id="18232-221">-like and -notlike</span></span>

<span data-ttu-id="18232-222">`-like` et `-notlike` se comportent de la même façon `-eq` que et `-ne` , mais le côté droit peut être une chaîne contenant des [caractères génériques](about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="18232-222">`-like` and `-notlike` behave similarly to `-eq` and `-ne`, but the right-hand side could be a string containing [wildcards](about_Wildcards.md).</span></span>

<span data-ttu-id="18232-223">Exemple :</span><span class="sxs-lookup"><span data-stu-id="18232-223">Example:</span></span>

```powershell
"PowerShell" -like    "*shell"           # Output: True
"PowerShell" -notlike "*shell"           # Output: False
"PowerShell" -like    "Power?hell"       # Output: True
"PowerShell" -notlike "Power?hell"       # Output: False
"PowerShell" -like    "Power[p-w]hell"   # Output: True
"PowerShell" -notlike "Power[p-w]hell"   # Output: False

"PowerShell", "Server" -like "*shell"    # Output: PowerShell
"PowerShell", "Server" -notlike "*shell" # Output: Server
```

### <a name="-match-and--notmatch"></a><span data-ttu-id="18232-224">-match et-notmatch</span><span class="sxs-lookup"><span data-stu-id="18232-224">-match and -notmatch</span></span>

<span data-ttu-id="18232-225">`-match` et `-notmatch` utilisent des expressions régulières pour rechercher le modèle dans les valeurs de gauche.</span><span class="sxs-lookup"><span data-stu-id="18232-225">`-match` and `-notmatch` use regular expressions to search for pattern in the left-hand side values.</span></span> <span data-ttu-id="18232-226">Les expressions régulières peuvent correspondre à des modèles complexes tels que des adresses de messagerie, des chemins d’accès UNC ou des numéros de téléphone mis en forme.</span><span class="sxs-lookup"><span data-stu-id="18232-226">Regular expressions can match complex patterns like email addresses, UNC paths, or formatted phone numbers.</span></span> <span data-ttu-id="18232-227">La chaîne de droite doit respecter les règles d' [expressions régulières](about_Regular_Expressions.md) .</span><span class="sxs-lookup"><span data-stu-id="18232-227">The right-hand side string must adhere to the [regular expressions](about_Regular_Expressions.md) rules.</span></span>

<span data-ttu-id="18232-228">Exemples scalaires :</span><span class="sxs-lookup"><span data-stu-id="18232-228">Scalar examples:</span></span>

```powershell
# Partial match test, showing how differently -match and -like behave
"PowerShell" -match 'shell'        # Output: True
"PowerShell" -like  'shell'        # Output: False

# Regex syntax test
"PowerShell" -match    '^Power\w+' # Output: True
'bag'        -notmatch 'b[iou]g'   # Output: True
```

<span data-ttu-id="18232-229">Si l’entrée est une collection, les opérateurs retournent les membres correspondants de cette collection.</span><span class="sxs-lookup"><span data-stu-id="18232-229">If the input is a collection, the operators return the matching members of that collection.</span></span>

<span data-ttu-id="18232-230">Exemples de collection :</span><span class="sxs-lookup"><span data-stu-id="18232-230">Collection examples:</span></span>

```powershell
"PowerShell", "Super PowerShell", "Power's hell" -match '^Power\w+'
# Output: PowerShell

"Rhell", "Chell", "Mel", "Smell", "Shell" -match "hell"
# Output: Rhell, Chell, Shell

"Bag", "Beg", "Big", "Bog", "Bug"  -match 'b[iou]g'
#Output: Big, Bog, Bug

"Bag", "Beg", "Big", "Bog", "Bug"  -notmatch 'b[iou]g'
#Output: Bag, Beg
```

<span data-ttu-id="18232-231">`-match` et `-notmatch` prennent en charge les groupes de capture Regex.</span><span class="sxs-lookup"><span data-stu-id="18232-231">`-match` and `-notmatch` support regex capture groups.</span></span> <span data-ttu-id="18232-232">Chaque fois qu’ils s’exécutent, ils remplacent la `$Matches` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="18232-232">Each time they run, they overwrite the `$Matches` automatic variable.</span></span> <span data-ttu-id="18232-233">Lorsque `<input>` est une collection `$Matches` , la variable est `$null` .</span><span class="sxs-lookup"><span data-stu-id="18232-233">When `<input>` is a collection the `$Matches` variable is `$null`.</span></span> <span data-ttu-id="18232-234">`$Matches` est une **Hashtable** qui a toujours une clé nommée « 0 », qui stocke la correspondance entière.</span><span class="sxs-lookup"><span data-stu-id="18232-234">`$Matches` is a **Hashtable** that always has a key named '0', which stores the entire match.</span></span> <span data-ttu-id="18232-235">Si l’expression régulière contient des groupes de capture, le `$Matches` contient des clés supplémentaires pour chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="18232-235">If the regular expression contains capture groups, the `$Matches` contains additional keys for each group.</span></span>

<span data-ttu-id="18232-236">Exemple :</span><span class="sxs-lookup"><span data-stu-id="18232-236">Example:</span></span>

```powershell
$string = 'The last logged on user was CONTOSO\jsmith'
$string -match 'was (?<domain>.+)\\(?<user>.+)'

$Matches

Write-Output "`nDomain name:"
$Matches.domain

Write-Output "`nUser name:"
$Matches.user
```

```output
True

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

Domain name:
CONTOSO

User name:
jsmith
```

<span data-ttu-id="18232-237">Pour plus d’informations, consultez [about_regular_expressions](about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="18232-237">For details, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

## <a name="replacement-operator"></a><span data-ttu-id="18232-238">Opérateur de remplacement</span><span class="sxs-lookup"><span data-stu-id="18232-238">Replacement operator</span></span>

### <a name="replacement-with-regular-expressions"></a><span data-ttu-id="18232-239">Remplacement à l’aide d’expressions régulières</span><span class="sxs-lookup"><span data-stu-id="18232-239">Replacement with regular expressions</span></span>

<span data-ttu-id="18232-240">Comme `-match` , l' `-replace` opérateur utilise des expressions régulières pour rechercher le modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="18232-240">Like `-match`, the `-replace` operator uses regular expressions to find the specified pattern.</span></span> <span data-ttu-id="18232-241">Mais contrairement à `-match` , elle remplace les correspondances par une autre valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="18232-241">But unlike `-match`, it replaces the matches with another specified value.</span></span>

<span data-ttu-id="18232-242">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="18232-242">Syntax:</span></span>

```
<input> -replace <regular-expression>, <substitute>
```

<span data-ttu-id="18232-243">L’opérateur remplace tout ou partie d’une valeur par la valeur spécifiée à l’aide d’expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="18232-243">The operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="18232-244">Vous pouvez utiliser l’opérateur pour de nombreuses tâches administratives, telles que le changement de nom des fichiers.</span><span class="sxs-lookup"><span data-stu-id="18232-244">You can use the operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="18232-245">Par exemple, la commande suivante modifie les extensions de nom de fichier de tous les `.txt` fichiers en `.log` :</span><span class="sxs-lookup"><span data-stu-id="18232-245">For example, the following command changes the file name extensions of all `.txt` files to `.log`:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

<span data-ttu-id="18232-246">Par défaut, l' `-replace` opérateur ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="18232-246">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="18232-247">Pour respecter la casse, utilisez `-creplace` .</span><span class="sxs-lookup"><span data-stu-id="18232-247">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="18232-248">Pour le rendre explicitement non sensible à la casse, utilisez `-ireplace` .</span><span class="sxs-lookup"><span data-stu-id="18232-248">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="18232-249">Exemples :</span><span class="sxs-lookup"><span data-stu-id="18232-249">Examples:</span></span>

```powershell
"book" -ireplace "B", "C" # Case insensitive
"book" -creplace "B", "C" # Case-sensitive; hence, nothing to replace
```

```Output
Cook
book
```

### <a name="regular-expressions-substitutions"></a><span data-ttu-id="18232-250">Substitutions d’expressions régulières</span><span class="sxs-lookup"><span data-stu-id="18232-250">Regular expressions substitutions</span></span>

<span data-ttu-id="18232-251">Il est également possible d’utiliser des expressions régulières pour remplacer dynamiquement du texte à l’aide de groupes de capture et de substitutions.</span><span class="sxs-lookup"><span data-stu-id="18232-251">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="18232-252">Les groupes de capture peuvent être référencés dans la `<substitute>` chaîne à l’aide du caractère dollar ( `$` ) avant l’identificateur de groupe.</span><span class="sxs-lookup"><span data-stu-id="18232-252">Capture groups can be referenced in the `<substitute>` string using the dollar sign (`$`) character before the group identifier.</span></span>

<span data-ttu-id="18232-253">Dans l’exemple suivant, l' `-replace` opérateur accepte un nom d’utilisateur sous la forme `DomainName\Username` et convertit le `Username@DomainName` format :</span><span class="sxs-lookup"><span data-stu-id="18232-253">In the following example, the `-replace` operator accepts a username in the form of `DomainName\Username` and converts to the `Username@DomainName` format:</span></span>

```powershell
$SearchExp = '^(?<DomainName>[\w-.]+)\\(?<Username>[\w-.]+)$'
$ReplaceExp = '${Username}@${DomainName}'

'Contoso.local\John.Doe' -replace $SearchExp,$ReplaceExp
```

```output
John.Doe@Contoso.local
```

> [!WARNING]
> <span data-ttu-id="18232-254">Le `$` caractère a des rôles syntatic dans PowerShell et les expressions régulières :</span><span class="sxs-lookup"><span data-stu-id="18232-254">The `$` character has syntatic roles in both PowerShell and regular expressions:</span></span>
>
> - <span data-ttu-id="18232-255">Dans PowerShell, entre guillemets doubles, il désigne les variables et agit comme un opérateur de sous-expression.</span><span class="sxs-lookup"><span data-stu-id="18232-255">In PowerShell, between double quotation marks, it designates variables and acts as a subexpression operator.</span></span>
> - <span data-ttu-id="18232-256">Dans les chaînes de recherche Regex, elle désigne la fin de la ligne</span><span class="sxs-lookup"><span data-stu-id="18232-256">In Regex search strings, it denotes end of the line</span></span>
> - <span data-ttu-id="18232-257">Dans les chaînes de substitution Regex, il désigne les groupes capturés. Veillez à placer vos expressions régulières entre des guillemets simples ou insérer un caractère de `` ` `` soulignement () avant.</span><span class="sxs-lookup"><span data-stu-id="18232-257">In Regex substitution strings, it denotes captured groups.Be sure to either put your regular expressions between single quotation marks or insert a backtick (`` ` ``) character before them.</span></span>

<span data-ttu-id="18232-258">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="18232-258">For example:</span></span>

```powershell
$1 = 'Goodbye'

'Hello World' -replace '(\w+) \w+', "$1 Universe"
# Output: Goodbye Universe

'Hello World' -replace '(\w+) \w+', '$1 Universe'
# Output: Hello Universe
```

<span data-ttu-id="18232-259">`$$` dans Regex, il désigne un littéral `$` .</span><span class="sxs-lookup"><span data-stu-id="18232-259">`$$` in Regex denotes a literal `$`.</span></span> <span data-ttu-id="18232-260">This `$$` dans la chaîne de substitution pour inclure un littéral `$` dans le de remplacement résultant.</span><span class="sxs-lookup"><span data-stu-id="18232-260">This `$$` in the substitution string to include a literal `$` in the resulting replacement.</span></span> <span data-ttu-id="18232-261">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="18232-261">For example:</span></span>

```powershell
'5.72' -replace '(.+)', '$ $1' # Output: $ 5.72
'5.72' -replace '(.+)', '$$$1' # Output: $5.72
'5.72' -replace '(.+)', '$$1'  # Output: $1
```

<span data-ttu-id="18232-262">Pour plus d’informations, consultez [about_regular_expressions](about_Regular_Expressions.md) et [substitutions dans les expressions régulières][4].</span><span class="sxs-lookup"><span data-stu-id="18232-262">To learn more, see [about_Regular_Expressions](about_Regular_Expressions.md) and [Substitutions in Regular Expressions][4].</span></span>

### <a name="substituting-in-a-collection"></a><span data-ttu-id="18232-263">Substitution d’une collection</span><span class="sxs-lookup"><span data-stu-id="18232-263">Substituting in a collection</span></span>

<span data-ttu-id="18232-264">Quand le `<input>` à l' `-replace` opérateur est une collection, PowerShell applique le remplacement à chaque valeur de la collection.</span><span class="sxs-lookup"><span data-stu-id="18232-264">When the `<input>` to the `-replace` operator is a collection, PowerShell applies the replacement to every value in the collection.</span></span> <span data-ttu-id="18232-265">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="18232-265">For example:</span></span>

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

### <a name="replacement-with-a-script-block"></a><span data-ttu-id="18232-266">Remplacement à l’aide d’un bloc de script</span><span class="sxs-lookup"><span data-stu-id="18232-266">Replacement with a script block</span></span>

<span data-ttu-id="18232-267">Dans PowerShell 6 et versions ultérieures, l' `-replace` opérateur accepte également un bloc de script qui effectue le remplacement.</span><span class="sxs-lookup"><span data-stu-id="18232-267">In PowerShell 6 and later, the `-replace` operator also accepts a script block that performs the replacement.</span></span> <span data-ttu-id="18232-268">Le bloc de script s’exécute une fois pour chaque correspondance.</span><span class="sxs-lookup"><span data-stu-id="18232-268">The script block runs once for every match.</span></span>

<span data-ttu-id="18232-269">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="18232-269">Syntax:</span></span>

```powershell
<String> -replace <regular-expression>, {<Script-block>}
```

<span data-ttu-id="18232-270">Dans le bloc de script, utilisez la `$_` variable automatique pour accéder au texte d’entrée qui est remplacé et à d’autres informations utiles.</span><span class="sxs-lookup"><span data-stu-id="18232-270">Within the script block, use the `$_` automatic variable to access the input text being replaced and other useful information.</span></span> <span data-ttu-id="18232-271">Le type de classe de cette variable est [System. Text. RegularExpressions. match][2].</span><span class="sxs-lookup"><span data-stu-id="18232-271">This variable's class type is [System.Text.RegularExpressions.Match][2].</span></span>

<span data-ttu-id="18232-272">L’exemple suivant remplace chaque séquence de trois chiffres par les caractères équivalents.</span><span class="sxs-lookup"><span data-stu-id="18232-272">The following example replaces each sequence of three digits with the character equivalents.</span></span> <span data-ttu-id="18232-273">Le bloc de script s’exécute pour chaque ensemble de trois chiffres qui doit être remplacé.</span><span class="sxs-lookup"><span data-stu-id="18232-273">The script block runs for each set of three digits that needs to be replaced.</span></span>

```powershell
"072101108108111" -replace "\d{3}", {return [char][int]$_.Value}
```

```output
Hello
```

## <a name="containment-operators"></a><span data-ttu-id="18232-274">Opérateurs de relation contenant-contenu</span><span class="sxs-lookup"><span data-stu-id="18232-274">Containment operators</span></span>

<span data-ttu-id="18232-275">Les opérateurs de relation contenant-contenu ( `-contains` , `-notcontains` , `-in` et `-notin` ) sont similaires aux opérateurs d’égalité, sauf qu’ils retournent toujours une valeur **booléenne** , même lorsque l’entrée est une collection.</span><span class="sxs-lookup"><span data-stu-id="18232-275">The containment operators (`-contains`, `-notcontains`, `-in`, and `-notin`) are similar to the equality operators, except that they always return a **Boolean** value, even when the input is a collection.</span></span> <span data-ttu-id="18232-276">Ces opérateurs cessent de comparer dès qu’ils détectent la première correspondance, tandis que les opérateurs d’égalité évaluent tous les membres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="18232-276">These operators stop comparing as soon as they detect the first match, whereas the equality operators evaluate all input members.</span></span> <span data-ttu-id="18232-277">Dans une collection très volumineuse, ces opérateurs retournent plus rapidement que les opérateurs d’égalité.</span><span class="sxs-lookup"><span data-stu-id="18232-277">In a very large collection, these operators return quicker than the equality operators.</span></span>

<span data-ttu-id="18232-278">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="18232-278">Syntax:</span></span>

```
<Collection> -contains <Test-object>
<Collection> -notcontains <Test-object>
<Test-object> -in <Collection>
<Test-object> -notin <Collection>
```

### <a name="-contains-and--notcontains"></a><span data-ttu-id="18232-279">-contient et-notcontains</span><span class="sxs-lookup"><span data-stu-id="18232-279">-contains and -notcontains</span></span>

<span data-ttu-id="18232-280">Ces opérateurs indiquent si un jeu comprend un certain élément.</span><span class="sxs-lookup"><span data-stu-id="18232-280">These operators tell whether a set includes a certain element.</span></span> <span data-ttu-id="18232-281">`-contains` retourne la valeur true lorsque le côté droit (objet de test) correspond à l’un des éléments du jeu.</span><span class="sxs-lookup"><span data-stu-id="18232-281">`-contains` returns True when the right-hand side (test object) matches one of the elements in the set.</span></span> <span data-ttu-id="18232-282">`-notcontains` retourne false à la place.</span><span class="sxs-lookup"><span data-stu-id="18232-282">`-notcontains` returns False instead.</span></span> <span data-ttu-id="18232-283">Lorsque l’objet de test est une collection, ces opérateurs utilisent l’égalité de référence, c’est-à-dire qu’ils vérifient si l’un des éléments du jeu est la même instance de l’objet de test.</span><span class="sxs-lookup"><span data-stu-id="18232-283">When the test object is a collection, these operators use reference equality, i.e. they check whether one of the set's elements is the same instance of the test object.</span></span>

<span data-ttu-id="18232-284">Exemples :</span><span class="sxs-lookup"><span data-stu-id="18232-284">Examples:</span></span>

```powershell
"abc", "def" -contains "def"                  # Output: True
"abc", "def" -notcontains "def"               # Output: False
"Windows", "PowerShell" -contains "Shell"     # Output: False
"Windows", "PowerShell" -notcontains "Shell"  # Output: True
"abc", "def", "ghi" -contains "abc", "def"    # Output: False
"abc", "def", "ghi" -notcontains "abc", "def" # Output: True
```

<span data-ttu-id="18232-285">Exemples plus complexes :</span><span class="sxs-lookup"><span data-stu-id="18232-285">More complex examples:</span></span>

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$DomainServers -contains $thisComputer
# Output: True

$a = "abc", "def"
"abc", "def", "ghi" -contains $a # Output: False
$a, "ghi" -contains $a           # Output: True
```

### <a name="-in-and--notin"></a><span data-ttu-id="18232-286">-in et-NOTIN</span><span class="sxs-lookup"><span data-stu-id="18232-286">-in and -notin</span></span>

<span data-ttu-id="18232-287">Les `-in` opérateurs et `notin` ont été introduits dans PowerShell 3 comme l’inverse syntaxique des `contains` opérateurs et `-notcontain` .</span><span class="sxs-lookup"><span data-stu-id="18232-287">The `-in` and -`notin` operators were introduced in PowerShell 3 as the syntactic reverse of the of `contains` and `-notcontain` operators.</span></span> <span data-ttu-id="18232-288">`-in` retourne la **valeur true** lorsque la partie gauche `<test-object>` correspond à l’un des éléments du jeu.</span><span class="sxs-lookup"><span data-stu-id="18232-288">`-in` returns **True** when the left-hand side `<test-object>` matches one of the elements in the set.</span></span> <span data-ttu-id="18232-289">`-notin` retourne **false** à la place.</span><span class="sxs-lookup"><span data-stu-id="18232-289">`-notin` returns **False** instead.</span></span> <span data-ttu-id="18232-290">Lorsque l’objet de test est un ensemble, ces opérateurs utilisent l’égalité de référence pour vérifier si l’un des éléments du jeu est la même instance de l’objet de test.</span><span class="sxs-lookup"><span data-stu-id="18232-290">When the test object is a set, these operators use reference equality to check whether one of the set's elements is the same instance of the test object.</span></span>

<span data-ttu-id="18232-291">Les exemples suivants font la même chose que les exemples pour `-contain` et `-notcontain` , mais ils sont écrits avec et à la `-in` `-notin` place.</span><span class="sxs-lookup"><span data-stu-id="18232-291">The following examples do the same thing that the examples for `-contain` and `-notcontain` do, but they are written with `-in` and `-notin` instead.</span></span>

```powershell
"def" -in "abc", "def"                  # Output: True
"def" -notin "abc", "def"               # Output: False
"Shell" -in "Windows", "PowerShell"     # Output: False
"Shell" -notin "Windows", "PowerShell"  # Output: True
"abc", "def" -in "abc", "def", "ghi"    # Output: False
"abc", "def" -notin "abc", "def", "ghi" # Output: True
```

<span data-ttu-id="18232-292">Exemples plus complexes :</span><span class="sxs-lookup"><span data-stu-id="18232-292">More complex examples:</span></span>

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$thisComputer -in $DomainServers
# Output: True

$a = "abc", "def"
$a -in "abc", "def", "ghi" # Output: False
$a -in $a, "ghi"           # Output: True
```

## <a name="type-comparison"></a><span data-ttu-id="18232-293">Comparaison de types</span><span class="sxs-lookup"><span data-stu-id="18232-293">Type comparison</span></span>

<span data-ttu-id="18232-294">Les opérateurs de comparaison de type ( `-is` et `-isnot` ) sont utilisés pour déterminer si un objet est un type spécifique.</span><span class="sxs-lookup"><span data-stu-id="18232-294">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

<span data-ttu-id="18232-295">Syntaxe :</span><span class="sxs-lookup"><span data-stu-id="18232-295">Syntax:</span></span>

```powershell
<object> -is <type-reference>
<object> -isnot <type-reference>
```

<span data-ttu-id="18232-296">Exemple :</span><span class="sxs-lookup"><span data-stu-id="18232-296">Example:</span></span>

```powershell
$a = 1
$b = "1"
$a -is [int]           # Output: True
$a -is $b.GetType()    # Output: False
$b -isnot [int]        # Output: True
$a -isnot $b.GetType() # Output: True
```

## <a name="see-also"></a><span data-ttu-id="18232-297">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="18232-297">SEE ALSO</span></span>

- [<span data-ttu-id="18232-298">about_Operators</span><span class="sxs-lookup"><span data-stu-id="18232-298">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="18232-299">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="18232-299">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="18232-300">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="18232-300">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="18232-301">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="18232-301">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="18232-302">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="18232-302">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="18232-303">Where-Object</span><span class="sxs-lookup"><span data-stu-id="18232-303">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)

[1]: /dotnet/api/system.icomparable
[2]: /dotnet/api/system.iequatable-1
[3]: /dotnet/api/system.text.regularexpressions.match
[4]: about_Redirection.md#potential-confusion-with-comparison-operators
[5]: /dotnet/standard/base-types/substitutions-in-regular-expressions
