---
title: Tout ce que vous avez toujours voulu savoir sur la substitution de variable dans les chaînes
description: Il existe de nombreuses façons d’utiliser des variables dans des chaînes pour créer du texte mis en forme.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 786526fb98dbf1b3ec7c5c6c985ac95b85a96259
ms.sourcegitcommit: 4bb44f183dcbfa8dced57f075812e02d3b45fd70
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301316"
---
# <a name="everything-you-wanted-to-know-about-variable-substitution-in-strings"></a><span data-ttu-id="5a412-103">Tout ce que vous avez toujours voulu savoir sur la substitution de variable dans les chaînes</span><span class="sxs-lookup"><span data-stu-id="5a412-103">Everything you wanted to know about variable substitution in strings</span></span>

<span data-ttu-id="5a412-104">Il existe de nombreuses façons d’utiliser des variables dans les chaînes.</span><span class="sxs-lookup"><span data-stu-id="5a412-104">There are many ways to use variables in strings.</span></span> <span data-ttu-id="5a412-105">J’appelle ceci « substitution de variable », mais je fais référence à chaque fois que vous voulez mettre en forme une chaîne pour y inclure des valeurs provenant de variables.</span><span class="sxs-lookup"><span data-stu-id="5a412-105">I'm calling this variable substitution but I'm referring to any time you want to format a string to include values from variables.</span></span> <span data-ttu-id="5a412-106">C’est quelque chose que j’explique souvent aux personnes qui débutent dans l’écriture de scripts.</span><span class="sxs-lookup"><span data-stu-id="5a412-106">This is something that I often find myself explaining to new scripters.</span></span>

> [!NOTE]
> <span data-ttu-id="5a412-107">La [Version d’origine][] de cet article est parue sur le blog écrit par [@KevinMarquette][].</span><span class="sxs-lookup"><span data-stu-id="5a412-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="5a412-108">L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu avec nous.</span><span class="sxs-lookup"><span data-stu-id="5a412-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="5a412-109">Consultez son blog sur [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="5a412-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="concatenation"></a><span data-ttu-id="5a412-110">Concaténation</span><span class="sxs-lookup"><span data-stu-id="5a412-110">Concatenation</span></span>

<span data-ttu-id="5a412-111">La première catégorie de méthodes est celle des méthodes de concaténation.</span><span class="sxs-lookup"><span data-stu-id="5a412-111">The first class of methods can be referred to as concatenation.</span></span> <span data-ttu-id="5a412-112">En gros, elles prennent plusieurs chaînes et les assemblent.</span><span class="sxs-lookup"><span data-stu-id="5a412-112">It's basically taking several strings and joining them together.</span></span> <span data-ttu-id="5a412-113">La concaténation est utilisée depuis longtemps pour construire des chaînes mises en forme.</span><span class="sxs-lookup"><span data-stu-id="5a412-113">There's a long history of using concatenation to build formatted strings.</span></span>

```powershell
$name = 'Kevin Marquette'
$message = 'Hello, ' + $name
```

<span data-ttu-id="5a412-114">La concaténation est une bonne solution quand il n’y a que quelques valeurs à ajouter.</span><span class="sxs-lookup"><span data-stu-id="5a412-114">Concatenation works out OK when there are only a few values to add.</span></span> <span data-ttu-id="5a412-115">Cela peut cependant devenir rapidement compliqué.</span><span class="sxs-lookup"><span data-stu-id="5a412-115">But this can get complicated quickly.</span></span>

```powershell
$first = 'Kevin'
$last = 'Marquette'
```

```powershell
$message = 'Hello, ' + $first + ' ' + $last + '.'
```

<span data-ttu-id="5a412-116">Ce simple exemple est déjà plus difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="5a412-116">This simple example is already getting harder to read.</span></span>

## <a name="variable-substitution"></a><span data-ttu-id="5a412-117">Substitution de variables</span><span class="sxs-lookup"><span data-stu-id="5a412-117">Variable substitution</span></span>

<span data-ttu-id="5a412-118">PowerShell a une autre option plus facile.</span><span class="sxs-lookup"><span data-stu-id="5a412-118">PowerShell has another option that is easier.</span></span> <span data-ttu-id="5a412-119">Vous pouvez spécifier vos variables directement dans les chaînes.</span><span class="sxs-lookup"><span data-stu-id="5a412-119">You can specify your variables directly in the strings.</span></span>

```powershell
$message = "Hello, $first $last."
```

<span data-ttu-id="5a412-120">Le type de guillemets que vous utilisez autour des chaînes fait la différence.</span><span class="sxs-lookup"><span data-stu-id="5a412-120">The type of quotes you use around the string makes a difference.</span></span> <span data-ttu-id="5a412-121">Une chaîne entre guillemets doubles permet la substitution, mais pas une chaîne entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="5a412-121">A double quoted string allows the substitution but a single quoted string doesn't.</span></span> <span data-ttu-id="5a412-122">Selon les moments, vous avez besoin de l’une ou de l’autre, et vous avez donc un choix à faire.</span><span class="sxs-lookup"><span data-stu-id="5a412-122">There are times you want one or the other so you have an option.</span></span>

## <a name="command-substitution"></a><span data-ttu-id="5a412-123">Substitution dans les commandes</span><span class="sxs-lookup"><span data-stu-id="5a412-123">Command substitution</span></span>

<span data-ttu-id="5a412-124">Les choses deviennent un peu plus compliquées quand vous voulez obtenir les valeurs de propriétés dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5a412-124">Things get a little tricky when you start trying to get the values of properties into a string.</span></span> <span data-ttu-id="5a412-125">C’est là que beaucoup de débutants ont des difficultés.</span><span class="sxs-lookup"><span data-stu-id="5a412-125">This is where many new people get tripped up.</span></span> <span data-ttu-id="5a412-126">Laissez-moi d’abord vous montrer ce qu’ils pensent devoir fonctionner (et à première vue, ce devrait bien être le cas).</span><span class="sxs-lookup"><span data-stu-id="5a412-126">First let me show you what they think should work (and at face value almost looks like it should).</span></span>

```powershell
$directory = Get-Item 'c:\windows'
$message = "Time: $directory.CreationTime"
```

<span data-ttu-id="5a412-127">Vous vous attendez à obtenir `CreationTime` de `$directory`, mais au lieu de cela, vous obtenez `Time: c:\windows.CreationTime` comme valeur.</span><span class="sxs-lookup"><span data-stu-id="5a412-127">You would be expecting to get the `CreationTime` off of the `$directory`, but instead you get this `Time: c:\windows.CreationTime` as your value.</span></span> <span data-ttu-id="5a412-128">La raison en est que ce type de substitution voit seulement la variable de base.</span><span class="sxs-lookup"><span data-stu-id="5a412-128">The reason is that this type of substitution only sees the base variable.</span></span> <span data-ttu-id="5a412-129">Elle considère le point comme faisant partie de la chaîne : elle arrête donc la résolution de la valeur à cet endroit.</span><span class="sxs-lookup"><span data-stu-id="5a412-129">It considers the period as part of the string so it stops resolving the value any deeper.</span></span>

<span data-ttu-id="5a412-130">Il arrive que cet objet donne une chaîne comme valeur par défaut quand il est placé dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5a412-130">It just so happens that this object gives a string as a default value when placed into a string.</span></span>
<span data-ttu-id="5a412-131">Certains objets vous donnent à la place le nom du type, comme `System.Collections.Hashtable`.</span><span class="sxs-lookup"><span data-stu-id="5a412-131">Some objects give you the type name instead like `System.Collections.Hashtable`.</span></span> <span data-ttu-id="5a412-132">Juste quelque chose à rechercher.</span><span class="sxs-lookup"><span data-stu-id="5a412-132">Just something to watch for.</span></span>

<span data-ttu-id="5a412-133">PowerShell vous permet de demander l’exécution de commandes à l’intérieur de la chaîne avec une syntaxe spéciale.</span><span class="sxs-lookup"><span data-stu-id="5a412-133">PowerShell allows you to do command execution inside the string with a special syntax.</span></span> <span data-ttu-id="5a412-134">Ce qui nous permet d’obtenir les propriétés de ces objets et d’exécuter n’importe quelle autre commande pour obtenir une valeur.</span><span class="sxs-lookup"><span data-stu-id="5a412-134">This allows us to get the properties of these objects and run any other command to get a value.</span></span>

```powershell
$message = "Time: $($directory.CreationTime)"
```

<span data-ttu-id="5a412-135">Cela fonctionne bien pour certaines situations, mais ce peut-être aussi compliqué que la concaténation si vous avez seulement quelques variables.</span><span class="sxs-lookup"><span data-stu-id="5a412-135">This works great for some situations but it can get just as crazy as concatenation if you have just a few variables.</span></span>

### <a name="command-execution"></a><span data-ttu-id="5a412-136">Exécution de commande</span><span class="sxs-lookup"><span data-stu-id="5a412-136">Command execution</span></span>

<span data-ttu-id="5a412-137">Vous pouvez exécuter des commandes à l’intérieure d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5a412-137">You can run commands inside a string.</span></span> <span data-ttu-id="5a412-138">Même si j’ai cette option, je ne l’aime pas.</span><span class="sxs-lookup"><span data-stu-id="5a412-138">Even though I have this option, I don't like it.</span></span> <span data-ttu-id="5a412-139">Cela devient rapidement compliqué et difficile à déboguer.</span><span class="sxs-lookup"><span data-stu-id="5a412-139">It gets cluttered quickly and hard to debug.</span></span> <span data-ttu-id="5a412-140">Je peux exécuter la commande et enregistrer dans une variable ou utiliser une chaîne de format.</span><span class="sxs-lookup"><span data-stu-id="5a412-140">I either run the command and save to a variable or use a format string.</span></span>

```powershell
$message = "Date: $(Get-Date)"
```

## <a name="format-string"></a><span data-ttu-id="5a412-141">Chaîne de format</span><span class="sxs-lookup"><span data-stu-id="5a412-141">Format string</span></span>

<span data-ttu-id="5a412-142">.NET a un moyen de mettre en forme les chaînes que je trouve facile à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5a412-142">.NET has a way to format strings that I find fairly easy to work with.</span></span> <span data-ttu-id="5a412-143">Laissez-moi d’abord vous montrer la méthode statique avant de vous montrer le raccourci PowerShell pour faire la même chose.</span><span class="sxs-lookup"><span data-stu-id="5a412-143">First let me show you the static method for it before I show you the PowerShell shortcut to do the same thing.</span></span>

```powershell
# .NET string format string
[string]::Format('Hello, {0} {1}.',$first,$last)

# PowerShell format string
'Hello, {0} {1}.' -f $first, $last
```

<span data-ttu-id="5a412-144">Ce qui se passe ici est que la chaîne est analysée à la recherche des jetons `{0}` et `{1}`, puis elle utilise ce numéro pour choisir parmi les valeurs fournies.</span><span class="sxs-lookup"><span data-stu-id="5a412-144">What is happening here is that the string is parsed for the tokens `{0}` and `{1}`, then it uses that number to pick from the values provided.</span></span> <span data-ttu-id="5a412-145">Si vous voulez répéter une valeur à un certain endroit dans la chaîne, vous pouvez réutiliser le numéro de cette valeur.</span><span class="sxs-lookup"><span data-stu-id="5a412-145">If you want to repeat one value some place in the string, you can reuse that values number.</span></span>

<span data-ttu-id="5a412-146">Plus la chaîne est complexe, plus cette approche est pratique.</span><span class="sxs-lookup"><span data-stu-id="5a412-146">The more complicated the string gets, the more value you get out of this approach.</span></span>

### <a name="format-values-as-arrays"></a><span data-ttu-id="5a412-147">Mettre en forme des valeurs en tant que tableaux</span><span class="sxs-lookup"><span data-stu-id="5a412-147">Format values as arrays</span></span>

<span data-ttu-id="5a412-148">Si votre ligne de mise en forme est trop longue, vous pouvez d’abord placer vos valeurs dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="5a412-148">If your format line gets too long, you can place your values into an array first.</span></span>

```powershell
$values = @(
    "Kevin"
    "Marquette"
)
'Hello, {0} {1}.' -f $values
```

<span data-ttu-id="5a412-149">Ce n’est pas du splatting, car je passe en entrée l’ensemble du tableau, mais l’idée est similaire.</span><span class="sxs-lookup"><span data-stu-id="5a412-149">This is not splatting because I'm passing the whole array in, but the idea is similar.</span></span>

## <a name="advanced-formatting"></a><span data-ttu-id="5a412-150">Mise en forme avancée</span><span class="sxs-lookup"><span data-stu-id="5a412-150">Advanced formatting</span></span>

<span data-ttu-id="5a412-151">Je les ai intentionnellement appelées comme provenant de .NET, car de nombreuses options de mise en forme y sont déjà bien [documentées][].</span><span class="sxs-lookup"><span data-stu-id="5a412-151">I intentionally called these out as coming from .NET because there are lots of formatting options already well [documented][] on it.</span></span> <span data-ttu-id="5a412-152">Il existe plusieurs moyens intégrés de mettre en forme différents types de données.</span><span class="sxs-lookup"><span data-stu-id="5a412-152">There are built in ways to format various data types.</span></span>

```powershell
"{0:yyyyMMdd}" -f (Get-Date)
"Population {0:N0}" -f  8175133
```

<span data-ttu-id="5a412-153">Je ne vais pas les détailler, mais je voulais simplement vous dire qu’il s’agit d’un moteur de mise en forme très puissant si vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="5a412-153">I'm not going to go into them but I just wanted to let you know that this is a very powerful formatting engine if you need it.</span></span>

## <a name="joining-strings"></a><span data-ttu-id="5a412-154">Jonction de chaînes</span><span class="sxs-lookup"><span data-stu-id="5a412-154">Joining strings</span></span>

<span data-ttu-id="5a412-155">Parfois, vous voulez concaténer une liste de valeurs.</span><span class="sxs-lookup"><span data-stu-id="5a412-155">Sometimes you actually do want to concatenate a list of values together.</span></span> <span data-ttu-id="5a412-156">Il existe un opérateur `-join` qui peut le faire pour vous.</span><span class="sxs-lookup"><span data-stu-id="5a412-156">There's a `-join` operator that can do that for you.</span></span> <span data-ttu-id="5a412-157">Il vous permet même de spécifier un caractère à joindre entre les chaînes.</span><span class="sxs-lookup"><span data-stu-id="5a412-157">It even lets you specify a character to join between the strings.</span></span>

```powershell
$servers = @(
    'server1'
    'server2'
    'server3'
)

$servers  -join ','
```

<span data-ttu-id="5a412-158">Si vous utilisez `-join` avec des chaînes mais sans séparateur, vous devez spécifier une chaîne vide `''`.</span><span class="sxs-lookup"><span data-stu-id="5a412-158">If you want to `-join` some strings without a separator, you need to specify an empty string `''`.</span></span>
<span data-ttu-id="5a412-159">Mais si c’est tout ce dont vous avez besoin, il y a une option plus rapide.</span><span class="sxs-lookup"><span data-stu-id="5a412-159">But if that is all you need, there's a faster option.</span></span>

```powershell
[string]::Concat('server1','server2','server3')
[string]::Concat($servers)
```

<span data-ttu-id="5a412-160">Il est intéressant de noter que vous pouvez aussi appliquer `-split` pour décomposer des chaînes.</span><span class="sxs-lookup"><span data-stu-id="5a412-160">It's also worth pointing out that you can also `-split` strings too.</span></span>

## <a name="join-path"></a><span data-ttu-id="5a412-161">Join-Path</span><span class="sxs-lookup"><span data-stu-id="5a412-161">Join-Path</span></span>

<span data-ttu-id="5a412-162">Bien que souvent négligée, il s’agit d’une applet de commande intéressante pour créer un chemin de fichier.</span><span class="sxs-lookup"><span data-stu-id="5a412-162">This is often overlooked but a great cmdlet for building a file path.</span></span>

```powershell
$folder = 'Temp'
Join-Path -Path 'c:\windows' -ChildPath $folder
```

<span data-ttu-id="5a412-163">L’avantage est qu’elle traite correctement les barres obliques inverses quand elle place les valeurs ensemble.</span><span class="sxs-lookup"><span data-stu-id="5a412-163">The great thing about this is it works out the backslashes correctly when it puts the values together.</span></span> <span data-ttu-id="5a412-164">C’est particulièrement important si vous prenez des valeurs provenant d’utilisateurs ou de fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="5a412-164">This is especially important if you are taking values from users or config files.</span></span>

<span data-ttu-id="5a412-165">Cela fonctionne également bien avec `Split-Path` et `Test-Path`.</span><span class="sxs-lookup"><span data-stu-id="5a412-165">This also goes well with `Split-Path` and `Test-Path`.</span></span> <span data-ttu-id="5a412-166">J’en parle aussi dans mon billet sur [la lecture et l’enregistrement dans des fichiers][].</span><span class="sxs-lookup"><span data-stu-id="5a412-166">I also cover these in my post about [reading and saving to files][].</span></span>

## <a name="strings-are-arrays"></a><span data-ttu-id="5a412-167">Les chaînes sont des tableaux</span><span class="sxs-lookup"><span data-stu-id="5a412-167">Strings are arrays</span></span>

<span data-ttu-id="5a412-168">Je dois parler ici de l’ajout de chaînes avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="5a412-168">I do need to mention adding strings here before I go on.</span></span> <span data-ttu-id="5a412-169">Rappelez-vous qu’une chaîne est simplement un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="5a412-169">Remember that a string is just an array of characters.</span></span> <span data-ttu-id="5a412-170">Quand vous ajoutez plusieurs chaînes ensemble, un nouveau tableau est créé chaque fois.</span><span class="sxs-lookup"><span data-stu-id="5a412-170">When you add multiple strings together, a new array is created each time.</span></span>

<span data-ttu-id="5a412-171">Regardez cet exemple :</span><span class="sxs-lookup"><span data-stu-id="5a412-171">Look at this example:</span></span>

```powershell
$message = "Numbers: "
foreach($number in 1..10000)
{
    $message += " $number"
}
```

<span data-ttu-id="5a412-172">Il semble très simple, mais ce que vous ne voyez pas, c’est qu’à chaque fois qu’une chaîne est ajoutée à `$message`, une chaîne entièrement nouvelle est créée.</span><span class="sxs-lookup"><span data-stu-id="5a412-172">It looks very basic but what you don't see is that each time a string is added to `$message` that a whole new string is created.</span></span> <span data-ttu-id="5a412-173">La mémoire est allouée, les données sont copiées et les anciennes sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="5a412-173">Memory gets allocated, data gets copied and the old one is discarded.</span></span>
<span data-ttu-id="5a412-174">Ce n’est pas problématique quand ce n’est fait que quelques fois, mais une boucle comme celle-ci ferait apparaître le problème.</span><span class="sxs-lookup"><span data-stu-id="5a412-174">Not a big deal when it's only done a few times, but a loop like this would really expose the issue.</span></span>

### <a name="stringbuilder"></a><span data-ttu-id="5a412-175">StringBuilder</span><span class="sxs-lookup"><span data-stu-id="5a412-175">StringBuilder</span></span>

<span data-ttu-id="5a412-176">StringBuilder est également très utilisée pour créer de grandes chaînes à partir d’un grand nombre de chaînes plus petites.</span><span class="sxs-lookup"><span data-stu-id="5a412-176">StringBuilder is also very popular for building large strings from lots of smaller strings.</span></span> <span data-ttu-id="5a412-177">La raison en est qu’elle collecte simplement toutes les chaînes que vous y ajoutez et les concatène seulement à la fin quand vous récupérez la valeur.</span><span class="sxs-lookup"><span data-stu-id="5a412-177">The reason why is because it just collects all the strings you add to it and only concatenates all of them at the end when you retrieve the value.</span></span>

```powershell
$stringBuilder = New-Object -TypeName "System.Text.StringBuilder"

[void]$stringBuilder.Append("Numbers: ")
foreach($number in 1..10000)
{
    [void]$stringBuilder.Append(" $number")
}
$message = $stringBuilder.ToString()
```

<span data-ttu-id="5a412-178">À nouveau, c’est quelque chose qui me vient de .NET.</span><span class="sxs-lookup"><span data-stu-id="5a412-178">Again, this is something that I'm reaching out to .NET for.</span></span> <span data-ttu-id="5a412-179">Je ne l’utilise plus très souvent, mais il est bon de savoir qu’elle existe.</span><span class="sxs-lookup"><span data-stu-id="5a412-179">I don't use it often anymore but it's good to know it's there.</span></span>

## <a name="delineation-with-braces"></a><span data-ttu-id="5a412-180">Délimitation avec des crochets</span><span class="sxs-lookup"><span data-stu-id="5a412-180">Delineation with braces</span></span>

<span data-ttu-id="5a412-181">Ils sont utilisés pour la concaténation de suffixes dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="5a412-181">This is used for suffix concatenation within the string.</span></span> <span data-ttu-id="5a412-182">Parfois, votre variable n’a pas de limite de mot claire.</span><span class="sxs-lookup"><span data-stu-id="5a412-182">Sometimes your variable doesn't have a clean word boundary.</span></span>

```powershell
$test = "Bet"
$tester = "Better"
Write-Host "$test $tester ${test}ter"
```

<span data-ttu-id="5a412-183">Merci à [/u/real_parbold][] pour ceci.</span><span class="sxs-lookup"><span data-stu-id="5a412-183">Thank you [/u/real_parbold][] for that one.</span></span>

<span data-ttu-id="5a412-184">Voici une alternative à cette approche :</span><span class="sxs-lookup"><span data-stu-id="5a412-184">Here is an alternate to this approach:</span></span>

```powershell
Write-Host "$test $tester $($test)ter"
Write-Host "{0} {1} {0}ter" -f $test, $tester
```

<span data-ttu-id="5a412-185">J’utilise personnellement pour cela la chaîne de mise en forme, mais il est néanmoins bon de la connaître au cas où vous la rencontrez.</span><span class="sxs-lookup"><span data-stu-id="5a412-185">I personally use format string for this, but this is good to know incase you see it in the wild.</span></span>

## <a name="find-and-replace-tokens"></a><span data-ttu-id="5a412-186">Rechercher et remplacer des jetons</span><span class="sxs-lookup"><span data-stu-id="5a412-186">Find and replace tokens</span></span>

<span data-ttu-id="5a412-187">Bien que la plupart de ces fonctionnalités limitent votre besoin de déployer votre propre solution, il peut arriver que vous ayez de grands fichiers modèles où vous voulez remplacer des chaînes.</span><span class="sxs-lookup"><span data-stu-id="5a412-187">While most of these features limit your need to roll your own solution, there are times where you may have large template files where you want to replace strings inside.</span></span>

<span data-ttu-id="5a412-188">Supposons que vous ayez extrait un modèle à partir d’un fichier contenant beaucoup de texte.</span><span class="sxs-lookup"><span data-stu-id="5a412-188">Let us assume you pulled in a template from a file that has a lot of text.</span></span>

```powershell
$letter = Get-Content -Path TemplateLetter.txt -RAW
$letter = $letter -replace '#FULL_NAME#', 'Kevin Marquette'
```

<span data-ttu-id="5a412-189">Vous pouvez avoir beaucoup de jetons à remplacer.</span><span class="sxs-lookup"><span data-stu-id="5a412-189">You may have lots of tokens to replace.</span></span> <span data-ttu-id="5a412-190">L’astuce consiste à utiliser un jeton très spécifique facile à trouver et à remplacer.</span><span class="sxs-lookup"><span data-stu-id="5a412-190">The trick is to use a very distinct token that is easy to find and replace.</span></span> <span data-ttu-id="5a412-191">J’ai tendance à utiliser un caractère spécial aux deux extrémités pour le distinguer plus facilement.</span><span class="sxs-lookup"><span data-stu-id="5a412-191">I tend to use a special character at both ends to help distinguish it.</span></span>

<span data-ttu-id="5a412-192">J’ai récemment trouvé une nouvelle façon d’approcher ce problème.</span><span class="sxs-lookup"><span data-stu-id="5a412-192">I recently found a new way to approach this.</span></span> <span data-ttu-id="5a412-193">J’ai décidé de conserver cette section ici, car il s’agit d’un modèle couramment utilisé.</span><span class="sxs-lookup"><span data-stu-id="5a412-193">I decided to leave this section in here because this is a pattern that is commonly used.</span></span>

### <a name="replace-multiple-tokens"></a><span data-ttu-id="5a412-194">Remplacer plusieurs jetons</span><span class="sxs-lookup"><span data-stu-id="5a412-194">Replace multiple tokens</span></span>

<span data-ttu-id="5a412-195">Quand j’ai une liste de jetons que je dois remplacer, j’adopte une approche plus générique.</span><span class="sxs-lookup"><span data-stu-id="5a412-195">When I have a list of tokens that I need to replace, I take a more generic approach.</span></span> <span data-ttu-id="5a412-196">Je les place dans une table de hachage et j’itère dessus pour effectuer le remplacement.</span><span class="sxs-lookup"><span data-stu-id="5a412-196">I would place them in a hashtable and iterate over them to do the replace.</span></span>

```powershell
$tokenList = @{
    Full_Name = 'Kevin Marquette'
    Location = 'Orange County'
    State = 'CA'
}

$letter = Get-Content -Path TemplateLetter.txt -RAW
foreach( $token in $tokenList.GetEnumerator() )
{
    $pattern = '#{0}#' -f $token.key
    $letter = $letter -replace $pattern, $token.Value
}
```

<span data-ttu-id="5a412-197">Ces jetons peuvent être chargés si nécessaire depuis un fichier JSON ou CSV.</span><span class="sxs-lookup"><span data-stu-id="5a412-197">Those tokens could be loaded from JSON or CSV if needed.</span></span>

### <a name="executioncontext-expandstring"></a><span data-ttu-id="5a412-198">ExecutionContext ExpandString</span><span class="sxs-lookup"><span data-stu-id="5a412-198">ExecutionContext ExpandString</span></span>

<span data-ttu-id="5a412-199">Il existe un moyen intelligent de définir une chaîne de substitution avec des guillemets simples et de développer les variables plus tard .</span><span class="sxs-lookup"><span data-stu-id="5a412-199">There's a clever way to define a substitution string with single quotes and expand the variables later.</span></span> <span data-ttu-id="5a412-200">Regardez cet exemple :</span><span class="sxs-lookup"><span data-stu-id="5a412-200">Look at this example:</span></span>

```powershell
$message = 'Hello, $Name!'
$name = 'Kevin Marquette'
$string = $ExecutionContext.InvokeCommand.ExpandString($message)
```

<span data-ttu-id="5a412-201">L’appel à `.InvokeCommand.ExpandString` sur le contexte d’exécution actif utilise les variables dans l’étendue actuelle pour la substitution.</span><span class="sxs-lookup"><span data-stu-id="5a412-201">The call to `.InvokeCommand.ExpandString` on the current execution context uses the variables in the current scope for substitution.</span></span> <span data-ttu-id="5a412-202">L’élément clé est ici que `$message` peut être défini très tôt avant même que les variables n’existent.</span><span class="sxs-lookup"><span data-stu-id="5a412-202">The key thing here is that the `$message` can be defined very early before the variables even exist.</span></span>

<span data-ttu-id="5a412-203">Si nous développons cela juste un peu, nous pouvons effectuer cette substitution de façon répétée avec différentes valeurs.</span><span class="sxs-lookup"><span data-stu-id="5a412-203">If we expand on that just a little bit, we can perform this substitution over and over wih different values.</span></span>

```powershell
$message = 'Hello, $Name!'
$nameList = 'Mark Kraus','Kevin Marquette','Lee Dailey'
foreach($name in $nameList){
    $ExecutionContext.InvokeCommand.ExpandString($message)
}
```

<span data-ttu-id="5a412-204">Pour continuer sur cette idée, vous pourriez importer un grand modèle d’e-mail à partir d’un fichier texte pour faire cela.</span><span class="sxs-lookup"><span data-stu-id="5a412-204">To keep going on this idea; you could be importing a large email template from a text file to do this.</span></span> <span data-ttu-id="5a412-205">Je dois remercier [Mark Kraus][] pour cette [suggestion][].</span><span class="sxs-lookup"><span data-stu-id="5a412-205">I have to thank [Mark Kraus][] for this [suggestion][].</span></span>

## <a name="whatever-works-the-best-for-you"></a><span data-ttu-id="5a412-206">Ce qui fonctionne le mieux pour vous</span><span class="sxs-lookup"><span data-stu-id="5a412-206">Whatever works the best for you</span></span>

<span data-ttu-id="5a412-207">Je suis partisan de l’approche des chaînes de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="5a412-207">I'm a fan of the format string approach.</span></span> <span data-ttu-id="5a412-208">Je fais toujours ainsi avec les chaînes les plus compliquées ou s’il y a plusieurs variables.</span><span class="sxs-lookup"><span data-stu-id="5a412-208">I definitely do this with the more complicated strings or if there are multiple variables.</span></span> <span data-ttu-id="5a412-209">Sur quelque chose de très court, je peux utiliser l’une de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="5a412-209">On anything that is very short, I may use any one of these.</span></span>

## <a name="anything-else"></a><span data-ttu-id="5a412-210">Autre chose ?</span><span class="sxs-lookup"><span data-stu-id="5a412-210">Anything else?</span></span>

<span data-ttu-id="5a412-211">J’ai abordé beaucoup de choses dans ce billet.</span><span class="sxs-lookup"><span data-stu-id="5a412-211">I covered a lot of ground on this one.</span></span> <span data-ttu-id="5a412-212">J’espère que vous avez pu apprendre quelque chose de nouveau.</span><span class="sxs-lookup"><span data-stu-id="5a412-212">My hope is that you walk away learning something new.</span></span>

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[original version]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Mark Kraus]: https://get-powershellblog.blogspot.com/
[suggestion]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[/u/real_parbold]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfm6p/
[la lecture et l’enregistrement dans des fichiers]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[reading and saving to files]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[documentées]: /dotnet/api/system.string.format#overloads
[documented]: /dotnet/api/system.string.format#overloads
