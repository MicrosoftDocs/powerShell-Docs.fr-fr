---
description: Décrit une commande de langage que vous pouvez utiliser pour exécuter des instructions basées sur un test conditionnel.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 3/4/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_for?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_For
ms.openlocfilehash: 5f4fc025ee36e99de7d2ad7a00b1c1dca9c5ce3f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207105"
---
# <a name="about-for"></a><span data-ttu-id="90e55-104">À propos de pour</span><span class="sxs-lookup"><span data-stu-id="90e55-104">About For</span></span>

## <a name="short-description"></a><span data-ttu-id="90e55-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="90e55-105">Short description</span></span>
<span data-ttu-id="90e55-106">Décrit une commande de langage que vous pouvez utiliser pour exécuter des instructions basées sur un test conditionnel.</span><span class="sxs-lookup"><span data-stu-id="90e55-106">Describes a language command you can use to run statements based on a conditional test.</span></span>

## <a name="long-description"></a><span data-ttu-id="90e55-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="90e55-107">Long description</span></span>

<span data-ttu-id="90e55-108">L' `For` instruction (également appelée `For` boucle) est une construction de langage que vous pouvez utiliser pour créer une boucle qui exécute des commandes dans un bloc de commande alors qu’une condition spécifiée a la valeur `$true` .</span><span class="sxs-lookup"><span data-stu-id="90e55-108">The `For` statement (also known as a `For` loop) is a language construct you can use to create a loop that runs commands in a command block while a specified condition evaluates to `$true`.</span></span>

<span data-ttu-id="90e55-109">Une utilisation courante de la `For` boucle consiste à itérer un tableau de valeurs et à opérer sur un sous-ensemble de ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="90e55-109">A typical use of the `For` loop is to iterate an array of values and to operate on a subset of these values.</span></span> <span data-ttu-id="90e55-110">Dans la plupart des cas, si vous souhaitez itérer toutes les valeurs d’un tableau, envisagez d’utiliser une `Foreach` instruction.</span><span class="sxs-lookup"><span data-stu-id="90e55-110">In most cases, if you want to iterate all the values in an array, consider using a `Foreach` statement.</span></span>

### <a name="syntax"></a><span data-ttu-id="90e55-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90e55-111">Syntax</span></span>

<span data-ttu-id="90e55-112">L’exemple suivant illustre la syntaxe de l' `For` instruction.</span><span class="sxs-lookup"><span data-stu-id="90e55-112">The following shows the `For` statement syntax.</span></span>

```
for (<Init>; <Condition>; <Repeat>)
{
    <Statement list>
}
```

<span data-ttu-id="90e55-113">L’espace réservé **init** représente une ou plusieurs commandes qui sont exécutées avant le début de la boucle.</span><span class="sxs-lookup"><span data-stu-id="90e55-113">The **Init** placeholder represents one or more commands that are run before the loop begins.</span></span> <span data-ttu-id="90e55-114">En général, vous utilisez la partie **init** de l’instruction pour créer et initialiser une variable avec une valeur de départ.</span><span class="sxs-lookup"><span data-stu-id="90e55-114">You typically use the **Init** portion of the statement to create and initialize a variable with a starting value.</span></span>

<span data-ttu-id="90e55-115">Cette variable sera ensuite la base de la condition à tester dans la partie suivante de l' `For` instruction.</span><span class="sxs-lookup"><span data-stu-id="90e55-115">This variable will then be the basis for the condition to be tested in the next portion of the `For` statement.</span></span>

<span data-ttu-id="90e55-116">L’espace réservé de **condition** représente la partie de l' `For` instruction qui correspond à une `$true` valeur `$false` **booléenne** ou.</span><span class="sxs-lookup"><span data-stu-id="90e55-116">The **Condition** placeholder represents the portion of the `For` statement that resolves to a `$true` or `$false` **Boolean** value.</span></span> <span data-ttu-id="90e55-117">PowerShell évalue la condition chaque fois que la `For` boucle s’exécute.</span><span class="sxs-lookup"><span data-stu-id="90e55-117">PowerShell evaluates the condition each time the `For` loop runs.</span></span> <span data-ttu-id="90e55-118">Si l’instruction est `$true` , les commandes du bloc de commande s’exécutent et l’instruction est de nouveau évaluée.</span><span class="sxs-lookup"><span data-stu-id="90e55-118">If the statement is `$true`, the commands in the command block run, and the statement is evaluated again.</span></span> <span data-ttu-id="90e55-119">Si la condition est toujours `$true` , les commandes de la **liste d’instructions** s’exécutent à nouveau.</span><span class="sxs-lookup"><span data-stu-id="90e55-119">If the condition is still `$true`, the commands in the **Statement list** run again.</span></span> <span data-ttu-id="90e55-120">La boucle est répétée jusqu’à ce que la condition devienne `$false` .</span><span class="sxs-lookup"><span data-stu-id="90e55-120">The loop is repeated until the condition becomes `$false`.</span></span>

<span data-ttu-id="90e55-121">L’espace réservé **REPEAT** représente une ou plusieurs commandes, séparées par des virgules, qui sont exécutées chaque fois que la boucle se répète.</span><span class="sxs-lookup"><span data-stu-id="90e55-121">The **Repeat** placeholder represents one or more commands, separated by commas, that are executed each time the loop repeats.</span></span> <span data-ttu-id="90e55-122">En général, il est utilisé pour modifier une variable qui est testée à l’intérieur de la partie **condition** de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="90e55-122">Typically, this is used to modify a variable that is tested inside the **Condition** part of the statement.</span></span>

<span data-ttu-id="90e55-123">L’espace réservé de la **liste d’instructions** représente un ensemble d’une ou plusieurs commandes qui sont exécutées chaque fois que la boucle est entrée ou répétée.</span><span class="sxs-lookup"><span data-stu-id="90e55-123">The **Statement list** placeholder represents a set of one or more commands that are run each time the loop is entered or repeated.</span></span> <span data-ttu-id="90e55-124">Le contenu de la **liste d’instructions** est entouré d’accolades.</span><span class="sxs-lookup"><span data-stu-id="90e55-124">The contents of the **Statement list** are surrounded by braces.</span></span>

### <a name="support-for-multiple-operations"></a><span data-ttu-id="90e55-125">Prise en charge de plusieurs opérations</span><span class="sxs-lookup"><span data-stu-id="90e55-125">Support for multiple operations</span></span>

<span data-ttu-id="90e55-126">Les syntaxes suivantes sont prises en charge pour les opérations d’assignation multiples dans l’instruction **init** :</span><span class="sxs-lookup"><span data-stu-id="90e55-126">The following syntaxes are supported for multiple assignment operations in the **Init** statement:</span></span>

```powershell
# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}
```

<span data-ttu-id="90e55-127">Les syntaxes suivantes sont prises en charge pour les opérations d’assignation multiples dans l’instruction **REPEAT** :</span><span class="sxs-lookup"><span data-stu-id="90e55-127">The following syntaxes are supported for multiple assignment operations in the **Repeat** statement:</span></span>

```powershell
# Comma separated assignment expressions.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; ($i++), ($j++))
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $($i++;$j++))
{
    "`$i:$i"
    "`$j:$j"
}
```

> [!NOTE]
> <span data-ttu-id="90e55-128">Les opérations autres que pre ou after Increment peuvent ne pas fonctionner avec toutes les syntaxes.</span><span class="sxs-lookup"><span data-stu-id="90e55-128">Operations other than pre or post increment may not work with all syntaxes.</span></span>

<span data-ttu-id="90e55-129">Pour plusieurs **conditions** , utilisez des opérateurs logiques, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="90e55-129">For multiple **Conditions** use logical operators as demonstrated by the following example.</span></span>

```powershell
for (($i = 0), ($j = 0); $i -lt 10 -and $j -lt 10; $i++,$j++)
{
    "`$i:$i"
    "`$j:$j"
}
```

<span data-ttu-id="90e55-130">Pour plus d’informations, consultez [about_Logical_Operators](about_Logical_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="90e55-130">For more information, see [about_Logical_Operators](about_Logical_Operators.md).</span></span>

### <a name="examples"></a><span data-ttu-id="90e55-131">Exemples</span><span class="sxs-lookup"><span data-stu-id="90e55-131">Examples</span></span>

<span data-ttu-id="90e55-132">Au minimum, une `For` instruction requiert la parenthèse entourant les éléments **init** , **condition** et **REPEAT** de l’instruction et une commande placée entre accolades dans la partie de la **liste d’instructions** de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="90e55-132">At a minimum, a `For` statement requires the parenthesis surrounding the **Init** , **Condition** , and **Repeat** part of the statement and a command surrounded by braces in the **Statement list** part of the statement.</span></span>

<span data-ttu-id="90e55-133">Notez que les exemples à venir montrent intentionnellement du code en dehors de l' `For` instruction.</span><span class="sxs-lookup"><span data-stu-id="90e55-133">Note that the upcoming examples intentionally show code outside the `For` statement.</span></span> <span data-ttu-id="90e55-134">Dans des exemples ultérieurs, le code est intégré à l' `For` instruction.</span><span class="sxs-lookup"><span data-stu-id="90e55-134">In later examples, code is integrated into the `For` statement.</span></span>

<span data-ttu-id="90e55-135">Par exemple, l' `For` instruction suivante affiche continuellement la valeur de la `$i` variable jusqu’à ce que vous sautiez manuellement de la commande en appuyant sur Ctrl + C.</span><span class="sxs-lookup"><span data-stu-id="90e55-135">For example, the following `For` statement continually displays the value of the `$i` variable until you manually break out of the command by pressing CTRL+C.</span></span>

```powershell
$i = 1
for (;;)
{
    Write-Host $i
}
```

<span data-ttu-id="90e55-136">Vous pouvez ajouter des commandes supplémentaires à la liste d’instructions afin que la valeur de `$i` soit incrémentée de 1 chaque fois que la boucle est exécutée, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="90e55-136">You can add additional commands to the statement list so that the value of `$i` is incremented by 1 each time the loop is run, as the following example shows.</span></span>

```powershell
for (;;)
{
    $i++; Write-Host $i
}
```

<span data-ttu-id="90e55-137">Jusqu’à sortir de la commande en appuyant sur CTRL + C, cette instruction affiche continuellement la valeur de la `$i` variable, car elle est incrémentée de 1 chaque fois que la boucle est exécutée.</span><span class="sxs-lookup"><span data-stu-id="90e55-137">Until you break out of the command by pressing CTRL+C, this statement will continually display the value of the `$i` variable as it is incremented by 1 each time the loop is run.</span></span>

<span data-ttu-id="90e55-138">Au lieu de modifier la valeur de la variable dans la partie de la liste d’instructions de l' `For` instruction, vous pouvez utiliser la portion **REPEAT** de l' `For` instruction à la place, comme suit.</span><span class="sxs-lookup"><span data-stu-id="90e55-138">Rather than change the value of the variable in the statement list part of the `For` statement, you can use the **Repeat** portion of the `For` statement instead, as follows.</span></span>

```powershell
$i=1
for (;;$i++)
{
    Write-Host $i
}
```

<span data-ttu-id="90e55-139">Cette instruction se répète toujours indéfiniment jusqu’à sortir de la commande en appuyant sur CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="90e55-139">This statement will still repeat indefinitely until you break out of the command by pressing CTRL+C.</span></span>

<span data-ttu-id="90e55-140">Vous pouvez arrêter la `For` boucle à l’aide d’une *condition* .</span><span class="sxs-lookup"><span data-stu-id="90e55-140">You can terminate the `For` loop using a *condition* .</span></span> <span data-ttu-id="90e55-141">Vous pouvez placer une condition à l’aide de la partie **condition** de l' `For` instruction.</span><span class="sxs-lookup"><span data-stu-id="90e55-141">You can place a condition using the **Condition** portion of the `For` statement.</span></span> <span data-ttu-id="90e55-142">La `For` boucle se termine lorsque la condition prend la valeur `$false` .</span><span class="sxs-lookup"><span data-stu-id="90e55-142">The `For` loop terminates when the condition evaluates to `$false`.</span></span>

<span data-ttu-id="90e55-143">Dans l’exemple suivant, la `For` boucle s’exécute tandis que la valeur de `$i` est inférieure ou égale à 10.</span><span class="sxs-lookup"><span data-stu-id="90e55-143">In the following example, the `For` loop runs while the value of `$i` is less than or equal to 10.</span></span>

```powershell
$i=1
for(;$i -le 10;$i++)
{
    Write-Host $i
}
```

<span data-ttu-id="90e55-144">Au lieu de créer et d’initialiser la variable en dehors de l' `For` instruction, vous pouvez effectuer cette tâche à l’intérieur de la boucle à l' `For` aide de la partie **init** de l' `For` instruction.</span><span class="sxs-lookup"><span data-stu-id="90e55-144">Instead of creating and initializing the variable outside the `For` statement, you can perform this task inside the `For` loop by using the **Init** portion of the `For` statement.</span></span>

```powershell
for($i=1; $i -le 10; $i++){Write-Host $i}
```

<span data-ttu-id="90e55-145">Vous pouvez utiliser des retours chariot plutôt que des points-virgules pour délimiter les portions **init** , **condition** et **REPEAT** de l' `For` instruction.</span><span class="sxs-lookup"><span data-stu-id="90e55-145">You can use carriage returns instead of semicolons to delimit the **Init** , **Condition** , and **Repeat** portions of the `For` statement.</span></span> <span data-ttu-id="90e55-146">L’exemple suivant montre un `For` qui utilise cette syntaxe alternative.</span><span class="sxs-lookup"><span data-stu-id="90e55-146">The following example shows a `For` that uses this alternative syntax.</span></span>

```powershell
for ($i = 0
  $i -lt 10
  $i++){
  $i
}
```

<span data-ttu-id="90e55-147">Cette autre forme de l' `For` instruction fonctionne dans les fichiers de script PowerShell et à l’invite de commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="90e55-147">This alternative form of the `For` statement works in PowerShell script files and at the PowerShell command prompt.</span></span> <span data-ttu-id="90e55-148">Toutefois, il est plus facile d’utiliser la `For` syntaxe de l’instruction avec des points-virgules lorsque vous entrez des commandes interactives à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="90e55-148">However, it is easier to use the `For` statement syntax with semicolons when you enter interactive commands at the command prompt.</span></span>

<span data-ttu-id="90e55-149">La `For` boucle est plus flexible que la `Foreach` boucle, car elle vous permet d’incrémenter des valeurs dans un tableau ou une collection à l’aide de modèles.</span><span class="sxs-lookup"><span data-stu-id="90e55-149">The `For` loop is more flexible than the `Foreach` loop because it allows you to increment values in an array or collection by using patterns.</span></span> <span data-ttu-id="90e55-150">Dans l’exemple suivant, la `$i` variable est incrémentée de 2 dans la partie **REPEAT** de l' `For` instruction.</span><span class="sxs-lookup"><span data-stu-id="90e55-150">In the following example, the `$i` variable is incremented by 2 in the **Repeat** portion of the `For` statement.</span></span>

```powershell
for ($i = 0; $i -le 20; $i += 2)
{
    Write-Host $i
}
```

<span data-ttu-id="90e55-151">La `For` boucle peut également être écrite sur une ligne comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="90e55-151">The `For` loop can also be written on one line as in the following example.</span></span>

```powershell
for ($i = 0; $i -lt 10; $i++) { Write-Host $i }
```

## <a name="see-also"></a><span data-ttu-id="90e55-152">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="90e55-152">SEE ALSO</span></span>

[<span data-ttu-id="90e55-153">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="90e55-153">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="90e55-154">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="90e55-154">about_Foreach</span></span>](about_Foreach.md)
