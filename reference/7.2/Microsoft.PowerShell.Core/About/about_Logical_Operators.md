---
description: Décrit les opérateurs qui connectent des instructions dans PowerShell.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logical_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logical_Operators
ms.openlocfilehash: 8602551f3ecf74027b59715e1f47aab1b10bea92
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596920"
---
# <a name="about_logical_operators"></a><span data-ttu-id="dc5a0-103">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="dc5a0-103">about_Logical_Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="dc5a0-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="dc5a0-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="dc5a0-105">Décrit les opérateurs qui connectent des instructions dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-105">Describes the operators that connect statements in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="dc5a0-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="dc5a0-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="dc5a0-107">Les opérateurs logiques PowerShell connectent des expressions et des instructions, ce qui vous permet d’utiliser une expression unique pour tester plusieurs conditions.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-107">The PowerShell logical operators connect expressions and statements, allowing you to use a single expression to test for multiple conditions.</span></span>

<span data-ttu-id="dc5a0-108">Par exemple, l’instruction suivante utilise l’opérateur and et l’opérateur or pour connecter trois instructions conditionnelles.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-108">For example, the following statement uses the and operator and the or operator to connect three conditional statements.</span></span> <span data-ttu-id="dc5a0-109">L’instruction est vraie uniquement lorsque la valeur de $a est supérieure à la valeur de $b, et que $a ou $b est inférieur à</span><span class="sxs-lookup"><span data-stu-id="dc5a0-109">The statement is true only when the value of $a is greater than the value of $b, and either $a or $b is less than</span></span>
20.

```powershell
($a -gt $b) -and (($a -lt 20) -or ($b -lt 20))
```

<span data-ttu-id="dc5a0-110">PowerShell prend en charge les opérateurs logiques suivants.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-110">PowerShell supports the following logical operators.</span></span>

|<span data-ttu-id="dc5a0-111">Opérateur</span><span class="sxs-lookup"><span data-stu-id="dc5a0-111">Operator</span></span>|<span data-ttu-id="dc5a0-112">Description</span><span class="sxs-lookup"><span data-stu-id="dc5a0-112">Description</span></span>                        |<span data-ttu-id="dc5a0-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="dc5a0-113">Example</span></span>                   |
|--------|-----------------------------------|--------------------------|
|`-and`  |<span data-ttu-id="dc5a0-114">AND logique.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-114">Logical AND.</span></span> <span data-ttu-id="dc5a0-115">TRUE lorsque les deux</span><span class="sxs-lookup"><span data-stu-id="dc5a0-115">TRUE when both</span></span>        |`(1 -eq 1) -and (1 -eq 2)`|
|        |<span data-ttu-id="dc5a0-116">les instructions sont vraies.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-116">statements are TRUE.</span></span>               |`False`                   |
|`-or`   |<span data-ttu-id="dc5a0-117">OR logique.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-117">Logical OR.</span></span> <span data-ttu-id="dc5a0-118">TRUE lorsque</span><span class="sxs-lookup"><span data-stu-id="dc5a0-118">TRUE when either</span></span>       |`(1 -eq 1) -or (1 -eq 2)` |
|        |<span data-ttu-id="dc5a0-119">l’instruction a la valeur TRUE.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-119">statement is TRUE.</span></span>                 |`True`                    |
|`-xor`  |<span data-ttu-id="dc5a0-120">OR exclusif logique.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-120">Logical EXCLUSIVE OR.</span></span> <span data-ttu-id="dc5a0-121">TRUE lorsque</span><span class="sxs-lookup"><span data-stu-id="dc5a0-121">TRUE when</span></span>    |`(1 -eq 1) -xor (2 -eq 2)`|
|        |<span data-ttu-id="dc5a0-122">une seule instruction est vraie</span><span class="sxs-lookup"><span data-stu-id="dc5a0-122">only one statement is TRUE</span></span>         |`False`                   |
|`-not`  |<span data-ttu-id="dc5a0-123">Not logique.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-123">Logical not.</span></span> <span data-ttu-id="dc5a0-124">Inverse l’instruction</span><span class="sxs-lookup"><span data-stu-id="dc5a0-124">Negates the statement</span></span> |`-not (1 -eq 1)`          |
|        |<span data-ttu-id="dc5a0-125">Cela suit.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-125">that follows.</span></span>                      |`False`                   |
|`!`     |<span data-ttu-id="dc5a0-126">Identique à `-not`</span><span class="sxs-lookup"><span data-stu-id="dc5a0-126">Same as `-not`</span></span>                     |`!(1 -eq 1)`              |
|        |                                   |`False`                   |

 <span data-ttu-id="dc5a0-127">Remarque :</span><span class="sxs-lookup"><span data-stu-id="dc5a0-127">Note:</span></span>

<span data-ttu-id="dc5a0-128">Les exemples précédents utilisent également l’opérateur de comparaison égal à `-eq` .</span><span class="sxs-lookup"><span data-stu-id="dc5a0-128">The previous examples also use the equal to comparison operator `-eq`.</span></span> <span data-ttu-id="dc5a0-129">Pour plus d’informations, consultez [about_Comparison_Operators](about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc5a0-129">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span> <span data-ttu-id="dc5a0-130">Les exemples utilisent également les valeurs booléennes des entiers.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-130">The examples also use the Boolean values of integers.</span></span> <span data-ttu-id="dc5a0-131">L’entier 0 a la valeur FALSe.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-131">The integer 0 has a value of FALSE.</span></span> <span data-ttu-id="dc5a0-132">Tous les autres entiers ont la valeur TRUE.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-132">All other integers have a value of TRUE.</span></span>

<span data-ttu-id="dc5a0-133">La syntaxe des opérateurs logiques est la suivante :</span><span class="sxs-lookup"><span data-stu-id="dc5a0-133">The syntax of the logical operators is as follows:</span></span>

```
<statement> {-AND | -OR | -XOR} <statement>
{! | -NOT} <statement>
```

<span data-ttu-id="dc5a0-134">Les instructions qui utilisent les opérateurs logiques retournent des valeurs booléennes (TRUE ou FALSe).</span><span class="sxs-lookup"><span data-stu-id="dc5a0-134">Statements that use the logical operators return Boolean (TRUE or FALSE) values.</span></span>

<span data-ttu-id="dc5a0-135">Les opérateurs logiques PowerShell évaluent uniquement les instructions requises pour déterminer la valeur de vérité de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-135">The PowerShell logical operators evaluate only the statements required to determine the truth value of the statement.</span></span> <span data-ttu-id="dc5a0-136">Si l’opérande gauche dans une instruction qui contient l’opérateur and est FALSe, l’opérande de droite n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-136">If the left operand in a statement that contains the and operator is FALSE, the right operand is not evaluated.</span></span>
<span data-ttu-id="dc5a0-137">Si l’opérande gauche dans une instruction qui contient l’instruction ou a la valeur TRUE, l’opérande de droite n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-137">If the left operand in a statement that contains the or statement is TRUE, the right operand is not evaluated.</span></span> <span data-ttu-id="dc5a0-138">Par conséquent, vous pouvez utiliser ces instructions de la même façon que vous utilisez l' `If` instruction.</span><span class="sxs-lookup"><span data-stu-id="dc5a0-138">As a result, you can use these statements in the same way that you would use the `If` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc5a0-139">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="dc5a0-139">SEE ALSO</span></span>

[<span data-ttu-id="dc5a0-140">about_Operators</span><span class="sxs-lookup"><span data-stu-id="dc5a0-140">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="dc5a0-141">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="dc5a0-141">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)

[<span data-ttu-id="dc5a0-142">about_Comparison_operators</span><span class="sxs-lookup"><span data-stu-id="dc5a0-142">about_Comparison_operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="dc5a0-143">about_If</span><span class="sxs-lookup"><span data-stu-id="dc5a0-143">about_If</span></span>](about_If.md)

