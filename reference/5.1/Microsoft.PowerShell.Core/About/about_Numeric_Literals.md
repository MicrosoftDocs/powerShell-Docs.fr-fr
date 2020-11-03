---
description: Les littéraux numériques et réels peuvent avoir des suffixes de type et de multiplicateur.
Locale: en-US
ms.date: 04/09/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos des littéraux numériques
ms.openlocfilehash: 99fa8c1a751551d028fe6df0b0cec94e07f19c59
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208766"
---
# <a name="about-numeric-literals"></a><span data-ttu-id="c4d68-103">À propos des littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="c4d68-103">About numeric literals</span></span>

<span data-ttu-id="c4d68-104">Il existe deux types de littéraux numériques : entier et réel.</span><span class="sxs-lookup"><span data-stu-id="c4d68-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="c4d68-105">Les deux peuvent avoir des suffixes de type et multiplicateur.</span><span class="sxs-lookup"><span data-stu-id="c4d68-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="c4d68-106">Littéraux d'entier</span><span class="sxs-lookup"><span data-stu-id="c4d68-106">Integer literals</span></span>

<span data-ttu-id="c4d68-107">Les littéraux entiers peuvent être écrits en notation décimale ou hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="c4d68-107">Integer literals can be written in decimal or hexadecimal notation.</span></span> <span data-ttu-id="c4d68-108">Les littéraux hexadécimaux sont précédés de `0x` pour les distinguer des nombres décimaux.</span><span class="sxs-lookup"><span data-stu-id="c4d68-108">Hexadecimal literals are prefixed with `0x` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="c4d68-109">Les littéraux entiers peuvent avoir un suffixe de type et un suffixe multiplicateur.</span><span class="sxs-lookup"><span data-stu-id="c4d68-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="c4d68-110">Suffixe</span><span class="sxs-lookup"><span data-stu-id="c4d68-110">Suffix</span></span> |       <span data-ttu-id="c4d68-111">Signification</span><span class="sxs-lookup"><span data-stu-id="c4d68-111">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="c4d68-112">l</span><span class="sxs-lookup"><span data-stu-id="c4d68-112">l</span></span>      | <span data-ttu-id="c4d68-113">long (type de données)</span><span class="sxs-lookup"><span data-stu-id="c4d68-113">long data type</span></span>      |
| <span data-ttu-id="c4d68-114">kb</span><span class="sxs-lookup"><span data-stu-id="c4d68-114">kb</span></span>     | <span data-ttu-id="c4d68-115">multiplicateur de kilo-octets</span><span class="sxs-lookup"><span data-stu-id="c4d68-115">kilobyte multiplier</span></span> |
| <span data-ttu-id="c4d68-116">mb</span><span class="sxs-lookup"><span data-stu-id="c4d68-116">mb</span></span>     | <span data-ttu-id="c4d68-117">multiplicateur de mégaoctets</span><span class="sxs-lookup"><span data-stu-id="c4d68-117">megabyte multiplier</span></span> |
| <span data-ttu-id="c4d68-118">moins</span><span class="sxs-lookup"><span data-stu-id="c4d68-118">gb</span></span>     | <span data-ttu-id="c4d68-119">multiplicateur de gigaoctets</span><span class="sxs-lookup"><span data-stu-id="c4d68-119">gigabyte multiplier</span></span> |
| <span data-ttu-id="c4d68-120">to</span><span class="sxs-lookup"><span data-stu-id="c4d68-120">tb</span></span>     | <span data-ttu-id="c4d68-121">multiplicateur de téraoctets</span><span class="sxs-lookup"><span data-stu-id="c4d68-121">terabyte multiplier</span></span> |
| <span data-ttu-id="c4d68-122">gérés</span><span class="sxs-lookup"><span data-stu-id="c4d68-122">pb</span></span>     | <span data-ttu-id="c4d68-123">multiplicateur de pétaoctet</span><span class="sxs-lookup"><span data-stu-id="c4d68-123">petabyte multiplier</span></span> |

<span data-ttu-id="c4d68-124">Le type d’un littéral entier est déterminé par sa valeur, le suffixe de type et le suffixe multiplicateur numérique.</span><span class="sxs-lookup"><span data-stu-id="c4d68-124">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="c4d68-125">Pour un littéral d’entier sans suffixe de type :</span><span class="sxs-lookup"><span data-stu-id="c4d68-125">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="c4d68-126">Si la valeur peut être représentée par le type `[int]` , il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="c4d68-126">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="c4d68-127">Sinon, si la valeur peut être représentée par le type `[long]` , il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="c4d68-127">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="c4d68-128">Sinon, si la valeur peut être représentée par le type `[decimal]` , il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="c4d68-128">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="c4d68-129">Dans le cas contraire, il est représenté par le type `[double]` .</span><span class="sxs-lookup"><span data-stu-id="c4d68-129">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="c4d68-130">Pour un littéral d’entier avec un suffixe de type :</span><span class="sxs-lookup"><span data-stu-id="c4d68-130">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="c4d68-131">Si le suffixe de type est `u` et que la valeur peut être représentée par le type, `[int]` son type est `[int]` .</span><span class="sxs-lookup"><span data-stu-id="c4d68-131">If the type suffix is `u` and the value can be represented by type `[int]` then its type is `[int]`.</span></span>
- <span data-ttu-id="c4d68-132">Si le suffixe de type est `u` et que la valeur peut être représentée par le type, `[long]` son type est `[long]` .</span><span class="sxs-lookup"><span data-stu-id="c4d68-132">If the type suffix is `u` and the value can be represented by type `[long]` then its type is `[long]`.</span></span>
- <span data-ttu-id="c4d68-133">Si sa valeur peut être représentée par le type spécifié, alors il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="c4d68-133">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="c4d68-134">Dans le cas contraire, ce littéral est incorrect.</span><span class="sxs-lookup"><span data-stu-id="c4d68-134">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="c4d68-135">Littéraux réels</span><span class="sxs-lookup"><span data-stu-id="c4d68-135">Real literals</span></span>

<span data-ttu-id="c4d68-136">Les littéraux réels ne peuvent être écrits qu’en notation décimale.</span><span class="sxs-lookup"><span data-stu-id="c4d68-136">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="c4d68-137">Cette notation peut inclure des valeurs fractionnaires à la suite d’une virgule décimale et d’une notation scientifique à l’aide d’une partie exponentielle.</span><span class="sxs-lookup"><span data-stu-id="c4d68-137">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="c4d68-138">La partie exponentielle comprend un « e » suivi d’un signe facultatif (+/-) et d’un nombre représentant l’exposant.</span><span class="sxs-lookup"><span data-stu-id="c4d68-138">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="c4d68-139">Par exemple, la valeur littérale `1e2` est égale à la valeur numérique 100.</span><span class="sxs-lookup"><span data-stu-id="c4d68-139">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="c4d68-140">Les littéraux réels peuvent avoir un suffixe de type et un suffixe multiplicateur.</span><span class="sxs-lookup"><span data-stu-id="c4d68-140">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="c4d68-141">Suffixe</span><span class="sxs-lookup"><span data-stu-id="c4d68-141">Suffix</span></span> |       <span data-ttu-id="c4d68-142">Signification</span><span class="sxs-lookup"><span data-stu-id="c4d68-142">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="c4d68-143">d</span><span class="sxs-lookup"><span data-stu-id="c4d68-143">d</span></span>      | <span data-ttu-id="c4d68-144">type de données decimal</span><span class="sxs-lookup"><span data-stu-id="c4d68-144">decimal data type</span></span>   |
| <span data-ttu-id="c4d68-145">kb</span><span class="sxs-lookup"><span data-stu-id="c4d68-145">kb</span></span>     | <span data-ttu-id="c4d68-146">multiplicateur de kilo-octets</span><span class="sxs-lookup"><span data-stu-id="c4d68-146">kilobyte multiplier</span></span> |
| <span data-ttu-id="c4d68-147">mb</span><span class="sxs-lookup"><span data-stu-id="c4d68-147">mb</span></span>     | <span data-ttu-id="c4d68-148">multiplicateur de mégaoctets</span><span class="sxs-lookup"><span data-stu-id="c4d68-148">megabyte multiplier</span></span> |
| <span data-ttu-id="c4d68-149">moins</span><span class="sxs-lookup"><span data-stu-id="c4d68-149">gb</span></span>     | <span data-ttu-id="c4d68-150">multiplicateur de gigaoctets</span><span class="sxs-lookup"><span data-stu-id="c4d68-150">gigabyte multiplier</span></span> |
| <span data-ttu-id="c4d68-151">to</span><span class="sxs-lookup"><span data-stu-id="c4d68-151">tb</span></span>     | <span data-ttu-id="c4d68-152">multiplicateur de téraoctets</span><span class="sxs-lookup"><span data-stu-id="c4d68-152">terabyte multiplier</span></span> |
| <span data-ttu-id="c4d68-153">gérés</span><span class="sxs-lookup"><span data-stu-id="c4d68-153">pb</span></span>     | <span data-ttu-id="c4d68-154">multiplicateur de pétaoctet</span><span class="sxs-lookup"><span data-stu-id="c4d68-154">petabyte multiplier</span></span> |

<span data-ttu-id="c4d68-155">Il existe deux types de littéraux réels : double et Decimal.</span><span class="sxs-lookup"><span data-stu-id="c4d68-155">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="c4d68-156">Celles-ci sont indiquées par l’absence ou la présence, respectivement, du suffixe de type décimal.</span><span class="sxs-lookup"><span data-stu-id="c4d68-156">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="c4d68-157">PowerShell ne prend pas en charge la représentation littérale d’une `[float]` valeur.</span><span class="sxs-lookup"><span data-stu-id="c4d68-157">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="c4d68-158">Un littéral réel double a le type `[double]` .</span><span class="sxs-lookup"><span data-stu-id="c4d68-158">A double real literal has type `[double]`.</span></span> <span data-ttu-id="c4d68-159">Un littéral réel décimal a le type `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="c4d68-159">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="c4d68-160">Les zéros de fin dans la partie fractionnaire d’un littéral réel décimal sont significatifs.</span><span class="sxs-lookup"><span data-stu-id="c4d68-160">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="c4d68-161">Si la valeur des chiffres de la partie exposant dans un `[double]` littéral réel est inférieure à la valeur minimale prise en charge, la valeur de ce `[double]` littéral réel est 0.</span><span class="sxs-lookup"><span data-stu-id="c4d68-161">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="c4d68-162">Si la valeur des chiffres de la partie exposant dans un `[decimal]` littéral réel est inférieure à la valeur minimale prise en charge, ce littéral est incorrect.</span><span class="sxs-lookup"><span data-stu-id="c4d68-162">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="c4d68-163">Si la valeur des chiffres de la partie exposant dans un `[double]` `[decimal]` littéral réel ou est supérieure à la valeur maximale prise en charge, ce littéral est incorrect.</span><span class="sxs-lookup"><span data-stu-id="c4d68-163">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="c4d68-164">La syntaxe autorise un littéral double réel à avoir un suffixe de type long.</span><span class="sxs-lookup"><span data-stu-id="c4d68-164">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="c4d68-165">PowerShell traite ce cas comme un littéral d’entier dont la valeur est représentée par le type `[long]` .</span><span class="sxs-lookup"><span data-stu-id="c4d68-165">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="c4d68-166">Cette fonctionnalité a été conservée à des fins de compatibilité descendante avec les versions antérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4d68-166">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="c4d68-167">Toutefois, les programmeurs sont déconseillés d’utiliser des littéraux entiers de ce formulaire, car ils peuvent facilement masquer la valeur réelle du littéral.</span><span class="sxs-lookup"><span data-stu-id="c4d68-167">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="c4d68-168">Par exemple, `1.2L` a la valeur 1, `1.2345e1L` a la valeur 12 et `1.2345e-5L` a la valeur 0, aucune d’entre elles étant immédiatement évidente.</span><span class="sxs-lookup"><span data-stu-id="c4d68-168">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="c4d68-169">Multiplicateurs numériques</span><span class="sxs-lookup"><span data-stu-id="c4d68-169">Numeric multipliers</span></span>

<span data-ttu-id="c4d68-170">Pour des raisons pratiques, les littéraux entiers et réels peuvent contenir un multiplicateur numérique, ce qui indique un ensemble de puissances couramment utilisées de 2.</span><span class="sxs-lookup"><span data-stu-id="c4d68-170">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="c4d68-171">Le multiplicateur numérique peut être écrit dans n’importe quelle combinaison de lettres majuscules ou minuscules.</span><span class="sxs-lookup"><span data-stu-id="c4d68-171">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="c4d68-172">Les suffixes de multiplicateur peuvent être utilisés en combinaison avec `u` les `ul` `l` suffixes de type, et.</span><span class="sxs-lookup"><span data-stu-id="c4d68-172">The multiplier suffixes can be used in combination with the `u`, `ul`, and `l` type suffixes.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="c4d68-173">Exemples de multiplicateur</span><span class="sxs-lookup"><span data-stu-id="c4d68-173">Multiplier examples</span></span>

```
PS> 1kb
1024

PS> 1.30Dmb
1363148.80

PS> 0x10Gb
17179869184

PS> 1.4e23tb
1.5393162788864E+35

PS> 0x12Lpb
20266198323167232
```

## <a name="numeric-type-accelerators"></a><span data-ttu-id="c4d68-174">Accélérateurs de type numérique</span><span class="sxs-lookup"><span data-stu-id="c4d68-174">Numeric type accelerators</span></span>

<span data-ttu-id="c4d68-175">PowerShell prend en charge les accélérateurs de type suivants :</span><span class="sxs-lookup"><span data-stu-id="c4d68-175">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="c4d68-176">Accélérateur</span><span class="sxs-lookup"><span data-stu-id="c4d68-176">Accelerator</span></span> |         <span data-ttu-id="c4d68-177">Notes</span><span class="sxs-lookup"><span data-stu-id="c4d68-177">Note</span></span>         |           <span data-ttu-id="c4d68-178">Description</span><span class="sxs-lookup"><span data-stu-id="c4d68-178">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="c4d68-179">Byte (non signé)</span><span class="sxs-lookup"><span data-stu-id="c4d68-179">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="c4d68-180">Octet (signé)</span><span class="sxs-lookup"><span data-stu-id="c4d68-180">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="c4d68-181">Entier de 16 bits</span><span class="sxs-lookup"><span data-stu-id="c4d68-181">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="c4d68-182">entier 16 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="c4d68-182">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="c4d68-183">Entier de 32 bits</span><span class="sxs-lookup"><span data-stu-id="c4d68-183">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="c4d68-184">alias pour `[int32]`</span><span class="sxs-lookup"><span data-stu-id="c4d68-184">alias for `[int32]`</span></span>  | <span data-ttu-id="c4d68-185">Entier de 32 bits</span><span class="sxs-lookup"><span data-stu-id="c4d68-185">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="c4d68-186">entier 32 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="c4d68-186">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="c4d68-187">Entier 64 bits</span><span class="sxs-lookup"><span data-stu-id="c4d68-187">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="c4d68-188">alias pour `[int64]`</span><span class="sxs-lookup"><span data-stu-id="c4d68-188">alias for `[int64]`</span></span>  | <span data-ttu-id="c4d68-189">Entier 64 bits</span><span class="sxs-lookup"><span data-stu-id="c4d68-189">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="c4d68-190">entier 64 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="c4d68-190">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="c4d68-191">Voir [BigInteger, struct][bigint]</span><span class="sxs-lookup"><span data-stu-id="c4d68-191">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="c4d68-192">Virgule flottante simple précision</span><span class="sxs-lookup"><span data-stu-id="c4d68-192">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="c4d68-193">alias pour `[single]`</span><span class="sxs-lookup"><span data-stu-id="c4d68-193">alias for `[single]`</span></span> | <span data-ttu-id="c4d68-194">Virgule flottante simple précision</span><span class="sxs-lookup"><span data-stu-id="c4d68-194">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="c4d68-195">Virgule flottante double précision</span><span class="sxs-lookup"><span data-stu-id="c4d68-195">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="c4d68-196">virgule flottante 128 bits</span><span class="sxs-lookup"><span data-stu-id="c4d68-196">128-bit floating point</span></span>           |

### <a name="working-with-other-numeric-types"></a><span data-ttu-id="c4d68-197">Utilisation d’autres types numériques</span><span class="sxs-lookup"><span data-stu-id="c4d68-197">Working with other numeric types</span></span>

<span data-ttu-id="c4d68-198">Pour travailler avec d’autres types numériques, vous devez utiliser des accélérateurs de type, ce qui n’est pas sans problèmes.</span><span class="sxs-lookup"><span data-stu-id="c4d68-198">To work with any other numeric types you must use type accelerators, which is not without some problems.</span></span> <span data-ttu-id="c4d68-199">Par exemple, les valeurs entières élevées sont toujours analysées comme double avant d’être converties en un autre type.</span><span class="sxs-lookup"><span data-stu-id="c4d68-199">For example, high integer values are always parsed as double before being cast to any other type.</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="c4d68-200">La valeur est analysée en premier, ce qui perd la précision dans les plages supérieures.</span><span class="sxs-lookup"><span data-stu-id="c4d68-200">The value is parsed as a double first, losing precision in the higher ranges.</span></span>
<span data-ttu-id="c4d68-201">Pour éviter ce problème, entrez des valeurs sous forme de chaînes, puis convertissez-les :</span><span class="sxs-lookup"><span data-stu-id="c4d68-201">To avoid this problem, enter values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

## <a name="examples"></a><span data-ttu-id="c4d68-202">Exemples</span><span class="sxs-lookup"><span data-stu-id="c4d68-202">Examples</span></span>

<span data-ttu-id="c4d68-203">Le tableau suivant contient plusieurs exemples de littéraux numériques et répertorie leur type et leur valeur :</span><span class="sxs-lookup"><span data-stu-id="c4d68-203">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|  <span data-ttu-id="c4d68-204">Number</span><span class="sxs-lookup"><span data-stu-id="c4d68-204">Number</span></span>  |  <span data-ttu-id="c4d68-205">Type</span><span class="sxs-lookup"><span data-stu-id="c4d68-205">Type</span></span>   |    <span data-ttu-id="c4d68-206">Valeur</span><span class="sxs-lookup"><span data-stu-id="c4d68-206">Value</span></span>     |
| -------: | ------- | -----------: |
|      <span data-ttu-id="c4d68-207">100</span><span class="sxs-lookup"><span data-stu-id="c4d68-207">100</span></span> | <span data-ttu-id="c4d68-208">Int32</span><span class="sxs-lookup"><span data-stu-id="c4d68-208">Int32</span></span>   |          <span data-ttu-id="c4d68-209">100</span><span class="sxs-lookup"><span data-stu-id="c4d68-209">100</span></span> |
|     <span data-ttu-id="c4d68-210">100D</span><span class="sxs-lookup"><span data-stu-id="c4d68-210">100D</span></span> | <span data-ttu-id="c4d68-211">Decimal</span><span class="sxs-lookup"><span data-stu-id="c4d68-211">Decimal</span></span> |          <span data-ttu-id="c4d68-212">100</span><span class="sxs-lookup"><span data-stu-id="c4d68-212">100</span></span> |
|     <span data-ttu-id="c4d68-213">100l</span><span class="sxs-lookup"><span data-stu-id="c4d68-213">100l</span></span> | <span data-ttu-id="c4d68-214">Int64</span><span class="sxs-lookup"><span data-stu-id="c4d68-214">Int64</span></span>   |          <span data-ttu-id="c4d68-215">100</span><span class="sxs-lookup"><span data-stu-id="c4d68-215">100</span></span> |
|      <span data-ttu-id="c4d68-216">1e2</span><span class="sxs-lookup"><span data-stu-id="c4d68-216">1e2</span></span> | <span data-ttu-id="c4d68-217">Double</span><span class="sxs-lookup"><span data-stu-id="c4d68-217">Double</span></span>  |          <span data-ttu-id="c4d68-218">100</span><span class="sxs-lookup"><span data-stu-id="c4d68-218">100</span></span> |
|     <span data-ttu-id="c4d68-219">1. E2</span><span class="sxs-lookup"><span data-stu-id="c4d68-219">1.e2</span></span> | <span data-ttu-id="c4d68-220">Double</span><span class="sxs-lookup"><span data-stu-id="c4d68-220">Double</span></span>  |          <span data-ttu-id="c4d68-221">100</span><span class="sxs-lookup"><span data-stu-id="c4d68-221">100</span></span> |
|    <span data-ttu-id="c4d68-222">0x1e2</span><span class="sxs-lookup"><span data-stu-id="c4d68-222">0x1e2</span></span> | <span data-ttu-id="c4d68-223">Int32</span><span class="sxs-lookup"><span data-stu-id="c4d68-223">Int32</span></span>   |          <span data-ttu-id="c4d68-224">482</span><span class="sxs-lookup"><span data-stu-id="c4d68-224">482</span></span> |
|   <span data-ttu-id="c4d68-225">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="c4d68-225">0x1e2L</span></span> | <span data-ttu-id="c4d68-226">Int64</span><span class="sxs-lookup"><span data-stu-id="c4d68-226">Int64</span></span>   |          <span data-ttu-id="c4d68-227">482</span><span class="sxs-lookup"><span data-stu-id="c4d68-227">482</span></span> |
|   <span data-ttu-id="c4d68-228">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="c4d68-228">0x1e2D</span></span> | <span data-ttu-id="c4d68-229">Int32</span><span class="sxs-lookup"><span data-stu-id="c4d68-229">Int32</span></span>   |         <span data-ttu-id="c4d68-230">7725</span><span class="sxs-lookup"><span data-stu-id="c4d68-230">7725</span></span> |
|     <span data-ttu-id="c4d68-231">482D</span><span class="sxs-lookup"><span data-stu-id="c4d68-231">482D</span></span> | <span data-ttu-id="c4d68-232">Decimal</span><span class="sxs-lookup"><span data-stu-id="c4d68-232">Decimal</span></span> |          <span data-ttu-id="c4d68-233">482</span><span class="sxs-lookup"><span data-stu-id="c4d68-233">482</span></span> |
|    <span data-ttu-id="c4d68-234">482gb</span><span class="sxs-lookup"><span data-stu-id="c4d68-234">482gb</span></span> | <span data-ttu-id="c4d68-235">Int64</span><span class="sxs-lookup"><span data-stu-id="c4d68-235">Int64</span></span>   | <span data-ttu-id="c4d68-236">517543559168</span><span class="sxs-lookup"><span data-stu-id="c4d68-236">517543559168</span></span> |
| <span data-ttu-id="c4d68-237">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="c4d68-237">0x1e2lgb</span></span> | <span data-ttu-id="c4d68-238">Int64</span><span class="sxs-lookup"><span data-stu-id="c4d68-238">Int64</span></span>   | <span data-ttu-id="c4d68-239">517543559168</span><span class="sxs-lookup"><span data-stu-id="c4d68-239">517543559168</span></span> |

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="c4d68-240">Commandes qui ressemblent à des littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="c4d68-240">Commands that look like numeric literals</span></span>

<span data-ttu-id="c4d68-241">Toute commande ressemblant à un littéral numérique doit être exécutée à l’aide de l’opérateur `&` d’appel (), sinon elle est interprétée comme un nombre du type associé.</span><span class="sxs-lookup"><span data-stu-id="c4d68-241">Any command that looks like a numeric literal must be executed using the the call operator (`&`), otherwise it is interpreted as a number of the associated type.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="c4d68-242">Accéder aux propriétés et aux méthodes d’objets numériques</span><span class="sxs-lookup"><span data-stu-id="c4d68-242">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="c4d68-243">Pour accéder à un membre d’un littéral numérique, il y a des cas où vous devez placer le littéral entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="c4d68-243">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="c4d68-244">Le littéral n’a pas de virgule décimale</span><span class="sxs-lookup"><span data-stu-id="c4d68-244">The literal does not have a decimal point</span></span>
- <span data-ttu-id="c4d68-245">Le littéral n’a pas de chiffres après la virgule décimale</span><span class="sxs-lookup"><span data-stu-id="c4d68-245">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="c4d68-246">Le littéral n’a pas de suffixe</span><span class="sxs-lookup"><span data-stu-id="c4d68-246">The literal does not have a suffix</span></span>

<span data-ttu-id="c4d68-247">Par exemple, l’exemple suivant échoue :</span><span class="sxs-lookup"><span data-stu-id="c4d68-247">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="c4d68-248">Les exemples suivants fonctionnent :</span><span class="sxs-lookup"><span data-stu-id="c4d68-248">The following examples work:</span></span>

```
PS> 2L.GetType().Name
Int64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="c4d68-249">Les deux premiers exemples fonctionnent sans mettre la valeur littérale entre parenthèses, car l’analyseur PowerShell peut déterminer où se termine le littéral numérique et la méthode **GetType** démarre.</span><span class="sxs-lookup"><span data-stu-id="c4d68-249">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
