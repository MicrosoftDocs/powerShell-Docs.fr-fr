---
title: Contrôle de flux
description: PowerShell fournit des méthodes pour créer des boucles, prendre des décisions et contrôler logiquement le flux du code dans les scripts.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 4f0d7b7f5f3c12bb9475af5aed42b2d32cfbc14d
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84437990"
---
# <a name="chapter-6---flow-control"></a><span data-ttu-id="6f482-103">Chapitre 6 : Contrôle de flux</span><span class="sxs-lookup"><span data-stu-id="6f482-103">Chapter 6 - Flow control</span></span>

## <a name="scripting"></a><span data-ttu-id="6f482-104">Création de scripts</span><span class="sxs-lookup"><span data-stu-id="6f482-104">Scripting</span></span>

<span data-ttu-id="6f482-105">Passer des one-liners PowerShell aux scripts est bien plus simple que ça n’en a l’air.</span><span class="sxs-lookup"><span data-stu-id="6f482-105">When you move from writing PowerShell one-liners to writing scripts, it sounds a lot more complicated than it really is.</span></span> <span data-ttu-id="6f482-106">Un script n’est rien de plus qu’un ensemble de commandes identiques ou similaires que vous exécutez de manière interactive dans la console PowerShell, sauf que ces commandes sont enregistrées dans un fichier `.PS1`.</span><span class="sxs-lookup"><span data-stu-id="6f482-106">A script is nothing more than the same or similar commands that you would run interactively in the PowerShell console, except they're saved as a `.PS1` file.</span></span> <span data-ttu-id="6f482-107">Vous pouvez utiliser certaines constructions de script, comme une boucle `foreach`, au lieu de l’applet de commande `ForEach-Object`.</span><span class="sxs-lookup"><span data-stu-id="6f482-107">There are some scripting constructs that you may use such as a `foreach` loop instead of the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="6f482-108">Pour les débutants, les différences peuvent porter à confusion, en particulier quand `foreach` est à la fois une construction de script et un alias de l’applet de commande `ForEach-Object`.</span><span class="sxs-lookup"><span data-stu-id="6f482-108">To beginners, the differences can be confusing especially when you consider that `foreach` is both a scripting construct and an alias for the `ForEach-Object` cmdlet.</span></span>

## <a name="looping"></a><span data-ttu-id="6f482-109">Bouclage</span><span class="sxs-lookup"><span data-stu-id="6f482-109">Looping</span></span>

<span data-ttu-id="6f482-110">L’un des avantages de PowerShell est que, une fois que vous avez trouvé comment faire pour un élément, il vous suffit presque de répéter la même chose pour des centaines d’autres.</span><span class="sxs-lookup"><span data-stu-id="6f482-110">One of the great things about PowerShell is, once you figure out how to do something for one item, it's almost as easy to do the same task for hundreds of items.</span></span> <span data-ttu-id="6f482-111">Vous n’avez qu’à exécuter un des nombreux types de boucle PowerShell sur les éléments.</span><span class="sxs-lookup"><span data-stu-id="6f482-111">Simply loop through the items using one of the many different types of loops in PowerShell.</span></span>

### <a name="foreach-object"></a><span data-ttu-id="6f482-112">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="6f482-112">ForEach-Object</span></span>

<span data-ttu-id="6f482-113">`ForEach-Object` est une applet de commande pour effectuer des itérations au sein d’éléments dans un pipeline, par exemple avec les one-liners PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6f482-113">`ForEach-Object` is a cmdlet for iterating through items in a pipeline such as with PowerShell one-liners.</span></span> <span data-ttu-id="6f482-114">`ForEach-Object` envoie en streaming les objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="6f482-114">`ForEach-Object` streams the objects through the pipeline.</span></span>

<span data-ttu-id="6f482-115">Bien que le paramètre **Module** de `Get-Command` accepte plusieurs valeurs sous forme de chaînes, il les accepte uniquement via une entrée de pipeline par nom de propriété ou via une entrée de paramètre.</span><span class="sxs-lookup"><span data-stu-id="6f482-115">Although the **Module** parameter of `Get-Command` accepts multiple values that are strings, it only accepts them via pipeline input by property name or via parameter input.</span></span> <span data-ttu-id="6f482-116">Dans le scénario suivant, si je veux envoyer deux chaînes par valeur vers `Get-Command` pour les utiliser avec le paramètre **Module**, je dois utiliser l’applet de commande `ForEach-Object`.</span><span class="sxs-lookup"><span data-stu-id="6f482-116">In the following scenario, if I want to pipe two strings by value to `Get-Command` for use with the **Module** parameter, I would need to use the `ForEach-Object` cmdlet.</span></span>

```powershell
'ActiveDirectory', 'SQLServer' |
   ForEach-Object {Get-Command -Module $_} |
     Group-Object -Property ModuleName -NoElement |
         Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  147 ActiveDirectory
   82 SqlServer
```

<span data-ttu-id="6f482-117">Dans l’exemple précédent, `$_` est l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="6f482-117">In the previous example, `$_` is the current object.</span></span> <span data-ttu-id="6f482-118">À partir de la version 3.0 de PowerShell, `$PSItem` peut être utilisé à la place de `$_`.</span><span class="sxs-lookup"><span data-stu-id="6f482-118">Beginning with PowerShell version 3.0, `$PSItem` can be used instead of `$_`.</span></span> <span data-ttu-id="6f482-119">Mais je trouve que la plupart des utilisateurs expérimentés de PowerShell préfèrent encore utiliser `$_`, car il a une compatibilité descendante et est plus court à taper.</span><span class="sxs-lookup"><span data-stu-id="6f482-119">But I find that most experienced PowerShell users still prefer using `$_` since it's backward compatible and less to type.</span></span>

<span data-ttu-id="6f482-120">Quand vous utilisez le mot clé `foreach`, vous devez stocker tous les éléments en mémoire pour pouvoir lancer l’itération, ce qui peut être difficile si vous ne savez combien d’éléments vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="6f482-120">When using the `foreach` keyword, you must store all of the items in memory before iterating through them, which could be difficult if you don't know how many items you're working with.</span></span>

```powershell
$ComputerName = 'DC01', 'WEB01'
foreach ($Computer in $ComputerName) {
  Get-ADComputer -Identity $Computer
}
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

<span data-ttu-id="6f482-121">La plupart du temps, une boucle comme `foreach` ou `ForEach-Object` est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6f482-121">Many times a loop such as `foreach` or `ForEach-Object` is necessary.</span></span> <span data-ttu-id="6f482-122">Sinon, vous recevez un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6f482-122">Otherwise you'll receive an error message.</span></span>

```powershell
Get-ADComputer -Identity 'DC01', 'WEB01'
```

```Output
Get-ADComputer : Cannot convert 'System.Object[]' to the type
'Microsoft.ActiveDirectory.Management.ADComputer' required by parameter 'Identity'.
Specified method is not supported.
At line:1 char:26
+ Get-ADComputer -Identity 'DC01', 'WEB01'
+                          ```````````````
    + CategoryInfo          : InvalidArgument: (:) [Get-ADComputer], ParameterBindingExc
   eption
    + FullyQualifiedErrorId : CannotConvertArgument,Microsoft.ActiveDirectory.Management
   .Commands.GetADComputer
```

<span data-ttu-id="6f482-123">Dans d’autres cas, vous pouvez obtenir les mêmes résultats tout en éliminant complètement la boucle.</span><span class="sxs-lookup"><span data-stu-id="6f482-123">Other times, you can get the same results while eliminating the loop altogether.</span></span> <span data-ttu-id="6f482-124">Consultez l’applet de commande pour comprendre vos options.</span><span class="sxs-lookup"><span data-stu-id="6f482-124">Consult the cmdlet help to understand your options.</span></span>

```powershell
'DC01', 'WEB01' | Get-ADComputer
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

<span data-ttu-id="6f482-125">Comme vous pouvez le voir dans les exemples précédents, le paramètre **Identity** pour `Get-ADComputer` accepte seulement une valeur quand elle est fournie par le biais d’une entrée de paramètre, mais il autorise plusieurs éléments quand l’entrée est fournie via une entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="6f482-125">As you can see in the previous examples, the **Identity** parameter for `Get-ADComputer` only accepts a single value when provided via parameter input, but it allows for multiple items when the input is provided via pipeline input.</span></span>

### <a name="for"></a><span data-ttu-id="6f482-126">For</span><span class="sxs-lookup"><span data-stu-id="6f482-126">For</span></span>

<span data-ttu-id="6f482-127">Une boucle `for` effectue une itération quand une condition spécifiée a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="6f482-127">A `for` loop iterates while a specified condition is true.</span></span> <span data-ttu-id="6f482-128">Je n’utilise pas souvent la boucle `for`, mais elle a son utilité.</span><span class="sxs-lookup"><span data-stu-id="6f482-128">The `for` loop is not something that I use often, but it does have its uses.</span></span>

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
}
```

```Output
Sleeping for 1 seconds
Sleeping for 2 seconds
Sleeping for 3 seconds
Sleeping for 4 seconds
```

<span data-ttu-id="6f482-129">Dans l’exemple précédent, la boucle effectue 4 itérations en commençant par le numéro 1 et continue tant que la variable de compteur `$i` est inférieure à 5.</span><span class="sxs-lookup"><span data-stu-id="6f482-129">In the previous example, the loop will iterate four times by starting off with the number one and continue as long as the counter variable `$i` is less than 5.</span></span> <span data-ttu-id="6f482-130">Elle se met en veille pendant un total de 10 secondes.</span><span class="sxs-lookup"><span data-stu-id="6f482-130">It will sleep for a total of 10 seconds.</span></span>

### <a name="do"></a><span data-ttu-id="6f482-131">À faire</span><span class="sxs-lookup"><span data-stu-id="6f482-131">Do</span></span>

<span data-ttu-id="6f482-132">Il existe deux boucles `do` différentes dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6f482-132">There are two different `do` loops in PowerShell.</span></span> <span data-ttu-id="6f482-133">`Do Until` s’exécute quand la condition spécifiée a la valeur false.</span><span class="sxs-lookup"><span data-stu-id="6f482-133">`Do Until` runs while the specified condition is false.</span></span>

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  }
  elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
until ($guess -eq $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
```

<span data-ttu-id="6f482-134">L’exemple précédent est un jeu de nombres qui continue jusqu’à ce que la valeur que vous devinez soit égale au nombre généré par l’applet de commande `Get-Random`.</span><span class="sxs-lookup"><span data-stu-id="6f482-134">The previous example is a numbers game that continues until the value you guess equals the same number that the `Get-Random` cmdlet generated.</span></span>

<span data-ttu-id="6f482-135">`Do While` est juste l’inverse.</span><span class="sxs-lookup"><span data-stu-id="6f482-135">`Do While` is just the opposite.</span></span> <span data-ttu-id="6f482-136">Elle s’exécute tant que la condition spécifiée a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="6f482-136">It runs as long as the specified condition evaluates to true.</span></span>

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  } elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
while ($guess -ne $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
Too low!
What's your guess?: 4
```

<span data-ttu-id="6f482-137">Les mêmes résultats sont obtenus avec une boucle `Do While` en inversant la condition de test (différent de).</span><span class="sxs-lookup"><span data-stu-id="6f482-137">The same results are achieved with a `Do While` loop by reversing the test condition to not equals.</span></span>

<span data-ttu-id="6f482-138">Les boucles `Do` s’exécutent toujours au moins une fois, car la condition est évaluée à la fin de la boucle.</span><span class="sxs-lookup"><span data-stu-id="6f482-138">`Do` loops always run at least once because the condition is evaluated at the end of the loop.</span></span>

### <a name="while"></a><span data-ttu-id="6f482-139">While</span><span class="sxs-lookup"><span data-stu-id="6f482-139">While</span></span>

<span data-ttu-id="6f482-140">Tout comme la boucle `Do While`, une boucle `While` s’exécute tant que la condition spécifiée a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="6f482-140">Similar to the `Do While` loop, a `While` loop runs as long as the specified condition is true.</span></span> <span data-ttu-id="6f482-141">À la différence que la boucle `While` évalue la condition en haut de la boucle avant l’exécution du code.</span><span class="sxs-lookup"><span data-stu-id="6f482-141">The difference however, is that a `While` loop evaluates the condition at the top of the loop before any code is run.</span></span> <span data-ttu-id="6f482-142">Elle ne s’exécute donc pas si la condition a la valeur false.</span><span class="sxs-lookup"><span data-stu-id="6f482-142">So it doesn't run if the condition evaluates to false.</span></span>

```powershell
$date = Get-Date -Date 'November 22'
while ($date.DayOfWeek -ne 'Thursday') {
  $date = $date.AddDays(1)
}
Write-Output $date
```

```Output
Thursday, November 23, 2017 12:00:00 AM
```

<span data-ttu-id="6f482-143">L’exemple précédent calcule le jour auquel Thanksgiving a lieu aux États-Unis.</span><span class="sxs-lookup"><span data-stu-id="6f482-143">The previous example calculates what day Thanksgiving Day is on in the United States.</span></span> <span data-ttu-id="6f482-144">C’est toujours le quatrième jeudi de novembre.</span><span class="sxs-lookup"><span data-stu-id="6f482-144">It's always on the fourth Thursday of November.</span></span> <span data-ttu-id="6f482-145">Par conséquent, la boucle commence par le 22 novembre et ajoute un jour quand le jour de la semaine n’est pas égal à jeudi.</span><span class="sxs-lookup"><span data-stu-id="6f482-145">So the loop starts with the 22nd day of November and adds a day while the day of the week isn't equal to Thursday.</span></span> <span data-ttu-id="6f482-146">Si le 22 est un jeudi, la boucle ne s’exécute pas du tout.</span><span class="sxs-lookup"><span data-stu-id="6f482-146">If the 22nd is a Thursday, the loop doesn't run at all.</span></span>

## <a name="break-continue-and-return"></a><span data-ttu-id="6f482-147">Break, Continue et Return</span><span class="sxs-lookup"><span data-stu-id="6f482-147">Break, Continue, and Return</span></span>

<span data-ttu-id="6f482-148">L’instruction `Break` permet de casser une boucle.</span><span class="sxs-lookup"><span data-stu-id="6f482-148">`Break` is designed to break out of a loop.</span></span> <span data-ttu-id="6f482-149">Elle est également couramment utilisée avec l’instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="6f482-149">It's also commonly used with the `switch` statement.</span></span>

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
  break
}
```

```Output
Sleeping for 1 seconds
```

<span data-ttu-id="6f482-150">L’instruction `break` présentée dans l’exemple précédent casse la boucle à la première itération.</span><span class="sxs-lookup"><span data-stu-id="6f482-150">The `break` statement shown in the previous example causes the loop to exit on the first iteration.</span></span>

<span data-ttu-id="6f482-151">L’instruction Continue permet de passer à l’itération suivante d’une boucle.</span><span class="sxs-lookup"><span data-stu-id="6f482-151">Continue is designed to skip to the next iteration of a loop.</span></span>

```powershell
while ($i -lt 5) {
  $i += 1
  if ($i -eq 3) {
    continue
  }
  Write-Output $i
}
```

```Output
1
2
4
5
```

<span data-ttu-id="6f482-152">L’exemple précédent génère les nombres 1, 2, 4 et 5.</span><span class="sxs-lookup"><span data-stu-id="6f482-152">The previous example will output the numbers 1, 2, 4, and 5.</span></span> <span data-ttu-id="6f482-153">Il ignore le numéro 3 et continue avec l’itération suivante de la boucle.</span><span class="sxs-lookup"><span data-stu-id="6f482-153">It skips number 3 and continues with the next iteration of the loop.</span></span> <span data-ttu-id="6f482-154">Tout comme `break`, `continue` interrompt la boucle, sauf pour l’itération actuelle.</span><span class="sxs-lookup"><span data-stu-id="6f482-154">Similar to `break`, `continue` breaks out of the loop except only for the current iteration.</span></span> <span data-ttu-id="6f482-155">L’exécution se poursuit avec l’itération suivante au lieu de casser la boucle et de s’arrêter.</span><span class="sxs-lookup"><span data-stu-id="6f482-155">Execution continues with the next iteration instead of breaking out of the loop and stopping.</span></span>

<span data-ttu-id="6f482-156">L’instruction Return permet de quitter l’étendue existante.</span><span class="sxs-lookup"><span data-stu-id="6f482-156">Return is designed to exit out of the existing scope.</span></span>

```powershell
$number = 1..10
foreach ($n in $number) {
  if ($n -ge 4) {
    Return $n
  }
}
```

```Output
4
```

<span data-ttu-id="6f482-157">Notez que dans l’exemple précédent, return génère le premier résultat et n’existe plus dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="6f482-157">Notice that in the previous example, return outputs the first result and then exists out of the loop.</span></span> <span data-ttu-id="6f482-158">Une explication plus complète de l’instruction return est disponible dans l’un de mes articles de blog : [« The PowerShell return keyword »][].</span><span class="sxs-lookup"><span data-stu-id="6f482-158">A more thorough explanation of the result statement can be found in one of my blog articles: ["The PowerShell return keyword"][].</span></span>

## <a name="summary"></a><span data-ttu-id="6f482-159">Résumé</span><span class="sxs-lookup"><span data-stu-id="6f482-159">Summary</span></span>

<span data-ttu-id="6f482-160">Dans ce chapitre, vous avez découvert les différents types de boucles qui existent dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6f482-160">In this chapter, you've learned about the different types of loops that exist in PowerShell.</span></span>

## <a name="review"></a><span data-ttu-id="6f482-161">Révision</span><span class="sxs-lookup"><span data-stu-id="6f482-161">Review</span></span>

1. <span data-ttu-id="6f482-162">Quelle est la différence entre l’applet de commande `ForEach-Object` et la construction de script ForEach ?</span><span class="sxs-lookup"><span data-stu-id="6f482-162">What is the difference in the `ForEach-Object` cmdlet and the foreach scripting construct?</span></span>
1. <span data-ttu-id="6f482-163">Quel est le principal avantage d’une boucle While par rapport à une boucle Do While ou Do Until ?</span><span class="sxs-lookup"><span data-stu-id="6f482-163">What is the primary advantage of using a While loop instead of a Do While or Do Until loop.</span></span>
1. <span data-ttu-id="6f482-164">En quoi les instructions break et continue sont-elles différentes ?</span><span class="sxs-lookup"><span data-stu-id="6f482-164">How do the break and continue statements differ?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="6f482-165">Lecture recommandée</span><span class="sxs-lookup"><span data-stu-id="6f482-165">Recommended Reading</span></span>

- <span data-ttu-id="6f482-166">[ForEach-Object][]</span><span class="sxs-lookup"><span data-stu-id="6f482-166">[ForEach-Object][]</span></span>
- <span data-ttu-id="6f482-167">[about_ForEach][]</span><span class="sxs-lookup"><span data-stu-id="6f482-167">[about_ForEach][]</span></span>
- <span data-ttu-id="6f482-168">[about_For][]</span><span class="sxs-lookup"><span data-stu-id="6f482-168">[about_For][]</span></span>
- <span data-ttu-id="6f482-169">[about_Do][]</span><span class="sxs-lookup"><span data-stu-id="6f482-169">[about_Do][]</span></span>
- <span data-ttu-id="6f482-170">[about_While][]</span><span class="sxs-lookup"><span data-stu-id="6f482-170">[about_While][]</span></span>
- <span data-ttu-id="6f482-171">[about_Break][]</span><span class="sxs-lookup"><span data-stu-id="6f482-171">[about_Break][]</span></span>
- <span data-ttu-id="6f482-172">[about_Continue][]</span><span class="sxs-lookup"><span data-stu-id="6f482-172">[about_Continue][]</span></span>
- <span data-ttu-id="6f482-173">[about_Return][]</span><span class="sxs-lookup"><span data-stu-id="6f482-173">[about_Return][]</span></span>

<!-- link references -->
[ForEach-Object]: /powershell/module/microsoft.powershell.core/foreach-object
[about_ForEach]: /powershell/module/microsoft.powershell.core/about/about_foreach
[about_For]: /powershell/module/microsoft.powershell.core/about/about_for
[about_Do]: /powershell/module/microsoft.powershell.core/about/about_do
[about_While]: /powershell/module/microsoft.powershell.core/about/about_while
[about_Break]: /powershell/module/microsoft.powershell.core/about/about_break
[about_Continue]: /powershell/module/microsoft.powershell.core/about/about_continue
[about_Return]: /powershell/module/microsoft.powershell.core/about/about_return
[« The PowerShell return keyword »]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
["The PowerShell return keyword"]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
