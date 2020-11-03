---
description: Décrit une commande de langage que vous pouvez utiliser pour exécuter des listes d’instructions basées sur les résultats d’un ou plusieurs tests conditionnels.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_If
ms.openlocfilehash: 33c0050cb5f8c3dfa623213b288ef3a84d10099d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206725"
---
# <a name="about-if"></a><span data-ttu-id="03156-104">À propos de si</span><span class="sxs-lookup"><span data-stu-id="03156-104">About If</span></span>

## <a name="short-description"></a><span data-ttu-id="03156-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="03156-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="03156-106">Décrit une commande de langage que vous pouvez utiliser pour exécuter des listes d’instructions basées sur les résultats d’un ou plusieurs tests conditionnels.</span><span class="sxs-lookup"><span data-stu-id="03156-106">Describes a language command you can use to run statement lists based on the results of one or more conditional tests.</span></span>

## <a name="long-description"></a><span data-ttu-id="03156-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="03156-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="03156-108">Vous pouvez utiliser l' `If` instruction pour exécuter des blocs de code si un test conditionnel spécifié prend la valeur true.</span><span class="sxs-lookup"><span data-stu-id="03156-108">You can use the `If` statement to run code blocks if a specified conditional test evaluates to true.</span></span> <span data-ttu-id="03156-109">Vous pouvez également spécifier un ou plusieurs tests conditionnels supplémentaires à exécuter si tous les tests précédents ont la valeur false.</span><span class="sxs-lookup"><span data-stu-id="03156-109">You can also specify one or more additional conditional tests to run if all the prior tests evaluate to false.</span></span> <span data-ttu-id="03156-110">Enfin, vous pouvez spécifier un bloc de code supplémentaire qui est exécuté si aucun autre test conditionnel antérieur ne prend la valeur true.</span><span class="sxs-lookup"><span data-stu-id="03156-110">Finally, you can specify an additional code block that is run if no other prior conditional test evaluates to true.</span></span>

### <a name="syntax"></a><span data-ttu-id="03156-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03156-111">Syntax</span></span>

<span data-ttu-id="03156-112">L’exemple suivant illustre la `If` syntaxe de l’instruction :</span><span class="sxs-lookup"><span data-stu-id="03156-112">The following example shows the `If` statement syntax:</span></span>

```powershell
if (<test1>)
    {<statement list 1>}
[elseif (<test2>)
    {<statement list 2>}]
[else
    {<statement list 3>}]
```

<span data-ttu-id="03156-113">Lorsque vous exécutez une `If` instruction, PowerShell évalue l' `<test1>` expression conditionnelle comme true ou false.</span><span class="sxs-lookup"><span data-stu-id="03156-113">When you run an `If` statement, PowerShell evaluates the `<test1>` conditional expression as true or false.</span></span> <span data-ttu-id="03156-114">Si `<test1>` a la valeur true, `<statement list 1>` s’exécute et PowerShell quitte l' `If` instruction.</span><span class="sxs-lookup"><span data-stu-id="03156-114">If `<test1>` is true, `<statement list 1>` runs, and PowerShell exits the `If` statement.</span></span> <span data-ttu-id="03156-115">Si `<test1>` a la valeur false, PowerShell évalue la condition spécifiée par l' `<test2>` instruction conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="03156-115">If `<test1>` is false, PowerShell evaluates the condition specified by the `<test2>` conditional statement.</span></span>

<span data-ttu-id="03156-116">Si `<test2>` a la valeur true, `<statement list 2>` s’exécute et PowerShell quitte l' `If` instruction.</span><span class="sxs-lookup"><span data-stu-id="03156-116">If `<test2>` is true, `<statement list 2>` runs, and PowerShell exits the `If` statement.</span></span> <span data-ttu-id="03156-117">Si `<test1>` et ont tous deux `<test2>` la valeur false, le `<statement list 3` bloc de code> s’exécute et PowerShell quitte l’instruction if.</span><span class="sxs-lookup"><span data-stu-id="03156-117">If both `<test1>` and `<test2>` evaluate to false, the `<statement list 3`> code block runs, and PowerShell exits the If statement.</span></span>

<span data-ttu-id="03156-118">Vous pouvez utiliser plusieurs instructions ElseIf pour chaîner une série de tests conditionnels.</span><span class="sxs-lookup"><span data-stu-id="03156-118">You can use multiple Elseif statements to chain a series of conditional tests.</span></span> <span data-ttu-id="03156-119">Par conséquent, chaque test est exécuté uniquement si tous les tests précédents ont la valeur false.</span><span class="sxs-lookup"><span data-stu-id="03156-119">So, that each test is run only if all the previous tests are false.</span></span>
<span data-ttu-id="03156-120">Si vous avez besoin de créer une `If` instruction qui contient de nombreuses instructions ElseIf, envisagez d’utiliser une instruction switch à la place.</span><span class="sxs-lookup"><span data-stu-id="03156-120">If you need to create an `If` statement that contains many Elseif statements, consider using a Switch statement instead.</span></span>

<span data-ttu-id="03156-121">Exemples :</span><span class="sxs-lookup"><span data-stu-id="03156-121">Examples:</span></span>

<span data-ttu-id="03156-122">L’instruction la plus simple `If` contient une seule commande et ne contient aucune instruction ElseIf, ni aucune instruction Else.</span><span class="sxs-lookup"><span data-stu-id="03156-122">The simplest `If` statement contains a single command and does not contain any Elseif statements or any Else statements.</span></span> <span data-ttu-id="03156-123">L’exemple suivant montre la forme la plus simple de l' `If` instruction :</span><span class="sxs-lookup"><span data-stu-id="03156-123">The following example shows the simplest form of the `If` statement:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
```

<span data-ttu-id="03156-124">Dans cet exemple, si la variable $a est supérieure à 2, la condition prend la valeur true et la liste d’instructions est exécutée.</span><span class="sxs-lookup"><span data-stu-id="03156-124">In this example, if the $a variable is greater than 2, the condition evaluates to true, and the statement list runs.</span></span> <span data-ttu-id="03156-125">Toutefois, si $a est inférieur ou égal à 2 ou qu’il ne s’agit pas d’une variable existante, l' `If` instruction n’affiche pas de message.</span><span class="sxs-lookup"><span data-stu-id="03156-125">However, if $a is less than or equal to 2 or is not an existing variable, the `If` statement does not display a message.</span></span>

<span data-ttu-id="03156-126">En ajoutant une instruction Else, un message s’affiche lorsque $a est inférieur ou égal à 2.</span><span class="sxs-lookup"><span data-stu-id="03156-126">By adding an Else statement, a message is displayed when $a is less than or equal to 2.</span></span> <span data-ttu-id="03156-127">Comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="03156-127">As the next example shows:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
else {
    Write-Host ("The value $a is less than or equal to 2," +
        " is not created or is not initialized.")
}
```

<span data-ttu-id="03156-128">Pour affiner cet exemple, vous pouvez utiliser l’instruction ElseIf pour afficher un message lorsque la valeur de $a est égale à 2.</span><span class="sxs-lookup"><span data-stu-id="03156-128">To further refine this example, you can use the Elseif statement to display a message when the value of $a is equal to 2.</span></span> <span data-ttu-id="03156-129">Comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="03156-129">As the next example shows:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
elseif ($a -eq 2) {
    Write-Host "The value $a is equal to 2."
}
else {
    Write-Host ("The value $a is less than 2 or" +
        " was not created or initialized.")
}
```

### <a name="using-the-ternary-operator-syntax"></a><span data-ttu-id="03156-130">Utilisation de la syntaxe d’opérateur ternaire</span><span class="sxs-lookup"><span data-stu-id="03156-130">Using the ternary operator syntax</span></span>

<span data-ttu-id="03156-131">PowerShell 7,0 a introduit une nouvelle syntaxe à l’aide de l’opérateur ternaire.</span><span class="sxs-lookup"><span data-stu-id="03156-131">PowerShell 7.0 introduced a new syntax using the ternary operator.</span></span> <span data-ttu-id="03156-132">Il suit la syntaxe de l’opérateur ternaire C# :</span><span class="sxs-lookup"><span data-stu-id="03156-132">It follows the C# ternary operator syntax:</span></span>

```Syntax
<condition> ? <if-true> : <if-false>
```

<span data-ttu-id="03156-133">L’opérateur ternaire se comporte comme l’instruction simplifiée `if-else` .</span><span class="sxs-lookup"><span data-stu-id="03156-133">The ternary operator behaves like the simplified `if-else` statement.</span></span> <span data-ttu-id="03156-134">L' `<condition>` expression est évaluée et le résultat est converti en valeur booléenne pour déterminer quelle branche doit être évaluée ensuite :</span><span class="sxs-lookup"><span data-stu-id="03156-134">The `<condition>` expression is evaluated and the result is converted to a boolean to determine which branch should be evaluated next:</span></span>

- <span data-ttu-id="03156-135">L’expression `<if-true>` est exécutée si l’expression `<condition>` a la valeur true</span><span class="sxs-lookup"><span data-stu-id="03156-135">The `<if-true>` expression is executed if the `<condition>` expression is true</span></span>
- <span data-ttu-id="03156-136">L’expression `<if-false>` est exécutée si l’expression `<condition>` a la valeur false</span><span class="sxs-lookup"><span data-stu-id="03156-136">The `<if-false>` expression is executed if the `<condition>` expression is false</span></span>

<span data-ttu-id="03156-137">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="03156-137">For example:</span></span>

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

<span data-ttu-id="03156-138">Dans cet exemple, la valeur de `$message` est « Path existing » lorsque `Test-Path` retourne `$true` .</span><span class="sxs-lookup"><span data-stu-id="03156-138">In this example, the value of `$message` is "Path exists" when `Test-Path` returns `$true`.</span></span> <span data-ttu-id="03156-139">Lorsque `Test-Path` retourne `$false` , la valeur de `$message` est « Path introuvable ».</span><span class="sxs-lookup"><span data-stu-id="03156-139">When `Test-Path` returns `$false`, the value of `$message` is "Path not found".</span></span>

```powershell
$service = Get-Service BITS
$service.Status -eq 'Running' ? (Stop-Service $service) : (Start-Service $service)
```

<span data-ttu-id="03156-140">Dans cet exemple, si le service est en cours d’exécution, il est arrêté et, si son état n’est pas **en cours d’exécution** , il est démarré.</span><span class="sxs-lookup"><span data-stu-id="03156-140">In this example, if the service is running, it is stopped, and if its status is not **Running** , it is started.</span></span>

## <a name="see-also"></a><span data-ttu-id="03156-141">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="03156-141">SEE ALSO</span></span>

[<span data-ttu-id="03156-142">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="03156-142">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="03156-143">about_Switch</span><span class="sxs-lookup"><span data-stu-id="03156-143">about_Switch</span></span>](about_Switch.md)

