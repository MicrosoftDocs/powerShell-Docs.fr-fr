---
title: Tout ce que vous avez toujours voulu savoir sur les tables de hachage
description: Les tables de hachage sont très importantes dans PowerShell, c’est pourquoi il est judicieux de parfaitement les maîtriser.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: e386e2aa2f7b85bee4bf622fd9251ef7642cf16a
ms.sourcegitcommit: 57e577097085dc621bd797ef4a7e2854ea7d4e29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "97980499"
---
# <a name="everything-you-wanted-to-know-about-hashtables"></a><span data-ttu-id="83f88-103">Tout ce que vous avez toujours voulu savoir sur les tables de hachage</span><span class="sxs-lookup"><span data-stu-id="83f88-103">Everything you wanted to know about hashtables</span></span>

<span data-ttu-id="83f88-104">Revenons en arrière pour parler des [tables de hachage][].</span><span class="sxs-lookup"><span data-stu-id="83f88-104">I want to take a step back and talk about [hashtables][].</span></span> <span data-ttu-id="83f88-105">Je les utilise tout le temps maintenant.</span><span class="sxs-lookup"><span data-stu-id="83f88-105">I use them all the time now.</span></span> <span data-ttu-id="83f88-106">Je les expliquais hier soir à quelqu’un, après la réunion de notre groupe d'utilisateurs, et je me suis rendu compte que j’avais les mêmes lacunes que lui.</span><span class="sxs-lookup"><span data-stu-id="83f88-106">I was teaching someone about them after our user group meeting last night and I realized I had the same confusion about them as he had.</span></span> <span data-ttu-id="83f88-107">Les tables de hachage sont très importantes dans PowerShell, c’est pourquoi il est judicieux de parfaitement les maîtriser.</span><span class="sxs-lookup"><span data-stu-id="83f88-107">Hashtables are really important in PowerShell so it's good to have a solid understanding of them.</span></span>

> [!NOTE]
> <span data-ttu-id="83f88-108">La [Version d’origine][] de cet article est parue sur le blog écrit par [@KevinMarquette][].</span><span class="sxs-lookup"><span data-stu-id="83f88-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="83f88-109">L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu.</span><span class="sxs-lookup"><span data-stu-id="83f88-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="83f88-110">Consultez son blog à l’adresse [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="83f88-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="hashtable-as-a-collection-of-things"></a><span data-ttu-id="83f88-111">Table de hachage comme collection d’objets</span><span class="sxs-lookup"><span data-stu-id="83f88-111">Hashtable as a collection of things</span></span>

<span data-ttu-id="83f88-112">J’aimerais vous présenter tout d’abord le concept de **table de hachage** comme collection dans la définition traditionnelle d’une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="83f88-112">I want you to first see a **Hashtable** as a collection in the traditional definition of a hashtable.</span></span> <span data-ttu-id="83f88-113">Cette définition vous donne une compréhension fondamentale de la façon dont les tables de hachage fonctionnent quand elles sont utilisées ultérieurement pour des éléments plus avancés.</span><span class="sxs-lookup"><span data-stu-id="83f88-113">This definition gives you a fundamental understanding of how they work when they get used for more advanced stuff later.</span></span> <span data-ttu-id="83f88-114">Omettre cette définition constitue souvent une source de confusion.</span><span class="sxs-lookup"><span data-stu-id="83f88-114">Skipping this understanding is often a source of confusion.</span></span>

## <a name="what-is-an-array"></a><span data-ttu-id="83f88-115">Qu’est-ce qu’un tableau ?</span><span class="sxs-lookup"><span data-stu-id="83f88-115">What is an array?</span></span>

<span data-ttu-id="83f88-116">Avant de passer à la définition d’une **table de hachage**, examinons d’abord les [tableaux][].</span><span class="sxs-lookup"><span data-stu-id="83f88-116">Before I jump into what a **Hashtable** is, I need to mention [arrays][] first.</span></span> <span data-ttu-id="83f88-117">Dans le cadre de cette discussion, un tableau est une liste ou une collection de valeurs ou d’objets.</span><span class="sxs-lookup"><span data-stu-id="83f88-117">For the purpose of this discussion, an array is a list or collection of values or objects.</span></span>

```powershell
$array = @(1,2,3,5,7,11)
```

<span data-ttu-id="83f88-118">Une fois que vous avez placé vos éléments dans un tableau, vous pouvez utiliser `foreach` pour effectuer une itération au sein de la liste, ou utiliser un index pour accéder à des éléments individuels du tableau.</span><span class="sxs-lookup"><span data-stu-id="83f88-118">Once you have your items into an array, you can either use `foreach` to iterate over the list or use an index to access individual elements in the array.</span></span>

```powershell
foreach($item in $array)
{
    Write-Output $item
}

Write-Output $array[3]
```

<span data-ttu-id="83f88-119">Vous pouvez de la même façon mettre à jour les valeurs à l’aide d’un index.</span><span class="sxs-lookup"><span data-stu-id="83f88-119">You can also update values using an index in the same way.</span></span>

```powershell
$array[2] = 13
```

<span data-ttu-id="83f88-120">Je n’ai fait qu’effleurer le concept des tableaux, mais cela devrait les placer dans le contexte approprié au moment d’aborder les tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="83f88-120">I just scratched the surface on arrays but that should put them into the right context as I move onto hashtables.</span></span>

## <a name="what-is-a-hashtable"></a><span data-ttu-id="83f88-121">Qu’est-ce qu’une table de hachage ?</span><span class="sxs-lookup"><span data-stu-id="83f88-121">What is a hashtable?</span></span>

<span data-ttu-id="83f88-122">Je commencerai par une description technique de base de ce que sont les tables de hachage, d’une manière générale, avant de passer aux autres méthodes utilisées par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83f88-122">I'm going to start with a basic technical description of what hashtables are, in the general sense, before I shift into the other ways PowerShell uses them.</span></span>

<span data-ttu-id="83f88-123">Une table de hachage est une structure de données, à l’instar d’un tableau, sauf que vous stockez chaque valeur (objet) à l’aide d’une clé.</span><span class="sxs-lookup"><span data-stu-id="83f88-123">A hashtable is a data structure, much like an array, except you store each value (object) using a key.</span></span> <span data-ttu-id="83f88-124">Il s’agit d’un magasin de clés/valeurs de base.</span><span class="sxs-lookup"><span data-stu-id="83f88-124">It's a basic key/value store.</span></span> <span data-ttu-id="83f88-125">Commençons par créer une table de hachage vide.</span><span class="sxs-lookup"><span data-stu-id="83f88-125">First, we create an empty hashtable.</span></span>

```powershell
$ageList = @{}
```

<span data-ttu-id="83f88-126">Notez que des accolades, et non des parenthèses, servent à définir une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="83f88-126">Notice that braces, instead of parentheses, are used to define a hashtable.</span></span> <span data-ttu-id="83f88-127">Ajoutons ensuite un élément à l’aide d’une clé comme celle-ci :</span><span class="sxs-lookup"><span data-stu-id="83f88-127">Then we add an item using a key like this:</span></span>

```powershell
$key = 'Kevin'
$value = 36
$ageList.add( $key, $value )

$ageList.add( 'Alex', 9 )
```

<span data-ttu-id="83f88-128">Le nom de la personne représente la clé, et son âge correspond à la valeur que je souhaite enregistrer.</span><span class="sxs-lookup"><span data-stu-id="83f88-128">The person's name is the key and their age is the value that I want to save.</span></span>

## <a name="using-the-brackets-for-access"></a><span data-ttu-id="83f88-129">Utilisation de crochets pour l’accès</span><span class="sxs-lookup"><span data-stu-id="83f88-129">Using the brackets for access</span></span>

<span data-ttu-id="83f88-130">Après avoir ajouté vos valeurs à la table de hachage, vous pouvez les extraire à l’aide de cette même clé (au lieu d’utiliser un index numérique comme vous le feriez pour un tableau).</span><span class="sxs-lookup"><span data-stu-id="83f88-130">Once you add your values to the hashtable, you can pull them back out using that same key (instead of using a numeric index like you would have for an array).</span></span>

```powershell
$ageList['Kevin']
$ageList['Alex']
```

<span data-ttu-id="83f88-131">Pour connaître l’âge de Kevin, j’utilise son nom pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="83f88-131">When I want Kevin's age, I use his name to access it.</span></span> <span data-ttu-id="83f88-132">Nous pouvons également utiliser cette approche pour ajouter ou mettre à jour des valeurs dans la table de hachage,</span><span class="sxs-lookup"><span data-stu-id="83f88-132">We can use this approach to add or update values into the hashtable too.</span></span> <span data-ttu-id="83f88-133">exactement comme si vous utilisiez la fonction `add()` ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="83f88-133">This is just like using the `add()` function above.</span></span>

```powershell
$ageList = @{}

$key = 'Kevin'
$value = 36
$ageList[$key] = $value

$ageList['Alex'] = 9
```

<span data-ttu-id="83f88-134">Vous pouvez utiliser une autre syntaxe pour accéder et mettre à jour les valeurs que je couvrirai dans une section ultérieure.</span><span class="sxs-lookup"><span data-stu-id="83f88-134">There's another syntax you can use for accessing and updating values that I'll cover in a later section.</span></span> <span data-ttu-id="83f88-135">Si vous passez à PowerShell à partir d’un autre langage, ces exemples devraient vous rappeler la façon dont vous utilisiez les tables de hachage auparavant.</span><span class="sxs-lookup"><span data-stu-id="83f88-135">If you're coming to PowerShell from another language, these examples should fit in with how you may have used hashtables before.</span></span>

### <a name="creating-hashtables-with-values"></a><span data-ttu-id="83f88-136">Création de tables de hachage avec des valeurs</span><span class="sxs-lookup"><span data-stu-id="83f88-136">Creating hashtables with values</span></span>

<span data-ttu-id="83f88-137">Jusqu’à présent, j’ai créé une table de hachage vide pour ces exemples.</span><span class="sxs-lookup"><span data-stu-id="83f88-137">So far I've created an empty hashtable for these examples.</span></span> <span data-ttu-id="83f88-138">Vous pouvez préremplir les clés et les valeurs lors de leur création.</span><span class="sxs-lookup"><span data-stu-id="83f88-138">You can pre-populate the keys and values when you create them.</span></span>

```powershell
$ageList = @{
    Kevin = 36
    Alex  = 9
}
```

### <a name="as-a-lookup-table"></a><span data-ttu-id="83f88-139">Comme table de recherche</span><span class="sxs-lookup"><span data-stu-id="83f88-139">As a lookup table</span></span>

<span data-ttu-id="83f88-140">Ce type de table de hachage est particulièrement utile en tant que table de recherche.</span><span class="sxs-lookup"><span data-stu-id="83f88-140">The real value of this type of a hashtable is that you can use them as a lookup table.</span></span> <span data-ttu-id="83f88-141">Voici un exemple simple.</span><span class="sxs-lookup"><span data-stu-id="83f88-141">Here is a simple example.</span></span>

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}

$server = $environments[$env]
```

<span data-ttu-id="83f88-142">Dans cet exemple, vous spécifiez un environnement pour la variable `$env`, et celle-ci choisit le serveur approprié.</span><span class="sxs-lookup"><span data-stu-id="83f88-142">In this example, you specify an environment for the `$env` variable and it will pick the correct server.</span></span> <span data-ttu-id="83f88-143">Vous pouvez utiliser un élément `switch($env){...}` pour une sélection comme celle-ci, mais une table de hachage est une option intéressante.</span><span class="sxs-lookup"><span data-stu-id="83f88-143">You could use a `switch($env){...}` for a selection like this but a hashtable is a nice option.</span></span>

<span data-ttu-id="83f88-144">Les avantages sont encore plus visibles quand vous générez dynamiquement la table de recherche en vue d’une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="83f88-144">This gets even better when you dynamically build the lookup table to use it later.</span></span> <span data-ttu-id="83f88-145">Par conséquent, privilégiez cette approche lorsque vous avez besoin de référencer quelque chose.</span><span class="sxs-lookup"><span data-stu-id="83f88-145">So think about using this approach when you need to cross reference something.</span></span> <span data-ttu-id="83f88-146">Je pense que les résultats seraient encore plus évidents si PowerShell ne filtrait pas de façon si efficace le canal avec `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="83f88-146">I think we would see this even more if PowerShell wasn't so good at filtering on the pipe with `Where-Object`.</span></span> <span data-ttu-id="83f88-147">Si vous vous retrouvez dans une situation où les performances sont importantes, cette approche doit être prise en compte.</span><span class="sxs-lookup"><span data-stu-id="83f88-147">If you're ever in a situation where performance matters, this approach needs to be considered.</span></span>

<span data-ttu-id="83f88-148">Je ne dis pas qu’elle est plus rapide, mais elle s’adapte à la règle [Si les performances l’exigent, effectuez un test][].</span><span class="sxs-lookup"><span data-stu-id="83f88-148">I won't say that it's faster, but it does fit into the rule of [If performance matters, test it][].</span></span>

#### <a name="multiselection"></a><span data-ttu-id="83f88-149">Sélection multiple</span><span class="sxs-lookup"><span data-stu-id="83f88-149">Multiselection</span></span>

<span data-ttu-id="83f88-150">En général, considérez une table de hachage comme une paire clé/valeur dans laquelle vous fournissez une clé pour obtenir une valeur.</span><span class="sxs-lookup"><span data-stu-id="83f88-150">Generally, you think of a hashtable as a key/value pair, where you provide one key and get one value.</span></span> <span data-ttu-id="83f88-151">PowerShell vous permet de fournir un tableau de clés pour obtenir plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="83f88-151">PowerShell allows you to provide an array of keys to get multiple values.</span></span>

```powershell
$environments[@('QA','DEV')]
$environments[('QA','DEV')]
$environments['QA','DEV']
```

<span data-ttu-id="83f88-152">Dans cet exemple, j’utilise la même table de hachage de recherche que ci-dessus et je fournis trois styles de tableaux différents pour obtenir les correspondances.</span><span class="sxs-lookup"><span data-stu-id="83f88-152">In this example, I use the same lookup hashtable from above and provide three different array styles to get the matches.</span></span> <span data-ttu-id="83f88-153">Il s’agit d’une fonction secrète de PowerShell que la plupart des utilisateurs ignorent.</span><span class="sxs-lookup"><span data-stu-id="83f88-153">This is a hidden gem in PowerShell that most people aren't aware of.</span></span>

## <a name="iterating-hashtables"></a><span data-ttu-id="83f88-154">Itérations de tables de hachage</span><span class="sxs-lookup"><span data-stu-id="83f88-154">Iterating hashtables</span></span>

<span data-ttu-id="83f88-155">Étant donné qu’une table de hachage est une collection de paires clé/valeur, vous pouvez effectuer une itération différemment de celle d’un tableau ou d’une liste d’éléments standard.</span><span class="sxs-lookup"><span data-stu-id="83f88-155">Because a hashtable is a collection of key/value pairs, you iterate over it differently than you do for an array or a normal list of items.</span></span>

<span data-ttu-id="83f88-156">La première chose à noter est que si vous dirigez votre table de hachage, le canal le traite comme un objet,</span><span class="sxs-lookup"><span data-stu-id="83f88-156">The first thing to notice is that if you pipe your hashtable, the pipe treats it like one object.</span></span>

```powershell
PS> $ageList | Measure-Object
count : 1
```

<span data-ttu-id="83f88-157">même si la propriété `.count` vous indique le nombre de valeurs qu’elle contient.</span><span class="sxs-lookup"><span data-stu-id="83f88-157">Even though the `.count` property tells you how many values it contains.</span></span>

```powershell
PS> $ageList.count
2
```

<span data-ttu-id="83f88-158">Pour résoudre ce problème, utilisez la propriété `.values` si vous n’avez besoin que des valeurs.</span><span class="sxs-lookup"><span data-stu-id="83f88-158">You get around this issue by using the `.values` property if all you need is just the values.</span></span>

```powershell
PS> $ageList.values | Measure-Object -Average
Count   : 2
Average : 22.5
```

<span data-ttu-id="83f88-159">Il est souvent plus utile d’énumérer les clés et de les utiliser pour accéder aux valeurs.</span><span class="sxs-lookup"><span data-stu-id="83f88-159">It's often more useful to enumerate the keys and use them to access the values.</span></span>

```powershell
PS> $ageList.keys | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_, $ageList[$_]
    Write-Output $message
}
Kevin is 36 years old
Alex is 9 years old
```

<span data-ttu-id="83f88-160">Voici le même exemple avec une boucle `foreach(){...}`.</span><span class="sxs-lookup"><span data-stu-id="83f88-160">Here is the same example with a `foreach(){...}` loop.</span></span>

```powershell
foreach($key in $ageList.keys)
{
    $message = '{0} is {1} years old' -f $key, $ageList[$key]
    Write-Output $message
}
```

<span data-ttu-id="83f88-161">Nous allons parcourir chaque clé de la table de hachage, puis l’utiliser pour accéder à la valeur.</span><span class="sxs-lookup"><span data-stu-id="83f88-161">We are walking each key in the hashtable and then using it to access the value.</span></span> <span data-ttu-id="83f88-162">Il s’agit d’un modèle courant lors de l’utilisation de tables de hachage en tant que collection.</span><span class="sxs-lookup"><span data-stu-id="83f88-162">This is a common pattern when working with hashtables as a collection.</span></span>

### <a name="getenumerator"></a><span data-ttu-id="83f88-163">GetEnumerator()</span><span class="sxs-lookup"><span data-stu-id="83f88-163">GetEnumerator()</span></span>

<span data-ttu-id="83f88-164">Cela nous amène à l’instruction `GetEnumerator()`, qui permet d’effectuer une itération dans notre table de hachage.</span><span class="sxs-lookup"><span data-stu-id="83f88-164">That brings us to `GetEnumerator()` for iterating over our hashtable.</span></span>

```powershell
$ageList.GetEnumerator() | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_.key, $_.value
    Write-Output $message
}
```

<span data-ttu-id="83f88-165">L’énumérateur vous fournit chaque paire clé/valeur, l’une après l’autre.</span><span class="sxs-lookup"><span data-stu-id="83f88-165">The enumerator gives you each key/value pair one after another.</span></span> <span data-ttu-id="83f88-166">Il a été conçu spécifiquement pour ce cas d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="83f88-166">It was designed specifically for this use case.</span></span> <span data-ttu-id="83f88-167">Je tiens à remercier [Mark Kraus](https://get-PowerShellblog.blogspot.com) de m’avoir rappelé ce point.</span><span class="sxs-lookup"><span data-stu-id="83f88-167">Thank you to [Mark Kraus](https://get-PowerShellblog.blogspot.com) for reminding me of this one.</span></span>

### <a name="badenumeration"></a><span data-ttu-id="83f88-168">BadEnumeration</span><span class="sxs-lookup"><span data-stu-id="83f88-168">BadEnumeration</span></span>

<span data-ttu-id="83f88-169">Un détail important est que vous ne pouvez pas modifier une opération de hachage pendant son énumération.</span><span class="sxs-lookup"><span data-stu-id="83f88-169">One important detail is that you can't modify a hashtable while it's being enumerated.</span></span> <span data-ttu-id="83f88-170">Si nous commençons par notre exemple `$environments` de base :</span><span class="sxs-lookup"><span data-stu-id="83f88-170">If we start with our basic `$environments` example:</span></span>

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}
```

<span data-ttu-id="83f88-171">Toute tentative de définition de chaque clé avec la même valeur de serveur échoue.</span><span class="sxs-lookup"><span data-stu-id="83f88-171">And trying to set every key to the same server value fails.</span></span>

```powershell
$environments.Keys | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}

An error occurred while enumerating through a collection: Collection was modified; enumeration operation may not execute.
+ CategoryInfo          : InvalidOperation: tableEnumerator:HashtableEnumerator) [], RuntimeException
+ FullyQualifiedErrorId : BadEnumeration
```

<span data-ttu-id="83f88-172">C’est également le cas même s’il semble que l’opération va réussir :</span><span class="sxs-lookup"><span data-stu-id="83f88-172">This will also fail even though it looks like it should also be fine:</span></span>

```powershell
foreach($key in $environments.keys) {
    $environments[$key] = 'SrvDev03'
}

Collection was modified; enumeration operation may not execute.
    + CategoryInfo          : OperationStopped: (:) [], InvalidOperationException
    + FullyQualifiedErrorId : System.InvalidOperationException
```

<span data-ttu-id="83f88-173">dans cette situation, l’astuce consiste à cloner les clés avant d’effectuer l’énumération.</span><span class="sxs-lookup"><span data-stu-id="83f88-173">The trick to this situation is to clone the keys before doing the enumeration.</span></span>

```powershell
$environments.Keys.Clone() | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}
```

## <a name="hashtable-as-a-collection-of-properties"></a><span data-ttu-id="83f88-174">Table de hachage comme collection de propriétés</span><span class="sxs-lookup"><span data-stu-id="83f88-174">Hashtable as a collection of properties</span></span>

<span data-ttu-id="83f88-175">Jusqu’à présent, tous les types d’objets que nous avons placés dans la table de hachage étaient identiques.</span><span class="sxs-lookup"><span data-stu-id="83f88-175">So far the type of objects we placed in our hashtable were all the same type of object.</span></span> <span data-ttu-id="83f88-176">J’ai utilisé des âges dans tous ces exemples, et la clé était le nom de la personne.</span><span class="sxs-lookup"><span data-stu-id="83f88-176">I used ages in all those examples and the key was the person's name.</span></span> <span data-ttu-id="83f88-177">C’est une excellente méthode lorsque les objets de votre collection portent tous un nom.</span><span class="sxs-lookup"><span data-stu-id="83f88-177">This is a great way to look at it when your collection of objects each have a name.</span></span> <span data-ttu-id="83f88-178">Une autre façon courante d’utiliser des tables de hachage dans PowerShell consiste à conserver une collection de propriétés où la clé est le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="83f88-178">Another common way to use hashtables in PowerShell is to hold a collection of properties where the key is the name of the property.</span></span> <span data-ttu-id="83f88-179">Nous allons aborder ce concept dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="83f88-179">I'll step into that idea in this next example.</span></span>

### <a name="property-based-access"></a><span data-ttu-id="83f88-180">Accès basé sur les propriétés</span><span class="sxs-lookup"><span data-stu-id="83f88-180">Property-based access</span></span>

<span data-ttu-id="83f88-181">L’utilisation de l’accès basé sur les propriétés modifie la dynamique des tables de hachage et la manière dont vous pouvez les utiliser dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83f88-181">The use of property-based access changes the dynamics of hashtables and how you can use them in PowerShell.</span></span> <span data-ttu-id="83f88-182">Voici un exemple standard dans lequel les clés sont traitées comme des propriétés.</span><span class="sxs-lookup"><span data-stu-id="83f88-182">Here is our usual example from above treating the keys as properties.</span></span>

```powershell
$ageList = @{}
$ageList.Kevin = 35
$ageList.Alex = 9
```

<span data-ttu-id="83f88-183">Comme les exemples ci-dessus, cet exemple ajoute ces clés s’ils n’existent pas déjà dans la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="83f88-183">Just like the examples above, this example adds those keys if they don't exist in the hashtable already.</span></span> <span data-ttu-id="83f88-184">Selon la façon dont vous avez défini vos clés et ce que représentent vos valeurs, cette méthode peut générer un résultat quelque peu étrange ou parfait.</span><span class="sxs-lookup"><span data-stu-id="83f88-184">Depending on how you defined your keys and what your values are, this is either a little strange or a perfect fit.</span></span> <span data-ttu-id="83f88-185">L’exemple de liste d’âges a fonctionné jusqu’à ce stade.</span><span class="sxs-lookup"><span data-stu-id="83f88-185">The age list example has worked great up until this point.</span></span> <span data-ttu-id="83f88-186">Nous avons besoin d’un nouvel exemple pour que cela continue de fonctionner.</span><span class="sxs-lookup"><span data-stu-id="83f88-186">We need a new example for this to feel right going forward.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
```

<span data-ttu-id="83f88-187">Nous pouvons ajouter des attributs et y accéder au niveau de `$person`.</span><span class="sxs-lookup"><span data-stu-id="83f88-187">And we can add and access attributes on the `$person` like this.</span></span>

```powershell
$person.city = 'Austin'
$person.state = 'TX'
```

<span data-ttu-id="83f88-188">Et soudain, cette table de hachage commence à ressembler à un véritable objet.</span><span class="sxs-lookup"><span data-stu-id="83f88-188">All of a sudden this hashtable starts to feel and act like an object.</span></span> <span data-ttu-id="83f88-189">Mais il s’agit toujours d’un ensemble de choses, et tous les exemples ci-dessus continueront donc de s’appliquer.</span><span class="sxs-lookup"><span data-stu-id="83f88-189">It's still a collection of things, so all the examples above still apply.</span></span> <span data-ttu-id="83f88-190">Nous nous plaçons simplement d’un autre point de vue.</span><span class="sxs-lookup"><span data-stu-id="83f88-190">We just approach it from a different point of view.</span></span>

### <a name="checking-for-keys-and-values"></a><span data-ttu-id="83f88-191">Recherche de clés et de valeurs</span><span class="sxs-lookup"><span data-stu-id="83f88-191">Checking for keys and values</span></span>

<span data-ttu-id="83f88-192">Dans la plupart des cas, vous pouvez simplement tester la valeur avec un nom semblable à celui-ci :</span><span class="sxs-lookup"><span data-stu-id="83f88-192">In most cases, you can just test for the value with something like this:</span></span>

```powershell
if( $person.age ){...}
```

<span data-ttu-id="83f88-193">Bien que simple, cette méthode est une source de nombreuses erreurs pour moi car j’ai négligé un détail important dans ma logique.</span><span class="sxs-lookup"><span data-stu-id="83f88-193">It's simple but has been the source of many bugs for me because I was overlooking one important detail in my logic.</span></span> <span data-ttu-id="83f88-194">J’ai commencé à l’utiliser pour vérifier la présence d’une clé.</span><span class="sxs-lookup"><span data-stu-id="83f88-194">I started to use it to test if a key was present.</span></span> <span data-ttu-id="83f88-195">Lorsque la valeur était `$false` ou égale à zéro, cette instruction retournait `$false` de manière inattendue.</span><span class="sxs-lookup"><span data-stu-id="83f88-195">When the value was `$false` or zero, that statement would return `$false` unexpectedly.</span></span>

```powershell
if( $person.age -ne $null ){...}
```

<span data-ttu-id="83f88-196">Cette méthode contourne ce problème pour les valeurs zéro, mais pas pour les clés $null et inexistantes.</span><span class="sxs-lookup"><span data-stu-id="83f88-196">This works around that issue for zero values but not $null vs non-existent keys.</span></span> <span data-ttu-id="83f88-197">La plupart du temps, vous n’avez pas besoin de faire cette distinction, mais il existe des fonctions où cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="83f88-197">Most of the time you don't need to make that distinction but there are functions for when you do.</span></span>

```powershell
if( $person.ContainsKey('age') ){...}
```

<span data-ttu-id="83f88-198">Nous disposons également d’une instruction `ContainsValue()` pour le cas où vous devez tester une valeur sans connaître la clé ou itérer l’intégralité de la collection.</span><span class="sxs-lookup"><span data-stu-id="83f88-198">We also have a `ContainsValue()` for the situation where you need to test for a value without knowing the key or iterating the whole collection.</span></span>

### <a name="removing-and-clearing-keys"></a><span data-ttu-id="83f88-199">Suppression et effacement de clés</span><span class="sxs-lookup"><span data-stu-id="83f88-199">Removing and clearing keys</span></span>

<span data-ttu-id="83f88-200">Vous pouvez supprimer des clés à l’aide de la fonction `.Remove()`.</span><span class="sxs-lookup"><span data-stu-id="83f88-200">You can remove keys with the `.Remove()` function.</span></span>

```powershell
$person.remove('age')
```

<span data-ttu-id="83f88-201">L’attribution d’une valeur `$null` a des clés vous laisse une seule clé avec une valeur `$null`.</span><span class="sxs-lookup"><span data-stu-id="83f88-201">Assigning them a `$null` value just leaves you with a key that has a `$null` value.</span></span>

<span data-ttu-id="83f88-202">Une méthode courante pour effacer une table de hachage consiste à l’initialiser simplement afin d’obtenir une table de hachage vide.</span><span class="sxs-lookup"><span data-stu-id="83f88-202">A common way to clear a hashtable is to just initialize it to an empty hashtable.</span></span>

```powershell
$person = @{}
```

<span data-ttu-id="83f88-203">Bien que cela fonctionne, essayez plutôt d’utiliser la fonction `clear()`.</span><span class="sxs-lookup"><span data-stu-id="83f88-203">While that does work, try to use the `clear()` function instead.</span></span>

```powershell
$person.clear()
```

<span data-ttu-id="83f88-204">Il s’agit de l’une des instances où l’utilisation de la fonction crée du code autodocumenté et rend les intentions du code très claires.</span><span class="sxs-lookup"><span data-stu-id="83f88-204">This is one of those instances where using the function creates self-documenting code and it makes the intentions of the code very clean.</span></span>

## <a name="all-the-fun-stuff"></a><span data-ttu-id="83f88-205">Amusons-nous un peu</span><span class="sxs-lookup"><span data-stu-id="83f88-205">All the fun stuff</span></span>

### <a name="ordered-hashtables"></a><span data-ttu-id="83f88-206">Tables de hachage ordonnées</span><span class="sxs-lookup"><span data-stu-id="83f88-206">Ordered hashtables</span></span>

<span data-ttu-id="83f88-207">Par défaut, les tables de hachage ne sont pas ordonnées (ou triées).</span><span class="sxs-lookup"><span data-stu-id="83f88-207">By default, hashtables aren't ordered (or sorted).</span></span> <span data-ttu-id="83f88-208">Dans le contexte traditionnel, l’ordre n’a pas d’importance lorsque vous utilisez toujours une clé pour accéder aux valeurs.</span><span class="sxs-lookup"><span data-stu-id="83f88-208">In the traditional context, the order doesn't matter when you always use a key to access values.</span></span> <span data-ttu-id="83f88-209">Vous souhaiterez peut-être conserver les propriétés dans l’ordre dans lequel vous les définissez.</span><span class="sxs-lookup"><span data-stu-id="83f88-209">You may find that you want the properties to stay in the order that you define them.</span></span> <span data-ttu-id="83f88-210">Heureusement, il existe un moyen de le faire grâce au mot clé `ordered`.</span><span class="sxs-lookup"><span data-stu-id="83f88-210">Thankfully, there's a way to do that with the `ordered` keyword.</span></span>

```powershell
$person = [ordered]@{
    name = 'Kevin'
    age  = 36
}
```

<span data-ttu-id="83f88-211">Désormais, lorsque vous énumérez les clés et les valeurs, elles restent dans cet ordre.</span><span class="sxs-lookup"><span data-stu-id="83f88-211">Now when you enumerate the keys and values, they stay in that order.</span></span>

### <a name="inline-hashtables"></a><span data-ttu-id="83f88-212">Tables de hachage en ligne</span><span class="sxs-lookup"><span data-stu-id="83f88-212">Inline hashtables</span></span>

<span data-ttu-id="83f88-213">Lorsque vous définissez une table de hachage sur une ligne, vous pouvez séparer les paires clé/valeur par un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="83f88-213">When you're defining a hashtable on one line, you can separate the key/value pairs with a semicolon.</span></span>

```powershell
$person = @{ name = 'kevin'; age = 36; }
```

<span data-ttu-id="83f88-214">Cela s’avère pratique si vous les créez sur le canal.</span><span class="sxs-lookup"><span data-stu-id="83f88-214">This will come in handy if you're creating them on the pipe.</span></span>

### <a name="custom-expressions-in-common-pipeline-commands"></a><span data-ttu-id="83f88-215">Expressions personnalisées dans les commandes de pipeline courantes</span><span class="sxs-lookup"><span data-stu-id="83f88-215">Custom expressions in common pipeline commands</span></span>

<span data-ttu-id="83f88-216">Il existe quelques applets de commande qui prennent en charge l’utilisation de tables de hachage pour créer des propriétés personnalisées ou calculées.</span><span class="sxs-lookup"><span data-stu-id="83f88-216">There are a few cmdlets that support the use of hashtables to create custom or calculated properties.</span></span> <span data-ttu-id="83f88-217">C’est généralement le cas avec `Select-Object` et `Format-Table`.</span><span class="sxs-lookup"><span data-stu-id="83f88-217">You commonly see this with `Select-Object` and `Format-Table`.</span></span> <span data-ttu-id="83f88-218">Les tables de hachage comportent une syntaxe spéciale qui ressemble à celle-ci lorsqu’elle est entièrement développée.</span><span class="sxs-lookup"><span data-stu-id="83f88-218">The hashtables have a special syntax that looks like this when fully expanded.</span></span>

```powershell
$property = @{
    name = 'totalSpaceGB'
    expression = { ($_.used + $_.free) / 1GB }
}
```

<span data-ttu-id="83f88-219">`name` correspond à la façon dont l’applet de commande étiquetterait cette colonne.</span><span class="sxs-lookup"><span data-stu-id="83f88-219">The `name` is what the cmdlet would label that column.</span></span> <span data-ttu-id="83f88-220">`expression` est un bloc de script exécuté où `$_` est la valeur de l’objet sur le canal.</span><span class="sxs-lookup"><span data-stu-id="83f88-220">The `expression` is a script block that is executed where `$_` is the value of the object on the pipe.</span></span> <span data-ttu-id="83f88-221">Voici ce script en action :</span><span class="sxs-lookup"><span data-stu-id="83f88-221">Here is that script in action:</span></span>

```powershell
$drives = Get-PSDrive | Where Used
$drives | Select-Object -Properties name, $property

Name     totalSpaceGB
----     ------------
C    238.472652435303
```

<span data-ttu-id="83f88-222">Je l’ai placé dans une variable, mais il peut être facilement défini en ligne et vous pouvez raccourcir `name` en `n` et `expression` en `e` à cette étape.</span><span class="sxs-lookup"><span data-stu-id="83f88-222">I placed that in a variable but it could easily be defined inline and you can shorten `name` to `n` and `expression` to `e` while you're at it.</span></span>

```powershell
$drives | Select-Object -properties name, @{n='totalSpaceGB';e={($_.used + $_.free) / 1GB}}
```

<span data-ttu-id="83f88-223">Personnellement, je trouve ces commandes un peut trop longues et sources de comportements erronés sur lesquels je ne m’étendrai pas.</span><span class="sxs-lookup"><span data-stu-id="83f88-223">I personally don't like how long that makes commands and it often promotes some bad behaviors that I won't get into.</span></span> <span data-ttu-id="83f88-224">Je préfère créer une table de hachage ou `pscustomobject` avec tous les champs et propriétés souhaités, au lieu d’utiliser cette approche dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="83f88-224">I'm more likely to create a new hashtable or `pscustomobject` with all the fields and properties that I want instead of using this approach in scripts.</span></span> <span data-ttu-id="83f88-225">Mais il existe beaucoup de codes capables de le faire, et je tenais à vous en informer.</span><span class="sxs-lookup"><span data-stu-id="83f88-225">But there's a lot of code out there that does this so I wanted you to be aware of it.</span></span> <span data-ttu-id="83f88-226">Je parlerai de la création d’un objet `pscustomobject` un peu plus tard.</span><span class="sxs-lookup"><span data-stu-id="83f88-226">I talk about creating a `pscustomobject` later on.</span></span>

### <a name="custom-sort-expression"></a><span data-ttu-id="83f88-227">Expression de tri personnalisée</span><span class="sxs-lookup"><span data-stu-id="83f88-227">Custom sort expression</span></span>

<span data-ttu-id="83f88-228">Vous pouvez facilement trier une collection si les objets contiennent les données que vous souhaitez trier.</span><span class="sxs-lookup"><span data-stu-id="83f88-228">It's easy to sort a collection if the objects have the data that you want to sort on.</span></span> <span data-ttu-id="83f88-229">Vous pouvez soit ajouter les données à l’objet avant de les trier, soit créer une expression personnalisée pour `Sort-Object`.</span><span class="sxs-lookup"><span data-stu-id="83f88-229">You can either add the data to the object before you sort it or create a custom expression for `Sort-Object`.</span></span>

```powershell
Get-ADUser | Sort-Object -Parameter @{ e={ Get-TotalSales $_.Name } }
```

<span data-ttu-id="83f88-230">Dans cet exemple, je prends une liste d’utilisateurs et j’utilise une applet de commande personnalisée pour obtenir des informations supplémentaires uniquement à des fins de tri.</span><span class="sxs-lookup"><span data-stu-id="83f88-230">In this example I'm taking a list of users and using some custom cmdlet to get additional information just for the sort.</span></span>

#### <a name="sort-a-list-of-hashtables"></a><span data-ttu-id="83f88-231">Trier une liste de tables de hachage</span><span class="sxs-lookup"><span data-stu-id="83f88-231">Sort a list of Hashtables</span></span>

<span data-ttu-id="83f88-232">Si vous souhaitez trier une liste de tables de hachage, vous constaterez que `Sort-Object` ne traite pas vos clés comme des propriétés.</span><span class="sxs-lookup"><span data-stu-id="83f88-232">If you have a list of hashtables that you want to sort, you'll find that the `Sort-Object` doesn't treat your keys as properties.</span></span> <span data-ttu-id="83f88-233">Nous pouvons contourner ce problème à l’aide d’une expression de tri personnalisée.</span><span class="sxs-lookup"><span data-stu-id="83f88-233">We can get a round that by using a custom sort expression.</span></span>

```powershell
$data = @(
    @{name='a'}
    @{name='c'}
    @{name='e'}
    @{name='f'}
    @{name='d'}
    @{name='b'}
)

$data | Sort-Object -Property @{e={$_.name}}
```

## <a name="splatting-hashtables-at-cmdlets"></a><span data-ttu-id="83f88-234">Projection de tables de hachage au niveau d’applets de commande</span><span class="sxs-lookup"><span data-stu-id="83f88-234">Splatting hashtables at cmdlets</span></span>

<span data-ttu-id="83f88-235">C’est l’un de mes aspects préférés concernant les tables de hachage, et beaucoup d’utilisateurs n’en sont pas tout de suite conscients.</span><span class="sxs-lookup"><span data-stu-id="83f88-235">This is one of my favorite things about hashtables that many people don't discover early on.</span></span>
<span data-ttu-id="83f88-236">L’idée est que, au lieu de fournir toutes les propriétés à une applet de commande sur une seule ligne, vous pouvez d’abord les empaqueter dans une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="83f88-236">The idea is that instead of providing all the properties to a cmdlet on one line, you can instead pack them into a hashtable first.</span></span> <span data-ttu-id="83f88-237">Vous pouvez ensuite fournir la table de hachage à la fonction d’une façon spéciale.</span><span class="sxs-lookup"><span data-stu-id="83f88-237">Then you can give the hashtable to the function in a special way.</span></span>
<span data-ttu-id="83f88-238">Voici un exemple de création d’une étendue DHCP de manière normale.</span><span class="sxs-lookup"><span data-stu-id="83f88-238">Here is an example of creating a DHCP scope the normal way.</span></span>

```powershell
Add-DhcpServerv4Scope -Name 'TestNetwork' -StartRange'10.0.0.2' -EndRange '10.0.0.254' -SubnetMask '255.255.255.0' -Description 'Network for testlab A' -LeaseDuration (New-TimeSpan -Days 8) -Type "Both"
```

<span data-ttu-id="83f88-239">Si vous n’utilisez aucune [projection][], tous ces éléments doivent être définis sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="83f88-239">Without using [splatting][], all those things need to be defined on a single line.</span></span> <span data-ttu-id="83f88-240">Cela permet de faire défiler l’écran ou d’encapsuler les éléments là où vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="83f88-240">It either scrolls off the screen or will wrap where ever it feels like.</span></span> <span data-ttu-id="83f88-241">Comparez maintenant cela à une commande qui utilise la projection.</span><span class="sxs-lookup"><span data-stu-id="83f88-241">Now compare that to a command that uses splatting.</span></span>

```powershell
$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    SubnetMask  = '255.255.255.0'
    Description = 'Network for testlab A'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}
Add-DhcpServerv4Scope @DHCPScope
```

<span data-ttu-id="83f88-242">L’utilisation du signe `@` à la place de `$` appelle l’opération de projection.</span><span class="sxs-lookup"><span data-stu-id="83f88-242">The use of the `@` sign instead of the `$` is what invokes the splat operation.</span></span>

<span data-ttu-id="83f88-243">Prenez quelques instants pour apprécier la lisibilité de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="83f88-243">Just take a moment to appreciate how easy that example is to read.</span></span> <span data-ttu-id="83f88-244">Cette commande est identique pour toutes les valeurs.</span><span class="sxs-lookup"><span data-stu-id="83f88-244">They are the exact same command with all the same values.</span></span> <span data-ttu-id="83f88-245">La deuxième est plus facile à comprendre et à gérer à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="83f88-245">The second one is easier to understand and maintain going forward.</span></span>

<span data-ttu-id="83f88-246">J’utilise la projection chaque fois que la commande devient trop longue.</span><span class="sxs-lookup"><span data-stu-id="83f88-246">I use splatting anytime the command gets too long.</span></span> <span data-ttu-id="83f88-247">Trop longue signifie que je dois faire défiler la fenêtre vers la droite.</span><span class="sxs-lookup"><span data-stu-id="83f88-247">I define too long as causing my window to scroll right.</span></span> <span data-ttu-id="83f88-248">Si j’atteins trois propriétés pour une fonction, il est probable que je les réécrive à l’aide d’une table de hachage projetée.</span><span class="sxs-lookup"><span data-stu-id="83f88-248">If I hit three properties for a function, odds are that I'll rewrite it using a splatted hashtable.</span></span>

### <a name="splatting-for-optional-parameters"></a><span data-ttu-id="83f88-249">Projection de paramètres optionnels</span><span class="sxs-lookup"><span data-stu-id="83f88-249">Splatting for optional parameters</span></span>

<span data-ttu-id="83f88-250">L’une des méthodes les plus courantes d’utilisation de la projection consiste à gérer des paramètres facultatifs provenant d’autres emplacements dans mon script.</span><span class="sxs-lookup"><span data-stu-id="83f88-250">One of the most common ways I use splatting is to deal with optional parameters that come from some place else in my script.</span></span> <span data-ttu-id="83f88-251">Imaginons une fonction qui encapsule un appel `Get-CIMInstance` avec un argument `$Credential` facultatif.</span><span class="sxs-lookup"><span data-stu-id="83f88-251">Let's say I have a function that wraps a `Get-CIMInstance` call that has an optional `$Credential` argument.</span></span>

```powershell
$CIMParams = @{
    ClassName = 'Win32_Bios'
    ComputerName = $ComputerName
}

if($Credential)
{
    $CIMParams.Credential = $Credential
}

Get-CIMInstance @CIMParams
```

<span data-ttu-id="83f88-252">Je commence par créer ma table de hachage avec des paramètres communs.</span><span class="sxs-lookup"><span data-stu-id="83f88-252">I start by creating my hashtable with common parameters.</span></span> <span data-ttu-id="83f88-253">Puis j’ajoute l’élément `$Credential`, s’il existe.</span><span class="sxs-lookup"><span data-stu-id="83f88-253">Then I add the `$Credential` if it exists.</span></span>
<span data-ttu-id="83f88-254">Comme j’utilise ici la projection, je n’ai besoin de l’appel à `Get-CIMInstance` dans mon code qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="83f88-254">Because I'm using splatting here, I only need to have the call to `Get-CIMInstance` in my code once.</span></span> <span data-ttu-id="83f88-255">Ce modèle de conception est très clair et permet de gérer facilement un grand nombre de paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="83f88-255">This design pattern is very clean and can handle lots of optional parameters easily.</span></span>

<span data-ttu-id="83f88-256">Pour être honnête, vous pouvez écrire vos commandes et autoriser ainsi des valeurs `$null` dans les paramètres.</span><span class="sxs-lookup"><span data-stu-id="83f88-256">To be fair, you could write your commands to allow `$null` values for parameters.</span></span> <span data-ttu-id="83f88-257">Vous n’avez tout simplement pas le contrôle sur les autres commandes que vous appelez.</span><span class="sxs-lookup"><span data-stu-id="83f88-257">You just don't always have control over the other commands you're calling.</span></span>

### <a name="multiple-splats"></a><span data-ttu-id="83f88-258">Projections multiples</span><span class="sxs-lookup"><span data-stu-id="83f88-258">Multiple splats</span></span>

<span data-ttu-id="83f88-259">Vous pouvez projeter plusieurs tables de hachage dans la même applet de commande.</span><span class="sxs-lookup"><span data-stu-id="83f88-259">You can splat multiple hashtables to the same cmdlet.</span></span> <span data-ttu-id="83f88-260">Si nous revenons à notre exemple de projection d’origine :</span><span class="sxs-lookup"><span data-stu-id="83f88-260">If we revisit our original splatting example:</span></span>

```powershell
$Common = @{
    SubnetMask  = '255.255.255.0'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}

$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    Description = 'Network for testlab A'
}

Add-DhcpServerv4Scope @DHCPScope @Common
```

<span data-ttu-id="83f88-261">Je vais utiliser cette méthode avec un ensemble commun de paramètres que je passe à un grand nombre de commandes.</span><span class="sxs-lookup"><span data-stu-id="83f88-261">I'll use this method when I have a common set of parameters that I'm passing to lots of commands.</span></span>

### <a name="splatting-for-clean-code"></a><span data-ttu-id="83f88-262">Projection pour un code propre</span><span class="sxs-lookup"><span data-stu-id="83f88-262">Splatting for clean code</span></span>

<span data-ttu-id="83f88-263">Vous pouvez tout à fait effectuer une projection d’un seul paramètre si vous améliorez le code.</span><span class="sxs-lookup"><span data-stu-id="83f88-263">There's nothing wrong with splatting a single parameter if makes you code cleaner.</span></span>

```powershell
$log = @{Path = '.\logfile.log'}
Add-Content "logging this command" @log
```

### <a name="splatting-executables"></a><span data-ttu-id="83f88-264">Projection d’exécutables</span><span class="sxs-lookup"><span data-stu-id="83f88-264">Splatting executables</span></span>

<span data-ttu-id="83f88-265">La projection fonctionne également sur certains exécutables qui utilisent une syntaxe de type `/param:value`.</span><span class="sxs-lookup"><span data-stu-id="83f88-265">Splatting also works on some executables that use a `/param:value` syntax.</span></span> <span data-ttu-id="83f88-266">`Robocopy.exe`, par exemple, possède des paramètres tels que celui-ci.</span><span class="sxs-lookup"><span data-stu-id="83f88-266">`Robocopy.exe`, for example, has some parameters like this.</span></span>

```powershell
$robo = @{R=1;W=1;MT=8}
robocopy source destination @robo
```

<span data-ttu-id="83f88-267">J’ignore si tout cela est vraiment utile, mais c’est assez intéressant.</span><span class="sxs-lookup"><span data-stu-id="83f88-267">I don't know that this is all that useful, but I found it interesting.</span></span>

## <a name="adding-hashtables"></a><span data-ttu-id="83f88-268">Ajout de tables de hachage</span><span class="sxs-lookup"><span data-stu-id="83f88-268">Adding hashtables</span></span>

<span data-ttu-id="83f88-269">Les tables de hachage prennent en charge l’opérateur d’addition pour combiner deux tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="83f88-269">Hashtables support the addition operator to combine two hashtables.</span></span>

```powershell
$person += @{Zip = '78701'}
```

<span data-ttu-id="83f88-270">Cette approche fonctionne uniquement si les deux tables de hachage ne partagent aucune clé.</span><span class="sxs-lookup"><span data-stu-id="83f88-270">This only works if the two hashtables don't share a key.</span></span>

## <a name="nested-hashtables"></a><span data-ttu-id="83f88-271">Tables de hachage imbriquées</span><span class="sxs-lookup"><span data-stu-id="83f88-271">Nested hashtables</span></span>

<span data-ttu-id="83f88-272">Nous pouvons utiliser des tables de hachage comme valeurs à l’intérieur d’une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="83f88-272">We can use hashtables as values inside a hashtable.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
$person.location = @{}
$person.location.city = 'Austin'
$person.location.state = 'TX'
```

<span data-ttu-id="83f88-273">J’ai commencé avec une table de hachage de base contenant deux clés.</span><span class="sxs-lookup"><span data-stu-id="83f88-273">I started with a basic hashtable containing two keys.</span></span> <span data-ttu-id="83f88-274">J’ai ajouté une clé nommée `location` avec une table de hachage vide.</span><span class="sxs-lookup"><span data-stu-id="83f88-274">I added a key called `location` with an empty hashtable.</span></span> <span data-ttu-id="83f88-275">J’ai ensuite ajouté les deux derniers éléments à cette table de hachage `location`.</span><span class="sxs-lookup"><span data-stu-id="83f88-275">Then I added the last two items to that `location` hashtable.</span></span> <span data-ttu-id="83f88-276">Nous pouvons également effectuer toute cette procédure en ligne.</span><span class="sxs-lookup"><span data-stu-id="83f88-276">We can do this all inline too.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
    location = @{
        city  = 'Austin'
        state = 'TX'
    }
}
```

<span data-ttu-id="83f88-277">Cela crée la même table de hachage que celle que nous étudiée ci-dessus et nous pouvons accéder aux propriétés de la même façon.</span><span class="sxs-lookup"><span data-stu-id="83f88-277">This creates the same hashtable that we saw above and can access the properties the same way.</span></span>

```powershell
$person.location.city
Austin
```

<span data-ttu-id="83f88-278">Il existe de nombreuses façons d’aborder la structure de vos objets.</span><span class="sxs-lookup"><span data-stu-id="83f88-278">There are many ways to approach the structure of your objects.</span></span> <span data-ttu-id="83f88-279">Voici une deuxième façon de regarder une table de hachage imbriquée.</span><span class="sxs-lookup"><span data-stu-id="83f88-279">Here is a second way to look at a nested hashtable.</span></span>

```powershell
$people = @{
    Kevin = @{
        age  = 36
        city = 'Austin'
    }
    Alex = @{
        age  = 9
        city = 'Austin'
    }
}
```

<span data-ttu-id="83f88-280">Cette méthode combine le concept d’utilisation de tables de hachage comme une collection d’objets et une collection de propriétés.</span><span class="sxs-lookup"><span data-stu-id="83f88-280">This mixes the concept of using hashtables as a collection of objects and a collection of properties.</span></span> <span data-ttu-id="83f88-281">Les valeurs restent facilement accessibles, même lorsqu’elles sont imbriquées à l’aide de l’approche de votre choix.</span><span class="sxs-lookup"><span data-stu-id="83f88-281">The values are still easy to access even when they're nested using whatever approach you prefer.</span></span>

```powershell
PS> $people.kevin.age
36
PS> $people.kevin['city']
Austin
PS> $people['Alex'].age
9
PS> $people['Alex']['City']
Austin
```

<span data-ttu-id="83f88-282">J’ai tendance à utiliser la propriété dot lorsque je la traite comme une propriété.</span><span class="sxs-lookup"><span data-stu-id="83f88-282">I tend to use the dot property when I'm treating it like a property.</span></span> <span data-ttu-id="83f88-283">Il s’agit généralement d’éléments qui me viennent à l’esprit et que j’ai définis de manière statique dans mon code.</span><span class="sxs-lookup"><span data-stu-id="83f88-283">Those are generally things I've defined statically in my code and I know them off the top of my head.</span></span> <span data-ttu-id="83f88-284">Si je dois parcourir la liste ou accéder par programmation aux clés, j’utilise les crochets pour fournir le nom de la clé.</span><span class="sxs-lookup"><span data-stu-id="83f88-284">If I need to walk the list or programmatically access the keys, I use the brackets to provide the key name.</span></span>

```powershell
foreach($name in $people.keys)
{
    $person = $people[$name]
    '{0}, age {1}, is in {2}' -f $name, $person.age, $person.city
}
```

<span data-ttu-id="83f88-285">La possibilité d’imbriquer des tables de hachage vous offre beaucoup de flexibilité et d’options.</span><span class="sxs-lookup"><span data-stu-id="83f88-285">Having the ability to nest hashtables gives you a lot of flexibility and options.</span></span>

### <a name="looking-at-nested-hashtables"></a><span data-ttu-id="83f88-286">Examen des tables de hachage imbriquées</span><span class="sxs-lookup"><span data-stu-id="83f88-286">Looking at nested hashtables</span></span>

<span data-ttu-id="83f88-287">Dès que vous commencez à imbriquer des tables de hachage, vous aurez besoin d’une méthode simple pour les examiner à partir de la console.</span><span class="sxs-lookup"><span data-stu-id="83f88-287">As soon as you start nesting hashtables, you're going to need an easy way to look at them from the console.</span></span> <span data-ttu-id="83f88-288">Si je sélectionne la dernière table de hachage, j’obtiens une sortie semblable à celle-ci :</span><span class="sxs-lookup"><span data-stu-id="83f88-288">If I take that last hashtable, I get an output that looks like this and it only goes so deep:</span></span>

```powershell
PS> $people
Name                           Value
----                           -----
Kevin                          {age, city}
Alex                           {age, city}
```

<span data-ttu-id="83f88-289">Ma commande préférée pour examiner ces éléments est `ConvertTo-JSON` car elle est très claire, et j’utilise fréquemment JSON pour d’autres choses.</span><span class="sxs-lookup"><span data-stu-id="83f88-289">My go to command for looking at these things is `ConvertTo-JSON` because it's very clean and I frequently use JSON on other things.</span></span>

```powershell
PS> $people | ConvertTo-Json
{
    "Kevin":  {
                "age":  36,
                "city":  "Austin"
            },
    "Alex":  {
                "age":  9,
                "city":  "Austin"
            }
}
```

<span data-ttu-id="83f88-290">Même si vous ne connaissez pas JSON, vous devriez trouver ce que vous recherchez.</span><span class="sxs-lookup"><span data-stu-id="83f88-290">Even if you don't know JSON, you should be able to see what you're looking for.</span></span> <span data-ttu-id="83f88-291">Il existe une commande `Format-Custom` pour les données structurées comme celle-ci, mais je préfère néanmoins la méthode JSON.</span><span class="sxs-lookup"><span data-stu-id="83f88-291">There's a `Format-Custom` command for structured data like this but I still like the JSON view better.</span></span>

## <a name="creating-objects"></a><span data-ttu-id="83f88-292">Création d'objets</span><span class="sxs-lookup"><span data-stu-id="83f88-292">Creating objects</span></span>

<span data-ttu-id="83f88-293">Parfois, vous n’avez besoin que d’un objet, et utiliser une table de hachage pour y conserver des propriétés ne répond pas à vos besoins.</span><span class="sxs-lookup"><span data-stu-id="83f88-293">Sometimes you just need to have an object and using a hashtable to hold properties just isn't getting the job done.</span></span> <span data-ttu-id="83f88-294">Le plus souvent, vous souhaitez afficher les clés en tant que noms de colonne.</span><span class="sxs-lookup"><span data-stu-id="83f88-294">Most commonly you want to see the keys as column names.</span></span> <span data-ttu-id="83f88-295">C’est facile avec l’élément `pscustomobject`.</span><span class="sxs-lookup"><span data-stu-id="83f88-295">A `pscustomobject` makes that easy.</span></span>

```powershell
$person = [pscustomobject]@{
    name = 'Kevin'
    age  = 36
}

$person

name  age
----  ---
Kevin  36
```

<span data-ttu-id="83f88-296">Même si vous ne le créez pas en tant que `pscustomobject` initialement, vous pouvez toujours le convertir ultérieurement si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="83f88-296">Even if you don't create it as a `pscustomobject` initially, you can always cast it later when needed.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}

[pscustomobject]$person

name  age
----  ---
Kevin  36
```

<span data-ttu-id="83f88-297">J’ai déjà écrit un article détaillé concernant [pscustomobject][], que vous je vous conseille de lire après celui-ci.</span><span class="sxs-lookup"><span data-stu-id="83f88-297">I already have detailed write-up for [pscustomobject][] that you should go read after this one.</span></span> <span data-ttu-id="83f88-298">Il s’appuie sur un grand nombre des éléments appris ici.</span><span class="sxs-lookup"><span data-stu-id="83f88-298">It builds on a lot of the things learned here.</span></span>

## <a name="reading-and-writing-hashtables-to-file"></a><span data-ttu-id="83f88-299">Lecture et écriture de tables de hachage dans un fichier</span><span class="sxs-lookup"><span data-stu-id="83f88-299">Reading and writing hashtables to file</span></span>

### <a name="saving-to-csv"></a><span data-ttu-id="83f88-300">Enregistrement au format CSV</span><span class="sxs-lookup"><span data-stu-id="83f88-300">Saving to CSV</span></span>

<span data-ttu-id="83f88-301">L’utilisation d’une table de hachage pour l’enregistrement au format CSV est l’un des problèmes auquel je faisais référence ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="83f88-301">Struggling with getting a hashtable to save to a CSV is one of the difficulties that I was referring to above.</span></span> <span data-ttu-id="83f88-302">Convertissez votre table de hachage en un objet `pscustomobject` afin de l’enregistrer correctement au format CSV.</span><span class="sxs-lookup"><span data-stu-id="83f88-302">Convert your hashtable to a `pscustomobject` and it will save correctly to CSV.</span></span> <span data-ttu-id="83f88-303">Cela vous permet de commencer avec un objet `pscustomobject` en préservant l’ordre des colonnes.</span><span class="sxs-lookup"><span data-stu-id="83f88-303">It helps if you start with a `pscustomobject` so the column order is preserved.</span></span> <span data-ttu-id="83f88-304">Mais vous pouvez le convertir en un objet `pscustomobject` en ligne, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="83f88-304">But you can cast it to a `pscustomobject` inline if needed.</span></span>

```powershell
$person | ForEach-Object{ [pscustomobject]$_ } | Export-CSV -Path $path
```

<span data-ttu-id="83f88-305">Là encore, consultez mon article sur utilisation d’un objet [pscustomobject][].</span><span class="sxs-lookup"><span data-stu-id="83f88-305">Again, check out my write-up on using a [pscustomobject][].</span></span>

### <a name="saving-a-nested-hashtable-to-file"></a><span data-ttu-id="83f88-306">Enregistrement d’une table de hachage imbriquée dans un fichier</span><span class="sxs-lookup"><span data-stu-id="83f88-306">Saving a nested hashtable to file</span></span>

<span data-ttu-id="83f88-307">Si j’ai besoin d’enregistrer une table de hachage imbriquée dans un fichier, puis de la lire à nouveau, j’utilise pour cela les applets de commande JSON.</span><span class="sxs-lookup"><span data-stu-id="83f88-307">If I need to save a nested hashtable to a file and then read it back in again, I use the JSON cmdlets to do it.</span></span>

```powershell
$people | ConvertTo-JSON | Set-Content -Path $path
$people = Get-Content -Path $path -Raw | ConvertFrom-JSON
```

<span data-ttu-id="83f88-308">Il existe deux points importants à noter concernant cette méthode.</span><span class="sxs-lookup"><span data-stu-id="83f88-308">There are two important points about this method.</span></span> <span data-ttu-id="83f88-309">Tout d’abord, l’objet JSON est écrit en mode multiligne et je dois donc utiliser l’option `-Raw` pour le relire dans une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="83f88-309">First is that the JSON is written out multiline so I need to use the `-Raw` option to read it back into a single string.</span></span> <span data-ttu-id="83f88-310">Deuxièmement, l’objet importé n’est plus un objet `[hashtable]`.</span><span class="sxs-lookup"><span data-stu-id="83f88-310">The Second is that the imported object is no longer a `[hashtable]`.</span></span> <span data-ttu-id="83f88-311">C’est maintenant un objet `[pscustomobject]` et cela peut provoquer des problèmes si vous ne vous y attendiez pas.</span><span class="sxs-lookup"><span data-stu-id="83f88-311">It's now a `[pscustomobject]` and that can cause issues if you don't expect it.</span></span>

<span data-ttu-id="83f88-312">Observez les tables de hachage profondément imbriquées.</span><span class="sxs-lookup"><span data-stu-id="83f88-312">Watch for deeply-nested hashtables.</span></span> <span data-ttu-id="83f88-313">Lorsque vous les convertissez en JSON, vous risquez de ne pas obtenir les résultats attendus.</span><span class="sxs-lookup"><span data-stu-id="83f88-313">When you convert it to JSON you might not get the results you expect.</span></span>

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json

{
  "a": {
    "b": {
      "c": "System.Collections.Hashtable"
    }
  }
}
```

<span data-ttu-id="83f88-314">Utilisez le paramètre **Depth** pour vous assurer que vous avez développé toutes les tables de hachage imbriquées.</span><span class="sxs-lookup"><span data-stu-id="83f88-314">Use **Depth** parameter to ensure that you have expanded all the nested hashtables.</span></span>

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json -Depth 3

{
  "a": {
    "b": {
      "c": {
        "d": "e"
      }
    }
  }
}
```

<span data-ttu-id="83f88-315">Si vous avez besoin d’un objet `[hashtable]` lors de l’importation, vous devez utiliser les commandes `Export-CliXml` et `Import-CliXml`.</span><span class="sxs-lookup"><span data-stu-id="83f88-315">If you need it to be a `[hashtable]` on import, then you need to use the `Export-CliXml` and `Import-CliXml` commands.</span></span>

### <a name="converting-json-to-hashtable"></a><span data-ttu-id="83f88-316">Conversion d’un objet JSON en table de hachage</span><span class="sxs-lookup"><span data-stu-id="83f88-316">Converting JSON to Hashtable</span></span>

<span data-ttu-id="83f88-317">Si vous avez besoin de convertir un objet JSON en `[hashtable]`, vous pouvez utiliser [JavaScriptSerializer][] dans .NET.</span><span class="sxs-lookup"><span data-stu-id="83f88-317">If you need to convert JSON to a `[hashtable]`, there's one way that I know of to do it with the [JavaScriptSerializer][] in .NET.</span></span>

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Web.Script.Serialization")
$JSSerializer = [System.Web.Script.Serialization.JavaScriptSerializer]::new()
$JSSerializer.Deserialize($json,'Hashtable')
```

<span data-ttu-id="83f88-318">À compter de PowerShell v6, la prise en charge de JSON utilise JSON.NET NewtonSoft et ajoute la prise en charge de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="83f88-318">Beginning in PowerShell v6, JSON support uses the NewtonSoft JSON.NET and adds hashtable support.</span></span>

```powershell
'{ "a": "b" }' | ConvertFrom-Json -AsHashtable

Name      Value
----      -----
a         b
```

<span data-ttu-id="83f88-319">PowerShell 6.2 a ajouté le paramètre **Depth** à `ConvertFrom-Json`.</span><span class="sxs-lookup"><span data-stu-id="83f88-319">PowerShell 6.2 added the **Depth** parameter to `ConvertFrom-Json`.</span></span> <span data-ttu-id="83f88-320">La valeur par défaut de **Depth** est 1024.</span><span class="sxs-lookup"><span data-stu-id="83f88-320">The default **Depth** is 1024.</span></span>

### <a name="reading-directly-from-a-file"></a><span data-ttu-id="83f88-321">Lecture directe à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="83f88-321">Reading directly from a file</span></span>

<span data-ttu-id="83f88-322">Si vous utilisez un fichier contenant une table de hachage avec la syntaxe PowerShell, il existe un moyen de l’importer directement.</span><span class="sxs-lookup"><span data-stu-id="83f88-322">If you have a file that contains a hashtable using PowerShell syntax, there's a way to import it directly.</span></span>

```powershell
$content = Get-Content -Path $Path -Raw -ErrorAction Stop
$scriptBlock = [scriptblock]::Create( $content )
$scriptBlock.CheckRestrictedLanguage( $allowedCommands, $allowedVariables, $true )
$hashtable = ( & $scriptBlock )
```

<span data-ttu-id="83f88-323">Cette procédure importe le contenu du fichier dans un objet `scriptblock`, puis vérifie s’il n’existe pas d’autres commandes PowerShell avant de l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="83f88-323">It imports the contents of the file into a `scriptblock`, then checks to make sure it doesn't have any other PowerShell commands in it before it executes it.</span></span>

<span data-ttu-id="83f88-324">Saviez-vous qu’un manifeste de module (fichier psd1) n’est en fait qu’une simple table de hachage ?</span><span class="sxs-lookup"><span data-stu-id="83f88-324">On that note, did you know that a module manifest (the psd1 file) is just a hashtable?</span></span>

## <a name="keys-can-be-any-object"></a><span data-ttu-id="83f88-325">Les clés peuvent être n’importe quel objet</span><span class="sxs-lookup"><span data-stu-id="83f88-325">Keys can be any object</span></span>

<span data-ttu-id="83f88-326">La plupart du temps, les clés sont simplement des chaînes.</span><span class="sxs-lookup"><span data-stu-id="83f88-326">Most of the time, the keys are just strings.</span></span> <span data-ttu-id="83f88-327">Nous pouvons donc entourer de guillemets l’élément de notre choix pour le transformer en clé.</span><span class="sxs-lookup"><span data-stu-id="83f88-327">So we can put quotes around anything and make it a key.</span></span>

```powershell
$person = @{
    'full name' = 'Kevin Marquette'
    '#' = 3978
}
$person['full name']
```

<span data-ttu-id="83f88-328">Vous pouvez ainsi créer des éléments très particuliers dont vous n’aviez probablement même pas idée.</span><span class="sxs-lookup"><span data-stu-id="83f88-328">You can do some odd things that you may not have realized you could do.</span></span>

```powershell
$person.'full name'

$key = 'full name'
$person.$key
```

<span data-ttu-id="83f88-329">Mais ce n’est pas parce que vous pouvez réaliser quelque chose que vous devez nécessaire le faire.</span><span class="sxs-lookup"><span data-stu-id="83f88-329">Just because you can do something, it doesn't mean that you should.</span></span> <span data-ttu-id="83f88-330">Ce dernier exemple semble clairement annoncer qu’une erreur va se produire et risque d’être facilement mal interprété par quiconque lira votre code.</span><span class="sxs-lookup"><span data-stu-id="83f88-330">That last one just looks like a bug waiting to happen and would be easily misunderstood by anyone reading your code.</span></span>

<span data-ttu-id="83f88-331">Techniquement, votre clé ne doit pas nécessairement être une chaîne, mais les opérations sont bien plus simples à réaliser si vous utilisez uniquement des chaînes.</span><span class="sxs-lookup"><span data-stu-id="83f88-331">Technically your key doesn't have to be a string but they're easier to think about if you only use strings.</span></span> <span data-ttu-id="83f88-332">Toutefois, l’indexation ne fonctionne pas correctement avec les clés complexes.</span><span class="sxs-lookup"><span data-stu-id="83f88-332">However, indexing doesn't work well with the complex keys.</span></span>

```powershell
$ht = @{ @(1,2,3) = "a" }
$ht

Name                           Value
----                           -----
{1, 2, 3}                      a
```

<span data-ttu-id="83f88-333">L’accès à une valeur dans la table de hachage par sa clé ne fonctionne pas toujours.</span><span class="sxs-lookup"><span data-stu-id="83f88-333">Accessing a value in the hashtable by its key doesn't always work.</span></span> <span data-ttu-id="83f88-334">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="83f88-334">For example:</span></span>

```powershell
$key = $ht.keys[0]
$ht.$($key)
a
$ht[$key]
a
```

<span data-ttu-id="83f88-335">Quand la clé est un tableau, vous devez wrapper la variable `$key` dans une sous-expression afin qu’elle puisse être utilisée avec la notation d’accès au membre (`.`).</span><span class="sxs-lookup"><span data-stu-id="83f88-335">When the key is an array, you must wrap the `$key` variable in a subexpression so that it can be used with member access (`.`) notation.</span></span> <span data-ttu-id="83f88-336">Vous pouvez utiliser la notation d’index de tableau (`[]`).</span><span class="sxs-lookup"><span data-stu-id="83f88-336">Or, you can use array index (`[]`) notation.</span></span>

## <a name="use-in-automatic-variables"></a><span data-ttu-id="83f88-337">Utilisation dans des variables automatiques</span><span class="sxs-lookup"><span data-stu-id="83f88-337">Use in automatic variables</span></span>

### <a name="psboundparameters"></a><span data-ttu-id="83f88-338">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="83f88-338">$PSBoundParameters</span></span>

<span data-ttu-id="83f88-339">[$PSBoundParameters][] est une variable automatique qui n’existe que dans le contexte d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="83f88-339">[$PSBoundParameters][] is an automatic variable that only exists inside the context of a function.</span></span>
<span data-ttu-id="83f88-340">Elle contient tous les paramètres avec lesquels la fonction a été appelée.</span><span class="sxs-lookup"><span data-stu-id="83f88-340">It contains all the parameters that the function was called with.</span></span> <span data-ttu-id="83f88-341">Il ne s’agit pas exactement d’une table de hachage, mais elle y ressemble suffisamment pour la traiter en tant que telle.</span><span class="sxs-lookup"><span data-stu-id="83f88-341">This isn't exactly a hashtable but close enough that you can treat it like one.</span></span>

<span data-ttu-id="83f88-342">Cela comprend la suppression des clés et leur projection dans d’autres fonctions.</span><span class="sxs-lookup"><span data-stu-id="83f88-342">That includes removing keys and splatting it to other functions.</span></span> <span data-ttu-id="83f88-343">Si vous écrivez des fonctions de proxy, examinez cette variable plus en détail.</span><span class="sxs-lookup"><span data-stu-id="83f88-343">If you find yourself writing proxy functions, take a closer look at this one.</span></span>

<span data-ttu-id="83f88-344">Pour plus d'informations, consultez [about_Automatic_Variables][].</span><span class="sxs-lookup"><span data-stu-id="83f88-344">See [about_Automatic_Variables][] for more details.</span></span>

### <a name="psboundparameters-gotcha"></a><span data-ttu-id="83f88-345">Astuce PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="83f88-345">PSBoundParameters gotcha</span></span>

<span data-ttu-id="83f88-346">Une chose importante à retenir est que cette variable comprend uniquement les valeurs passées en tant que paramètres.</span><span class="sxs-lookup"><span data-stu-id="83f88-346">One important thing to remember is that this only includes the values that are passed in as parameters.</span></span> <span data-ttu-id="83f88-347">Si vous utilisez également des paramètres avec des valeurs par défaut, mais qui ne sont pas transmises par l’appelant, `$PSBoundParameters` ne contient pas ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="83f88-347">If you also have parameters with default values but aren't passed in by the caller, `$PSBoundParameters` doesn't contain those values.</span></span> <span data-ttu-id="83f88-348">Cet aspect est souvent négligé.</span><span class="sxs-lookup"><span data-stu-id="83f88-348">This is commonly overlooked.</span></span>

### <a name="psdefaultparametervalues"></a><span data-ttu-id="83f88-349">$PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="83f88-349">$PSDefaultParameterValues</span></span>

<span data-ttu-id="83f88-350">Cette variable automatique vous permet d’attribuer des valeurs par défaut à une applet de commande sans la modifier.</span><span class="sxs-lookup"><span data-stu-id="83f88-350">This automatic variable lets you assign default values to any cmdlet without changing the cmdlet.</span></span>
<span data-ttu-id="83f88-351">Prenons cet exemple :</span><span class="sxs-lookup"><span data-stu-id="83f88-351">Take a look at this example.</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "UTF8"
```

<span data-ttu-id="83f88-352">Cette variable ajoute une entrée à la table de hachage `$PSDefaultParameterValues` qui définit `UTF8` comme valeur par défaut pour le paramètre `Out-File -Encoding`.</span><span class="sxs-lookup"><span data-stu-id="83f88-352">This adds an entry to the `$PSDefaultParameterValues` hashtable that sets `UTF8` as the default value for the `Out-File -Encoding` parameter.</span></span> <span data-ttu-id="83f88-353">Ceci est spécifique à la session et vous devez donc la placer dans votre `$profile`.</span><span class="sxs-lookup"><span data-stu-id="83f88-353">This is session-specific so you should place it in your `$profile`.</span></span>

<span data-ttu-id="83f88-354">Je l’utilise souvent pour préattribuer des valeurs que je saisis très souvent.</span><span class="sxs-lookup"><span data-stu-id="83f88-354">I use this often to pre-assign values that I type quite often.</span></span>

```powershell
$PSDefaultParameterValues[ "Connect-VIServer:Server" ] = 'VCENTER01.contoso.local'
```

<span data-ttu-id="83f88-355">Cette méthode accepte également les caractères génériques, ce qui vous permet de définir des valeurs en bloc.</span><span class="sxs-lookup"><span data-stu-id="83f88-355">This also accepts wildcards so you can set values in bulk.</span></span> <span data-ttu-id="83f88-356">Voici d’autres exemples d’utilisation :</span><span class="sxs-lookup"><span data-stu-id="83f88-356">Here are some ways you can use that:</span></span>

```powershell
$PSDefaultParameterValues[ "Get-*:Verbose" ] = $true
$PSDefaultParameterValues[ "*:Credential" ] = Get-Credential
```

<span data-ttu-id="83f88-357">Pour une analyse plus approfondie, reportez-vous à cet article très intéressant sur [Valeurs automatiques par défaut][], écrit par [Michael Sorens][].</span><span class="sxs-lookup"><span data-stu-id="83f88-357">For a more in-depth breakdown, see this great article on [Automatic Defaults][] by [Michael Sorens][].</span></span>

## <a name="regex-matches"></a><span data-ttu-id="83f88-358">Regex $Matches</span><span class="sxs-lookup"><span data-stu-id="83f88-358">Regex $Matches</span></span>

<span data-ttu-id="83f88-359">Lorsque vous utilisez l’opérateur `-match`, une variable automatique appelée `$matches` est créée avec les résultats de la correspondance.</span><span class="sxs-lookup"><span data-stu-id="83f88-359">When you use the `-match` operator, an automatic variable called `$matches` is created with the results of the match.</span></span> <span data-ttu-id="83f88-360">Si votre expression régulière contient des sous-expressions, ces sous-correspondances sont également répertoriées.</span><span class="sxs-lookup"><span data-stu-id="83f88-360">If you have any sub expressions in your regex, those sub matches are also listed.</span></span>

```powershell
$message = 'My SSN is 123-45-6789.'

$message -match 'My SSN is (.+)\.'
$Matches[0]
$Matches[1]
```

### <a name="named-matches"></a><span data-ttu-id="83f88-361">Correspondances nommées</span><span class="sxs-lookup"><span data-stu-id="83f88-361">Named matches</span></span>

<span data-ttu-id="83f88-362">C’est l’une de mes fonctionnalités préférées, et que la plupart des utilisateurs ignorent.</span><span class="sxs-lookup"><span data-stu-id="83f88-362">This is one of my favorite features that most people don't know about.</span></span> <span data-ttu-id="83f88-363">Si vous utilisez une correspondance regex nommée, vous pouvez accéder à cette correspondance en recherchant son nom.</span><span class="sxs-lookup"><span data-stu-id="83f88-363">If you use a named regex match, then you can access that match by name on the matches.</span></span>

```powershell
$message = 'My Name is Kevin and my SSN is 123-45-6789.'

if($message -match 'My Name is (?<Name>.+) and my SSN is (?<SSN>.+)\.')
{
    $Matches.Name
    $Matches.SSN
}
```

<span data-ttu-id="83f88-364">Dans l’exemple ci-dessus, `(?<Name>.*)` est une sous-expression nommée.</span><span class="sxs-lookup"><span data-stu-id="83f88-364">In the example above, the `(?<Name>.*)` is a named sub expression.</span></span> <span data-ttu-id="83f88-365">Cette valeur est ensuite placée dans la propriété `$Matches.Name`.</span><span class="sxs-lookup"><span data-stu-id="83f88-365">This value is then placed in the `$Matches.Name` property.</span></span>

## <a name="group-object--ashashtable"></a><span data-ttu-id="83f88-366">Group-Object -AsHashtable</span><span class="sxs-lookup"><span data-stu-id="83f88-366">Group-Object -AsHashtable</span></span>

<span data-ttu-id="83f88-367">L’une des fonctionnalités les moins connues de `Group-Object` est sa capacité à convertir des jeux de données en une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="83f88-367">One little known feature of `Group-Object` is that it can turn some datasets into a hashtable for you.</span></span>

```powershell
Import-CSV $Path | Group-Object -AsHashtable -Property email
```

<span data-ttu-id="83f88-368">Cette opération ajoute chaque ligne à une table de hachage et utilise la propriété spécifiée comme clé pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="83f88-368">This will add each row into a hashtable and use the specified property as the key to access it.</span></span>

## <a name="copying-hashtables"></a><span data-ttu-id="83f88-369">Copie de tables de hachage</span><span class="sxs-lookup"><span data-stu-id="83f88-369">Copying Hashtables</span></span>

<span data-ttu-id="83f88-370">Il est important de savoir que les tables de hachage sont des objets.</span><span class="sxs-lookup"><span data-stu-id="83f88-370">One important thing to know is that hashtables are objects.</span></span> <span data-ttu-id="83f88-371">Et chaque variable est simplement une référence à un objet.</span><span class="sxs-lookup"><span data-stu-id="83f88-371">And each variable is just a reference to an object.</span></span> <span data-ttu-id="83f88-372">Cela signifie qu’une copie valide d’une table de hachage demande plus de travail.</span><span class="sxs-lookup"><span data-stu-id="83f88-372">This means that it takes more work to make a valid copy of a hashtable.</span></span>

### <a name="assigning-reference-types"></a><span data-ttu-id="83f88-373">Attribution de types de références</span><span class="sxs-lookup"><span data-stu-id="83f88-373">Assigning reference types</span></span>

<span data-ttu-id="83f88-374">Quand vous avez une table de hachage et que vous l’attribuez à une deuxième variable, les deux variables pointent vers la même table de hachage.</span><span class="sxs-lookup"><span data-stu-id="83f88-374">When you have one hashtable and assign it to a second variable, both variables point to the same hashtable.</span></span>

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [copy]
```

<span data-ttu-id="83f88-375">Cela a pour effet de les rendre identiques, car la modification des valeurs dans l’une modifie également les valeurs de l’autre.</span><span class="sxs-lookup"><span data-stu-id="83f88-375">This highlights that they're the same because altering the values in one will also alter the values in the other.</span></span> <span data-ttu-id="83f88-376">Cela s’applique également lors du passage de tables de hachage dans d’autres fonctions.</span><span class="sxs-lookup"><span data-stu-id="83f88-376">This also applies when passing hashtables into other functions.</span></span> <span data-ttu-id="83f88-377">Si ces fonctions apportent des modifications à cette table de hachage, votre table d’origine est également modifiée.</span><span class="sxs-lookup"><span data-stu-id="83f88-377">If those functions make changes to that hashtable, your original is also altered.</span></span>

### <a name="shallow-copies-single-level"></a><span data-ttu-id="83f88-378">Copies superficielles, niveau unique</span><span class="sxs-lookup"><span data-stu-id="83f88-378">Shallow copies, single level</span></span>

<span data-ttu-id="83f88-379">Si nous utilisons une simple table de hachage telle que notre exemple ci-dessus, nous pouvons utiliser `.Clone()` pour effectuer une copie superficielle.</span><span class="sxs-lookup"><span data-stu-id="83f88-379">If we have a simple hashtable like our example above, we can use `.Clone()` to make a shallow copy.</span></span>

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig.Clone()
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [orig]
```

<span data-ttu-id="83f88-380">Nous pourrons ainsi apporter des modifications de base dans l’une mais sans impacter l’autre.</span><span class="sxs-lookup"><span data-stu-id="83f88-380">This will allow us to make some basic changes to one that don't impact the other.</span></span>

### <a name="shallow-copies-nested"></a><span data-ttu-id="83f88-381">Copies superficielles, imbriquées</span><span class="sxs-lookup"><span data-stu-id="83f88-381">Shallow copies, nested</span></span>

<span data-ttu-id="83f88-382">La raison pour laquelle cette copie est dite superficielle vient du fait qu’elle copie uniquement les propriétés de niveau de base.</span><span class="sxs-lookup"><span data-stu-id="83f88-382">The reason why it's called a shallow copy is because it only copies the base level properties.</span></span> <span data-ttu-id="83f88-383">Si l’une de ces propriétés est un type de référence (par exemple, une autre table de hachage), ces objets imbriqués pointent quand même les uns vers les autres.</span><span class="sxs-lookup"><span data-stu-id="83f88-383">If one of those properties is a reference type (like another hashtable), then those nested objects will still point to each other.</span></span>

```powershell
PS> $orig = @{
        person=@{
            name='orig'
        }
    }
PS> $copy = $orig.Clone()
PS> $copy.person.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.person.name
PS> 'Orig: [{0}]' -f $orig.person.name

Copy: [copy]
Orig: [copy]
```

<span data-ttu-id="83f88-384">Vous pouvez constater que même si j’ai cloné la table de hachage, la référence à `person` n’a pas été clonée.</span><span class="sxs-lookup"><span data-stu-id="83f88-384">So you can see that even though I cloned the hashtable, the reference to `person` wasn't cloned.</span></span> <span data-ttu-id="83f88-385">Nous devons effectuer une copie complète pour obtenir véritablement une seconde table de hachage non liée à la première.</span><span class="sxs-lookup"><span data-stu-id="83f88-385">We need to make a deep copy to truly have a second hashtable that isn't linked to the first.</span></span>

### <a name="deep-copies"></a><span data-ttu-id="83f88-386">Copies complètes</span><span class="sxs-lookup"><span data-stu-id="83f88-386">Deep copies</span></span>

<span data-ttu-id="83f88-387">Il existe deux façons d’effectuer une copie complète d’une table de hachage (et de la conserver en tant que telle).</span><span class="sxs-lookup"><span data-stu-id="83f88-387">There are a couple of ways to make a deep copy of a hashtable (and keep it as a hashtable).</span></span> <span data-ttu-id="83f88-388">Voici une fonction qui utilise PowerShell pour créer de manière récursive une copie complète :</span><span class="sxs-lookup"><span data-stu-id="83f88-388">Here's a function using PowerShell to recursively create a deep copy:</span></span>

```powershell
function Get-DeepClone
{
    [CmdletBinding()]
    param(
        $InputObject
    )
    process
    {
        if($InputObject -is [hashtable]) {
            $clone = @{}
            foreach($key in $InputObject.keys)
            {
                $clone[$key] = Get-DeepClone $InputObject[$key]
            }
            return $clone
        } else {
            return $InputObject
        }
    }
}
```

<span data-ttu-id="83f88-389">Elle ne gère aucun un autre type de référence ou tableau, mais il s’agit d’un bon point de départ.</span><span class="sxs-lookup"><span data-stu-id="83f88-389">It doesn't handle any other reference types or arrays, but it's a good starting point.</span></span>

<span data-ttu-id="83f88-390">Une autre méthode consiste à utiliser .Net pour la désérialiser avec **CliXml** comme dans cette fonction :</span><span class="sxs-lookup"><span data-stu-id="83f88-390">Another way is to use .Net to deserialize it using **CliXml** like in this function:</span></span>

```powershell
function Get-DeepClone
{
    param(
        $InputObject
    )
    $TempCliXmlString = [System.Management.Automation.PSSerializer]::Serialize($obj, [int32]::MaxValue)
    return [System.Management.Automation.PSSerializer]::Deserialize($TempCliXmlString)
}
```

<span data-ttu-id="83f88-391">Pour les tables de hachage extrêmement grandes, la fonction de désérialisation est plus rapide parce qu’elle effectue un scale-out. Toutefois, vous devez tenir compte de certains éléments quand vous utilisez cette méthode.</span><span class="sxs-lookup"><span data-stu-id="83f88-391">For extremely large hashtables, the deserializing function is faster as it scales out. However, there are some things to consider when using this method.</span></span> <span data-ttu-id="83f88-392">Dans la mesure où elle utilise **CliXml**, elle sollicite la mémoire de manière intensive. Donc, si vous clonez d’énormes tables de hachage, cela peut poser problème.</span><span class="sxs-lookup"><span data-stu-id="83f88-392">Since it uses **CliXml**, it's memory intensive and if you are cloning huge hashtables, that might be a problem.</span></span> <span data-ttu-id="83f88-393">Il faut également savoir que **CliXml** a une limite de profondeur de 48.</span><span class="sxs-lookup"><span data-stu-id="83f88-393">Another limitation of the **CliXml** is there is a depth limitation of 48.</span></span> <span data-ttu-id="83f88-394">Cela signifie que si vous avez une table de hachage avec 48 couches de tables de hachage imbriquées, le clonage échoue et aucune table de hachage n’est générée.</span><span class="sxs-lookup"><span data-stu-id="83f88-394">Meaning, if you have a hashtable with 48 layers of nested hashtables, the cloning will fail and no hashtable will be output at all.</span></span>

## <a name="anything-else"></a><span data-ttu-id="83f88-395">Autre chose ?</span><span class="sxs-lookup"><span data-stu-id="83f88-395">Anything else?</span></span>

<span data-ttu-id="83f88-396">J’ai abordé beaucoup de concepts dans cet article.</span><span class="sxs-lookup"><span data-stu-id="83f88-396">I covered a lot of ground quickly.</span></span> <span data-ttu-id="83f88-397">Mon espoir est que vous puissiez apprendre quelque chose de nouveau ou approfondir vos connaissances à chaque lecture de cet article.</span><span class="sxs-lookup"><span data-stu-id="83f88-397">My hope is that you walk away leaning something new or understanding it better every time you read this.</span></span> <span data-ttu-id="83f88-398">Comme j’ai abordé le spectre complet de cette fonctionnalité, certains aspects ne s’appliquent pas à votre cas pour le moment.</span><span class="sxs-lookup"><span data-stu-id="83f88-398">Because I covered the full spectrum of this feature, there are aspects that just may not apply to you right now.</span></span> <span data-ttu-id="83f88-399">C’est tout à fait normal et attendu en fonction du volume du travail que vous effectuez avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83f88-399">That is perfectly OK and is kind of expected depending on how much you work with PowerShell.</span></span>

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[original version]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Tables de hachage]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[hashtables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[Tableaux]: /powershell/module/microsoft.powershell.core/about/about_arrays
[arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Si les performances l’exigent, effectuez un test]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best-Practices/Performance.md
[If performance matters, test it]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best-Practices/Performance.md
[Projection]: /powershell/module/microsoft.powershell.core/about/about_splatting
[splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[pscustomobject]: everything-about-pscustomobject.md
[JavaScriptSerializer]: /dotnet/api/system.web.script.serialization.javascriptserializer?view=netframework-4.8&preserve-view=true
[PSBoundParameters]: https://tommymaynard.com/the-psboundparameters-automatic-variable-2016/
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[Valeurs automatiques par défaut]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Automatic Defaults]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Michael Sorens]: http://cleancode.sourceforge.net/wwwdoc/about.html
