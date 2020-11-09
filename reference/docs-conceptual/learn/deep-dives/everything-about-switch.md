---
title: Tout ce que vous avez toujours voulu savoir sur l’instruction switch
description: L’instruction switch dans PowerShell offre des fonctionnalités qui n’existent pas dans d’autres langages.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: c2e77aa5fb36d04fec1bc86f751291205120c729
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355117"
---
# <a name="everything-you-ever-wanted-to-know-about-the-switch-statement"></a><span data-ttu-id="891cf-103">Tout ce que vous avez toujours voulu savoir sur l’instruction switch</span><span class="sxs-lookup"><span data-stu-id="891cf-103">Everything you ever wanted to know about the switch statement</span></span>

<span data-ttu-id="891cf-104">À l’instar de nombreux autres langages, PowerShell a des commandes pour contrôler le flux d’exécution dans vos scripts.</span><span class="sxs-lookup"><span data-stu-id="891cf-104">Like many other languages, PowerShell has commands for controlling the flow of execution within your scripts.</span></span> <span data-ttu-id="891cf-105">[switch][] est une de ces instructions et, dans PowerShell, elle offre des fonctionnalités qui n’existent pas dans d’autres langages.</span><span class="sxs-lookup"><span data-stu-id="891cf-105">One of those statements is the [switch][] statement and in PowerShell, it offers features that aren't found in other languages.</span></span> <span data-ttu-id="891cf-106">Aujourd’hui, nous nous intéressons à l’utilisation de l’instruction `switch` de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="891cf-106">Today, we take a deep dive into working with the PowerShell `switch`.</span></span>

> [!NOTE]
> <span data-ttu-id="891cf-107">La [Version d’origine][] de cet article est parue sur le blog écrit par [@KevinMarquette][].</span><span class="sxs-lookup"><span data-stu-id="891cf-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="891cf-108">L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu avec nous.</span><span class="sxs-lookup"><span data-stu-id="891cf-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="891cf-109">Consultez son blog sur [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="891cf-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="the-if-statement"></a><span data-ttu-id="891cf-110">Instruction `if`</span><span class="sxs-lookup"><span data-stu-id="891cf-110">The `if` statement</span></span>

<span data-ttu-id="891cf-111">Une des premières instructions que vous apprenez est l’instruction `if`.</span><span class="sxs-lookup"><span data-stu-id="891cf-111">One of the first statements that you learn is the `if` statement.</span></span> <span data-ttu-id="891cf-112">Elle vous permet d’exécuter un bloc de script si une affirmation est `$true`.</span><span class="sxs-lookup"><span data-stu-id="891cf-112">It lets you execute a script block if a statement is `$true`.</span></span>

``` powershell
if ( Test-Path $Path )
{
    Remove-Item $Path
}
```

<span data-ttu-id="891cf-113">Vous pouvez avoir une logique bien plus compliquée en utilisant les instructions `elseif` et `else`.</span><span class="sxs-lookup"><span data-stu-id="891cf-113">You can have much more complicated logic by using `elseif` and `else` statements.</span></span> <span data-ttu-id="891cf-114">Voici un exemple où j’ai une valeur numérique pour le jour de la semaine et où je veux obtenir le nom sous la forme d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="891cf-114">Here is an example where I have a numeric value for day of the week and I want to get the name as a string.</span></span>

``` powershell
$day = 3

if ( $day -eq 0 ) { $result = 'Sunday'        }
elseif ( $day -eq 1 ) { $result = 'Monday'    }
elseif ( $day -eq 2 ) { $result = 'Tuesday'   }
elseif ( $day -eq 3 ) { $result = 'Wednesday' }
elseif ( $day -eq 4 ) { $result = 'Thursday'  }
elseif ( $day -eq 5 ) { $result = 'Friday'    }
elseif ( $day -eq 6 ) { $result = 'Saturday'  }

$result
```

```Output
Wednesday
```

<span data-ttu-id="891cf-115">Il s’avère qu’il s’agit d’un cas de figure courant et qu’il existe de nombreuses façons de le traiter.</span><span class="sxs-lookup"><span data-stu-id="891cf-115">It turns out that this is a common pattern and there are many ways to deal with this.</span></span> <span data-ttu-id="891cf-116">Une de ces façons est via une instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="891cf-116">One of them is with a `switch`.</span></span>

## <a name="switch-statement"></a><span data-ttu-id="891cf-117">Instruction switch</span><span class="sxs-lookup"><span data-stu-id="891cf-117">Switch statement</span></span>

<span data-ttu-id="891cf-118">L’instruction `switch` vous permet de fournir une variable et une liste de valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="891cf-118">The `switch` statement allows you to provide a variable and a list of possible values.</span></span> <span data-ttu-id="891cf-119">Si la valeur correspond à la variable, son scriptblock est exécuté.</span><span class="sxs-lookup"><span data-stu-id="891cf-119">If the value matches the variable, then its scriptblock is executed.</span></span>

``` powershell
$day = 3

switch ( $day )
{
    0 { $result = 'Sunday'    }
    1 { $result = 'Monday'    }
    2 { $result = 'Tuesday'   }
    3 { $result = 'Wednesday' }
    4 { $result = 'Thursday'  }
    5 { $result = 'Friday'    }
    6 { $result = 'Saturday'  }
}

$result
```

```Output
'Wednesday'
```

<span data-ttu-id="891cf-120">Pour cet exemple, la valeur de `$day` correspond à une des valeurs numériques ; le nom correct est alors affecté à `$result`.</span><span class="sxs-lookup"><span data-stu-id="891cf-120">For this example, the value of `$day` matches one of the numeric values, then the correct name is assigned to `$result`.</span></span> <span data-ttu-id="891cf-121">Nous n’effectuons qu’une affectation de variable dans cet exemple, mais vous pouvez exécuter n’importe quelle instruction PowerShell dans ces blocs de script.</span><span class="sxs-lookup"><span data-stu-id="891cf-121">We are only doing a variable assignment in this example, but any PowerShell can be executed in those script blocks.</span></span>

### <a name="assign-to-a-variable"></a><span data-ttu-id="891cf-122">Affecter à une variable</span><span class="sxs-lookup"><span data-stu-id="891cf-122">Assign to a variable</span></span>

<span data-ttu-id="891cf-123">Nous pouvons écrire ce dernier exemple d’une autre façon.</span><span class="sxs-lookup"><span data-stu-id="891cf-123">We can write that last example in another way.</span></span>

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday'    }
    1 { 'Monday'    }
    2 { 'Tuesday'   }
    3 { 'Wednesday' }
    4 { 'Thursday'  }
    5 { 'Friday'    }
    6 { 'Saturday'  }
}
```

<span data-ttu-id="891cf-124">Nous plaçons la valeur sur le pipeline PowerShell et nous l’affectons à `$result`.</span><span class="sxs-lookup"><span data-stu-id="891cf-124">We are placing the value on the PowerShell pipeline and assigning it to the `$result`.</span></span> <span data-ttu-id="891cf-125">Vous pouvez effectuer la même chose avec les instructions `if` et `foreach`.</span><span class="sxs-lookup"><span data-stu-id="891cf-125">You can do this same thing with the `if` and `foreach` statements.</span></span>

### <a name="default"></a><span data-ttu-id="891cf-126">Default</span><span class="sxs-lookup"><span data-stu-id="891cf-126">Default</span></span>

<span data-ttu-id="891cf-127">Nous pouvons utiliser le mot clé `default` pour identifier ce qui doit se produire s’il n’y a pas de correspondance.</span><span class="sxs-lookup"><span data-stu-id="891cf-127">We can use the `default` keyword to identify the what should happen if there is no match.</span></span>

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday' }
    # ...
    6 { 'Saturday' }
    default { 'Unknown' }
}
```

<span data-ttu-id="891cf-128">Ici, nous retournons la valeur `Unknown` dans le cas « default ».</span><span class="sxs-lookup"><span data-stu-id="891cf-128">Here we return the value `Unknown` in the default case.</span></span>

### <a name="strings"></a><span data-ttu-id="891cf-129">Chaînes</span><span class="sxs-lookup"><span data-stu-id="891cf-129">Strings</span></span>

<span data-ttu-id="891cf-130">Dans ces derniers exemples, j’ai mis en correspondance des nombres, mais vous pouvez également faire correspondre des chaînes.</span><span class="sxs-lookup"><span data-stu-id="891cf-130">I was matching numbers in those last examples, but you can also match strings.</span></span>

``` powershell
$item = 'Role'

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

<span data-ttu-id="891cf-131">J’ai décidé de ne pas placer ici de guillemets autour des correspondances de `Component`,`Role` et `Location`, pour mettre en évidence le fait qu’ils sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="891cf-131">I decided not to wrap the `Component`,`Role` and `Location` matches in quotes here to highlight that they're optional.</span></span> <span data-ttu-id="891cf-132">`switch` les traite comme une chaîne dans la plupart des cas.</span><span class="sxs-lookup"><span data-stu-id="891cf-132">The `switch` treats those as a string in most cases.</span></span>

## <a name="arrays"></a><span data-ttu-id="891cf-133">Tableaux</span><span class="sxs-lookup"><span data-stu-id="891cf-133">Arrays</span></span>

<span data-ttu-id="891cf-134">Une des fonctionnalités intéressantes de l'instruction `switch` de PowerShell est la façon dont elle traite les tableaux.</span><span class="sxs-lookup"><span data-stu-id="891cf-134">One of the cool features of the PowerShell `switch` is the way it handles arrays.</span></span> <span data-ttu-id="891cf-135">Si vous donnez un tableau à `switch`, elle traite chaque élément de cette collection.</span><span class="sxs-lookup"><span data-stu-id="891cf-135">If you give a `switch` an array, it processes each element in that collection.</span></span>

``` powershell
$roles = @('WEB','Database')

switch ( $roles ) {
    'Database'   { 'Configure SQL' }
    'WEB'        { 'Configure IIS' }
    'FileServer' { 'Configure Share' }
}
```

```Output
Configure IIS
Configure SQL
```

<span data-ttu-id="891cf-136">Si vous avez des éléments qui se répètent dans votre tableau, ils sont mis en correspondance plusieurs fois par la section appropriée.</span><span class="sxs-lookup"><span data-stu-id="891cf-136">If you have repeated items in your array, then they're matched multiple times by the appropriate section.</span></span>

### <a name="psitem"></a><span data-ttu-id="891cf-137">PSItem</span><span class="sxs-lookup"><span data-stu-id="891cf-137">PSItem</span></span>

<span data-ttu-id="891cf-138">Vous pouvez utiliser `$PSItem` ou `$_` pour référencer l’élément actif qui a été traité.</span><span class="sxs-lookup"><span data-stu-id="891cf-138">You can use the `$PSItem` or `$_` to reference the current item that was processed.</span></span> <span data-ttu-id="891cf-139">Quand nous faisons une correspondance simple, `$PSItem` est la valeur que nous mettons en correspondance.</span><span class="sxs-lookup"><span data-stu-id="891cf-139">When we do a simple match, `$PSItem` is the value that we are matching.</span></span> <span data-ttu-id="891cf-140">Je ferai des correspondances avancées dans la section suivante où cette variable est utilisée.</span><span class="sxs-lookup"><span data-stu-id="891cf-140">I'll be performing some advanced matches in the next section where this variable is used.</span></span>

## <a name="parameters"></a><span data-ttu-id="891cf-141">Paramètres</span><span class="sxs-lookup"><span data-stu-id="891cf-141">Parameters</span></span>

<span data-ttu-id="891cf-142">Une fonctionnalité unique de l'instruction `switch` de PowerShell est qu’elle a plusieurs [paramètres de commutateur][] qui modifient son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="891cf-142">A unique feature of the PowerShell `switch` is that it has a number of [switch parameters][] that change how it performs.</span></span>

### <a name="-casesensitive"></a><span data-ttu-id="891cf-143">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="891cf-143">-CaseSensitive</span></span>

<span data-ttu-id="891cf-144">Par défaut, les correspondances ne sont pas sensibles à la casse.</span><span class="sxs-lookup"><span data-stu-id="891cf-144">The matches aren't case-sensitive by default.</span></span> <span data-ttu-id="891cf-145">Si vous devez respecter la casse, vous pouvez utiliser `-CaseSensitive`.</span><span class="sxs-lookup"><span data-stu-id="891cf-145">If you need to be case-sensitive, you can use `-CaseSensitive`.</span></span> <span data-ttu-id="891cf-146">Ceci peut être utilisé en combinaison avec les autres paramètres de commutateur.</span><span class="sxs-lookup"><span data-stu-id="891cf-146">This can be used in combination with the other switch parameters.</span></span>

### <a name="-wildcard"></a><span data-ttu-id="891cf-147">-Wildcard</span><span class="sxs-lookup"><span data-stu-id="891cf-147">-Wildcard</span></span>

<span data-ttu-id="891cf-148">Nous pouvons activer la prise en charge des caractères génériques avec le commutateur `-wildcard`.</span><span class="sxs-lookup"><span data-stu-id="891cf-148">We can enable wildcard support with the `-wildcard` switch.</span></span> <span data-ttu-id="891cf-149">Ceci utilise la même logique de caractères génériques que l’opérateur `-like` pour établir chaque correspondance.</span><span class="sxs-lookup"><span data-stu-id="891cf-149">This uses the same wildcard logic as the `-like` operator to do each match.</span></span>

``` powershell
$Message = 'Warning, out of disk space'

switch -Wildcard ( $message )
{
    'Error*'
    {
        Write-Error -Message $Message
    }
    'Warning*'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

```Output
WARNING: Warning, out of disk space
```

<span data-ttu-id="891cf-150">Ici, nous traitons un message, puis nous le plaçons sur des flux différents en fonction du contenu.</span><span class="sxs-lookup"><span data-stu-id="891cf-150">Here we are processing a message and then outputting it on different streams based on the contents.</span></span>

### <a name="-regex"></a><span data-ttu-id="891cf-151">-Regex</span><span class="sxs-lookup"><span data-stu-id="891cf-151">-Regex</span></span>

<span data-ttu-id="891cf-152">L’instruction switch prend en charge les correspondances d’expressions régulières exactement comme les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="891cf-152">The switch statement supports regex matches just like it does wildcards.</span></span>

``` powershell
switch -Regex ( $message )
{
    '^Error'
    {
        Write-Error -Message $Message
    }
    '^Warning'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

<span data-ttu-id="891cf-153">Il y a plus d’exemples d’utilisation d’expressions régulières dans un autre article que j’ai écrit : [Les nombreuses façons d’utiliser les expressions régulières][].</span><span class="sxs-lookup"><span data-stu-id="891cf-153">I have more examples of using regex in another article I wrote: [The many ways to use regex][].</span></span>

### <a name="-file"></a><span data-ttu-id="891cf-154">-File</span><span class="sxs-lookup"><span data-stu-id="891cf-154">-File</span></span>

<span data-ttu-id="891cf-155">Une fonctionnalité peu connue de l’instruction switch est qu’elle peut traiter un fichier avec le paramètre `-File`.</span><span class="sxs-lookup"><span data-stu-id="891cf-155">A little known feature of the switch statement is that it can process a file with the `-File` parameter.</span></span> <span data-ttu-id="891cf-156">Vous utilisez `-file` avec un chemin vers un fichier au lieu de lui donner une expression de variable.</span><span class="sxs-lookup"><span data-stu-id="891cf-156">You use `-file` with a path to a file instead of giving it a variable expression.</span></span>

``` powershell
switch -Wildcard -File $path
{
    'Error*'
    {
        Write-Error -Message $PSItem
    }
    'Warning*'
    {
        Write-Warning -Message $PSItem
    }
    default
    {
        Write-Output $PSItem
    }
}
```

<span data-ttu-id="891cf-157">Elle fonctionne de la même façon qu’elle traite un tableau.</span><span class="sxs-lookup"><span data-stu-id="891cf-157">It works just like processing an array.</span></span> <span data-ttu-id="891cf-158">Dans cet exemple, je la combine avec la correspondance de caractères génériques et j’utilise `$PSItem`.</span><span class="sxs-lookup"><span data-stu-id="891cf-158">In this example, I combine it with wildcard matching and make use of the `$PSItem`.</span></span> <span data-ttu-id="891cf-159">Ceci va traiter un fichier journal et le convertir en messages d’avertissement et d’erreur en fonction des correspondances des expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="891cf-159">This would process a log file and convert it to warning and error messages depending on the regex matches.</span></span>

## <a name="advanced-details"></a><span data-ttu-id="891cf-160">Détails avancés</span><span class="sxs-lookup"><span data-stu-id="891cf-160">Advanced details</span></span>

<span data-ttu-id="891cf-161">Maintenant que vous avez pris connaissance de toutes ces fonctionnalités documentées, nous pouvons les utiliser dans le contexte d’un traitement plus avancé.</span><span class="sxs-lookup"><span data-stu-id="891cf-161">Now that you're aware of all these documented features, we can use them in the context of more advanced processing.</span></span>

### <a name="expressions"></a><span data-ttu-id="891cf-162">Expressions</span><span class="sxs-lookup"><span data-stu-id="891cf-162">Expressions</span></span>

<span data-ttu-id="891cf-163">`switch` peut porter sur une expression au lieu d’une variable.</span><span class="sxs-lookup"><span data-stu-id="891cf-163">The `switch` can be on an expression instead of a variable.</span></span>

``` powershell
switch ( ( Get-Service | Where status -eq 'running' ).name ) {...}
```

<span data-ttu-id="891cf-164">Le résultat de l’évaluation de l’expression est la valeur utilisée pour la correspondance.</span><span class="sxs-lookup"><span data-stu-id="891cf-164">Whatever the expression evaluates to is the value used for the match.</span></span>

### <a name="multiple-matches"></a><span data-ttu-id="891cf-165">Correspondances multiples</span><span class="sxs-lookup"><span data-stu-id="891cf-165">Multiple matches</span></span>

<span data-ttu-id="891cf-166">Vous avez peut-être déjà rencontré cela, mais `switch` peut établir une correspondance avec plusieurs conditions.</span><span class="sxs-lookup"><span data-stu-id="891cf-166">You may have already picked up on this, but a `switch` can match to multiple conditions.</span></span> <span data-ttu-id="891cf-167">C’est particulièrement vrai lors de l’utilisation de correspondances `-wildcard` ou `-regex`.</span><span class="sxs-lookup"><span data-stu-id="891cf-167">This is especially true when using `-wildcard` or `-regex` matches.</span></span> <span data-ttu-id="891cf-168">Vous pouvez ajouter la même condition plusieurs fois : dans ce cas, toutes sont déclenchées.</span><span class="sxs-lookup"><span data-stu-id="891cf-168">You can add the same condition multiple times and all of them are triggered.</span></span>

``` powershell
switch ( 'Word' )
{
    'word' { 'lower case word match' }
    'Word' { 'mixed case word match' }
    'WORD' { 'upper case word match' }
}
```

```Output
lower case word match
mixed case word match
upper case word match
```

<span data-ttu-id="891cf-169">Ces trois instructions sont déclenchées.</span><span class="sxs-lookup"><span data-stu-id="891cf-169">All three of these statements are fired.</span></span> <span data-ttu-id="891cf-170">Ceci montre que chaque condition est vérifiée (dans l’ordre).</span><span class="sxs-lookup"><span data-stu-id="891cf-170">This shows that every condition is checked (in order).</span></span> <span data-ttu-id="891cf-171">Ceci vaut aussi pour le traitement des tableaux où chaque élément vérifie chaque condition.</span><span class="sxs-lookup"><span data-stu-id="891cf-171">This holds true for processing arrays where each item checks each condition.</span></span>

### <a name="continue"></a><span data-ttu-id="891cf-172">Continue</span><span class="sxs-lookup"><span data-stu-id="891cf-172">Continue</span></span>

<span data-ttu-id="891cf-173">Normalement, ce serait le moment d’introduire l’instruction `break`, mais il est préférable de d’abord apprendre à utiliser `continue`.</span><span class="sxs-lookup"><span data-stu-id="891cf-173">Normally, this is where I would introduce the `break` statement, but it's better that we learn how to use `continue` first.</span></span> <span data-ttu-id="891cf-174">À l’instar d’une boucle `foreach`, `continue` poursuit sur l’élément suivant de la collection ou quitte l’instruction `switch` s’il n’y a plus d’éléments.</span><span class="sxs-lookup"><span data-stu-id="891cf-174">Just like with a `foreach` loop, `continue` continues onto the next item in the collection or exits the `switch` if there are no more items.</span></span> <span data-ttu-id="891cf-175">Nous pouvons réécrire ce dernier exemple avec des instructions continue de façon à ce qu’une seule instruction s’exécute.</span><span class="sxs-lookup"><span data-stu-id="891cf-175">We can rewrite that last example with continue statements so that only one statement executes.</span></span>

``` powershell
switch ( 'Word' )
{
    'word'
    {
        'lower case word match'
        continue
    }
    'Word'
    {
        'mixed case word match'
        continue
    }
    'WORD'
    {
        'upper case word match'
        continue
    }
}
```

```Output
lower case word match
```

<span data-ttu-id="891cf-176">Au lieu de mettre en correspondance les trois éléments, le premier est mis en correspondance et l’instruction switch continue à la valeur suivante.</span><span class="sxs-lookup"><span data-stu-id="891cf-176">Instead of matching all three items, the first one is matched and the switch continues to the next value.</span></span> <span data-ttu-id="891cf-177">Comme il n’y a plus de valeurs à traiter, l’instruction switch se termine.</span><span class="sxs-lookup"><span data-stu-id="891cf-177">Because there are no values left to process, the switch exits.</span></span> <span data-ttu-id="891cf-178">L’exemple suivant montre comment un caractère générique peut correspondre à plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="891cf-178">This next example is showing how a wildcard could match multiple items.</span></span>

``` powershell
switch -Wildcard -File $path
{
    '*Error*'
    {
        Write-Error -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

<span data-ttu-id="891cf-179">Comme une ligne du fichier d’entrée peut contenir à la fois le mot `Error` et le mot `Warning`, nous voulons seulement que le premier s’exécute, puis nous poursuivons le traitement du fichier.</span><span class="sxs-lookup"><span data-stu-id="891cf-179">Because a line in the input file could contain both the word `Error` and `Warning`, we only want the first one to execute and then continue processing the file.</span></span>

### <a name="break"></a><span data-ttu-id="891cf-180">Arrêter</span><span class="sxs-lookup"><span data-stu-id="891cf-180">Break</span></span>

<span data-ttu-id="891cf-181">Une instruction `break` quitte l’instruction switch.</span><span class="sxs-lookup"><span data-stu-id="891cf-181">A `break` statement exits the switch.</span></span> <span data-ttu-id="891cf-182">Il s’agit du même comportement que celui présenté par `continue` pour les valeurs uniques.</span><span class="sxs-lookup"><span data-stu-id="891cf-182">This is the same behavior that `continue` presents for single values.</span></span> <span data-ttu-id="891cf-183">La différence apparaît lors du traitement d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="891cf-183">The difference is shown when processing an array.</span></span> <span data-ttu-id="891cf-184">`break` arrête tout traitement dans l’instruction switch et `continue` passe à l’élément suivant.</span><span class="sxs-lookup"><span data-stu-id="891cf-184">`break` stops all processing in the switch and `continue` moves onto the next item.</span></span>

``` powershell
$Messages = @(
    'Downloading update'
    'Ran into errors downloading file'
    'Error: out of disk space'
    'Sending email'
    '...'
)

switch -Wildcard ($Messages)
{
    'Error*'
    {
        Write-Error -Message $PSItem
        break
    }
    '*Error*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

```Output
Downloading update
WARNING: Ran into errors downloading file
write-error -message $PSItem : Error: out of disk space
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

<span data-ttu-id="891cf-185">Dans le cas présent, si nous atteignons des lignes commençant par `Error`, nous obtenons une erreur et l’instruction switch s’arrête.</span><span class="sxs-lookup"><span data-stu-id="891cf-185">In this case, if we hit any lines that start with `Error` then we get an error and the switch stops.</span></span>
<span data-ttu-id="891cf-186">C’est ce que l’instruction `break` fait pour nous.</span><span class="sxs-lookup"><span data-stu-id="891cf-186">This is what that `break` statement is doing for us.</span></span> <span data-ttu-id="891cf-187">Si nous trouvons `Error` dans la chaîne et pas seulement au début, nous l’écrivons en tant qu’avertissement.</span><span class="sxs-lookup"><span data-stu-id="891cf-187">If we find `Error` inside the string and not just at the beginning, we write it as a warning.</span></span> <span data-ttu-id="891cf-188">Nous faisons la même chose pour `Warning`.</span><span class="sxs-lookup"><span data-stu-id="891cf-188">We do the same thing for `Warning`.</span></span> <span data-ttu-id="891cf-189">Il est possible qu’une ligne ait à la fois le mot `Error` et le mot `Warning`, mais nous ne devons traiter qu’un seul de ces mots.</span><span class="sxs-lookup"><span data-stu-id="891cf-189">It's possible that a line could have both the word `Error` and `Warning`, but we only need one to process.</span></span> <span data-ttu-id="891cf-190">C’est ce que fait l’instruction `continue` pour nous.</span><span class="sxs-lookup"><span data-stu-id="891cf-190">This is what the `continue` statement is doing for us.</span></span>

### <a name="break-labels"></a><span data-ttu-id="891cf-191">Étiquette de break</span><span class="sxs-lookup"><span data-stu-id="891cf-191">Break labels</span></span>

<span data-ttu-id="891cf-192">L’instruction `switch` prend en charge les étiquettes `break/continue`, tout comme `foreach`.</span><span class="sxs-lookup"><span data-stu-id="891cf-192">The `switch` statement supports `break/continue` labels just like `foreach`.</span></span>

``` powershell
:filelist foreach($path in $logs)
{
    :logFile switch -Wildcard -File $path
    {
        'Error*'
        {
            Write-Error -Message $PSItem
            break filelist
        }
        'Warning*'
        {
            Write-Error -Message $PSItem
            break logFile
        }
        default
        {
            Write-Output $PSItem
        }
    }
}
```

<span data-ttu-id="891cf-193">Personnellement, je n’aime pas utiliser des étiquettes de break, mais je voulais en parler car elles induisent de la confusion si vous ne les avez jamais vues auparavant.</span><span class="sxs-lookup"><span data-stu-id="891cf-193">I personally don't like the use of break labels but I wanted to point them out because they're confusing if you've never seen them before.</span></span> <span data-ttu-id="891cf-194">Quand vous avez plusieurs instructions `switch` ou `foreach` imbriquées, vous pouvez souhaiter quitter plus que l’élément le plus intérieur.</span><span class="sxs-lookup"><span data-stu-id="891cf-194">When you have multiple `switch` or `foreach` statements that are nested, you may want to break out of more than the inner most item.</span></span> <span data-ttu-id="891cf-195">Vous pouvez placer une étiquette sur une instruction `switch` qui peut être la cible de votre `break`.</span><span class="sxs-lookup"><span data-stu-id="891cf-195">You can place a label on a `switch` that can be the target of your `break`.</span></span>

### <a name="enum"></a><span data-ttu-id="891cf-196">Enum</span><span class="sxs-lookup"><span data-stu-id="891cf-196">Enum</span></span>

<span data-ttu-id="891cf-197">PowerShell 5.0 nous a apporté les énumérations et nous pouvons les utiliser dans une instruction switch.</span><span class="sxs-lookup"><span data-stu-id="891cf-197">PowerShell 5.0 gave us enums and we can use them in a switch.</span></span>

``` powershell
enum Context {
    Component
    Role
    Location
}

$item = [Context]::Role

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

<span data-ttu-id="891cf-198">Si vous voulez conserver tout sous forme d’énumérations fortement typées, vous pouvez les placer entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="891cf-198">If you want to keep everything as strongly typed enums, then you can place them in parentheses.</span></span>

``` powershell
switch ($item )
{
    ([Context]::Component)
    {
        'is a component'
    }
    ([Context]::Role)
    {
        'is a role'
    }
    ([Context]::Location)
    {
        'is a location'
    }
}
```

<span data-ttu-id="891cf-199">Les parenthèses sont nécessaires ici afin que l’instruction switch ne traite pas la valeur `[Context]::Location` comme chaîne littérale.</span><span class="sxs-lookup"><span data-stu-id="891cf-199">The parentheses are needed here so that the switch doesn't treat the value `[Context]::Location` as a literal string.</span></span>

### <a name="scriptblock"></a><span data-ttu-id="891cf-200">ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="891cf-200">ScriptBlock</span></span>

<span data-ttu-id="891cf-201">Nous pouvons utiliser un scriptblock pour effectuer si nécessaire l’évaluation d’une correspondance.</span><span class="sxs-lookup"><span data-stu-id="891cf-201">We can use a scriptblock to perform the evaluation for a match if needed.</span></span>

``` powershell
$age = 37

switch ( $age )
{
    {$PSItem -le 18}
    {
        'child'
    }
    {$PSItem -gt 18}
    {
        'adult'
    }
}
```

```Output
'adult'
```

<span data-ttu-id="891cf-202">Ceci ajoute de la complexité et peut rendre votre instruction `switch` difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="891cf-202">This adds complexity and can make your `switch` hard to read.</span></span> <span data-ttu-id="891cf-203">Dans la plupart des cas où vous utiliseriez quelque chose comme ceci, il serait préférable d’utiliser des instructions `if` et `elseif`.</span><span class="sxs-lookup"><span data-stu-id="891cf-203">In most cases where you would use something like this it would be better to use `if` and `elseif` statements.</span></span> <span data-ttu-id="891cf-204">J’envisagerais de l’utiliser si j’avais déjà une grande instruction switch en place et que j’avais besoin de deux éléments pour atteindre le même bloc d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="891cf-204">I would consider using this if I already had a large switch in place and I needed two items to hit the same evaluation block.</span></span>

<span data-ttu-id="891cf-205">Une chose dont je pense qu’elle augmente la lisibilité est de placer le scriptblock entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="891cf-205">One thing that I think helps with legibility is to place the scriptblock in parentheses.</span></span>

``` powershell
switch ( $age )
{
    ({$PSItem -le 18})
    {
        'child'
    }
    ({$PSItem -gt 18})
    {
        'adult'
    }
}
```

<span data-ttu-id="891cf-206">Il s’exécute pareillement et offre une meilleure décomposition visuelle quand vous le regardez rapidement.</span><span class="sxs-lookup"><span data-stu-id="891cf-206">It still executes the same way and gives a better visual break when quickly looking at it.</span></span>

### <a name="regex-matches"></a><span data-ttu-id="891cf-207">$matches pour les expressions régulières</span><span class="sxs-lookup"><span data-stu-id="891cf-207">Regex $matches</span></span>

<span data-ttu-id="891cf-208">Nous devons revisiter regex pour expliquer quelque chose qui n’est pas immédiatement évident.</span><span class="sxs-lookup"><span data-stu-id="891cf-208">We need to revisit regex to touch on something that isn't immediately obvious.</span></span> <span data-ttu-id="891cf-209">L’utilisation de regex remplit la variable `$matches`.</span><span class="sxs-lookup"><span data-stu-id="891cf-209">The use of regex populates the `$matches` variable.</span></span> <span data-ttu-id="891cf-210">J’explique de façon plus détaillée l’utilisation de `$matches` quand je parle des [Les nombreuses façons d’utiliser les expressions régulières][].</span><span class="sxs-lookup"><span data-stu-id="891cf-210">I do go into the use of `$matches` more when I talk about [The many ways to use regex][].</span></span> <span data-ttu-id="891cf-211">Voici un exemple rapide qui le montre en action avec des correspondances nommées.</span><span class="sxs-lookup"><span data-stu-id="891cf-211">Here is a quick sample to show it in action with named matches.</span></span>

``` powershell
$message = 'my ssn is 123-23-3456 and credit card: 1234-5678-1234-5678'

switch -regex ($message)
{
    '(?<SSN>\d\d\d-\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a SSN: $($matches.SSN)"
    }
    '(?<CC>\d\d\d\d-\d\d\d\d-\d\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a credit card number: $($matches.CC)"
    }
    '(?<Phone>\d\d\d-\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a phone number: $($matches.Phone)"
    }
}
```

```Output
WARNING: message may contain a SSN: 123-23-3456
WARNING: message may contain a credit card number: 1234-5678-1234-5678
```

### <a name="null"></a><span data-ttu-id="891cf-212">$null</span><span class="sxs-lookup"><span data-stu-id="891cf-212">$null</span></span>

<span data-ttu-id="891cf-213">Vous pouvez mettre en correspondance une valeur de `$null` qui ne doit pas nécessairement être la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="891cf-213">You can match a `$null` value that doesn't have to be the default.</span></span>

``` powershell
$value = $null

switch ( $value )
{
    $null
    {
        'Value is null'
    }
    default
    {
        'value is not null'
    }
}

```Output
Value is null
```

<span data-ttu-id="891cf-214">Il en va de même pour une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="891cf-214">Same goes for an empty string.</span></span>

``` powershell
switch ( '' )
{
    ''
    {
        'Value is empty'
    }
    default
    {
        'value is a empty string'
    }
}

```Output
Value is empty
```

### <a name="constant-expression"></a><span data-ttu-id="891cf-215">Expression de constante</span><span class="sxs-lookup"><span data-stu-id="891cf-215">Constant expression</span></span>

<span data-ttu-id="891cf-216">Lee Dailey a fait remarquer que nous pouvions utiliser une expression `$true` de constante pour évaluer des éléments `[bool]`.</span><span class="sxs-lookup"><span data-stu-id="891cf-216">Lee Dailey pointed out that we can use a constant `$true` expression to evaluate `[bool]` items.</span></span>
<span data-ttu-id="891cf-217">Imaginez si nous avons plusieurs vérifications booléennes qui doivent se produire.</span><span class="sxs-lookup"><span data-stu-id="891cf-217">Imagine if we have several boolean checks that need to happen.</span></span>

``` powershell
$isVisible = $false
$isEnabled = $true
$isSecure = $true

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isSecure
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Enabled-AdminMenu
```

<span data-ttu-id="891cf-218">Il s’agit d’une méthode propre pour évaluer et entreprendre des actions selon l’état de plusieurs champs booléens.</span><span class="sxs-lookup"><span data-stu-id="891cf-218">This is a clean way to evaluate and take action on the status of several boolean fields.</span></span> <span data-ttu-id="891cf-219">L’avantage est que vous pouvez faire en sorte qu’une correspondance inverse l’état d’une valeur qui n’a pas encore été évaluée.</span><span class="sxs-lookup"><span data-stu-id="891cf-219">The cool thing about this is that you can have one match flip the status of a value that hasn't been evaluated yet.</span></span>

``` powershell
$isVisible = $false
$isEnabled = $true
$isAdmin = $false

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
        $isVisible = $true
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isAdmin
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Show-Animation
```

<span data-ttu-id="891cf-220">Définir `$isEnabled` sur `$true` dans cet exemple permet de garantir que `$isVisible` est également défini sur `$true`.</span><span class="sxs-lookup"><span data-stu-id="891cf-220">Setting `$isEnabled` to `$true` in this example makes sure that `$isVisible` is also set to `$true`.</span></span> <span data-ttu-id="891cf-221">Ensuite, quand `$isVisible` est évalué, son scriptblock est appelé.</span><span class="sxs-lookup"><span data-stu-id="891cf-221">Then when `$isVisible` gets evaluated, its scriptblock is invoked.</span></span> <span data-ttu-id="891cf-222">C’est un peu contre-intuitif, mais c’est une utilisation intelligente de la mécanique.</span><span class="sxs-lookup"><span data-stu-id="891cf-222">This is a bit counter-intuitive but is a clever use of the mechanics.</span></span>

### <a name="switch-automatic-variable"></a><span data-ttu-id="891cf-223">Variable automatique $switch</span><span class="sxs-lookup"><span data-stu-id="891cf-223">$switch automatic variable</span></span>

<span data-ttu-id="891cf-224">Quand l’instruction `switch` traite ses valeurs, elle crée un énumérateur et l’appelle `$switch`.</span><span class="sxs-lookup"><span data-stu-id="891cf-224">When the `switch` is processing its values, it creates an enumerator and calls it `$switch`.</span></span> <span data-ttu-id="891cf-225">Il s’agit d’une variable automatique créée par PowerShell et vous pouvez la manipuler directement.</span><span class="sxs-lookup"><span data-stu-id="891cf-225">This is an automatic variable created by PowerShell and you can manipulate it directly.</span></span>

```powershell
$a = 1, 2, 3, 4

switch($a) {
    1 { [void]$switch.MoveNext(); $switch.Current }
    3 { [void]$switch.MoveNext(); $switch.Current }
}
```

<span data-ttu-id="891cf-226">Vous obtenez les résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="891cf-226">This gives you the results of:</span></span>

```Output
2
4
```

<span data-ttu-id="891cf-227">En déplaçant l’énumérateur vers l’avant, l’élément suivant n’est pas traité par l’instruction `switch`, mais vous pouvez accéder à cette valeur directement.</span><span class="sxs-lookup"><span data-stu-id="891cf-227">By moving the enumerator forward, the next item doesn't get processed by the `switch` but you can access that value directly.</span></span> <span data-ttu-id="891cf-228">Je pense que ce ne serait pas raisonnable.</span><span class="sxs-lookup"><span data-stu-id="891cf-228">I would call it madness.</span></span>

## <a name="other-patterns"></a><span data-ttu-id="891cf-229">Autres modèles</span><span class="sxs-lookup"><span data-stu-id="891cf-229">Other patterns</span></span>

### <a name="hashtables"></a><span data-ttu-id="891cf-230">Tables de hachage</span><span class="sxs-lookup"><span data-stu-id="891cf-230">Hashtables</span></span>

<span data-ttu-id="891cf-231">Une de mes publications les plus consultées est celle qui est consacrée aux [tables de hachage][].</span><span class="sxs-lookup"><span data-stu-id="891cf-231">One of my most popular posts is the one I did on [hashtables][].</span></span> <span data-ttu-id="891cf-232">Un des cas d’usage d’une `hashtable` est d’en faire une table de recherche.</span><span class="sxs-lookup"><span data-stu-id="891cf-232">One of the use cases for a `hashtable` is to be a lookup table.</span></span> <span data-ttu-id="891cf-233">Il s’agit d’une approche alternative à un modèle courant où l’on utilise souvent une instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="891cf-233">That is an alternate approach to a common pattern that a `switch` statement is often addressing.</span></span>

``` powershell
$day = 3

$lookup = @{
    0 = 'Sunday'
    1 = 'Monday'
    2 = 'Tuesday'
    3 = 'Wednesday'
    4 = 'Thursday'
    5 = 'Friday'
    6 = 'Saturday'
}

$lookup[$day]
```

```Output
Wednesday
```

<span data-ttu-id="891cf-234">Si je constate que j’utilise une instruction `switch` seulement comme une structure pour la recherche, j’utilise alors souvent une `hashtable` à la place.</span><span class="sxs-lookup"><span data-stu-id="891cf-234">If I'm only using a `switch` as a lookup, I often use a `hashtable` instead.</span></span>

### <a name="enum"></a><span data-ttu-id="891cf-235">Enum</span><span class="sxs-lookup"><span data-stu-id="891cf-235">Enum</span></span>

<span data-ttu-id="891cf-236">PowerShell 5.0 a introduit `Enum` et c’est également une option dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="891cf-236">PowerShell 5.0 introduced the `Enum` and it's also an option in this case.</span></span>

``` powershell
$day = 3

enum DayOfTheWeek {
    Sunday
    Monday
    Tuesday
    Wednesday
    Thursday
    Friday
    Saturday
}

[DayOfTheWeek]$day
```

```Output
Wednesday
```

<span data-ttu-id="891cf-237">Nous aurions pu rechercher pendant toute la journée différentes façons de résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="891cf-237">We could go all day looking at different ways to solve this problem.</span></span> <span data-ttu-id="891cf-238">Je voulais simplement être sûr que vous sachiez qu’il y avait différentes options.</span><span class="sxs-lookup"><span data-stu-id="891cf-238">I just wanted to make sure you knew you had options.</span></span>

## <a name="final-words"></a><span data-ttu-id="891cf-239">Le mot de la fin</span><span class="sxs-lookup"><span data-stu-id="891cf-239">Final words</span></span>

<span data-ttu-id="891cf-240">L’instruction switch est simple en apparence, mais elle offre des fonctionnalités avancées dont la plupart des gens ne savent pas qu’elles sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="891cf-240">The switch statement is simple on the surface but it offers some advanced features that most people don't realize are available.</span></span> <span data-ttu-id="891cf-241">Combiner ensemble ces fonctionnalités transforme le tout en une puissante fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="891cf-241">Stringing those features together makes this a powerful feature.</span></span> <span data-ttu-id="891cf-242">J’espère que vous avez appris des choses que vous ne connaissiez pas encore.</span><span class="sxs-lookup"><span data-stu-id="891cf-242">I hope you learned something that you had not realized before.</span></span>

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[original version]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[switch]: /powershell/module/microsoft.powershell.core/about/about_switch
[Paramètres de commutateur]: https://www.powershellmagazine.com/2013/12/20/using-powershell-switch-vs-boolean-parameters-in-sma-runbooks/
[switch parameters]: https://www.powershellmagazine.com/2013/12/20/using-powershell-switch-vs-boolean-parameters-in-sma-runbooks/
[Les nombreuses façons d’utiliser les expressions régulières]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[The many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[Tables de hachage]: everything-about-hashtable.md
[hashtables]: everything-about-hashtable.md
