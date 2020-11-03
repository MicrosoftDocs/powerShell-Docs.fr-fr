---
description: Explique comment utiliser un commutateur pour gérer plusieurs `If` instructions.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 05/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_switch?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Switch
ms.openlocfilehash: 1cb0e95aa942af4aa29f449da0c7cbbaf15d7dc5
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207533"
---
# <a name="about-switch"></a><span data-ttu-id="83929-104">À propos du commutateur</span><span class="sxs-lookup"><span data-stu-id="83929-104">About Switch</span></span>

## <a name="short-description"></a><span data-ttu-id="83929-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="83929-105">Short description</span></span>
<span data-ttu-id="83929-106">Explique comment utiliser un commutateur pour gérer plusieurs `If` instructions.</span><span class="sxs-lookup"><span data-stu-id="83929-106">Explains how to use a switch to handle multiple `If` statements.</span></span>

## <a name="long-description"></a><span data-ttu-id="83929-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="83929-107">Long description</span></span>

<span data-ttu-id="83929-108">Pour vérifier une condition dans un script ou une fonction, utilisez une `If` instruction.</span><span class="sxs-lookup"><span data-stu-id="83929-108">To check a condition in a script or function, use an `If` statement.</span></span> <span data-ttu-id="83929-109">L' `If` instruction peut vérifier de nombreux types de conditions, y compris la valeur des variables et les propriétés des objets.</span><span class="sxs-lookup"><span data-stu-id="83929-109">The `If` statement can check many types of conditions, including the value of variables and the properties of objects.</span></span>

<span data-ttu-id="83929-110">Pour vérifier plusieurs conditions, utilisez une `Switch` instruction.</span><span class="sxs-lookup"><span data-stu-id="83929-110">To check multiple conditions, use a `Switch` statement.</span></span> <span data-ttu-id="83929-111">L' `Switch` instruction est équivalente à une série d' `If` instructions, mais elle est plus simple.</span><span class="sxs-lookup"><span data-stu-id="83929-111">The `Switch` statement is equivalent to a series of `If` statements, but it is simpler.</span></span> <span data-ttu-id="83929-112">L' `Switch` instruction répertorie chaque condition et une action facultative.</span><span class="sxs-lookup"><span data-stu-id="83929-112">The `Switch` statement lists each condition and an optional action.</span></span> <span data-ttu-id="83929-113">Si une condition est obtenue, l’action est effectuée.</span><span class="sxs-lookup"><span data-stu-id="83929-113">If a condition obtains, the action is performed.</span></span>

<span data-ttu-id="83929-114">L' `Switch` instruction peut utiliser les `$_` `$switch` variables automatiques et.</span><span class="sxs-lookup"><span data-stu-id="83929-114">The `Switch` statement can use the `$_` and `$switch` automatic variables.</span></span> <span data-ttu-id="83929-115">Pour plus d’informations, consultez [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="83929-115">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="83929-116">Une instruction de base `Switch` a le format suivant :</span><span class="sxs-lookup"><span data-stu-id="83929-116">A basic `Switch` statement has the following format:</span></span>

```powershell
Switch (<test-value>)
{
    <condition> {<action>}
    <condition> {<action>}
}
```

<span data-ttu-id="83929-117">Par exemple, l' `Switch` instruction suivante compare la valeur de test, 3, à chacune des conditions.</span><span class="sxs-lookup"><span data-stu-id="83929-117">For example, the following `Switch` statement compares the test value, 3, to each of the conditions.</span></span> <span data-ttu-id="83929-118">Lorsque la valeur de test correspond à la condition, l’action est effectuée.</span><span class="sxs-lookup"><span data-stu-id="83929-118">When the test value matches the condition, the action is performed.</span></span>

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
}
```

```Output
It is three.
```

<span data-ttu-id="83929-119">Dans cet exemple simple, la valeur est comparée à chaque condition de la liste, même s’il existe une correspondance pour la valeur 3.</span><span class="sxs-lookup"><span data-stu-id="83929-119">In this simple example, the value is compared to each condition in the list, even though there is a match for the value 3.</span></span> <span data-ttu-id="83929-120">L' `Switch` instruction suivante a deux conditions pour la valeur 3.</span><span class="sxs-lookup"><span data-stu-id="83929-120">The following `Switch` statement has two conditions for a value of 3.</span></span> <span data-ttu-id="83929-121">Il montre que, par défaut, toutes les conditions sont testées.</span><span class="sxs-lookup"><span data-stu-id="83929-121">It demonstrates that, by default, all conditions are tested.</span></span>

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
Three again.
```

<span data-ttu-id="83929-122">Pour indiquer `Switch` à d’arrêter la comparaison après une correspondance, utilisez l' `Break` instruction.</span><span class="sxs-lookup"><span data-stu-id="83929-122">To direct the `Switch` to stop comparing after a match, use the `Break` statement.</span></span> <span data-ttu-id="83929-123">L' `Break` instruction termine l' `Switch` instruction.</span><span class="sxs-lookup"><span data-stu-id="83929-123">The `Break` statement terminates the `Switch` statement.</span></span>

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."; Break}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
```

<span data-ttu-id="83929-124">Si la valeur de test est une collection, telle qu’un tableau, chaque élément de la collection est évalué dans l’ordre dans lequel il apparaît.</span><span class="sxs-lookup"><span data-stu-id="83929-124">If the test value is a collection, such as an array, each item in the collection is evaluated in the order in which it appears.</span></span> <span data-ttu-id="83929-125">Les exemples suivants évaluent 4, puis 2.</span><span class="sxs-lookup"><span data-stu-id="83929-125">The following examples evaluates 4 and then 2.</span></span>

```powershell
switch (4, 2)
{
    1 {"It is one." }
    2 {"It is two." }
    3 {"It is three." }
    4 {"It is four." }
    3 {"Three again."}
}
```

```Output
It is four.
It is two.
```

<span data-ttu-id="83929-126">Toutes les `Break` instructions s’appliquent à la collection, et non à chaque valeur, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="83929-126">Any `Break` statements apply to the collection, not to each value, as shown in the following example.</span></span> <span data-ttu-id="83929-127">L’instruction `Switch` se termine par l' `Break` instruction dans la condition de valeur 4.</span><span class="sxs-lookup"><span data-stu-id="83929-127">The `Switch` statement is terminated by the `Break` statement in the condition of value 4.</span></span>

```powershell
switch (4, 2)
{
    1 {"It is one."; Break}
    2 {"It is two." ; Break }
    3 {"It is three." ; Break }
    4 {"It is four." ; Break }
    3 {"Three again."}
}
```

```Output
It is four.
```

### <a name="syntax"></a><span data-ttu-id="83929-128">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83929-128">Syntax</span></span>

<span data-ttu-id="83929-129">La syntaxe complète de l' `Switch` instruction est la suivante :</span><span class="sxs-lookup"><span data-stu-id="83929-129">The complete `Switch` statement syntax is as follows:</span></span>

```
switch [-regex|-wildcard|-exact][-casesensitive] (<value>)
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

<span data-ttu-id="83929-130">ou</span><span class="sxs-lookup"><span data-stu-id="83929-130">or</span></span>

```
switch [-regex|-wildcard|-exact][-casesensitive] -file filename
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

<span data-ttu-id="83929-131">Si aucun paramètre n’est utilisé, `Switch` se comporte de la même façon que l’utilisation du paramètre **exact** .</span><span class="sxs-lookup"><span data-stu-id="83929-131">If no parameters are used, `Switch` behaves the same as using the **Exact** parameter.</span></span> <span data-ttu-id="83929-132">Elle effectue une correspondance qui ne respecte pas la casse pour la valeur.</span><span class="sxs-lookup"><span data-stu-id="83929-132">It performs a case-insensitive match for the value.</span></span> <span data-ttu-id="83929-133">Si la valeur est une collection, chaque élément est évalué dans l’ordre dans lequel il apparaît.</span><span class="sxs-lookup"><span data-stu-id="83929-133">If the value is a collection, each element is evaluated in the order in which it appears.</span></span>

<span data-ttu-id="83929-134">L' `Switch` instruction doit inclure au moins une instruction de condition.</span><span class="sxs-lookup"><span data-stu-id="83929-134">The `Switch` statement must include at least one condition statement.</span></span>

<span data-ttu-id="83929-135">La `Default` clause est déclenchée lorsque la valeur ne correspond à aucune des conditions.</span><span class="sxs-lookup"><span data-stu-id="83929-135">The `Default` clause is triggered when the value does not match any of the conditions.</span></span> <span data-ttu-id="83929-136">Elle est équivalente à une `Else` clause dans une `If` instruction.</span><span class="sxs-lookup"><span data-stu-id="83929-136">It is equivalent to an `Else` clause in an `If` statement.</span></span> <span data-ttu-id="83929-137">Une seule `Default` clause est autorisée dans chaque `Switch` instruction.</span><span class="sxs-lookup"><span data-stu-id="83929-137">Only one `Default` clause is permitted in each `Switch` statement.</span></span>

<span data-ttu-id="83929-138">`Switch` a les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="83929-138">`Switch` has the following parameters:</span></span>

- <span data-ttu-id="83929-139">**Caractère générique** : indique que la condition est une chaîne de caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="83929-139">**Wildcard** - Indicates that the condition is a wildcard string.</span></span> <span data-ttu-id="83929-140">Si la clause match n’est pas une chaîne, le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="83929-140">If the match clause is not a string, the parameter is ignored.</span></span> <span data-ttu-id="83929-141">La comparaison ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="83929-141">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="83929-142">**Exact** -indique que la clause match, s’il s’agit d’une chaîne, doit correspondre exactement.</span><span class="sxs-lookup"><span data-stu-id="83929-142">**Exact** - Indicates that the match clause, if it is a string, must match exactly.</span></span> <span data-ttu-id="83929-143">Si la clause match n’est pas une chaîne, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="83929-143">If the match clause is not a string, this parameter is ignored.</span></span> <span data-ttu-id="83929-144">La comparaison ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="83929-144">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="83929-145">**CaseSensitive** -effectue une correspondance respectant la casse.</span><span class="sxs-lookup"><span data-stu-id="83929-145">**CaseSensitive** - Performs a case-sensitive match.</span></span> <span data-ttu-id="83929-146">Si la clause match n’est pas une chaîne, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="83929-146">If the match clause is not a string, this parameter is ignored.</span></span>
- <span data-ttu-id="83929-147">**Fichier** : prend une entrée à partir d’un fichier plutôt qu’une instruction de valeur.</span><span class="sxs-lookup"><span data-stu-id="83929-147">**File** - Takes input from a file rather than a value statement.</span></span> <span data-ttu-id="83929-148">Si plusieurs paramètres de **fichier** sont inclus, seul le dernier est utilisé.</span><span class="sxs-lookup"><span data-stu-id="83929-148">If multiple **File** parameters are included, only the last one is used.</span></span> <span data-ttu-id="83929-149">Chaque ligne du fichier est lue et évaluée par l' `Switch` instruction.</span><span class="sxs-lookup"><span data-stu-id="83929-149">Each line of the file is read and evaluated by the `Switch` statement.</span></span> <span data-ttu-id="83929-150">La comparaison ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="83929-150">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="83929-151">**Regex** : effectue la correspondance d’expression régulière de la valeur avec la condition.</span><span class="sxs-lookup"><span data-stu-id="83929-151">**Regex** - Performs regular expression matching of the value to the condition.</span></span> <span data-ttu-id="83929-152">Si la clause match n’est pas une chaîne, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="83929-152">If the match clause is not a string, this parameter is ignored.</span></span>
  <span data-ttu-id="83929-153">La comparaison ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="83929-153">The comparison is case-insensitive.</span></span> <span data-ttu-id="83929-154">La `$matches` variable automatique est disponible pour une utilisation dans le bloc d’instructions correspondant.</span><span class="sxs-lookup"><span data-stu-id="83929-154">The `$matches` automatic variable is available for use within the matching statement block.</span></span>

> [!NOTE]
> <span data-ttu-id="83929-155">Lorsque vous spécifiez des valeurs conflictuelles, comme **Regex** et **caractère générique** , le dernier paramètre spécifié est prioritaire et tous les paramètres en conflit sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="83929-155">When specifying conflicting values, like **Regex** and **Wildcard** , the last parameter specified takes precedence, and all conflicting parameters are ignored.</span></span> <span data-ttu-id="83929-156">Plusieurs instances de paramètres sont également autorisées.</span><span class="sxs-lookup"><span data-stu-id="83929-156">Multiple instances of parameters are also permitted.</span></span> <span data-ttu-id="83929-157">Toutefois, seul le dernier paramètre utilisé est effectif.</span><span class="sxs-lookup"><span data-stu-id="83929-157">However, only the last parameter used is effective.</span></span>

<span data-ttu-id="83929-158">Dans cet exemple, un objet qui n’est pas une chaîne ou des données numériques est passé à l' `Switch` .</span><span class="sxs-lookup"><span data-stu-id="83929-158">In this example, an object that's not a string or numerical data is passed to the `Switch`.</span></span> <span data-ttu-id="83929-159">`Switch`Effectue une contrainte de chaîne sur l’objet et évalue le résultat.</span><span class="sxs-lookup"><span data-stu-id="83929-159">The `Switch` performs a string coercion on the object and evaluates the outcome.</span></span>

```powershell
$test = @{
    Test  = 'test'
    Test2 = 'test2'
}

$test.ToString()

switch -Exact ($test)
{
    'System.Collections.Hashtable'
    {
        'Hashtable string coercion'
    }
    'test'
    {
        'Hashtable value'
    }
}
```

```Output
System.Collections.Hashtable
Hashtable string coercion
```

<span data-ttu-id="83929-160">Dans cet exemple, il n’y a pas de casse correspondante et il n’y a pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="83929-160">In this example, there is no matching case so there is no output.</span></span>

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
}
```

<span data-ttu-id="83929-161">En ajoutant la `Default` clause, vous pouvez effectuer une action quand aucune autre condition ne parvient.</span><span class="sxs-lookup"><span data-stu-id="83929-161">By adding the `Default` clause, you can perform an action when no other conditions succeed.</span></span>

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
    Default {
        "No matches"
    }
}
```

```Output
No matches
```

<span data-ttu-id="83929-162">Pour que le mot « quatorze » corresponde à un cas, vous devez utiliser le `-Wildcard` `-Regex` paramètre ou.</span><span class="sxs-lookup"><span data-stu-id="83929-162">For the word "fourteen" to match a case you must use the `-Wildcard` or `-Regex` parameter.</span></span>

```powershell
   PS> switch -Wildcard ("fourteen")
       {
           1 {"It is one."; Break}
           2 {"It is two."; Break}
           3 {"It is three."; Break}
           4 {"It is four."; Break}
           "fo*" {"That's too many."}
       }
 ```

```Output
That's too many.
```

<span data-ttu-id="83929-163">L’exemple suivant utilise le `-Regex` paramètre.</span><span class="sxs-lookup"><span data-stu-id="83929-163">The following example uses the `-Regex` parameter.</span></span>

```powershell
$target = 'https://bing.com'
switch -Regex ($target)
{
    '^ftp\://.*$' { "$_ is an ftp address"; Break }
    '^\w+@\w+\.com|edu|org$' { "$_ is an email address"; Break }
    '^(http[s]?)\://.*$' { "$_ is a web address that uses $($matches[1])"; Break }
}
```

```Output
https://bing.com is a web address that uses https
```

<span data-ttu-id="83929-164">Une condition de l’instruction switch peut être :</span><span class="sxs-lookup"><span data-stu-id="83929-164">A Switch statement condition may be either:</span></span>

- <span data-ttu-id="83929-165">Expression dont la valeur est comparée à la valeur d’entrée</span><span class="sxs-lookup"><span data-stu-id="83929-165">An expression whose value is compared to the input value</span></span>
- <span data-ttu-id="83929-166">Bloc de script qui doit retourner `$true` si une condition est remplie.</span><span class="sxs-lookup"><span data-stu-id="83929-166">A script block which should return `$true` if a condition is met.</span></span>

<span data-ttu-id="83929-167">La `$_` variable automatique contient la valeur transmise à l’instruction switch et est disponible à des fins d’évaluation et d’utilisation dans l’étendue des instructions de condition.</span><span class="sxs-lookup"><span data-stu-id="83929-167">The `$_` automatic variable contains the value passed to the switch statement and is available for evaluation and use within the scope of the condition statements.</span></span>

<span data-ttu-id="83929-168">L’action pour chaque condition est indépendante des actions dans d’autres conditions.</span><span class="sxs-lookup"><span data-stu-id="83929-168">The action for each condition is independent of the actions in other conditions.</span></span>

<span data-ttu-id="83929-169">L’exemple suivant illustre l’utilisation de blocs de script comme `Switch` conditions d’instruction.</span><span class="sxs-lookup"><span data-stu-id="83929-169">The following example demonstrates the use of script blocks as `Switch` statement conditions.</span></span>

```powershell
switch ("Test")
{
    {$_ -is [String]} {
        "Found a string"
    }
    "Test" {
        "This $_ executes as well"
    }
}
```

```Output
Found a string
This Test executes as well
```

<span data-ttu-id="83929-170">Si la valeur correspond à plusieurs conditions, l’action de chaque condition est exécutée.</span><span class="sxs-lookup"><span data-stu-id="83929-170">If the value matches multiple conditions, the action for each condition is executed.</span></span> <span data-ttu-id="83929-171">Pour modifier ce comportement, utilisez les `Break` `Continue` Mots clés ou.</span><span class="sxs-lookup"><span data-stu-id="83929-171">To change this behavior, use the `Break` or `Continue` keywords.</span></span>

<span data-ttu-id="83929-172">Le `Break` mot clé arrête le traitement et quitte l' `Switch` instruction.</span><span class="sxs-lookup"><span data-stu-id="83929-172">The `Break` keyword stops processing and exits the `Switch` statement.</span></span>

<span data-ttu-id="83929-173">Le `Continue` mot clé arrête le traitement de la valeur actuelle, mais continue le traitement des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="83929-173">The `Continue` keyword stops processing the current value, but continues processing any subsequent values.</span></span>

<span data-ttu-id="83929-174">L’exemple suivant traite un tableau de nombres et s’affiche s’ils sont impairs ou pairs.</span><span class="sxs-lookup"><span data-stu-id="83929-174">The following example processes an array of numbers and displays if they are odd or even.</span></span> <span data-ttu-id="83929-175">Les nombres négatifs sont ignorés par le `Continue` mot clé.</span><span class="sxs-lookup"><span data-stu-id="83929-175">Negative numbers are skipped with the `Continue` keyword.</span></span> <span data-ttu-id="83929-176">Si aucun nombre n’est rencontré, l’exécution se termine par le `Break` mot clé.</span><span class="sxs-lookup"><span data-stu-id="83929-176">If a non-number is encountered, execution is terminated with the `Break` keyword.</span></span>

```powershell
switch (1,4,-1,3,"Hello",2,1)
{
    {$_ -lt 0} { Continue }
    {$_ -isnot [Int32]} { Break }
    {$_ % 2} {
        "$_ is Odd"
    }
    {-not ($_ % 2)} {
        "$_ is Even"
    }
}
```

```Output
1 is Odd
4 is Even
3 is Odd
```

## <a name="see-also"></a><span data-ttu-id="83929-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83929-177">See also</span></span>

[<span data-ttu-id="83929-178">about_Break</span><span class="sxs-lookup"><span data-stu-id="83929-178">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="83929-179">about_Continue</span><span class="sxs-lookup"><span data-stu-id="83929-179">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="83929-180">about_If</span><span class="sxs-lookup"><span data-stu-id="83929-180">about_If</span></span>](about_If.md)

[<span data-ttu-id="83929-181">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="83929-181">about_Script_Blocks</span></span>](about_Script_Blocks.md)
