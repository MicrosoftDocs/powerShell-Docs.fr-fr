---
description: Les littéraux numériques et réels peuvent avoir des suffixes de type et de multiplicateur.
Locale: en-US
ms.date: 04/09/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos des littéraux numériques
ms.openlocfilehash: dc1a55dbec1f0de99e06011645e6884b37480233
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354827"
---
# <a name="about-numeric-literals"></a><span data-ttu-id="e86cc-103">À propos des littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="e86cc-103">About numeric literals</span></span>

<span data-ttu-id="e86cc-104">Il existe deux types de littéraux numériques : entier et réel.</span><span class="sxs-lookup"><span data-stu-id="e86cc-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="e86cc-105">Les deux peuvent avoir des suffixes de type et multiplicateur.</span><span class="sxs-lookup"><span data-stu-id="e86cc-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="e86cc-106">Littéraux d'entier</span><span class="sxs-lookup"><span data-stu-id="e86cc-106">Integer literals</span></span>

<span data-ttu-id="e86cc-107">Les littéraux entiers peuvent être écrits en notation décimale ou hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="e86cc-107">Integer literals can be written in decimal or hexadecimal notation.</span></span> <span data-ttu-id="e86cc-108">Les littéraux hexadécimaux sont précédés de `0x` pour les distinguer des nombres décimaux.</span><span class="sxs-lookup"><span data-stu-id="e86cc-108">Hexadecimal literals are prefixed with `0x` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="e86cc-109">Les littéraux entiers peuvent avoir un suffixe de type et un suffixe multiplicateur.</span><span class="sxs-lookup"><span data-stu-id="e86cc-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="e86cc-110">Suffixe</span><span class="sxs-lookup"><span data-stu-id="e86cc-110">Suffix</span></span> |            <span data-ttu-id="e86cc-111">Signification</span><span class="sxs-lookup"><span data-stu-id="e86cc-111">Meaning</span></span>             |          <span data-ttu-id="e86cc-112">Notes</span><span class="sxs-lookup"><span data-stu-id="e86cc-112">Note</span></span>           |
| ------ | ------------------------------ | ----------------------- |
| <span data-ttu-id="e86cc-113">o</span><span class="sxs-lookup"><span data-stu-id="e86cc-113">y</span></span>      | <span data-ttu-id="e86cc-114">type de données Byte signé</span><span class="sxs-lookup"><span data-stu-id="e86cc-114">signed byte data type</span></span>          | <span data-ttu-id="e86cc-115">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="e86cc-115">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="e86cc-116">uy</span><span class="sxs-lookup"><span data-stu-id="e86cc-116">uy</span></span>     | <span data-ttu-id="e86cc-117">type de données Byte non signé</span><span class="sxs-lookup"><span data-stu-id="e86cc-117">unsigned byte data type</span></span>        | <span data-ttu-id="e86cc-118">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="e86cc-118">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="e86cc-119">s</span><span class="sxs-lookup"><span data-stu-id="e86cc-119">s</span></span>      | <span data-ttu-id="e86cc-120">short (type de données)</span><span class="sxs-lookup"><span data-stu-id="e86cc-120">short data type</span></span>                | <span data-ttu-id="e86cc-121">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="e86cc-121">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="e86cc-122">us</span><span class="sxs-lookup"><span data-stu-id="e86cc-122">us</span></span>     | <span data-ttu-id="e86cc-123">type de données Short non signé</span><span class="sxs-lookup"><span data-stu-id="e86cc-123">unsigned short data type</span></span>       | <span data-ttu-id="e86cc-124">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="e86cc-124">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="e86cc-125">l</span><span class="sxs-lookup"><span data-stu-id="e86cc-125">l</span></span>      | <span data-ttu-id="e86cc-126">long (type de données)</span><span class="sxs-lookup"><span data-stu-id="e86cc-126">long data type</span></span>                 |                         |
| <span data-ttu-id="e86cc-127">u</span><span class="sxs-lookup"><span data-stu-id="e86cc-127">u</span></span>      | <span data-ttu-id="e86cc-128">type de données int ou long non signé</span><span class="sxs-lookup"><span data-stu-id="e86cc-128">unsigned int or long data type</span></span> | <span data-ttu-id="e86cc-129">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="e86cc-129">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="e86cc-130">ul</span><span class="sxs-lookup"><span data-stu-id="e86cc-130">ul</span></span>     | <span data-ttu-id="e86cc-131">type de données long non signé</span><span class="sxs-lookup"><span data-stu-id="e86cc-131">unsigned long data type</span></span>        | <span data-ttu-id="e86cc-132">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="e86cc-132">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="e86cc-133">kb</span><span class="sxs-lookup"><span data-stu-id="e86cc-133">kb</span></span>     | <span data-ttu-id="e86cc-134">multiplicateur de kilo-octets</span><span class="sxs-lookup"><span data-stu-id="e86cc-134">kilobyte multiplier</span></span>            |                         |
| <span data-ttu-id="e86cc-135">mb</span><span class="sxs-lookup"><span data-stu-id="e86cc-135">mb</span></span>     | <span data-ttu-id="e86cc-136">multiplicateur de mégaoctets</span><span class="sxs-lookup"><span data-stu-id="e86cc-136">megabyte multiplier</span></span>            |                         |
| <span data-ttu-id="e86cc-137">moins</span><span class="sxs-lookup"><span data-stu-id="e86cc-137">gb</span></span>     | <span data-ttu-id="e86cc-138">multiplicateur de gigaoctets</span><span class="sxs-lookup"><span data-stu-id="e86cc-138">gigabyte multiplier</span></span>            |                         |
| <span data-ttu-id="e86cc-139">to</span><span class="sxs-lookup"><span data-stu-id="e86cc-139">tb</span></span>     | <span data-ttu-id="e86cc-140">multiplicateur de téraoctets</span><span class="sxs-lookup"><span data-stu-id="e86cc-140">terabyte multiplier</span></span>            |                         |
| <span data-ttu-id="e86cc-141">gérés</span><span class="sxs-lookup"><span data-stu-id="e86cc-141">pb</span></span>     | <span data-ttu-id="e86cc-142">multiplicateur de pétaoctet</span><span class="sxs-lookup"><span data-stu-id="e86cc-142">petabyte multiplier</span></span>            |                         |

<span data-ttu-id="e86cc-143">Le type d’un littéral entier est déterminé par sa valeur, le suffixe de type et le suffixe multiplicateur numérique.</span><span class="sxs-lookup"><span data-stu-id="e86cc-143">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="e86cc-144">Pour un littéral d’entier sans suffixe de type :</span><span class="sxs-lookup"><span data-stu-id="e86cc-144">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="e86cc-145">Si la valeur peut être représentée par le type `[int]` , il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="e86cc-145">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="e86cc-146">Sinon, si la valeur peut être représentée par le type `[long]` , il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="e86cc-146">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="e86cc-147">Sinon, si la valeur peut être représentée par le type `[decimal]` , il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="e86cc-147">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="e86cc-148">Dans le cas contraire, il est représenté par le type `[double]` .</span><span class="sxs-lookup"><span data-stu-id="e86cc-148">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="e86cc-149">Pour un littéral d’entier avec un suffixe de type :</span><span class="sxs-lookup"><span data-stu-id="e86cc-149">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="e86cc-150">Si le suffixe de type est `u` et que la valeur peut être représentée par le type, `[uint]` son type est `[uint]` .</span><span class="sxs-lookup"><span data-stu-id="e86cc-150">If the type suffix is `u` and the value can be represented by type `[uint]` then its type is `[uint]`.</span></span>
- <span data-ttu-id="e86cc-151">Si le suffixe de type est `u` et que la valeur peut être représentée par le type, `[ulong]` son type est `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="e86cc-151">If the type suffix is `u` and the value can be represented by type `[ulong]` then its type is `[ulong]`.</span></span>
- <span data-ttu-id="e86cc-152">Si sa valeur peut être représentée par le type spécifié, alors il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="e86cc-152">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="e86cc-153">Dans le cas contraire, ce littéral est incorrect.</span><span class="sxs-lookup"><span data-stu-id="e86cc-153">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="e86cc-154">Littéraux réels</span><span class="sxs-lookup"><span data-stu-id="e86cc-154">Real literals</span></span>

<span data-ttu-id="e86cc-155">Les littéraux réels ne peuvent être écrits qu’en notation décimale.</span><span class="sxs-lookup"><span data-stu-id="e86cc-155">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="e86cc-156">Cette notation peut inclure des valeurs fractionnaires à la suite d’une virgule décimale et d’une notation scientifique à l’aide d’une partie exponentielle.</span><span class="sxs-lookup"><span data-stu-id="e86cc-156">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="e86cc-157">La partie exponentielle comprend un « e » suivi d’un signe facultatif (+/-) et d’un nombre représentant l’exposant.</span><span class="sxs-lookup"><span data-stu-id="e86cc-157">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="e86cc-158">Par exemple, la valeur littérale `1e2` est égale à la valeur numérique 100.</span><span class="sxs-lookup"><span data-stu-id="e86cc-158">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="e86cc-159">Les littéraux réels peuvent avoir un suffixe de type et un suffixe multiplicateur.</span><span class="sxs-lookup"><span data-stu-id="e86cc-159">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="e86cc-160">Suffixe</span><span class="sxs-lookup"><span data-stu-id="e86cc-160">Suffix</span></span> |       <span data-ttu-id="e86cc-161">Signification</span><span class="sxs-lookup"><span data-stu-id="e86cc-161">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="e86cc-162">d</span><span class="sxs-lookup"><span data-stu-id="e86cc-162">d</span></span>      | <span data-ttu-id="e86cc-163">type de données decimal</span><span class="sxs-lookup"><span data-stu-id="e86cc-163">decimal data type</span></span>   |
| <span data-ttu-id="e86cc-164">kb</span><span class="sxs-lookup"><span data-stu-id="e86cc-164">kb</span></span>     | <span data-ttu-id="e86cc-165">multiplicateur de kilo-octets</span><span class="sxs-lookup"><span data-stu-id="e86cc-165">kilobyte multiplier</span></span> |
| <span data-ttu-id="e86cc-166">mb</span><span class="sxs-lookup"><span data-stu-id="e86cc-166">mb</span></span>     | <span data-ttu-id="e86cc-167">multiplicateur de mégaoctets</span><span class="sxs-lookup"><span data-stu-id="e86cc-167">megabyte multiplier</span></span> |
| <span data-ttu-id="e86cc-168">moins</span><span class="sxs-lookup"><span data-stu-id="e86cc-168">gb</span></span>     | <span data-ttu-id="e86cc-169">multiplicateur de gigaoctets</span><span class="sxs-lookup"><span data-stu-id="e86cc-169">gigabyte multiplier</span></span> |
| <span data-ttu-id="e86cc-170">to</span><span class="sxs-lookup"><span data-stu-id="e86cc-170">tb</span></span>     | <span data-ttu-id="e86cc-171">multiplicateur de téraoctets</span><span class="sxs-lookup"><span data-stu-id="e86cc-171">terabyte multiplier</span></span> |
| <span data-ttu-id="e86cc-172">gérés</span><span class="sxs-lookup"><span data-stu-id="e86cc-172">pb</span></span>     | <span data-ttu-id="e86cc-173">multiplicateur de pétaoctet</span><span class="sxs-lookup"><span data-stu-id="e86cc-173">petabyte multiplier</span></span> |

<span data-ttu-id="e86cc-174">Il existe deux types de littéraux réels : double et Decimal.</span><span class="sxs-lookup"><span data-stu-id="e86cc-174">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="e86cc-175">Celles-ci sont indiquées par l’absence ou la présence, respectivement, du suffixe de type décimal.</span><span class="sxs-lookup"><span data-stu-id="e86cc-175">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="e86cc-176">PowerShell ne prend pas en charge la représentation littérale d’une `[float]` valeur.</span><span class="sxs-lookup"><span data-stu-id="e86cc-176">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="e86cc-177">Un littéral réel double a le type `[double]` .</span><span class="sxs-lookup"><span data-stu-id="e86cc-177">A double real literal has type `[double]`.</span></span> <span data-ttu-id="e86cc-178">Un littéral réel décimal a le type `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="e86cc-178">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="e86cc-179">Les zéros de fin dans la partie fractionnaire d’un littéral réel décimal sont significatifs.</span><span class="sxs-lookup"><span data-stu-id="e86cc-179">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="e86cc-180">Si la valeur des chiffres de la partie exposant dans un `[double]` littéral réel est inférieure à la valeur minimale prise en charge, la valeur de ce `[double]` littéral réel est 0.</span><span class="sxs-lookup"><span data-stu-id="e86cc-180">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="e86cc-181">Si la valeur des chiffres de la partie exposant dans un `[decimal]` littéral réel est inférieure à la valeur minimale prise en charge, ce littéral est incorrect.</span><span class="sxs-lookup"><span data-stu-id="e86cc-181">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="e86cc-182">Si la valeur des chiffres de la partie exposant dans un `[double]` `[decimal]` littéral réel ou est supérieure à la valeur maximale prise en charge, ce littéral est incorrect.</span><span class="sxs-lookup"><span data-stu-id="e86cc-182">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="e86cc-183">La syntaxe autorise un littéral double réel à avoir un suffixe de type long.</span><span class="sxs-lookup"><span data-stu-id="e86cc-183">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="e86cc-184">PowerShell traite ce cas comme un littéral d’entier dont la valeur est représentée par le type `[long]` .</span><span class="sxs-lookup"><span data-stu-id="e86cc-184">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="e86cc-185">Cette fonctionnalité a été conservée à des fins de compatibilité descendante avec les versions antérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e86cc-185">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="e86cc-186">Toutefois, les programmeurs sont déconseillés d’utiliser des littéraux entiers de ce formulaire, car ils peuvent facilement masquer la valeur réelle du littéral.</span><span class="sxs-lookup"><span data-stu-id="e86cc-186">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="e86cc-187">Par exemple, `1.2L` a la valeur 1, `1.2345e1L` a la valeur 12 et `1.2345e-5L` a la valeur 0, aucune d’entre elles étant immédiatement évidente.</span><span class="sxs-lookup"><span data-stu-id="e86cc-187">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="e86cc-188">Multiplicateurs numériques</span><span class="sxs-lookup"><span data-stu-id="e86cc-188">Numeric multipliers</span></span>

<span data-ttu-id="e86cc-189">Pour des raisons pratiques, les littéraux entiers et réels peuvent contenir un multiplicateur numérique, ce qui indique un ensemble de puissances couramment utilisées de 2.</span><span class="sxs-lookup"><span data-stu-id="e86cc-189">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="e86cc-190">Le multiplicateur numérique peut être écrit dans n’importe quelle combinaison de lettres majuscules ou minuscules.</span><span class="sxs-lookup"><span data-stu-id="e86cc-190">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="e86cc-191">Les suffixes de multiplicateur peuvent être utilisés en combinaison avec `u` les `ul` `l` suffixes de type, et.</span><span class="sxs-lookup"><span data-stu-id="e86cc-191">The multiplier suffixes can be used in combination with the `u`, `ul`, and `l` type suffixes.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="e86cc-192">Exemples de multiplicateur</span><span class="sxs-lookup"><span data-stu-id="e86cc-192">Multiplier examples</span></span>

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

## <a name="numeric-type-accelerators"></a><span data-ttu-id="e86cc-193">Accélérateurs de type numérique</span><span class="sxs-lookup"><span data-stu-id="e86cc-193">Numeric type accelerators</span></span>

<span data-ttu-id="e86cc-194">PowerShell prend en charge les accélérateurs de type suivants :</span><span class="sxs-lookup"><span data-stu-id="e86cc-194">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="e86cc-195">Accélérateur</span><span class="sxs-lookup"><span data-stu-id="e86cc-195">Accelerator</span></span> |         <span data-ttu-id="e86cc-196">Notes</span><span class="sxs-lookup"><span data-stu-id="e86cc-196">Note</span></span>         |           <span data-ttu-id="e86cc-197">Description</span><span class="sxs-lookup"><span data-stu-id="e86cc-197">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="e86cc-198">Byte (non signé)</span><span class="sxs-lookup"><span data-stu-id="e86cc-198">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="e86cc-199">Octet (signé)</span><span class="sxs-lookup"><span data-stu-id="e86cc-199">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="e86cc-200">Entier de 16 bits</span><span class="sxs-lookup"><span data-stu-id="e86cc-200">16-bit integer</span></span>                   |
| `[short]`   | <span data-ttu-id="e86cc-201">alias pour `[int16]`</span><span class="sxs-lookup"><span data-stu-id="e86cc-201">alias for `[int16]`</span></span>  | <span data-ttu-id="e86cc-202">Entier de 16 bits</span><span class="sxs-lookup"><span data-stu-id="e86cc-202">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="e86cc-203">entier 16 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="e86cc-203">16-bit integer (unsigned)</span></span>        |
| `[ushort]`  | <span data-ttu-id="e86cc-204">alias pour `[uint16]`</span><span class="sxs-lookup"><span data-stu-id="e86cc-204">alias for `[uint16]`</span></span> | <span data-ttu-id="e86cc-205">entier 16 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="e86cc-205">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="e86cc-206">Entier de 32 bits</span><span class="sxs-lookup"><span data-stu-id="e86cc-206">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="e86cc-207">alias pour `[int32]`</span><span class="sxs-lookup"><span data-stu-id="e86cc-207">alias for `[int32]`</span></span>  | <span data-ttu-id="e86cc-208">Entier de 32 bits</span><span class="sxs-lookup"><span data-stu-id="e86cc-208">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="e86cc-209">entier 32 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="e86cc-209">32-bit integer (unsigned)</span></span>        |
| `[uint]`    | <span data-ttu-id="e86cc-210">alias pour `[uint32]`</span><span class="sxs-lookup"><span data-stu-id="e86cc-210">alias for `[uint32]`</span></span> | <span data-ttu-id="e86cc-211">entier 32 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="e86cc-211">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="e86cc-212">Entier 64 bits</span><span class="sxs-lookup"><span data-stu-id="e86cc-212">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="e86cc-213">alias pour `[int64]`</span><span class="sxs-lookup"><span data-stu-id="e86cc-213">alias for `[int64]`</span></span>  | <span data-ttu-id="e86cc-214">Entier 64 bits</span><span class="sxs-lookup"><span data-stu-id="e86cc-214">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="e86cc-215">entier 64 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="e86cc-215">64-bit integer (unsigned)</span></span>        |
| `[ulong]`   | <span data-ttu-id="e86cc-216">alias pour `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="e86cc-216">alias for `[uint64]`</span></span> | <span data-ttu-id="e86cc-217">entier 64 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="e86cc-217">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="e86cc-218">Voir [BigInteger, struct][bigint]</span><span class="sxs-lookup"><span data-stu-id="e86cc-218">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="e86cc-219">Virgule flottante simple précision</span><span class="sxs-lookup"><span data-stu-id="e86cc-219">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="e86cc-220">alias pour `[single]`</span><span class="sxs-lookup"><span data-stu-id="e86cc-220">alias for `[single]`</span></span> | <span data-ttu-id="e86cc-221">Virgule flottante simple précision</span><span class="sxs-lookup"><span data-stu-id="e86cc-221">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="e86cc-222">Virgule flottante double précision</span><span class="sxs-lookup"><span data-stu-id="e86cc-222">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="e86cc-223">virgule flottante 128 bits</span><span class="sxs-lookup"><span data-stu-id="e86cc-223">128-bit floating point</span></span>           |

> [!NOTE]
> <span data-ttu-id="e86cc-224">Les accélérateurs de type suivants ont été ajoutés dans PowerShell 6,2 : `[short]` , `[ushort]` ,, `[uint]` `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="e86cc-224">The following type accelerators were added in PowerShell 6.2: `[short]`, `[ushort]`, `[uint]`, `[ulong]`.</span></span>

### <a name="working-with-other-numeric-types"></a><span data-ttu-id="e86cc-225">Utilisation d’autres types numériques</span><span class="sxs-lookup"><span data-stu-id="e86cc-225">Working with other numeric types</span></span>

<span data-ttu-id="e86cc-226">Pour travailler avec d’autres types numériques, vous devez utiliser des accélérateurs de type, ce qui n’est pas sans problèmes.</span><span class="sxs-lookup"><span data-stu-id="e86cc-226">To work with any other numeric types you must use type accelerators, which is not without some problems.</span></span> <span data-ttu-id="e86cc-227">Par exemple, les valeurs entières élevées sont toujours analysées comme double avant d’être converties en un autre type.</span><span class="sxs-lookup"><span data-stu-id="e86cc-227">For example, high integer values are always parsed as double before being cast to any other type.</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="e86cc-228">La valeur est analysée en premier, ce qui perd la précision dans les plages supérieures.</span><span class="sxs-lookup"><span data-stu-id="e86cc-228">The value is parsed as a double first, losing precision in the higher ranges.</span></span>
<span data-ttu-id="e86cc-229">Pour éviter ce problème, entrez des valeurs sous forme de chaînes, puis convertissez-les :</span><span class="sxs-lookup"><span data-stu-id="e86cc-229">To avoid this problem, enter values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

## <a name="examples"></a><span data-ttu-id="e86cc-230">Exemples</span><span class="sxs-lookup"><span data-stu-id="e86cc-230">Examples</span></span>

<span data-ttu-id="e86cc-231">Le tableau suivant contient plusieurs exemples de littéraux numériques et répertorie leur type et leur valeur :</span><span class="sxs-lookup"><span data-stu-id="e86cc-231">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|  <span data-ttu-id="e86cc-232">Nombre</span><span class="sxs-lookup"><span data-stu-id="e86cc-232">Number</span></span>  |  <span data-ttu-id="e86cc-233">Type</span><span class="sxs-lookup"><span data-stu-id="e86cc-233">Type</span></span>   |    <span data-ttu-id="e86cc-234">Valeur</span><span class="sxs-lookup"><span data-stu-id="e86cc-234">Value</span></span>     |
| -------: | ------- | -----------: |
|      <span data-ttu-id="e86cc-235">100</span><span class="sxs-lookup"><span data-stu-id="e86cc-235">100</span></span> | <span data-ttu-id="e86cc-236">Int32</span><span class="sxs-lookup"><span data-stu-id="e86cc-236">Int32</span></span>   |          <span data-ttu-id="e86cc-237">100</span><span class="sxs-lookup"><span data-stu-id="e86cc-237">100</span></span> |
|     <span data-ttu-id="e86cc-238">100D</span><span class="sxs-lookup"><span data-stu-id="e86cc-238">100D</span></span> | <span data-ttu-id="e86cc-239">Decimal</span><span class="sxs-lookup"><span data-stu-id="e86cc-239">Decimal</span></span> |          <span data-ttu-id="e86cc-240">100</span><span class="sxs-lookup"><span data-stu-id="e86cc-240">100</span></span> |
|     <span data-ttu-id="e86cc-241">100l</span><span class="sxs-lookup"><span data-stu-id="e86cc-241">100l</span></span> | <span data-ttu-id="e86cc-242">Int64</span><span class="sxs-lookup"><span data-stu-id="e86cc-242">Int64</span></span>   |          <span data-ttu-id="e86cc-243">100</span><span class="sxs-lookup"><span data-stu-id="e86cc-243">100</span></span> |
|    <span data-ttu-id="e86cc-244">100uL</span><span class="sxs-lookup"><span data-stu-id="e86cc-244">100uL</span></span> | <span data-ttu-id="e86cc-245">UInt64</span><span class="sxs-lookup"><span data-stu-id="e86cc-245">UInt64</span></span>  |          <span data-ttu-id="e86cc-246">100</span><span class="sxs-lookup"><span data-stu-id="e86cc-246">100</span></span> |
|    <span data-ttu-id="e86cc-247">100us</span><span class="sxs-lookup"><span data-stu-id="e86cc-247">100us</span></span> | <span data-ttu-id="e86cc-248">UInt16</span><span class="sxs-lookup"><span data-stu-id="e86cc-248">UInt16</span></span>  |          <span data-ttu-id="e86cc-249">100</span><span class="sxs-lookup"><span data-stu-id="e86cc-249">100</span></span> |
|    <span data-ttu-id="e86cc-250">100uy</span><span class="sxs-lookup"><span data-stu-id="e86cc-250">100uy</span></span> | <span data-ttu-id="e86cc-251">Byte</span><span class="sxs-lookup"><span data-stu-id="e86cc-251">Byte</span></span>    |          <span data-ttu-id="e86cc-252">100</span><span class="sxs-lookup"><span data-stu-id="e86cc-252">100</span></span> |
|     <span data-ttu-id="e86cc-253">100y</span><span class="sxs-lookup"><span data-stu-id="e86cc-253">100y</span></span> | <span data-ttu-id="e86cc-254">SByte</span><span class="sxs-lookup"><span data-stu-id="e86cc-254">SByte</span></span>   |          <span data-ttu-id="e86cc-255">100</span><span class="sxs-lookup"><span data-stu-id="e86cc-255">100</span></span> |
|      <span data-ttu-id="e86cc-256">1e2</span><span class="sxs-lookup"><span data-stu-id="e86cc-256">1e2</span></span> | <span data-ttu-id="e86cc-257">Double</span><span class="sxs-lookup"><span data-stu-id="e86cc-257">Double</span></span>  |          <span data-ttu-id="e86cc-258">100</span><span class="sxs-lookup"><span data-stu-id="e86cc-258">100</span></span> |
|     <span data-ttu-id="e86cc-259">1. E2</span><span class="sxs-lookup"><span data-stu-id="e86cc-259">1.e2</span></span> | <span data-ttu-id="e86cc-260">Double</span><span class="sxs-lookup"><span data-stu-id="e86cc-260">Double</span></span>  |          <span data-ttu-id="e86cc-261">100</span><span class="sxs-lookup"><span data-stu-id="e86cc-261">100</span></span> |
|    <span data-ttu-id="e86cc-262">0x1e2</span><span class="sxs-lookup"><span data-stu-id="e86cc-262">0x1e2</span></span> | <span data-ttu-id="e86cc-263">Int32</span><span class="sxs-lookup"><span data-stu-id="e86cc-263">Int32</span></span>   |          <span data-ttu-id="e86cc-264">482</span><span class="sxs-lookup"><span data-stu-id="e86cc-264">482</span></span> |
|   <span data-ttu-id="e86cc-265">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="e86cc-265">0x1e2L</span></span> | <span data-ttu-id="e86cc-266">Int64</span><span class="sxs-lookup"><span data-stu-id="e86cc-266">Int64</span></span>   |          <span data-ttu-id="e86cc-267">482</span><span class="sxs-lookup"><span data-stu-id="e86cc-267">482</span></span> |
|   <span data-ttu-id="e86cc-268">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="e86cc-268">0x1e2D</span></span> | <span data-ttu-id="e86cc-269">Int32</span><span class="sxs-lookup"><span data-stu-id="e86cc-269">Int32</span></span>   |         <span data-ttu-id="e86cc-270">7725</span><span class="sxs-lookup"><span data-stu-id="e86cc-270">7725</span></span> |
|     <span data-ttu-id="e86cc-271">482D</span><span class="sxs-lookup"><span data-stu-id="e86cc-271">482D</span></span> | <span data-ttu-id="e86cc-272">Decimal</span><span class="sxs-lookup"><span data-stu-id="e86cc-272">Decimal</span></span> |          <span data-ttu-id="e86cc-273">482</span><span class="sxs-lookup"><span data-stu-id="e86cc-273">482</span></span> |
|    <span data-ttu-id="e86cc-274">482gb</span><span class="sxs-lookup"><span data-stu-id="e86cc-274">482gb</span></span> | <span data-ttu-id="e86cc-275">Int64</span><span class="sxs-lookup"><span data-stu-id="e86cc-275">Int64</span></span>   | <span data-ttu-id="e86cc-276">517543559168</span><span class="sxs-lookup"><span data-stu-id="e86cc-276">517543559168</span></span> |
| <span data-ttu-id="e86cc-277">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="e86cc-277">0x1e2lgb</span></span> | <span data-ttu-id="e86cc-278">Int64</span><span class="sxs-lookup"><span data-stu-id="e86cc-278">Int64</span></span>   | <span data-ttu-id="e86cc-279">517543559168</span><span class="sxs-lookup"><span data-stu-id="e86cc-279">517543559168</span></span> |

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="e86cc-280">Commandes qui ressemblent à des littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="e86cc-280">Commands that look like numeric literals</span></span>

<span data-ttu-id="e86cc-281">Toute commande ressemblant à un littéral numérique doit être exécutée à l’aide de l’opérateur `&` d’appel (), sinon elle est interprétée comme un nombre du type associé.</span><span class="sxs-lookup"><span data-stu-id="e86cc-281">Any command that looks like a numeric literal must be executed using the the call operator (`&`), otherwise it is interpreted as a number of the associated type.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="e86cc-282">Accéder aux propriétés et aux méthodes d’objets numériques</span><span class="sxs-lookup"><span data-stu-id="e86cc-282">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="e86cc-283">Pour accéder à un membre d’un littéral numérique, il y a des cas où vous devez placer le littéral entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="e86cc-283">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="e86cc-284">Le littéral n’a pas de virgule décimale</span><span class="sxs-lookup"><span data-stu-id="e86cc-284">The literal does not have a decimal point</span></span>
- <span data-ttu-id="e86cc-285">Le littéral n’a pas de chiffres après la virgule décimale</span><span class="sxs-lookup"><span data-stu-id="e86cc-285">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="e86cc-286">Le littéral n’a pas de suffixe</span><span class="sxs-lookup"><span data-stu-id="e86cc-286">The literal does not have a suffix</span></span>

<span data-ttu-id="e86cc-287">Par exemple, l’exemple suivant échoue :</span><span class="sxs-lookup"><span data-stu-id="e86cc-287">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="e86cc-288">Les exemples suivants fonctionnent :</span><span class="sxs-lookup"><span data-stu-id="e86cc-288">The following examples work:</span></span>

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="e86cc-289">Les deux premiers exemples fonctionnent sans mettre la valeur littérale entre parenthèses, car l’analyseur PowerShell peut déterminer où se termine le littéral numérique et la méthode **GetType** démarre.</span><span class="sxs-lookup"><span data-stu-id="e86cc-289">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
