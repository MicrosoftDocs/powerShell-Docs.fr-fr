---
description: Décrit comment l' `continue` instruction retourne immédiatement le déroulement du programme au début d’une boucle de programme, d’une `switch` instruction ou d’une `trap` instruction.
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_continue?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Continue
ms.openlocfilehash: 36c14dc0489345083e8938c066cefa77e3f5ef8d
ms.sourcegitcommit: 0c31814bed14ff715dc7d4aace07cbdc6df2438e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "99597970"
---
# <a name="about-continue"></a><span data-ttu-id="4d1c7-103">À propos de continue</span><span class="sxs-lookup"><span data-stu-id="4d1c7-103">About Continue</span></span>

## <a name="short-description"></a><span data-ttu-id="4d1c7-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="4d1c7-104">Short description</span></span>

<span data-ttu-id="4d1c7-105">Décrit comment l' `continue` instruction retourne immédiatement le déroulement du programme au début d’une boucle de programme, d’une `switch` instruction ou d’une `trap` instruction.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-105">Describes how the `continue` statement immediately returns the program flow to the top of a program loop, a `switch` statement, or a `trap` statement.</span></span>

## <a name="long-description"></a><span data-ttu-id="4d1c7-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="4d1c7-106">Long description</span></span>

<span data-ttu-id="4d1c7-107">L' `continue` instruction fournit un moyen de quitter le bloc de contrôle actuel, mais de continuer l’exécution, au lieu de quitter complètement.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-107">The `continue` statement provides a way to exit the current control block but continue execution, rather than exit completely.</span></span> <span data-ttu-id="4d1c7-108">L’instruction prend en charge les étiquettes.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-108">The statement supports labels.</span></span>
<span data-ttu-id="4d1c7-109">Une étiquette est un nom que vous attribuez à une instruction dans un script.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-109">A label is a name you assign to a statement in a script.</span></span>

## <a name="using-continue-in-loops"></a><span data-ttu-id="4d1c7-110">Utilisation des boucles continue dans</span><span class="sxs-lookup"><span data-stu-id="4d1c7-110">Using continue in loops</span></span>

<span data-ttu-id="4d1c7-111">Une `continue` instruction sans étiquette retourne immédiatement le déroulement du programme au début de la boucle la plus profonde qui est contrôlée par `for` une `foreach` instruction,, `do` ou `while` .</span><span class="sxs-lookup"><span data-stu-id="4d1c7-111">An unlabeled `continue` statement immediately returns the program flow to the top of the innermost loop that is controlled by a `for`, `foreach`, `do`, or `while` statement.</span></span> <span data-ttu-id="4d1c7-112">L’itération actuelle de la boucle est terminée et la boucle se poursuit avec l’itération suivante.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-112">The current iteration of the loop is terminated and the loop continues with the next iteration.</span></span>

<span data-ttu-id="4d1c7-113">Dans l’exemple suivant, le déroulement du programme revient au sommet de la `while` boucle si la `$ctr` variable est égale à 5.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-113">In the following example, program flow returns to the top of the `while` loop if the `$ctr` variable is equal to 5.</span></span> <span data-ttu-id="4d1c7-114">Par conséquent, tous les nombres compris entre 1 et 10 sont affichés, à l’exception de 5 :</span><span class="sxs-lookup"><span data-stu-id="4d1c7-114">As a result, all the numbers between 1 and 10 are displayed except for 5:</span></span>

```powershell
while ($ctr -lt 10)
{
    $ctr += 1
    if ($ctr -eq 5)
    {
        continue
    }

    Write-Host -Object $ctr
}
```

<span data-ttu-id="4d1c7-115">Lors de l’utilisation d’une `for` boucle, l’exécution se poursuit au niveau de l' `<Repeat>` instruction, suivie du `<Condition>` test.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-115">When using a `for` loop, execution continues at the `<Repeat>` statement, followed by the `<Condition>` test.</span></span> <span data-ttu-id="4d1c7-116">Dans l’exemple ci-dessous, une boucle infinie ne se produit pas, car la décrémentation de `$i` se produit après le `continue` mot clé.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-116">In the example below, an infinite loop will not occur because the decrement of `$i` occurs after the `continue` keyword.</span></span>

```powershell
#   <Init>  <Condition> <Repeat>
for ($i = 0; $i -lt 10; $i++)
{
    Write-Host -Object $i
    if ($i -eq 5)
    {
        continue
        # Will not result in an infinite loop.
        $i--
    }
}
```

### <a name="using-a-labeled-continue-in-a-loop"></a><span data-ttu-id="4d1c7-117">Utilisation d’une étiquette continue dans une boucle</span><span class="sxs-lookup"><span data-stu-id="4d1c7-117">Using a labeled continue in a loop</span></span>

<span data-ttu-id="4d1c7-118">Une instruction étiquetée `continue` termine l’exécution de l’itération et transfère le contrôle à l’itération ou à l’étiquette d’instruction englobante ciblée `switch` .</span><span class="sxs-lookup"><span data-stu-id="4d1c7-118">A labeled `continue` statement terminates execution of the iteration and transfers control to the targeted enclosing iteration or `switch` statement label.</span></span>

<span data-ttu-id="4d1c7-119">Dans l’exemple suivant, le plus profond `for` se termine lorsque `$condition` a la **valeur true** et que l’itération continue avec la deuxième `for` boucle à `labelB` .</span><span class="sxs-lookup"><span data-stu-id="4d1c7-119">In the following example, the innermost `for` is terminated when `$condition` is **True** and iteration continues with the second `for` loop at `labelB`.</span></span>

```powershell
:labelA for ($i = 1; $i -le 10; $i++) {
    :labelB for ($j = 1; $j -le 10; $j++) {
        :labelC for ($k = 1; $k -le 10; $k++) {
            if ($condition) {
                continue labelB
            } else {
                $condition = Update-Condition
            }
        }
    }
}
```

## <a name="using-continue-in-a-switch-statement"></a><span data-ttu-id="4d1c7-120">Utilisation de continue dans une instruction switch</span><span class="sxs-lookup"><span data-stu-id="4d1c7-120">Using continue in a switch statement</span></span>

<span data-ttu-id="4d1c7-121">Une instruction sans étiquette `continue` dans un `switch` met fin à l’exécution de l' `switch` itération actuelle et transfère le contrôle vers le haut de `switch` pour obtenir l’élément d’entrée suivant.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-121">An unlabeled `continue` statement within a `switch` terminates execution of the current `switch` iteration and transfers control to the top of the `switch` to get the next input item.</span></span>

<span data-ttu-id="4d1c7-122">Lorsqu’il existe un seul élément d’entrée `continue` , la totalité de l’instruction est fermée `switch` .</span><span class="sxs-lookup"><span data-stu-id="4d1c7-122">When there is a single input item `continue` exits the entire `switch` statement.</span></span>
<span data-ttu-id="4d1c7-123">Lorsque l' `switch` entrée est une collection, le `switch` teste chaque élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-123">When the `switch` input is a collection, the `switch` tests each element of the collection.</span></span> <span data-ttu-id="4d1c7-124">Le `continue` quitte l’itération actuelle et `switch` poursuit avec l’élément suivant.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-124">The `continue` exits the current iteration and the `switch` continues with the next element.</span></span>

```powershell
switch (1,2,3) {
  2 { continue }  # moves on to the next element, 3
  default { $_ }
}
```

```Output
1
3
```

## <a name="using-continue-in-a-trap-statement"></a><span data-ttu-id="4d1c7-125">Utilisation de continue dans une instruction Trap</span><span class="sxs-lookup"><span data-stu-id="4d1c7-125">Using continue in a trap statement</span></span>

<span data-ttu-id="4d1c7-126">Si la dernière instruction exécutée dans le corps d’une `trap` instruction est `continue` , l’erreur interceptée est ignorée silencieusement et l’exécution se poursuit avec l’instruction qui suit immédiatement celle qui a entraîné l' `trap` apparition de.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-126">If the final statement executed in the body a `trap` statement is `continue`, the trapped error is silently ignored and execution continues with the statement immediately following the one that caused `trap` to occur.</span></span>

## <a name="do-not-use-continue-outside-of-a-loop-switch-or-trap"></a><span data-ttu-id="4d1c7-127">Ne pas utiliser continuer en dehors d’une boucle, d’un commutateur ou d’une interruption</span><span class="sxs-lookup"><span data-stu-id="4d1c7-127">Do not use continue outside of a loop, switch, or trap</span></span>

<span data-ttu-id="4d1c7-128">Quand `continue` est utilisé en dehors d’une construction qui le prend directement en charge (boucles, `switch` , `trap` ), PowerShell recherche _la pile des appels_ pour une construction englobante.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-128">When `continue` is used outside of a construct that directly supports it (loops, `switch`, `trap`), PowerShell looks _up the call stack_ for an enclosing construct.</span></span> <span data-ttu-id="4d1c7-129">S’il ne trouve pas de construction englobante, l’instance d’exécution actuelle est arrêtée en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-129">If it can't find an enclosing construct, the current runspace is quietly terminated.</span></span>

<span data-ttu-id="4d1c7-130">Cela signifie que les fonctions et les scripts qui utilisent par inadvertance un `continue` en dehors d’une construction englobante qui la prend en charge peuvent arrêter par inadvertance leurs _appelants_.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-130">This means that functions and scripts that inadvertently use a `continue` outside of an enclosing construct that supports it, can inadvertently terminate their _callers_.</span></span>

<span data-ttu-id="4d1c7-131">L’utilisation `continue` de l’intérieur d’un pipeline, tel qu’un `ForEach-Object` bloc de script, non seulement quitte le pipeline, mais il peut mettre fin à la totalité de l’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4d1c7-131">Using `continue` inside a pipeline, such as a `ForEach-Object` script block, not only exits the pipeline, it potentially terminates the entire runspace.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d1c7-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d1c7-132">See also</span></span>

[<span data-ttu-id="4d1c7-133">about_Break</span><span class="sxs-lookup"><span data-stu-id="4d1c7-133">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="4d1c7-134">about_For</span><span class="sxs-lookup"><span data-stu-id="4d1c7-134">about_For</span></span>](about_For.md)

[<span data-ttu-id="4d1c7-135">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="4d1c7-135">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="4d1c7-136">about_Throw</span><span class="sxs-lookup"><span data-stu-id="4d1c7-136">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="4d1c7-137">about_Trap</span><span class="sxs-lookup"><span data-stu-id="4d1c7-137">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="4d1c7-138">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="4d1c7-138">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
