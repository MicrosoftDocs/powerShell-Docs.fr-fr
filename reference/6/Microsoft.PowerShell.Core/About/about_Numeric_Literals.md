---
description: Les littéraux numériques et réels peuvent avoir des suffixes de type et de multiplicateur.
Locale: en-US
ms.date: 04/09/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos des littéraux numériques
ms.openlocfilehash: 62f00ae9f3643724808146134fd03b6f01c29bce
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208630"
---
# <a name="about-numeric-literals"></a><span data-ttu-id="41736-103">À propos des littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="41736-103">About numeric literals</span></span>

<span data-ttu-id="41736-104">Il existe deux types de littéraux numériques : entier et réel.</span><span class="sxs-lookup"><span data-stu-id="41736-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="41736-105">Les deux peuvent avoir des suffixes de type et multiplicateur.</span><span class="sxs-lookup"><span data-stu-id="41736-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="41736-106">Littéraux d'entier</span><span class="sxs-lookup"><span data-stu-id="41736-106">Integer literals</span></span>

<span data-ttu-id="41736-107">Les littéraux entiers peuvent être écrits en notation décimale ou hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="41736-107">Integer literals can be written in decimal or hexadecimal notation.</span></span> <span data-ttu-id="41736-108">Les littéraux hexadécimaux sont précédés de `0x` pour les distinguer des nombres décimaux.</span><span class="sxs-lookup"><span data-stu-id="41736-108">Hexadecimal literals are prefixed with `0x` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="41736-109">Les littéraux entiers peuvent avoir un suffixe de type et un suffixe multiplicateur.</span><span class="sxs-lookup"><span data-stu-id="41736-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="41736-110">Suffixe</span><span class="sxs-lookup"><span data-stu-id="41736-110">Suffix</span></span> |            <span data-ttu-id="41736-111">Signification</span><span class="sxs-lookup"><span data-stu-id="41736-111">Meaning</span></span>             |          <span data-ttu-id="41736-112">Notes</span><span class="sxs-lookup"><span data-stu-id="41736-112">Note</span></span>           |
| ------ | ------------------------------ | ----------------------- |
| <span data-ttu-id="41736-113">o</span><span class="sxs-lookup"><span data-stu-id="41736-113">y</span></span>      | <span data-ttu-id="41736-114">type de données Byte signé</span><span class="sxs-lookup"><span data-stu-id="41736-114">signed byte data type</span></span>          | <span data-ttu-id="41736-115">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="41736-115">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="41736-116">uy</span><span class="sxs-lookup"><span data-stu-id="41736-116">uy</span></span>     | <span data-ttu-id="41736-117">type de données Byte non signé</span><span class="sxs-lookup"><span data-stu-id="41736-117">unsigned byte data type</span></span>        | <span data-ttu-id="41736-118">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="41736-118">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="41736-119">s</span><span class="sxs-lookup"><span data-stu-id="41736-119">s</span></span>      | <span data-ttu-id="41736-120">short (type de données)</span><span class="sxs-lookup"><span data-stu-id="41736-120">short data type</span></span>                | <span data-ttu-id="41736-121">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="41736-121">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="41736-122">us</span><span class="sxs-lookup"><span data-stu-id="41736-122">us</span></span>     | <span data-ttu-id="41736-123">type de données Short non signé</span><span class="sxs-lookup"><span data-stu-id="41736-123">unsigned short data type</span></span>       | <span data-ttu-id="41736-124">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="41736-124">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="41736-125">l</span><span class="sxs-lookup"><span data-stu-id="41736-125">l</span></span>      | <span data-ttu-id="41736-126">long (type de données)</span><span class="sxs-lookup"><span data-stu-id="41736-126">long data type</span></span>                 |                         |
| <span data-ttu-id="41736-127">u</span><span class="sxs-lookup"><span data-stu-id="41736-127">u</span></span>      | <span data-ttu-id="41736-128">type de données int ou long non signé</span><span class="sxs-lookup"><span data-stu-id="41736-128">unsigned int or long data type</span></span> | <span data-ttu-id="41736-129">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="41736-129">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="41736-130">ul</span><span class="sxs-lookup"><span data-stu-id="41736-130">ul</span></span>     | <span data-ttu-id="41736-131">type de données long non signé</span><span class="sxs-lookup"><span data-stu-id="41736-131">unsigned long data type</span></span>        | <span data-ttu-id="41736-132">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="41736-132">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="41736-133">kb</span><span class="sxs-lookup"><span data-stu-id="41736-133">kb</span></span>     | <span data-ttu-id="41736-134">multiplicateur de kilo-octets</span><span class="sxs-lookup"><span data-stu-id="41736-134">kilobyte multiplier</span></span>            |                         |
| <span data-ttu-id="41736-135">mb</span><span class="sxs-lookup"><span data-stu-id="41736-135">mb</span></span>     | <span data-ttu-id="41736-136">multiplicateur de mégaoctets</span><span class="sxs-lookup"><span data-stu-id="41736-136">megabyte multiplier</span></span>            |                         |
| <span data-ttu-id="41736-137">moins</span><span class="sxs-lookup"><span data-stu-id="41736-137">gb</span></span>     | <span data-ttu-id="41736-138">multiplicateur de gigaoctets</span><span class="sxs-lookup"><span data-stu-id="41736-138">gigabyte multiplier</span></span>            |                         |
| <span data-ttu-id="41736-139">to</span><span class="sxs-lookup"><span data-stu-id="41736-139">tb</span></span>     | <span data-ttu-id="41736-140">multiplicateur de téraoctets</span><span class="sxs-lookup"><span data-stu-id="41736-140">terabyte multiplier</span></span>            |                         |
| <span data-ttu-id="41736-141">gérés</span><span class="sxs-lookup"><span data-stu-id="41736-141">pb</span></span>     | <span data-ttu-id="41736-142">multiplicateur de pétaoctet</span><span class="sxs-lookup"><span data-stu-id="41736-142">petabyte multiplier</span></span>            |                         |

<span data-ttu-id="41736-143">Le type d’un littéral entier est déterminé par sa valeur, le suffixe de type et le suffixe multiplicateur numérique.</span><span class="sxs-lookup"><span data-stu-id="41736-143">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="41736-144">Pour un littéral d’entier sans suffixe de type :</span><span class="sxs-lookup"><span data-stu-id="41736-144">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="41736-145">Si la valeur peut être représentée par le type `[int]` , il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="41736-145">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="41736-146">Sinon, si la valeur peut être représentée par le type `[long]` , il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="41736-146">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="41736-147">Sinon, si la valeur peut être représentée par le type `[decimal]` , il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="41736-147">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="41736-148">Dans le cas contraire, il est représenté par le type `[double]` .</span><span class="sxs-lookup"><span data-stu-id="41736-148">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="41736-149">Pour un littéral d’entier avec un suffixe de type :</span><span class="sxs-lookup"><span data-stu-id="41736-149">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="41736-150">Si le suffixe de type est `u` et que la valeur peut être représentée par le type, `[uint]` son type est `[uint]` .</span><span class="sxs-lookup"><span data-stu-id="41736-150">If the type suffix is `u` and the value can be represented by type `[uint]` then its type is `[uint]`.</span></span>
- <span data-ttu-id="41736-151">Si le suffixe de type est `u` et que la valeur peut être représentée par le type, `[ulong]` son type est `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="41736-151">If the type suffix is `u` and the value can be represented by type `[ulong]` then its type is `[ulong]`.</span></span>
- <span data-ttu-id="41736-152">Si sa valeur peut être représentée par le type spécifié, alors il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="41736-152">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="41736-153">Dans le cas contraire, ce littéral est incorrect.</span><span class="sxs-lookup"><span data-stu-id="41736-153">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="41736-154">Littéraux réels</span><span class="sxs-lookup"><span data-stu-id="41736-154">Real literals</span></span>

<span data-ttu-id="41736-155">Les littéraux réels ne peuvent être écrits qu’en notation décimale.</span><span class="sxs-lookup"><span data-stu-id="41736-155">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="41736-156">Cette notation peut inclure des valeurs fractionnaires à la suite d’une virgule décimale et d’une notation scientifique à l’aide d’une partie exponentielle.</span><span class="sxs-lookup"><span data-stu-id="41736-156">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="41736-157">La partie exponentielle comprend un « e » suivi d’un signe facultatif (+/-) et d’un nombre représentant l’exposant.</span><span class="sxs-lookup"><span data-stu-id="41736-157">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="41736-158">Par exemple, la valeur littérale `1e2` est égale à la valeur numérique 100.</span><span class="sxs-lookup"><span data-stu-id="41736-158">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="41736-159">Les littéraux réels peuvent avoir un suffixe de type et un suffixe multiplicateur.</span><span class="sxs-lookup"><span data-stu-id="41736-159">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="41736-160">Suffixe</span><span class="sxs-lookup"><span data-stu-id="41736-160">Suffix</span></span> |       <span data-ttu-id="41736-161">Signification</span><span class="sxs-lookup"><span data-stu-id="41736-161">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="41736-162">d</span><span class="sxs-lookup"><span data-stu-id="41736-162">d</span></span>      | <span data-ttu-id="41736-163">type de données decimal</span><span class="sxs-lookup"><span data-stu-id="41736-163">decimal data type</span></span>   |
| <span data-ttu-id="41736-164">kb</span><span class="sxs-lookup"><span data-stu-id="41736-164">kb</span></span>     | <span data-ttu-id="41736-165">multiplicateur de kilo-octets</span><span class="sxs-lookup"><span data-stu-id="41736-165">kilobyte multiplier</span></span> |
| <span data-ttu-id="41736-166">mb</span><span class="sxs-lookup"><span data-stu-id="41736-166">mb</span></span>     | <span data-ttu-id="41736-167">multiplicateur de mégaoctets</span><span class="sxs-lookup"><span data-stu-id="41736-167">megabyte multiplier</span></span> |
| <span data-ttu-id="41736-168">moins</span><span class="sxs-lookup"><span data-stu-id="41736-168">gb</span></span>     | <span data-ttu-id="41736-169">multiplicateur de gigaoctets</span><span class="sxs-lookup"><span data-stu-id="41736-169">gigabyte multiplier</span></span> |
| <span data-ttu-id="41736-170">to</span><span class="sxs-lookup"><span data-stu-id="41736-170">tb</span></span>     | <span data-ttu-id="41736-171">multiplicateur de téraoctets</span><span class="sxs-lookup"><span data-stu-id="41736-171">terabyte multiplier</span></span> |
| <span data-ttu-id="41736-172">gérés</span><span class="sxs-lookup"><span data-stu-id="41736-172">pb</span></span>     | <span data-ttu-id="41736-173">multiplicateur de pétaoctet</span><span class="sxs-lookup"><span data-stu-id="41736-173">petabyte multiplier</span></span> |

<span data-ttu-id="41736-174">Il existe deux types de littéraux réels : double et Decimal.</span><span class="sxs-lookup"><span data-stu-id="41736-174">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="41736-175">Celles-ci sont indiquées par l’absence ou la présence, respectivement, du suffixe de type décimal.</span><span class="sxs-lookup"><span data-stu-id="41736-175">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="41736-176">PowerShell ne prend pas en charge la représentation littérale d’une `[float]` valeur.</span><span class="sxs-lookup"><span data-stu-id="41736-176">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="41736-177">Un littéral réel double a le type `[double]` .</span><span class="sxs-lookup"><span data-stu-id="41736-177">A double real literal has type `[double]`.</span></span> <span data-ttu-id="41736-178">Un littéral réel décimal a le type `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="41736-178">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="41736-179">Les zéros de fin dans la partie fractionnaire d’un littéral réel décimal sont significatifs.</span><span class="sxs-lookup"><span data-stu-id="41736-179">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="41736-180">Si la valeur des chiffres de la partie exposant dans un `[double]` littéral réel est inférieure à la valeur minimale prise en charge, la valeur de ce `[double]` littéral réel est 0.</span><span class="sxs-lookup"><span data-stu-id="41736-180">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="41736-181">Si la valeur des chiffres de la partie exposant dans un `[decimal]` littéral réel est inférieure à la valeur minimale prise en charge, ce littéral est incorrect.</span><span class="sxs-lookup"><span data-stu-id="41736-181">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="41736-182">Si la valeur des chiffres de la partie exposant dans un `[double]` `[decimal]` littéral réel ou est supérieure à la valeur maximale prise en charge, ce littéral est incorrect.</span><span class="sxs-lookup"><span data-stu-id="41736-182">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="41736-183">La syntaxe autorise un littéral double réel à avoir un suffixe de type long.</span><span class="sxs-lookup"><span data-stu-id="41736-183">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="41736-184">PowerShell traite ce cas comme un littéral d’entier dont la valeur est représentée par le type `[long]` .</span><span class="sxs-lookup"><span data-stu-id="41736-184">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="41736-185">Cette fonctionnalité a été conservée à des fins de compatibilité descendante avec les versions antérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41736-185">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="41736-186">Toutefois, les programmeurs sont déconseillés d’utiliser des littéraux entiers de ce formulaire, car ils peuvent facilement masquer la valeur réelle du littéral.</span><span class="sxs-lookup"><span data-stu-id="41736-186">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="41736-187">Par exemple, `1.2L` a la valeur 1, `1.2345e1L` a la valeur 12 et `1.2345e-5L` a la valeur 0, aucune d’entre elles étant immédiatement évidente.</span><span class="sxs-lookup"><span data-stu-id="41736-187">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="41736-188">Multiplicateurs numériques</span><span class="sxs-lookup"><span data-stu-id="41736-188">Numeric multipliers</span></span>

<span data-ttu-id="41736-189">Pour des raisons pratiques, les littéraux entiers et réels peuvent contenir un multiplicateur numérique, ce qui indique un ensemble de puissances couramment utilisées de 2.</span><span class="sxs-lookup"><span data-stu-id="41736-189">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="41736-190">Le multiplicateur numérique peut être écrit dans n’importe quelle combinaison de lettres majuscules ou minuscules.</span><span class="sxs-lookup"><span data-stu-id="41736-190">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="41736-191">Les suffixes de multiplicateur peuvent être utilisés en combinaison avec `u` les `ul` `l` suffixes de type, et.</span><span class="sxs-lookup"><span data-stu-id="41736-191">The multiplier suffixes can be used in combination with the `u`, `ul`, and `l` type suffixes.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="41736-192">Exemples de multiplicateur</span><span class="sxs-lookup"><span data-stu-id="41736-192">Multiplier examples</span></span>

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

## <a name="numeric-type-accelerators"></a><span data-ttu-id="41736-193">Accélérateurs de type numérique</span><span class="sxs-lookup"><span data-stu-id="41736-193">Numeric type accelerators</span></span>

<span data-ttu-id="41736-194">PowerShell prend en charge les accélérateurs de type suivants :</span><span class="sxs-lookup"><span data-stu-id="41736-194">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="41736-195">Accélérateur</span><span class="sxs-lookup"><span data-stu-id="41736-195">Accelerator</span></span> |         <span data-ttu-id="41736-196">Notes</span><span class="sxs-lookup"><span data-stu-id="41736-196">Note</span></span>         |           <span data-ttu-id="41736-197">Description</span><span class="sxs-lookup"><span data-stu-id="41736-197">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="41736-198">Byte (non signé)</span><span class="sxs-lookup"><span data-stu-id="41736-198">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="41736-199">Octet (signé)</span><span class="sxs-lookup"><span data-stu-id="41736-199">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="41736-200">Entier de 16 bits</span><span class="sxs-lookup"><span data-stu-id="41736-200">16-bit integer</span></span>                   |
| `[short]`   | <span data-ttu-id="41736-201">alias pour `[int16]`</span><span class="sxs-lookup"><span data-stu-id="41736-201">alias for `[int16]`</span></span>  | <span data-ttu-id="41736-202">Entier de 16 bits</span><span class="sxs-lookup"><span data-stu-id="41736-202">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="41736-203">entier 16 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="41736-203">16-bit integer (unsigned)</span></span>        |
| `[ushort]`  | <span data-ttu-id="41736-204">alias pour `[uint16]`</span><span class="sxs-lookup"><span data-stu-id="41736-204">alias for `[uint16]`</span></span> | <span data-ttu-id="41736-205">entier 16 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="41736-205">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="41736-206">Entier de 32 bits</span><span class="sxs-lookup"><span data-stu-id="41736-206">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="41736-207">alias pour `[int32]`</span><span class="sxs-lookup"><span data-stu-id="41736-207">alias for `[int32]`</span></span>  | <span data-ttu-id="41736-208">Entier de 32 bits</span><span class="sxs-lookup"><span data-stu-id="41736-208">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="41736-209">entier 32 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="41736-209">32-bit integer (unsigned)</span></span>        |
| `[uint]`    | <span data-ttu-id="41736-210">alias pour `[uint32]`</span><span class="sxs-lookup"><span data-stu-id="41736-210">alias for `[uint32]`</span></span> | <span data-ttu-id="41736-211">entier 32 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="41736-211">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="41736-212">Entier 64 bits</span><span class="sxs-lookup"><span data-stu-id="41736-212">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="41736-213">alias pour `[int64]`</span><span class="sxs-lookup"><span data-stu-id="41736-213">alias for `[int64]`</span></span>  | <span data-ttu-id="41736-214">Entier 64 bits</span><span class="sxs-lookup"><span data-stu-id="41736-214">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="41736-215">entier 64 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="41736-215">64-bit integer (unsigned)</span></span>        |
| `[ulong]`   | <span data-ttu-id="41736-216">alias pour `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="41736-216">alias for `[uint64]`</span></span> | <span data-ttu-id="41736-217">entier 64 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="41736-217">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="41736-218">Voir [BigInteger, struct][bigint]</span><span class="sxs-lookup"><span data-stu-id="41736-218">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="41736-219">Virgule flottante simple précision</span><span class="sxs-lookup"><span data-stu-id="41736-219">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="41736-220">alias pour `[single]`</span><span class="sxs-lookup"><span data-stu-id="41736-220">alias for `[single]`</span></span> | <span data-ttu-id="41736-221">Virgule flottante simple précision</span><span class="sxs-lookup"><span data-stu-id="41736-221">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="41736-222">Virgule flottante double précision</span><span class="sxs-lookup"><span data-stu-id="41736-222">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="41736-223">virgule flottante 128 bits</span><span class="sxs-lookup"><span data-stu-id="41736-223">128-bit floating point</span></span>           |

> [!NOTE]
> <span data-ttu-id="41736-224">Les accélérateurs de type suivants ont été ajoutés dans PowerShell 6,2 : `[short]` , `[ushort]` ,, `[uint]` `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="41736-224">The following type accelerators were added in PowerShell 6.2: `[short]`, `[ushort]`, `[uint]`, `[ulong]`.</span></span>

### <a name="working-with-other-numeric-types"></a><span data-ttu-id="41736-225">Utilisation d’autres types numériques</span><span class="sxs-lookup"><span data-stu-id="41736-225">Working with other numeric types</span></span>

<span data-ttu-id="41736-226">Pour travailler avec d’autres types numériques, vous devez utiliser des accélérateurs de type, ce qui n’est pas sans problèmes.</span><span class="sxs-lookup"><span data-stu-id="41736-226">To work with any other numeric types you must use type accelerators, which is not without some problems.</span></span> <span data-ttu-id="41736-227">Par exemple, les valeurs entières élevées sont toujours analysées comme double avant d’être converties en un autre type.</span><span class="sxs-lookup"><span data-stu-id="41736-227">For example, high integer values are always parsed as double before being cast to any other type.</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="41736-228">La valeur est analysée en premier, ce qui perd la précision dans les plages supérieures.</span><span class="sxs-lookup"><span data-stu-id="41736-228">The value is parsed as a double first, losing precision in the higher ranges.</span></span>
<span data-ttu-id="41736-229">Pour éviter ce problème, entrez des valeurs sous forme de chaînes, puis convertissez-les :</span><span class="sxs-lookup"><span data-stu-id="41736-229">To avoid this problem, enter values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

## <a name="examples"></a><span data-ttu-id="41736-230">Exemples</span><span class="sxs-lookup"><span data-stu-id="41736-230">Examples</span></span>

<span data-ttu-id="41736-231">Le tableau suivant contient plusieurs exemples de littéraux numériques et répertorie leur type et leur valeur :</span><span class="sxs-lookup"><span data-stu-id="41736-231">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|  <span data-ttu-id="41736-232">Number</span><span class="sxs-lookup"><span data-stu-id="41736-232">Number</span></span>  |  <span data-ttu-id="41736-233">Type</span><span class="sxs-lookup"><span data-stu-id="41736-233">Type</span></span>   |    <span data-ttu-id="41736-234">Valeur</span><span class="sxs-lookup"><span data-stu-id="41736-234">Value</span></span>     |
| -------: | ------- | -----------: |
|      <span data-ttu-id="41736-235">100</span><span class="sxs-lookup"><span data-stu-id="41736-235">100</span></span> | <span data-ttu-id="41736-236">Int32</span><span class="sxs-lookup"><span data-stu-id="41736-236">Int32</span></span>   |          <span data-ttu-id="41736-237">100</span><span class="sxs-lookup"><span data-stu-id="41736-237">100</span></span> |
|     <span data-ttu-id="41736-238">100D</span><span class="sxs-lookup"><span data-stu-id="41736-238">100D</span></span> | <span data-ttu-id="41736-239">Decimal</span><span class="sxs-lookup"><span data-stu-id="41736-239">Decimal</span></span> |          <span data-ttu-id="41736-240">100</span><span class="sxs-lookup"><span data-stu-id="41736-240">100</span></span> |
|     <span data-ttu-id="41736-241">100l</span><span class="sxs-lookup"><span data-stu-id="41736-241">100l</span></span> | <span data-ttu-id="41736-242">Int64</span><span class="sxs-lookup"><span data-stu-id="41736-242">Int64</span></span>   |          <span data-ttu-id="41736-243">100</span><span class="sxs-lookup"><span data-stu-id="41736-243">100</span></span> |
|    <span data-ttu-id="41736-244">100uL</span><span class="sxs-lookup"><span data-stu-id="41736-244">100uL</span></span> | <span data-ttu-id="41736-245">UInt64</span><span class="sxs-lookup"><span data-stu-id="41736-245">UInt64</span></span>  |          <span data-ttu-id="41736-246">100</span><span class="sxs-lookup"><span data-stu-id="41736-246">100</span></span> |
|    <span data-ttu-id="41736-247">100us</span><span class="sxs-lookup"><span data-stu-id="41736-247">100us</span></span> | <span data-ttu-id="41736-248">UInt16</span><span class="sxs-lookup"><span data-stu-id="41736-248">UInt16</span></span>  |          <span data-ttu-id="41736-249">100</span><span class="sxs-lookup"><span data-stu-id="41736-249">100</span></span> |
|    <span data-ttu-id="41736-250">100uy</span><span class="sxs-lookup"><span data-stu-id="41736-250">100uy</span></span> | <span data-ttu-id="41736-251">Byte</span><span class="sxs-lookup"><span data-stu-id="41736-251">Byte</span></span>    |          <span data-ttu-id="41736-252">100</span><span class="sxs-lookup"><span data-stu-id="41736-252">100</span></span> |
|     <span data-ttu-id="41736-253">100y</span><span class="sxs-lookup"><span data-stu-id="41736-253">100y</span></span> | <span data-ttu-id="41736-254">SByte</span><span class="sxs-lookup"><span data-stu-id="41736-254">SByte</span></span>   |          <span data-ttu-id="41736-255">100</span><span class="sxs-lookup"><span data-stu-id="41736-255">100</span></span> |
|      <span data-ttu-id="41736-256">1e2</span><span class="sxs-lookup"><span data-stu-id="41736-256">1e2</span></span> | <span data-ttu-id="41736-257">Double</span><span class="sxs-lookup"><span data-stu-id="41736-257">Double</span></span>  |          <span data-ttu-id="41736-258">100</span><span class="sxs-lookup"><span data-stu-id="41736-258">100</span></span> |
|     <span data-ttu-id="41736-259">1. E2</span><span class="sxs-lookup"><span data-stu-id="41736-259">1.e2</span></span> | <span data-ttu-id="41736-260">Double</span><span class="sxs-lookup"><span data-stu-id="41736-260">Double</span></span>  |          <span data-ttu-id="41736-261">100</span><span class="sxs-lookup"><span data-stu-id="41736-261">100</span></span> |
|    <span data-ttu-id="41736-262">0x1e2</span><span class="sxs-lookup"><span data-stu-id="41736-262">0x1e2</span></span> | <span data-ttu-id="41736-263">Int32</span><span class="sxs-lookup"><span data-stu-id="41736-263">Int32</span></span>   |          <span data-ttu-id="41736-264">482</span><span class="sxs-lookup"><span data-stu-id="41736-264">482</span></span> |
|   <span data-ttu-id="41736-265">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="41736-265">0x1e2L</span></span> | <span data-ttu-id="41736-266">Int64</span><span class="sxs-lookup"><span data-stu-id="41736-266">Int64</span></span>   |          <span data-ttu-id="41736-267">482</span><span class="sxs-lookup"><span data-stu-id="41736-267">482</span></span> |
|   <span data-ttu-id="41736-268">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="41736-268">0x1e2D</span></span> | <span data-ttu-id="41736-269">Int32</span><span class="sxs-lookup"><span data-stu-id="41736-269">Int32</span></span>   |         <span data-ttu-id="41736-270">7725</span><span class="sxs-lookup"><span data-stu-id="41736-270">7725</span></span> |
|     <span data-ttu-id="41736-271">482D</span><span class="sxs-lookup"><span data-stu-id="41736-271">482D</span></span> | <span data-ttu-id="41736-272">Decimal</span><span class="sxs-lookup"><span data-stu-id="41736-272">Decimal</span></span> |          <span data-ttu-id="41736-273">482</span><span class="sxs-lookup"><span data-stu-id="41736-273">482</span></span> |
|    <span data-ttu-id="41736-274">482gb</span><span class="sxs-lookup"><span data-stu-id="41736-274">482gb</span></span> | <span data-ttu-id="41736-275">Int64</span><span class="sxs-lookup"><span data-stu-id="41736-275">Int64</span></span>   | <span data-ttu-id="41736-276">517543559168</span><span class="sxs-lookup"><span data-stu-id="41736-276">517543559168</span></span> |
| <span data-ttu-id="41736-277">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="41736-277">0x1e2lgb</span></span> | <span data-ttu-id="41736-278">Int64</span><span class="sxs-lookup"><span data-stu-id="41736-278">Int64</span></span>   | <span data-ttu-id="41736-279">517543559168</span><span class="sxs-lookup"><span data-stu-id="41736-279">517543559168</span></span> |

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="41736-280">Commandes qui ressemblent à des littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="41736-280">Commands that look like numeric literals</span></span>

<span data-ttu-id="41736-281">Toute commande ressemblant à un littéral numérique doit être exécutée à l’aide de l’opérateur `&` d’appel (), sinon elle est interprétée comme un nombre du type associé.</span><span class="sxs-lookup"><span data-stu-id="41736-281">Any command that looks like a numeric literal must be executed using the the call operator (`&`), otherwise it is interpreted as a number of the associated type.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="41736-282">Accéder aux propriétés et aux méthodes d’objets numériques</span><span class="sxs-lookup"><span data-stu-id="41736-282">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="41736-283">Pour accéder à un membre d’un littéral numérique, il y a des cas où vous devez placer le littéral entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="41736-283">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="41736-284">Le littéral n’a pas de virgule décimale</span><span class="sxs-lookup"><span data-stu-id="41736-284">The literal does not have a decimal point</span></span>
- <span data-ttu-id="41736-285">Le littéral n’a pas de chiffres après la virgule décimale</span><span class="sxs-lookup"><span data-stu-id="41736-285">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="41736-286">Le littéral n’a pas de suffixe</span><span class="sxs-lookup"><span data-stu-id="41736-286">The literal does not have a suffix</span></span>

<span data-ttu-id="41736-287">Par exemple, l’exemple suivant échoue :</span><span class="sxs-lookup"><span data-stu-id="41736-287">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="41736-288">Les exemples suivants fonctionnent :</span><span class="sxs-lookup"><span data-stu-id="41736-288">The following examples work:</span></span>

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="41736-289">Les deux premiers exemples fonctionnent sans mettre la valeur littérale entre parenthèses, car l’analyseur PowerShell peut déterminer où se termine le littéral numérique et la méthode **GetType** démarre.</span><span class="sxs-lookup"><span data-stu-id="41736-289">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger?view=netcore-2.2
