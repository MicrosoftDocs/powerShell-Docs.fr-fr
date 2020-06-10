---
title: Tout ce que vous avez toujours voulu savoir sur l’instruction IF
description: À l’instar de nombreux autres langages, PowerShell comporte des instructions pour l’exécution conditionnelle de code dans vos scripts.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 6ffb70af694e80430d31991045b9fadc1a2cc3f0
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149522"
---
# <a name="everything-you-wanted-to-know-about-the-if-statement"></a><span data-ttu-id="15bcb-103">Tout ce que vous avez toujours voulu savoir sur l’instruction IF</span><span class="sxs-lookup"><span data-stu-id="15bcb-103">Everything you wanted to know about the IF statement</span></span>

<span data-ttu-id="15bcb-104">À l’instar de nombreux autres langages, PowerShell comporte des instructions pour l’exécution conditionnelle de code dans vos scripts.</span><span class="sxs-lookup"><span data-stu-id="15bcb-104">Like many other languages, PowerShell has statements for conditionally executing code in your scripts.</span></span> <span data-ttu-id="15bcb-105">L’une de ces instructions est l’instruction [if][].</span><span class="sxs-lookup"><span data-stu-id="15bcb-105">One of those statements is the [if][] statement.</span></span> <span data-ttu-id="15bcb-106">Nous allons aujourd’hui étudier de manière approfondie l’une des commandes les plus fondamentales de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15bcb-106">Today we will take a deep dive into one of the most fundamental commands in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="15bcb-107">La [Version d’origine][] de cet article est parue sur le blog écrit par [@KevinMarquette][].</span><span class="sxs-lookup"><span data-stu-id="15bcb-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="15bcb-108">L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu.</span><span class="sxs-lookup"><span data-stu-id="15bcb-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="15bcb-109">Consultez son blog à l’adresse [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="15bcb-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="conditional-execution"></a><span data-ttu-id="15bcb-110">Exécution conditionnelle</span><span class="sxs-lookup"><span data-stu-id="15bcb-110">Conditional execution</span></span>

<span data-ttu-id="15bcb-111">Vos scripts doivent souvent prendre des décisions et exécuter une logique différente en fonction de ces décisions.</span><span class="sxs-lookup"><span data-stu-id="15bcb-111">Your scripts often need to make decisions and perform different logic based on those decisions.</span></span>
<span data-ttu-id="15bcb-112">C’est ce qu’on appelle une exécution conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="15bcb-112">This is what I mean by conditional execution.</span></span> <span data-ttu-id="15bcb-113">Vous avez une instruction ou une valeur à évaluer, et vous exécutez une autre section de code en fonction de cette évaluation.</span><span class="sxs-lookup"><span data-stu-id="15bcb-113">You have one statement or value to evaluate, then execute a different section of code based on that evaluation.</span></span> <span data-ttu-id="15bcb-114">C’est là précisément qu’intervient l’instruction `if`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-114">This is exactly what the `if` statement does.</span></span>

## <a name="the-if-statement"></a><span data-ttu-id="15bcb-115">L’instruction if</span><span class="sxs-lookup"><span data-stu-id="15bcb-115">The if statement</span></span>

<span data-ttu-id="15bcb-116">Voici un exemple de base de l’instruction `if` :</span><span class="sxs-lookup"><span data-stu-id="15bcb-116">Here is a basic example of the `if` statement:</span></span>

```powershell
$condition = $true
if ( $condition )
{
    Write-Output "The condition was true"
}
```

<span data-ttu-id="15bcb-117">L’instruction `if` commence par évaluer l’expression entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="15bcb-117">The first thing the `if` statement does is evaluate the expression in parentheses.</span></span> <span data-ttu-id="15bcb-118">Si l’évaluation génère une valeur `$true`, elle exécute l’élément `scriptblock` entre les accolades.</span><span class="sxs-lookup"><span data-stu-id="15bcb-118">If it evaluates to `$true`, then it executes the `scriptblock` in the braces.</span></span> <span data-ttu-id="15bcb-119">Si la valeur est `$false`, elle ignore cet élément scriptblock.</span><span class="sxs-lookup"><span data-stu-id="15bcb-119">If the value was `$false`, then it would skip over that scriptblock.</span></span>

<span data-ttu-id="15bcb-120">Dans l’exemple précédent, l’instruction `if` a simplement évalué la variable `$condition`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-120">In the previous example, the `if` statement was just evaluating the `$condition` variable.</span></span> <span data-ttu-id="15bcb-121">Cette valeur `$true` aurait exécuté la commande `Write-Output` à l’intérieur du scriptblock.</span><span class="sxs-lookup"><span data-stu-id="15bcb-121">It was `$true` and would have executed the `Write-Output` command inside the scriptblock.</span></span>

<span data-ttu-id="15bcb-122">Dans certains langages, vous pouvez placer une simple ligne de code après l’instruction `if` afin de l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="15bcb-122">In some languages, you can place a single line of code after the `if` statement and it gets executed.</span></span> <span data-ttu-id="15bcb-123">Ce n’est pas le cas dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15bcb-123">That isn't the case in PowerShell.</span></span> <span data-ttu-id="15bcb-124">Vous devez fournir un élément `scriptblock` complet avec entre accolades pour que l’instruction fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="15bcb-124">You must provide a full `scriptblock` with braces for it to work correctly.</span></span>

## <a name="comparison-operators"></a><span data-ttu-id="15bcb-125">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="15bcb-125">Comparison operators</span></span>

<span data-ttu-id="15bcb-126">Le plus souvent, l’instruction `if` sert à comparer deux éléments.</span><span class="sxs-lookup"><span data-stu-id="15bcb-126">The most common use of the `if` statement for is comparing two items with each other.</span></span> <span data-ttu-id="15bcb-127">PowerShell propose des opérateurs spéciaux pour différents scénarios de comparaison.</span><span class="sxs-lookup"><span data-stu-id="15bcb-127">PowerShell has special operators for different comparison scenarios.</span></span> <span data-ttu-id="15bcb-128">Lorsque vous utilisez un opérateur de comparaison, la valeur à gauche est comparée à la valeur à droite.</span><span class="sxs-lookup"><span data-stu-id="15bcb-128">When you use a comparison operator, the value on the left-hand side is compared to the value on the right-hand side.</span></span>

### <a name="-eq-for-equality"></a><span data-ttu-id="15bcb-129">-eq pour égalité</span><span class="sxs-lookup"><span data-stu-id="15bcb-129">-eq for equality</span></span>

<span data-ttu-id="15bcb-130">L’opérateur `-eq` vérifie l’égalité entre deux valeurs pour s’assurer qu’elles sont égales.</span><span class="sxs-lookup"><span data-stu-id="15bcb-130">The `-eq` does an equality check between two values to make sure they're equal to each other.</span></span>

```powershell
$value = Get-MysteryValue
if ( 5 -eq $value )
{
    # do something
}
```

<span data-ttu-id="15bcb-131">Dans cet exemple, je prends une valeur connue `5` et je la compare à ma valeur `$value` pour vérifier si elles correspondent.</span><span class="sxs-lookup"><span data-stu-id="15bcb-131">In this example, I'm taking a known value of `5` and comparing it to my `$value` to see if they match.</span></span>

<span data-ttu-id="15bcb-132">Un cas d’utilisation possible consiste à vérifier l’état d’une valeur avant d’effectuer une action sur celle-ci.</span><span class="sxs-lookup"><span data-stu-id="15bcb-132">One possible use case is to check the status of a value before you take an action on it.</span></span> <span data-ttu-id="15bcb-133">Vous pouvez obtenir un service et vérifier que l’état était en cours d’exécution avant d’appeler `Restart-Service` sur ce service.</span><span class="sxs-lookup"><span data-stu-id="15bcb-133">You could get a service and check that the status was running before you called `Restart-Service` on it.</span></span>

<span data-ttu-id="15bcb-134">Dans d’autres langages comme C#, il est courant d’utiliser `==` pour l’égalité (ex : `5 == $value`), mais cela ne fonctionne pas avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15bcb-134">It's common in other languages like C# to use `==` for equality (ex: `5 == $value`) but that doesn't work with PowerShell.</span></span> <span data-ttu-id="15bcb-135">Une autre erreur courante commise consiste à utiliser le signe égal (ex : `5 = $value`) qui est réservé à l’attribution de valeurs aux variables.</span><span class="sxs-lookup"><span data-stu-id="15bcb-135">Another common mistake that people make is to use the equals sign (ex: `5 = $value`) that is reserved for assigning values to variables.</span></span> <span data-ttu-id="15bcb-136">En plaçant votre valeur connue sur la partie gauche, vous limitez les risques de produire cette erreur.</span><span class="sxs-lookup"><span data-stu-id="15bcb-136">By placing your known value on the left, it makes that mistaken more awkward to make.</span></span>

<span data-ttu-id="15bcb-137">Cet opérateur (et d’autres) comportent quelques variantes.</span><span class="sxs-lookup"><span data-stu-id="15bcb-137">This operator (and others) has a few variations.</span></span>

- <span data-ttu-id="15bcb-138">`-eq` égalité, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-138">`-eq` case-insensitive equality</span></span>
- <span data-ttu-id="15bcb-139">`-ieq` égalité, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-139">`-ieq` case-insensitive equality</span></span>
- <span data-ttu-id="15bcb-140">`-ceq` égalité, avec respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-140">`-ceq` case-sensitive equality</span></span>

### <a name="-ne-not-equal"></a><span data-ttu-id="15bcb-141">-ne non égal à</span><span class="sxs-lookup"><span data-stu-id="15bcb-141">-ne not equal</span></span>

<span data-ttu-id="15bcb-142">De nombreux opérateurs intègrent un opérateur associé qui vérifie le résultat inverse.</span><span class="sxs-lookup"><span data-stu-id="15bcb-142">Many operators have a related operator that is checking for the opposite result.</span></span> <span data-ttu-id="15bcb-143">`-ne` vérifie que les valeurs ne sont pas égales.</span><span class="sxs-lookup"><span data-stu-id="15bcb-143">`-ne` verifies that the values don't equal each other.</span></span>

```powershell
if ( 5 -ne $value )
{
    # do something
}
```

<span data-ttu-id="15bcb-144">Utilisez-le pour vous assurer que l’action s’exécute uniquement si la valeur n’est pas `5`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-144">Use this to make sure that the action only executes if the value isn't `5`.</span></span> <span data-ttu-id="15bcb-145">Ce type d’opérateur est notamment utile pour vérifier si un service était à l’état en cours d’exécution avant d’essayer de le démarrer.</span><span class="sxs-lookup"><span data-stu-id="15bcb-145">A good use-cases where would be to check if a service was in the running state before you try to start it.</span></span>

<span data-ttu-id="15bcb-146">**Variantes :**</span><span class="sxs-lookup"><span data-stu-id="15bcb-146">**Variations:**</span></span>

- <span data-ttu-id="15bcb-147">`-ne` non égal à, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-147">`-ne` case-insensitive not equal</span></span>
- <span data-ttu-id="15bcb-148">`-ine` non égal à, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-148">`-ine` case-insensitive not equal</span></span>
- <span data-ttu-id="15bcb-149">`-cne` non égal à, avec respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-149">`-cne` case-sensitive not equal</span></span>

<span data-ttu-id="15bcb-150">Il s’agit de variantes inverses de `-eq`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-150">These are inverse variations of `-eq`.</span></span> <span data-ttu-id="15bcb-151">Je regroupe ces types lorsque je répertorie des variantes pour d’autres opérateurs.</span><span class="sxs-lookup"><span data-stu-id="15bcb-151">I'll group these types together when I list variations for other operators.</span></span>

### <a name="-gt--ge--lt--le-for-greater-than-or-less-than"></a><span data-ttu-id="15bcb-152">-gt -ge -lt -le pour supérieur à ou inférieur à</span><span class="sxs-lookup"><span data-stu-id="15bcb-152">-gt -ge -lt -le for greater than or less than</span></span>

<span data-ttu-id="15bcb-153">Ces opérateurs servent à vérifier si une valeur est supérieure ou inférieure à une autre valeur.</span><span class="sxs-lookup"><span data-stu-id="15bcb-153">These operators are used when checking to see if a value is larger or smaller than another value.</span></span>
<span data-ttu-id="15bcb-154">Les valeurs `-gt -ge -lt -le` signifient GreaterThan (supérieur à), GreaterThanOrEqual (supérieur ou égal à), LessThan (inférieur à) et LessThanOrEqual (inférieur ou égal à).</span><span class="sxs-lookup"><span data-stu-id="15bcb-154">The `-gt -ge -lt -le` stand for GreaterThan, GreaterThanOrEqual, LessThan, and LessThanOrEqual.</span></span>

```powershell
if ( $value -gt 5 )
{
    # do something
}
```

<span data-ttu-id="15bcb-155">**Variantes :**</span><span class="sxs-lookup"><span data-stu-id="15bcb-155">**Variations:**</span></span>

- <span data-ttu-id="15bcb-156">`-gt` supérieur à</span><span class="sxs-lookup"><span data-stu-id="15bcb-156">`-gt` greater than</span></span>
- <span data-ttu-id="15bcb-157">`-igt` supérieur à, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-157">`-igt` greater than, case-insensitive</span></span>
- <span data-ttu-id="15bcb-158">`-cgt` supérieur à, avec respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-158">`-cgt` greater than, case-sensitive</span></span>
- <span data-ttu-id="15bcb-159">`-ge` supérieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="15bcb-159">`-ge` greater than or equal</span></span>
- <span data-ttu-id="15bcb-160">`-ige` supérieur ou égal à, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-160">`-ige` greater than or equal, case-insensitive</span></span>
- <span data-ttu-id="15bcb-161">`-cge` supérieur ou égal à, avec respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-161">`-cge` greater than or equal, case-sensitive</span></span>
- <span data-ttu-id="15bcb-162">`-lt` inférieur à</span><span class="sxs-lookup"><span data-stu-id="15bcb-162">`-lt` less than</span></span>
- <span data-ttu-id="15bcb-163">`-ilt` inférieur à, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-163">`-ilt` less than, case-insensitive</span></span>
- <span data-ttu-id="15bcb-164">`-clt` inférieur à, avec respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-164">`-clt` less than, case-sensitive</span></span>
- <span data-ttu-id="15bcb-165">`-le` inférieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="15bcb-165">`-le` less than or equal</span></span>
- <span data-ttu-id="15bcb-166">`-ile` inférieur ou égal à, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-166">`-ile` less than or equal, case-insensitive</span></span>
- <span data-ttu-id="15bcb-167">`-cle` inférieur ou égal à, avec respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-167">`-cle` less than or equal, case-sensitive</span></span>

<span data-ttu-id="15bcb-168">Il n’y a aucune raison d’utiliser des options qui respectent ou non la casse pour ces opérateurs.</span><span class="sxs-lookup"><span data-stu-id="15bcb-168">I don't know why you would use case-sensitive and insensitive options for these operators.</span></span>

### <a name="-like-wildcard-matches"></a><span data-ttu-id="15bcb-169">-like correspondances de caractères génériques</span><span class="sxs-lookup"><span data-stu-id="15bcb-169">-like wildcard matches</span></span>

<span data-ttu-id="15bcb-170">PowerShell possède sa propre syntaxe de correspondance de modèles de caractères génériques, et vous pouvez l’utiliser avec l’opérateur `-like`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-170">PowerShell has its own wildcard-based pattern matching syntax and you can use it with the `-like` operator.</span></span> <span data-ttu-id="15bcb-171">Ces modèles de caractères génériques sont assez simples.</span><span class="sxs-lookup"><span data-stu-id="15bcb-171">These wildcard patterns are fairly basic.</span></span>

- <span data-ttu-id="15bcb-172">`?` représente n'importe quel caractère unique</span><span class="sxs-lookup"><span data-stu-id="15bcb-172">`?` matches any single character</span></span>
- <span data-ttu-id="15bcb-173">`*` représente n’importe quel nombre de caractères</span><span class="sxs-lookup"><span data-stu-id="15bcb-173">`*` matches any number of characters</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -like 'S-*-SQL??')
{
    # do something
}
```

<span data-ttu-id="15bcb-174">Il est important de souligner que le modèle correspond à la chaîne entière.</span><span class="sxs-lookup"><span data-stu-id="15bcb-174">It's important to point out that the pattern matches the whole string.</span></span> <span data-ttu-id="15bcb-175">Si vous devez mettre en correspondance un élément au milieu de la chaîne, vous devez placer le symbole `*` aux deux extrémités de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="15bcb-175">If you need to match something in the middle of the string, you need to place the `*` on both ends of the string.</span></span>

```powershell
$value = 'S-ATX-SQL02'
if ( $value -like '*SQL*')
{
    # do something
}
```

<span data-ttu-id="15bcb-176">**Variantes :**</span><span class="sxs-lookup"><span data-stu-id="15bcb-176">**Variations:**</span></span>

- <span data-ttu-id="15bcb-177">`-like` caractère générique, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-177">`-like` case-insensitive wildcard</span></span>
- <span data-ttu-id="15bcb-178">`-ilike` caractère générique, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-178">`-ilike` case-insensitive wildcard</span></span>
- <span data-ttu-id="15bcb-179">`-clike` caractère générique, avec respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-179">`-clike` case-sensitive wildcard</span></span>
- <span data-ttu-id="15bcb-180">`-notlike` caractère générique sans correspondance, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-180">`-notlike` case-insensitive wildcard not matched</span></span>
- <span data-ttu-id="15bcb-181">`-inotlike` caractère générique sans correspondance, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-181">`-inotlike` case-insensitive wildcard not matched</span></span>
- <span data-ttu-id="15bcb-182">`-cnotlike` caractère générique sans correspondance, avec respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-182">`-cnotlike` case-sensitive wildcard not matched</span></span>

### <a name="-match-regular-expression"></a><span data-ttu-id="15bcb-183">-match expression régulière</span><span class="sxs-lookup"><span data-stu-id="15bcb-183">-match regular expression</span></span>

<span data-ttu-id="15bcb-184">L’opérateur `-match` vous permet de vérifier la correspondance d’une chaîne en fonction d’une expression régulière.</span><span class="sxs-lookup"><span data-stu-id="15bcb-184">The `-match` operator allows you to check a string for a regular-expression-based match.</span></span> <span data-ttu-id="15bcb-185">Utilisez cet opérateur si les modèles de caractères génériques ne vous offrent pas assez de souplesse.</span><span class="sxs-lookup"><span data-stu-id="15bcb-185">Use this when the wildcard patterns aren't flexible enough for you.</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'S-\w\w\w-SQL\d\d')
{
    # do something
}
```

<span data-ttu-id="15bcb-186">Par défaut, un modèle d’expression régulière (regex) représente n’importe quelle partie de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="15bcb-186">A regex pattern matches anywhere in the string by default.</span></span> <span data-ttu-id="15bcb-187">Vous pouvez donc définir la correspondance d’une sous-chaîne de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="15bcb-187">So you can specify a substring that you want matched like this:</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'SQL')
{
    # do something
}
```

<span data-ttu-id="15bcb-188">Regex est un langage complexe, qui mérite d’être examiné.</span><span class="sxs-lookup"><span data-stu-id="15bcb-188">Regex is a complex language of its own and worth looking into.</span></span> <span data-ttu-id="15bcb-189">J’aborderai plus en détail l’opérateur `-match` et [les nombreuses façons d’utiliser regex][] dans un autre article.</span><span class="sxs-lookup"><span data-stu-id="15bcb-189">I talk more about `-match` and [the many ways to use regex][] in another article.</span></span>

<span data-ttu-id="15bcb-190">**Variantes :**</span><span class="sxs-lookup"><span data-stu-id="15bcb-190">**Variations:**</span></span>

- <span data-ttu-id="15bcb-191">`-match` regex, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-191">`-match` case-insensitive regex</span></span>
- <span data-ttu-id="15bcb-192">`-imatch` regex, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-192">`-imatch` case-insensitive regex</span></span>
- <span data-ttu-id="15bcb-193">`-cmatch` regex, avec respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-193">`-cmatch` case-sensitive regex</span></span>
- <span data-ttu-id="15bcb-194">`-notmatch` regex sans correspondance, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-194">`-notmatch` case-insensitive regex not matched</span></span>
- <span data-ttu-id="15bcb-195">`-inotmatch` regex sans correspondance, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-195">`-inotmatch` case-insensitive regex not matched</span></span>
- <span data-ttu-id="15bcb-196">`-cnotmatch` regex sans correspondance, avec respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-196">`-cnotmatch` case-sensitive regex not matched</span></span>

### <a name="-is-of-type"></a><span data-ttu-id="15bcb-197">-is de type</span><span class="sxs-lookup"><span data-stu-id="15bcb-197">-is of type</span></span>

<span data-ttu-id="15bcb-198">Vous pouvez vérifier le type d’une valeur à l’aide de l’opérateur `-is`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-198">You can check a value's type with the `-is` operator.</span></span>

```powershell
if ( $value -is [string] )
{
    # do something
}
```

<span data-ttu-id="15bcb-199">Vous pouvez l’utiliser avec des classes ou pour accepter différents objets sur le pipeline.</span><span class="sxs-lookup"><span data-stu-id="15bcb-199">You may use this if you're working with classes or accepting various objects over the pipeline.</span></span> <span data-ttu-id="15bcb-200">Vous pouvez utiliser un service ou un nom de service comme entrée.</span><span class="sxs-lookup"><span data-stu-id="15bcb-200">You could have either a service or a service name as your input.</span></span> <span data-ttu-id="15bcb-201">Puis pour vérifier si vous disposez d’un service et pour extraire le service si vous avez uniquement le nom.</span><span class="sxs-lookup"><span data-stu-id="15bcb-201">Then check to see if you have a service and fetch the service if you only have the name.</span></span>

```powershell
if ( $Service -isnot [System.ServiceProcess.ServiceController] )
{
    $Service = Get-Service -Name $Service
}
```

<span data-ttu-id="15bcb-202">**Variantes :**</span><span class="sxs-lookup"><span data-stu-id="15bcb-202">**Variations:**</span></span>

- <span data-ttu-id="15bcb-203">`-is` de type</span><span class="sxs-lookup"><span data-stu-id="15bcb-203">`-is` of type</span></span>
- <span data-ttu-id="15bcb-204">`-isnot` non de type</span><span class="sxs-lookup"><span data-stu-id="15bcb-204">`-isnot` not of type</span></span>

## <a name="collection-operators"></a><span data-ttu-id="15bcb-205">Ensemble d’opérateurs</span><span class="sxs-lookup"><span data-stu-id="15bcb-205">Collection operators</span></span>

<span data-ttu-id="15bcb-206">Lorsque vous utilisez les opérateurs précédents avec une valeur unique, le résultat est `$true` ou `$false`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-206">When you use the previous operators with a single value, the result is `$true` or `$false`.</span></span> <span data-ttu-id="15bcb-207">Avec un ensemble d’opérateurs, la procédure est légèrement différente.</span><span class="sxs-lookup"><span data-stu-id="15bcb-207">This is handled slightly differently when working with a collection.</span></span> <span data-ttu-id="15bcb-208">Chaque élément de l’ensemble est évalué, et l’opérateur retourne chaque valeur correspondant à `$true`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-208">Each item in the collection gets evaluated and the operator returns every value that evaluates to `$true`.</span></span>

```powershell
PS> 1,2,3,4 -eq 3
3
```

<span data-ttu-id="15bcb-209">Cette méthode fonctionne également avec une instruction `if`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-209">This still works correctly in a `if` statement.</span></span> <span data-ttu-id="15bcb-210">Par conséquent, une valeur est retournée par votre opérateur, puis l’instruction entière est `$true`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-210">So a value is returned by your operator, then the whole statement is `$true`.</span></span>

```powershell
$array = 1..6
if ( $array -gt 3 )
{
    # do something
}
```

<span data-ttu-id="15bcb-211">Mais cette méthode cache un petit piège que je tiens à signaler. Lorsque vous utilisez l’opérateur `-ne` de cette manière, il est facile d’appliquer par erreur la logique de manière inversée.</span><span class="sxs-lookup"><span data-stu-id="15bcb-211">There's one small trap hiding in the details here that I need to point out. When using the `-ne` operator this way, it's easy to mistakenly look at the logic backwards.</span></span> <span data-ttu-id="15bcb-212">L’utilisation de `-ne` avec un ensemble d’opérateurs retourne `$true` si un élément de l’ensemble ne correspond pas à votre valeur.</span><span class="sxs-lookup"><span data-stu-id="15bcb-212">Using `-ne` with a collection returns `$true` if any item in the collection doesn't match your value.</span></span>

```powershell
PS> 1,2,3 -ne 4
1
2
3
```

<span data-ttu-id="15bcb-213">Cela peut sembler astucieux, mais nous disposons des opérateurs `-contains` et `-in` encore plus efficaces.</span><span class="sxs-lookup"><span data-stu-id="15bcb-213">This may look like a clever trick, but we have operators `-contains` and `-in` that handle this more efficiently.</span></span> <span data-ttu-id="15bcb-214">Et l’opérateur `-notcontains` répond exactement à vos besoins.</span><span class="sxs-lookup"><span data-stu-id="15bcb-214">And `-notcontains` does what you expect.</span></span>

### <a name="-contains"></a><span data-ttu-id="15bcb-215">-contains</span><span class="sxs-lookup"><span data-stu-id="15bcb-215">-contains</span></span>

<span data-ttu-id="15bcb-216">L’opérateur `-contains` recherche votre valeur dans l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="15bcb-216">The `-contains` operator checks the collection for your value.</span></span> <span data-ttu-id="15bcb-217">Dès qu’il trouve une correspondance, il retourne `$true`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-217">As soon as it finds a match, it returns `$true`.</span></span>

```powershell
$array = 1..6
if ( $array -contains 3 )
{
    # do something
}
```

<span data-ttu-id="15bcb-218">Il s’agit de la méthode recommandée pour déterminer si un ensemble contient votre valeur.</span><span class="sxs-lookup"><span data-stu-id="15bcb-218">This is the preferred way to see if a collection contains your value.</span></span> <span data-ttu-id="15bcb-219">L’utilisation de `Where-Object` (ou `-eq`) parcourt chaque fois la liste entière mais ce processus est beaucoup plus lent.</span><span class="sxs-lookup"><span data-stu-id="15bcb-219">Using `Where-Object` (or `-eq`) walks the entire list every time and is significantly slower.</span></span>

<span data-ttu-id="15bcb-220">**Variantes :**</span><span class="sxs-lookup"><span data-stu-id="15bcb-220">**Variations:**</span></span>

- <span data-ttu-id="15bcb-221">`-contains` correspondance, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-221">`-contains` case-insensitive match</span></span>
- <span data-ttu-id="15bcb-222">`-icontains` correspondance, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-222">`-icontains` case-insensitive match</span></span>
- <span data-ttu-id="15bcb-223">`-ccontains` correspondance, avec respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-223">`-ccontains` case-sensitive match</span></span>
- <span data-ttu-id="15bcb-224">`-notcontains` sans correspondance, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-224">`-notcontains` case-insensitive not matched</span></span>
- <span data-ttu-id="15bcb-225">`-inotcontains` sans correspondance, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-225">`-inotcontains` case-insensitive not matched</span></span>
- <span data-ttu-id="15bcb-226">`-cnotcontains` sans correspondance, avec respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-226">`-cnotcontains` case-sensitive not matched</span></span>

### <a name="-in"></a><span data-ttu-id="15bcb-227">-in</span><span class="sxs-lookup"><span data-stu-id="15bcb-227">-in</span></span>

<span data-ttu-id="15bcb-228">L’opérateur `-in` est similaire à l’opérateur `-contains`, sauf que l’ensemble se trouve sur le côté droit.</span><span class="sxs-lookup"><span data-stu-id="15bcb-228">The `-in` operator is just like the `-contains` operator except the collection is on the right-hand side.</span></span>

```powershell
$array = 1..6
if ( 3 -in $array )
{
    # do something
}
```

<span data-ttu-id="15bcb-229">**Variantes :**</span><span class="sxs-lookup"><span data-stu-id="15bcb-229">**Variations:**</span></span>

- <span data-ttu-id="15bcb-230">`-in` correspondance, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-230">`-in` case-insensitive match</span></span>
- <span data-ttu-id="15bcb-231">`-iin` correspondance, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-231">`-iin` case-insensitive match</span></span>
- <span data-ttu-id="15bcb-232">`-cin` correspondance, avec respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-232">`-cin` case-sensitive match</span></span>
- <span data-ttu-id="15bcb-233">`-notin` sans correspondance, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-233">`-notin` case-insensitive not matched</span></span>
- <span data-ttu-id="15bcb-234">`-inotin` sans correspondance, sans respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-234">`-inotin` case-insensitive not matched</span></span>
- <span data-ttu-id="15bcb-235">`-cnotin` sans correspondance, avec respect de la casse</span><span class="sxs-lookup"><span data-stu-id="15bcb-235">`-cnotin` case-sensitive not matched</span></span>

## <a name="logical-operators"></a><span data-ttu-id="15bcb-236">Opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="15bcb-236">Logical operators</span></span>

<span data-ttu-id="15bcb-237">Les opérateurs logiques sont utilisés pour inverser ou combiner d’autres expressions.</span><span class="sxs-lookup"><span data-stu-id="15bcb-237">Logical operators are used to invert or combine other expressions.</span></span>

### <a name="-not"></a><span data-ttu-id="15bcb-238">-not</span><span class="sxs-lookup"><span data-stu-id="15bcb-238">-not</span></span>

<span data-ttu-id="15bcb-239">L’opérateur `-not` retourne une expression de `$false` à `$true` ou de `$true` à `$false`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-239">The `-not` operator flips an expression from `$false` to `$true` or from `$true` to `$false`.</span></span> <span data-ttu-id="15bcb-240">Voici un exemple dans lequel effectuer une action lorsque `Test-Path` est `$false`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-240">Here is an example where we want to perform an action when `Test-Path` is `$false`.</span></span>

```powershell
if ( -not ( Test-Path -Path $path ) )
```

<span data-ttu-id="15bcb-241">La plupart des opérateurs dont nous avons parlé proposent une variante dans laquelle vous n’avez pas besoin d’utiliser l’opérateur `-not`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-241">Most of the operators we talked about do have a variation where you do not need to use the `-not` operator.</span></span> <span data-ttu-id="15bcb-242">Mais cet opérateur est parfois utile.</span><span class="sxs-lookup"><span data-stu-id="15bcb-242">But there are still times it is useful.</span></span>

### <a name="-operator"></a><span data-ttu-id="15bcb-243">!</span><span class="sxs-lookup"><span data-stu-id="15bcb-243">!</span></span> <span data-ttu-id="15bcb-244">operator</span><span class="sxs-lookup"><span data-stu-id="15bcb-244">operator</span></span>

<span data-ttu-id="15bcb-245">Vous pouvez utiliser `!` comme alias pour `-not`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-245">You can use `!` as an alias for `-not`.</span></span>

```powershell
if ( -not $value ){}
if ( !$value ){}
```

<span data-ttu-id="15bcb-246">Peut-être avez-vous remarqué que l’opérateur `!` était davantage utilisé par les personnes qui maîtrisent d’autres langages, comme C# .</span><span class="sxs-lookup"><span data-stu-id="15bcb-246">You may see `!` used more by people that come from another languages like C#.</span></span> <span data-ttu-id="15bcb-247">Je préfère le saisir car j’ai parfois du mal à le repérer quand j’examine rapidement mes scripts.</span><span class="sxs-lookup"><span data-stu-id="15bcb-247">I prefer to type it out because I find it hard to see when quickly looking at my scripts.</span></span>

### <a name="-and"></a><span data-ttu-id="15bcb-248">-and</span><span class="sxs-lookup"><span data-stu-id="15bcb-248">-and</span></span>

<span data-ttu-id="15bcb-249">Vous pouvez combiner des expressions avec l’opérateur `-and`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-249">You can combine expressions with the `-and` operator.</span></span> <span data-ttu-id="15bcb-250">Dans ce cas, les deux côtés doivent être `$true` pour que l’expression entière soit `$true`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-250">When you do that, both sides need to be `$true` for the whole expression to be `$true`.</span></span>

```powershell
if ( ($age -gt 13) -and ($age -lt 55) )
```

<span data-ttu-id="15bcb-251">Dans cet exemple, `$age` doit être supérieur ou égal à 13 pour le côté gauche, et inférieur à 55 pour le côté droit.</span><span class="sxs-lookup"><span data-stu-id="15bcb-251">In that example, `$age` must be 13 or older for the left side and less than 55 for the right side.</span></span> <span data-ttu-id="15bcb-252">J’ai ajouté d’autres parenthèses pour le rendre plus clair dans cet exemple, mais elles sont facultatives tant que l’expression est simple.</span><span class="sxs-lookup"><span data-stu-id="15bcb-252">I added extra parentheses to make it clearer in that example but they're optional as long as the expression is simple.</span></span> <span data-ttu-id="15bcb-253">Voici le même exemple sans parenthèses.</span><span class="sxs-lookup"><span data-stu-id="15bcb-253">Here is the same example without them.</span></span>

```powershell
if ( $age -gt 13 -and $age -lt 55 )
```

<span data-ttu-id="15bcb-254">L’évaluation se produit de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="15bcb-254">Evaluation happens from left to right.</span></span> <span data-ttu-id="15bcb-255">Si le premier élément a la valeur `$false`, il s’arrête prématurément et n’effectue pas la comparaison appropriée.</span><span class="sxs-lookup"><span data-stu-id="15bcb-255">If the first item evaluates to `$false`, it exits early and doesn't perform the right comparison.</span></span> <span data-ttu-id="15bcb-256">Cela est pratique lorsque vous devez vérifier qu’une valeur existe avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="15bcb-256">This is handy when you need to make sure a value exists before you use it.</span></span> <span data-ttu-id="15bcb-257">Par exemple, `Test-Path` génère une erreur si vous lui attribuez un chemin d’accès `$null`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-257">For example, `Test-Path` throws an error if you give it a `$null` path.</span></span>

```powershell
if ( $null -ne $path -and (Test-Path -Path $path) )
```

### <a name="-or"></a><span data-ttu-id="15bcb-258">-or</span><span class="sxs-lookup"><span data-stu-id="15bcb-258">-or</span></span>

<span data-ttu-id="15bcb-259">L’opérateur `-or` vous permet de spécifier deux expressions, et retourne `$true` si l’une d’elles est `$true`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-259">The `-or` allows for you to specify two expressions and returns `$true` if either one of them is `$true`.</span></span>

```powershell
if ( $age -le 13 -or $age -ge 55 )
```

<span data-ttu-id="15bcb-260">Comme avec l’opérateur `-and`, l’évaluation se produit de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="15bcb-260">Just like with the `-and` operator, the evaluation happens from left to right.</span></span> <span data-ttu-id="15bcb-261">Hormis le fait que si la première partie est `$true`, l’instruction entière est `$true` et elle ignore le reste de l’expression.</span><span class="sxs-lookup"><span data-stu-id="15bcb-261">Except that if the first part is `$true`, then the whole statement is `$true` and it doesn't process the rest of the expression.</span></span>

<span data-ttu-id="15bcb-262">Notez également le fonctionnement de la syntaxe pour ces opérateurs.</span><span class="sxs-lookup"><span data-stu-id="15bcb-262">Also make note of how the syntax works for these operators.</span></span> <span data-ttu-id="15bcb-263">Vous avez besoin de deux expressions distinctes.</span><span class="sxs-lookup"><span data-stu-id="15bcb-263">You need two separate expressions.</span></span> <span data-ttu-id="15bcb-264">Certains utilisateurs essaient d’effectuer une opération semblable à celle-ci `$value -eq 5 -or 6`, sans se rendre compte de leur erreur.</span><span class="sxs-lookup"><span data-stu-id="15bcb-264">I have seen users try to do something like this `$value -eq 5 -or 6` without realizing their mistake.</span></span>

### <a name="-xor-exclusive-or"></a><span data-ttu-id="15bcb-265">-xor or exclusif</span><span class="sxs-lookup"><span data-stu-id="15bcb-265">-xor exclusive or</span></span>

<span data-ttu-id="15bcb-266">Cet opérateur est un peu particulier.</span><span class="sxs-lookup"><span data-stu-id="15bcb-266">This one is a little unusual.</span></span> <span data-ttu-id="15bcb-267">`-xor` permet à une seule expression de renvoyer la valeur `$true`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-267">`-xor` allows only one expression to evaluate to `$true`.</span></span> <span data-ttu-id="15bcb-268">Par conséquent, si les deux éléments sont `$false` ou `$true`, l’expression entière est `$false`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-268">So if both items are `$false` or both items are `$true`, then the whole expression is `$false`.</span></span> <span data-ttu-id="15bcb-269">Cela revient à affirmer que cette expression est uniquement `$true` lorsque les résultats de l’expression sont différents.</span><span class="sxs-lookup"><span data-stu-id="15bcb-269">Another way to look at this is the expression is only `$true` when the results of the expression are different.</span></span>

<span data-ttu-id="15bcb-270">Il est très peu probable qu’une personne utilise cet opérateur logique, et je ne vois aucun exemple où il pourrait être utile.</span><span class="sxs-lookup"><span data-stu-id="15bcb-270">It's rare that anyone would ever use this logical operator and I can't think up a good example as to why I would ever use it.</span></span>

## <a name="bitwise-operators"></a><span data-ttu-id="15bcb-271">Opérateurs de bits</span><span class="sxs-lookup"><span data-stu-id="15bcb-271">Bitwise operators</span></span>

<span data-ttu-id="15bcb-272">Les opérateurs de bits effectuent des calculs sur les bits dans les valeurs et génèrent une nouvelle valeur comme résultat.</span><span class="sxs-lookup"><span data-stu-id="15bcb-272">Bitwise operators perform calculations on the bits within the values and produce a new value as the result.</span></span> <span data-ttu-id="15bcb-273">L’apprentissage des [opérateurs de bits][] dépasse le cadre de cet article, mais en voici la liste.</span><span class="sxs-lookup"><span data-stu-id="15bcb-273">Teaching [bitwise operators][] is beyond the scope of this article, but here is the list the them.</span></span>

- <span data-ttu-id="15bcb-274">`-band` binaire AND</span><span class="sxs-lookup"><span data-stu-id="15bcb-274">`-band` binary AND</span></span>
- <span data-ttu-id="15bcb-275">`-bor` binaire OR</span><span class="sxs-lookup"><span data-stu-id="15bcb-275">`-bor` binary OR</span></span>
- <span data-ttu-id="15bcb-276">`-bxor` binaire OR exclusif</span><span class="sxs-lookup"><span data-stu-id="15bcb-276">`-bxor` binary exclusive OR</span></span>
- <span data-ttu-id="15bcb-277">`-bnot` binaire NOT</span><span class="sxs-lookup"><span data-stu-id="15bcb-277">`-bnot` binary NOT</span></span>
- <span data-ttu-id="15bcb-278">`-shl` décalage vers la gauche</span><span class="sxs-lookup"><span data-stu-id="15bcb-278">`-shl` shift left</span></span>
- <span data-ttu-id="15bcb-279">`-shr` décalage vers la droite</span><span class="sxs-lookup"><span data-stu-id="15bcb-279">`-shr` shift right</span></span>

## <a name="powershell-expressions"></a><span data-ttu-id="15bcb-280">Expressions PowerShell</span><span class="sxs-lookup"><span data-stu-id="15bcb-280">PowerShell expressions</span></span>

<span data-ttu-id="15bcb-281">Nous pouvons utiliser PowerShell normalement dans l’instruction de condition.</span><span class="sxs-lookup"><span data-stu-id="15bcb-281">We can use normal PowerShell inside the condition statement.</span></span>

```powershell
if ( Test-Path -Path $Path )
```

<span data-ttu-id="15bcb-282">`Test-Path` retourne `$true` ou `$false` lorsqu’il s’exécute.</span><span class="sxs-lookup"><span data-stu-id="15bcb-282">`Test-Path` returns `$true` or `$false` when it executes.</span></span> <span data-ttu-id="15bcb-283">Cela s’applique également aux commandes qui retournent d’autres valeurs.</span><span class="sxs-lookup"><span data-stu-id="15bcb-283">This also applies to commands that return other values.</span></span>

```powershell
if ( Get-Process Notepad* )
```

<span data-ttu-id="15bcb-284">L’expression renvoie la valeur `$true` s’il existe un processus retourné, et `$false` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="15bcb-284">It evaluates to `$true` if there's a returned process and `$false` if there'sn'thing.</span></span> <span data-ttu-id="15bcb-285">Vous pouvez tout à fait utiliser des expressions de pipeline ou d’autres instructions PowerShell comme suit :</span><span class="sxs-lookup"><span data-stu-id="15bcb-285">It's perfectly valid to use pipeline expressions or other PowerShell statements like this:</span></span>

```powershell
if ( Get-Process | Where Name -eq Notepad )
```

<span data-ttu-id="15bcb-286">Ces expressions peuvent être combinées avec les opérateurs `-and` et `-or`, mais vous devrez peut-être utiliser des parenthèses pour les décomposer en sous-expressions.</span><span class="sxs-lookup"><span data-stu-id="15bcb-286">These expressions can be combined with each other with the `-and` and `-or` operators, but you may have to use parenthesis to break them into subexpressions.</span></span>

```powershell
if ( (Get-Process) -and (Get-Service) )
```

### <a name="checking-for-null"></a><span data-ttu-id="15bcb-287">Recherche de $null</span><span class="sxs-lookup"><span data-stu-id="15bcb-287">Checking for $null</span></span>

<span data-ttu-id="15bcb-288">Si vous n’obtenez aucun résultat ou une valeur `$null`, la valeur `$false` s’affiche dans l’instruction `if`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-288">Having a no result or a `$null` value evaluates to `$false` in the `if` statement.</span></span> <span data-ttu-id="15bcb-289">Lorsqu’il s’agit de vérifier spécifiquement `$null`, il est recommandé de placer `$null` sur le côté gauche.</span><span class="sxs-lookup"><span data-stu-id="15bcb-289">When checking specifically for `$null`, it's a best practice to place the `$null` on the left-hand side.</span></span>

```powershell
if ( $null -eq $value )
```

<span data-ttu-id="15bcb-290">Il existe quelques nuances lorsque vous utilisez des valeurs `$null` dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15bcb-290">There are quite a few nuances when dealing with `$null` values in PowerShell.</span></span> <span data-ttu-id="15bcb-291">Si vous souhaitez approfondir vos connaissances, j’ai préparé un article intitulé [Tout ce que vous avez toujours voulu savoir sur $null][].</span><span class="sxs-lookup"><span data-stu-id="15bcb-291">If you're interested in diving deeper, I have an article about [everything you wanted to know about $null][].</span></span>

### <a name="variable-assignment"></a><span data-ttu-id="15bcb-292">Attribution de variables</span><span class="sxs-lookup"><span data-stu-id="15bcb-292">Variable assignment</span></span>

<span data-ttu-id="15bcb-293">J’allais oublier d’ajouter cet opérateur jusqu’à ce que [Prasoon Karunan V][] me le rappelle.</span><span class="sxs-lookup"><span data-stu-id="15bcb-293">I almost forgot to add this one until [Prasoon Karunan V][] reminded me of it.</span></span>

```powershell
if ($process=Get-Process notepad -ErrorAction ignore) {$process} else {$false}
```

<span data-ttu-id="15bcb-294">Normalement, lorsque vous attribuez une valeur à une variable, la valeur n’est pas transmise au pipeline ni à la console.</span><span class="sxs-lookup"><span data-stu-id="15bcb-294">Normally when you assign a value to a variable, the value isn't passed onto the pipeline or console.</span></span> <span data-ttu-id="15bcb-295">Lorsque vous attribuez une variable dans une sous-expression, elle est transmise au pipeline.</span><span class="sxs-lookup"><span data-stu-id="15bcb-295">When you do a variable assignment in a sub expression, it does get passed on to the pipeline.</span></span>

```powershell
PS> $first = 1
PS> ($second = 2)
2
```

<span data-ttu-id="15bcb-296">Vous remarquez que l’attribution de `$first` n’a pas de sortie, contrairement à l’attribution de `$second` ?</span><span class="sxs-lookup"><span data-stu-id="15bcb-296">See how the `$first` assignment has no output and the `$second` assignment does?</span></span> <span data-ttu-id="15bcb-297">Lorsqu’une attribution est effectuée dans une instruction `if`, elle s’exécute de la même manière que l’attribution `$second` ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="15bcb-297">When an assignment is done in an `if` statement, it executes just like the `$second` assignment above.</span></span> <span data-ttu-id="15bcb-298">Voici un exemple d’utilisation assez clair :</span><span class="sxs-lookup"><span data-stu-id="15bcb-298">Here is a clean example on how you could use it:</span></span>

```powershell
if ( $process = Get-Process Notepad* )
{
    $process | Stop-Process
}
```

<span data-ttu-id="15bcb-299">Si une valeur est attribuée à `$process`, l’instruction est `$true` et `$process` s’arrête.</span><span class="sxs-lookup"><span data-stu-id="15bcb-299">If `$process` gets assigned a value, then the statement is `$true` and `$process` gets stopped.</span></span>

<span data-ttu-id="15bcb-300">Veillez à ne pas confondre cela avec `-eq`, car il ne s’agit pas d’une vérification d’égalité.</span><span class="sxs-lookup"><span data-stu-id="15bcb-300">Make sure you don't confuse this with `-eq` because this isn't an equality check.</span></span> <span data-ttu-id="15bcb-301">Il s’agit d’une fonctionnalité plus complexe dont la plupart des utilisateurs ignorent le processus.</span><span class="sxs-lookup"><span data-stu-id="15bcb-301">This is a more obscure feature that most people don't realize works this way.</span></span>

## <a name="alternate-execution-path"></a><span data-ttu-id="15bcb-302">Autre chemin d'accès d'exécution</span><span class="sxs-lookup"><span data-stu-id="15bcb-302">Alternate execution path</span></span>

<span data-ttu-id="15bcb-303">L’instruction `if` vous permet de spécifier une action non seulement lorsque l’instruction est `$true`, mais également quand elle est `$false`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-303">The `if` statement allows you to specify an action for not only when the statement is `$true`, but also for when it's `$false`.</span></span> <span data-ttu-id="15bcb-304">C’est ici qu’intervient l’instruction `else`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-304">This is where the `else` statement comes into play.</span></span>

### <a name="else"></a><span data-ttu-id="15bcb-305">else</span><span class="sxs-lookup"><span data-stu-id="15bcb-305">else</span></span>

<span data-ttu-id="15bcb-306">L’instruction `else` constitue toujours la dernière partie de l’instruction `if` lorsqu’elle est utilisée.</span><span class="sxs-lookup"><span data-stu-id="15bcb-306">The `else` statement is always the last part of the `if` statement when used.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    Write-Warning "$path doesn't exist or isn't a file."
}
```

<span data-ttu-id="15bcb-307">Dans cet exemple, nous vérifions la valeur `$path` pour s’assurer qu’il s’agit d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="15bcb-307">In this example, we check the `$path` to make sure it's a file.</span></span> <span data-ttu-id="15bcb-308">Si nous trouvons le fichier, nous le déplaçons.</span><span class="sxs-lookup"><span data-stu-id="15bcb-308">If we find the file, we move it.</span></span> <span data-ttu-id="15bcb-309">Sinon, nous créons un avertissement.</span><span class="sxs-lookup"><span data-stu-id="15bcb-309">If not, we write a warning.</span></span> <span data-ttu-id="15bcb-310">Ce type de logique de création de branche est très courant.</span><span class="sxs-lookup"><span data-stu-id="15bcb-310">This type of branching logic is very common.</span></span>

### <a name="nested-if"></a><span data-ttu-id="15bcb-311">if imbriqué</span><span class="sxs-lookup"><span data-stu-id="15bcb-311">Nested if</span></span>

<span data-ttu-id="15bcb-312">Les instructions `if` et `else` prennent un bloc de script, ce qui nous permet de placer n’importe quelle commande PowerShell à l’intérieur de celles-ci, y compris une autre instruction `if`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-312">The `if` and `else` statements take a script block, so we can place any PowerShell command inside them, including another `if` statement.</span></span> <span data-ttu-id="15bcb-313">Vous pouvez ainsi utiliser une logique bien plus complexe.</span><span class="sxs-lookup"><span data-stu-id="15bcb-313">This allows you to make use of much more complicated logic.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    if ( Test-Path -Path $Path )
    {
        Write-Warning "A file was required but a directory was found instead."
    }
    else
    {
        Write-Warning "$path could not be found."
    }
}
```

<span data-ttu-id="15bcb-314">Dans cet exemple, nous testons d’abord le bon chemin d’accès puis nous y effectuons une action.</span><span class="sxs-lookup"><span data-stu-id="15bcb-314">In this example, we test the happy path first and then take action on it.</span></span> <span data-ttu-id="15bcb-315">En cas d’échec, nous procédons à une autre vérification et fournissons des informations plus détaillées à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="15bcb-315">If that fails, we do another check and to provide more detailed information to the user.</span></span>

### <a name="elseif"></a><span data-ttu-id="15bcb-316">elseif</span><span class="sxs-lookup"><span data-stu-id="15bcb-316">elseif</span></span>

<span data-ttu-id="15bcb-317">Nous ne sommes pas limités à une seule vérification conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="15bcb-317">We aren't limited to just a single conditional check.</span></span> <span data-ttu-id="15bcb-318">Nous pouvons chaîner des instructions `if` et `else` au lieu de les imbriquer à l’aide de l’instruction `elseif`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-318">We can chain `if` and `else` statements together instead of nesting them by using the `elseif` statement.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
elseif ( Test-Path -Path $Path )
{
    Write-Warning "A file was required but a directory was found instead."
}
else
{
    Write-Warning "$path could not be found."
}
```

<span data-ttu-id="15bcb-319">L’exécution s’effectue de haut en bas.</span><span class="sxs-lookup"><span data-stu-id="15bcb-319">The execution happens from the top to the bottom.</span></span> <span data-ttu-id="15bcb-320">L’instruction `if` en haut de la liste est évaluée en premier.</span><span class="sxs-lookup"><span data-stu-id="15bcb-320">The top `if` statement is evaluated first.</span></span> <span data-ttu-id="15bcb-321">Si la valeur est `$false`, l’instruction descend jusqu’au prochain élément `elseif` ou `else` dans la liste.</span><span class="sxs-lookup"><span data-stu-id="15bcb-321">If that is `$false`, then it moves down to the next `elseif` or `else` in the list.</span></span> <span data-ttu-id="15bcb-322">Le dernier élément `else` est l’action par défaut à effectuer si aucune des autres ne retourne `$true`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-322">That last `else` is the default action to take if none of the others return `$true`.</span></span>

### <a name="switch"></a><span data-ttu-id="15bcb-323">commutateur</span><span class="sxs-lookup"><span data-stu-id="15bcb-323">switch</span></span>

<span data-ttu-id="15bcb-324">À ce stade, il est important de mentionner l’instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-324">At this point, I need to mention the `switch` statement.</span></span> <span data-ttu-id="15bcb-325">Cette instruction fournit une autre syntaxe permettant d’effectuer plusieurs comparaisons avec une valeur.</span><span class="sxs-lookup"><span data-stu-id="15bcb-325">It provides an alternate syntax for doing multiple comparisons with a value.</span></span> <span data-ttu-id="15bcb-326">Avec l’instruction `switch`, vous spécifiez une expression et ce résultat est comparé à plusieurs valeurs différentes.</span><span class="sxs-lookup"><span data-stu-id="15bcb-326">With the `switch`, you specify an expression and that result gets compared with several different values.</span></span> <span data-ttu-id="15bcb-327">Si l’une de ces valeurs correspond, le bloc de code correspondant est exécuté.</span><span class="sxs-lookup"><span data-stu-id="15bcb-327">If one of those values match, the matching code block is executed.</span></span> <span data-ttu-id="15bcb-328">Prenons cet exemple :</span><span class="sxs-lookup"><span data-stu-id="15bcb-328">Take a look at this example:</span></span>

```powershell
$itemType = 'Role'
switch ( $itemType )
{
    'Component'
    {
        'is a component'
    }
    'Role'
    {
        'is a role'
    }
    'Location'
    {
        'is a location'
    }
}
```

<span data-ttu-id="15bcb-329">trois valeurs possibles peuvent correspondre à `$itemType`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-329">There three possible values that can match the `$itemType`.</span></span> <span data-ttu-id="15bcb-330">Dans ce cas, la valeur correspond à `Role`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-330">In this case, it matches with `Role`.</span></span> <span data-ttu-id="15bcb-331">J’ai utilisé un exemple simple pour vous présenter l’opérateur `switch`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-331">I used a simple example just to give you some exposure to the `switch` operator.</span></span> <span data-ttu-id="15bcb-332">J’aborderai plus en détail le thème [Tout ce que vous avez toujours voulu savoir sur l’instruction switch][] dans un autre article.</span><span class="sxs-lookup"><span data-stu-id="15bcb-332">I talk more about [everything you ever wanted to know about the switch statement][] in another article.</span></span>

## <a name="pipeline"></a><span data-ttu-id="15bcb-333">Pipeline</span><span class="sxs-lookup"><span data-stu-id="15bcb-333">Pipeline</span></span>

<span data-ttu-id="15bcb-334">Le pipeline est une fonctionnalité unique et importante de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15bcb-334">The pipeline is a unique and important feature of PowerShell.</span></span> <span data-ttu-id="15bcb-335">Toute valeur qui n’est pas supprimée ou affectée à une variable est placée dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="15bcb-335">Any value that isn't suppressed or assigned to a variable gets placed in the pipeline.</span></span> <span data-ttu-id="15bcb-336">L’instruction `if` permet de tirer parti du pipeline d’une manière qui n’est pas toujours évidente.</span><span class="sxs-lookup"><span data-stu-id="15bcb-336">The `if` provides us a way to take advantage of the pipeline in a way that isn't always obvious.</span></span>

```powershell
$discount = if ( $age -ge 55 )
{
    Get-SeniorDiscount
}
elseif ( $age -le 13 )
{
    Get-ChildDiscount
}
else
{
    0.00
}
```

<span data-ttu-id="15bcb-337">Chaque bloc de script place les résultats des commandes ou la valeur dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="15bcb-337">Each script block is placing the results the commands or the value into the pipeline.</span></span> <span data-ttu-id="15bcb-338">Nous attribuons ensuite le résultat de l’instruction if à la variable `$discount`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-338">Then we assign the result of the if statement to the `$discount` variable.</span></span> <span data-ttu-id="15bcb-339">Cet exemple peut simplement attribuer ces valeurs à la variable `$discount` directement dans chaque élément scriptblock.</span><span class="sxs-lookup"><span data-stu-id="15bcb-339">That example could have just as easily assigned those values to the `$discount` variable directly in each scriptblock.</span></span> <span data-ttu-id="15bcb-340">Je ne dis pas que je l’utilise souvent avec l’instruction `if`, mais je me rappelle l’avoir fait récemment.</span><span class="sxs-lookup"><span data-stu-id="15bcb-340">I can't say that I use this with the `if` statement often, but I do have an example where I used this recently.</span></span>

### <a name="array-inline"></a><span data-ttu-id="15bcb-341">Tableau en ligne</span><span class="sxs-lookup"><span data-stu-id="15bcb-341">Array inline</span></span>

<span data-ttu-id="15bcb-342">Voici une fonction appelée [Invoke-SnowSql][] qui lance un exécutable avec plusieurs arguments de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="15bcb-342">I have a function called [Invoke-SnowSql][] that launches an executable with several command-line arguments.</span></span> <span data-ttu-id="15bcb-343">Voici un clip dans lequel j’utilise cette fonction pour créer le tableau d’arguments.</span><span class="sxs-lookup"><span data-stu-id="15bcb-343">Here is a clip from that function where I build the array of arguments.</span></span>

```powershell
$snowSqlParam = @(
    '--accountname', $Endpoint
    '--username', $Credential.UserName
    '--option', 'exit_on_error=true'
    '--option', 'output_format=csv'
    '--option', 'friendly=false'
    '--option', 'timing=false'
    if ($Debug)
    {
        '--option', 'log_level=DEBUG'
    }
    if ($Path)
    {
        '--filename', $Path
    }
    else
    {
        '--query', $singleLineQuery
    }
)
```

<span data-ttu-id="15bcb-344">Les variables `$Debug` et `$Path` sont des paramètres de la fonction, fournis par l’utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="15bcb-344">The `$Debug` and `$Path` variables are parameters on the function that are provided by the end user.</span></span>
<span data-ttu-id="15bcb-345">Je les évalue en ligne dans l’initialisation de mon tableau.</span><span class="sxs-lookup"><span data-stu-id="15bcb-345">I evaluate them inline inside the initialization of my array.</span></span> <span data-ttu-id="15bcb-346">Si `$Debug` a la valeur true, ces valeurs sont placées dans `$snowSqlParam`, à l’emplacement approprié.</span><span class="sxs-lookup"><span data-stu-id="15bcb-346">If `$Debug` is true, then those values fall into the `$snowSqlParam` in the correct place.</span></span> <span data-ttu-id="15bcb-347">Il en va de même pour la variable `$Path`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-347">Same holds true for the `$Path` variable.</span></span>

## <a name="simplify-complex-operations"></a><span data-ttu-id="15bcb-348">Simplifier les opérations complexes</span><span class="sxs-lookup"><span data-stu-id="15bcb-348">Simplify complex operations</span></span>

<span data-ttu-id="15bcb-349">Vous vous retrouverez inévitablement dans une situation dans laquelle votre instruction if déborde sur le côté droit de l’écran en raison d’un trop grand nombre de comparaisons à vérifier.</span><span class="sxs-lookup"><span data-stu-id="15bcb-349">It's inevitable that you run into a situation that has way too many comparisons to check and your if statement scrolls way off the right side of the screen.</span></span>

```powershell
$user = Get-ADUser -Identity $UserName
if ( $null -ne $user -and $user.Department -eq 'Finance' -and $user.Title -match 'Senior' -and $user.HomeDrive -notlike '\\server\*' )
{
    # Do Something
}
```

<span data-ttu-id="15bcb-350">Ces comparaisons peuvent être difficiles à lire et ainsi augmenter le risque d’erreur.</span><span class="sxs-lookup"><span data-stu-id="15bcb-350">They can be hard to read and that make you more prone to make mistakes.</span></span> <span data-ttu-id="15bcb-351">Nous pouvons y remédier de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="15bcb-351">There are a few things we can do about that.</span></span>

### <a name="line-continuation"></a><span data-ttu-id="15bcb-352">Continuation de ligne</span><span class="sxs-lookup"><span data-stu-id="15bcb-352">Line continuation</span></span>

<span data-ttu-id="15bcb-353">Dans PowerShell, certains opérateurs vous permettent de prolonger la commande à la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="15bcb-353">There some operators in PowerShell that let you wrap you command to the next line.</span></span> <span data-ttu-id="15bcb-354">Les opérateurs logiques `-and` et `-or` constituent de bons opérateurs si vous souhaitez fractionner votre expression sur plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="15bcb-354">The logical operators `-and` and `-or` are good operators to use if you want to break your expression into multiple lines.</span></span>

```powershell
if ($null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'
)
{
    # Do Something
}
```

<span data-ttu-id="15bcb-355">Beaucoup d’éléments interviennent ici, mais placer chaque morceau sur sa propre ligne améliore grandement le processus.</span><span class="sxs-lookup"><span data-stu-id="15bcb-355">There's still a lot going on there, but placing each piece on its own line makes a big difference.</span></span>
<span data-ttu-id="15bcb-356">Je l’utilise généralement lorsque j’obtiens plus de deux comparaisons ou quand je dois faire défiler l’écran vers la droite pour lire une logique.</span><span class="sxs-lookup"><span data-stu-id="15bcb-356">I generally use this when I get more than two comparisons or if I have to scroll to the right to read any of the logic.</span></span>

### <a name="pre-calculating-results"></a><span data-ttu-id="15bcb-357">Précalcul des résultats</span><span class="sxs-lookup"><span data-stu-id="15bcb-357">Pre-calculating results</span></span>

<span data-ttu-id="15bcb-358">Nous pouvons extraire cette instruction de l’instruction if et vérifier uniquement le résultat.</span><span class="sxs-lookup"><span data-stu-id="15bcb-358">We can take that statement out of the if statement and only check the result.</span></span>

```powershell
$needsSecureHomeDrive = $null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'

if ( $needsSecureHomeDrive )
{
    # Do Something
}
```

<span data-ttu-id="15bcb-359">Cette méthode se révèle plus efficace que celle utilisée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="15bcb-359">This just feels much cleaner than the previous example.</span></span> <span data-ttu-id="15bcb-360">Vous avez également la possibilité d’utiliser un nom de variable qui explique ce que vous êtes en train de vérifier.</span><span class="sxs-lookup"><span data-stu-id="15bcb-360">You also are given an opportunity to use a variable name that explains what it's that you're really checking.</span></span> <span data-ttu-id="15bcb-361">Il s’agit également d’un exemple de code autodocumenté qui consigne les commentaires inutiles.</span><span class="sxs-lookup"><span data-stu-id="15bcb-361">This is also and example of self-documenting code that saves unnecessary comments.</span></span>

### <a name="multiple-if-statements"></a><span data-ttu-id="15bcb-362">Instructions if multiples</span><span class="sxs-lookup"><span data-stu-id="15bcb-362">Multiple if statements</span></span>

<span data-ttu-id="15bcb-363">Nous pouvons la décomposer en plusieurs instructions et les vérifier une par une.</span><span class="sxs-lookup"><span data-stu-id="15bcb-363">We can break this up into multiple statements and check them one at a time.</span></span> <span data-ttu-id="15bcb-364">Dans ce cas, nous utilisons un indicateur ou une variable de suivi pour combiner les résultats.</span><span class="sxs-lookup"><span data-stu-id="15bcb-364">In this case, we use a flag or a tracking variable to combine the results.</span></span>

```powershell

$skipUser = $false

if( $null -eq $user )
{
    $skipUser = $true
}

if( $user.Department -ne 'Finance' )
{
    Write-Verbose "isn't in Finance department"
    $skipUser = $true
}

if( $user.Title -match 'Senior' )
{
    Write-Verbose "Doesn't have Senior title"
    $skipUser = $true
}

if( $user.HomeDrive -like '\\server\*' )
{
    Write-Verbose "Home drive already configured"
    $skipUser = $true
}

if ( -not $skipUser )
{
    # do something
}
```

<span data-ttu-id="15bcb-365">Je n’ai pas eu à inverser la logique pour que la logique de l’indicateur fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="15bcb-365">I did have to invert the logic to make the flag logic work correctly.</span></span> <span data-ttu-id="15bcb-366">Chaque évaluation représente une instruction `if` individuelle.</span><span class="sxs-lookup"><span data-stu-id="15bcb-366">Each evaluation is an individual `if` statement.</span></span> <span data-ttu-id="15bcb-367">L’avantage de cette approche est que lorsque vous effectuez un débogage, vous pouvez déterminer exactement ce que fait la logique.</span><span class="sxs-lookup"><span data-stu-id="15bcb-367">The advantage of this is that when you're debugging, you can tell exactly what the logic is doing.</span></span> <span data-ttu-id="15bcb-368">Parallèlement, j’ai pu ajouter des commentaires bien plus pertinents.</span><span class="sxs-lookup"><span data-stu-id="15bcb-368">I was able to add much better verbosity at the same time.</span></span>

<span data-ttu-id="15bcb-369">L’inconvénient, c’est qu’il faut évidemment écrire bien plus de code.</span><span class="sxs-lookup"><span data-stu-id="15bcb-369">The obvious downside is that it's so much more code to write.</span></span> <span data-ttu-id="15bcb-370">Le code est plus complexe à examiner lorsqu’il prend une seule ligne de logique et l’éclate en 25 lignes ou plus.</span><span class="sxs-lookup"><span data-stu-id="15bcb-370">The code is more complex to look at as it takes a single line of logic and explodes it into 25 or more lines.</span></span>

### <a name="using-functions"></a><span data-ttu-id="15bcb-371">Utilisation des fonctions</span><span class="sxs-lookup"><span data-stu-id="15bcb-371">Using functions</span></span>

<span data-ttu-id="15bcb-372">Nous pouvons également déplacer toute cette logique de validation dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="15bcb-372">We can also move all that validation logic into a function.</span></span> <span data-ttu-id="15bcb-373">Remarquez à quel point cette logique est simple.</span><span class="sxs-lookup"><span data-stu-id="15bcb-373">Look at how clean this looks at a glance.</span></span>

```powershell
if ( Test-SecureDriveConfiguration -ADUser $user )
{
    # do something
}
```

<span data-ttu-id="15bcb-374">Vous devrez toujours créer la fonction pour effectuer la validation, mais ce code est beaucoup plus facile à utiliser.</span><span class="sxs-lookup"><span data-stu-id="15bcb-374">You still have to create the function to do the validation, but it makes this code much easier to work with.</span></span> <span data-ttu-id="15bcb-375">Cela facilite le test de ce code.</span><span class="sxs-lookup"><span data-stu-id="15bcb-375">It makes this code easier to test.</span></span> <span data-ttu-id="15bcb-376">Dans vos tests, vous pouvez simuler l’appel à `Test-ADDriveConfiguration`, et deux tests suffisent pour cette fonction :</span><span class="sxs-lookup"><span data-stu-id="15bcb-376">In your tests, you can mock the call to `Test-ADDriveConfiguration` and you only need two tests for this function.</span></span> <span data-ttu-id="15bcb-377">un test qui retourne `$true` et un autre qui retourne `$false`.</span><span class="sxs-lookup"><span data-stu-id="15bcb-377">One where it returns `$true` and one where it returns `$false`.</span></span> <span data-ttu-id="15bcb-378">Le test de l’autre fonction est plus simple car le code est vraiment court.</span><span class="sxs-lookup"><span data-stu-id="15bcb-378">Testing the other function is simpler because it's so small.</span></span>

<span data-ttu-id="15bcb-379">Nous pouvons toujours commencer par le corps de cette fonction, avec une seule ligne, ou opter pour la logique éclatée que nous avons utilisée dans la dernière section.</span><span class="sxs-lookup"><span data-stu-id="15bcb-379">The body of that function could still be that one-liner we started with or the exploded logic that we used in the last section.</span></span> <span data-ttu-id="15bcb-380">Cela fonctionne bien dans les deux scénarios et vous pouvez ainsi modifier facilement cette implémentation ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="15bcb-380">This works well for both scenarios and allows you to easily change that implementation later.</span></span>

## <a name="error-handling"></a><span data-ttu-id="15bcb-381">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="15bcb-381">Error handling</span></span>

<span data-ttu-id="15bcb-382">Une utilisation importante de l’instruction `if` consiste à vérifier les conditions d’erreur avant de rencontrer des erreurs.</span><span class="sxs-lookup"><span data-stu-id="15bcb-382">One important use of the `if` statement is to check for error conditions before you run into errors.</span></span> <span data-ttu-id="15bcb-383">Un bon exemple consiste à vérifier si un dossier existe déjà avant d’essayer de le créer.</span><span class="sxs-lookup"><span data-stu-id="15bcb-383">A good example is to check if a folder already exists before you try to create it.</span></span>

```powershell
if ( -not (Test-Path -Path $folder) )
{
    New-Item -Type Directory -Path $folder
}
```

<span data-ttu-id="15bcb-384">Je tiens à souligner que si vous attendez une exception, il ne s’agit pas alors vraiment d’une exception.</span><span class="sxs-lookup"><span data-stu-id="15bcb-384">I like to say that if you expect an exception to happen, then it's not really an exception.</span></span> <span data-ttu-id="15bcb-385">Vérifiez vos valeurs et validez vos conditions lorsque vous le pouvez.</span><span class="sxs-lookup"><span data-stu-id="15bcb-385">So check your values and validate your conditions where you can.</span></span>

<span data-ttu-id="15bcb-386">Si vous souhaitez approfondir un peu plus la gestion des exceptions, j’ai préparé un article intitulé [Tout ce que vous avez toujours voulu savoir sur les exceptions][].</span><span class="sxs-lookup"><span data-stu-id="15bcb-386">If you want to dive a little more into actual exception handling, I have an article on [everything you ever wanted to know about exceptions][].</span></span>

## <a name="final-words"></a><span data-ttu-id="15bcb-387">Conclusion</span><span class="sxs-lookup"><span data-stu-id="15bcb-387">Final words</span></span>

<span data-ttu-id="15bcb-388">L’instruction `if` est une instruction simple, mais elle constitue un élément fondamental de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15bcb-388">The `if` statement is such a simple statement but is a fundamental piece of PowerShell.</span></span> <span data-ttu-id="15bcb-389">Vous vous en servirez plusieurs fois dans presque tous les scripts que vous écrirez.</span><span class="sxs-lookup"><span data-stu-id="15bcb-389">You will find yourself using this multiple times in almost every script you write.</span></span> <span data-ttu-id="15bcb-390">J’espère que vous avez désormais une meilleure compréhension de ces concepts.</span><span class="sxs-lookup"><span data-stu-id="15bcb-390">I hope you have a better understanding than you had before.</span></span>

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2019-08-11-PowerShell-if-then-else-equals-operator/
[original version]: https://powershellexplained.com/2019-08-11-PowerShell-if-then-else-equals-operator/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[if]: /powershell/module/microsoft.powershell.core/about/about_if
[opérateurs de bits]: https://powershellexplained.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[bitwise operators]: https://powershellexplained.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[les nombreuses façons d’utiliser regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[the many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[tout ce que vous avez toujours voulu savoir sur les exceptions]: everything-about-exceptions.md
[everything you ever wanted to know about exceptions]: everything-about-exceptions.md
[Tout ce que vous avez toujours voulu savoir sur $null]: everything-about-null.md
[everything you wanted to know about $null]: everything-about-null.md
[Prasoon Karunan V]: https://twitter.com/prasoonkarunan
[Tout ce que vous avez toujours voulu savoir sur l’instruction switch]: everything-about-switch.md
[everything you ever wanted to know about the switch statement]: everything-about-switch.md
[Invoke-SnowSql]: https://github.com/loanDepot/SnowSQL/blob/a3731b52e4ab4ecb503fb81e2d8cb131e8f90410/SnowSQL/public/Invoke-SnowSql.ps1#L90
