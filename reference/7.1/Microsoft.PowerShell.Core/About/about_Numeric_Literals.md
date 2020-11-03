---
description: Les littéraux numériques et réels peuvent avoir des suffixes de type et de multiplicateur.
Locale: en-US
ms.date: 04/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos des littéraux numériques
ms.openlocfilehash: 25518b80f87c90c59829bb575b059f0efcadd566
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208342"
---
# <a name="about-numeric-literals"></a><span data-ttu-id="c0adf-103">À propos des littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="c0adf-103">About numeric literals</span></span>

<span data-ttu-id="c0adf-104">Il existe deux types de littéraux numériques : entier et réel.</span><span class="sxs-lookup"><span data-stu-id="c0adf-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="c0adf-105">Les deux peuvent avoir des suffixes de type et multiplicateur.</span><span class="sxs-lookup"><span data-stu-id="c0adf-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="c0adf-106">Littéraux d'entier</span><span class="sxs-lookup"><span data-stu-id="c0adf-106">Integer literals</span></span>

<span data-ttu-id="c0adf-107">Les littéraux entiers peuvent être écrits en notation décimale, hexadécimale ou binaire.</span><span class="sxs-lookup"><span data-stu-id="c0adf-107">Integer literals can be written in decimal, hexadecimal, or binary notation.</span></span>
<span data-ttu-id="c0adf-108">Les littéraux hexadécimaux sont préfixés par `0x` et les littéraux binaires sont préfixés avec `0b` pour les distinguer des nombres décimaux.</span><span class="sxs-lookup"><span data-stu-id="c0adf-108">Hexadecimal literals are prefixed with `0x` and binary literals are prefixed with `0b` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="c0adf-109">Les littéraux entiers peuvent avoir un suffixe de type et un suffixe multiplicateur.</span><span class="sxs-lookup"><span data-stu-id="c0adf-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="c0adf-110">Suffixe</span><span class="sxs-lookup"><span data-stu-id="c0adf-110">Suffix</span></span> |            <span data-ttu-id="c0adf-111">Signification</span><span class="sxs-lookup"><span data-stu-id="c0adf-111">Meaning</span></span>             |          <span data-ttu-id="c0adf-112">Notes</span><span class="sxs-lookup"><span data-stu-id="c0adf-112">Note</span></span>           |
| ------ | ------------------------------ | ----------------------- |
| <span data-ttu-id="c0adf-113">o</span><span class="sxs-lookup"><span data-stu-id="c0adf-113">y</span></span>      | <span data-ttu-id="c0adf-114">type de données Byte signé</span><span class="sxs-lookup"><span data-stu-id="c0adf-114">signed byte data type</span></span>          | <span data-ttu-id="c0adf-115">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="c0adf-115">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="c0adf-116">uy</span><span class="sxs-lookup"><span data-stu-id="c0adf-116">uy</span></span>     | <span data-ttu-id="c0adf-117">type de données Byte non signé</span><span class="sxs-lookup"><span data-stu-id="c0adf-117">unsigned byte data type</span></span>        | <span data-ttu-id="c0adf-118">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="c0adf-118">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="c0adf-119">s</span><span class="sxs-lookup"><span data-stu-id="c0adf-119">s</span></span>      | <span data-ttu-id="c0adf-120">short (type de données)</span><span class="sxs-lookup"><span data-stu-id="c0adf-120">short data type</span></span>                | <span data-ttu-id="c0adf-121">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="c0adf-121">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="c0adf-122">us</span><span class="sxs-lookup"><span data-stu-id="c0adf-122">us</span></span>     | <span data-ttu-id="c0adf-123">type de données Short non signé</span><span class="sxs-lookup"><span data-stu-id="c0adf-123">unsigned short data type</span></span>       | <span data-ttu-id="c0adf-124">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="c0adf-124">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="c0adf-125">l</span><span class="sxs-lookup"><span data-stu-id="c0adf-125">l</span></span>      | <span data-ttu-id="c0adf-126">long (type de données)</span><span class="sxs-lookup"><span data-stu-id="c0adf-126">long data type</span></span>                 |                         |
| <span data-ttu-id="c0adf-127">u</span><span class="sxs-lookup"><span data-stu-id="c0adf-127">u</span></span>      | <span data-ttu-id="c0adf-128">type de données int ou long non signé</span><span class="sxs-lookup"><span data-stu-id="c0adf-128">unsigned int or long data type</span></span> | <span data-ttu-id="c0adf-129">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="c0adf-129">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="c0adf-130">ul</span><span class="sxs-lookup"><span data-stu-id="c0adf-130">ul</span></span>     | <span data-ttu-id="c0adf-131">type de données long non signé</span><span class="sxs-lookup"><span data-stu-id="c0adf-131">unsigned long data type</span></span>        | <span data-ttu-id="c0adf-132">Ajouté dans PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="c0adf-132">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="c0adf-133">n</span><span class="sxs-lookup"><span data-stu-id="c0adf-133">n</span></span>      | <span data-ttu-id="c0adf-134">BigInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="c0adf-134">BigInteger data type</span></span>           | <span data-ttu-id="c0adf-135">Ajouté dans PowerShell 7,0</span><span class="sxs-lookup"><span data-stu-id="c0adf-135">Added in PowerShell 7.0</span></span> |
| <span data-ttu-id="c0adf-136">kb</span><span class="sxs-lookup"><span data-stu-id="c0adf-136">kb</span></span>     | <span data-ttu-id="c0adf-137">multiplicateur de kilo-octets</span><span class="sxs-lookup"><span data-stu-id="c0adf-137">kilobyte multiplier</span></span>            |                         |
| <span data-ttu-id="c0adf-138">mb</span><span class="sxs-lookup"><span data-stu-id="c0adf-138">mb</span></span>     | <span data-ttu-id="c0adf-139">multiplicateur de mégaoctets</span><span class="sxs-lookup"><span data-stu-id="c0adf-139">megabyte multiplier</span></span>            |                         |
| <span data-ttu-id="c0adf-140">moins</span><span class="sxs-lookup"><span data-stu-id="c0adf-140">gb</span></span>     | <span data-ttu-id="c0adf-141">multiplicateur de gigaoctets</span><span class="sxs-lookup"><span data-stu-id="c0adf-141">gigabyte multiplier</span></span>            |                         |
| <span data-ttu-id="c0adf-142">to</span><span class="sxs-lookup"><span data-stu-id="c0adf-142">tb</span></span>     | <span data-ttu-id="c0adf-143">multiplicateur de téraoctets</span><span class="sxs-lookup"><span data-stu-id="c0adf-143">terabyte multiplier</span></span>            |                         |
| <span data-ttu-id="c0adf-144">gérés</span><span class="sxs-lookup"><span data-stu-id="c0adf-144">pb</span></span>     | <span data-ttu-id="c0adf-145">multiplicateur de pétaoctet</span><span class="sxs-lookup"><span data-stu-id="c0adf-145">petabyte multiplier</span></span>            |                         |

<span data-ttu-id="c0adf-146">Le type d’un littéral entier est déterminé par sa valeur, le suffixe de type et le suffixe multiplicateur numérique.</span><span class="sxs-lookup"><span data-stu-id="c0adf-146">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="c0adf-147">Pour un littéral d’entier sans suffixe de type :</span><span class="sxs-lookup"><span data-stu-id="c0adf-147">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="c0adf-148">Si la valeur peut être représentée par le type `[int]` , il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="c0adf-148">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="c0adf-149">Sinon, si la valeur peut être représentée par le type `[long]` , il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="c0adf-149">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="c0adf-150">Sinon, si la valeur peut être représentée par le type `[decimal]` , il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="c0adf-150">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="c0adf-151">Dans le cas contraire, il est représenté par le type `[double]` .</span><span class="sxs-lookup"><span data-stu-id="c0adf-151">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="c0adf-152">Pour un littéral d’entier avec un suffixe de type :</span><span class="sxs-lookup"><span data-stu-id="c0adf-152">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="c0adf-153">Si le suffixe de type est `u` et que la valeur peut être représentée par le type, `[uint]` son type est `[uint]` .</span><span class="sxs-lookup"><span data-stu-id="c0adf-153">If the type suffix is `u` and the value can be represented by type `[uint]` then its type is `[uint]`.</span></span>
- <span data-ttu-id="c0adf-154">Si le suffixe de type est `u` et que la valeur peut être représentée par le type, `[ulong]` son type est `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="c0adf-154">If the type suffix is `u` and the value can be represented by type `[ulong]` then its type is `[ulong]`.</span></span>
- <span data-ttu-id="c0adf-155">Si sa valeur peut être représentée par le type spécifié, alors il s’agit de son type.</span><span class="sxs-lookup"><span data-stu-id="c0adf-155">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="c0adf-156">Dans le cas contraire, ce littéral est incorrect.</span><span class="sxs-lookup"><span data-stu-id="c0adf-156">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="c0adf-157">Littéraux réels</span><span class="sxs-lookup"><span data-stu-id="c0adf-157">Real literals</span></span>

<span data-ttu-id="c0adf-158">Les littéraux réels ne peuvent être écrits qu’en notation décimale.</span><span class="sxs-lookup"><span data-stu-id="c0adf-158">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="c0adf-159">Cette notation peut inclure des valeurs fractionnaires à la suite d’une virgule décimale et d’une notation scientifique à l’aide d’une partie exponentielle.</span><span class="sxs-lookup"><span data-stu-id="c0adf-159">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="c0adf-160">La partie exponentielle comprend un « e » suivi d’un signe facultatif (+/-) et d’un nombre représentant l’exposant.</span><span class="sxs-lookup"><span data-stu-id="c0adf-160">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="c0adf-161">Par exemple, la valeur littérale `1e2` est égale à la valeur numérique 100.</span><span class="sxs-lookup"><span data-stu-id="c0adf-161">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="c0adf-162">Les littéraux réels peuvent avoir un suffixe de type et un suffixe multiplicateur.</span><span class="sxs-lookup"><span data-stu-id="c0adf-162">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="c0adf-163">Suffixe</span><span class="sxs-lookup"><span data-stu-id="c0adf-163">Suffix</span></span> |       <span data-ttu-id="c0adf-164">Signification</span><span class="sxs-lookup"><span data-stu-id="c0adf-164">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="c0adf-165">d</span><span class="sxs-lookup"><span data-stu-id="c0adf-165">d</span></span>      | <span data-ttu-id="c0adf-166">type de données decimal</span><span class="sxs-lookup"><span data-stu-id="c0adf-166">decimal data type</span></span>   |
| <span data-ttu-id="c0adf-167">kb</span><span class="sxs-lookup"><span data-stu-id="c0adf-167">kb</span></span>     | <span data-ttu-id="c0adf-168">multiplicateur de kilo-octets</span><span class="sxs-lookup"><span data-stu-id="c0adf-168">kilobyte multiplier</span></span> |
| <span data-ttu-id="c0adf-169">mb</span><span class="sxs-lookup"><span data-stu-id="c0adf-169">mb</span></span>     | <span data-ttu-id="c0adf-170">multiplicateur de mégaoctets</span><span class="sxs-lookup"><span data-stu-id="c0adf-170">megabyte multiplier</span></span> |
| <span data-ttu-id="c0adf-171">moins</span><span class="sxs-lookup"><span data-stu-id="c0adf-171">gb</span></span>     | <span data-ttu-id="c0adf-172">multiplicateur de gigaoctets</span><span class="sxs-lookup"><span data-stu-id="c0adf-172">gigabyte multiplier</span></span> |
| <span data-ttu-id="c0adf-173">to</span><span class="sxs-lookup"><span data-stu-id="c0adf-173">tb</span></span>     | <span data-ttu-id="c0adf-174">multiplicateur de téraoctets</span><span class="sxs-lookup"><span data-stu-id="c0adf-174">terabyte multiplier</span></span> |
| <span data-ttu-id="c0adf-175">gérés</span><span class="sxs-lookup"><span data-stu-id="c0adf-175">pb</span></span>     | <span data-ttu-id="c0adf-176">multiplicateur de pétaoctet</span><span class="sxs-lookup"><span data-stu-id="c0adf-176">petabyte multiplier</span></span> |

<span data-ttu-id="c0adf-177">Il existe deux types de littéraux réels : double et Decimal.</span><span class="sxs-lookup"><span data-stu-id="c0adf-177">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="c0adf-178">Celles-ci sont indiquées par l’absence ou la présence, respectivement, du suffixe de type décimal.</span><span class="sxs-lookup"><span data-stu-id="c0adf-178">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="c0adf-179">PowerShell ne prend pas en charge la représentation littérale d’une `[float]` valeur.</span><span class="sxs-lookup"><span data-stu-id="c0adf-179">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="c0adf-180">Un littéral réel double a le type `[double]` .</span><span class="sxs-lookup"><span data-stu-id="c0adf-180">A double real literal has type `[double]`.</span></span> <span data-ttu-id="c0adf-181">Un littéral réel décimal a le type `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="c0adf-181">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="c0adf-182">Les zéros de fin dans la partie fractionnaire d’un littéral réel décimal sont significatifs.</span><span class="sxs-lookup"><span data-stu-id="c0adf-182">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="c0adf-183">Si la valeur des chiffres de la partie exposant dans un `[double]` littéral réel est inférieure à la valeur minimale prise en charge, la valeur de ce `[double]` littéral réel est 0.</span><span class="sxs-lookup"><span data-stu-id="c0adf-183">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="c0adf-184">Si la valeur des chiffres de la partie exposant dans un `[decimal]` littéral réel est inférieure à la valeur minimale prise en charge, ce littéral est incorrect.</span><span class="sxs-lookup"><span data-stu-id="c0adf-184">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="c0adf-185">Si la valeur des chiffres de la partie exposant dans un `[double]` `[decimal]` littéral réel ou est supérieure à la valeur maximale prise en charge, ce littéral est incorrect.</span><span class="sxs-lookup"><span data-stu-id="c0adf-185">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="c0adf-186">La syntaxe autorise un littéral double réel à avoir un suffixe de type long.</span><span class="sxs-lookup"><span data-stu-id="c0adf-186">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="c0adf-187">PowerShell traite ce cas comme un littéral d’entier dont la valeur est représentée par le type `[long]` .</span><span class="sxs-lookup"><span data-stu-id="c0adf-187">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="c0adf-188">Cette fonctionnalité a été conservée à des fins de compatibilité descendante avec les versions antérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0adf-188">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="c0adf-189">Toutefois, les programmeurs sont déconseillés d’utiliser des littéraux entiers de ce formulaire, car ils peuvent facilement masquer la valeur réelle du littéral.</span><span class="sxs-lookup"><span data-stu-id="c0adf-189">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="c0adf-190">Par exemple, `1.2L` a la valeur 1, `1.2345e1L` a la valeur 12 et `1.2345e-5L` a la valeur 0, aucune d’entre elles étant immédiatement évidente.</span><span class="sxs-lookup"><span data-stu-id="c0adf-190">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="c0adf-191">Multiplicateurs numériques</span><span class="sxs-lookup"><span data-stu-id="c0adf-191">Numeric multipliers</span></span>

<span data-ttu-id="c0adf-192">Pour des raisons pratiques, les littéraux entiers et réels peuvent contenir un multiplicateur numérique, ce qui indique un ensemble de puissances couramment utilisées de 2.</span><span class="sxs-lookup"><span data-stu-id="c0adf-192">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="c0adf-193">Le multiplicateur numérique peut être écrit dans n’importe quelle combinaison de lettres majuscules ou minuscules.</span><span class="sxs-lookup"><span data-stu-id="c0adf-193">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="c0adf-194">Les suffixes de multiplicateur peuvent être utilisés en combinaison avec n’importe quel suffixe de type, mais doivent être présents après le suffixe de type.</span><span class="sxs-lookup"><span data-stu-id="c0adf-194">The multiplier suffixes can be used in combination with any type suffixes, but must be present after the type suffix.</span></span> <span data-ttu-id="c0adf-195">Par exemple, le littéral `100gbL` est incorrect, mais le littéral `100Lgb` est valide.</span><span class="sxs-lookup"><span data-stu-id="c0adf-195">For example, the literal `100gbL` is malformed, but the literal `100Lgb` is valid.</span></span>

<span data-ttu-id="c0adf-196">Si un multiplicateur crée une valeur qui dépasse les valeurs possibles pour le type numérique que le suffixe spécifie, le littéral est incorrect.</span><span class="sxs-lookup"><span data-stu-id="c0adf-196">If a multiplier creates a value that exceeds the possible values for the numeric type that the suffix specifies, the literal is malformed.</span></span> <span data-ttu-id="c0adf-197">Par exemple, le littéral `1usgb` est incorrect, car la valeur `1gb` est supérieure à ce qui est autorisé pour le `[ushort]` type spécifié par le `us` suffixe.</span><span class="sxs-lookup"><span data-stu-id="c0adf-197">For example, the literal `1usgb` is malformed, because the value `1gb` is larger than what is permitted for the `[ushort]` type specified by the `us` suffix.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="c0adf-198">Exemples de multiplicateur</span><span class="sxs-lookup"><span data-stu-id="c0adf-198">Multiplier examples</span></span>

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

## <a name="numeric-type-accelerators"></a><span data-ttu-id="c0adf-199">Accélérateurs de type numérique</span><span class="sxs-lookup"><span data-stu-id="c0adf-199">Numeric type accelerators</span></span>

<span data-ttu-id="c0adf-200">PowerShell prend en charge les accélérateurs de type suivants :</span><span class="sxs-lookup"><span data-stu-id="c0adf-200">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="c0adf-201">Accélérateur</span><span class="sxs-lookup"><span data-stu-id="c0adf-201">Accelerator</span></span> |         <span data-ttu-id="c0adf-202">Notes</span><span class="sxs-lookup"><span data-stu-id="c0adf-202">Note</span></span>         |           <span data-ttu-id="c0adf-203">Description</span><span class="sxs-lookup"><span data-stu-id="c0adf-203">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="c0adf-204">Byte (non signé)</span><span class="sxs-lookup"><span data-stu-id="c0adf-204">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="c0adf-205">Octet (signé)</span><span class="sxs-lookup"><span data-stu-id="c0adf-205">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="c0adf-206">Entier de 16 bits</span><span class="sxs-lookup"><span data-stu-id="c0adf-206">16-bit integer</span></span>                   |
| `[short]`   | <span data-ttu-id="c0adf-207">alias pour `[int16]`</span><span class="sxs-lookup"><span data-stu-id="c0adf-207">alias for `[int16]`</span></span>  | <span data-ttu-id="c0adf-208">Entier de 16 bits</span><span class="sxs-lookup"><span data-stu-id="c0adf-208">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="c0adf-209">entier 16 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="c0adf-209">16-bit integer (unsigned)</span></span>        |
| `[ushort]`  | <span data-ttu-id="c0adf-210">alias pour `[uint16]`</span><span class="sxs-lookup"><span data-stu-id="c0adf-210">alias for `[uint16]`</span></span> | <span data-ttu-id="c0adf-211">entier 16 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="c0adf-211">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="c0adf-212">Entier de 32 bits</span><span class="sxs-lookup"><span data-stu-id="c0adf-212">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="c0adf-213">alias pour `[int32]`</span><span class="sxs-lookup"><span data-stu-id="c0adf-213">alias for `[int32]`</span></span>  | <span data-ttu-id="c0adf-214">Entier de 32 bits</span><span class="sxs-lookup"><span data-stu-id="c0adf-214">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="c0adf-215">entier 32 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="c0adf-215">32-bit integer (unsigned)</span></span>        |
| `[uint]`    | <span data-ttu-id="c0adf-216">alias pour `[uint32]`</span><span class="sxs-lookup"><span data-stu-id="c0adf-216">alias for `[uint32]`</span></span> | <span data-ttu-id="c0adf-217">entier 32 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="c0adf-217">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="c0adf-218">Entier 64 bits</span><span class="sxs-lookup"><span data-stu-id="c0adf-218">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="c0adf-219">alias pour `[int64]`</span><span class="sxs-lookup"><span data-stu-id="c0adf-219">alias for `[int64]`</span></span>  | <span data-ttu-id="c0adf-220">Entier 64 bits</span><span class="sxs-lookup"><span data-stu-id="c0adf-220">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="c0adf-221">entier 64 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="c0adf-221">64-bit integer (unsigned)</span></span>        |
| `[ulong]`   | <span data-ttu-id="c0adf-222">alias pour `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="c0adf-222">alias for `[uint64]`</span></span> | <span data-ttu-id="c0adf-223">entier 64 bits (non signé)</span><span class="sxs-lookup"><span data-stu-id="c0adf-223">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="c0adf-224">Voir [BigInteger, struct][bigint]</span><span class="sxs-lookup"><span data-stu-id="c0adf-224">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="c0adf-225">Virgule flottante simple précision</span><span class="sxs-lookup"><span data-stu-id="c0adf-225">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="c0adf-226">alias pour `[single]`</span><span class="sxs-lookup"><span data-stu-id="c0adf-226">alias for `[single]`</span></span> | <span data-ttu-id="c0adf-227">Virgule flottante simple précision</span><span class="sxs-lookup"><span data-stu-id="c0adf-227">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="c0adf-228">Virgule flottante double précision</span><span class="sxs-lookup"><span data-stu-id="c0adf-228">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="c0adf-229">virgule flottante 128 bits</span><span class="sxs-lookup"><span data-stu-id="c0adf-229">128-bit floating point</span></span>           |

> [!NOTE]
> <span data-ttu-id="c0adf-230">Les accélérateurs de type suivants ont été ajoutés dans PowerShell 6,2 : `[short]` , `[ushort]` ,, `[uint]` `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="c0adf-230">The following type accelerators were added in PowerShell 6.2: `[short]`, `[ushort]`, `[uint]`, `[ulong]`.</span></span>

## <a name="examples"></a><span data-ttu-id="c0adf-231">Exemples</span><span class="sxs-lookup"><span data-stu-id="c0adf-231">Examples</span></span>

<span data-ttu-id="c0adf-232">Le tableau suivant contient plusieurs exemples de littéraux numériques et répertorie leur type et leur valeur :</span><span class="sxs-lookup"><span data-stu-id="c0adf-232">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|   <span data-ttu-id="c0adf-233">Number</span><span class="sxs-lookup"><span data-stu-id="c0adf-233">Number</span></span>    |    <span data-ttu-id="c0adf-234">Type</span><span class="sxs-lookup"><span data-stu-id="c0adf-234">Type</span></span>    |    <span data-ttu-id="c0adf-235">Valeur</span><span class="sxs-lookup"><span data-stu-id="c0adf-235">Value</span></span>     |
| ----------: | ---------- | -----------: |
|         <span data-ttu-id="c0adf-236">100</span><span class="sxs-lookup"><span data-stu-id="c0adf-236">100</span></span> | <span data-ttu-id="c0adf-237">Int32</span><span class="sxs-lookup"><span data-stu-id="c0adf-237">Int32</span></span>      |          <span data-ttu-id="c0adf-238">100</span><span class="sxs-lookup"><span data-stu-id="c0adf-238">100</span></span> |
|        <span data-ttu-id="c0adf-239">100u</span><span class="sxs-lookup"><span data-stu-id="c0adf-239">100u</span></span> | <span data-ttu-id="c0adf-240">UInt32</span><span class="sxs-lookup"><span data-stu-id="c0adf-240">UInt32</span></span>     |          <span data-ttu-id="c0adf-241">100</span><span class="sxs-lookup"><span data-stu-id="c0adf-241">100</span></span> |
|        <span data-ttu-id="c0adf-242">100D</span><span class="sxs-lookup"><span data-stu-id="c0adf-242">100D</span></span> | <span data-ttu-id="c0adf-243">Decimal</span><span class="sxs-lookup"><span data-stu-id="c0adf-243">Decimal</span></span>    |          <span data-ttu-id="c0adf-244">100</span><span class="sxs-lookup"><span data-stu-id="c0adf-244">100</span></span> |
|        <span data-ttu-id="c0adf-245">100l</span><span class="sxs-lookup"><span data-stu-id="c0adf-245">100l</span></span> | <span data-ttu-id="c0adf-246">Int64</span><span class="sxs-lookup"><span data-stu-id="c0adf-246">Int64</span></span>      |          <span data-ttu-id="c0adf-247">100</span><span class="sxs-lookup"><span data-stu-id="c0adf-247">100</span></span> |
|       <span data-ttu-id="c0adf-248">100uL</span><span class="sxs-lookup"><span data-stu-id="c0adf-248">100uL</span></span> | <span data-ttu-id="c0adf-249">UInt64</span><span class="sxs-lookup"><span data-stu-id="c0adf-249">UInt64</span></span>     |          <span data-ttu-id="c0adf-250">100</span><span class="sxs-lookup"><span data-stu-id="c0adf-250">100</span></span> |
|       <span data-ttu-id="c0adf-251">100us</span><span class="sxs-lookup"><span data-stu-id="c0adf-251">100us</span></span> | <span data-ttu-id="c0adf-252">UInt16</span><span class="sxs-lookup"><span data-stu-id="c0adf-252">UInt16</span></span>     |          <span data-ttu-id="c0adf-253">100</span><span class="sxs-lookup"><span data-stu-id="c0adf-253">100</span></span> |
|       <span data-ttu-id="c0adf-254">100uy</span><span class="sxs-lookup"><span data-stu-id="c0adf-254">100uy</span></span> | <span data-ttu-id="c0adf-255">Byte</span><span class="sxs-lookup"><span data-stu-id="c0adf-255">Byte</span></span>       |          <span data-ttu-id="c0adf-256">100</span><span class="sxs-lookup"><span data-stu-id="c0adf-256">100</span></span> |
|        <span data-ttu-id="c0adf-257">100y</span><span class="sxs-lookup"><span data-stu-id="c0adf-257">100y</span></span> | <span data-ttu-id="c0adf-258">SByte</span><span class="sxs-lookup"><span data-stu-id="c0adf-258">SByte</span></span>      |          <span data-ttu-id="c0adf-259">100</span><span class="sxs-lookup"><span data-stu-id="c0adf-259">100</span></span> |
|         <span data-ttu-id="c0adf-260">1e2</span><span class="sxs-lookup"><span data-stu-id="c0adf-260">1e2</span></span> | <span data-ttu-id="c0adf-261">Double</span><span class="sxs-lookup"><span data-stu-id="c0adf-261">Double</span></span>     |          <span data-ttu-id="c0adf-262">100</span><span class="sxs-lookup"><span data-stu-id="c0adf-262">100</span></span> |
|        <span data-ttu-id="c0adf-263">1. E2</span><span class="sxs-lookup"><span data-stu-id="c0adf-263">1.e2</span></span> | <span data-ttu-id="c0adf-264">Double</span><span class="sxs-lookup"><span data-stu-id="c0adf-264">Double</span></span>     |          <span data-ttu-id="c0adf-265">100</span><span class="sxs-lookup"><span data-stu-id="c0adf-265">100</span></span> |
|       <span data-ttu-id="c0adf-266">0x1e2</span><span class="sxs-lookup"><span data-stu-id="c0adf-266">0x1e2</span></span> | <span data-ttu-id="c0adf-267">Int32</span><span class="sxs-lookup"><span data-stu-id="c0adf-267">Int32</span></span>      |          <span data-ttu-id="c0adf-268">482</span><span class="sxs-lookup"><span data-stu-id="c0adf-268">482</span></span> |
|      <span data-ttu-id="c0adf-269">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="c0adf-269">0x1e2L</span></span> | <span data-ttu-id="c0adf-270">Int64</span><span class="sxs-lookup"><span data-stu-id="c0adf-270">Int64</span></span>      |          <span data-ttu-id="c0adf-271">482</span><span class="sxs-lookup"><span data-stu-id="c0adf-271">482</span></span> |
|      <span data-ttu-id="c0adf-272">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="c0adf-272">0x1e2D</span></span> | <span data-ttu-id="c0adf-273">Int32</span><span class="sxs-lookup"><span data-stu-id="c0adf-273">Int32</span></span>      |         <span data-ttu-id="c0adf-274">7725</span><span class="sxs-lookup"><span data-stu-id="c0adf-274">7725</span></span> |
|        <span data-ttu-id="c0adf-275">482D</span><span class="sxs-lookup"><span data-stu-id="c0adf-275">482D</span></span> | <span data-ttu-id="c0adf-276">Decimal</span><span class="sxs-lookup"><span data-stu-id="c0adf-276">Decimal</span></span>    |          <span data-ttu-id="c0adf-277">482</span><span class="sxs-lookup"><span data-stu-id="c0adf-277">482</span></span> |
|       <span data-ttu-id="c0adf-278">482gb</span><span class="sxs-lookup"><span data-stu-id="c0adf-278">482gb</span></span> | <span data-ttu-id="c0adf-279">Int64</span><span class="sxs-lookup"><span data-stu-id="c0adf-279">Int64</span></span>      | <span data-ttu-id="c0adf-280">517543559168</span><span class="sxs-lookup"><span data-stu-id="c0adf-280">517543559168</span></span> |
|      <span data-ttu-id="c0adf-281">482ngb</span><span class="sxs-lookup"><span data-stu-id="c0adf-281">482ngb</span></span> | <span data-ttu-id="c0adf-282">BigInteger</span><span class="sxs-lookup"><span data-stu-id="c0adf-282">BigInteger</span></span> | <span data-ttu-id="c0adf-283">517543559168</span><span class="sxs-lookup"><span data-stu-id="c0adf-283">517543559168</span></span> |
|    <span data-ttu-id="c0adf-284">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="c0adf-284">0x1e2lgb</span></span> | <span data-ttu-id="c0adf-285">Int64</span><span class="sxs-lookup"><span data-stu-id="c0adf-285">Int64</span></span>      | <span data-ttu-id="c0adf-286">517543559168</span><span class="sxs-lookup"><span data-stu-id="c0adf-286">517543559168</span></span> |
|   <span data-ttu-id="c0adf-287">0b1011011</span><span class="sxs-lookup"><span data-stu-id="c0adf-287">0b1011011</span></span> | <span data-ttu-id="c0adf-288">Int32</span><span class="sxs-lookup"><span data-stu-id="c0adf-288">Int32</span></span>      |           <span data-ttu-id="c0adf-289">91</span><span class="sxs-lookup"><span data-stu-id="c0adf-289">91</span></span> |
|     <span data-ttu-id="c0adf-290">0xFFFFs</span><span class="sxs-lookup"><span data-stu-id="c0adf-290">0xFFFFs</span></span> | <span data-ttu-id="c0adf-291">Int16</span><span class="sxs-lookup"><span data-stu-id="c0adf-291">Int16</span></span>      |           <span data-ttu-id="c0adf-292">-1</span><span class="sxs-lookup"><span data-stu-id="c0adf-292">-1</span></span> |
|  <span data-ttu-id="c0adf-293">Égale</span><span class="sxs-lookup"><span data-stu-id="c0adf-293">0xFFFFFFFF</span></span> | <span data-ttu-id="c0adf-294">Int32</span><span class="sxs-lookup"><span data-stu-id="c0adf-294">Int32</span></span>      |           <span data-ttu-id="c0adf-295">-1</span><span class="sxs-lookup"><span data-stu-id="c0adf-295">-1</span></span> |
| <span data-ttu-id="c0adf-296">-0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="c0adf-296">-0xFFFFFFFF</span></span> | <span data-ttu-id="c0adf-297">Int32</span><span class="sxs-lookup"><span data-stu-id="c0adf-297">Int32</span></span>      |            <span data-ttu-id="c0adf-298">1</span><span class="sxs-lookup"><span data-stu-id="c0adf-298">1</span></span> |
| <span data-ttu-id="c0adf-299">0xFFFFFFFFu</span><span class="sxs-lookup"><span data-stu-id="c0adf-299">0xFFFFFFFFu</span></span> | <span data-ttu-id="c0adf-300">UInt32</span><span class="sxs-lookup"><span data-stu-id="c0adf-300">UInt32</span></span>     |   <span data-ttu-id="c0adf-301">4294967295</span><span class="sxs-lookup"><span data-stu-id="c0adf-301">4294967295</span></span> |

### <a name="working-with-binary-or-hexadecimal-numbers"></a><span data-ttu-id="c0adf-302">Utilisation de nombres binaires ou hexadécimaux</span><span class="sxs-lookup"><span data-stu-id="c0adf-302">Working with binary or hexadecimal numbers</span></span>

<span data-ttu-id="c0adf-303">Les littéraux binaires ou hexadécimaux trop grands peuvent retourner au `[bigint]` lieu d’échouer à l’analyse, si et seulement si le `n` suffixe est spécifié.</span><span class="sxs-lookup"><span data-stu-id="c0adf-303">Overly large binary or hexadecimal literals can return as `[bigint]` rather than failing the parse, if and only if the `n` suffix is specified.</span></span> <span data-ttu-id="c0adf-304">Les bits de signe sont toujours respectés au-dessus des `[decimal]` plages paires, mais :</span><span class="sxs-lookup"><span data-stu-id="c0adf-304">Sign bits are still respected above even `[decimal]` ranges, however:</span></span>

- <span data-ttu-id="c0adf-305">Si une chaîne binaire est un multiple de 8 bits de long, le bit le plus élevé est traité comme le bit de signe.</span><span class="sxs-lookup"><span data-stu-id="c0adf-305">If a binary string is some multiple of 8 bits long, the highest bit is treated as the sign bit.</span></span>
- <span data-ttu-id="c0adf-306">Si une chaîne hexadécimale, dont la longueur est un multiple de 8, a le premier chiffre avec 8 ou plus, le chiffre est traité comme négatif.</span><span class="sxs-lookup"><span data-stu-id="c0adf-306">If a hex string, which has a length that is a multiple of 8, has the first digit with 8 or higher, the numeral is treated as negative.</span></span>

<span data-ttu-id="c0adf-307">La spécification d’un suffixe non signé sur des littéraux binaires et hexadécimaux ignore les bits de signe.</span><span class="sxs-lookup"><span data-stu-id="c0adf-307">Specifying an unsigned suffix on binary and hex literals ignores sign bits.</span></span> <span data-ttu-id="c0adf-308">Par exemple, `0xFFFFFFFF` retourne `-1` , mais `0xFFFFFFFFu` retourne le `[uint]::MaxValue` de 4294967295.</span><span class="sxs-lookup"><span data-stu-id="c0adf-308">For example, `0xFFFFFFFF` returns `-1`, but `0xFFFFFFFFu` returns the `[uint]::MaxValue` of 4294967295.</span></span>

<span data-ttu-id="c0adf-309">Dans PowerShell 7,1, l’utilisation d’un suffixe de type sur un littéral hexadécimal retourne désormais une valeur signée de ce type.</span><span class="sxs-lookup"><span data-stu-id="c0adf-309">In PowerShell 7.1, using a type suffix on a hex literal now returns a signed value of that type.</span></span> <span data-ttu-id="c0adf-310">Par exemple, dans PowerShell 7,0, l’expression `0xFFFFs` retourne une erreur, car la valeur positive est trop grande pour un `[int16]` type.</span><span class="sxs-lookup"><span data-stu-id="c0adf-310">For example, in PowerShell 7.0 the expression `0xFFFFs` returns an error because the positive value is too large for an `[int16]` type.</span></span>
<span data-ttu-id="c0adf-311">PowerShell 7,1 interprète cela comme étant `-1` un `[int16]` type.</span><span class="sxs-lookup"><span data-stu-id="c0adf-311">PowerShell 7.1 interprets this as `-1` that is an `[int16]` type.</span></span>

<span data-ttu-id="c0adf-312">Le préfixe du littéral avec un `0` contournera cette opération et sera traité comme non signé.</span><span class="sxs-lookup"><span data-stu-id="c0adf-312">Prefixing the literal with a `0` will bypass this and be treated as unsigned.</span></span>
<span data-ttu-id="c0adf-313">Par exemple : `0b011111111`.</span><span class="sxs-lookup"><span data-stu-id="c0adf-313">For example: `0b011111111`.</span></span> <span data-ttu-id="c0adf-314">Cela peut être nécessaire lors de l’utilisation de littéraux dans la `[bigint]` plage, car les `u` `n` suffixes et ne peuvent pas être combinés.</span><span class="sxs-lookup"><span data-stu-id="c0adf-314">This can be necessary when working with literals in the `[bigint]` range, as the `u` and `n` suffixes cannot be combined.</span></span>

<span data-ttu-id="c0adf-315">Vous pouvez également nier les littéraux binaires et hexadécimaux à l’aide du `-` préfixe.</span><span class="sxs-lookup"><span data-stu-id="c0adf-315">You can also negate binary and hex literals using the `-` prefix.</span></span> <span data-ttu-id="c0adf-316">Cela peut entraîner un nombre positif, car les bits de signe sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="c0adf-316">This can result in a positive number since sign bits are permitted.</span></span>

<span data-ttu-id="c0adf-317">Les bits de signe sont acceptés pour les chiffres avec suffixe BigInteger :</span><span class="sxs-lookup"><span data-stu-id="c0adf-317">Sign bits are accepted for BigInteger-suffixed numerals:</span></span>

- <span data-ttu-id="c0adf-318">Le paramètre hexadécimal avec suffixe BigInteger traite le bit élevé de tout littéral avec une longueur multiple de 8 caractères comme bit de signe.</span><span class="sxs-lookup"><span data-stu-id="c0adf-318">BigInteger-suffixed hex treats the high bit of any literal with a length multiple of 8 characters as the sign bit.</span></span> <span data-ttu-id="c0adf-319">La longueur n’inclut ni le `0x` préfixe, ni les suffixes.</span><span class="sxs-lookup"><span data-stu-id="c0adf-319">The length does not include the `0x` prefix or any suffixes.</span></span>
- <span data-ttu-id="c0adf-320">Le binaire avec suffixe BigInteger accepte les bits de signe à 96 et 128 caractères, et à tous les 8 caractères après.</span><span class="sxs-lookup"><span data-stu-id="c0adf-320">BigInteger-suffixed binary accepts sign bits at 96 and 128 characters, and at every 8 characters after.</span></span>

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="c0adf-321">Commandes qui ressemblent à des littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="c0adf-321">Commands that look like numeric literals</span></span>

<span data-ttu-id="c0adf-322">Toute commande ressemblant à un littéral numérique valide doit être exécutée à l’aide de l’opérateur d’appel ( `&` ), sinon elle est interprétée comme un nombre.</span><span class="sxs-lookup"><span data-stu-id="c0adf-322">Any command that looks like a valid numeric literal must be executed using the call operator (`&`), otherwise it is interpreted as a number.</span></span> <span data-ttu-id="c0adf-323">Les littéraux mal formés avec une syntaxe valide `1usgb` , comme, provoquent l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="c0adf-323">Malformed literals with valid syntax like `1usgb` will result in the following error:</span></span>

```
PS> 1usgb
At line:1 char:6
+ 1usgb
+      ~
The numeric constant 1usgb is not valid.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : BadNumericConstant
```

<span data-ttu-id="c0adf-324">Toutefois, les littéraux mal formés avec une syntaxe non valide comme `1gbus` seront interprétés comme une chaîne simple standard et peuvent être interprétés comme un nom de commande valide dans les contextes où les commandes peuvent être appelées.</span><span class="sxs-lookup"><span data-stu-id="c0adf-324">However, malformed literals with invalid syntax like `1gbus` will be interpreted as a standard bare string, and can be interpreted as a valid command name in contexts where commands may be called.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="c0adf-325">Accéder aux propriétés et aux méthodes d’objets numériques</span><span class="sxs-lookup"><span data-stu-id="c0adf-325">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="c0adf-326">Pour accéder à un membre d’un littéral numérique, il y a des cas où vous devez placer le littéral entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="c0adf-326">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="c0adf-327">Le littéral n’a pas de virgule décimale</span><span class="sxs-lookup"><span data-stu-id="c0adf-327">The literal does not have a decimal point</span></span>
- <span data-ttu-id="c0adf-328">Le littéral n’a pas de chiffres après la virgule décimale</span><span class="sxs-lookup"><span data-stu-id="c0adf-328">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="c0adf-329">Le littéral n’a pas de suffixe</span><span class="sxs-lookup"><span data-stu-id="c0adf-329">The literal does not have a suffix</span></span>

<span data-ttu-id="c0adf-330">Par exemple, l’exemple suivant échoue :</span><span class="sxs-lookup"><span data-stu-id="c0adf-330">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="c0adf-331">Les exemples suivants fonctionnent :</span><span class="sxs-lookup"><span data-stu-id="c0adf-331">The following examples work:</span></span>

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="c0adf-332">Les deux premiers exemples fonctionnent sans mettre la valeur littérale entre parenthèses, car l’analyseur PowerShell peut déterminer où se termine le littéral numérique et la méthode **GetType** démarre.</span><span class="sxs-lookup"><span data-stu-id="c0adf-332">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

## <a name="how-powershell-parses-numeric-literals"></a><span data-ttu-id="c0adf-333">Comment PowerShell analyse les littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="c0adf-333">How PowerShell parses numeric literals</span></span>

<span data-ttu-id="c0adf-334">PowerShell v 7.0 a changé la façon dont les littéraux numériques sont analysés pour activer les nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="c0adf-334">PowerShell v7.0 changed the way numeric literals are parsed to enable the new features.</span></span>

### <a name="parsing-real-numeric-literals"></a><span data-ttu-id="c0adf-335">Analyse des littéraux numériques réels</span><span class="sxs-lookup"><span data-stu-id="c0adf-335">Parsing real numeric literals</span></span>

<span data-ttu-id="c0adf-336">Si le littéral contient une virgule décimale ou une notation électronique, la chaîne littérale est analysée comme un nombre réel.</span><span class="sxs-lookup"><span data-stu-id="c0adf-336">If the literal contains a decimal point or the e-notation, the literal string is parsed a real number.</span></span>

- <span data-ttu-id="c0adf-337">Si le suffixe décimal est présent, puis directement dans `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="c0adf-337">If the decimal-suffix is present then directly into `[decimal]`.</span></span>
- <span data-ttu-id="c0adf-338">Sinon, analyser en tant que `[Double]` et appliquer le multiplicateur à la valeur.</span><span class="sxs-lookup"><span data-stu-id="c0adf-338">Else, parse as `[Double]` and apply multiplier to the value.</span></span> <span data-ttu-id="c0adf-339">Vérifiez ensuite les suffixes de type et tentez d’effectuer un cast en type approprié.</span><span class="sxs-lookup"><span data-stu-id="c0adf-339">Then check the type suffixes and attempt to cast into appropriate type.</span></span>
- <span data-ttu-id="c0adf-340">Si la chaîne n’a pas de suffixe de type, analyser en tant que `[Double]` .</span><span class="sxs-lookup"><span data-stu-id="c0adf-340">If the string has no type suffix, then parse as `[Double]`.</span></span>

### <a name="paring-integer-numeric-literals"></a><span data-ttu-id="c0adf-341">Littéraux numériques géocouplage Integer</span><span class="sxs-lookup"><span data-stu-id="c0adf-341">Paring integer numeric literals</span></span>

<span data-ttu-id="c0adf-342">Les littéraux de type entier sont analysés à l’aide des étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c0adf-342">Integer type literals are parsed using the following steps:</span></span>

1. <span data-ttu-id="c0adf-343">Déterminer le format de base</span><span class="sxs-lookup"><span data-stu-id="c0adf-343">Determine the radix format</span></span>
   - <span data-ttu-id="c0adf-344">Pour les formats binaires, analysez dans `[BigInteger]` .</span><span class="sxs-lookup"><span data-stu-id="c0adf-344">For binary formats, parse into `[BigInteger]`.</span></span>
   - <span data-ttu-id="c0adf-345">Pour les formats hexadécimaux, analysez dans `[BigInteger]` à l’aide de Casies spéciaux pour conserver les comportements d’origine lorsque la valeur est dans la `[int]` `[long]` plage ou.</span><span class="sxs-lookup"><span data-stu-id="c0adf-345">For hexidecimal formats, parse into `[BigInteger]` using special casies to retain original behaviours when the value is in the `[int]` or `[long]` range.</span></span>
   - <span data-ttu-id="c0adf-346">Si ni Binary ni Hex, ne sont normalement analysés en tant que `[BigInteger]` .</span><span class="sxs-lookup"><span data-stu-id="c0adf-346">If neither binary nor hex, parse normally as a `[BigInteger]`.</span></span>
2. <span data-ttu-id="c0adf-347">Appliquez la valeur de multiplicateur avant de tenter d’effectuer des casts pour vous assurer que les limites du type peuvent être vérifiées correctement sans dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="c0adf-347">Apply the multiplier value before attempting any casts to ensure type bounds can be appropriately checked without overflows.</span></span>
3. <span data-ttu-id="c0adf-348">Vérifiez les suffixes de type.</span><span class="sxs-lookup"><span data-stu-id="c0adf-348">Check type suffixes.</span></span>
   - <span data-ttu-id="c0adf-349">Vérifiez les limites du type et tentez d’analyser ce type.</span><span class="sxs-lookup"><span data-stu-id="c0adf-349">Check type bounds and attempt to parse into that type.</span></span>
   - <span data-ttu-id="c0adf-350">Si aucun suffixe n’est utilisé, la valeur est Bounds-Checked dans l’ordre suivant, ce qui entraîne le premier test réussi déterminant le type du nombre.</span><span class="sxs-lookup"><span data-stu-id="c0adf-350">If no suffix is used, then the value is bounds-checked in the following order, resulting in the first successful test determining the type of the number.</span></span>
     - `[int]`
     - `[long]`
     - <span data-ttu-id="c0adf-351">`[decimal]` (valeurs littérales de base 10 uniquement)</span><span class="sxs-lookup"><span data-stu-id="c0adf-351">`[decimal]` (base-10 literals only)</span></span>
     - <span data-ttu-id="c0adf-352">`[double]` (valeurs littérales de base 10 uniquement)</span><span class="sxs-lookup"><span data-stu-id="c0adf-352">`[double]` (base-10 literals only)</span></span>
   - <span data-ttu-id="c0adf-353">Si la valeur est en dehors `[long]` de la plage pour les nombres hexadécimaux et binaires, l’analyse échoue.</span><span class="sxs-lookup"><span data-stu-id="c0adf-353">If the value is outside the `[long]` range for hex and binary numbers, the parse fails.</span></span>
   - <span data-ttu-id="c0adf-354">Si la valeur est en dehors `[double]` de la plage pour le nombre de base 10, l’analyse échoue.</span><span class="sxs-lookup"><span data-stu-id="c0adf-354">If the value is outside the `[double]` range for base 10 number, the parse fails.</span></span>
   - <span data-ttu-id="c0adf-355">Les valeurs supérieures doivent être écrites explicitement à l’aide du `n` suffixe pour analyser le littéral en tant que `BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="c0adf-355">Higher values must be explicitly written using the `n` suffix to parse the literal as a `BigInteger`.</span></span>

### <a name="parsing-large-value-literals"></a><span data-ttu-id="c0adf-356">Analyse des littéraux de valeur élevée</span><span class="sxs-lookup"><span data-stu-id="c0adf-356">Parsing large value literals</span></span>

<span data-ttu-id="c0adf-357">Auparavant, les valeurs entières supérieures étaient analysées comme double avant d’être transtypées en un autre type.</span><span class="sxs-lookup"><span data-stu-id="c0adf-357">Previously, higher integer values were parsed as double before being cast to any other type.</span></span> <span data-ttu-id="c0adf-358">Cela entraîne une perte de précision dans les plages supérieures.</span><span class="sxs-lookup"><span data-stu-id="c0adf-358">This results in a loss of precision in the higher ranges.</span></span> <span data-ttu-id="c0adf-359">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c0adf-359">For example:</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="c0adf-360">Pour éviter ce problème, vous deviez écrire des valeurs sous forme de chaînes, puis les convertir :</span><span class="sxs-lookup"><span data-stu-id="c0adf-360">To avoid this problem you had to write values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

<span data-ttu-id="c0adf-361">Dans PowerShell 7,0, vous devez utiliser le `N` suffixe.</span><span class="sxs-lookup"><span data-stu-id="c0adf-361">In PowerShell 7.0 you must use the `N` suffix.</span></span>

```
PS> 111111111111111111111111111111111111111111111111111111n
111111111111111111111111111111111111111111111111111111
```

<span data-ttu-id="c0adf-362">En outre, les valeurs comprises entre `[ulong]::MaxValue` et `[decimal]::MaxValue` doivent être dénotées à l’aide du suffixe décimal `D` pour assurer la précision.</span><span class="sxs-lookup"><span data-stu-id="c0adf-362">Also values between `[ulong]::MaxValue` and `[decimal]::MaxValue` should be denoted using the decimal-suffix `D` to maintain accuracy.</span></span> <span data-ttu-id="c0adf-363">Sans le suffixe, ces valeurs sont analysées comme `[Double]` utilisant le mode d’analyse réelle.</span><span class="sxs-lookup"><span data-stu-id="c0adf-363">Without the suffix, these values are parsed as `[Double]` using the real-parsing mode.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger?view=netcore-2.2
