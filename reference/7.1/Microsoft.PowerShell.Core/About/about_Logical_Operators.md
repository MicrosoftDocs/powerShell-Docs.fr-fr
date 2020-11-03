---
description: Décrit les opérateurs qui connectent des instructions dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logical_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logical_Operators
ms.openlocfilehash: f8db290b87043451241613358a2f6d4fdf1dc342
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206510"
---
# <a name="about_logical_operators"></a><span data-ttu-id="142a2-104">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="142a2-104">about_Logical_Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="142a2-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="142a2-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="142a2-106">Décrit les opérateurs qui connectent des instructions dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="142a2-106">Describes the operators that connect statements in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="142a2-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="142a2-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="142a2-108">Les opérateurs logiques PowerShell connectent des expressions et des instructions, ce qui vous permet d’utiliser une expression unique pour tester plusieurs conditions.</span><span class="sxs-lookup"><span data-stu-id="142a2-108">The PowerShell logical operators connect expressions and statements, allowing you to use a single expression to test for multiple conditions.</span></span>

<span data-ttu-id="142a2-109">Par exemple, l’instruction suivante utilise l’opérateur and et l’opérateur or pour connecter trois instructions conditionnelles.</span><span class="sxs-lookup"><span data-stu-id="142a2-109">For example, the following statement uses the and operator and the or operator to connect three conditional statements.</span></span> <span data-ttu-id="142a2-110">L’instruction est vraie uniquement lorsque la valeur de $a est supérieure à la valeur de $b, et que $a ou $b est inférieur à</span><span class="sxs-lookup"><span data-stu-id="142a2-110">The statement is true only when the value of $a is greater than the value of $b, and either $a or $b is less than</span></span>
20.

```powershell
($a -gt $b) -and (($a -lt 20) -or ($b -lt 20))
```

<span data-ttu-id="142a2-111">PowerShell prend en charge les opérateurs logiques suivants.</span><span class="sxs-lookup"><span data-stu-id="142a2-111">PowerShell supports the following logical operators.</span></span>

|<span data-ttu-id="142a2-112">Opérateur</span><span class="sxs-lookup"><span data-stu-id="142a2-112">Operator</span></span>|<span data-ttu-id="142a2-113">Description</span><span class="sxs-lookup"><span data-stu-id="142a2-113">Description</span></span>                        |<span data-ttu-id="142a2-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="142a2-114">Example</span></span>                   |
|--------|-----------------------------------|--------------------------|
|`-and`  |<span data-ttu-id="142a2-115">AND logique.</span><span class="sxs-lookup"><span data-stu-id="142a2-115">Logical AND.</span></span> <span data-ttu-id="142a2-116">TRUE lorsque les deux</span><span class="sxs-lookup"><span data-stu-id="142a2-116">TRUE when both</span></span>        |`(1 -eq 1) -and (1 -eq 2)`|
|        |<span data-ttu-id="142a2-117">les instructions sont vraies.</span><span class="sxs-lookup"><span data-stu-id="142a2-117">statements are TRUE.</span></span>               |`False`                   |
|`-or`   |<span data-ttu-id="142a2-118">OR logique.</span><span class="sxs-lookup"><span data-stu-id="142a2-118">Logical OR.</span></span> <span data-ttu-id="142a2-119">TRUE lorsque</span><span class="sxs-lookup"><span data-stu-id="142a2-119">TRUE when either</span></span>       |`(1 -eq 1) -or (1 -eq 2)` |
|        |<span data-ttu-id="142a2-120">l’instruction a la valeur TRUE.</span><span class="sxs-lookup"><span data-stu-id="142a2-120">statement is TRUE.</span></span>                 |`True`                    |
|`-xor`  |<span data-ttu-id="142a2-121">OR exclusif logique.</span><span class="sxs-lookup"><span data-stu-id="142a2-121">Logical EXCLUSIVE OR.</span></span> <span data-ttu-id="142a2-122">TRUE lorsque</span><span class="sxs-lookup"><span data-stu-id="142a2-122">TRUE when</span></span>    |`(1 -eq 1) -xor (2 -eq 2)`|
|        |<span data-ttu-id="142a2-123">une seule instruction est vraie</span><span class="sxs-lookup"><span data-stu-id="142a2-123">only one statement is TRUE</span></span>         |`False`                   |
|`-not`  |<span data-ttu-id="142a2-124">Not logique.</span><span class="sxs-lookup"><span data-stu-id="142a2-124">Logical not.</span></span> <span data-ttu-id="142a2-125">Inverse l’instruction</span><span class="sxs-lookup"><span data-stu-id="142a2-125">Negates the statement</span></span> |`-not (1 -eq 1)`          |
|        |<span data-ttu-id="142a2-126">Cela suit.</span><span class="sxs-lookup"><span data-stu-id="142a2-126">that follows.</span></span>                      |`False`                   |
|`!`     |<span data-ttu-id="142a2-127">Identique à `-not`</span><span class="sxs-lookup"><span data-stu-id="142a2-127">Same as `-not`</span></span>                     |`!(1 -eq 1)`              |
|        |                                   |`False`                   |

 <span data-ttu-id="142a2-128">Remarque :</span><span class="sxs-lookup"><span data-stu-id="142a2-128">Note:</span></span>

<span data-ttu-id="142a2-129">Les exemples précédents utilisent également l’opérateur de comparaison égal à `-eq` .</span><span class="sxs-lookup"><span data-stu-id="142a2-129">The previous examples also use the equal to comparison operator `-eq`.</span></span> <span data-ttu-id="142a2-130">Pour plus d’informations, consultez [about_Comparison_Operators](about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="142a2-130">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span> <span data-ttu-id="142a2-131">Les exemples utilisent également les valeurs booléennes des entiers.</span><span class="sxs-lookup"><span data-stu-id="142a2-131">The examples also use the Boolean values of integers.</span></span> <span data-ttu-id="142a2-132">L’entier 0 a la valeur FALSe.</span><span class="sxs-lookup"><span data-stu-id="142a2-132">The integer 0 has a value of FALSE.</span></span> <span data-ttu-id="142a2-133">Tous les autres entiers ont la valeur TRUE.</span><span class="sxs-lookup"><span data-stu-id="142a2-133">All other integers have a value of TRUE.</span></span>

<span data-ttu-id="142a2-134">La syntaxe des opérateurs logiques est la suivante :</span><span class="sxs-lookup"><span data-stu-id="142a2-134">The syntax of the logical operators is as follows:</span></span>

```
<statement> {-AND | -OR | -XOR} <statement>
{! | -NOT} <statement>
```

<span data-ttu-id="142a2-135">Les instructions qui utilisent les opérateurs logiques retournent des valeurs booléennes (TRUE ou FALSe).</span><span class="sxs-lookup"><span data-stu-id="142a2-135">Statements that use the logical operators return Boolean (TRUE or FALSE) values.</span></span>

<span data-ttu-id="142a2-136">Les opérateurs logiques PowerShell évaluent uniquement les instructions requises pour déterminer la valeur de vérité de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="142a2-136">The PowerShell logical operators evaluate only the statements required to determine the truth value of the statement.</span></span> <span data-ttu-id="142a2-137">Si l’opérande gauche dans une instruction qui contient l’opérateur and est FALSe, l’opérande de droite n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="142a2-137">If the left operand in a statement that contains the and operator is FALSE, the right operand is not evaluated.</span></span>
<span data-ttu-id="142a2-138">Si l’opérande gauche dans une instruction qui contient l’instruction ou a la valeur TRUE, l’opérande de droite n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="142a2-138">If the left operand in a statement that contains the or statement is TRUE, the right operand is not evaluated.</span></span> <span data-ttu-id="142a2-139">Par conséquent, vous pouvez utiliser ces instructions de la même façon que vous utilisez l' `If` instruction.</span><span class="sxs-lookup"><span data-stu-id="142a2-139">As a result, you can use these statements in the same way that you would use the `If` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="142a2-140">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="142a2-140">SEE ALSO</span></span>

[<span data-ttu-id="142a2-141">about_Operators</span><span class="sxs-lookup"><span data-stu-id="142a2-141">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="142a2-142">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="142a2-142">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)

[<span data-ttu-id="142a2-143">about_Comparison_operators</span><span class="sxs-lookup"><span data-stu-id="142a2-143">about_Comparison_operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="142a2-144">about_If</span><span class="sxs-lookup"><span data-stu-id="142a2-144">about_If</span></span>](about_If.md)

