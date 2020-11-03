---
description: Décrit une instruction que vous pouvez utiliser pour quitter immédiatement les instructions,,,, `foreach` `for` `while` `do` `switch` ou `trap` .
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_break?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Break
ms.openlocfilehash: 4dbc1a09ca4ec317c4756c65058f661ec41a513a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206666"
---
# <a name="about-break"></a><span data-ttu-id="d9061-104">À propos des arrêts</span><span class="sxs-lookup"><span data-stu-id="d9061-104">About Break</span></span>

## <a name="short-description"></a><span data-ttu-id="d9061-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="d9061-105">Short description</span></span>

<span data-ttu-id="d9061-106">Décrit une instruction que vous pouvez utiliser pour quitter immédiatement les instructions,,,, `foreach` `for` `while` `do` `switch` ou `trap` .</span><span class="sxs-lookup"><span data-stu-id="d9061-106">Describes a statement you can use to immediately exit `foreach`, `for`, `while`, `do`, `switch`, or `trap` statements.</span></span>

## <a name="long-description"></a><span data-ttu-id="d9061-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="d9061-107">Long description</span></span>

<span data-ttu-id="d9061-108">L' `break` instruction fournit un moyen de quitter le bloc de contrôle actuel.</span><span class="sxs-lookup"><span data-stu-id="d9061-108">The `break` statement provides a way to exit the current control block.</span></span>
<span data-ttu-id="d9061-109">L’exécution se poursuit à l’instruction suivante après le bloc de contrôle.</span><span class="sxs-lookup"><span data-stu-id="d9061-109">Execution continues at the next statement after the control block.</span></span> <span data-ttu-id="d9061-110">L’instruction prend en charge les étiquettes.</span><span class="sxs-lookup"><span data-stu-id="d9061-110">The statement supports labels.</span></span> <span data-ttu-id="d9061-111">Une étiquette est un nom que vous attribuez à une instruction dans un script.</span><span class="sxs-lookup"><span data-stu-id="d9061-111">A label is a name you assign to a statement in a script.</span></span>

## <a name="using-break-in-loops"></a><span data-ttu-id="d9061-112">Utilisation de boucles Break in</span><span class="sxs-lookup"><span data-stu-id="d9061-112">Using break in loops</span></span>

<span data-ttu-id="d9061-113">Lorsqu’une `break` instruction apparaît dans une boucle, telle qu’une `foreach` boucle,, `for` `do` ou `while` , PowerShell quitte immédiatement la boucle.</span><span class="sxs-lookup"><span data-stu-id="d9061-113">When a `break` statement appears in a loop, such as a `foreach`, `for`, `do`, or `while` loop, PowerShell immediately exits the loop.</span></span>

<span data-ttu-id="d9061-114">Une `break` instruction peut inclure une étiquette qui vous permet de quitter des boucles incorporées.</span><span class="sxs-lookup"><span data-stu-id="d9061-114">A `break` statement can include a label that lets you exit embedded loops.</span></span> <span data-ttu-id="d9061-115">Une étiquette peut spécifier n’importe quel mot clé de boucle, tel que `foreach` , `for` ou `while` , dans un script.</span><span class="sxs-lookup"><span data-stu-id="d9061-115">A label can specify any loop keyword, such as `foreach`, `for`, or `while`, in a script.</span></span>

<span data-ttu-id="d9061-116">L’exemple suivant montre comment utiliser une `break` instruction pour quitter une `for` instruction :</span><span class="sxs-lookup"><span data-stu-id="d9061-116">The following example shows how to use a `break` statement to exit a `for` statement:</span></span>

```powershell
for($i=1; $i -le 10; $i++) {
   Write-Host $i
   break
}
```

<span data-ttu-id="d9061-117">Dans cet exemple, l' `break` instruction quitte la `for` boucle lorsque la `$i` variable est égale à 1.</span><span class="sxs-lookup"><span data-stu-id="d9061-117">In this example, the `break` statement exits the `for` loop when the `$i` variable equals 1.</span></span> <span data-ttu-id="d9061-118">Même si l' `for` instruction prend la **valeur true** jusqu’à ce que `$i` soit supérieur à 10, PowerShell atteint l’instruction Break la première fois que la `for` boucle est exécutée.</span><span class="sxs-lookup"><span data-stu-id="d9061-118">Even though the `for` statement evaluates to **True** until `$i` is greater than 10, PowerShell reaches the break statement the first time the `for` loop is run.</span></span>

<span data-ttu-id="d9061-119">Il est plus courant d’utiliser l' `break` instruction dans une boucle où une condition interne doit être remplie.</span><span class="sxs-lookup"><span data-stu-id="d9061-119">It is more common to use the `break` statement in a loop where an inner condition must be met.</span></span> <span data-ttu-id="d9061-120">Prenons l’exemple de l' `foreach` instruction suivante :</span><span class="sxs-lookup"><span data-stu-id="d9061-120">Consider the following `foreach` statement example:</span></span>

```powershell
$i=0
$varB = 10,20,30,40
foreach ($val in $varB) {
  if ($val -eq 30) {
    break
  }
  $i++
}
Write-Host "30 was found in array index $i"
```

<span data-ttu-id="d9061-121">Dans cet exemple, l' `foreach` instruction itère le `$varB` tableau.</span><span class="sxs-lookup"><span data-stu-id="d9061-121">In this example, the `foreach` statement iterates the `$varB` array.</span></span> <span data-ttu-id="d9061-122">L' `if` instruction prend la valeur false les deux premières fois que la boucle est exécutée et la variable `$i` est incrémentée de 1.</span><span class="sxs-lookup"><span data-stu-id="d9061-122">The `if` statement evaluates to False the first two times the loop is run and the variable `$i` is incremented by 1.</span></span> <span data-ttu-id="d9061-123">La troisième fois que la boucle est exécutée, est `$i` égal à 2 et la `$val` variable est égale à 30.</span><span class="sxs-lookup"><span data-stu-id="d9061-123">The third time the loop is run, `$i` equals 2, and the `$val` variable equals 30.</span></span> <span data-ttu-id="d9061-124">À ce stade, l' `break` instruction s’exécute et la `foreach` boucle se termine.</span><span class="sxs-lookup"><span data-stu-id="d9061-124">At this point, the `break` statement runs, and the `foreach` loop exits.</span></span>

### <a name="using-a-labeled-break-in-a-loop"></a><span data-ttu-id="d9061-125">Utilisation d’un saut de chaîne étiqueté dans une boucle</span><span class="sxs-lookup"><span data-stu-id="d9061-125">Using a labeled break in a loop</span></span>

<span data-ttu-id="d9061-126">Une `break` instruction peut inclure une étiquette.</span><span class="sxs-lookup"><span data-stu-id="d9061-126">A `break` statement can include a label.</span></span> <span data-ttu-id="d9061-127">Si vous utilisez le `break` mot clé avec une étiquette, PowerShell quitte la boucle étiquetée au lieu de quitter la boucle en cours.</span><span class="sxs-lookup"><span data-stu-id="d9061-127">If you use the `break` keyword with a label, PowerShell exits the labeled loop instead of exiting the current loop.</span></span>
<span data-ttu-id="d9061-128">L’étiquette est un signe deux-points suivi d’un nom que vous attribuez.</span><span class="sxs-lookup"><span data-stu-id="d9061-128">The label is a colon followed by a name that you assign.</span></span> <span data-ttu-id="d9061-129">L’étiquette doit être le premier jeton d’une instruction, et elle doit être suivie par le mot clé de bouclage, par exemple `while` .</span><span class="sxs-lookup"><span data-stu-id="d9061-129">The label must be the first token in a statement, and it must be followed by the looping keyword, such as `while`.</span></span>

<span data-ttu-id="d9061-130">`break` déplace l’exécution en dehors de la boucle étiquetée.</span><span class="sxs-lookup"><span data-stu-id="d9061-130">`break` moves execution out of the labeled loop.</span></span> <span data-ttu-id="d9061-131">Dans les boucles incorporées, le résultat est différent de celui du `break` mot clé lorsqu’il est utilisé par lui-même.</span><span class="sxs-lookup"><span data-stu-id="d9061-131">In embedded loops, this has a different result than the `break` keyword has when it is used by itself.</span></span> <span data-ttu-id="d9061-132">Cet exemple contient une `while` instruction avec une `for` instruction :</span><span class="sxs-lookup"><span data-stu-id="d9061-132">This example has a `while` statement with a `for` statement:</span></span>

```powershell
:myLabel while (<condition 1>) {
  for ($item in $items) {
    if (<condition 2>) {
      break myLabel
    }
    $item = $x   # A statement inside the For-loop
  }
}
$a = $c  # A statement after the labeled While-loop
```

<span data-ttu-id="d9061-133">Si la condition 2 prend la **valeur true** , l’exécution du script passe à l’instruction qui suit la boucle étiquetée.</span><span class="sxs-lookup"><span data-stu-id="d9061-133">If condition 2 evaluates to **True** , the execution of the script skips down to the statement after the labeled loop.</span></span> <span data-ttu-id="d9061-134">Dans l’exemple, l’exécution recommence avec l’instruction `$a = $c` .</span><span class="sxs-lookup"><span data-stu-id="d9061-134">In the example, execution starts again with the statement `$a = $c`.</span></span>

<span data-ttu-id="d9061-135">Vous pouvez imbriquer de nombreuses boucles étiquetées, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d9061-135">You can nest many labeled loops, as shown in the following example.</span></span>

```powershell
:red while (<condition1>) {
  :yellow while (<condition2>) {
    while (<condition3>) {
      if ($a) {break}
      if ($b) {break red}
      if ($c) {break yellow}
    }
    Write-Host "After innermost loop"
  }
  Write-Host "After yellow loop"
}
Write-Host "After red loop"
```

<span data-ttu-id="d9061-136">Si la `$b` variable prend la valeur true, l’exécution du script reprend après la boucle étiquetée « Red ».</span><span class="sxs-lookup"><span data-stu-id="d9061-136">If the `$b` variable evaluates to True, execution of the script resumes after the loop that is labeled "red".</span></span> <span data-ttu-id="d9061-137">Si la `$c` variable prend la valeur true, l’exécution du contrôle de script reprend après la boucle étiquetée « Yellow ».</span><span class="sxs-lookup"><span data-stu-id="d9061-137">If the `$c` variable evaluates to True, execution of the script control resumes after the loop that is labeled "yellow".</span></span>

<span data-ttu-id="d9061-138">Si la `$a` variable prend la valeur true, l’exécution reprend après la boucle la plus profonde.</span><span class="sxs-lookup"><span data-stu-id="d9061-138">If the `$a` variable evaluates to True, execution resumes after the innermost loop.</span></span> <span data-ttu-id="d9061-139">Aucune étiquette n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d9061-139">No label is needed.</span></span>

<span data-ttu-id="d9061-140">PowerShell ne limite pas la manière dont les étiquettes peuvent reprendre l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d9061-140">PowerShell does not limit how far labels can resume execution.</span></span> <span data-ttu-id="d9061-141">L’étiquette peut même passer le contrôle entre les limites d’appel de script et de fonction.</span><span class="sxs-lookup"><span data-stu-id="d9061-141">The label can even pass control across script and function call boundaries.</span></span>

## <a name="using-break-in-a-switch-statement"></a><span data-ttu-id="d9061-142">Utilisation de Break dans une instruction switch</span><span class="sxs-lookup"><span data-stu-id="d9061-142">Using break in a switch statement</span></span>

<span data-ttu-id="d9061-143">Dans une `switch` construction, `break` fait en sorte que PowerShell quitte le `switch` bloc de code.</span><span class="sxs-lookup"><span data-stu-id="d9061-143">In a `switch`construct, `break` causes PowerShell to exit the `switch` code block.</span></span>

<span data-ttu-id="d9061-144">Le `break` mot clé est utilisé pour conserver la `switch` construction.</span><span class="sxs-lookup"><span data-stu-id="d9061-144">The `break` keyword is used to leave the `switch` construct.</span></span> <span data-ttu-id="d9061-145">Par exemple, l' `switch` instruction suivante utilise des `break` instructions pour tester la condition la plus spécifique :</span><span class="sxs-lookup"><span data-stu-id="d9061-145">For example, the following `switch` statement uses `break` statements to test for the most specific condition:</span></span>

```powershell
$var = "word2"
switch -regex ($var) {
    "word2" {
      Write-Host "Exact" $_
      break
    }

    "word.*" {
      Write-Host "Match on the prefix" $_
      break
    }

    "w.*" {
      Write-Host "Match on at least the first letter" $_
      break
    }

    default {
      Write-Host "No match" $_
      break
    }
}
```

<span data-ttu-id="d9061-146">Dans cet exemple, la `$var` variable est créée et initialisée avec une valeur de chaîne de `word2` .</span><span class="sxs-lookup"><span data-stu-id="d9061-146">In this example, the `$var` variable is created and initialized to a string value of `word2`.</span></span> <span data-ttu-id="d9061-147">L' `switch` instruction utilise la classe **Regex** pour faire correspondre d’abord la valeur de la variable au terme `word2` .</span><span class="sxs-lookup"><span data-stu-id="d9061-147">The `switch` statement uses the **Regex** class to match the variable value first with the term `word2`.</span></span> <span data-ttu-id="d9061-148">Étant donné que la valeur de la variable et le premier test de l' `switch` instruction correspondent, le premier bloc de code de l' `switch` instruction s’exécute.</span><span class="sxs-lookup"><span data-stu-id="d9061-148">Because the variable value and the first test in the `switch` statement match, the first code block in the `switch` statement runs.</span></span>

<span data-ttu-id="d9061-149">Lorsque PowerShell atteint la première `break` instruction, l' `switch` instruction se termine.</span><span class="sxs-lookup"><span data-stu-id="d9061-149">When PowerShell reaches the first `break` statement, the `switch` statement exits.</span></span> <span data-ttu-id="d9061-150">Si les quatre `break` instructions sont supprimées de l’exemple, les quatre conditions sont remplies.</span><span class="sxs-lookup"><span data-stu-id="d9061-150">If the four `break` statements are removed from the example, all four conditions are met.</span></span> <span data-ttu-id="d9061-151">L’exemple suivant utilise l' `break` instruction pour afficher les résultats lorsque la condition la plus spécifique est remplie.</span><span class="sxs-lookup"><span data-stu-id="d9061-151">This example uses the `break` statement to display results when the most specific condition is met.</span></span>

## <a name="using-break-in-a-trap-statement"></a><span data-ttu-id="d9061-152">Utilisation de Break dans une instruction Trap</span><span class="sxs-lookup"><span data-stu-id="d9061-152">Using break in a trap statement</span></span>

<span data-ttu-id="d9061-153">Si la dernière instruction exécutée dans le corps d’une `trap` instruction est `break` , l’objet d’erreur est supprimé et l’exception est de nouveau levée.</span><span class="sxs-lookup"><span data-stu-id="d9061-153">If the final statement executed in the body of a `trap` statement is `break`, the error object is suppressed and the exception is re-thrown.</span></span>

<span data-ttu-id="d9061-154">L’exemple suivant crée une exception **DivideByZeroException** qui est interceptée à l’aide de l' `trap` instruction.</span><span class="sxs-lookup"><span data-stu-id="d9061-154">The following example create a **DivideByZeroException** exception that is trapped using the `trap` statement.</span></span>

```powershell
function test {
  trap [DivideByZeroException] {
    Write-Host 'divide by zero trapped'
    break
  }

  $i = 3
  'Before loop'
  while ($true) {
     "1 / $i = " + (1 / $i--)
  }
  'After loop'
}
test
```

Notez que l’exécution s’arrête à l’exception. <span data-ttu-id="d9061-156">`After loop`N’est jamais atteint.</span><span class="sxs-lookup"><span data-stu-id="d9061-156">The `After loop` is never reached.</span></span>
<span data-ttu-id="d9061-157">L’exception est à nouveau levée après l' `trap` exécution de.</span><span class="sxs-lookup"><span data-stu-id="d9061-157">The exception is re-thrown after the `trap` executes.</span></span>

```Output
Before loop
1 / 3 = 0.333333333333333
1 / 2 = 0.5
1 / 1 = 1
divide by zero trapped
ParentContainsErrorRecordException:
Line |
  10 |       "1 / $i = " + (1 / $i--)
     |       ~~~~~~~~~~~~~~~~~~~~~~~~
     | Attempted to divide by zero.
```

## <a name="do-not-use-break-outside-of-a-loop-switch-or-trap"></a><span data-ttu-id="d9061-158">N’utilisez pas de saut en dehors d’une boucle, d’un commutateur ou d’une interruption</span><span class="sxs-lookup"><span data-stu-id="d9061-158">Do not use break outside of a loop, switch, or trap</span></span>

<span data-ttu-id="d9061-159">Quand `break` est utilisé en dehors d’une construction qui le prend directement en charge (boucles, `switch` , `trap` ), PowerShell recherche _la pile des appels_ pour une construction englobante.</span><span class="sxs-lookup"><span data-stu-id="d9061-159">When `break` is used outside of a construct that directly supports it (loops, `switch`, `trap`), PowerShell looks _up the call stack_ for an enclosing construct.</span></span> <span data-ttu-id="d9061-160">S’il ne trouve pas de construction englobante, l’instance d’exécution actuelle est arrêtée en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="d9061-160">If it can't find an enclosing construct, the current runspace is quietly terminated.</span></span>

<span data-ttu-id="d9061-161">Cela signifie que les fonctions et les scripts qui utilisent par inadvertance un `break` en dehors d’une construction englobante qui la prend en charge peuvent mettre fin par inadvertance à leurs _appelants_ .</span><span class="sxs-lookup"><span data-stu-id="d9061-161">This means that functions and scripts that inadvertently use a `break` outside of an enclosing construct that supports it can inadvertently terminate their _callers_ .</span></span>

<span data-ttu-id="d9061-162">L’utilisation `break` de l’intérieur d’un pipeline `break` , tel qu’un `ForEach-Object` bloc de script, non seulement quitte le pipeline, mais il peut mettre fin à la totalité de l’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d9061-162">Using `break` inside a pipeline `break`, such as a `ForEach-Object` script block, not only exits the pipeline, it potentially terminates the entire runspace.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9061-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9061-163">See also</span></span>

[<span data-ttu-id="d9061-164">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="d9061-164">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="d9061-165">about_Continue</span><span class="sxs-lookup"><span data-stu-id="d9061-165">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="d9061-166">about_For</span><span class="sxs-lookup"><span data-stu-id="d9061-166">about_For</span></span>](about_For.md)

[<span data-ttu-id="d9061-167">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="d9061-167">about_Foreach</span></span>](about_Foreach.md)

[<span data-ttu-id="d9061-168">about_Switch</span><span class="sxs-lookup"><span data-stu-id="d9061-168">about_Switch</span></span>](about_Switch.md)

[<span data-ttu-id="d9061-169">about_Throw</span><span class="sxs-lookup"><span data-stu-id="d9061-169">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="d9061-170">about_Trap</span><span class="sxs-lookup"><span data-stu-id="d9061-170">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="d9061-171">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="d9061-171">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)

[<span data-ttu-id="d9061-172">about_While</span><span class="sxs-lookup"><span data-stu-id="d9061-172">about_While</span></span>](about_While.md)
