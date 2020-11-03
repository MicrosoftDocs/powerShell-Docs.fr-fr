---
description: Décrit les opérateurs qui effectuent des opérations arithmétiques dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arithmetic_Operators
ms.openlocfilehash: 5c9118eaa166beffc9d7a24f77a730d637a36a00
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207501"
---
# <a name="about-arithmetic-operators"></a><span data-ttu-id="8805a-104">À propos des opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="8805a-104">About Arithmetic Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="8805a-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="8805a-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="8805a-106">Décrit les opérateurs qui effectuent des opérations arithmétiques dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8805a-106">Describes the operators that perform arithmetic in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="8805a-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="8805a-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="8805a-108">Les opérateurs arithmétiques calculent des valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="8805a-108">Arithmetic operators calculate numeric values.</span></span> <span data-ttu-id="8805a-109">Vous pouvez utiliser un ou plusieurs opérateurs arithmétiques pour ajouter, soustraire, multiplier et diviser des valeurs, et pour calculer le reste (modulo) d’une opération de division.</span><span class="sxs-lookup"><span data-stu-id="8805a-109">You can use one or more arithmetic operators to add, subtract, multiply, and divide values, and to calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="8805a-110">En outre, l’opérateur d’addition ( `+` ) et l’opérateur de multiplication ( `*` ) fonctionnent également sur les chaînes, les tableaux et les tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="8805a-110">In addition, the addition operator (`+`) and multiplication operator (`*`) also operate on strings, arrays, and hash tables.</span></span> <span data-ttu-id="8805a-111">L’opérateur d’addition concatène l’entrée.</span><span class="sxs-lookup"><span data-stu-id="8805a-111">The addition operator concatenates the input.</span></span> <span data-ttu-id="8805a-112">L’opérateur de multiplication retourne plusieurs copies de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="8805a-112">The multiplication operator returns multiple copies of the input.</span></span> <span data-ttu-id="8805a-113">Vous pouvez même mélanger des types d’objet dans une instruction arithmétique.</span><span class="sxs-lookup"><span data-stu-id="8805a-113">You can even mix object types in an arithmetic statement.</span></span> <span data-ttu-id="8805a-114">La méthode utilisée pour évaluer l’instruction est déterminée par le type de l’objet le plus à gauche dans l’expression.</span><span class="sxs-lookup"><span data-stu-id="8805a-114">The method that is used to evaluate the statement is determined by the type of the leftmost object in the expression.</span></span>

<span data-ttu-id="8805a-115">À compter de PowerShell 2,0, tous les opérateurs arithmétiques fonctionnent sur des nombres 64 bits.</span><span class="sxs-lookup"><span data-stu-id="8805a-115">Beginning in PowerShell 2.0, all arithmetic operators work on 64-bit numbers.</span></span>

<span data-ttu-id="8805a-116">À compter de PowerShell 3,0, le `-shr` (Shift-Right) et `-shl` (Shift-Left) sont ajoutés pour prendre en charge l’arithmétique au niveau du bit dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8805a-116">Beginning in PowerShell 3.0, the `-shr` (shift-right) and `-shl` (shift-left) are added to support bitwise arithmetic in PowerShell.</span></span>

<span data-ttu-id="8805a-117">PowerShell prend en charge les opérateurs arithmétiques suivants :</span><span class="sxs-lookup"><span data-stu-id="8805a-117">PowerShell supports the following arithmetic operators:</span></span>

|<span data-ttu-id="8805a-118">Opérateur</span><span class="sxs-lookup"><span data-stu-id="8805a-118">Operator</span></span>|<span data-ttu-id="8805a-119">Description</span><span class="sxs-lookup"><span data-stu-id="8805a-119">Description</span></span>                       |<span data-ttu-id="8805a-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="8805a-120">Example</span></span>                      |
|--------|----------------------------------|-----------------------------|
| +      |<span data-ttu-id="8805a-121">Ajoute des entiers. concatène</span><span class="sxs-lookup"><span data-stu-id="8805a-121">Adds integers; concatenates</span></span>       |`6 + 2`                      |
|        |<span data-ttu-id="8805a-122">les chaînes, les tableaux et les tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="8805a-122">strings, arrays, and hash tables.</span></span> |`"file" + "name"`            |
|        |                                  |`@(1, "one") + @(2.0, "two")`|
|        |                                  |`@{"one" = 1} + @{"two" = 2}`|
| -      |<span data-ttu-id="8805a-123">Soustrait une valeur d’une autre</span><span class="sxs-lookup"><span data-stu-id="8805a-123">Subtracts one value from another</span></span>  |`6 - 2`                      |
|        |<span data-ttu-id="8805a-124">value</span><span class="sxs-lookup"><span data-stu-id="8805a-124">value</span></span>                             |                             |
| -      |<span data-ttu-id="8805a-125">Fait d’un nombre un nombre négatif</span><span class="sxs-lookup"><span data-stu-id="8805a-125">Makes a number a negative number</span></span>  |`-6`                         |
|        |                                  |`(Get-Date).AddDays(-1)`     |
| *      |<span data-ttu-id="8805a-126">Multiplier des nombres ou copier des chaînes</span><span class="sxs-lookup"><span data-stu-id="8805a-126">Multiply numbers or copy strings</span></span>  |`6 * 2`                      |
|        |<span data-ttu-id="8805a-127">et tableaux le nombre spécifié</span><span class="sxs-lookup"><span data-stu-id="8805a-127">and arrays the specified number</span></span>   |`@("!") * 4`                 |
|        |<span data-ttu-id="8805a-128">de fois.</span><span class="sxs-lookup"><span data-stu-id="8805a-128">of times.</span></span>                         |`"!" * 3`                    |
| /      |<span data-ttu-id="8805a-129">Divise deux valeurs.</span><span class="sxs-lookup"><span data-stu-id="8805a-129">Divides two values.</span></span>               |`6 / 2`                      |
| %      |<span data-ttu-id="8805a-130">Modulo-retourne le reste de</span><span class="sxs-lookup"><span data-stu-id="8805a-130">Modulus - returns the remainder of</span></span>|`7 % 2`                      |
|        |<span data-ttu-id="8805a-131">opération de division.</span><span class="sxs-lookup"><span data-stu-id="8805a-131">a division operation.</span></span>             |                             |
|<span data-ttu-id="8805a-132">-bande</span><span class="sxs-lookup"><span data-stu-id="8805a-132">-band</span></span>   |<span data-ttu-id="8805a-133">ET au niveau du bit</span><span class="sxs-lookup"><span data-stu-id="8805a-133">Bitwise AND</span></span>                       |`5 -band 3`                  |
|<span data-ttu-id="8805a-134">-bnot</span><span class="sxs-lookup"><span data-stu-id="8805a-134">-bnot</span></span>   |<span data-ttu-id="8805a-135">NOT au niveau du bit</span><span class="sxs-lookup"><span data-stu-id="8805a-135">Bitwise NOT</span></span>                       |`-bnot 5`                    |
|<span data-ttu-id="8805a-136">-Bor</span><span class="sxs-lookup"><span data-stu-id="8805a-136">-bor</span></span>    |<span data-ttu-id="8805a-137">Opération de bits OR</span><span class="sxs-lookup"><span data-stu-id="8805a-137">Bitwise OR</span></span>                        |`5 -bor 0x03`                |
|<span data-ttu-id="8805a-138">-bxor</span><span class="sxs-lookup"><span data-stu-id="8805a-138">-bxor</span></span>   |<span data-ttu-id="8805a-139">Opération de bits XOR</span><span class="sxs-lookup"><span data-stu-id="8805a-139">Bitwise XOR</span></span>                       |`5 -bxor 3`                  |
|<span data-ttu-id="8805a-140">-SHL</span><span class="sxs-lookup"><span data-stu-id="8805a-140">-shl</span></span>    |<span data-ttu-id="8805a-141">Décale les bits vers la gauche</span><span class="sxs-lookup"><span data-stu-id="8805a-141">Shifts bits to the left</span></span>           |`102 -shl 2`                 |
|<span data-ttu-id="8805a-142">-SHR</span><span class="sxs-lookup"><span data-stu-id="8805a-142">-shr</span></span>    |<span data-ttu-id="8805a-143">Décale les bits vers la droite</span><span class="sxs-lookup"><span data-stu-id="8805a-143">Shifts bits to the right</span></span>          |`102 -shr 2`                 |

<span data-ttu-id="8805a-144">Les opérateurs au niveau du bit fonctionnent uniquement sur les types entiers.</span><span class="sxs-lookup"><span data-stu-id="8805a-144">The bitwise operators only work on integer types.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="8805a-145">PRIORITÉ DES OPÉRATEURS</span><span class="sxs-lookup"><span data-stu-id="8805a-145">OPERATOR PRECEDENCE</span></span>

<span data-ttu-id="8805a-146">PowerShell traite les opérateurs arithmétiques dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="8805a-146">PowerShell processes arithmetic operators in the following order:</span></span>

|<span data-ttu-id="8805a-147">Priorité</span><span class="sxs-lookup"><span data-stu-id="8805a-147">Precedence</span></span>|<span data-ttu-id="8805a-148">Opérateur</span><span class="sxs-lookup"><span data-stu-id="8805a-148">Operator</span></span>          |<span data-ttu-id="8805a-149">Description</span><span class="sxs-lookup"><span data-stu-id="8805a-149">Description</span></span>                            |
|----------|------------------|---------------------------------------|
|<span data-ttu-id="8805a-150">1</span><span class="sxs-lookup"><span data-stu-id="8805a-150">1</span></span>         | `()`             |<span data-ttu-id="8805a-151">Parenthèses</span><span class="sxs-lookup"><span data-stu-id="8805a-151">Parentheses</span></span>                            |
|<span data-ttu-id="8805a-152">2</span><span class="sxs-lookup"><span data-stu-id="8805a-152">2</span></span>         | `-`              |<span data-ttu-id="8805a-153">Pour un nombre négatif ou un opérateur unaire</span><span class="sxs-lookup"><span data-stu-id="8805a-153">For a negative number or unary operator</span></span>|
|<span data-ttu-id="8805a-154">3</span><span class="sxs-lookup"><span data-stu-id="8805a-154">3</span></span>         | <span data-ttu-id="8805a-155">`*`, `/`, `%`</span><span class="sxs-lookup"><span data-stu-id="8805a-155">`*`, `/`, `%`</span></span>    |<span data-ttu-id="8805a-156">Pour la multiplication et la Division</span><span class="sxs-lookup"><span data-stu-id="8805a-156">For multiplication and division</span></span>        |
|<span data-ttu-id="8805a-157">4</span><span class="sxs-lookup"><span data-stu-id="8805a-157">4</span></span>         | <span data-ttu-id="8805a-158">`+`, `-`</span><span class="sxs-lookup"><span data-stu-id="8805a-158">`+`, `-`</span></span>         |<span data-ttu-id="8805a-159">Pour l’addition et la soustraction</span><span class="sxs-lookup"><span data-stu-id="8805a-159">For addition and subtraction</span></span>           |
|<span data-ttu-id="8805a-160">5</span><span class="sxs-lookup"><span data-stu-id="8805a-160">5</span></span>         | <span data-ttu-id="8805a-161">`-band`, `-bnot`</span><span class="sxs-lookup"><span data-stu-id="8805a-161">`-band`, `-bnot`</span></span> |<span data-ttu-id="8805a-162">Pour les opérations au niveau du bit</span><span class="sxs-lookup"><span data-stu-id="8805a-162">For bitwise operations</span></span>                 |
|<span data-ttu-id="8805a-163">5</span><span class="sxs-lookup"><span data-stu-id="8805a-163">5</span></span>         | <span data-ttu-id="8805a-164">`-bor`, `-bxor`</span><span class="sxs-lookup"><span data-stu-id="8805a-164">`-bor`, `-bxor`</span></span>  |<span data-ttu-id="8805a-165">Pour les opérations au niveau du bit</span><span class="sxs-lookup"><span data-stu-id="8805a-165">For bitwise operations</span></span>                 |
|<span data-ttu-id="8805a-166">5</span><span class="sxs-lookup"><span data-stu-id="8805a-166">5</span></span>         | <span data-ttu-id="8805a-167">`-shr`, `-shl`</span><span class="sxs-lookup"><span data-stu-id="8805a-167">`-shr`, `-shl`</span></span>   |<span data-ttu-id="8805a-168">Pour les opérations au niveau du bit</span><span class="sxs-lookup"><span data-stu-id="8805a-168">For bitwise operations</span></span>                 |

<span data-ttu-id="8805a-169">PowerShell traite les expressions de gauche à droite en fonction des règles de précédence.</span><span class="sxs-lookup"><span data-stu-id="8805a-169">PowerShell processes the expressions from left to right according to the precedence rules.</span></span> <span data-ttu-id="8805a-170">Les exemples suivants illustrent l’effet des règles de précédence :</span><span class="sxs-lookup"><span data-stu-id="8805a-170">The following examples show the effect of the precedence rules:</span></span>

|<span data-ttu-id="8805a-171">Expression</span><span class="sxs-lookup"><span data-stu-id="8805a-171">Expression</span></span> |<span data-ttu-id="8805a-172">Résultats</span><span class="sxs-lookup"><span data-stu-id="8805a-172">Result</span></span>|
|-----------|------|
|`3+6/3*4`  |`11`  |
|`3+6/(3*4)`|`3.5` |
|`(3+6)/3*4`|`12`  |

<span data-ttu-id="8805a-173">L’ordre dans lequel PowerShell évalue les expressions peut différer des autres langages de programmation et de script que vous avez utilisés.</span><span class="sxs-lookup"><span data-stu-id="8805a-173">The order in which PowerShell evaluates expressions might differ from other programming and scripting languages that you have used.</span></span> <span data-ttu-id="8805a-174">L’exemple suivant montre une instruction d’assignation complexe.</span><span class="sxs-lookup"><span data-stu-id="8805a-174">The following example shows a complicated assignment statement.</span></span>

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$b[$a] = $c[$a++]
```

<span data-ttu-id="8805a-175">Dans cet exemple, l’expression `$a++` est évaluée avant `$b[$a]` .</span><span class="sxs-lookup"><span data-stu-id="8805a-175">In this example, the expression `$a++` is evaluated before `$b[$a]`.</span></span>
<span data-ttu-id="8805a-176">`$a++`L’évaluation de modifie la valeur de `$a` lorsqu’elle est utilisée dans l’instruction `$c[$a++]` , mais avant qu’elle ne soit utilisée dans `$b[$a]` .</span><span class="sxs-lookup"><span data-stu-id="8805a-176">Evaluating `$a++` changes the value of `$a` after it is used in the statement `$c[$a++]`; but, before it is used in `$b[$a]`.</span></span> <span data-ttu-id="8805a-177">La variable `$a` de `$b[$a]` est égal `1` à, pas `0` ; par conséquent, l’instruction assigne une valeur à `$b[1]` , et non à `$b[0]` .</span><span class="sxs-lookup"><span data-stu-id="8805a-177">The variable `$a` in `$b[$a]` equals `1`, not `0`; so, the statement assigns a value to `$b[1]`, not `$b[0]`.</span></span>

<span data-ttu-id="8805a-178">Le code ci-dessus équivaut à :</span><span class="sxs-lookup"><span data-stu-id="8805a-178">The above code is equivalent to:</span></span>

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$tmp = $c[$a]
$a = $a + 1
$b[$a] = $tmp
```

## <a name="division-and-rounding"></a><span data-ttu-id="8805a-179">DIVISION ET ARRONDI</span><span class="sxs-lookup"><span data-stu-id="8805a-179">DIVISION AND ROUNDING</span></span>

<span data-ttu-id="8805a-180">Lorsque le quotient d’une opération de division est un entier, PowerShell arrondit la valeur à l’entier le plus proche.</span><span class="sxs-lookup"><span data-stu-id="8805a-180">When the quotient of a division operation is an integer, PowerShell rounds the value to the nearest integer.</span></span> <span data-ttu-id="8805a-181">Lorsque la valeur est `.5` , elle est arrondie à l’entier pair le plus proche.</span><span class="sxs-lookup"><span data-stu-id="8805a-181">When the value is `.5`, it rounds to the nearest even integer.</span></span>

<span data-ttu-id="8805a-182">L’exemple suivant montre l’effet de l’arrondi à l’entier pair le plus proche.</span><span class="sxs-lookup"><span data-stu-id="8805a-182">The following example shows the effect of rounding to the nearest even integer.</span></span>

|<span data-ttu-id="8805a-183">Expression</span><span class="sxs-lookup"><span data-stu-id="8805a-183">Expression</span></span>      |<span data-ttu-id="8805a-184">Résultats</span><span class="sxs-lookup"><span data-stu-id="8805a-184">Result</span></span>|
|----------------|------|
|`[int]( 5 / 2 )`|`2`   |
|`[int]( 7 / 2 )`|`4`   |

<span data-ttu-id="8805a-185">Notez que **_5/2_ = 2,5** est arrondi à **2** .</span><span class="sxs-lookup"><span data-stu-id="8805a-185">Notice how **_5/2_ = 2.5** gets rounded to **2** .</span></span> <span data-ttu-id="8805a-186">Toutefois, **_7/2_ = 3,5** est arrondi à **4** .</span><span class="sxs-lookup"><span data-stu-id="8805a-186">But, **_7/2_ = 3.5** gets rounded to **4** .</span></span>

<span data-ttu-id="8805a-187">Vous pouvez utiliser la `[Math]` classe pour bénéficier d’un comportement d’arrondi différent.</span><span class="sxs-lookup"><span data-stu-id="8805a-187">You can use the `[Math]` class to get different rounding behavior.</span></span>

|                          <span data-ttu-id="8805a-188">Expression</span><span class="sxs-lookup"><span data-stu-id="8805a-188">Expression</span></span>                          | <span data-ttu-id="8805a-189">Résultats</span><span class="sxs-lookup"><span data-stu-id="8805a-189">Result</span></span> |
| ------------------------------------------------------------ | ------ |
| `[int][Math]::Round(5 / 2,[MidpointRounding]::AwayFromZero)` | `3`    |
| `[int][Math]::Ceiling(5 / 2)`                                | `3`    |
| `[int][Math]::Floor(5 / 2)`                                  | `2`    |

<span data-ttu-id="8805a-190">Pour plus d’informations, consultez la méthode [Math. Round](/dotnet/api/system.math.round) .</span><span class="sxs-lookup"><span data-stu-id="8805a-190">For more information, see the [Math.Round](/dotnet/api/system.math.round) method.</span></span>

## <a name="adding-and-multiplying-non-numeric-types"></a><span data-ttu-id="8805a-191">AJOUT ET MULTIPLICATION DE TYPES NON NUMÉRIQUES</span><span class="sxs-lookup"><span data-stu-id="8805a-191">ADDING AND MULTIPLYING NON-NUMERIC TYPES</span></span>

<span data-ttu-id="8805a-192">Vous pouvez ajouter des nombres, des chaînes, des tableaux et des tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="8805a-192">You can add numbers, strings, arrays, and hash tables.</span></span> <span data-ttu-id="8805a-193">Et, vous pouvez multiplier des nombres, des chaînes et des tableaux.</span><span class="sxs-lookup"><span data-stu-id="8805a-193">And, you can multiply numbers, strings, and arrays.</span></span> <span data-ttu-id="8805a-194">Toutefois, vous ne pouvez pas multiplier les tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="8805a-194">However, you cannot multiply hash tables.</span></span>

<span data-ttu-id="8805a-195">Lorsque vous ajoutez des chaînes, des tableaux ou des tables de hachage, les éléments sont concaténés.</span><span class="sxs-lookup"><span data-stu-id="8805a-195">When you add strings, arrays, or hash tables, the elements are concatenated.</span></span> <span data-ttu-id="8805a-196">Lorsque vous concaténez des collections, telles que des tableaux ou des tables de hachage, un nouvel objet contenant les objets des deux collections est créé.</span><span class="sxs-lookup"><span data-stu-id="8805a-196">When you concatenate collections, such as arrays or hash tables, a new object is created that contains the objects from both collections.</span></span> <span data-ttu-id="8805a-197">Si vous essayez de concaténer des tables de hachage qui ont la même clé, l’opération échoue.</span><span class="sxs-lookup"><span data-stu-id="8805a-197">If you try to concatenate hash tables that have the same key, the operation fails.</span></span>

<span data-ttu-id="8805a-198">Par exemple, les commandes suivantes créent deux tableaux, puis les ajoutent :</span><span class="sxs-lookup"><span data-stu-id="8805a-198">For example, the following commands create two arrays and then add them:</span></span>

```powershell
$a = 1,2,3
$b = "A","B","C"
$a + $b
```

```output
1
2
3
A
B
C
```

<span data-ttu-id="8805a-199">Vous pouvez également effectuer des opérations arithmétiques sur des objets de types différents.</span><span class="sxs-lookup"><span data-stu-id="8805a-199">You can also perform arithmetic operations on objects of different types.</span></span>
<span data-ttu-id="8805a-200">L’opération exécutée par PowerShell est déterminée par le type de Microsoft .NET Framework de l’objet le plus à gauche dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="8805a-200">The operation that PowerShell performs is determined by the Microsoft .NET Framework type of the leftmost object in the operation.</span></span> <span data-ttu-id="8805a-201">PowerShell tente de convertir tous les objets de l’opération en .NET Framework type du premier objet.</span><span class="sxs-lookup"><span data-stu-id="8805a-201">PowerShell tries to convert all the objects in the operation to the .NET Framework type of the first object.</span></span> <span data-ttu-id="8805a-202">S’il parvient à convertir les objets, il effectue l’opération appropriée au type de .NET Framework du premier objet.</span><span class="sxs-lookup"><span data-stu-id="8805a-202">If it succeeds in converting the objects, it performs the operation appropriate to the .NET Framework type of the first object.</span></span> <span data-ttu-id="8805a-203">Si la conversion de l’un des objets échoue, l’opération échoue.</span><span class="sxs-lookup"><span data-stu-id="8805a-203">If it fails to convert any of the objects, the operation fails.</span></span>

<span data-ttu-id="8805a-204">Les exemples suivants illustrent l’utilisation des opérateurs d’addition et de multiplication. dans les opérations qui incluent des types d’objets différents.</span><span class="sxs-lookup"><span data-stu-id="8805a-204">The following examples demonstrate the use of the addition and multiplication operators; in operations that include different object types.</span></span> <span data-ttu-id="8805a-205">Supposons que `$array = 1,2,3` :</span><span class="sxs-lookup"><span data-stu-id="8805a-205">Assume `$array = 1,2,3`:</span></span>

|<span data-ttu-id="8805a-206">Expression</span><span class="sxs-lookup"><span data-stu-id="8805a-206">Expression</span></span>       |<span data-ttu-id="8805a-207">Résultats</span><span class="sxs-lookup"><span data-stu-id="8805a-207">Result</span></span>                 |
|-----------------|-----------------------|
|`"file" + 16`    |`file16`               |
|`$array + 16`    |<span data-ttu-id="8805a-208">`1`,`2`,`3`,`16`</span><span class="sxs-lookup"><span data-stu-id="8805a-208">`1`,`2`,`3`,`16`</span></span>       |
|`$array + "file"`|<span data-ttu-id="8805a-209">`1`,`2`,`3`,`file`</span><span class="sxs-lookup"><span data-stu-id="8805a-209">`1`,`2`,`3`,`file`</span></span>     |
|`$array * 2`     |<span data-ttu-id="8805a-210">`1`,`2`,`3`,`1`,`2`,`3`</span><span class="sxs-lookup"><span data-stu-id="8805a-210">`1`,`2`,`3`,`1`,`2`,`3`</span></span>|
|`"file" * 3`     |`filefilefile`         |

<span data-ttu-id="8805a-211">Étant donné que la méthode utilisée pour évaluer les instructions est déterminée par l’objet le plus à gauche, l’addition et la multiplication dans PowerShell ne sont pas strictement commutatables.</span><span class="sxs-lookup"><span data-stu-id="8805a-211">Because the method that is used to evaluate statements is determined by the leftmost object, addition and multiplication in PowerShell are not strictly commutative.</span></span> <span data-ttu-id="8805a-212">Par exemple, `(a + b)` n’est pas toujours égal à `(b + a)` et `(ab)` n’est pas toujours égal à `(ba)` .</span><span class="sxs-lookup"><span data-stu-id="8805a-212">For example, `(a + b)` does not always equal `(b + a)`, and `(ab)` does not always equal `(ba)`.</span></span>

<span data-ttu-id="8805a-213">Les exemples suivants illustrent ce principe :</span><span class="sxs-lookup"><span data-stu-id="8805a-213">The following examples demonstrate this principle:</span></span>

|<span data-ttu-id="8805a-214">Expression</span><span class="sxs-lookup"><span data-stu-id="8805a-214">Expression</span></span>   |<span data-ttu-id="8805a-215">Résultats</span><span class="sxs-lookup"><span data-stu-id="8805a-215">Result</span></span>                                               |
|-------------|-----------------------------------------------------|
|`"file" + 16`|`file16`                                             |
|`16 + "file"`|`Cannot convert value "file" to type "System.Int32".`|
|             |`Error: "Input string was not in a correct format."` |
|             |`At line:1 char:1`                                   |
|             |<span data-ttu-id="8805a-216">+ 16 + "fichier" '</span><span class="sxs-lookup"><span data-stu-id="8805a-216">+ 16 + "file"\`</span></span>                                       |

<span data-ttu-id="8805a-217">Les tables de hachage sont un cas légèrement différent.</span><span class="sxs-lookup"><span data-stu-id="8805a-217">Hash tables are a slightly different case.</span></span> <span data-ttu-id="8805a-218">Vous pouvez ajouter des tables de hachage à une autre table de hachage, à condition que les tables de hachage ajoutées n’aient pas de clés dupliquées.</span><span class="sxs-lookup"><span data-stu-id="8805a-218">You can add hash tables to another hash table, as long as, the added hash tables don't have duplicate keys.</span></span>

<span data-ttu-id="8805a-219">L’exemple suivant montre comment ajouter des tables de hachage les unes aux autres.</span><span class="sxs-lookup"><span data-stu-id="8805a-219">The following example show how to add hash tables to each other.</span></span>

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c2="Server02"}
$hash1 + $hash2
```

```output
Name                           Value
----                           -----
c2                             Server02
a                              1
b                              2
c1                             Server01
c                              3
```

<span data-ttu-id="8805a-220">L’exemple suivant génère une erreur, car l’une des clés est dupliquée dans les deux tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="8805a-220">The following example throws an error because one of the keys is duplicated in both hash tables.</span></span>

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c="Server02"}
$hash1 + $hash2
```

```output
Item has already been added. Key in dictionary: 'c'  Key being added: 'c'
At line:3 char:1
+ $hash1 + $hash2
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], ArgumentException
    + FullyQualifiedErrorId : System.ArgumentException
```

<span data-ttu-id="8805a-221">En outre, vous pouvez ajouter une table de hachage à un tableau. et, l’ensemble de la table de hachage devient un élément dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="8805a-221">Also, you can add a hash table to an array; and, the entire hash table becomes an item in the array.</span></span>

```powershell
$array1 = @(0, "Hello World", [datetime]::Now)
$hash1 = @{a=1; b=2}
$array2 = $array1 + $hash1
$array2
```

```output
0
Hello World

Monday, June 12, 2017 3:05:46 PM

Key   : a
Value : 1
Name  : a

Key   : b
Value : 2
Name  : b
```

<span data-ttu-id="8805a-222">Toutefois, vous ne pouvez pas ajouter d’autres types à une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="8805a-222">However, you cannot add any other type to a hash table.</span></span>

```powershell
$hash1 + 2
```

```output
A hash table can only be added to another hash table.
At line:3 char:1
+ $hash1 + 2
```

<span data-ttu-id="8805a-223">Bien que les opérateurs d’addition soient très utiles, utilisez les opérateurs d’assignation pour ajouter des éléments aux tableaux de hachage et aux tableaux.</span><span class="sxs-lookup"><span data-stu-id="8805a-223">Although the addition operators are very useful, use the assignment operators to add elements to hash tables and arrays.</span></span> <span data-ttu-id="8805a-224">Pour plus d’informations, consultez [about_Assignment_Operators](about_Assignment_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="8805a-224">For more information see [about_assignment_operators](about_Assignment_Operators.md).</span></span> <span data-ttu-id="8805a-225">Les exemples suivants utilisent l' `+=` opérateur d’assignation pour ajouter des éléments à un tableau :</span><span class="sxs-lookup"><span data-stu-id="8805a-225">The following examples use the `+=` assignment operator to add items to an array:</span></span>

```powershell
$array = @()
(0..9).foreach{ $array += $_ }
$array
```

```output
0
1
2
```

## <a name="type-conversion-to-accommodate-result"></a><span data-ttu-id="8805a-226">CONVERSION DE TYPE EN FONCTION DU RÉSULTAT</span><span class="sxs-lookup"><span data-stu-id="8805a-226">TYPE CONVERSION TO ACCOMMODATE RESULT</span></span>

<span data-ttu-id="8805a-227">PowerShell sélectionne automatiquement le type de .NET Framework numérique qui exprime le mieux le résultat sans perte de précision.</span><span class="sxs-lookup"><span data-stu-id="8805a-227">PowerShell automatically selects the .NET Framework numeric type that best expresses the result without losing precision.</span></span> <span data-ttu-id="8805a-228">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8805a-228">For example:</span></span>

```powershell
2 + 3.1

(2). GetType().FullName
(2 + 3.1).GetType().FullName
```

```output
5.1
System.Int32
System.Double
```

<span data-ttu-id="8805a-229">Si le résultat d’une opération est trop grand pour le type, le type du résultat est élargi pour s’adapter au résultat, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8805a-229">If the result of an operation is too large for the type, the type of the result is widened to accommodate the result, as in the following example:</span></span>

```powershell
(512MB).GetType().FullName
(512MB * 512MB).GetType().FullName
```

```output
System.Int32
System.Double
```

<span data-ttu-id="8805a-230">Le type du résultat n’est pas nécessairement le même que l’un des opérandes.</span><span class="sxs-lookup"><span data-stu-id="8805a-230">The type of the result will not necessarily be the same as one of the operands.</span></span> <span data-ttu-id="8805a-231">Dans l’exemple suivant, la valeur négative ne peut pas être convertie en entier non signé et l’entier non signé est trop grand pour être converti en `Int32` :</span><span class="sxs-lookup"><span data-stu-id="8805a-231">In the following example, the negative value cannot be cast to an unsigned integer, and the unsigned integer is too large to be cast to `Int32`:</span></span>

```powershell
([int32]::minvalue + [uint32]::maxvalue).gettype().fullname
```

```output
System.Int64
```

<span data-ttu-id="8805a-232">Dans cet exemple, `Int64` peut prendre en charge les deux types.</span><span class="sxs-lookup"><span data-stu-id="8805a-232">In this example, `Int64` can accommodate both types.</span></span>

<span data-ttu-id="8805a-233">Le `System.Decimal` type est une exception.</span><span class="sxs-lookup"><span data-stu-id="8805a-233">The `System.Decimal` type is an exception.</span></span> <span data-ttu-id="8805a-234">Si l’un des opérandes a le type décimal, le résultat sera du type décimal.</span><span class="sxs-lookup"><span data-stu-id="8805a-234">If either operand has the Decimal type, the result will be of the Decimal type.</span></span> <span data-ttu-id="8805a-235">Si le résultat est trop grand pour le type décimal, il n’est pas converti en double.</span><span class="sxs-lookup"><span data-stu-id="8805a-235">If the result is too large for the Decimal type, it will not be cast to Double.</span></span> <span data-ttu-id="8805a-236">Au lieu de cela, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="8805a-236">Instead, an error results.</span></span>

|<span data-ttu-id="8805a-237">Expression</span><span class="sxs-lookup"><span data-stu-id="8805a-237">Expression</span></span>               |<span data-ttu-id="8805a-238">Résultats</span><span class="sxs-lookup"><span data-stu-id="8805a-238">Result</span></span>                                         |
|-------------------------|-----------------------------------------------|
|`[Decimal]::maxvalue`    |`79228162514264337593543950335`                |
|`[Decimal]::maxvalue + 1`|`Value was either too large or too small for a`|
|                         |`Decimal.`                                     |

## <a name="arithmetic-operators-and-variables"></a><span data-ttu-id="8805a-239">OPÉRATEURS ARITHMÉTIQUES ET VARIABLES</span><span class="sxs-lookup"><span data-stu-id="8805a-239">ARITHMETIC OPERATORS AND VARIABLES</span></span>

<span data-ttu-id="8805a-240">Vous pouvez également utiliser des opérateurs arithmétiques avec des variables.</span><span class="sxs-lookup"><span data-stu-id="8805a-240">You can also use arithmetic operators with variables.</span></span> <span data-ttu-id="8805a-241">Les opérateurs agissent sur les valeurs des variables.</span><span class="sxs-lookup"><span data-stu-id="8805a-241">The operators act on the values of the variables.</span></span> <span data-ttu-id="8805a-242">Les exemples suivants illustrent l’utilisation d’opérateurs arithmétiques avec des variables :</span><span class="sxs-lookup"><span data-stu-id="8805a-242">The following examples demonstrate the use of arithmetic operators with variables:</span></span>

| <span data-ttu-id="8805a-243">Expression</span><span class="sxs-lookup"><span data-stu-id="8805a-243">Expression</span></span>                                    |<span data-ttu-id="8805a-244">Résultats</span><span class="sxs-lookup"><span data-stu-id="8805a-244">Result</span></span>      |
|-----------------------------------------------|------------|
|`$intA = 6`<br/>`$intB = 4`<br/>`$intA + $intB`|`10`        |
|`$a = "Power"`<br/>`$b = "Shell"`<br/>`$a + $b`|`PowerShell`|

## <a name="arithmetic-operators-and-commands"></a><span data-ttu-id="8805a-245">OPÉRATEURS ARITHMÉTIQUES ET COMMANDES</span><span class="sxs-lookup"><span data-stu-id="8805a-245">ARITHMETIC OPERATORS AND COMMANDS</span></span>

<span data-ttu-id="8805a-246">En général, vous utilisez les opérateurs arithmétiques dans les expressions avec des nombres, des chaînes et des tableaux.</span><span class="sxs-lookup"><span data-stu-id="8805a-246">Typically, you use the arithmetic operators in expressions with numbers, strings, and arrays.</span></span> <span data-ttu-id="8805a-247">Toutefois, vous pouvez également utiliser des opérateurs arithmétiques avec les objets retournés par les commandes et avec les propriétés de ces objets.</span><span class="sxs-lookup"><span data-stu-id="8805a-247">However, you can also use arithmetic operators with the objects that commands return and with the properties of those objects.</span></span>

<span data-ttu-id="8805a-248">Les exemples suivants montrent comment utiliser les opérateurs arithmétiques dans les expressions avec des commandes PowerShell :</span><span class="sxs-lookup"><span data-stu-id="8805a-248">The following examples show how to use the arithmetic operators in expressions with PowerShell commands:</span></span>

```powershell
(get-date) + (new-timespan -day 1)
```

<span data-ttu-id="8805a-249">L’opérateur parenthèse force l’évaluation de l' `get-date` applet de commande et l’évaluation de l’expression de l' `new-timespan -day 1` applet de commande, dans cet ordre.</span><span class="sxs-lookup"><span data-stu-id="8805a-249">The parenthesis operator forces the evaluation of the `get-date` cmdlet and the evaluation of the `new-timespan -day 1` cmdlet expression, in that order.</span></span> <span data-ttu-id="8805a-250">Les deux résultats sont ensuite ajoutés à l’aide de l' `+` opérateur.</span><span class="sxs-lookup"><span data-stu-id="8805a-250">Both results are then added using the `+` operator.</span></span>

```powershell
Get-Process | Where-Object { ($_.ws * 2) -gt 50mb }
```

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1896      39    50968      30620   264 1,572.55   1104 explorer
  12802      78   188468      81032   753 3,676.39   5676 OUTLOOK
    660       9    36168      26956   143    12.20    988 PowerShell
    561      14     6592      28144   110 1,010.09    496 services
   3476      80    34664      26092   234 ...45.69    876 svchost
    967      30    58804      59496   416   930.97   2508 WINWORD
```

<span data-ttu-id="8805a-251">Dans l’expression ci-dessus, chaque espace de travail de processus ( `$_.ws` ) est multiplié par `2` ; et, le résultat, comparé `50mb` pour voir s’il est supérieur à.</span><span class="sxs-lookup"><span data-stu-id="8805a-251">In the above expression, each process working space (`$_.ws`) is multiplied by `2`; and, the result, compared against `50mb` to see if it is greater than that.</span></span>

## <a name="bitwise-operators"></a><span data-ttu-id="8805a-252">Opérateurs au niveau du bit</span><span class="sxs-lookup"><span data-stu-id="8805a-252">Bitwise Operators</span></span>

<span data-ttu-id="8805a-253">PowerShell prend en charge les opérateurs de bits standard, y compris les opérateurs de bits and ( `-bAnd` ), les opérateurs or inclusifs et exclusifs ( `-bOr` and `-bXor` ) et not au niveau du bit ( `-bNot` ).</span><span class="sxs-lookup"><span data-stu-id="8805a-253">PowerShell supports the standard bitwise operators, including bitwise-AND (`-bAnd`), the inclusive and exclusive bitwise-OR operators (`-bOr` and `-bXor`), and bitwise-NOT (`-bNot`).</span></span>

<span data-ttu-id="8805a-254">À compter de PowerShell 2,0, tous les opérateurs au niveau du bit fonctionnent avec des entiers 64 bits.</span><span class="sxs-lookup"><span data-stu-id="8805a-254">Beginning in PowerShell 2.0, all bitwise operators work with 64-bit integers.</span></span>

<span data-ttu-id="8805a-255">À compter de PowerShell 3,0, le `-shr` (Shift-Right) et `-shl` (Shift-Left) sont introduits pour prendre en charge l’arithmétique au niveau du bit dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8805a-255">Beginning in PowerShell 3.0, the `-shr` (shift-right) and `-shl` (shift-left) are introduced to support bitwise arithmetic in PowerShell.</span></span>

<span data-ttu-id="8805a-256">PowerShell prend en charge les opérateurs de bits suivants.</span><span class="sxs-lookup"><span data-stu-id="8805a-256">PowerShell supports the following bitwise operators.</span></span>

| <span data-ttu-id="8805a-257">Opérateur</span><span class="sxs-lookup"><span data-stu-id="8805a-257">Operator</span></span> | <span data-ttu-id="8805a-258">Description</span><span class="sxs-lookup"><span data-stu-id="8805a-258">Description</span></span>            | <span data-ttu-id="8805a-259">Expression</span><span class="sxs-lookup"><span data-stu-id="8805a-259">Expression</span></span>   | <span data-ttu-id="8805a-260">Résultats</span><span class="sxs-lookup"><span data-stu-id="8805a-260">Result</span></span> |
| -------- | ---------------------- | ------------ | ------ |
| `-band`  | <span data-ttu-id="8805a-261">ET au niveau du bit</span><span class="sxs-lookup"><span data-stu-id="8805a-261">Bitwise AND</span></span>            | `10 -band 3` | <span data-ttu-id="8805a-262">2</span><span class="sxs-lookup"><span data-stu-id="8805a-262">2</span></span>      |
| `-bor`   | <span data-ttu-id="8805a-263">Or au niveau du bit (inclusive)</span><span class="sxs-lookup"><span data-stu-id="8805a-263">Bitwise OR (inclusive)</span></span> | `10 -bor 3`  | <span data-ttu-id="8805a-264">11</span><span class="sxs-lookup"><span data-stu-id="8805a-264">11</span></span>     |
| `-bxor`  | <span data-ttu-id="8805a-265">Or au niveau du bit (exclusif)</span><span class="sxs-lookup"><span data-stu-id="8805a-265">Bitwise OR (exclusive)</span></span> | `10 -bxor 3` | <span data-ttu-id="8805a-266">9</span><span class="sxs-lookup"><span data-stu-id="8805a-266">9</span></span>      |
| `-bnot`  | <span data-ttu-id="8805a-267">NOT au niveau du bit</span><span class="sxs-lookup"><span data-stu-id="8805a-267">Bitwise NOT</span></span>            | `-bNot 10`   | <span data-ttu-id="8805a-268">-11</span><span class="sxs-lookup"><span data-stu-id="8805a-268">-11</span></span>    |
| `-shl`   | <span data-ttu-id="8805a-269">Décalage vers la gauche</span><span class="sxs-lookup"><span data-stu-id="8805a-269">Shift-left</span></span>             | `102 -shl 2` | <span data-ttu-id="8805a-270">408</span><span class="sxs-lookup"><span data-stu-id="8805a-270">408</span></span>    |
| `-shr`   | <span data-ttu-id="8805a-271">Décalage vers la droite</span><span class="sxs-lookup"><span data-stu-id="8805a-271">Shift-right</span></span>            | `102 -shr 1` | <span data-ttu-id="8805a-272">51</span><span class="sxs-lookup"><span data-stu-id="8805a-272">51</span></span>     |

<span data-ttu-id="8805a-273">Les opérateurs au niveau du bit agissent sur le format binaire d’une valeur.</span><span class="sxs-lookup"><span data-stu-id="8805a-273">Bitwise operators act on the binary format of a value.</span></span> <span data-ttu-id="8805a-274">Par exemple, la structure de bits pour le nombre 10 est 00001010 (sur la base de 1 octet) et la structure de bits pour le nombre 3 est 00000011.</span><span class="sxs-lookup"><span data-stu-id="8805a-274">For example, the bit structure for the number 10 is 00001010 (based on 1 byte), and the bit structure for the number 3 is 00000011.</span></span> <span data-ttu-id="8805a-275">Lorsque vous utilisez un opérateur au niveau du bit pour comparer 10 à 3, les bits individuels de chaque octet sont comparés.</span><span class="sxs-lookup"><span data-stu-id="8805a-275">When you use a bitwise operator to compare 10 to 3, the individual bits in each byte are compared.</span></span>

<span data-ttu-id="8805a-276">Dans une opération AND au niveau du bit, le bit résultant est défini sur 1 uniquement lorsque les deux bits d’entrée ont la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="8805a-276">In a bitwise AND operation, the resulting bit is set to 1 only when both input bits are 1.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bAND
0010      ( 2)
```

<span data-ttu-id="8805a-277">Dans une opération or au niveau du bit (inclusive), le bit résultant est défini sur 1 lorsque l’un des bits d’entrée ou les deux sont 1.</span><span class="sxs-lookup"><span data-stu-id="8805a-277">In a bitwise OR (inclusive) operation, the resulting bit is set to 1 when either or both input bits are 1.</span></span> <span data-ttu-id="8805a-278">Le bit résultant est défini sur 0 uniquement lorsque les deux bits d’entrée ont la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="8805a-278">The resulting bit is set to 0 only when both input bits are set to 0.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bOR (inclusive)
1011      (11)
```

<span data-ttu-id="8805a-279">Dans une opération de bits or (exclusive), le bit résultant est défini sur 1 uniquement lorsqu’un bit d’entrée est 1.</span><span class="sxs-lookup"><span data-stu-id="8805a-279">In a bitwise OR (exclusive) operation, the resulting bit is set to 1 only when one input bit is 1.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bXOR (exclusive)
1001      ( 9)
```

<span data-ttu-id="8805a-280">L’opérateur de bits NOT est un opérateur unaire qui produit le complément binaire de la valeur.</span><span class="sxs-lookup"><span data-stu-id="8805a-280">The bitwise NOT operator is a unary operator that produces the binary complement of the value.</span></span> <span data-ttu-id="8805a-281">Un bit de 1 est défini sur 0 et un bit de 0 est défini sur 1.</span><span class="sxs-lookup"><span data-stu-id="8805a-281">A bit of 1 is set to 0 and a bit of 0 is set to 1.</span></span>

<span data-ttu-id="8805a-282">Par exemple, le complément binaire de 0 est égal à-1, l’entier non signé maximal (0xFFFFFFFF) et le complément binaire-1 à 0.</span><span class="sxs-lookup"><span data-stu-id="8805a-282">For example, the binary complement of 0 is -1, the maximum unsigned integer (0xffffffff), and the binary complement of -1 is 0.</span></span>

```powershell
-bNot 10
```

```Output
-11
```

```
0000 0000 0000 1010  (10)
------------------------- bNOT
1111 1111 1111 0101  (-11, xfffffff5)
```

<span data-ttu-id="8805a-283">Dans une opération de décalage vers la gauche au niveau du bit, tous les bits sont déplacés vers la gauche, où « n » est la valeur de l’opérande de droite.</span><span class="sxs-lookup"><span data-stu-id="8805a-283">In a bitwise shift-left operation, all bits are moved "n" places to the left, where "n" is the value of the right operand.</span></span> <span data-ttu-id="8805a-284">Un zéro est inséré à l’endroit.</span><span class="sxs-lookup"><span data-stu-id="8805a-284">A zero is inserted in the ones place.</span></span>

<span data-ttu-id="8805a-285">Lorsque l’opérande gauche est une valeur entière (32 bits), les 5 bits inférieurs de l’opérande droit déterminent le nombre de bits de l’opérande gauche qui sont décalés.</span><span class="sxs-lookup"><span data-stu-id="8805a-285">When the left operand is an Integer (32-bit) value, the lower 5 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

<span data-ttu-id="8805a-286">Lorsque l’opérande gauche est une valeur longue (64 bits), les 6 bits inférieurs de l’opérande droit déterminent le nombre de bits de l’opérande gauche qui sont décalés.</span><span class="sxs-lookup"><span data-stu-id="8805a-286">When the left operand is a Long (64-bit) value, the lower 6 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

|<span data-ttu-id="8805a-287">Expression</span><span class="sxs-lookup"><span data-stu-id="8805a-287">Expression</span></span> |<span data-ttu-id="8805a-288">Résultats</span><span class="sxs-lookup"><span data-stu-id="8805a-288">Result</span></span>|<span data-ttu-id="8805a-289">Résultat binaire</span><span class="sxs-lookup"><span data-stu-id="8805a-289">Binary Result</span></span>|
|-----------|------|-------------|
|`21 -shl 0`|<span data-ttu-id="8805a-290">21</span><span class="sxs-lookup"><span data-stu-id="8805a-290">21</span></span>    |<span data-ttu-id="8805a-291">0001 0101</span><span class="sxs-lookup"><span data-stu-id="8805a-291">0001 0101</span></span>    |
|`21 -shl 1`|<span data-ttu-id="8805a-292">42</span><span class="sxs-lookup"><span data-stu-id="8805a-292">42</span></span>    |<span data-ttu-id="8805a-293">0010 1010</span><span class="sxs-lookup"><span data-stu-id="8805a-293">0010 1010</span></span>    |
|`21 -shl 2`|<span data-ttu-id="8805a-294">84</span><span class="sxs-lookup"><span data-stu-id="8805a-294">84</span></span>    |<span data-ttu-id="8805a-295">0101 0100</span><span class="sxs-lookup"><span data-stu-id="8805a-295">0101 0100</span></span>    |

<span data-ttu-id="8805a-296">Dans une opération de décalage vers la droite au niveau du bit, tous les bits sont déplacés vers la droite, où « n » est spécifié par l’opérande de droite.</span><span class="sxs-lookup"><span data-stu-id="8805a-296">In a bitwise shift-right operation, all bits are moved "n" places to the right, where "n" is specified by the right operand.</span></span> <span data-ttu-id="8805a-297">L’opérateur Shift-Right (-SHR) insère un zéro à l’emplacement le plus à gauche lors du décalage d’une valeur positive ou non signée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="8805a-297">The shift-right operator (-shr) inserts a zero in the left-most place when shifting a positive or unsigned value to the right.</span></span>

<span data-ttu-id="8805a-298">Lorsque l’opérande gauche est une valeur entière (32 bits), les 5 bits inférieurs de l’opérande droit déterminent le nombre de bits de l’opérande gauche qui sont décalés.</span><span class="sxs-lookup"><span data-stu-id="8805a-298">When the left operand is an Integer (32-bit) value, the lower 5 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

<span data-ttu-id="8805a-299">Lorsque l’opérande gauche est une valeur longue (64 bits), les 6 bits inférieurs de l’opérande droit déterminent le nombre de bits de l’opérande gauche qui sont décalés.</span><span class="sxs-lookup"><span data-stu-id="8805a-299">When the left operand is a Long (64-bit) value, the lower 6 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

|<span data-ttu-id="8805a-300">Expression</span><span class="sxs-lookup"><span data-stu-id="8805a-300">Expression</span></span>              |<span data-ttu-id="8805a-301">Résultats</span><span class="sxs-lookup"><span data-stu-id="8805a-301">Result</span></span>      |<span data-ttu-id="8805a-302">Binary</span><span class="sxs-lookup"><span data-stu-id="8805a-302">Binary</span></span>     |<span data-ttu-id="8805a-303">Hex</span><span class="sxs-lookup"><span data-stu-id="8805a-303">Hex</span></span>         |
|------------------------|------------|-----------|------------|
|`21 -shr 0`             | <span data-ttu-id="8805a-304">21</span><span class="sxs-lookup"><span data-stu-id="8805a-304">21</span></span>         | <span data-ttu-id="8805a-305">0001 0101</span><span class="sxs-lookup"><span data-stu-id="8805a-305">0001 0101</span></span> | <span data-ttu-id="8805a-306">0x15</span><span class="sxs-lookup"><span data-stu-id="8805a-306">0x15</span></span>       |
|`21 -shr 1`             | <span data-ttu-id="8805a-307">10</span><span class="sxs-lookup"><span data-stu-id="8805a-307">10</span></span>         | <span data-ttu-id="8805a-308">0000 1010</span><span class="sxs-lookup"><span data-stu-id="8805a-308">0000 1010</span></span> | <span data-ttu-id="8805a-309">0x0A</span><span class="sxs-lookup"><span data-stu-id="8805a-309">0x0A</span></span>       |
|`21 -shr 2`             | <span data-ttu-id="8805a-310">5</span><span class="sxs-lookup"><span data-stu-id="8805a-310">5</span></span>          | <span data-ttu-id="8805a-311">0000 0101</span><span class="sxs-lookup"><span data-stu-id="8805a-311">0000 0101</span></span> | <span data-ttu-id="8805a-312">0x05</span><span class="sxs-lookup"><span data-stu-id="8805a-312">0x05</span></span>       |
|`21 -shr 31`            | <span data-ttu-id="8805a-313">0</span><span class="sxs-lookup"><span data-stu-id="8805a-313">0</span></span>          | <span data-ttu-id="8805a-314">0000 0000</span><span class="sxs-lookup"><span data-stu-id="8805a-314">0000 0000</span></span> | <span data-ttu-id="8805a-315">0x00</span><span class="sxs-lookup"><span data-stu-id="8805a-315">0x00</span></span>       |
|`21 -shr 32`            | <span data-ttu-id="8805a-316">21</span><span class="sxs-lookup"><span data-stu-id="8805a-316">21</span></span>         | <span data-ttu-id="8805a-317">0001 0101</span><span class="sxs-lookup"><span data-stu-id="8805a-317">0001 0101</span></span> | <span data-ttu-id="8805a-318">0x15</span><span class="sxs-lookup"><span data-stu-id="8805a-318">0x15</span></span>       |
|`21 -shr 64`            | <span data-ttu-id="8805a-319">21</span><span class="sxs-lookup"><span data-stu-id="8805a-319">21</span></span>         | <span data-ttu-id="8805a-320">0001 0101</span><span class="sxs-lookup"><span data-stu-id="8805a-320">0001 0101</span></span> | <span data-ttu-id="8805a-321">0x15</span><span class="sxs-lookup"><span data-stu-id="8805a-321">0x15</span></span>       |
|`21 -shr 65`            | <span data-ttu-id="8805a-322">10</span><span class="sxs-lookup"><span data-stu-id="8805a-322">10</span></span>         | <span data-ttu-id="8805a-323">0000 1010</span><span class="sxs-lookup"><span data-stu-id="8805a-323">0000 1010</span></span> | <span data-ttu-id="8805a-324">0x0A</span><span class="sxs-lookup"><span data-stu-id="8805a-324">0x0A</span></span>       |
|`21 -shr 66`            | <span data-ttu-id="8805a-325">5</span><span class="sxs-lookup"><span data-stu-id="8805a-325">5</span></span>          | <span data-ttu-id="8805a-326">0000 0101</span><span class="sxs-lookup"><span data-stu-id="8805a-326">0000 0101</span></span> | <span data-ttu-id="8805a-327">0x05</span><span class="sxs-lookup"><span data-stu-id="8805a-327">0x05</span></span>       |
|`[int]::MaxValue -shr 1`| <span data-ttu-id="8805a-328">1073741823</span><span class="sxs-lookup"><span data-stu-id="8805a-328">1073741823</span></span> |           | <span data-ttu-id="8805a-329">0x3FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="8805a-329">0x3FFFFFFF</span></span> |
|`[int]::MinValue -shr 1`| <span data-ttu-id="8805a-330">-1073741824</span><span class="sxs-lookup"><span data-stu-id="8805a-330">-1073741824</span></span>|           | <span data-ttu-id="8805a-331">0xC0000000</span><span class="sxs-lookup"><span data-stu-id="8805a-331">0xC0000000</span></span> |
|`-1 -shr 1`             | <span data-ttu-id="8805a-332">-1</span><span class="sxs-lookup"><span data-stu-id="8805a-332">-1</span></span>         |           | <span data-ttu-id="8805a-333">Égale</span><span class="sxs-lookup"><span data-stu-id="8805a-333">0xFFFFFFFF</span></span> |

## <a name="see-also"></a><span data-ttu-id="8805a-334">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="8805a-334">SEE ALSO</span></span>

- [<span data-ttu-id="8805a-335">about_arrays</span><span class="sxs-lookup"><span data-stu-id="8805a-335">about_arrays</span></span>](about_Arrays.md)
- [<span data-ttu-id="8805a-336">about_assignment_operators</span><span class="sxs-lookup"><span data-stu-id="8805a-336">about_assignment_operators</span></span>](about_Assignment_Operators.md)
- [<span data-ttu-id="8805a-337">about_comparison_operators</span><span class="sxs-lookup"><span data-stu-id="8805a-337">about_comparison_operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="8805a-338">about_hash_tables</span><span class="sxs-lookup"><span data-stu-id="8805a-338">about_hash_tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="8805a-339">about_operators</span><span class="sxs-lookup"><span data-stu-id="8805a-339">about_operators</span></span>](about_Operators.md)
- [<span data-ttu-id="8805a-340">about_variables</span><span class="sxs-lookup"><span data-stu-id="8805a-340">about_variables</span></span>](about_Variables.md)
- [<span data-ttu-id="8805a-341">Obtient la date</span><span class="sxs-lookup"><span data-stu-id="8805a-341">Get-Date</span></span>](xref:Microsoft.PowerShell.Utility.Get-Date)
- [<span data-ttu-id="8805a-342">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="8805a-342">New-TimeSpan</span></span>](xref:Microsoft.PowerShell.Utility.New-TimeSpan)