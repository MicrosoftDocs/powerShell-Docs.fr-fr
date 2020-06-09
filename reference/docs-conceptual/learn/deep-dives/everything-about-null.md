---
title: Tout ce que vous avez toujours voulu savoir sur $null
description: La variable PowerShell $null semble souvent être simple, mais elle présente de nombreuses subtilités. Examinons $null pour savoir ce qui se passe quand vous rencontrez de manière inattendue une valeur Null.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: e0553a5e17450d8044f548792649369e99903850
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149472"
---
# <a name="everything-you-wanted-to-know-about-null"></a><span data-ttu-id="faa9a-104">Tout ce que vous avez toujours voulu savoir sur $null</span><span class="sxs-lookup"><span data-stu-id="faa9a-104">Everything you wanted to know about $null</span></span>

<span data-ttu-id="faa9a-105">La variable PowerShell `$null` semble souvent être simple, mais elle présente de nombreuses subtilités.</span><span class="sxs-lookup"><span data-stu-id="faa9a-105">The PowerShell `$null` often appears to be simple but it has a lot of nuances.</span></span> <span data-ttu-id="faa9a-106">Examinons `$null` pour savoir ce qui se passe quand vous rencontrez de manière inattendue une valeur `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-106">Let's take a close look at `$null` so you know what happens when you unexpectedly run into a `$null` value.</span></span>

> [!NOTE]
> <span data-ttu-id="faa9a-107">La [version d’origine][] de cet article est apparue sur le blog écrit par [@KevinMarquette][].</span><span class="sxs-lookup"><span data-stu-id="faa9a-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="faa9a-108">L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu avec nous.</span><span class="sxs-lookup"><span data-stu-id="faa9a-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="faa9a-109">Consultez son blog à l’adresse [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="faa9a-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-null"></a><span data-ttu-id="faa9a-110">Qu’est-ce qu’une valeur Null ?</span><span class="sxs-lookup"><span data-stu-id="faa9a-110">What is NULL?</span></span>

<span data-ttu-id="faa9a-111">Vous pouvez considérer Null comme une valeur inconnue ou vide.</span><span class="sxs-lookup"><span data-stu-id="faa9a-111">You can think of NULL as an unknown or empty value.</span></span> <span data-ttu-id="faa9a-112">Une variable a la valeur Null tant que vous ne lui avez pas attribué une valeur ou un objet.</span><span class="sxs-lookup"><span data-stu-id="faa9a-112">A variable is NULL until you assign a value or an object to it.</span></span> <span data-ttu-id="faa9a-113">Cela peut être important car certaines commandes exige une valeur et génèrent des erreurs si la valeur est Null.</span><span class="sxs-lookup"><span data-stu-id="faa9a-113">This can be important because there are some commands that require a value and generate errors if the value is NULL.</span></span>

### <a name="powershell-null"></a><span data-ttu-id="faa9a-114">Variable PowerShell $null</span><span class="sxs-lookup"><span data-stu-id="faa9a-114">PowerShell $null</span></span>

<span data-ttu-id="faa9a-115">`$null` est une variable automatique de PowerShell utilisée pour représenter une valeur Null.</span><span class="sxs-lookup"><span data-stu-id="faa9a-115">`$null` is an automatic variable in PowerShell used to represent NULL.</span></span> <span data-ttu-id="faa9a-116">Vous pouvez l’affecter à des variables, l’utiliser dans des comparaisons et l’utiliser comme espace réservé pour une valeur Null dans une collection.</span><span class="sxs-lookup"><span data-stu-id="faa9a-116">You can assign it to variables, use it in comparisons and use it as a place holder for NULL in a collection.</span></span>

<span data-ttu-id="faa9a-117">PowerShell traite `$null` comme un objet avec une valeur Null.</span><span class="sxs-lookup"><span data-stu-id="faa9a-117">PowerShell treats `$null` as an object with a value of NULL.</span></span> <span data-ttu-id="faa9a-118">C’est différent de ce que vous pouvez attendre si vous êtes habitué à un autre langage.</span><span class="sxs-lookup"><span data-stu-id="faa9a-118">This is different than what you may expect if you come from another language.</span></span>

## <a name="examples-of-null"></a><span data-ttu-id="faa9a-119">Exemples de variable $null</span><span class="sxs-lookup"><span data-stu-id="faa9a-119">Examples of $null</span></span>

<span data-ttu-id="faa9a-120">Chaque fois que vous essayez d’utiliser une variable que vous n’avez pas initialisée, la valeur est `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-120">Anytime you try to use a variable that you have not initialized, the value is `$null`.</span></span> <span data-ttu-id="faa9a-121">C’est l’une des façons les plus courantes pour les valeurs `$null` d’entrer dans votre code.</span><span class="sxs-lookup"><span data-stu-id="faa9a-121">This is one of the most common ways that `$null` values sneak into your code.</span></span>

```powershell
PS> $null -eq $undefinedVariable
True
```

<span data-ttu-id="faa9a-122">Si vous tapez mal un nom de variable, PowerShell le voit comme une variable différente et la valeur est `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-122">If you happen to mistype a variable name then PowerShell sees it as a different variable and the value is `$null`.</span></span>

<span data-ttu-id="faa9a-123">L’autre façon de trouver les valeurs `$null` est quand elles proviennent d’autres commandes qui ne vous donnent aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="faa9a-123">The other way you find `$null` values is when they come from other commands that don't give you any results.</span></span>

```powershell
PS> function Get-Nothing {}
PS> $value = Get-Nothing
PS> $null -eq $value
True
```

## <a name="impact-of-null"></a><span data-ttu-id="faa9a-124">Impact de $null</span><span class="sxs-lookup"><span data-stu-id="faa9a-124">Impact of $null</span></span>

<span data-ttu-id="faa9a-125">Les valeurs `$null` affectent votre code différemment en fonction de l’endroit où elles s’affichent.</span><span class="sxs-lookup"><span data-stu-id="faa9a-125">`$null` values impact your code differently depending on where they show up.</span></span>

### <a name="in-strings"></a><span data-ttu-id="faa9a-126">Dans des chaînes</span><span class="sxs-lookup"><span data-stu-id="faa9a-126">In strings</span></span>

<span data-ttu-id="faa9a-127">Si vous utilisez `$null` dans une chaîne, il s’agit d’une valeur vide (ou d’une chaîne vide).</span><span class="sxs-lookup"><span data-stu-id="faa9a-127">If you use `$null` in a string, then it's a blank value (or empty string).</span></span>

```powershell
PS> $value = $null
PS> Write-Output "The value is $value"
The value is
```

<span data-ttu-id="faa9a-128">C’est l’une des raisons pour lesquelles j’aime placer les variables entre crochets quand elles sont utilisées dans des messages de journal.</span><span class="sxs-lookup"><span data-stu-id="faa9a-128">This is one of the reasons that I like to place brackets around variables when using them in log messages.</span></span> <span data-ttu-id="faa9a-129">Il est encore plus important d’identifier les limites de vos valeurs de variables quand la valeur se trouve à la fin de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="faa9a-129">It's even more important to identify the edges of your variable values when the value is at the end of the string.</span></span>

```powershell
PS> $value = $null
PS> Write-Output "The value is [$value]"
The value is []
```

<span data-ttu-id="faa9a-130">Cela permet de repérer facilement les chaînes vides et les valeurs `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-130">This makes empty strings and `$null` values easy to spot.</span></span>

### <a name="in-numeric-equation"></a><span data-ttu-id="faa9a-131">Dans une équation numérique</span><span class="sxs-lookup"><span data-stu-id="faa9a-131">In numeric equation</span></span>

<span data-ttu-id="faa9a-132">Quand une valeur `$null` est utilisée dans une équation numérique, vos résultats ne sont pas valides s’ils ne génèrent pas d’erreur.</span><span class="sxs-lookup"><span data-stu-id="faa9a-132">When a `$null` value is used in a numeric equation then your results are invalid if they don't give an error.</span></span> <span data-ttu-id="faa9a-133">Parfois, `$null` prend la valeur `0`, et dans d’autres cas, elle constitue la totalité du résultat `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-133">Sometimes the `$null` evaluates to `0` and other times it makes the whole result `$null`.</span></span>
<span data-ttu-id="faa9a-134">Voici un exemple de multiplication qui donne 0 ou `$null` en fonction de l’ordre des valeurs.</span><span class="sxs-lookup"><span data-stu-id="faa9a-134">Here is an example with multiplication that gives 0 or `$null` depending on the order of the values.</span></span>

```powershell
PS> $null * 5
PS> $null -eq ( $null * 5 )
True

PS> 5 * $null
0
PS> $null -eq ( 5 * $null )
False
```

### <a name="in-place-of-a-collection"></a><span data-ttu-id="faa9a-135">À la place d’une collection</span><span class="sxs-lookup"><span data-stu-id="faa9a-135">In place of a collection</span></span>

<span data-ttu-id="faa9a-136">Une collection vous permet d’utiliser un index pour accéder à des valeurs.</span><span class="sxs-lookup"><span data-stu-id="faa9a-136">A collection allow you use an index to access values.</span></span> <span data-ttu-id="faa9a-137">Si vous essayez de créer une indexation dans une collection qui est en fait `null`, vous obtenez l’erreur suivante : `Cannot index into a null array`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-137">If you try to index into a collection that is actually `null`, you get this error: `Cannot index into a null array`.</span></span>

```powershell
PS> $value = $null
PS> $value[10]
Cannot index into a null array.
At line:1 char:1
+ $value[10]
+ ~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : NullArray
```

<span data-ttu-id="faa9a-138">Si vous disposez d’une collection, mais que vous tentez d’accéder à un élément qui ne se trouve pas dans la collection, vous obtenez le résultat `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-138">If you have a collection but try to access an element that is not in the collection, you get a `$null` result.</span></span>

```powershell
$array = @( 'one','two','three' )
$null -eq $array[100]
True
```

### <a name="in-place-of-an-object"></a><span data-ttu-id="faa9a-139">À la place d’un objet</span><span class="sxs-lookup"><span data-stu-id="faa9a-139">In place of an object</span></span>

<span data-ttu-id="faa9a-140">Si vous tentez d’accéder à une propriété ou à une sous-propriété d’un objet qui n’a pas la propriété spécifiée, vous obtenez une valeur `$null` comme ce serait le cas pour une variable non définie.</span><span class="sxs-lookup"><span data-stu-id="faa9a-140">If you try to access a property or sub property of an object that doesn't have the specified property, you get a `$null` value like you would for an undefined variable.</span></span> <span data-ttu-id="faa9a-141">Dans ce cas, le fait que la variable ait la valeur `$null` ou qu’elle soit un objet réel n’a pas d’importance.</span><span class="sxs-lookup"><span data-stu-id="faa9a-141">It doesn't matter if the variable is `$null` or an actual object in this case.</span></span>

```powershell
PS> $null -eq $undefined.some.fake.property
True

PS> $date = Get-Date
PS> $null -eq $date.some.fake.property
True
```

### <a name="method-on-a-null-valued-expression"></a><span data-ttu-id="faa9a-142">Méthode sur une expression ayant une valeur Null</span><span class="sxs-lookup"><span data-stu-id="faa9a-142">Method on a null-valued expression</span></span>

<span data-ttu-id="faa9a-143">L’appel d’une méthode sur un objet `$null` lève un `RuntimeException`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-143">Calling a method on a `$null` object throws a `RuntimeException`.</span></span>

```powershell
PS> $value = $null
PS> $value.toString()
You cannot call a method on a null-valued expression.
At line:1 char:1
+ $value.tostring()
+ ~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvokeMethodOnNull
```

<span data-ttu-id="faa9a-144">Chaque fois que je vois l’expression `You cannot call a method on a null-valued expression`, la première chose que je recherche est l’endroit où j’appelle une méthode sur une variable sans vérifier au préalable si sa valeur est `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-144">Whenever I see the phrase `You cannot call a method on a null-valued expression` then the first thing I look for are places where I am calling a method on a variable without first checking it for `$null`.</span></span>

## <a name="checking-for-null"></a><span data-ttu-id="faa9a-145">Recherche de $null</span><span class="sxs-lookup"><span data-stu-id="faa9a-145">Checking for $null</span></span>

<span data-ttu-id="faa9a-146">Vous avez peut-être remarqué que je place toujours le `$null` à gauche lors de la recherche de `$null` dans mes exemples.</span><span class="sxs-lookup"><span data-stu-id="faa9a-146">You may have noticed that I always place the `$null` on the left when checking for `$null` in my examples.</span></span> <span data-ttu-id="faa9a-147">Cela est intentionnel et accepté comme bonne pratique PowerShell.</span><span class="sxs-lookup"><span data-stu-id="faa9a-147">This is intentional and accepted as a PowerShell best practice.</span></span> <span data-ttu-id="faa9a-148">Dans certains scénarios, le fait de le placer à droite ne vous donne pas le résultat attendu.</span><span class="sxs-lookup"><span data-stu-id="faa9a-148">There are some scenarios where placing it on the right doesn't give you the expected result.</span></span>

<span data-ttu-id="faa9a-149">Examinez l’exemple suivant et essayez de prédire les résultats :</span><span class="sxs-lookup"><span data-stu-id="faa9a-149">Look at this next example and try to predict the results:</span></span>

```powershell
if ( $value -eq $null )
{
    'The array is $null'
}
if ( $value -ne $null )
{
    'The array is not $null'
}
```

<span data-ttu-id="faa9a-150">Si je ne définis pas `$value`, le premier résultat est `$true` et notre message est `The array is $null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-150">If I do not define `$value`, the first one evaluates to `$true` and our message is `The array is $null`.</span></span> <span data-ttu-id="faa9a-151">Le piège ici est qu’il est possible de créer un `$value` qui permet que les deux aient la valeur `$false`</span><span class="sxs-lookup"><span data-stu-id="faa9a-151">The trap here is that it's possible to create a `$value` that allows both of them to be `$false`</span></span>

```powershell
$value = @( $null )
```

<span data-ttu-id="faa9a-152">Dans ce cas, `$value` est un tableau qui contient une valeur `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-152">In this case, the `$value` is an array that contains a `$null`.</span></span> <span data-ttu-id="faa9a-153">`-eq` vérifie chaque valeur du tableau et retourne la valeur `$null` qui est mise en correspondance.</span><span class="sxs-lookup"><span data-stu-id="faa9a-153">The `-eq` checks every value in the array and returns the `$null` that is matched.</span></span> <span data-ttu-id="faa9a-154">Le résultat obtenu est `$false`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-154">This evaluates to `$false`.</span></span> <span data-ttu-id="faa9a-155">`-ne` retourne tout ce qui ne correspond pas à `$null` et, dans le cas présent, il n’y a aucun résultat. (Cette expression renvoie également la valeur `$false`.)</span><span class="sxs-lookup"><span data-stu-id="faa9a-155">The `-ne` returns everything that doesn't match `$null` and in this case there are no results (This also evaluates to `$false`).</span></span> <span data-ttu-id="faa9a-156">Aucune ne renvoie `$true` même s’il semble que l’une d’entre elles le devrait.</span><span class="sxs-lookup"><span data-stu-id="faa9a-156">Neither one is `$true` even though it looks like one of them should be.</span></span>

<span data-ttu-id="faa9a-157">Nous pouvons non seulement créer une valeur qui les fait renvoyer toutes les deux `$false`, mais il est également possible de créer une valeur où elles renvoient toutes les deux la valeur `$true`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-157">Not only can we create a value that makes both of them evaluate to `$false`, it's possible to create a value where they both evaluate to `$true`.</span></span> <span data-ttu-id="faa9a-158">Mathias Jessen (@IISResetMe) a un [bon billet][] qui fournit des informations détaillées sur ce scénario.</span><span class="sxs-lookup"><span data-stu-id="faa9a-158">Mathias Jessen (@IISResetMe) has a [good post][] that dives into that scenario.</span></span>

### <a name="psscriptanalyzer-and-vscode"></a><span data-ttu-id="faa9a-159">PSScriptAnalyzer et VSCode</span><span class="sxs-lookup"><span data-stu-id="faa9a-159">PSScriptAnalyzer and VSCode</span></span>

<span data-ttu-id="faa9a-160">Le module [PSScriptAnalyzer][] comprend une règle appelée `PSPossibleIncorrectComparisonWithNull` qui vérifie ce problème.</span><span class="sxs-lookup"><span data-stu-id="faa9a-160">The [PSScriptAnalyzer][] module has a rule that checks for this issue called `PSPossibleIncorrectComparisonWithNull`.</span></span>

```powershell
PS> Invoke-ScriptAnalyzer ./myscript.ps1

RuleName                              Message
--------                              -------
PSPossibleIncorrectComparisonWithNull $null should be on the left side of equality comparisons.
```

<span data-ttu-id="faa9a-161">Étant donné que VS Code utilise également les règles PSScriptAnalyser, il met également cela en évidence ou l’identifie comme un problème dans votre script.</span><span class="sxs-lookup"><span data-stu-id="faa9a-161">Because VS Code uses the PSScriptAnalyser rules too, it also highlights or identifies this as a problem in your script.</span></span>

### <a name="simple-if-check"></a><span data-ttu-id="faa9a-162">Contrôle « if » simple</span><span class="sxs-lookup"><span data-stu-id="faa9a-162">Simple if check</span></span>

<span data-ttu-id="faa9a-163">Une façon courante pour les gens de rechercher une valeur non $null consiste à utiliser une instruction `if()` simple sans la comparaison.</span><span class="sxs-lookup"><span data-stu-id="faa9a-163">A common way that people check for a non-$null value is to use a simple `if()` statement without the comparison.</span></span>

```powershell
if ( $value )
{
    Do-Something
}
```

<span data-ttu-id="faa9a-164">Si la valeur est `$null`, le résultat est `$false`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-164">If the value is `$null`, this evaluates to `$false`.</span></span> <span data-ttu-id="faa9a-165">Cela est facile à lire, mais veillez à ce qu’il recherche exactement ce que vous attendez.</span><span class="sxs-lookup"><span data-stu-id="faa9a-165">This is easy to read, but be careful that it's looking for exactly what you're expecting it to look for.</span></span> <span data-ttu-id="faa9a-166">Je lis cette ligne de code comme suit :</span><span class="sxs-lookup"><span data-stu-id="faa9a-166">I read that line of code as:</span></span>

> <span data-ttu-id="faa9a-167">Si `$value` a une valeur.</span><span class="sxs-lookup"><span data-stu-id="faa9a-167">If `$value` has a value.</span></span>

<span data-ttu-id="faa9a-168">Mais tout ne se résume pas à ça.</span><span class="sxs-lookup"><span data-stu-id="faa9a-168">But that's not the whole story.</span></span> <span data-ttu-id="faa9a-169">Cette ligne indique en fait :</span><span class="sxs-lookup"><span data-stu-id="faa9a-169">That line is actually saying:</span></span>

> <span data-ttu-id="faa9a-170">Si `$value` n’a pas la valeur `$null`, `0`, `$false` ou une `empty string`</span><span class="sxs-lookup"><span data-stu-id="faa9a-170">If `$value` is not `$null` or `0` or `$false` or an `empty string`</span></span>

<span data-ttu-id="faa9a-171">Voici un exemple plus complet de cette instruction.</span><span class="sxs-lookup"><span data-stu-id="faa9a-171">Here is a more complete sample of that statement.</span></span>

```powershell
if ( $null -ne $value -and
        $value -ne 0 -and
        $value -ne '' -and
        $value -ne $false )
{
    Do-Something
}
```

<span data-ttu-id="faa9a-172">Il est tout à fait possible d’utiliser un contrôle `if` de base à condition de se rappeler que ces autres valeurs comptent comme `$false` et pas seulement qu’une variable a une valeur.</span><span class="sxs-lookup"><span data-stu-id="faa9a-172">It's perfectly OK to use a basic `if` check as long as you remember those other values count as `$false` and not just that a variable has a value.</span></span>

<span data-ttu-id="faa9a-173">J’ai rencontré ce problème lors de la refactorisation de code il y a quelques jours.</span><span class="sxs-lookup"><span data-stu-id="faa9a-173">I ran into this issue when refactoring some code a few days ago.</span></span> <span data-ttu-id="faa9a-174">Il avait un contrôle de propriété de base comme celle-ci.</span><span class="sxs-lookup"><span data-stu-id="faa9a-174">It had a basic property check like this.</span></span>

```powershell
if ( $object.property )
{
    $object.property = $value
}
```

<span data-ttu-id="faa9a-175">Je voulais affecter une valeur à la propriété de l’objet uniquement si elle existait.</span><span class="sxs-lookup"><span data-stu-id="faa9a-175">I wanted to assign a value to the object property only if it existed.</span></span> <span data-ttu-id="faa9a-176">Dans la plupart des cas, l’objet d’origine comportait une valeur qui renvoyait `$true` dans l’instruction `if`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-176">In most cases, the original object had a value that would evaluate to `$true` in the `if` statement.</span></span> <span data-ttu-id="faa9a-177">Mais j’ai rencontré un problème dans lequel la valeur n’était parfois pas définie.</span><span class="sxs-lookup"><span data-stu-id="faa9a-177">But I ran into an issue where the value was occasionally not getting set.</span></span> <span data-ttu-id="faa9a-178">J’ai débogué le code et trouvé que l’objet avait la propriété mais il s’agissait d’une valeur de chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="faa9a-178">I debugged the code and found that the object had the property but it was a blank string value.</span></span> <span data-ttu-id="faa9a-179">Cela a empêché sa mise à jour avec la logique précédente.</span><span class="sxs-lookup"><span data-stu-id="faa9a-179">This prevented it from ever getting updated with the previous logic.</span></span> <span data-ttu-id="faa9a-180">J’ai donc ajouté un contrôle de `$null` approprié, après quoi tout a fonctionné.</span><span class="sxs-lookup"><span data-stu-id="faa9a-180">So I added a proper `$null` check and everything worked.</span></span>

```powershell
if ( $null -ne $object.property )
{
    $object.property = $value
}
```

<span data-ttu-id="faa9a-181">Ce sont de petits bogues comme ceux-là qui sont difficiles à repérer et qui me font contrôler de manière intensive les valeurs de `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-181">It's little bugs like these that are hard to spot and make me aggressively check values for `$null`.</span></span>

## <a name="nullcount"></a><span data-ttu-id="faa9a-182">$null.Count</span><span class="sxs-lookup"><span data-stu-id="faa9a-182">$null.Count</span></span>

<span data-ttu-id="faa9a-183">Si vous essayez d’accéder à une propriété sur une valeur `$null`, cette propriété a également la valeur `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-183">If you try to access a property on a `$null` value, that the property is also `$null`.</span></span> <span data-ttu-id="faa9a-184">La propriété `count` est l’exception à cette règle.</span><span class="sxs-lookup"><span data-stu-id="faa9a-184">The `count` property is the exception to this rule.</span></span>

```powershell
PS> $value = $null
PS> $value.count
0
```

<span data-ttu-id="faa9a-185">Quand vous avez une valeur `$null`, `count` a la valeur `0`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-185">When you have a `$null` value, then the `count` is `0`.</span></span> <span data-ttu-id="faa9a-186">Cette propriété spéciale est ajoutée par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="faa9a-186">This special property is added by PowerShell.</span></span>

### <a name="pscustomobject-count"></a><span data-ttu-id="faa9a-187">[PSCustomObject] Count</span><span class="sxs-lookup"><span data-stu-id="faa9a-187">[PSCustomObject] Count</span></span>

<span data-ttu-id="faa9a-188">Dans PowerShell, presque tous les objets ont cette propriété count.</span><span class="sxs-lookup"><span data-stu-id="faa9a-188">Almost all objects in PowerShell have that count property.</span></span> <span data-ttu-id="faa9a-189">Une exception importante est `[PSCustomObject]` dans Windows PowerShell 5.1. (Cela est corrigé dans PowerShell 6.0.)</span><span class="sxs-lookup"><span data-stu-id="faa9a-189">One important exception is the `[PSCustomObject]` in Windows PowerShell 5.1 (This is fixed in PowerShell 6.0).</span></span> <span data-ttu-id="faa9a-190">Il n’a pas de propriété count. Vous obtenez donc une valeur `$null` si vous essayez de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="faa9a-190">It doesn't have a count property so you get a `$null` value if you try to use it.</span></span> <span data-ttu-id="faa9a-191">Je le mentionne ici pour que vous ne tentiez pas d’utiliser `.Count` au lieu d’un contrôle de `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-191">I call this out here so that you don't try to use `.Count` instead of a `$null` check.</span></span>

<span data-ttu-id="faa9a-192">L’exécution de cet exemple sur Windows PowerShell 5.1 et sur PowerShell 6.0 donne des résultats différents.</span><span class="sxs-lookup"><span data-stu-id="faa9a-192">Running this example on Windows PowerShell 5.1 and PowerShell 6.0 gives you different results.</span></span>

```powershell
$value = [PSCustomObject]@{Name='MyObject'}
if ( $value.count -eq 1 )
{
    "We have a value"
}
```

## <a name="empty-null"></a><span data-ttu-id="faa9a-193">Valeur Null vide</span><span class="sxs-lookup"><span data-stu-id="faa9a-193">Empty null</span></span>

<span data-ttu-id="faa9a-194">Il existe un type spécial de `$null` qui agit différemment des autres.</span><span class="sxs-lookup"><span data-stu-id="faa9a-194">There is one special type of `$null` that acts differently than the others.</span></span> <span data-ttu-id="faa9a-195">Je vais l’appeler la valeur `$null` vide, mais il s’agit véritablement d’une valeur [System.Management.Automation.Internal.AutomationNull][].</span><span class="sxs-lookup"><span data-stu-id="faa9a-195">I am going to call it the empty `$null` but it's really a [System.Management.Automation.Internal.AutomationNull][].</span></span> <span data-ttu-id="faa9a-196">Cette valeur `$null` vide est celle que vous obtenez comme résultat d’une fonction ou d’un bloc de script qui ne retourne rien (résultat void).</span><span class="sxs-lookup"><span data-stu-id="faa9a-196">This empty `$null` is the one you get as the result of a function or script block that returns nothing (a void result).</span></span>

```powershell
PS> function Get-Nothing {}
PS> $nothing = Get-Nothing
PS> $null -eq $nothing
True
```

<span data-ttu-id="faa9a-197">Si vous la comparez à `$null`, vous obtenez une valeur `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-197">If you compare it with `$null`, you get a `$null` value.</span></span> <span data-ttu-id="faa9a-198">Quand elle est utilisée dans une évaluation où une valeur est nécessaire, la valeur est toujours `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-198">When used in an evaluation where a value is required, the value is always `$null`.</span></span> <span data-ttu-id="faa9a-199">Mais si vous la placez dans un tableau, elle est traitée comme un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="faa9a-199">But if you place it inside an array, it's treated the same as an empty array.</span></span>

```powershell
PS> $containempty = @( @() )
PS> $containnothing = @($nothing)
PS> $containnull = @($null)

PS> $containempty.count
0
PS> $containnothing.count
0
PS> $containnull.count
1
```

<span data-ttu-id="faa9a-200">Vous pouvez avoir un tableau qui contient une valeur `$null` et sa valeur `count` est `1`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-200">You can have an array that contains one `$null` value and its `count` is `1`.</span></span> <span data-ttu-id="faa9a-201">Toutefois, si vous placez un résultat vide dans un tableau, il n’est pas comptabilisé comme un élément.</span><span class="sxs-lookup"><span data-stu-id="faa9a-201">But if you place an empty result inside an array then it's not counted as an item.</span></span> <span data-ttu-id="faa9a-202">Le nombre est `0`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-202">The count is `0`.</span></span>

<span data-ttu-id="faa9a-203">Si vous traitez la valeur `$null` vide comme une collection, elle est vide.</span><span class="sxs-lookup"><span data-stu-id="faa9a-203">If you treat the empty `$null` like a collection, then it's empty.</span></span>

### <a name="pipeline"></a><span data-ttu-id="faa9a-204">Pipeline</span><span class="sxs-lookup"><span data-stu-id="faa9a-204">Pipeline</span></span>

<span data-ttu-id="faa9a-205">Le principal moment où vous voyez la différence est lors de l’utilisation du pipeline.</span><span class="sxs-lookup"><span data-stu-id="faa9a-205">The primary place you see the difference is when using the pipeline.</span></span> <span data-ttu-id="faa9a-206">Vous pouvez acheminer une valeur `$null` mais pas une valeur `$null` vide.</span><span class="sxs-lookup"><span data-stu-id="faa9a-206">You can pipe a `$null` value but not an empty `$null` value.</span></span>

```powershell
PS> $null | ForEach-Object{ Write-Output 'NULL Value' }
'NULL Value'
PS> $nothing | ForEach-Object{ Write-Output 'No Value' }
```

<span data-ttu-id="faa9a-207">En fonction de votre code, vous devez tenir compte de la valeur `$null` dans votre logique.</span><span class="sxs-lookup"><span data-stu-id="faa9a-207">Depending on your code, you should account for the `$null` in your logic.</span></span>

<span data-ttu-id="faa9a-208">Recherchez d’abord la valeur `$null`</span><span class="sxs-lookup"><span data-stu-id="faa9a-208">Either check for `$null` first</span></span>

- <span data-ttu-id="faa9a-209">Filtrer les valeurs Null sur le pipeline (`... | Where {$null -ne $_} | ...`)</span><span class="sxs-lookup"><span data-stu-id="faa9a-209">Filter out null on the pipeline (`... | Where {$null -ne $_} | ...`)</span></span>
- <span data-ttu-id="faa9a-210">Gérer-la dans la fonction pipeline</span><span class="sxs-lookup"><span data-stu-id="faa9a-210">Handle it in the pipeline function</span></span>

## <a name="foreach"></a><span data-ttu-id="faa9a-211">foreach</span><span class="sxs-lookup"><span data-stu-id="faa9a-211">foreach</span></span>

<span data-ttu-id="faa9a-212">L’une de mes fonctionnalités préférées de `foreach` est qu’il n’effectue pas d’énumération sur une collection `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-212">One of my favorite features of `foreach` is that it doesn't enumerate over a `$null` collection.</span></span>

```powershell
foreach ( $node in $null )
{
    #skipped
}
```

<span data-ttu-id="faa9a-213">Cela m’évite d’avoir à contrôler les valeurs `$null` dans la collection avant de l’énumérer.</span><span class="sxs-lookup"><span data-stu-id="faa9a-213">This saves me from having to `$null` check the collection before I enumerate it.</span></span> <span data-ttu-id="faa9a-214">Si vous disposez d’une collection de valeurs de `$null`, `$node` peut toujours avoir une valeur `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-214">If you have a collection of `$null` values, the `$node` can still be `$null`.</span></span>

<span data-ttu-id="faa9a-215">La variable foreach a commencé à fonctionner de cette manière avec PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="faa9a-215">The foreach started working this way with PowerShell 3.0.</span></span> <span data-ttu-id="faa9a-216">Si vous êtes sur une version antérieure, ce n’est pas le cas.</span><span class="sxs-lookup"><span data-stu-id="faa9a-216">If you happen to be on an older version, then this is not the case.</span></span> <span data-ttu-id="faa9a-217">Il s’agit de l’un des principaux changements à connaître lors du rétroportage de code pour la compatibilité 2.0.</span><span class="sxs-lookup"><span data-stu-id="faa9a-217">This is one of the important changes to be aware of when back-porting code for 2.0 compatibility.</span></span>

## <a name="value-types"></a><span data-ttu-id="faa9a-218">Types valeur</span><span class="sxs-lookup"><span data-stu-id="faa9a-218">Value types</span></span>

<span data-ttu-id="faa9a-219">Techniquement, seuls les types référence peuvent avoir une valeur `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-219">Technically, only reference types can be `$null`.</span></span> <span data-ttu-id="faa9a-220">Mais PowerShell est très généreux et permet que les variables soient de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="faa9a-220">But PowerShell is very generous and allows for variables to be any type.</span></span> <span data-ttu-id="faa9a-221">Si vous décidez de typer fortement un type valeur, il ne peut pas être `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-221">If you decide to strongly type a value type, it cannot be `$null`.</span></span>
<span data-ttu-id="faa9a-222">PowerShell convertit `$null`en une valeur par défaut pour de nombreux types.</span><span class="sxs-lookup"><span data-stu-id="faa9a-222">PowerShell converts `$null` to a default value for many types.</span></span>

```powershell
PS> [int]$number = $null
PS> $number
0

PS> [bool]$boolean = $null
PS> $boolean
False

PS> [string]$string = $null
PS> $string -eq ''
True
```

<span data-ttu-id="faa9a-223">Certains types n’ont pas de conversion valide à partir de `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-223">There are some types that do not have a valid conversion from `$null`.</span></span> <span data-ttu-id="faa9a-224">Ces types génèrent une erreur `Cannot convert null to type`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-224">These types generate a `Cannot convert null to type` error.</span></span>

```powershell
PS> [datetime]$date = $null
Cannot convert null to type "System.DateTime".
At line:1 char:1
+ [datetime]$date = $null
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : MetadataError: (:) [], ArgumentTransformationMetadataException
    + FullyQualifiedErrorId : RuntimeException
```

### <a name="function-parameters"></a><span data-ttu-id="faa9a-225">Paramètres de fonction</span><span class="sxs-lookup"><span data-stu-id="faa9a-225">Function parameters</span></span>

<span data-ttu-id="faa9a-226">Il est très courant d’utiliser une valeur fortement typée dans des paramètres de fonction.</span><span class="sxs-lookup"><span data-stu-id="faa9a-226">Using a strongly typed values in function parameters is very common.</span></span> <span data-ttu-id="faa9a-227">Nous apprenons généralement à définir les types de nos paramètres, même si nous avons tendance à ne pas définir les types d’autres variables dans nos scripts.</span><span class="sxs-lookup"><span data-stu-id="faa9a-227">We generally learn to define the types of our parameters even if we tend not to define the types of other variables in our scripts.</span></span> <span data-ttu-id="faa9a-228">Vous avez peut-être déjà des variables fortement typées dans vos fonctions et vous ne vous en rendez même pas compte.</span><span class="sxs-lookup"><span data-stu-id="faa9a-228">You may already have some strongly typed variables in your functions and not even realize it.</span></span>

```powershell
function Do-Something
{
    param(
        [String] $Value
    )
}
```

<span data-ttu-id="faa9a-229">Dès que vous définissez le type du paramètre en tant que `string`, la valeur ne peut jamais être `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-229">As soon as you set the type of the parameter as a `string`, the value can never be `$null`.</span></span> <span data-ttu-id="faa9a-230">Il est courant de vérifier si une valeur est `$null` pour voir si l’utilisateur a, ou non, fourni une valeur.</span><span class="sxs-lookup"><span data-stu-id="faa9a-230">It's common to check if a value is `$null` to see if the user provided a value or not.</span></span>

```powershell
if ( $null -ne $Value ){...}
```

<span data-ttu-id="faa9a-231">`$Value` est une chaîne vide `''` quand aucune valeur n’est fournie.</span><span class="sxs-lookup"><span data-stu-id="faa9a-231">`$Value` is an empty string `''` when no value is provided.</span></span> <span data-ttu-id="faa9a-232">Utilisez la variable automatique `$PSBoundParameters.Value` à la place.</span><span class="sxs-lookup"><span data-stu-id="faa9a-232">Use the automatic variable `$PSBoundParameters.Value` instead.</span></span>

```powershell
if ( $null -ne $PSBoundParameters.Value ){...}
```

<span data-ttu-id="faa9a-233">`$PSBoundParameters` contient uniquement les paramètres qui ont été spécifiés lors de l’appel de la fonction.</span><span class="sxs-lookup"><span data-stu-id="faa9a-233">`$PSBoundParameters` only contains the parameters that were specified when the function was called.</span></span>
<span data-ttu-id="faa9a-234">Vous pouvez également utiliser la méthode `ContainsKey` pour rechercher la propriété.</span><span class="sxs-lookup"><span data-stu-id="faa9a-234">You can also use the `ContainsKey` method to check for the property.</span></span>

```powershell
if ( $PSBoundParameters.ContainsKey('Value') ){...}
```

### <a name="isnotnullorempty"></a><span data-ttu-id="faa9a-235">IsNotNullOrEmpty</span><span class="sxs-lookup"><span data-stu-id="faa9a-235">IsNotNullOrEmpty</span></span>

<span data-ttu-id="faa9a-236">Si la valeur est une chaîne, vous pouvez utiliser une fonction de chaîne statique pour vérifier si la valeur est `$null` ou une chaîne vide en même temps.</span><span class="sxs-lookup"><span data-stu-id="faa9a-236">If the value is a string, you can use a static string function to check if the value is `$null` or an empty string at the same time.</span></span>

```powershell
if ( -not [string]::IsNullOrEmpty( $value ) ){...}
```

<span data-ttu-id="faa9a-237">Il m’arrive souvent de l’utiliser quand je sais que le type valeur doit être une chaîne.</span><span class="sxs-lookup"><span data-stu-id="faa9a-237">I find myself using this often when I know the value type should be a string.</span></span>

## <a name="when-i-null-check"></a><span data-ttu-id="faa9a-238">Quand je contrôle les valeurs $null</span><span class="sxs-lookup"><span data-stu-id="faa9a-238">When I $null check</span></span>

<span data-ttu-id="faa9a-239">Je suis un générateur de script prudent.</span><span class="sxs-lookup"><span data-stu-id="faa9a-239">I am a defensive scripter.</span></span> <span data-ttu-id="faa9a-240">Chaque fois que j’appelle une fonction et que je l’affecte à une variable, je vérifie si elle comprend une valeur `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-240">Anytime I call a function and assign it to a variable, I check it for `$null`.</span></span>

```powershell
$userList = Get-ADUser kevmar
if ($null -ne $userList){...}
```

<span data-ttu-id="faa9a-241">Je préfère de beaucoup utiliser `if` ou `foreach` plutôt que `try/catch`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-241">I much prefer using `if` or `foreach` over using `try/catch`.</span></span> <span data-ttu-id="faa9a-242">Ne vous méprenez pas : j’utilise encore beaucoup `try/catch`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-242">Don't get me wrong, I still use `try/catch` a lot.</span></span> <span data-ttu-id="faa9a-243">Toutefois, si je peux tester une condition d’erreur ou un jeu de résultats vide, je peux autoriser que la gestion de mes exceptions concerne les véritables exceptions.</span><span class="sxs-lookup"><span data-stu-id="faa9a-243">But if I can test for an error condition or an empty set of results, I can allow my exception handling be for true exceptions.</span></span>

<span data-ttu-id="faa9a-244">J’ai également tendance à rechercher les valeurs `$null` avant de créer une indexation dans une valeur ou d’appeler des méthodes sur un objet.</span><span class="sxs-lookup"><span data-stu-id="faa9a-244">I also tend to check for `$null` before I index into a value or call methods on an object.</span></span> <span data-ttu-id="faa9a-245">Comme ces deux actions échouent pour un objet `$null`, je trouve qu’il est important de d’abord les valider.</span><span class="sxs-lookup"><span data-stu-id="faa9a-245">These two actions fail for a `$null` object so I find it important to validate them first.</span></span> <span data-ttu-id="faa9a-246">J’ai déjà abordé ces scénarios précédemment dans cette publication.</span><span class="sxs-lookup"><span data-stu-id="faa9a-246">I already covered those scenarios earlier in this post.</span></span>

### <a name="no-results-scenario"></a><span data-ttu-id="faa9a-247">Scénario sans résultat</span><span class="sxs-lookup"><span data-stu-id="faa9a-247">No results scenario</span></span>

<span data-ttu-id="faa9a-248">Il est important de savoir que différentes fonctions et commandes gèrent le scénario sans résultat différemment.</span><span class="sxs-lookup"><span data-stu-id="faa9a-248">It's important to know that different functions and commands handle the no results scenario differently.</span></span> <span data-ttu-id="faa9a-249">De nombreuses commandes PowerShell retournent la valeur `$null` vide et une erreur dans le flux d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="faa9a-249">Many PowerShell commands return the empty `$null` and an error in the error stream.</span></span> <span data-ttu-id="faa9a-250">Mais d’autres lèvent des exceptions ou vous donnent un objet d’état.</span><span class="sxs-lookup"><span data-stu-id="faa9a-250">But others throw exceptions or give you a status object.</span></span> <span data-ttu-id="faa9a-251">Il vous appartient quand même de découvrir comment les commandes que vous utilisez traitent les scénarios sans résultat et les scénarios d’erreur.</span><span class="sxs-lookup"><span data-stu-id="faa9a-251">It's still up to you to know how the commands you use deal with the no results and error scenarios.</span></span>

## <a name="initializing-to-null"></a><span data-ttu-id="faa9a-252">Initialisation sur $null</span><span class="sxs-lookup"><span data-stu-id="faa9a-252">Initializing to $null</span></span>

<span data-ttu-id="faa9a-253">J’ai pris, entre autres, l’habitude d’initialiser toutes mes variables avant de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="faa9a-253">One habit that I have picked up is initializing all my variables before I use them.</span></span> <span data-ttu-id="faa9a-254">Vous devez effectuer cette opération dans d’autres langages.</span><span class="sxs-lookup"><span data-stu-id="faa9a-254">You are required to do this in other languages.</span></span> <span data-ttu-id="faa9a-255">En haut de ma fonction ou quand j’entre une boucle foreach, je définis toutes les valeurs que j’utilise.</span><span class="sxs-lookup"><span data-stu-id="faa9a-255">At the top of my function or as I enter a foreach loop, I define all the values that I'm using.</span></span>

<span data-ttu-id="faa9a-256">Voici un scénario que je veux que vous examiniez en détail.</span><span class="sxs-lookup"><span data-stu-id="faa9a-256">Here is a scenario that I want you to take a close look at.</span></span> <span data-ttu-id="faa9a-257">Il s’agit d’un exemple de bogue que j’ai déjà recherché.</span><span class="sxs-lookup"><span data-stu-id="faa9a-257">It's an example of a bug I had to chase down before.</span></span>

```powershell
function Do-Something
{
    foreach ( $node in 1..6 )
    {
        try
        {
            $result = Get-Something -ID $node
        }
        catch
        {
            Write-Verbose "[$result] not valid"
        }

        if ( $null -ne $result )
        {
            Update-Something $result
        }
    }
}
```

<span data-ttu-id="faa9a-258">On s’attend à ce que `Get-Something` retourne soit un résultat, soit une valeur `$null` vide.</span><span class="sxs-lookup"><span data-stu-id="faa9a-258">The expectation here is that `Get-Something` returns either a result or an empty `$null`.</span></span> <span data-ttu-id="faa9a-259">Si une erreur se produit, nous la consignons.</span><span class="sxs-lookup"><span data-stu-id="faa9a-259">If there is an error, we log it.</span></span> <span data-ttu-id="faa9a-260">Nous vérifions ensuite que nous avons obtenu un résultat valide avant de le traiter.</span><span class="sxs-lookup"><span data-stu-id="faa9a-260">Then we check to make sure we got a valid result before processing it.</span></span>

<span data-ttu-id="faa9a-261">Le masquage du bogue se produit dans ce code quand `Get-Something` lève une exception et n’affecte pas de valeur à `$result`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-261">The bug hiding in this code is when `Get-Something` throws an exception and doesn't assign a value to `$result`.</span></span> <span data-ttu-id="faa9a-262">Comme il échoue avant l’affectation, nous n’affectons même pas `$null` à la variable `$result`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-262">It fails before the assignment so we don't even assign `$null` to the `$result` variable.</span></span> <span data-ttu-id="faa9a-263">`$result` contient encore le `$result` valide précédent provenant d’autres itérations.</span><span class="sxs-lookup"><span data-stu-id="faa9a-263">`$result` still contains the previous valid `$result` from other iterations.</span></span>
<span data-ttu-id="faa9a-264">Définissez la commande `Update-Something` pour qu’elle s’exécute plusieurs fois sur le même objet dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="faa9a-264">`Update-Something` to execute multiple times on the same object in this example.</span></span>

<span data-ttu-id="faa9a-265">Je définis `$result` sur `$null` directement dans la boucle foreach avant de l’utiliser pour atténuer ce problème.</span><span class="sxs-lookup"><span data-stu-id="faa9a-265">I set `$result` to `$null` right inside the foreach loop before I use it to mitigate this issue.</span></span>

```powershell
foreach ( $node in 1..6 )
{
    $result = $null
    try
    {
        ...
```

### <a name="scope-issues"></a><span data-ttu-id="faa9a-266">Problèmes d’étendue</span><span class="sxs-lookup"><span data-stu-id="faa9a-266">Scope issues</span></span>

<span data-ttu-id="faa9a-267">Cela permet également d’atténuer les problèmes de portée.</span><span class="sxs-lookup"><span data-stu-id="faa9a-267">This also helps mitigate scoping issues.</span></span> <span data-ttu-id="faa9a-268">Dans cet exemple, nous affectons plusieurs fois des valeurs à `$result` dans une boucle.</span><span class="sxs-lookup"><span data-stu-id="faa9a-268">In that example, we assign values to `$result` over and over in a loop.</span></span> <span data-ttu-id="faa9a-269">Toutefois, étant donné que PowerShell permet que des valeurs de variables extérieures à la fonction débordent dans l’étendue de la fonction active, leur initialisation à l’intérieur de votre fonction atténue les bogues qui peuvent être introduits de cette façon.</span><span class="sxs-lookup"><span data-stu-id="faa9a-269">But because PowerShell allows variable values from outside the function to bleed into the scope of the current function, initializing them inside your function mitigates bugs that can be introduced that way.</span></span>

<span data-ttu-id="faa9a-270">Une variable non initialisée dans votre fonction n’a pas une valeur `$null` si elle est définie sur une valeur d’une étendue parente.</span><span class="sxs-lookup"><span data-stu-id="faa9a-270">An uninitialized variable in your function is not `$null` if it's set to a value in a parent scope.</span></span>
<span data-ttu-id="faa9a-271">L’étendue parente peut être une autre fonction qui appelle votre fonction et utilise les mêmes noms de variables.</span><span class="sxs-lookup"><span data-stu-id="faa9a-271">The parent scope could be another function that calls your function and uses the same variable names.</span></span>

<span data-ttu-id="faa9a-272">Si je prends ce même exemple `Do-something` et que je supprime la boucle, j’obtiens quelque chose ressemblant à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="faa9a-272">If I take that same `Do-something` example and remove the loop, I would end up with something that looks like this example:</span></span>

```powershell
function Invoke-Something
{
    $result = 'ParentScope'
    Do-Something
}

function Do-Something
{
    try
    {
        $result = Get-Something -ID $node
    }
    catch
    {
        Write-Verbose "[$result] not valid"
    }

    if ( $null -ne $result )
    {
        Update-Something $result
    }
}
```

<span data-ttu-id="faa9a-273">Si l’appel à `Get-Something` lève une exception, mon contrôle des valeurs `$null` trouve `$result` dans `Invoke-Something`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-273">If the call to `Get-Something` throws an exception, then my `$null` check finds the `$result` from `Invoke-Something`.</span></span> <span data-ttu-id="faa9a-274">L’initialisation de la valeur dans votre fonction atténue ce problème.</span><span class="sxs-lookup"><span data-stu-id="faa9a-274">Initializing the value inside your function mitigates this issue.</span></span>

<span data-ttu-id="faa9a-275">Le nommage de variables est difficile et il est courant qu’un auteur utilise les mêmes noms de variables dans plusieurs fonctions.</span><span class="sxs-lookup"><span data-stu-id="faa9a-275">Naming variables is hard and it's common for an author to use the same variable names in multiple functions.</span></span> <span data-ttu-id="faa9a-276">Je sais que j’utilise tout le temps `$node`,`$result` et `$data`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-276">I know I use `$node`,`$result`,`$data` all the time.</span></span> <span data-ttu-id="faa9a-277">C’est pourquoi il est très facile pour des valeurs de différentes étendues de s’afficher dans des emplacements où elles ne devraient pas être.</span><span class="sxs-lookup"><span data-stu-id="faa9a-277">So it would be very easy for values from different scopes to show up in places where they should not be.</span></span>

## <a name="redirect-output-to-null"></a><span data-ttu-id="faa9a-278">Rediriger la sortie vers $null</span><span class="sxs-lookup"><span data-stu-id="faa9a-278">Redirect output to $null</span></span>

<span data-ttu-id="faa9a-279">Je parle des valeurs `$null` dans l’ensemble de cet article, mais le sujet n’est pas complet si je ne mentionne pas la redirection de la sortie vers `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-279">I have been talking about `$null` values for this entire article but the topic is not complete if I didn't mention redirecting output to `$null`.</span></span> <span data-ttu-id="faa9a-280">Vous avez parfois des commandes qui génèrent des informations ou des objets que vous voulez supprimer.</span><span class="sxs-lookup"><span data-stu-id="faa9a-280">There are times when you have commands that output information or objects that you want to suppress.</span></span> <span data-ttu-id="faa9a-281">C’est le cas de la redirection de la sortie vers `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-281">Redirecting output to `$null` does that.</span></span>

### <a name="out-null"></a><span data-ttu-id="faa9a-282">Out-Null</span><span class="sxs-lookup"><span data-stu-id="faa9a-282">Out-Null</span></span>

<span data-ttu-id="faa9a-283">La commande Out-Null est le moyen intégré de rediriger des données de pipeline vers `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-283">The Out-Null command is the built-in way to redirect pipeline data to `$null`.</span></span>

```powershell
New-Item -Type Directory -Path $path | Out-Null
```

### <a name="assign-to-null"></a><span data-ttu-id="faa9a-284">Attribuer à $null</span><span class="sxs-lookup"><span data-stu-id="faa9a-284">Assign to $null</span></span>

<span data-ttu-id="faa9a-285">Vous pouvez attribuer les résultats d’une commande à `$null` pour obtenir le même effet qu’en utilisant `Out-Null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-285">You can assign the results of a command to `$null` for the same effect as using `Out-Null`.</span></span>

```powershell
$null = New-Item -Type Directory -Path $path
```

<span data-ttu-id="faa9a-286">Étant donné que `$null` est une valeur constante, vous ne pouvez jamais la remplacer.</span><span class="sxs-lookup"><span data-stu-id="faa9a-286">Because `$null` is a constant value, you can never overwrite it.</span></span> <span data-ttu-id="faa9a-287">Je n’aime pas la façon dont cela se présente dans mon code, mais l’exécution est souvent plus rapide qu’avec `Out-Null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-287">I don't like the way it looks in my code but it often performs faster than `Out-Null`.</span></span>

### <a name="redirect-to-null"></a><span data-ttu-id="faa9a-288">Rediriger vers $null</span><span class="sxs-lookup"><span data-stu-id="faa9a-288">Redirect to $null</span></span>

<span data-ttu-id="faa9a-289">Vous pouvez également utiliser l’opérateur de redirection pour envoyer la sortie vers `$null`.</span><span class="sxs-lookup"><span data-stu-id="faa9a-289">You can also use the redirection operator to send output to `$null`.</span></span>

```powershell
New-Item -Type Directory -Path $path > $null
```

<span data-ttu-id="faa9a-290">Si vous utilisez des exécutables de ligne de commande qui génèrent les sorties sur les différents flux.</span><span class="sxs-lookup"><span data-stu-id="faa9a-290">If you're dealing with command-line executables that output on the different streams.</span></span> <span data-ttu-id="faa9a-291">Vous pouvez rediriger tous les flux de sortie vers `$null` comme suit :</span><span class="sxs-lookup"><span data-stu-id="faa9a-291">You can redirect all output streams to `$null` like this:</span></span>

```powershell
git status *> $null
```

## <a name="summary"></a><span data-ttu-id="faa9a-292">Résumé</span><span class="sxs-lookup"><span data-stu-id="faa9a-292">Summary</span></span>

<span data-ttu-id="faa9a-293">J’ai abordé beaucoup de sujets dans ce billet et je sais que cet article est plus morcelé que la plupart de mes analyses approfondies.</span><span class="sxs-lookup"><span data-stu-id="faa9a-293">I covered a lot of ground on this one and I know this article is more fragmented than most of my deep dives.</span></span> <span data-ttu-id="faa9a-294">Cela est dû au fait que les valeurs `$null` peuvent apparaître à de nombreux endroits différents dans PowerShell et que toutes les formes sont spécifiques à l’emplacement où vous les trouvez.</span><span class="sxs-lookup"><span data-stu-id="faa9a-294">That is because `$null` values can pop up in many different places in PowerShell and all the nuances are specific to where you find it.</span></span> <span data-ttu-id="faa9a-295">J’espère que vous avez désormais une meilleure compréhension des valeurs `$null` et une connaissance des scénarios les plus nébuleux que vous pouvez rencontrer.</span><span class="sxs-lookup"><span data-stu-id="faa9a-295">I hope you walk away from this with a better understanding of `$null` and an awareness of the more obscure scenarios you may run into.</span></span>

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[original version]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[bon billet]: https://blog.iisreset.me/schrodingers-argumentlist
[good post]: https://blog.iisreset.me/schrodingers-argumentlist
[PSScriptAnalyzer]: https://www.powershellgallery.com/packages/PSScriptAnalyzer
[System.Management.Automation.Internal.AutomationNull]: /dotnet/api/system.management.automation.internal.automationnull
