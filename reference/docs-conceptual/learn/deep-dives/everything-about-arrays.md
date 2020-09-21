---
title: Tout ce que vous avez toujours voulu savoir sur les tableaux
description: Les tableaux constituent une fonctionnalité fondamentale de la plupart des langages de programmation.
ms.date: 07/07/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: e744878844a3cfd32d6124538a44a29ba90798ab
ms.sourcegitcommit: 57df49488015e7ac17ff1df402a94441aa6d6064
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "86092097"
---
# <a name="everything-you-wanted-to-know-about-arrays"></a><span data-ttu-id="5eda3-103">Tout ce que vous avez toujours voulu savoir sur les tableaux</span><span class="sxs-lookup"><span data-stu-id="5eda3-103">Everything you wanted to know about arrays</span></span>

<span data-ttu-id="5eda3-104">Les [tableaux][] constituent une fonctionnalité fondamentale de la plupart des langages de programmation.</span><span class="sxs-lookup"><span data-stu-id="5eda3-104">[Arrays][] are a fundamental language feature of most programming languages.</span></span> <span data-ttu-id="5eda3-105">Il s’agit d’une collection de valeurs ou d’objets qu’il est difficile d’éviter.</span><span class="sxs-lookup"><span data-stu-id="5eda3-105">They're a collection of values or objects that are difficult to avoid.</span></span> <span data-ttu-id="5eda3-106">Examinons plus en détails les tableaux et ce qu’ils ont à offrir.</span><span class="sxs-lookup"><span data-stu-id="5eda3-106">Let's take a close look at arrays and everything they have to offer.</span></span>

> [!NOTE]
> <span data-ttu-id="5eda3-107">La [Version d’origine][] de cet article est parue sur le blog écrit par [@KevinMarquette][].</span><span class="sxs-lookup"><span data-stu-id="5eda3-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="5eda3-108">L’équipe PowerShell remercie Kevin d’avoir partagé ce contenu.</span><span class="sxs-lookup"><span data-stu-id="5eda3-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="5eda3-109">Consultez son blog à l’adresse [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="5eda3-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-an-array"></a><span data-ttu-id="5eda3-110">Qu’est-ce qu’un tableau ?</span><span class="sxs-lookup"><span data-stu-id="5eda3-110">What is an array?</span></span>

<span data-ttu-id="5eda3-111">Commençons par une description technique de base des tableaux et de leur utilisation dans la plupart des langages de programmation avant de passer aux autres usages qu’en fait PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5eda3-111">I'm going to start with a basic technical description of what arrays are and how they are used by most programming languages before I shift into the other ways PowerShell makes use of them.</span></span>

<span data-ttu-id="5eda3-112">Un tableau est une structure de données qui sert de collection de plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="5eda3-112">An array is a data structure that serves as a collection of multiple items.</span></span> <span data-ttu-id="5eda3-113">Il est possible de boucler sur le tableau ou d’accéder à certains éléments individuellement à l’aide d’un index.</span><span class="sxs-lookup"><span data-stu-id="5eda3-113">You can iterate over the array or access individual items using an index.</span></span> <span data-ttu-id="5eda3-114">Le tableau est créé sous la forme d’un bloc séquentiel de mémoire dans lequel chaque valeur est stockée juste à côté de l’autre.</span><span class="sxs-lookup"><span data-stu-id="5eda3-114">The array is created as a sequential chunk of memory where each value is stored right next to the other.</span></span>

<span data-ttu-id="5eda3-115">Ces différents détails seront expliqués au fur et à mesure.</span><span class="sxs-lookup"><span data-stu-id="5eda3-115">I'll touch on each of those details as we go.</span></span>

## <a name="basic-usage"></a><span data-ttu-id="5eda3-116">Utilisation de base</span><span class="sxs-lookup"><span data-stu-id="5eda3-116">Basic usage</span></span>

<span data-ttu-id="5eda3-117">Étant donné que les tableaux sont une fonctionnalité de base de PowerShell, il existe une syntaxe simple pour les utiliser dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5eda3-117">Because arrays are such a basic feature of PowerShell, there is a simple syntax for working with them in PowerShell.</span></span>

### <a name="create-an-array"></a><span data-ttu-id="5eda3-118">Création d’un tableau</span><span class="sxs-lookup"><span data-stu-id="5eda3-118">Create an array</span></span>

<span data-ttu-id="5eda3-119">`@()` permet de créer un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="5eda3-119">An empty array can be created by using `@()`</span></span>

```powershell
PS> $data = @()
PS> $data.count
0
```

<span data-ttu-id="5eda3-120">Il est possible de créer un tableau et de l’amorcer avec des valeurs en les plaçant simplement entre les parenthèses `@()`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-120">We can create an array and seed it with values just by placing them in the `@()` parentheses.</span></span>

```powershell
PS> $data = @('Zero','One','Two','Three')
PS> $data.count
4

PS> $data
Zero
One
Two
Three
```

<span data-ttu-id="5eda3-121">Ce tableau contient 4 éléments.</span><span class="sxs-lookup"><span data-stu-id="5eda3-121">This array has 4 items.</span></span> <span data-ttu-id="5eda3-122">Lorsque l’on appelle la variable `$data`, la liste des éléments s’affiche.</span><span class="sxs-lookup"><span data-stu-id="5eda3-122">When we call the `$data` variable, we see the list of our items.</span></span> <span data-ttu-id="5eda3-123">S’il s’agit d’un tableau de chaînes, on obtient une ligne par chaîne.</span><span class="sxs-lookup"><span data-stu-id="5eda3-123">If it's an array of strings, then we get one line per string.</span></span>

<span data-ttu-id="5eda3-124">Le tableau peut être déclaré sur plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="5eda3-124">We can declare an array on multiple lines.</span></span> <span data-ttu-id="5eda3-125">La virgule, facultative dans ce cas, est généralement omise.</span><span class="sxs-lookup"><span data-stu-id="5eda3-125">The comma is optional in this case and generally left out.</span></span>

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
```

<span data-ttu-id="5eda3-126">L’avantage qu’il y a à déclarer les tableaux sur plusieurs lignes</span><span class="sxs-lookup"><span data-stu-id="5eda3-126">I prefer to declare my arrays on multiple lines like that.</span></span> <span data-ttu-id="5eda3-127">est qu’ils sont plus faciles à lire lorsqu’ils comportent plusieurs éléments, ainsi qu’à comparer avec les versions précédentes dans le cadre du contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="5eda3-127">Not only does it get easier to read when you have multiple items, it also makes it easier to compare to previous versions when using source control.</span></span>

#### <a name="other-syntax"></a><span data-ttu-id="5eda3-128">Autre syntaxe</span><span class="sxs-lookup"><span data-stu-id="5eda3-128">Other syntax</span></span>

<span data-ttu-id="5eda3-129">Il est communément admis que `@()` est la syntaxe pour créer un tableau, mais les listes séparées par des virgules fonctionnent la plupart du temps.</span><span class="sxs-lookup"><span data-stu-id="5eda3-129">It's commonly understood that `@()` is the syntax for creating an array, but comma-separated lists work most of the time.</span></span>

```powershell
$data = 'Zero','One','Two','Three'
```

#### <a name="write-output-to-create-arrays"></a><span data-ttu-id="5eda3-130">Write-Output pour créer des tableaux</span><span class="sxs-lookup"><span data-stu-id="5eda3-130">Write-Output to create arrays</span></span>

<span data-ttu-id="5eda3-131">Petite astuce intéressante, vous pouvez utiliser `Write-Output` pour créer rapidement des chaînes au niveau de la console.</span><span class="sxs-lookup"><span data-stu-id="5eda3-131">One cool little trick worth mentioning is that you can use `Write-Output` to quickly create strings at the console.</span></span>

```powershell
$data = Write-Output Zero One Two Three
```

<span data-ttu-id="5eda3-132">C’est pratique, car il n’est pas nécessaire de placer de guillemets autour des chaînes lorsque le paramètre accepte des chaînes.</span><span class="sxs-lookup"><span data-stu-id="5eda3-132">This is handy because you don't have to put quotes around the strings when the parameter accepts strings.</span></span> <span data-ttu-id="5eda3-133">Si cette pratique est clairement à éviter dans un script, elle reste intéressante dans la console.</span><span class="sxs-lookup"><span data-stu-id="5eda3-133">I would never do this in a script but it's fair game in the console.</span></span>

### <a name="accessing-items"></a><span data-ttu-id="5eda3-134">Accès aux éléments</span><span class="sxs-lookup"><span data-stu-id="5eda3-134">Accessing items</span></span>

<span data-ttu-id="5eda3-135">Maintenant que nous disposons d’un tableau contenant des éléments, il s’agit d’accéder à ces éléments et de les mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="5eda3-135">Now that you have an array with items in it, you may want to access and update those items.</span></span>

#### <a name="offset"></a><span data-ttu-id="5eda3-136">Offset</span><span class="sxs-lookup"><span data-stu-id="5eda3-136">Offset</span></span>

<span data-ttu-id="5eda3-137">Pour accéder à des éléments individuels, on utilise les crochets `[]` avec une valeur de décalage commençant à 0.</span><span class="sxs-lookup"><span data-stu-id="5eda3-137">To access individual items, we use the brackets `[]` with an offset value starting at 0.</span></span> <span data-ttu-id="5eda3-138">Voici comment obtenir le premier élément du tableau :</span><span class="sxs-lookup"><span data-stu-id="5eda3-138">This is how we get the first item in our array:</span></span>

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data[0]
Zero
```

<span data-ttu-id="5eda3-139">La raison pour laquelle nous utilisons ici 0 est que le premier élément se trouve au début de la liste, ce qui implique d’employer un décalage de 0 élément pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="5eda3-139">The reason why we use zero here is because the first item is at the beginning of the list so we use an offset of 0 items to get to it.</span></span> <span data-ttu-id="5eda3-140">Pour atteindre le deuxième élément, il faudrait un décalage de 1 permettant d’ignorer le premier élément.</span><span class="sxs-lookup"><span data-stu-id="5eda3-140">To get to the second item, we would need to use an offset of 1 to skip the first item.</span></span>

```powershell
PS> $data[1]
One
```

<span data-ttu-id="5eda3-141">Par conséquent, le dernier élément est associé à un décalage de 3.</span><span class="sxs-lookup"><span data-stu-id="5eda3-141">This would mean that the last item is at offset 3.</span></span>

```powershell
PS> $data[3]
Three
```

#### <a name="index"></a><span data-ttu-id="5eda3-142">Index</span><span class="sxs-lookup"><span data-stu-id="5eda3-142">Index</span></span>

<span data-ttu-id="5eda3-143">Le choix des valeurs de cet exemple semble maintenant plus clair.</span><span class="sxs-lookup"><span data-stu-id="5eda3-143">Now you can see why I picked the values that I did for this example.</span></span> <span data-ttu-id="5eda3-144">Ce que nous avons jusqu’ici appelé décalage dans un souci d’exactitude est plus communément nommé index.</span><span class="sxs-lookup"><span data-stu-id="5eda3-144">I introduced this as an offset because that is what it really is, but this offset is more commonly referred to as an index.</span></span> <span data-ttu-id="5eda3-145">Il s’agit d’un index qui commence à `0`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-145">An index that starts at `0`.</span></span> <span data-ttu-id="5eda3-146">Nous parlerons d’index pour désigner le décalage dans la suite de cet article.</span><span class="sxs-lookup"><span data-stu-id="5eda3-146">For the rest of this article I will call the offset an index.</span></span>

#### <a name="special-index-tricks"></a><span data-ttu-id="5eda3-147">Astuces concernant les index</span><span class="sxs-lookup"><span data-stu-id="5eda3-147">Special index tricks</span></span>

<span data-ttu-id="5eda3-148">Dans la plupart des langages, on ne peut spécifier qu’un seul nombre comme index et on récupère un seul élément.</span><span class="sxs-lookup"><span data-stu-id="5eda3-148">In most languages, you can only specify a single number as the index and you get a single item back.</span></span>
<span data-ttu-id="5eda3-149">PowerShell est bien plus flexible.</span><span class="sxs-lookup"><span data-stu-id="5eda3-149">PowerShell is much more flexible.</span></span> <span data-ttu-id="5eda3-150">Il est possible d’utiliser plusieurs index à la fois.</span><span class="sxs-lookup"><span data-stu-id="5eda3-150">You can use multiple indexes at once.</span></span> <span data-ttu-id="5eda3-151">Fournir une liste d’index permet de sélectionner plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="5eda3-151">By providing a list of indexes, we can select several items.</span></span>

```powershell
PS> $data[0,2,3]
Zero
Two
Three
```

<span data-ttu-id="5eda3-152">Les éléments sont retournés dans l’ordre des index fournis.</span><span class="sxs-lookup"><span data-stu-id="5eda3-152">The items are returned based on the order of the indexes provided.</span></span> <span data-ttu-id="5eda3-153">Si l’on duplique un index, on récupère cet élément les deux fois.</span><span class="sxs-lookup"><span data-stu-id="5eda3-153">If you duplicate an index, you get that item both times.</span></span>

```powershell
PS> $data[3,0,3]
Three
Zero
Three
```

<span data-ttu-id="5eda3-154">Il est possible de spécifier une séquence de nombres avec l’opérateur `..` intégré.</span><span class="sxs-lookup"><span data-stu-id="5eda3-154">We can specify a sequence of numbers with the built-in `..` operator.</span></span>

```powershell
PS> $data[1..3]
One
Two
Three
```

<span data-ttu-id="5eda3-155">Cela fonctionne également en sens inverse.</span><span class="sxs-lookup"><span data-stu-id="5eda3-155">This works in reverse too.</span></span>

```powershell
PS> $data[3..1]
Three
Two
One
```

<span data-ttu-id="5eda3-156">Vous pouvez utiliser des valeurs d’index négatives pour suivre un décalage à partir de la fin.</span><span class="sxs-lookup"><span data-stu-id="5eda3-156">You can use negative index values to offset from the end.</span></span> <span data-ttu-id="5eda3-157">Par conséquent, si vous avez besoin du dernier élément de la liste, vous pouvez employer `-1`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-157">So if you need the last item in the list, you can use `-1`.</span></span>

```powershell
PS> $data[-1]
Three
```

<span data-ttu-id="5eda3-158">Attention à l’opérateur `..`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-158">One word of caution here with the `..` operator.</span></span> <span data-ttu-id="5eda3-159">La séquence `0..-1` et `-1..0` correspond aux valeurs `0,-1` et `-1,0`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-159">The sequence `0..-1` and `-1..0` evaluate to the values `0,-1` and `-1,0`.</span></span> <span data-ttu-id="5eda3-160">Il est facile de voir `$data[0..-1]` et de croire qu’elle énumère tous les éléments si l’on oublie ce détail.</span><span class="sxs-lookup"><span data-stu-id="5eda3-160">It's easy to see `$data[0..-1]` and think it would enumerate all items if you forget this detail.</span></span> <span data-ttu-id="5eda3-161">`$data[0..-1]` donne la même valeur que `$data[0,-1]`, à savoir le premier et le dernier élément du tableau (sans aucune autre valeur).</span><span class="sxs-lookup"><span data-stu-id="5eda3-161">`$data[0..-1]` gives you the same value as `$data[0,-1]` by giving you the first and last item in the array (and none of the other values).</span></span>

#### <a name="out-of-bounds"></a><span data-ttu-id="5eda3-162">Hors limites</span><span class="sxs-lookup"><span data-stu-id="5eda3-162">Out of bounds</span></span>

<span data-ttu-id="5eda3-163">Dans la plupart des langages, si l’on tente d’accéder à un index d’élément qui se trouve au-delà de la fin du tableau, on obtient un certain type d’erreur ou une exception.</span><span class="sxs-lookup"><span data-stu-id="5eda3-163">In most languages, if you try to access an index of an item that is past the end of the array, you would get some type of error or an exception.</span></span> <span data-ttu-id="5eda3-164">PowerShell ne retourne rien.</span><span class="sxs-lookup"><span data-stu-id="5eda3-164">PowerShell silently returns nothing.</span></span>

```powershell
PS> $null -eq $data[9000]
True
```

#### <a name="cannot-index-into-a-null-array"></a><span data-ttu-id="5eda3-165">Impossible d’indexer dans un tableau Null</span><span class="sxs-lookup"><span data-stu-id="5eda3-165">Cannot index into a null array</span></span>

<span data-ttu-id="5eda3-166">Si vous tentez d’indexer une variable `$null` comme un tableau, vous recevez une exception `System.Management.Automation.RuntimeException` avec le message `Cannot index into a null array`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-166">If your variable is `$null` and you try to index it like an array, you get a `System.Management.Automation.RuntimeException` exception with the message `Cannot index into a null array`.</span></span>

```powershell
PS> $empty = $null
SP> $empty[0]
Error: Cannot index into a null array.
```

<span data-ttu-id="5eda3-167">Par conséquent, vérifiez que vos tableaux ne sont pas `$null` avant d’essayer d’accéder aux éléments qu’ils contiennent.</span><span class="sxs-lookup"><span data-stu-id="5eda3-167">So make sure your arrays are not `$null` before you try to access elements inside them.</span></span>

#### <a name="count"></a><span data-ttu-id="5eda3-168">Count</span><span class="sxs-lookup"><span data-stu-id="5eda3-168">Count</span></span>

<span data-ttu-id="5eda3-169">Les tableaux et autres collections possèdent une propriété count qui indique le nombre d’éléments qu’ils contiennent.</span><span class="sxs-lookup"><span data-stu-id="5eda3-169">Arrays and other collections have a count property that tells you how many items are in the array.</span></span>

```powershell
PS> $data.count
4
```

<span data-ttu-id="5eda3-170">Dans la version 3.0 de PowerShell, une propriété count a été ajoutée à la plupart des objets.</span><span class="sxs-lookup"><span data-stu-id="5eda3-170">PowerShell 3.0 added a count property to most objects.</span></span> <span data-ttu-id="5eda3-171">Pour un seul objet, elle doit donner le nombre `1`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-171">you can have a single object and it should give you a count of `1`.</span></span>

```powershell
PS> $date = Get-Date
PS> $date.count
1
```

<span data-ttu-id="5eda3-172">Même `$null` possède une propriété count, à ceci près qu’elle retourne `0`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-172">Even `$null` has a count property except it returns `0`.</span></span>

```powershell
PS> $null.count
0
```

<span data-ttu-id="5eda3-173">Cet aspect présente quelques pièges, que nous examinerons lorsque nous aborderons les tableaux `$null` ou vides plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="5eda3-173">There are some traps here that I will revisit when I cover checking for `$null` or empty arrays later on in this article.</span></span>

#### <a name="off-by-one-errors"></a><span data-ttu-id="5eda3-174">Erreur par décalage de un</span><span class="sxs-lookup"><span data-stu-id="5eda3-174">Off-by-one errors</span></span>

<span data-ttu-id="5eda3-175">Le fait que les tableaux commencent à l’index 0 représente une source d’erreur de programmation courante.</span><span class="sxs-lookup"><span data-stu-id="5eda3-175">A common programming error is created because arrays start at index 0.</span></span> <span data-ttu-id="5eda3-176">Les erreurs par décalage de un peuvent être introduites de deux façons.</span><span class="sxs-lookup"><span data-stu-id="5eda3-176">Off-by-one errors can be introduced in two ways.</span></span>

<span data-ttu-id="5eda3-177">La première consiste à penser mentalement que l’on souhaite le deuxième élément et à utiliser l’index `2`, pour en fin de compte obtenir le troisième élément.</span><span class="sxs-lookup"><span data-stu-id="5eda3-177">The first is by mentally thinking you want the second item and using an index of `2` and really getting the third item.</span></span> <span data-ttu-id="5eda3-178">De même, on peut être tenté de considérer qu’il suffit de prendre le nombre total d’éléments (dans notre exemple, 4) pour accéder au dernier élément.</span><span class="sxs-lookup"><span data-stu-id="5eda3-178">Or by thinking that you have four items and you want last item, so you use the count to access the last item.</span></span>

```powershell
$data[ $data.count ]
```

<span data-ttu-id="5eda3-179">PowerShell autorise sans problème cette manipulation et se contente de fournir l’élément qui se trouve précisément à l’index 4 : `$null`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-179">PowerShell is perfectly happy to let you do that and give you exactly what item exists at index 4: `$null`.</span></span> <span data-ttu-id="5eda3-180">Il faudrait utiliser `$data.count - 1`, ou `-1` comme nous l’avons vu ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="5eda3-180">You should be using `$data.count - 1` or the `-1` that we learned about above.</span></span>

```powershell
PS> $data[ $data.count - 1 ]
Three
```

<span data-ttu-id="5eda3-181">C’est là que vous pouvez utiliser l’index `-1` pour récupérer le dernier élément.</span><span class="sxs-lookup"><span data-stu-id="5eda3-181">This is where you can use the `-1` index to get the last element.</span></span>

```powershell
PS> $data[ -1 ]
Three
```

<span data-ttu-id="5eda3-182">Lee Dailey a également indiqué que l’on peut utiliser `$data.GetUpperBound(0)` pour récupérer le numéro d’index maximal.</span><span class="sxs-lookup"><span data-stu-id="5eda3-182">Lee Dailey also pointed out to me that we can use `$data.GetUpperBound(0)` to get the max index number.</span></span>

```powershell
PS> $data.GetUpperBound(0)
3
PS> $data[ $data.GetUpperBound(0) ]
Three
```

<span data-ttu-id="5eda3-183">La seconde erreur la plus courante consiste à boucler sur la liste et à ne pas s’arrêter au bon moment.</span><span class="sxs-lookup"><span data-stu-id="5eda3-183">The second most common way is when iterating the list and not stopping at the right time.</span></span> <span data-ttu-id="5eda3-184">Nous reviendrons sur ce sujet lorsque nous parlerons de la boucle `for`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-184">I'll revisit this when we talk about using the `for` loop.</span></span>

### <a name="updating-items"></a><span data-ttu-id="5eda3-185">Mise à jour des éléments</span><span class="sxs-lookup"><span data-stu-id="5eda3-185">Updating items</span></span>

<span data-ttu-id="5eda3-186">Le même index peut servir à mettre à jour des éléments existants dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-186">We can use the same index to update existing items in the array.</span></span> <span data-ttu-id="5eda3-187">Il nous donne un accès direct à des éléments individuels.</span><span class="sxs-lookup"><span data-stu-id="5eda3-187">This gives us direct access to update individual items.</span></span>

```powershell
$data[2] = 'dos'
$data[3] = 'tres'
```

<span data-ttu-id="5eda3-188">Si l’on tente de mettre à jour un élément qui se trouve au-delà du dernier élément, on obtient une erreur `Index was outside the bounds of the array.`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-188">If we try to update an item that is past the last element, then we get an `Index was outside the bounds of the array.` error.</span></span>

```powershell
PS> $data[4] = 'four'
Index was outside the bounds of the array.
At line:1 char:1
+ $data[4] = 'four'
+ ~~~~~~~~~~~~~
+ CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
+ FullyQualifiedErrorId : System.IndexOutOfRangeException
```

<span data-ttu-id="5eda3-189">Nous reviendrons sur ce point plus tard lorsque nous évoquerons l’agrandissement d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-189">I'll revisit this later when I talk about how to make an array larger.</span></span>

### <a name="iteration"></a><span data-ttu-id="5eda3-190">Itération</span><span class="sxs-lookup"><span data-stu-id="5eda3-190">Iteration</span></span>

<span data-ttu-id="5eda3-191">À un moment donné, il peut être nécessaire de parcourir toute la liste et d’effectuer une action pour chacun des éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-191">At some point, you might need to walk or iterate the entire list and perform some action for each item in the array.</span></span>

#### <a name="pipeline"></a><span data-ttu-id="5eda3-192">Pipeline</span><span class="sxs-lookup"><span data-stu-id="5eda3-192">Pipeline</span></span>

<span data-ttu-id="5eda3-193">Les tableaux et le pipeline PowerShell sont conçus pour fonctionner ensemble.</span><span class="sxs-lookup"><span data-stu-id="5eda3-193">Arrays and the PowerShell pipeline are meant for each other.</span></span> <span data-ttu-id="5eda3-194">Il s’agit de l’une des méthodes les plus simples pour traiter ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="5eda3-194">This is one of the simplest ways to process over those values.</span></span> <span data-ttu-id="5eda3-195">Lorsque l’on transmet un tableau à un pipeline, chacun des éléments du tableau est traité individuellement.</span><span class="sxs-lookup"><span data-stu-id="5eda3-195">When you pass an array to a pipeline, each item inside the array is processed individually.</span></span>

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data | ForEach-Object {"Item: [$PSItem]"}
Item: [Zero]
Item: [One]
Item: [Two]
Item: [Three]
```

<span data-ttu-id="5eda3-196">Si vous n’avez pas encore rencontré `$PSItem`, sachez qu’il s’agit de la même chose que `$_`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-196">If you have not seen `$PSItem` before, just know that it's the same thing as `$_`.</span></span> <span data-ttu-id="5eda3-197">Vous pouvez utiliser celui de votre choix, car ils représentent tous deux l’objet actuel dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="5eda3-197">You can use either one because they both represent the current object in the pipeline.</span></span>

#### <a name="foreach-loop"></a><span data-ttu-id="5eda3-198">Boucle foreach</span><span class="sxs-lookup"><span data-stu-id="5eda3-198">ForEach loop</span></span>

<span data-ttu-id="5eda3-199">La boucle `ForEach` fonctionne bien avec les collections,</span><span class="sxs-lookup"><span data-stu-id="5eda3-199">The `ForEach` loop works well with collections.</span></span> <span data-ttu-id="5eda3-200">suivant la syntaxe : `foreach ( <variable> in <collection> )`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-200">Using the syntax: `foreach ( <variable> in <collection> )`</span></span>

```powershell
foreach ( $node in $data )
{
    "Item: [$node]"
}
```

#### <a name="foreach-method"></a><span data-ttu-id="5eda3-201">Méthode foreach</span><span class="sxs-lookup"><span data-stu-id="5eda3-201">ForEach method</span></span>

<span data-ttu-id="5eda3-202">Point que j’ai tendance à oublier, elle fonctionne bien pour les opérations simples.</span><span class="sxs-lookup"><span data-stu-id="5eda3-202">I tend to forget about this one but it works well for simple operations.</span></span> <span data-ttu-id="5eda3-203">PowerShell autorise l’appel à `.ForEach()` sur une collection.</span><span class="sxs-lookup"><span data-stu-id="5eda3-203">PowerShell allows you to call `.ForEach()` on a collection.</span></span>

```powershell
PS> $data.foreach({"Item [$PSItem]"})
Item [Zero]
Item [One]
Item [Two]
Item [Three]
```

<span data-ttu-id="5eda3-204">`.foreach()` accepte un paramètre qui est un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="5eda3-204">The `.foreach()` takes a parameter that is a script block.</span></span> <span data-ttu-id="5eda3-205">Vous pouvez enlever les parenthèses pour n’indiquer que le bloc de script.</span><span class="sxs-lookup"><span data-stu-id="5eda3-205">You can drop the parentheses and just provide the script block.</span></span>

```powershell
$data.foreach{"Item [$PSItem]"}
```

<span data-ttu-id="5eda3-206">Cette syntaxe, moins connue, fonctionne exactement de la même façon.</span><span class="sxs-lookup"><span data-stu-id="5eda3-206">This is a lesser known syntax but it works just the same.</span></span> <span data-ttu-id="5eda3-207">Cette méthode `foreach` a été ajoutée dans la version 4.0 de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5eda3-207">This `foreach` method was added in PowerShell 4.0.</span></span>

#### <a name="for-loop"></a><span data-ttu-id="5eda3-208">Boucle for</span><span class="sxs-lookup"><span data-stu-id="5eda3-208">For loop</span></span>

<span data-ttu-id="5eda3-209">La boucle `for`, très utilisée dans la plupart des langages, l’est assez peu dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5eda3-209">The `for` loop is used heavily in most other languages but you don't see it much in PowerShell.</span></span> <span data-ttu-id="5eda3-210">Quand on la rencontre, c’est souvent dans le contexte d’un parcours de tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-210">When you do see it, it's often in the context of walking an array.</span></span>

```powershell
for ( $index = 0; $index -lt $data.count; $index++)
{
    "Item: [{0}]" -f $data[$index]
}
```

<span data-ttu-id="5eda3-211">La première chose à faire est d’initialiser un `$index` à `0`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-211">The first thing we do is initialize an `$index` to `0`.</span></span> <span data-ttu-id="5eda3-212">Ensuite, nous ajoutons la condition selon laquelle `$index` doit être inférieur à `$data.count`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-212">Then we add the condition that `$index` must be less than `$data.count`.</span></span> <span data-ttu-id="5eda3-213">Enfin, nous spécifions que, à chaque itération, l’index doit augmenter de `1`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-213">Finally, we specify that every time we loop that me must increase the index by `1`.</span></span> <span data-ttu-id="5eda3-214">Dans ce cas, `$index++` est la version abrégée de `$index = $index + 1`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-214">In this case `$index++` is short for `$index = $index + 1`.</span></span>

<span data-ttu-id="5eda3-215">Chaque fois que vous utilisez une boucle `for`, portez une attention particulière à la condition.</span><span class="sxs-lookup"><span data-stu-id="5eda3-215">Whenever you're using a `for` loop, pay special attention to the condition.</span></span> <span data-ttu-id="5eda3-216">Il s’agit ici de `$index -lt $data.count`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-216">I used `$index -lt $data.count` here.</span></span> <span data-ttu-id="5eda3-217">Il est facile de se tromper sur la condition en introduisant par erreur un décalage de un dans la logique.</span><span class="sxs-lookup"><span data-stu-id="5eda3-217">It's easy to get the condition slightly wrong to get an off-by-one error in your logic.</span></span> <span data-ttu-id="5eda3-218">`$index -le $data.count` et `$index -lt ($data.count - 1)` sont incorrects.</span><span class="sxs-lookup"><span data-stu-id="5eda3-218">Using `$index -le $data.count` or `$index -lt ($data.count - 1)` are ever so slightly wrong.</span></span> <span data-ttu-id="5eda3-219">En résulterait le traitement de trop ou trop peu d’éléments dans le résultat.</span><span class="sxs-lookup"><span data-stu-id="5eda3-219">That would cause your result to process too many or too few items.</span></span> <span data-ttu-id="5eda3-220">Il s’agit de l’erreur classique de décalage de un.</span><span class="sxs-lookup"><span data-stu-id="5eda3-220">This is the classic off-by-one error.</span></span>

#### <a name="switch-loop"></a><span data-ttu-id="5eda3-221">Boucle switch</span><span class="sxs-lookup"><span data-stu-id="5eda3-221">Switch loop</span></span>

<span data-ttu-id="5eda3-222">On peut facilement passer à côté de cette boucle.</span><span class="sxs-lookup"><span data-stu-id="5eda3-222">This is one that is easy to overlook.</span></span> <span data-ttu-id="5eda3-223">Si l’on donne un tableau à une [instruction switch][], elle vérifie chacun des éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-223">If you provide an array to a [switch statement][], it checks each item in the array.</span></span>

```powershell
$data = 'Zero','One','Two','Three'
switch( $data )
{
    'One'
    {
        'Tock'
    }
    'Three'
    {
        'Tock'
    }
    Default
    {
        'Tick'
    }
}
```

```Output
Tick
Tock
Tick
Tock
```

<span data-ttu-id="5eda3-224">L’instruction switch présente de nombreuses applications intéressantes.</span><span class="sxs-lookup"><span data-stu-id="5eda3-224">There are a lot of cool things that we can do with the switch statement.</span></span> <span data-ttu-id="5eda3-225">Voir à ce sujet l’article suivant :</span><span class="sxs-lookup"><span data-stu-id="5eda3-225">I have another article dedicated to this.</span></span>

- <span data-ttu-id="5eda3-226">[Tout ce que vous avez toujours voulu savoir sur l’instruction switch][instruction switch]</span><span class="sxs-lookup"><span data-stu-id="5eda3-226">[Everything you ever wanted to know about the switch statement][switch statement]</span></span>

#### <a name="updating-values"></a><span data-ttu-id="5eda3-227">Mise à jour des valeurs</span><span class="sxs-lookup"><span data-stu-id="5eda3-227">Updating values</span></span>

<span data-ttu-id="5eda3-228">Lorsque le tableau est une collection de chaînes ou d’entiers (types valeur), il peut être intéressant de mettre à jour les valeurs dans le tableau au fur et à mesure qu’il est parcouru.</span><span class="sxs-lookup"><span data-stu-id="5eda3-228">When your array is a collection of string or integers (value types), sometimes you may want to update the values in the array as you loop over them.</span></span> <span data-ttu-id="5eda3-229">La plupart des boucles ci-dessus comportent une variable contenant une copie de la valeur.</span><span class="sxs-lookup"><span data-stu-id="5eda3-229">Most of the loops above use a variable in the loop that holds a copy of the value.</span></span> <span data-ttu-id="5eda3-230">Si l’on met à jour cette variable, la valeur d’origine dans le tableau n’est pas mise à jour.</span><span class="sxs-lookup"><span data-stu-id="5eda3-230">If you update that variable, the original value in the array is not updated.</span></span>

<span data-ttu-id="5eda3-231">Il existe une exception à cette règle : la boucle `for`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-231">The exception to that statement is the `for` loop.</span></span> <span data-ttu-id="5eda3-232">Elle permet de parcourir un tableau et de mettre à jour des valeurs à l’intérieur.</span><span class="sxs-lookup"><span data-stu-id="5eda3-232">If you want to walk an array and update values inside it, then the `for` loop is what you're looking for.</span></span>

```powershell
for ( $index = 0; $index -lt $data.count; $index++ )
{
    $data[$index] = "Item: [{0}]" -f $data[$index]
}
```

<span data-ttu-id="5eda3-233">Cet exemple prend une valeur par son index, effectue quelques modifications, puis utilise ce même index pour la réassigner.</span><span class="sxs-lookup"><span data-stu-id="5eda3-233">This example takes a value by index, makes a few changes, and then uses that same index to assign it back.</span></span>

## <a name="arrays-of-objects"></a><span data-ttu-id="5eda3-234">Tableaux d'objets</span><span class="sxs-lookup"><span data-stu-id="5eda3-234">Arrays of Objects</span></span>

<span data-ttu-id="5eda3-235">Jusqu’à présent, la seule chose que nos tableaux comportaient était un type valeur, mais ils peuvent également contenir des objets.</span><span class="sxs-lookup"><span data-stu-id="5eda3-235">So far, the only thing we've placed in an array is a value type, but arrays can also contain objects.</span></span>

```powershell
$data = @(
    [pscustomobject]@{FirstName='Kevin';LastName='Marquette'}
    [pscustomobject]@{FirstName='John'; LastName='Doe'}
)
```

<span data-ttu-id="5eda3-236">De nombreuses cmdlets retournent des collections d’objets sous forme de tableaux lorsqu’elles sont assignées à une variable.</span><span class="sxs-lookup"><span data-stu-id="5eda3-236">Many cmdlets return collections of objects as arrays when you assign them to a variable.</span></span>

```powershell
$processList = Get-Process
```

<span data-ttu-id="5eda3-237">Toutes les fonctionnalités de base que nous avons déjà évoquées s’appliquent aussi à des tableaux d’objets ; cependant, certains points méritent d’être soulignés.</span><span class="sxs-lookup"><span data-stu-id="5eda3-237">All of the basic features we already talked about still apply to arrays of objects with a few details worth pointing out.</span></span>

### <a name="accessing-properties"></a><span data-ttu-id="5eda3-238">Accès aux propriétés</span><span class="sxs-lookup"><span data-stu-id="5eda3-238">Accessing properties</span></span>

<span data-ttu-id="5eda3-239">Il est possible d’utiliser un index pour accéder à un élément individuel dans une collection, comme avec les types valeur.</span><span class="sxs-lookup"><span data-stu-id="5eda3-239">We can use an index to access an individual item in a collection just like with value types.</span></span>

```powershell
PS> $data[0]

FirstName LastName
-----     ----
Kevin     Marquette
```

<span data-ttu-id="5eda3-240">Les propriétés sont accessibles et peuvent être mises à jour directement.</span><span class="sxs-lookup"><span data-stu-id="5eda3-240">We can access and update properties directly.</span></span>

```powershell
PS> $data[0].FirstName

Kevin

PS> $data[0].FirstName = 'Jay'
PS> $data[0]

FirstName LastName
-----     ----
Jay       Marquette
```

#### <a name="array-properties"></a><span data-ttu-id="5eda3-241">Propriétés des tableaux</span><span class="sxs-lookup"><span data-stu-id="5eda3-241">Array properties</span></span>

<span data-ttu-id="5eda3-242">Il faut normalement énumérer ainsi l’ensemble de la liste pour accéder à toutes les propriétés :</span><span class="sxs-lookup"><span data-stu-id="5eda3-242">Normally you would have to enumerate the whole list like this to access all the properties:</span></span>

```powershell
PS> $data | ForEach-Object {$_.LastName}

Marquette
Doe
```

<span data-ttu-id="5eda3-243">Il est également possible d’utiliser la cmdlet `Select-Object -ExpandProperty`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-243">Or by using the `Select-Object -ExpandProperty` cmdlet.</span></span>

```powershell
PS> $data | Select-Object -ExpandProperty LastName

Marquette
Doe
```

<span data-ttu-id="5eda3-244">Cependant, PowerShell offre la possibilité de demander directement `LastName`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-244">But PowerShell offers us the ability to request `LastName` directly.</span></span> <span data-ttu-id="5eda3-245">PowerShell les énumère tous automatiquement et retourne une liste nettoyée.</span><span class="sxs-lookup"><span data-stu-id="5eda3-245">PowerShell enumerates them all for us and returns a clean list.</span></span>

```powershell
PS> $data.LastName

Marquette
Doe
```

<span data-ttu-id="5eda3-246">L’énumération se produit toujours, mais la complexité sous-jacente n’est pas visible.</span><span class="sxs-lookup"><span data-stu-id="5eda3-246">The enumeration still happens but we don't see the complexity behind it.</span></span>

### <a name="where-object-filtering"></a><span data-ttu-id="5eda3-247">Filtrage Where-Object</span><span class="sxs-lookup"><span data-stu-id="5eda3-247">Where-Object filtering</span></span>

<span data-ttu-id="5eda3-248">C’est là qu’intervient `Where-Object`, qui permet de filtrer et de sélectionner des objets à extraire du tableau en fonction de leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="5eda3-248">This is where `Where-Object` comes in so we can filter and select what we want out of the array based on the properties of the object.</span></span>

```powershell
PS> $data | Where-Object {$_.FirstName -eq 'Kevin'}

FirstName LastName
-----     ----
Kevin     Marquette
```

<span data-ttu-id="5eda3-249">Il est possible d’écrire la même requête pour obtenir le `FirstName` recherché.</span><span class="sxs-lookup"><span data-stu-id="5eda3-249">We can write that same query to get the `FirstName` we are looking for.</span></span>

```powershell
$data | Where FirstName -eq Kevin
```

#### <a name="where"></a><span data-ttu-id="5eda3-250">Where()</span><span class="sxs-lookup"><span data-stu-id="5eda3-250">Where()</span></span>

<span data-ttu-id="5eda3-251">Les tableaux comportent une méthode `Where()` qui permet de spécifier un `scriptblock` pour le filtre.</span><span class="sxs-lookup"><span data-stu-id="5eda3-251">Arrays have a `Where()` method on them that allows you to specify a `scriptblock` for the filter.</span></span>

```powershell
$data.Where({$_.FirstName -eq 'Kevin'})
```

<span data-ttu-id="5eda3-252">Cette fonctionnalité a été ajoutée dans la version 4.0 de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5eda3-252">This feature was added in PowerShell 4.0.</span></span>

### <a name="updating-objects-in-loops"></a><span data-ttu-id="5eda3-253">Mise à jour des objets dans les boucles</span><span class="sxs-lookup"><span data-stu-id="5eda3-253">Updating objects in loops</span></span>

<span data-ttu-id="5eda3-254">Avec les types valeur, la seule façon de mettre à jour le tableau consiste à utiliser une boucle for, car il faut connaître l’index pour remplacer la valeur.</span><span class="sxs-lookup"><span data-stu-id="5eda3-254">With value types, the only way to update the array is to use a for loop because we need to know the index to replace the value.</span></span> <span data-ttu-id="5eda3-255">Les objets offrent davantage de possibilités, car il s’agit de types référence.</span><span class="sxs-lookup"><span data-stu-id="5eda3-255">We have more options with objects because they are reference types.</span></span> <span data-ttu-id="5eda3-256">Voici un exemple rapide :</span><span class="sxs-lookup"><span data-stu-id="5eda3-256">Here is a quick example:</span></span>

```powershell
foreach($person in $data)
{
    $person.FirstName = 'Kevin'
}
```

<span data-ttu-id="5eda3-257">Cette boucle parcourt chaque objet du tableau `$data`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-257">This loop is walking every object in the `$data` array.</span></span> <span data-ttu-id="5eda3-258">Étant donné que les objets sont des types référence, la variable `$person` fait précisément référence à l’objet qui se trouve dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-258">Because objects are reference types, the `$person` variable references the exact same object that is in the array.</span></span> <span data-ttu-id="5eda3-259">Ainsi, mettre à jour ses propriétés a pour effet de mettre à jour l’original.</span><span class="sxs-lookup"><span data-stu-id="5eda3-259">So updates to its properties do update the original.</span></span>

<span data-ttu-id="5eda3-260">Il n’est cependant pas possible de remplacer l’intégralité de l’objet de cette façon.</span><span class="sxs-lookup"><span data-stu-id="5eda3-260">You still can't replace the whole object this way.</span></span> <span data-ttu-id="5eda3-261">Si vous essayez d’assigner un nouvel objet à la variable `$person`, vous mettez à jour la référence de variable sur une autre valeur qui ne pointe plus vers l’objet d’origine du tableau,</span><span class="sxs-lookup"><span data-stu-id="5eda3-261">If you try to assign a new object to the `$person` variable, you're updating the variable reference to something else that no longer points to the original object in the array.</span></span> <span data-ttu-id="5eda3-262">ce qui ne donne pas le résultat attendu :</span><span class="sxs-lookup"><span data-stu-id="5eda3-262">This doesn't work like you would expect:</span></span>

```powershell
foreach($person in $data)
{
    $person = [pscustomobject]@{
        FirstName='Kevin'
        LastName='Marquette'
    }
}
```

## <a name="operators"></a><span data-ttu-id="5eda3-263">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="5eda3-263">Operators</span></span>

<span data-ttu-id="5eda3-264">Les opérateurs de PowerShell fonctionnent également sur les tableaux.</span><span class="sxs-lookup"><span data-stu-id="5eda3-264">The operators in PowerShell also work on arrays.</span></span> <span data-ttu-id="5eda3-265">Certains ont un comportement légèrement différent.</span><span class="sxs-lookup"><span data-stu-id="5eda3-265">Some of them work slightly differently.</span></span>

### <a name="-join"></a><span data-ttu-id="5eda3-266">-join</span><span class="sxs-lookup"><span data-stu-id="5eda3-266">-join</span></span>

<span data-ttu-id="5eda3-267">L’opérateur `-join` étant le plus évident, examinons-le en premier.</span><span class="sxs-lookup"><span data-stu-id="5eda3-267">The `-join` operator is the most obvious one so let's look at it first.</span></span> <span data-ttu-id="5eda3-268">Il est très intéressant à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5eda3-268">I like the `-join` operator and use it often.</span></span> <span data-ttu-id="5eda3-269">Il joint tous les éléments du tableau avec le caractère ou la chaîne spécifié.</span><span class="sxs-lookup"><span data-stu-id="5eda3-269">It joins all elements in the array with the character or string that you specify.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join '-'
1-2-3-4
PS> $data -join ','
1,2,3,4
```

<span data-ttu-id="5eda3-270">L’une des fonctionnalités les plus utiles de l’opérateur `-join` est le fait qu’il gère les éléments uniques.</span><span class="sxs-lookup"><span data-stu-id="5eda3-270">One of the features that I like about the `-join` operator is that it handles single items.</span></span>

```powershell
PS> 1 -join '-'
1
```

<span data-ttu-id="5eda3-271">C’est particulièrement pratique dans les messages de journalisation et les commentaires.</span><span class="sxs-lookup"><span data-stu-id="5eda3-271">I use this inside logging and verbose messages.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> "Data is $($data -join ',')."
Data is 1,2,3,4.
```

#### <a name="-join-array"></a><span data-ttu-id="5eda3-272">-join $array</span><span class="sxs-lookup"><span data-stu-id="5eda3-272">-join $array</span></span>

<span data-ttu-id="5eda3-273">Voici une astuce intelligente signalée par Lee Dailey.</span><span class="sxs-lookup"><span data-stu-id="5eda3-273">Here is a clever trick that Lee Dailey pointed out to me.</span></span> <span data-ttu-id="5eda3-274">Pour tout joindre sans délimiteur, au lieu de procéder ainsi :</span><span class="sxs-lookup"><span data-stu-id="5eda3-274">If you ever want to join everything without a delimiter, instead of doing this:</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join $null
1234
```

<span data-ttu-id="5eda3-275">Il est possible d’utiliser `-join` en mettant le tableau en paramètre sans préfixe.</span><span class="sxs-lookup"><span data-stu-id="5eda3-275">You can use `-join` with the array as the parameter with no prefix.</span></span> <span data-ttu-id="5eda3-276">Regardez cet exemple pour en voir une illustration.</span><span class="sxs-lookup"><span data-stu-id="5eda3-276">Take a look at this example to see that I'm talking about.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> -join $data
1234
```

### <a name="-replace-and--split"></a><span data-ttu-id="5eda3-277">-replace et -split</span><span class="sxs-lookup"><span data-stu-id="5eda3-277">-replace and -split</span></span>

<span data-ttu-id="5eda3-278">Les autres opérateurs, comme `-replace` et `-split`, s’exécutent sur chacun des éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-278">The other operators like `-replace` and `-split` execute on each item in the array.</span></span> <span data-ttu-id="5eda3-279">Je ne pense pas les avoir déjà utilisés de cette manière, mais en voici un exemple.</span><span class="sxs-lookup"><span data-stu-id="5eda3-279">I can't say that I have ever used them this way but here is an example.</span></span>

```powershell
PS> $data = @('ATX-SQL-01','ATX-SQL-02','ATX-SQL-03')
PS> $data -replace 'ATX','LAX'
LAX-SQL-01
LAX-SQL-02
LAX-SQL-03
```

### <a name="-contains"></a><span data-ttu-id="5eda3-280">-contains</span><span class="sxs-lookup"><span data-stu-id="5eda3-280">-contains</span></span>

<span data-ttu-id="5eda3-281">L’opérateur `-contains` permet de regarder si un tableau de valeurs contient une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5eda3-281">The `-contains` operator allows you to check an array of values to see if it contains a specified value.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -contains 'green'
True
```

### <a name="-in"></a><span data-ttu-id="5eda3-282">-in</span><span class="sxs-lookup"><span data-stu-id="5eda3-282">-in</span></span>

<span data-ttu-id="5eda3-283">Pour vérifier la correspondance entre une valeur unique et différentes valeurs, vous pouvez utiliser l’opérateur `-in`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-283">When you have a single value that you would like to verify matches one of several values, you can use the `-in` operator.</span></span> <span data-ttu-id="5eda3-284">La valeur se trouve du côté gauche et le tableau du côté droit de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="5eda3-284">The value would be on the left and the array on the right-hand side of the operator.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> 'green' -in $data
True
```

<span data-ttu-id="5eda3-285">Cette opération peut être coûteuse si la liste est volumineuse.</span><span class="sxs-lookup"><span data-stu-id="5eda3-285">This can get expensive if the list is large.</span></span> <span data-ttu-id="5eda3-286">Un modèle regex peut se révéler utile quand il y a de nombreuses valeurs à vérifier.</span><span class="sxs-lookup"><span data-stu-id="5eda3-286">I often use a regex pattern if I'm checking more than a few values.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $pattern = "^({0})$" -f ($data -join '|')
PS> $pattern
^(red|green|blue)$

PS> 'green' -match $pattern
True
```

### <a name="-eq-and--ne"></a><span data-ttu-id="5eda3-287">-eq et -ne</span><span class="sxs-lookup"><span data-stu-id="5eda3-287">-eq and -ne</span></span>

<span data-ttu-id="5eda3-288">L’égalité peut être compliquée avec les tableaux.</span><span class="sxs-lookup"><span data-stu-id="5eda3-288">Equality and arrays can get complicated.</span></span> <span data-ttu-id="5eda3-289">Lorsque le tableau se trouve sur le côté gauche, chacun des éléments est comparé.</span><span class="sxs-lookup"><span data-stu-id="5eda3-289">When the array is on the left side, every item gets compared.</span></span> <span data-ttu-id="5eda3-290">Au lieu de retourner `True`, elle retourne l’objet qui correspond.</span><span class="sxs-lookup"><span data-stu-id="5eda3-290">Instead of returning `True`, it returns the object that matches.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -eq 'green'
green
```

<span data-ttu-id="5eda3-291">L’opérateur `-ne` donne toutes les valeurs qui ne sont pas égales à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5eda3-291">When you use the `-ne` operator, we get all the values that are not equal to our value.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -ne 'green'
red
blue
```

<span data-ttu-id="5eda3-292">Si l’opérateur se trouve dans une instruction `if()`, la valeur retournée correspond à une valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-292">When you use this in an `if()` statement, a value that is returned is a `True` value.</span></span> <span data-ttu-id="5eda3-293">Si aucune valeur n’est retournée, il s’agit d’une valeur `False`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-293">If no value is returned, then it's a `False` value.</span></span> <span data-ttu-id="5eda3-294">Les deux instructions suivantes prennent la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-294">Both of these next statements evaluate to `True`.</span></span>

```powershell
$data = @('red','green','blue')
if ( $data -eq 'green' )
{
    'Green was found'
}
if ( $data -ne 'green' )
{
    'And green was not found'
}
```

<span data-ttu-id="5eda3-295">Nous reviendrons sur ce sujet lorsque nous parlerons des tests `$null`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-295">I'll revisit this in a moment when we talk about testing for `$null`.</span></span>

### <a name="-match"></a><span data-ttu-id="5eda3-296">-match</span><span class="sxs-lookup"><span data-stu-id="5eda3-296">-match</span></span>

<span data-ttu-id="5eda3-297">L’opérateur `-match` tente de faire correspondre chacun des éléments de la collection.</span><span class="sxs-lookup"><span data-stu-id="5eda3-297">The `-match` operator tries to match each item in the collection.</span></span>

```powershell
PS> $servers = @(
    'LAX-SQL-01'
    'LAX-API-01'
    'ATX-SQL-01'
    'ATX-API-01'
)
PS> $servers -match 'SQL'
LAX-SQL-01
ATX-SQL-01
```

<span data-ttu-id="5eda3-298">Si `-match` est utilisé avec une valeur unique, une variable spéciale `$Matches` est remplie avec les informations de correspondance.</span><span class="sxs-lookup"><span data-stu-id="5eda3-298">When you use `-match` with a single value, a special variable `$Matches` gets populated with match info.</span></span> <span data-ttu-id="5eda3-299">Ce n’est pas le cas lorsque l’on traite un tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-299">This isn't the case when an array is processed this way.</span></span>

<span data-ttu-id="5eda3-300">Il est possible d’adopter la même approche avec `Select-String`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-300">We can take the same approach with `Select-String`.</span></span>

```powershell
$servers | Select-String SQL
```

<span data-ttu-id="5eda3-301">`Select-String`, `-match` et la variable `$matches` sont examinés plus en détail dans un autre billet intitulé [Les nombreuses façons d’utiliser les regex][].</span><span class="sxs-lookup"><span data-stu-id="5eda3-301">I take a closer look at `Select-String`,`-match` and the `$matches` variable in another post called [The many ways to use regex][].</span></span>

### <a name="null-or-empty"></a><span data-ttu-id="5eda3-302">$null ou vide</span><span class="sxs-lookup"><span data-stu-id="5eda3-302">$null or empty</span></span>

<span data-ttu-id="5eda3-303">Il peut être difficile de tester les tableaux `$null` ou vides.</span><span class="sxs-lookup"><span data-stu-id="5eda3-303">Testing for `$null` or empty arrays can be tricky.</span></span> <span data-ttu-id="5eda3-304">Voici les pièges courants des tableaux.</span><span class="sxs-lookup"><span data-stu-id="5eda3-304">Here are the common traps with arrays.</span></span>

<span data-ttu-id="5eda3-305">Au premier coup d’œil, cette instruction semble fonctionner.</span><span class="sxs-lookup"><span data-stu-id="5eda3-305">At a glance, this statement looks like it should work.</span></span>

```powershell
if ( $array -eq $null)
{
    'Array is $null'
}
```

<span data-ttu-id="5eda3-306">Cependant, nous venons de voir comment `-eq` vérifie chacun des éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-306">But I just went over how `-eq` checks each item in the array.</span></span> <span data-ttu-id="5eda3-307">Avec un tableau de plusieurs éléments comportant une seule valeur $null, le résultat serait donc `$true`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-307">So we can have an array of several items with a single $null value and it would evaluate to `$true`</span></span>

```powershell
$array = @('one',$null,'three')
if ( $array -eq $null)
{
    'I think Array is $null, but I would be wrong'
}
```

<span data-ttu-id="5eda3-308">C’est la raison pour laquelle il est recommandé de placer `$null` du côté gauche de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="5eda3-308">This is why it's a best practice to place the `$null` on the left side of the operator.</span></span> <span data-ttu-id="5eda3-309">Ce scénario devient un faux problème.</span><span class="sxs-lookup"><span data-stu-id="5eda3-309">This makes this scenario a non-issue.</span></span>

```powershell
if ( $null -eq $array )
{
    'Array actually is $null'
}
```

<span data-ttu-id="5eda3-310">Un tableau `$null` n’est pas la même chose qu’un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="5eda3-310">A `$null` array isn't the same thing as an empty array.</span></span> <span data-ttu-id="5eda3-311">Si vous savez qu’il s’agit d’un tableau, vérifiez le nombre d’objets qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="5eda3-311">If you know you have an array, check the count of objects in it.</span></span> <span data-ttu-id="5eda3-312">Si le tableau est `$null`, le nombre est `0`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-312">If the array is `$null`, the count is `0`.</span></span>

```powershell
if ( $array.count -gt 0 )
{
    'Array isn't empty'
}
```

<span data-ttu-id="5eda3-313">Il existe un autre piège à surveiller.</span><span class="sxs-lookup"><span data-stu-id="5eda3-313">There is one more trap to watch out for here.</span></span> <span data-ttu-id="5eda3-314">Il est possible d’utiliser `count` même s’il n’y a qu’un seul objet, sauf si cet objet est un `PSCustomObject`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-314">You can use the `count` even if you have a single object, unless that object is a `PSCustomObject`.</span></span> <span data-ttu-id="5eda3-315">Ce bogue a été résolu dans la version 6.1 de PowerShell,</span><span class="sxs-lookup"><span data-stu-id="5eda3-315">This is a bug that is fixed in PowerShell 6.1.</span></span>
<span data-ttu-id="5eda3-316">ce qui est une bonne nouvelle. Cependant, nombreux sont ceux qui utilisent toujours la version 5.1 et doivent faire attention à ce point.</span><span class="sxs-lookup"><span data-stu-id="5eda3-316">That's good news, but a lot of people are still on 5.1 and need to watch out for it.</span></span>

```powershell
PS> $object = [PSCustomObject]@{Name='TestObject'}
PS> $object.count
$null
```

<span data-ttu-id="5eda3-317">Si c’est votre cas, vous pouvez encapsuler l’objet dans un tableau avant de compter les éléments pour obtenir un nombre exact.</span><span class="sxs-lookup"><span data-stu-id="5eda3-317">If you're still on PowerShell 5.1, you can wrap the object in an array before checking the count to get an accurate count.</span></span>

```powershell
if ( @($array).count -gt 0 )
{
    'Array isn't empty'
}
```

<span data-ttu-id="5eda3-318">Pour jouer la sécurité totale, vérifiez si le tableau est `$null`, puis comptez les éléments.</span><span class="sxs-lookup"><span data-stu-id="5eda3-318">To fully play it safe, check for `$null`, then check the count.</span></span>

```powershell
if ( $null -ne $array -and @($array).count -gt 0 )
{
    'Array isn't empty'
}
```

### <a name="all--eq"></a><span data-ttu-id="5eda3-319">Tout -eq</span><span class="sxs-lookup"><span data-stu-id="5eda3-319">All -eq</span></span>

<span data-ttu-id="5eda3-320">Récemment, quelqu’un a demandé [comment vérifier la correspondance entre chacune des valeurs d’un tableau et une valeur donnée][].</span><span class="sxs-lookup"><span data-stu-id="5eda3-320">I recently saw someone ask [how to verify that every value in an array matches a given value][].</span></span>
<span data-ttu-id="5eda3-321">L’utilisateur Reddit **/u/bis** a proposé cette [Solution][], qui recherche les valeurs incorrectes, puis inverse le résultat.</span><span class="sxs-lookup"><span data-stu-id="5eda3-321">Reddit user **/u/bis** had this clever [solution][] that checks for any incorrect values and then flips the result.</span></span>

```powershell
$results = Test-Something
if ( -not ( $results -ne 'Passed') )
{
    'All results a Passed'
}
```

## <a name="adding-to-arrays"></a><span data-ttu-id="5eda3-322">Ajout d’éléments à des tableaux</span><span class="sxs-lookup"><span data-stu-id="5eda3-322">Adding to arrays</span></span>

<span data-ttu-id="5eda3-323">La question est maintenant de savoir comment ajouter des éléments à un tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-323">At this point, you're starting to wonder how to add items to an array.</span></span> <span data-ttu-id="5eda3-324">La réponse rapide est que ce n’est pas possible.</span><span class="sxs-lookup"><span data-stu-id="5eda3-324">The quick answer is that you can't.</span></span> <span data-ttu-id="5eda3-325">Un tableau a une taille fixe en mémoire.</span><span class="sxs-lookup"><span data-stu-id="5eda3-325">An array is a fixed size in memory.</span></span> <span data-ttu-id="5eda3-326">Pour l’agrandir ou y ajouter un seul élément, il faut créer un nouveau tableau et copier toutes les valeurs de l’ancien tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-326">If you need to grow it or add a single item to it, then you need to create a new array and copy all the values over from the old array.</span></span> <span data-ttu-id="5eda3-327">Cette opération semble coûteuse et chronophage. Cependant, PowerShell masque la complexité liée à la création du nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-327">This sounds expensive and like a lot of work, however, PowerShell hides the complexity of creating the new array.</span></span>

### <a name="array-addition"></a><span data-ttu-id="5eda3-328">Ajout de tableaux</span><span class="sxs-lookup"><span data-stu-id="5eda3-328">Array addition</span></span>

<span data-ttu-id="5eda3-329">Il est possible d’utiliser l’opérateur d’addition avec des tableaux pour en créer un nouveau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-329">We can use the addition operator with arrays to create a new array.</span></span> <span data-ttu-id="5eda3-330">Prenons donc les deux tableaux suivants :</span><span class="sxs-lookup"><span data-stu-id="5eda3-330">So given these two arrays:</span></span>

```powershell
$first = @(
    'Zero'
    'One'
)
$second = @(
    'Two'
    'Three'
)
```

<span data-ttu-id="5eda3-331">Nous pouvons les ajouter ensemble pour obtenir un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-331">We can add them together to get a new array.</span></span>

```powershell
PS> $first + $second

Zero
One
Two
Three
```

### <a name="plus-equals-"></a><span data-ttu-id="5eda3-332">Plus égal +=</span><span class="sxs-lookup"><span data-stu-id="5eda3-332">Plus equals +=</span></span>

<span data-ttu-id="5eda3-333">Il est possible de créer un nouveau tableau sur place et d’y ajouter un élément :</span><span class="sxs-lookup"><span data-stu-id="5eda3-333">We can create a new array in place and add an item to it like this:</span></span>

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
$data += 'four'
```

<span data-ttu-id="5eda3-334">N’oubliez pas que, chaque fois que vous utilisez `+=`, vous dupliquez et créez un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-334">Just remember that every time you use `+=` that you're duplicating and creating a new array.</span></span> <span data-ttu-id="5eda3-335">Si ce n’est pas un problème pour les petits jeux de données, la scalabilité est en revanche extrêmement mauvaise.</span><span class="sxs-lookup"><span data-stu-id="5eda3-335">This is a not an issue for small datasets but it scales extremely poorly.</span></span>

### <a name="pipeline-assignment"></a><span data-ttu-id="5eda3-336">Assignation de pipeline</span><span class="sxs-lookup"><span data-stu-id="5eda3-336">Pipeline assignment</span></span>

<span data-ttu-id="5eda3-337">Vous pouvez assigner les résultats de n’importe quel pipeline dans une variable.</span><span class="sxs-lookup"><span data-stu-id="5eda3-337">You can assign the results of any pipeline into a variable.</span></span> <span data-ttu-id="5eda3-338">Il s’agit d’un tableau s’il contient plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="5eda3-338">It's an array if it contains multiple items.</span></span>

```powershell
$array = 1..5 | ForEach-Object {
    "ATX-SQL-$PSItem"
}
```

<span data-ttu-id="5eda3-339">En général, les pipelines PowerShell classiques à une ligne sont ceux qui viennent le plus souvent à l’esprit.</span><span class="sxs-lookup"><span data-stu-id="5eda3-339">Normally when we think of using the pipeline, we think of the typical PowerShell one-liners.</span></span> <span data-ttu-id="5eda3-340">Il est possible d’exploiter le pipeline avec des instructions `foreach()` et d’autres boucles.</span><span class="sxs-lookup"><span data-stu-id="5eda3-340">We can leverage the pipeline with `foreach()` statements and other loops.</span></span> <span data-ttu-id="5eda3-341">Au lieu d’ajouter des éléments à un tableau dans une boucle, nous pouvons ainsi déposer des éléments sur le pipeline.</span><span class="sxs-lookup"><span data-stu-id="5eda3-341">So instead of adding items to an array in a loop, we can drop items onto the pipeline.</span></span>

```powershell
$array = foreach ( $node in (1..5))
{
    "ATX-SQL-$node"
}
```

<span data-ttu-id="5eda3-342">En assignant les résultats de `foreach` à une variable, nous capturons tous les objets et créons un tableau unique.</span><span class="sxs-lookup"><span data-stu-id="5eda3-342">By assigning the results of the `foreach` to a variable, we capture all the objects and create a single array.</span></span>

## <a name="array-types"></a><span data-ttu-id="5eda3-343">Types de tableaux</span><span class="sxs-lookup"><span data-stu-id="5eda3-343">Array Types</span></span>

<span data-ttu-id="5eda3-344">Par défaut, un tableau dans PowerShell est créé avec le type `[PSObject[]]`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-344">By default, an array in PowerShell is created as a `[PSObject[]]` type.</span></span> <span data-ttu-id="5eda3-345">Cela lui permet de contenir n’importe quel type d’objet ou de valeur,</span><span class="sxs-lookup"><span data-stu-id="5eda3-345">This allows it to contain any type of object or value.</span></span> <span data-ttu-id="5eda3-346">car tout est hérité du type de `PSObject`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-346">This works because everything is inherited from the `PSObject` type.</span></span>

### <a name="strongly-typed-arrays"></a><span data-ttu-id="5eda3-347">Tableaux fortement typés</span><span class="sxs-lookup"><span data-stu-id="5eda3-347">Strongly typed arrays</span></span>

<span data-ttu-id="5eda3-348">On peut créer un tableau de n’importe quel type suivant une syntaxe similaire.</span><span class="sxs-lookup"><span data-stu-id="5eda3-348">You can create an array of any type using a similar syntax.</span></span> <span data-ttu-id="5eda3-349">Un tableau fortement typé ne peut contenir que des valeurs ou des objets du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="5eda3-349">When you create a strongly typed array, it can only contain values or objects the specified type.</span></span>

```powershell
PS> [int[]] $numbers = 1,2,3
PS> [int[]] $numbers2 = 'one','two','three'
ERROR: Cannot convert value "one" to type "System.Int32". Input string was not in a correct format."

PS> [string[]] $strings = 'one','two','three'
```

### <a name="arraylist"></a><span data-ttu-id="5eda3-350">ArrayList</span><span class="sxs-lookup"><span data-stu-id="5eda3-350">ArrayList</span></span>

<span data-ttu-id="5eda3-351">L’ajout d’éléments à un tableau est l’une de ses principales limitations, mais il existe d’autres collections qui permettent de résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="5eda3-351">Adding items to an array is one of its biggest limitations, but there are a few other collections that we can turn to that solve this problem.</span></span>

<span data-ttu-id="5eda3-352">`ArrayList` est généralement l’une des premières solutions qui viennent à l’esprit lorsque l’on a besoin d’un tableau plus rapide à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5eda3-352">The `ArrayList` is commonly one of the first things that we think of when we need an array that is faster to work with.</span></span> <span data-ttu-id="5eda3-353">Elle fonctionne comme un tableau d’objets là où c’est nécessaire, mais gère rapidement l’ajout d’éléments.</span><span class="sxs-lookup"><span data-stu-id="5eda3-353">It acts like an object array every place that we need it, but it handles adding items quickly.</span></span>

<span data-ttu-id="5eda3-354">Voici comment créer une `ArrayList` et y ajouter des éléments.</span><span class="sxs-lookup"><span data-stu-id="5eda3-354">Here is how we create an `ArrayList` and add items to it.</span></span>

```powershell
$myarray = [System.Collections.ArrayList]::new()
[void]$myArray.Add('Value')
```

<span data-ttu-id="5eda3-355">Nous appelons .NET pour obtenir ce type.</span><span class="sxs-lookup"><span data-stu-id="5eda3-355">We are calling into .NET to get this type.</span></span> <span data-ttu-id="5eda3-356">Dans ce cas, nous utilisons le constructeur par défaut pour le créer.</span><span class="sxs-lookup"><span data-stu-id="5eda3-356">In this case, we are using the default constructor to create it.</span></span> <span data-ttu-id="5eda3-357">Ensuite, nous appelons la méthode `Add` afin d’y ajouter un élément.</span><span class="sxs-lookup"><span data-stu-id="5eda3-357">Then we call the `Add` method to add an item to it.</span></span>

<span data-ttu-id="5eda3-358">La présence de `[void]` au début de la ligne permet de supprimer le code de retour.</span><span class="sxs-lookup"><span data-stu-id="5eda3-358">The reason I'm using `[void]` at the beginning of the line is to suppress the return code.</span></span> <span data-ttu-id="5eda3-359">Certains appels .NET produisent en effet une sortie inattendue.</span><span class="sxs-lookup"><span data-stu-id="5eda3-359">Some .NET calls do this and can create unexpected output.</span></span>

<span data-ttu-id="5eda3-360">Si les seules données du tableau sont des chaînes, examinez également [StringBuilder][].</span><span class="sxs-lookup"><span data-stu-id="5eda3-360">If the only data that you have in your array is strings, then also take a look at using [StringBuilder][].</span></span> <span data-ttu-id="5eda3-361">Il s’agit presque de la même chose, mais certaines de ses méthodes servent uniquement à traiter les chaînes.</span><span class="sxs-lookup"><span data-stu-id="5eda3-361">It's almost the same thing but has some methods that are just for dealing with strings.</span></span> <span data-ttu-id="5eda3-362">`StringBuilder` est spécialement conçu pour optimiser les performances.</span><span class="sxs-lookup"><span data-stu-id="5eda3-362">The `StringBuilder` is specially designed for performance.</span></span>

<span data-ttu-id="5eda3-363">Il est courant de voir des gens abandonner les tableaux pour passer aux `ArrayList`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-363">It's common to see people move to `ArrayList` from arrays.</span></span> <span data-ttu-id="5eda3-364">Cependant, cette pratique provient de l’époque où C# ne bénéficiait pas d’une prise en charge générique.</span><span class="sxs-lookup"><span data-stu-id="5eda3-364">But it comes from a time where C# didn't have generic support.</span></span> <span data-ttu-id="5eda3-365">`ArrayList` est déprécié en faveur de la `List[]` générique.</span><span class="sxs-lookup"><span data-stu-id="5eda3-365">The `ArrayList` is deprecated in support for the generic `List[]`</span></span>

### <a name="generic-list"></a><span data-ttu-id="5eda3-366">List générique</span><span class="sxs-lookup"><span data-stu-id="5eda3-366">Generic List</span></span>

<span data-ttu-id="5eda3-367">Un type générique est un type spécial dans C# qui définit une classe généralisée ; l’utilisateur spécifie les types de données qu’il utilise lors de sa création.</span><span class="sxs-lookup"><span data-stu-id="5eda3-367">A generic type is a special type in C# that defines a generalized class and the user specifies the data types it uses when created.</span></span> <span data-ttu-id="5eda3-368">Pour obtenir une liste de nombres ou de chaînes, vous devez donc définir une liste de types `int` ou `string`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-368">So if you want a list of numbers or strings, you would define that you want list of `int` or `string` types.</span></span>

<span data-ttu-id="5eda3-369">Voici comment créer une liste de chaînes.</span><span class="sxs-lookup"><span data-stu-id="5eda3-369">Here is how you create a List for strings.</span></span>

```powershell
$mylist = [System.Collections.Generic.List[string]]::new()
```

<span data-ttu-id="5eda3-370">Et voici une liste de nombres.</span><span class="sxs-lookup"><span data-stu-id="5eda3-370">Or a list for numbers.</span></span>

```powershell
$mylist = [System.Collections.Generic.List[int]]::new()
```

<span data-ttu-id="5eda3-371">Il est possible d’effectuer une conversion de type (transtypage) d’un tableau existant en une liste comme celle-ci sans créer l’objet au préalable :</span><span class="sxs-lookup"><span data-stu-id="5eda3-371">We can cast an existing array to a list like this without creating the object first:</span></span>

```powershell
$mylist = [System.Collections.Generic.List[int]]@(1,2,3)
```

<span data-ttu-id="5eda3-372">La syntaxe peut être raccourcie avec l’instruction `using namespace` dans la version 5 et les versions ultérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5eda3-372">We can shorten the syntax with the `using namespace` statement in PowerShell 5 and newer.</span></span> <span data-ttu-id="5eda3-373">L’instruction `using` doit apparaître en première ligne du script.</span><span class="sxs-lookup"><span data-stu-id="5eda3-373">The `using` statement needs to be the first line of your script.</span></span> <span data-ttu-id="5eda3-374">Avec PowerShell, déclarer un espace de noms permet d’éviter de le mentionner dans les types de données lorsque vous y faites référence.</span><span class="sxs-lookup"><span data-stu-id="5eda3-374">By declaring a namespace, PowerShell lets you leave it off of the data types when you reference them.</span></span>

```powershell
using namespace System.Collections.Generic
$myList = [List[int]]@(1,2,3)
```

<span data-ttu-id="5eda3-375">`List` devient ainsi bien plus facile à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5eda3-375">This makes the `List` much more usable.</span></span>

<span data-ttu-id="5eda3-376">Il existe une méthode `Add` similaire.</span><span class="sxs-lookup"><span data-stu-id="5eda3-376">You have a similar `Add` method available to you.</span></span> <span data-ttu-id="5eda3-377">Contrairement à ArrayList, il n’y a aucune valeur de retour sur la méthode `Add` ; il n’est donc pas nécessaire de la rendre `void`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-377">Unlike the ArrayList, there is no return value on the `Add` method so we don't have to `void` it.</span></span>

```powershell
$myList.Add(10)
```

<span data-ttu-id="5eda3-378">Comme pour les autres tableaux, les éléments restent accessibles.</span><span class="sxs-lookup"><span data-stu-id="5eda3-378">And we can still access the elements like other arrays.</span></span>

```powershell
PS> $myList[-1]
10
```

#### <a name="listpsobject"></a><span data-ttu-id="5eda3-379">List[PSObject]</span><span class="sxs-lookup"><span data-stu-id="5eda3-379">List[PSObject]</span></span>

<span data-ttu-id="5eda3-380">Une liste peut être de n’importe quel type. Cependant, si vous ne connaissez pas le type des objets, vous pouvez utiliser `[List[PSObject]]` pour les contenir.</span><span class="sxs-lookup"><span data-stu-id="5eda3-380">You can have a list of any type, but when you don't know the type of objects, you can use `[List[PSObject]]` to contain them.</span></span>

```powershell
$list = [List[PSObject]]::new()
```

#### <a name="remove"></a><span data-ttu-id="5eda3-381">Remove()</span><span class="sxs-lookup"><span data-stu-id="5eda3-381">Remove()</span></span>

<span data-ttu-id="5eda3-382">`ArrayList` et la `List[]` générique prennent tous deux en charge la suppression d’éléments de la collection.</span><span class="sxs-lookup"><span data-stu-id="5eda3-382">The `ArrayList` and the generic `List[]` both support removing items from the collection.</span></span>

```powershell
using namespace System.Collections.Generic
$myList = [List[string]]@('Zero','One','Two','Three')
[void]$myList.Remove("Two")
Zero
One
Three
```

<span data-ttu-id="5eda3-383">Si vous utilisez des types valeur, il supprime le premier de la liste.</span><span class="sxs-lookup"><span data-stu-id="5eda3-383">When working with value types, it removes the first one from the list.</span></span> <span data-ttu-id="5eda3-384">Vous pouvez l’appeler à nouveau pour continuer à supprimer cette valeur.</span><span class="sxs-lookup"><span data-stu-id="5eda3-384">You can call it over and over again to keep removing that value.</span></span> <span data-ttu-id="5eda3-385">Avec des types référence, vous devez indiquer l’objet que vous souhaitez supprimer.</span><span class="sxs-lookup"><span data-stu-id="5eda3-385">If you have reference types, you have to provide the object that you want removed.</span></span>

```powershell
[list[System.Management.Automation.PSDriveInfo]]$drives = Get-PSDrive
$drives.remove($drives[2])
```

```powershell
$delete = $drives[2]
$drives.remove($delete)
```

<span data-ttu-id="5eda3-386">La méthode remove retourne `true` si elle a pu trouver l’élément et le supprimer de la collection.</span><span class="sxs-lookup"><span data-stu-id="5eda3-386">The remove method returns `true` if it was able to find and remove the item from the collection.</span></span>

### <a name="more-collections"></a><span data-ttu-id="5eda3-387">Autres collections</span><span class="sxs-lookup"><span data-stu-id="5eda3-387">More collections</span></span>

<span data-ttu-id="5eda3-388">De nombreuses autres collections peuvent être utilisées, mais nous avons vu les bonnes solutions génériques de remplacement des tableaux.</span><span class="sxs-lookup"><span data-stu-id="5eda3-388">There are many other collections that can be used but these are the good generic array replacements.</span></span>
<span data-ttu-id="5eda3-389">Pour plus d’informations sur ces autres options, consultez ce [Guist](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c) compilé par [Mark Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html).</span><span class="sxs-lookup"><span data-stu-id="5eda3-389">If you're interested in learning about more of these options, take a look at this [Gist](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c) that [Mark Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html) put together.</span></span>

## <a name="other-nuances"></a><span data-ttu-id="5eda3-390">Autres nuances</span><span class="sxs-lookup"><span data-stu-id="5eda3-390">Other nuances</span></span>

<span data-ttu-id="5eda3-391">Maintenant que nous avons couvert toutes les fonctionnalités majeures, voici quelques points importants à signaler avant de conclure.</span><span class="sxs-lookup"><span data-stu-id="5eda3-391">Now that I have covered all the major functionality, here are a few more things that I wanted to mention before I wrap this up.</span></span>

### <a name="pre-sized-arrays"></a><span data-ttu-id="5eda3-392">Tableaux de taille prédéfinie</span><span class="sxs-lookup"><span data-stu-id="5eda3-392">Pre-sized arrays</span></span>

<span data-ttu-id="5eda3-393">Nous avons indiqué que la taille d’un tableau n’est pas modifiable une fois qu’il a été créé.</span><span class="sxs-lookup"><span data-stu-id="5eda3-393">I mentioned that you can't change the size of an array once it's created.</span></span> <span data-ttu-id="5eda3-394">Il est possible de créer un tableau d’une taille prédéfinie en l’appelant avec le constructeur `new($size)`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-394">We can create an array of a pre-determined size by calling it with the `new($size)` constructor.</span></span>

```powershell
$data = [Object[]]::new(4)
$data.count
4
```

### <a name="multiplying-arrays"></a><span data-ttu-id="5eda3-395">Multiplication de tableaux</span><span class="sxs-lookup"><span data-stu-id="5eda3-395">Multiplying arrays</span></span>

<span data-ttu-id="5eda3-396">Petite astuce intéressante : il est possible de multiplier un tableau par un entier.</span><span class="sxs-lookup"><span data-stu-id="5eda3-396">An interesting little trick is that you can multiply an array by an integer.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data * 3
red
green
blue
red
green
blue
red
green
blue
```

### <a name="initialize-with-0"></a><span data-ttu-id="5eda3-397">Initialisation avec 0</span><span class="sxs-lookup"><span data-stu-id="5eda3-397">Initialize with 0</span></span>

<span data-ttu-id="5eda3-398">Il arrive fréquemment que l’on doive créer un tableau comportant uniquement des zéros.</span><span class="sxs-lookup"><span data-stu-id="5eda3-398">A common scenario is that you want to create an array with all zeros.</span></span> <span data-ttu-id="5eda3-399">S’il n’est censé contenir que des entiers, vous pouvez utiliser un tableau fortement typé d’entiers, par défaut défini sur des zéros.</span><span class="sxs-lookup"><span data-stu-id="5eda3-399">If you're only going to have integers, a strongly typed array of integers defaults to all zeros.</span></span>

```powershell
PS> [int[]]::new(4)
0
0
0
0
```

<span data-ttu-id="5eda3-400">L’astuce de la multiplication permet également de parvenir à ce résultat.</span><span class="sxs-lookup"><span data-stu-id="5eda3-400">We can use the multiplying trick to do this too.</span></span>

```powershell
PS> $data = @(0) * 4
PS> $data
0
0
0
0
```

<span data-ttu-id="5eda3-401">L’avantage de la multiplication est qu’elle permet d’utiliser n’importe quelle valeur.</span><span class="sxs-lookup"><span data-stu-id="5eda3-401">The nice thing about the multiplying trick is that you can use any value.</span></span> <span data-ttu-id="5eda3-402">C’est un bon moyen d’obtenir par exemple `255` comme valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="5eda3-402">So if you would rather have `255` as your default value, this would be a good way to do it.</span></span>

```powershell
PS> $data = @(255) * 4
PS> $data
255
255
255
255
```

### <a name="nested-arrays"></a><span data-ttu-id="5eda3-403">Tableaux imbriqués</span><span class="sxs-lookup"><span data-stu-id="5eda3-403">Nested arrays</span></span>

<span data-ttu-id="5eda3-404">Un tableau qui se trouve à l’intérieur d’un tableau est appelé tableau imbriqué.</span><span class="sxs-lookup"><span data-stu-id="5eda3-404">An array inside an array is called a nested array.</span></span> <span data-ttu-id="5eda3-405">Je ne les utilise pas beaucoup dans PowerShell, à la différence d’autres langages.</span><span class="sxs-lookup"><span data-stu-id="5eda3-405">I don't use these much in PowerShell but I have used them more in other languages.</span></span> <span data-ttu-id="5eda3-406">Envisagez d’avoir recours à un tableau de tableaux lorsque vos données suivent un modèle de type grille.</span><span class="sxs-lookup"><span data-stu-id="5eda3-406">Consider using an array of arrays when your data fits in a grid like pattern.</span></span>

<span data-ttu-id="5eda3-407">Voici deux façons de créer un tableau à deux dimensions.</span><span class="sxs-lookup"><span data-stu-id="5eda3-407">Here are two ways we can create a two-dimensional array.</span></span>

```powershell
$data = @(@(1,2,3),@(4,5,6),@(7,8,9))

$data2 = @(
    @(1,2,3),
    @(4,5,6),
    @(7,8,9)
)
```

<span data-ttu-id="5eda3-408">La virgule est très importante dans ces exemples.</span><span class="sxs-lookup"><span data-stu-id="5eda3-408">The comma is very important in those examples.</span></span> <span data-ttu-id="5eda3-409">Dans le précédent exemple de tableau normal sur plusieurs lignes, la virgule était facultative.</span><span class="sxs-lookup"><span data-stu-id="5eda3-409">I gave an earlier example of a normal array on multiple lines where the comma was optional.</span></span> <span data-ttu-id="5eda3-410">Ce n’est pas le cas avec un tableau multidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="5eda3-410">That isn't the case with a multi-dimensional array.</span></span>

<span data-ttu-id="5eda3-411">La notation d’index change légèrement avec un tableau imbriqué.</span><span class="sxs-lookup"><span data-stu-id="5eda3-411">The way we use the index notation changes slightly now that we've a nested array.</span></span> <span data-ttu-id="5eda3-412">Reprenons `$data` de l’exemple ci-dessus. La valeur 3 est accessible de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="5eda3-412">Using the `$data` above, this is how we would access the value 3.</span></span>

```powershell
PS> $outside = 0
PS> $inside = 2
PS> $data[$outside][$inside]
3
```

<span data-ttu-id="5eda3-413">Ajoutez un ensemble de crochets pour chaque niveau d’imbrication de tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-413">Add a set of bracket for each level of array nesting.</span></span> <span data-ttu-id="5eda3-414">Le premier concerne le tableau situé le plus à l’extérieur, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="5eda3-414">The first set of brackets is for the outer most array and then you work your way in from there.</span></span>

### <a name="write-output--noenumerate"></a><span data-ttu-id="5eda3-415">Write-Output -NoEnumerate</span><span class="sxs-lookup"><span data-stu-id="5eda3-415">Write-Output -NoEnumerate</span></span>

<span data-ttu-id="5eda3-416">PowerShell a tendance à désenvelopper ou énumérer les tableaux.</span><span class="sxs-lookup"><span data-stu-id="5eda3-416">PowerShell likes to unwrap or enumerate arrays.</span></span> <span data-ttu-id="5eda3-417">Il s’agit d’un aspect fondamental de la façon dont il utilise le pipeline. Cependant, ce comportement n’est pas toujours souhaitable.</span><span class="sxs-lookup"><span data-stu-id="5eda3-417">This is a core aspect of the way PowerShell uses the pipeline but there are times that you don't want that to happen.</span></span>

<span data-ttu-id="5eda3-418">J’utilise souvent le pipe pour envoyer les objets vers `Get-Member` afin d’en savoir plus à leur sujet.</span><span class="sxs-lookup"><span data-stu-id="5eda3-418">I commonly pipe objects to `Get-Member` to learn more about them.</span></span> <span data-ttu-id="5eda3-419">Lorsqu’il s’agit d’un tableau, il est désenveloppé ; Get-Member voit ses membres et non le tableau proprement dit.</span><span class="sxs-lookup"><span data-stu-id="5eda3-419">When I pipe an array to it, it gets unwrapped and Get-Member sees the members of the array and not the actual array.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data | Get-Member
TypeName: System.String
...
```

<span data-ttu-id="5eda3-420">Pour éviter cette désencapsulation du tableau, vous pouvez utiliser `Write-Object -NoEnumerate`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-420">To prevent that unwrap of the array, you can use `Write-Object -NoEnumerate`.</span></span>

```powershell
PS> Write-Output -NoEnumerate $data | Get-Member
TypeName: System.Object[]
...
```

<span data-ttu-id="5eda3-421">Il existe un deuxième moyen de le faire, moins conventionnel et potentiellement à éviter.</span><span class="sxs-lookup"><span data-stu-id="5eda3-421">I have a second way that's more of a hack (and I try to avoid hacks like this).</span></span> <span data-ttu-id="5eda3-422">Vous pouvez placer une virgule devant le tableau avant d’utiliser le pipe.</span><span class="sxs-lookup"><span data-stu-id="5eda3-422">You can place a comma in front of the array before you pipe it.</span></span>

```powershell
PS> ,$data | Get-Member
TypeName: System.Object[]
...
```

### <a name="return-an-array"></a><span data-ttu-id="5eda3-423">Tableau retourné</span><span class="sxs-lookup"><span data-stu-id="5eda3-423">Return an array</span></span>

<span data-ttu-id="5eda3-424">Ce désenveloppement des tableaux se produit également lorsqu’une fonction renvoie ou retourne des valeurs.</span><span class="sxs-lookup"><span data-stu-id="5eda3-424">This unwrapping of arrays also happens when you output or return values from a function.</span></span> <span data-ttu-id="5eda3-425">Ce n’est généralement pas un problème, car il reste possible d’obtenir un tableau si la sortie est assignée à une variable.</span><span class="sxs-lookup"><span data-stu-id="5eda3-425">You can still get an array if you assign the output to a variable so this isn't commonly an issue.</span></span>

<span data-ttu-id="5eda3-426">Cependant, il s’agit alors d’un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="5eda3-426">The catch is that you have a new array.</span></span> <span data-ttu-id="5eda3-427">Si ce point pose problème, vous pouvez utiliser `Write-Output -NoEnumerate $array` ou `return ,$array` pour le contourner.</span><span class="sxs-lookup"><span data-stu-id="5eda3-427">If that is ever a problem, you can use `Write-Output -NoEnumerate $array` or `return ,$array` to work around it.</span></span>

## <a name="anything-else"></a><span data-ttu-id="5eda3-428">Autre chose ?</span><span class="sxs-lookup"><span data-stu-id="5eda3-428">Anything else?</span></span>

<span data-ttu-id="5eda3-429">Cet article comprend beaucoup d’informations.</span><span class="sxs-lookup"><span data-stu-id="5eda3-429">I know this is all a lot to take in.</span></span> <span data-ttu-id="5eda3-430">Nous espérons qu’il vous apprendra quelque chose chaque fois que vous le lirez et qu’il vous servira longtemps de référence.</span><span class="sxs-lookup"><span data-stu-id="5eda3-430">My hope is that you learn something from this article every time you read it and that it turns out to be a good reference for you for a long time to come.</span></span> <span data-ttu-id="5eda3-431">S’il vous a été utile, veuillez le partager avec d’autres personnes qui pourraient le trouver intéressant.</span><span class="sxs-lookup"><span data-stu-id="5eda3-431">If you found this to be helpful, please share it with others you think may get value out of it.</span></span>

<span data-ttu-id="5eda3-432">Nous vous recommandons de consulter maintenant un billet similaire sur les [tables de hachage][].</span><span class="sxs-lookup"><span data-stu-id="5eda3-432">From here, I would recommend you check out a similar post that I wrote about [hashtables][].</span></span>

<!-- link references -->
[Version d’origine]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[original version]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Tableaux]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Instruction switch]: everything-about-switch.md
[switch statement]: everything-about-switch.md
[Tables de hachage]: everything-about-hashtable.md
[hashtables]: everything-about-hashtable.md
[Les nombreuses façons d’utiliser les regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[The many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[Comment vérifier la correspondance entre chacune des valeurs d’un tableau et une valeur donnée]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[how to verify that every value in an array matches a given value]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[Solution]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[solution]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[StringBuilder]: https://powershellexplained.com/2017-11-20-Powershell-StringBuilder/
