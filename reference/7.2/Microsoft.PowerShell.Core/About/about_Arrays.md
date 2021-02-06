---
description: Décrit les tableaux, qui sont des structures de données conçues pour stocker des collections d’éléments.
Locale: en-US
ms.date: 08/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arrays?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arrays
ms.openlocfilehash: 2e7cf9c8f7d4e6f1d5bc66310f56d3de9461e592
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595511"
---
# <a name="about-arrays"></a><span data-ttu-id="7d0b8-103">À propos des tableaux</span><span class="sxs-lookup"><span data-stu-id="7d0b8-103">About Arrays</span></span>

## <a name="short-description"></a><span data-ttu-id="7d0b8-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="7d0b8-104">Short Description</span></span>
<span data-ttu-id="7d0b8-105">Décrit les tableaux, qui sont des structures de données conçues pour stocker des collections d’éléments.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-105">Describes arrays, which are data structures designed to store collections of items.</span></span>

## <a name="long-description"></a><span data-ttu-id="7d0b8-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="7d0b8-106">Long Description</span></span>

<span data-ttu-id="7d0b8-107">Un tableau est une structure de données conçue pour stocker une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-107">An array is a data structure that is designed to store a collection of items.</span></span>
<span data-ttu-id="7d0b8-108">Les éléments peuvent être du même type ou de types différents.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-108">The items can be the same type or different types.</span></span>

<span data-ttu-id="7d0b8-109">À compter de Windows PowerShell 3,0, une collection de zéro ou un objet a des propriétés de tableaux.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-109">Beginning in Windows PowerShell 3.0, a collection of zero or one object has some properties of arrays.</span></span>

## <a name="creating-and-initializing-an-array"></a><span data-ttu-id="7d0b8-110">Création et initialisation d’un tableau</span><span class="sxs-lookup"><span data-stu-id="7d0b8-110">Creating and initializing an array</span></span>

<span data-ttu-id="7d0b8-111">Pour créer et initialiser un tableau, assignez plusieurs valeurs à une variable.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-111">To create and initialize an array, assign multiple values to a variable.</span></span> <span data-ttu-id="7d0b8-112">Les valeurs stockées dans le tableau sont délimitées par une virgule et séparées du nom de la variable par l’opérateur d’assignation ( `=` ).</span><span class="sxs-lookup"><span data-stu-id="7d0b8-112">The values stored in the array are delimited with a comma and separated from the variable name by the assignment operator (`=`).</span></span>

<span data-ttu-id="7d0b8-113">Par exemple, pour créer un tableau nommé `$A` qui contient les sept valeurs numériques (int) de 22, 5, 10, 8, 12, 9 et 80, tapez :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-113">For example, to create an array named `$A` that contains the seven numeric (int) values of 22, 5, 10, 8, 12, 9, and 80, type:</span></span>

```powershell
$A = 22,5,10,8,12,9,80
```

<span data-ttu-id="7d0b8-114">La virgule peut également être utilisée pour initialiser un tableau à un seul élément en plaçant la virgule avant l’élément unique.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-114">The comma can also be used to initialize a single item array by placing the comma before the single item.</span></span>

<span data-ttu-id="7d0b8-115">Par exemple, pour créer un tableau d’éléments unique nommé `$B` contenant la valeur unique 7, tapez :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-115">For example, to create a single item array named `$B` containing the single value of 7, type:</span></span>

```powershell
$B = ,7
```

<span data-ttu-id="7d0b8-116">Vous pouvez également créer et initialiser un tableau à l’aide de l’opérateur de plage ( `..` ).</span><span class="sxs-lookup"><span data-stu-id="7d0b8-116">You can also create and initialize an array by using the range operator (`..`).</span></span>
<span data-ttu-id="7d0b8-117">L’exemple suivant crée un tableau contenant les valeurs de 5 à 8.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-117">The following example creates an array containing the values 5 through 8.</span></span>

```powershell
$C = 5..8
```

<span data-ttu-id="7d0b8-118">En conséquence, `$C` contient quatre valeurs : 5, 6, 7 et 8.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-118">As a result, `$C` contains four values: 5, 6, 7, and 8.</span></span>

<span data-ttu-id="7d0b8-119">Quand aucun type de données n’est spécifié, PowerShell crée chaque tableau en tant que tableau d’objets (**System. Object []**).</span><span class="sxs-lookup"><span data-stu-id="7d0b8-119">When no data type is specified, PowerShell creates each array as an object array (**System.Object[]**).</span></span> <span data-ttu-id="7d0b8-120">Pour déterminer le type de données d’un tableau, utilisez la méthode **GetType ()** .</span><span class="sxs-lookup"><span data-stu-id="7d0b8-120">To determine the data type of an array, use the **GetType()** method.</span></span> <span data-ttu-id="7d0b8-121">Par exemple, pour déterminer le type de données du `$A` tableau, tapez :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-121">For example, to determine the data type of the `$A` array, type:</span></span>

```powershell
$A.GetType()
```

<span data-ttu-id="7d0b8-122">Pour créer un tableau fortement typé, autrement dit un tableau qui peut contenir uniquement des valeurs d’un type particulier, effectuez un cast de la variable en type tableau, tel que **String []**, **long []** ou **Int32 []**.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-122">To create a strongly typed array, that is, an array that can contain only values of a particular type, cast the variable as an array type, such as **string[]**, **long[]**, or **int32[]**.</span></span> <span data-ttu-id="7d0b8-123">Pour effectuer un cast d’un tableau, faites précéder le nom de la variable d’un type de tableau entre crochets.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-123">To cast an array, precede the variable name with an array type enclosed in brackets.</span></span> <span data-ttu-id="7d0b8-124">Par exemple, pour créer un tableau d’entiers 32 bits nommé `$ia` contenant quatre entiers (1500, 2230, 3350 et 4000), tapez :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-124">For example, to create a 32-bit integer array named `$ia` containing four integers (1500, 2230, 3350, and 4000), type:</span></span>

```powershell
[int32[]]$ia = 1500,2230,3350,4000
```

<span data-ttu-id="7d0b8-125">Par conséquent, le `$ia` tableau peut contenir uniquement des entiers.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-125">As a result, the `$ia` array can contain only integers.</span></span>

<span data-ttu-id="7d0b8-126">Vous pouvez créer des tableaux qui sont convertis en n’importe quel type pris en charge dans le Framework Microsoft .NET.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-126">You can create arrays that are cast to any supported type in the Microsoft .NET Framework.</span></span> <span data-ttu-id="7d0b8-127">Par exemple, les objets qui `Get-Process` récupèrent pour représenter des processus sont du type **System. Diagnostics. Process** .</span><span class="sxs-lookup"><span data-stu-id="7d0b8-127">For example, the objects that `Get-Process` retrieves to represent processes are of the **System.Diagnostics.Process** type.</span></span> <span data-ttu-id="7d0b8-128">Pour créer un tableau d’objets de processus fortement typé, entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-128">To create a strongly typed array of process objects, enter the following command:</span></span>

```powershell
[Diagnostics.Process[]]$zz = Get-Process
```

## <a name="the-array-sub-expression-operator"></a><span data-ttu-id="7d0b8-129">Opérateur de sous-expression de tableau</span><span class="sxs-lookup"><span data-stu-id="7d0b8-129">The array sub-expression operator</span></span>

<span data-ttu-id="7d0b8-130">L’opérateur de sous-expression de tableau crée un tableau à partir des instructions qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-130">The array sub-expression operator creates an array from the statements inside it.</span></span> <span data-ttu-id="7d0b8-131">Quelle que soit l’instruction produite par l’opérateur, l’opérateur la place dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-131">Whatever the statement inside the operator produces, the operator will place it in an array.</span></span> <span data-ttu-id="7d0b8-132">Même s’il y a zéro ou un objet.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-132">Even if there is zero or one object.</span></span>

<span data-ttu-id="7d0b8-133">La syntaxe de l’opérateur Array est la suivante :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-133">The syntax of the array operator is as follows:</span></span>

```syntax
@( ... )
```

<span data-ttu-id="7d0b8-134">Vous pouvez utiliser l’opérateur de tableau pour créer un tableau de zéro ou un objet.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-134">You can use the array operator to create an array of zero or one object.</span></span> <span data-ttu-id="7d0b8-135">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-135">For example:</span></span>

```powershell
$a = @("Hello World")
$a.Count
```

```Output
1
```

```powershell
$b = @()
$b.Count
```

```Output
0
```

<span data-ttu-id="7d0b8-136">L’opérateur Array est utile dans les scripts lorsque vous obtenez des objets, mais que vous ne connaissez pas le nombre d’objets que vous obtenez.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-136">The array operator is useful in scripts when you are getting objects, but do not know how many objects you get.</span></span> <span data-ttu-id="7d0b8-137">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-137">For example:</span></span>

```powershell
$p = @(Get-Process Notepad)
```

<span data-ttu-id="7d0b8-138">Pour plus d’informations sur l’opérateur de sous-expression de tableau, consultez [about_Operators](about_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="7d0b8-138">For more information about the array sub-expression operator, see [about_Operators](about_Operators.md).</span></span>

## <a name="accessing-and-using-array-elements"></a><span data-ttu-id="7d0b8-139">Accès et utilisation d’éléments de tableau</span><span class="sxs-lookup"><span data-stu-id="7d0b8-139">Accessing and using array elements</span></span>

### <a name="reading-an-array"></a><span data-ttu-id="7d0b8-140">Lecture d’un tableau</span><span class="sxs-lookup"><span data-stu-id="7d0b8-140">Reading an array</span></span>

<span data-ttu-id="7d0b8-141">Vous pouvez faire référence à un tableau à l’aide de son nom de variable.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-141">You can refer to an array by using its variable name.</span></span> <span data-ttu-id="7d0b8-142">Pour afficher tous les éléments du tableau, tapez le nom du tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-142">To display all the elements in the array, type the array name.</span></span> <span data-ttu-id="7d0b8-143">Par exemple, en supposant `$a` que est un tableau contenant des entiers 0, 1, 2, jusqu’à 9, en tapant :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-143">For example, assuming `$a` is an array containing integers 0, 1, 2, until 9; typing:</span></span>

```powershell
$a
```

```Output
0
1
2
3
4
5
6
7
8
9
```

<span data-ttu-id="7d0b8-144">Vous pouvez faire référence aux éléments d’un tableau à l’aide d’un index, en commençant à la position 0.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-144">You can refer to the elements in an array by using an index, beginning at position 0.</span></span> <span data-ttu-id="7d0b8-145">Placez le numéro d’index entre crochets.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-145">Enclose the index number in brackets.</span></span> <span data-ttu-id="7d0b8-146">Par exemple, pour afficher le premier élément du `$a` tableau, tapez :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-146">For example, to display the first element in the `$a` array, type:</span></span>

```powershell
$a[0]
```

```Output
0
```

<span data-ttu-id="7d0b8-147">Pour afficher le troisième élément dans le `$a` tableau, tapez :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-147">To display the third element in the `$a` array, type:</span></span>

```powershell
$a[2]
```

```Output
2
```

<span data-ttu-id="7d0b8-148">Vous pouvez récupérer une partie du tableau à l’aide d’un opérateur de plage pour l’index.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-148">You can retrieve part of the array using a range operator for the index.</span></span> <span data-ttu-id="7d0b8-149">Par exemple, pour récupérer les deuxième et cinquième éléments du tableau, vous devez taper :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-149">For example, to retrieve the second to fifth elements of the array, you would type:</span></span>

```powershell
$a[1..4]
```

```Output
1
2
3
4
```

<span data-ttu-id="7d0b8-150">Nombre de nombres négatifs à partir de la fin du tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-150">Negative numbers count from the end of the array.</span></span> <span data-ttu-id="7d0b8-151">Par exemple, « -1 » fait référence au dernier élément du tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-151">For example, "-1" refers to the last element of the array.</span></span> <span data-ttu-id="7d0b8-152">Pour afficher les trois derniers éléments du tableau, dans l’ordre croissant de l’index, tapez :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-152">To display the last three elements of the array, in index ascending order, type:</span></span>

```powershell
$a = 0 .. 9
$a[-3..-1]
```

```Output
7
8
9
```

<span data-ttu-id="7d0b8-153">Si vous tapez des index négatifs dans l’ordre décroissant, votre sortie change.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-153">If you type negative indexes in descending order, your output changes.</span></span>

```powershell
$a = 0 .. 9
$a[-1..-3]
```

```Output
9
8
7
```

<span data-ttu-id="7d0b8-154">Toutefois, soyez prudent lorsque vous utilisez cette notation.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-154">However, be cautious when using this notation.</span></span> <span data-ttu-id="7d0b8-155">La notation passe de la limite de fin au début du tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-155">The notation cycles from the end boundary to the beginning of the array.</span></span>

```powershell
$a = 0 .. 9
$a[2..-2]
```

```Output
2
1
0
9
8
```

<span data-ttu-id="7d0b8-156">En outre, une erreur courante consiste à supposer que `$a[0..-2]` fait référence à tous les éléments du tableau, à l’exception du dernier.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-156">Also, one common mistake is to assume `$a[0..-2]` refers to all the elements of the array, except for the last one.</span></span> <span data-ttu-id="7d0b8-157">Elle fait référence aux premier, dernier et dernier élément dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-157">It refers to the first, last, and second-to-last elements in the array.</span></span>

<span data-ttu-id="7d0b8-158">Vous pouvez utiliser l’opérateur plus ( `+` ) pour combiner des plages avec une liste d’éléments dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-158">You can use the plus operator (`+`) to combine a ranges with a list of elements in an array.</span></span> <span data-ttu-id="7d0b8-159">Par exemple, pour afficher les éléments aux positions d’index 0, 2 et 4 à 6, tapez :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-159">For example, to display the elements at index positions 0, 2, and 4 through 6, type:</span></span>

```powershell
$a = 0 .. 9
$a[0,2+4..6]
```

```Output
0
2
4
5
6
```

<span data-ttu-id="7d0b8-160">En outre, pour répertorier plusieurs plages et éléments individuels, vous pouvez utiliser l’opérateur plus.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-160">Also, to list multiple ranges and individual elements you can use the plus operator.</span></span> <span data-ttu-id="7d0b8-161">Par exemple, pour répertorier les éléments de zéro à deux, quatre à six et l’élément à huitième type de position :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-161">For example, to list elements zero to two, four to six, and the element at eighth positional type:</span></span>

```powershell
$a = 0..9
$a[+0..2+4..6+8]
```

```Output
0
1
2
4
5
6
8
```

### <a name="iterations-over-array-elements"></a><span data-ttu-id="7d0b8-162">Itérations sur les éléments de tableau</span><span class="sxs-lookup"><span data-stu-id="7d0b8-162">Iterations over array elements</span></span>

<span data-ttu-id="7d0b8-163">Vous pouvez également utiliser des constructions de boucle, telles que ForEach, pour et des boucles While, pour faire référence aux éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-163">You can also use looping constructs, such as ForEach, For, and While loops, to refer to the elements in an array.</span></span> <span data-ttu-id="7d0b8-164">Par exemple, pour utiliser une boucle ForEach afin d’afficher les éléments du `$a` tableau, tapez :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-164">For example, to use a ForEach loop to display the elements in the `$a` array, type:</span></span>

```powershell
$a = 0..9
foreach ($element in $a) {
  $element
}
```

```Output
0
1
2
3
4
5
6
7
8
9
```

<span data-ttu-id="7d0b8-165">La boucle ForEach itère au sein du tableau et retourne chaque valeur dans le tableau jusqu’à atteindre la fin du tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-165">The Foreach loop iterates through the array and returns each value in the array until reaching the end of the array.</span></span>

<span data-ttu-id="7d0b8-166">La boucle for est utile lorsque vous incrémentez des compteurs tout en examinant les éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-166">The For loop is useful when you are incrementing counters while examining the elements in an array.</span></span> <span data-ttu-id="7d0b8-167">Par exemple, pour utiliser une boucle for pour retourner toutes les autres valeurs dans un tableau, tapez :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-167">For example, to use a For loop to return every other value in an array, type:</span></span>

```powershell
$a = 0..9
for ($i = 0; $i -le ($a.length - 1); $i += 2) {
  $a[$i]
}
```

```Output
0
2
4
6
8
```

<span data-ttu-id="7d0b8-168">Vous pouvez utiliser une boucle while pour afficher les éléments d’un tableau jusqu’à ce qu’une condition définie n’ait plus la valeur true.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-168">You can use a While loop to display the elements in an array until a defined condition is no longer true.</span></span> <span data-ttu-id="7d0b8-169">Par exemple, pour afficher les éléments du `$a` tableau alors que l’index du tableau est inférieur à 4, tapez :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-169">For example, to display the elements in the `$a` array while the array index is less than 4, type:</span></span>

```powershell
$a = 0..9
$i=0
while($i -lt 4) {
  $a[$i];
  $i++
}
```

```Output
0
1
2
3
```

## <a name="properties-of-arrays"></a><span data-ttu-id="7d0b8-170">Propriétés des tableaux</span><span class="sxs-lookup"><span data-stu-id="7d0b8-170">Properties of arrays</span></span>

### <a name="count-or-length-or-longlength"></a><span data-ttu-id="7d0b8-171">Count ou Length ou LongLength</span><span class="sxs-lookup"><span data-stu-id="7d0b8-171">Count or Length or LongLength</span></span>

<span data-ttu-id="7d0b8-172">Pour déterminer le nombre d’éléments contenus dans un tableau, utilisez la `Length` propriété ou son `Count` alias.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-172">To determine how many items are in an array, use the `Length` property or its `Count` alias.</span></span> <span data-ttu-id="7d0b8-173">`Longlength` est utile si le tableau contient plus de 2 147 483 647 éléments.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-173">`Longlength` is useful if the array contains more than 2,147,483,647 elements.</span></span>

```powershell
$a = 0..9
$a.Count
$a.Length
```

```Output
10
10
```

### <a name="rank"></a><span data-ttu-id="7d0b8-174">Rank</span><span class="sxs-lookup"><span data-stu-id="7d0b8-174">Rank</span></span>

<span data-ttu-id="7d0b8-175">Retourne le nombre de dimensions du tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-175">Returns the number of dimensions in the array.</span></span> <span data-ttu-id="7d0b8-176">La plupart des tableaux dans PowerShell ont une seule dimension, uniquement.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-176">Most arrays in PowerShell have one dimension, only.</span></span> <span data-ttu-id="7d0b8-177">Même lorsque vous pensez que vous créez un tableau multidimensionnel ; comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-177">Even when you think you are building a multidimensional array; like the following example:</span></span>

```powershell
$a = @(
  @(0,1),
  @("b", "c"),
  @(Get-Process)
)

[int]$r = $a.Rank
"`$a rank: $r"
```

```Output
$a rank: 1
```

<span data-ttu-id="7d0b8-178">L’exemple suivant montre comment créer un tableau véritablement multidimensionnel à l’aide du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-178">The following example shows how to create a truly multidimensional array using the .Net Framework.</span></span>

```powershell
[int[,]]$rank2 = [int[,]]::new(5,5)
$rank2.rank
```

```Output
2
```

## <a name="methods-of-arrays"></a><span data-ttu-id="7d0b8-179">Méthodes de tableaux</span><span class="sxs-lookup"><span data-stu-id="7d0b8-179">Methods of arrays</span></span>

### <a name="clear"></a><span data-ttu-id="7d0b8-180">Clear</span><span class="sxs-lookup"><span data-stu-id="7d0b8-180">Clear</span></span>

<span data-ttu-id="7d0b8-181">Affecte à toutes les valeurs d’élément la _valeur par défaut_ du type d’élément du tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-181">Sets all element values to the _default value_ of the array's element type.</span></span>
<span data-ttu-id="7d0b8-182">La méthode Clear () ne réinitialise pas la taille du tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-182">The Clear() method does not reset the size of the array.</span></span>

<span data-ttu-id="7d0b8-183">Dans l’exemple suivant, `$a` il s’agit d’un tableau d’objets.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-183">In the following example `$a` is an array of objects.</span></span>

```powershell
$a = 1, 2, 3
$a.Clear()
$a | % { $null -eq $_ }
```

```Output
True
True
True
```

<span data-ttu-id="7d0b8-184">Dans cet exemple, `$intA` est explicitement typé pour contenir des entiers.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-184">In this example, `$intA` is explicitly typed to contain integers.</span></span>

```powershell
[int[]] $intA = 1, 2, 3
$intA.Clear()
$intA
```

```Output
0
0
0
```

### <a name="foreach"></a><span data-ttu-id="7d0b8-185">ForEach</span><span class="sxs-lookup"><span data-stu-id="7d0b8-185">ForEach</span></span>

<span data-ttu-id="7d0b8-186">Permet d’itérer sur tous les éléments du tableau et d’effectuer une opération donnée pour chaque élément du tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-186">Allows to iterate over all elements in the array and perform a given operation for each element of the array.</span></span>

<span data-ttu-id="7d0b8-187">La méthode ForEach a plusieurs surcharges qui effectuent des opérations différentes.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-187">The ForEach method has several overloads that perform different operations.</span></span>

```
ForEach(scriptblock expression)
ForEach(scriptblock expression, object[] arguments)
ForEach(type convertToType)
ForEach(string propertyName)
ForEach(string propertyName, object[] newValue)
ForEach(string methodName)
ForEach(string methodName, object[] arguments)
```

#### <a name="foreachscriptblock-expression"></a><span data-ttu-id="7d0b8-188">ForEach (expression scriptblock)</span><span class="sxs-lookup"><span data-stu-id="7d0b8-188">ForEach(scriptblock expression)</span></span>

#### <a name="foreachscriptblock-expression-object-arguments"></a><span data-ttu-id="7d0b8-189">ForEach (expression scriptblock, Object [] arguments)</span><span class="sxs-lookup"><span data-stu-id="7d0b8-189">ForEach(scriptblock expression, object[] arguments)</span></span>

<span data-ttu-id="7d0b8-190">Cette méthode a été ajoutée dans PowerShell v4.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-190">This method was added in PowerShell v4.</span></span>

> [!NOTE]
> <span data-ttu-id="7d0b8-191">La syntaxe requiert l’utilisation d’un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-191">The syntax requires the usage of a script block.</span></span> <span data-ttu-id="7d0b8-192">Les parenthèses sont facultatives si le scriptblock est le seul paramètre.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-192">Parentheses are optional if the scriptblock is the only parameter.</span></span> <span data-ttu-id="7d0b8-193">En outre, il ne doit pas y avoir d’espace entre la méthode et la parenthèse ouvrante ou l’accolade ouvrante.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-193">Also, there must not be a space between the method and the opening parenthesis or brace.</span></span>

<span data-ttu-id="7d0b8-194">L’exemple suivant montre comment utiliser la méthode ForEach.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-194">The following example shows how use the foreach method.</span></span> <span data-ttu-id="7d0b8-195">Dans ce cas, l’objectif est de générer la valeur carrée des éléments dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-195">In this case the intent is to generate the square value of the elements in the array.</span></span>

```powershell
$a = @(0 .. 3)
$a.ForEach({ $_ * $_})
```

```Output
0
1
4
9
```

<span data-ttu-id="7d0b8-196">Tout comme le `-ArgumentList` paramètre de `ForEach-Object` , le `arguments` paramètre permet de passer un tableau d’arguments à un bloc de script configuré pour les accepter.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-196">Just like the `-ArgumentList` parameter of `ForEach-Object`, the `arguments` parameter allows the passing of an array of arguments to a script block configured to accept them.</span></span>

<span data-ttu-id="7d0b8-197">Pour plus d’informations sur le comportement de **argumentlist**, consultez [about_Splatting](about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="7d0b8-197">For more information about the behavior of **ArgumentList**, see [about_Splatting](about_Splatting.md#splatting-with-arrays).</span></span>

#### <a name="foreachtype-converttotype"></a><span data-ttu-id="7d0b8-198">ForEach (type convertToType)</span><span class="sxs-lookup"><span data-stu-id="7d0b8-198">ForEach(type convertToType)</span></span>

<span data-ttu-id="7d0b8-199">La `ForEach` méthode peut être utilisée pour effectuer un cast rapide des éléments vers un autre type. l’exemple suivant montre comment convertir une liste de dates de chaîne en `[DateTime]` type.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-199">The `ForEach` method can be used to swiftly cast the elements to a different type; the following example shows how to convert a list of string dates to `[DateTime]` type.</span></span>

```powershell
@("1/1/2017", "2/1/2017", "3/1/2017").ForEach([datetime])
```

```Output

Sunday, January 1, 2017 12:00:00 AM
Wednesday, February 1, 2017 12:00:00 AM
Wednesday, March 1, 2017 12:00:00 AM
```

#### <a name="foreachstring-propertyname"></a><span data-ttu-id="7d0b8-200">ForEach (String NomPropriété)</span><span class="sxs-lookup"><span data-stu-id="7d0b8-200">ForEach(string propertyName)</span></span>

#### <a name="foreachstring-propertyname-object-newvalue"></a><span data-ttu-id="7d0b8-201">ForEach (String NomPropriété, Object [] newValue)</span><span class="sxs-lookup"><span data-stu-id="7d0b8-201">ForEach(string propertyName, object[] newValue)</span></span>

<span data-ttu-id="7d0b8-202">La `ForEach` méthode peut également être utilisée pour récupérer rapidement ou définir des valeurs de propriété pour chaque élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-202">The `ForEach` method can also be used to quickly retrieve, or set property values for every item in the collection.</span></span>

```powershell
# Set all LastAccessTime properties of files to the current date.
(dir 'C:\Temp').ForEach('LastAccessTime', (Get-Date))
# View the newly set LastAccessTime of all items, and find Unique entries.
(dir 'C:\Temp').ForEach('LastAccessTime') | Get-Unique
```

```Output
Wednesday, June 20, 2018 9:21:57 AM
```

#### <a name="foreachstring-methodname"></a><span data-ttu-id="7d0b8-203">ForEach (String methodName)</span><span class="sxs-lookup"><span data-stu-id="7d0b8-203">ForEach(string methodName)</span></span>

#### <a name="foreachstring-methodname-object-arguments"></a><span data-ttu-id="7d0b8-204">ForEach (String methodName, Object [] arguments)</span><span class="sxs-lookup"><span data-stu-id="7d0b8-204">ForEach(string methodName, object[] arguments)</span></span>

<span data-ttu-id="7d0b8-205">Enfin, `ForEach` les méthodes peuvent être utilisées pour exécuter une méthode sur chaque élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-205">Lastly, `ForEach` methods can be used to execute a method on every item in the collection.</span></span>

```powershell
("one", "two", "three").ForEach("ToUpper")
```

```Output
ONE
TWO
THREE
```

<span data-ttu-id="7d0b8-206">Tout comme le `-ArgumentList` paramètre de `ForEach-Object` , le `arguments` paramètre permet de passer un tableau d’arguments à un bloc de script configuré pour les accepter.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-206">Just like the `-ArgumentList` parameter of `ForEach-Object`, the `arguments` parameter allows the passing of an array of arguments to a script block configured to accept them.</span></span>

> [!NOTE]
> <span data-ttu-id="7d0b8-207">À partir de Windows PowerShell 3,0, la récupération des propriétés et l’exécution de méthodes pour chaque élément d’une collection peut également être accomplie à l’aide de « méthodes des objets scalaires et des collections ». vous pouvez en savoir plus à ce sujet [about_methods](about_methods.md).</span><span class="sxs-lookup"><span data-stu-id="7d0b8-207">Starting in Windows PowerShell 3.0 retrieving properties and executing methods for each item in a collection can also be accomplished using "Methods of scalar objects and collections" You can read more about that here [about_methods](about_methods.md).</span></span>

### <a name="where"></a><span data-ttu-id="7d0b8-208">Where</span><span class="sxs-lookup"><span data-stu-id="7d0b8-208">Where</span></span>

<span data-ttu-id="7d0b8-209">Permet de filtrer ou de sélectionner les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-209">Allows to filter or select the elements of the array.</span></span> <span data-ttu-id="7d0b8-210">Le script doit avoir une valeur autre que : zéro (0), une chaîne vide `$false` ou `$null` pour l’élément à afficher après `Where`</span><span class="sxs-lookup"><span data-stu-id="7d0b8-210">The script must evaluate to anything different than: zero (0), empty string, `$false` or `$null` for the element to show after the `Where`</span></span>

<span data-ttu-id="7d0b8-211">Il existe une définition pour la `Where` méthode.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-211">There is one definition for the `Where` method.</span></span>

```
Where(scriptblock expression[, WhereOperatorSelectionMode mode
                            [, int numberToReturn]])
```

> [!NOTE]
> <span data-ttu-id="7d0b8-212">La syntaxe requiert l’utilisation d’un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-212">The syntax requires the usage of a script block.</span></span> <span data-ttu-id="7d0b8-213">Les parenthèses sont facultatives si le scriptblock est le seul paramètre.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-213">Parentheses are optional if the scriptblock is the only parameter.</span></span> <span data-ttu-id="7d0b8-214">En outre, il ne doit pas y avoir d’espace entre la méthode et la parenthèse ouvrante ou l’accolade ouvrante.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-214">Also, there must not be a space between the method and the opening parenthesis or brace.</span></span>

<span data-ttu-id="7d0b8-215">`Expression`Est un scriptblock qui est requis pour le filtrage, l' `mode` argument facultatif autorise des fonctionnalités de sélection supplémentaires et l' `numberToReturn` argument facultatif permet de limiter le nombre d’éléments retournés à partir du filtre.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-215">The `Expression` is scriptblock that is required for filtering, the `mode` optional argument allows additional selection capabilities, and the `numberToReturn` optional argument allows the ability to limit how many items are returned from the filter.</span></span>

<span data-ttu-id="7d0b8-216">Les valeurs acceptables pour `mode` sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-216">The acceptable values for `mode` are:</span></span>

- <span data-ttu-id="7d0b8-217">Valeur par défaut (0)-retourne tous les éléments</span><span class="sxs-lookup"><span data-stu-id="7d0b8-217">Default (0) - Return all items</span></span>
- <span data-ttu-id="7d0b8-218">First (1) : retourne le premier élément</span><span class="sxs-lookup"><span data-stu-id="7d0b8-218">First (1) - Return the first item</span></span>
- <span data-ttu-id="7d0b8-219">Last (2) : retourne le dernier élément</span><span class="sxs-lookup"><span data-stu-id="7d0b8-219">Last (2) - Return the last item</span></span>
- <span data-ttu-id="7d0b8-220">Ignorer jusqu’à (3)-ignorer les éléments tant que la condition n’a pas la valeur true, le retourne les éléments restants</span><span class="sxs-lookup"><span data-stu-id="7d0b8-220">SkipUntil (3) - Skip items until condition is true, the return the remaining items</span></span>
- <span data-ttu-id="7d0b8-221">Until (4)-renvoyer tous les éléments jusqu’à ce que condition ait la valeur true</span><span class="sxs-lookup"><span data-stu-id="7d0b8-221">Until (4) - Return all items until condition is true</span></span>
- <span data-ttu-id="7d0b8-222">Split (5) : retourne un tableau de deux éléments</span><span class="sxs-lookup"><span data-stu-id="7d0b8-222">Split (5) - Return an array of two elements</span></span>
  - <span data-ttu-id="7d0b8-223">Le premier élément contient des éléments correspondants</span><span class="sxs-lookup"><span data-stu-id="7d0b8-223">The first element contains matching items</span></span>
  - <span data-ttu-id="7d0b8-224">Le deuxième élément contient les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-224">The second element contains the remaining items</span></span>

<span data-ttu-id="7d0b8-225">L’exemple suivant montre comment sélectionner tous les nombres impairs dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-225">The following example shows how to select all odd numbers from the array.</span></span>

```powershell
(0..9).Where{ $_ % 2 }
```

```Output
1
3
5
7
9
```

<span data-ttu-id="7d0b8-226">Cet exemple montre comment sélectionner les chaînes qui ne sont pas vides.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-226">This example show how to select the strings that are not empty.</span></span>

```powershell
('hi', '', 'there').Where({$_.Length})
```

```Output
hi
there
```

#### <a name="default"></a><span data-ttu-id="7d0b8-227">Default</span><span class="sxs-lookup"><span data-stu-id="7d0b8-227">Default</span></span>

<span data-ttu-id="7d0b8-228">Le `Default` mode filtre les éléments à l’aide du `Expression` scriptblock.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-228">The `Default` mode filters items using the `Expression` scriptblock.</span></span>

<span data-ttu-id="7d0b8-229">Si un `numberToReturn` est fourni, il spécifie le nombre maximal d’éléments à retourner.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-229">If a `numberToReturn` is provided, it specifies the maximum number of items to return.</span></span>

```powershell
# Get the zip files in the current users profile, sorted by LastAccessTime.
$Zips = dir $env:userprofile -Recurse '*.zip' | Sort-Object LastAccessTime
# Get the least accessed file over 100MB
$Zips.Where({$_.Length -gt 100MB}, 'Default', 1)
```

> [!NOTE]
> <span data-ttu-id="7d0b8-230">Le `Default` mode et le `First` mode retournent tous deux les premiers `numberToReturn` éléments () et peuvent être utilisés indifféremment.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-230">Both the `Default` mode and `First` mode return the first (`numberToReturn`) items, and can be used interchangeably.</span></span>

#### <a name="last"></a><span data-ttu-id="7d0b8-231">Dernier</span><span class="sxs-lookup"><span data-stu-id="7d0b8-231">Last</span></span>

```powershell
$h = (Get-Date).AddHours(-1)
$logs = dir 'C:\' -Recurse '*.log' | Sort-Object CreationTime
# Find the last 5 log files created in the past hour.
$logs.Where({$_.CreationTime -gt $h}, 'Last', 5)
```

#### <a name="skipuntil"></a><span data-ttu-id="7d0b8-232">Ignorer jusqu’à</span><span class="sxs-lookup"><span data-stu-id="7d0b8-232">SkipUntil</span></span>

<span data-ttu-id="7d0b8-233">Le `SkipUntil` mode ignore tous les objets d’une collection jusqu’à ce qu’un objet passe le filtre d’expression de bloc de script.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-233">The `SkipUntil` mode skips all objects in a collection until an object passes the script block expression filter.</span></span> <span data-ttu-id="7d0b8-234">Elle retourne ensuite **tous les** éléments de collection restants sans les tester.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-234">It then returns **ALL** remaining collection items without testing them.</span></span> <span data-ttu-id="7d0b8-235">_Un seul élément de passage est testé_.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-235">_Only one passing item is tested_.</span></span>

<span data-ttu-id="7d0b8-236">Cela signifie que la collection retournée contient à la fois des éléments de _réussite_ et de _non-passage_ qui n’ont pas été testés.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-236">This means the returned collection contains both _passing_ and _non-passing_ items that have NOT been tested.</span></span>

<span data-ttu-id="7d0b8-237">Le nombre d’éléments retournés peut être limité en passant une valeur à l' `numberToReturn` argument.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-237">The number of items returned can be limited by passing a value to the `numberToReturn` argument.</span></span>

```powershell
$computers = "Server01", "Server02", "Server03", "localhost", "Server04"
# Find the first available online server.
$computers.Where({ Test-Connection $_ }, 'SkipUntil', 1)
```

```Output
localhost
```

#### <a name="until"></a><span data-ttu-id="7d0b8-238">Until</span><span class="sxs-lookup"><span data-stu-id="7d0b8-238">Until</span></span>

<span data-ttu-id="7d0b8-239">Le `Until` mode inverse le `SkipUntil` mode.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-239">The `Until` mode inverts the `SkipUntil` mode.</span></span>  <span data-ttu-id="7d0b8-240">Elle retourne **tous les** éléments d’une collection jusqu’à ce qu’un élément passe l’expression de bloc de script.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-240">It returns **ALL** items in a collection until an item passes the script block expression.</span></span> <span data-ttu-id="7d0b8-241">Une fois qu’un élément a _réussi_ l’expression scriptblock, la `Where` méthode arrête le traitement des éléments.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-241">Once an item _passes_ the scriptblock expression, the `Where` method stops processing items.</span></span>

<span data-ttu-id="7d0b8-242">Cela signifie que vous recevez le premier jeu de _non-passage_ d’éléments à partir de la `Where` méthode.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-242">This means that you receive the first set of _non-passing_ items from the `Where` method.</span></span> <span data-ttu-id="7d0b8-243">_Une fois qu'_ un élément est passé, les autres éléments ne sont pas testés ou retournés.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-243">_After_ one item passes, the rest are NOT tested or returned.</span></span>

<span data-ttu-id="7d0b8-244">Le nombre d’éléments retournés peut être limité en passant une valeur à l' `numberToReturn` argument.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-244">The number of items returned can be limited by passing a value to the `numberToReturn` argument.</span></span>

```powershell
# Retrieve the first set of numbers less than or equal to 10.
(1..50).Where({$_ -gt 10}, 'Until')
# This would perform the same operation.
(1..50).Where({$_ -le 10})
```

```Output
1
2
3
4
5
6
7
8
9
10
```

> [!NOTE]
> <span data-ttu-id="7d0b8-245">`Until`Et `SkipUntil` fonctionnent sous le principe de ne pas tester un lot d’éléments.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-245">Both `Until` and `SkipUntil` operate under the premise of NOT testing a batch of items.</span></span>
>
> <span data-ttu-id="7d0b8-246">`Until` retourne les éléments **avant** la première _passe_.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-246">`Until` returns the items **BEFORE** the first _pass_.</span></span>
>
> <span data-ttu-id="7d0b8-247">`SkipUntil` retourne tous les éléments **après** la première _passe_, y compris le premier élément passant.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-247">`SkipUntil` returns all the items **AFTER** the first _pass_, including the first passing item.</span></span>

#### <a name="split"></a><span data-ttu-id="7d0b8-248">Split</span><span class="sxs-lookup"><span data-stu-id="7d0b8-248">Split</span></span>

<span data-ttu-id="7d0b8-249">Le `Split` mode fractionne, ou regroupe les éléments de la collection en deux collections distinctes.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-249">The `Split` mode splits, or groups collection items into two separate collections.</span></span> <span data-ttu-id="7d0b8-250">Ceux qui passent l’expression scriptblock et ceux qui ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-250">Those that pass the scriptblock expression, and those that do not.</span></span>

<span data-ttu-id="7d0b8-251">Si un `numberToReturn` est spécifié, la première collection contient les éléments qui _passent_ , et non pas la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-251">If a `numberToReturn` is specified, the first collection, contains the _passing_ items, not to exceed the value specified.</span></span>

<span data-ttu-id="7d0b8-252">Les objets restants, y compris ceux qui **passent** le filtre d’expression, sont retournés dans la deuxième collection.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-252">The remaining objects, even those that **PASS** the expression filter, are returned in the second collection.</span></span>

```powershell
$running, $stopped = (Get-Service).Where({$_.Status -eq 'Running'}, 'Split')
$running
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  AudioEndpointBu... Windows Audio Endpoint Builder
Running  Audiosrv           Windows Audio
...
```

```powershell
$stopped
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
...
```

## <a name="get-the-members-of-an-array"></a><span data-ttu-id="7d0b8-253">Obtient les membres d’un tableau</span><span class="sxs-lookup"><span data-stu-id="7d0b8-253">Get the members of an array</span></span>

<span data-ttu-id="7d0b8-254">Pour récupérer les propriétés et les méthodes d’un tableau, telles que la propriété Length et la méthode **SetValue** , utilisez le paramètre **InputObject** de l’applet de commande `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="7d0b8-254">To get the properties and methods of an array, such as the Length property and the **SetValue** method, use the **InputObject** parameter of the `Get-Member` cmdlet.</span></span>

<span data-ttu-id="7d0b8-255">Quand vous dirigez un tableau vers `Get-Member` , PowerShell envoie les éléments un par un et `Get-Member` retourne le type de chaque élément dans le tableau (en ignorant les doublons).</span><span class="sxs-lookup"><span data-stu-id="7d0b8-255">When you pipe an array to `Get-Member`, PowerShell sends the items one at a time and `Get-Member` returns the type of each item in the array (ignoring duplicates).</span></span>

<span data-ttu-id="7d0b8-256">Quand vous utilisez le paramètre **InputObject** , `Get-Member` retourne les membres du tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-256">When you use the **InputObject** parameter, `Get-Member` returns the members of the array.</span></span>

<span data-ttu-id="7d0b8-257">Par exemple, la commande suivante obtient les membres de la `$a` variable tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-257">For example, the following command gets the members of the `$a` array variable.</span></span>

```powershell
Get-Member -InputObject $a
```

<span data-ttu-id="7d0b8-258">Vous pouvez également obtenir les membres d’un tableau en tapant une virgule (,) avant la valeur redirigée vers l' `Get-Member` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-258">You can also get the members of an array by typing a comma (,) before the value that is piped to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="7d0b8-259">La virgule fait du tableau le deuxième élément dans un tableau de tableaux.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-259">The comma makes the array the second item in an array of arrays.</span></span> <span data-ttu-id="7d0b8-260">PowerShell conduit les tableaux un par un et `Get-Member` retourne les membres du tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-260">PowerShell pipes the arrays one at a time and `Get-Member` returns the members of the array.</span></span> <span data-ttu-id="7d0b8-261">Comme les deux exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-261">Like the next two examples.</span></span>

```powershell
,$a | Get-Member

,(1,2,3) | Get-Member
```

## <a name="manipulating-an-array"></a><span data-ttu-id="7d0b8-262">Manipulation d’un tableau</span><span class="sxs-lookup"><span data-stu-id="7d0b8-262">Manipulating an array</span></span>

<span data-ttu-id="7d0b8-263">Vous pouvez modifier les éléments d’un tableau, ajouter un élément à un tableau et combiner les valeurs de deux tableaux dans un troisième tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-263">You can change the elements in an array, add an element to an array, and combine the values from two arrays into a third array.</span></span>

<span data-ttu-id="7d0b8-264">Pour modifier la valeur d’un élément particulier dans un tableau, spécifiez le nom du tableau et l’index de l’élément que vous souhaitez modifier, puis utilisez l’opérateur d’assignation ( `=` ) pour spécifier une nouvelle valeur pour l’élément.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-264">To change the value of a particular element in an array, specify the array name and the index of the element that you want to change, and then use the assignment operator (`=`) to specify a new value for the element.</span></span> <span data-ttu-id="7d0b8-265">Par exemple, pour modifier la valeur du deuxième élément du `$a` tableau (position d’index 1) sur 10, tapez :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-265">For example, to change the value of the second item in the `$a` array (index position 1) to 10, type:</span></span>

```powershell
$a[1] = 10
```

<span data-ttu-id="7d0b8-266">Vous pouvez également utiliser la méthode **SetValue** d’un tableau pour modifier une valeur.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-266">You can also use the **SetValue** method of an array to change a value.</span></span> <span data-ttu-id="7d0b8-267">L’exemple suivant remplace la deuxième valeur (position d’index 1) du `$a` tableau par 500 :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-267">The following example changes the second value (index position 1) of the `$a` array to 500:</span></span>

```powershell
$a.SetValue(500,1)
```

<span data-ttu-id="7d0b8-268">Vous pouvez utiliser l' `+=` opérateur pour ajouter un élément à un tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-268">You can use the `+=` operator to add an element to an array.</span></span> <span data-ttu-id="7d0b8-269">L’exemple suivant montre comment ajouter un élément au `$a` tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-269">The following example shows how to add an element to the `$a` array.</span></span>

```powershell
$a = @(0..4)
$a += 5
```

> [!NOTE]
> <span data-ttu-id="7d0b8-270">Lorsque vous utilisez l' `+=` opérateur, PowerShell crée en fait un nouveau tableau avec les valeurs du tableau d’origine et la valeur ajoutée.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-270">When you use the `+=` operator, PowerShell actually creates a new array with the values of the original array and the added value.</span></span> <span data-ttu-id="7d0b8-271">Cela peut entraîner des problèmes de performances si l’opération est répétée plusieurs fois ou si la taille du tableau est trop importante.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-271">This might cause performance issues if the operation is repeated several times or the size of the array is too big.</span></span>

<span data-ttu-id="7d0b8-272">Il n’est pas facile de supprimer des éléments d’un tableau, mais vous pouvez créer un nouveau tableau qui contient uniquement les éléments sélectionnés d’un tableau existant.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-272">It is not easy to delete elements from an array, but you can create a new array that contains only selected elements of an existing array.</span></span> <span data-ttu-id="7d0b8-273">Par exemple, pour créer le `$t` tableau avec tous les éléments du tableau, à l' `$a` exception de la valeur de la position d’index 2, tapez :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-273">For example, to create the `$t` array with all the elements in the `$a` array except for the value at index position 2, type:</span></span>

```powershell
$t = $a[0,1 + 3..($a.length - 1)]
```

<span data-ttu-id="7d0b8-274">Pour combiner deux tableaux en un seul tableau, utilisez l’opérateur plus ( `+` ).</span><span class="sxs-lookup"><span data-stu-id="7d0b8-274">To combine two arrays into a single array, use the plus operator (`+`).</span></span> <span data-ttu-id="7d0b8-275">L’exemple suivant crée deux tableaux, les combine, puis affiche le tableau combiné résultant.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-275">The following example creates two arrays, combines them, and then displays the resulting combined array.</span></span>

```powershell
$x = 1,3
$y = 5,9
$z = $x + $y
```

<span data-ttu-id="7d0b8-276">Par conséquent, le `$z` tableau contient 1, 3, 5 et 9.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-276">As a result, the `$z` array contains 1, 3, 5, and 9.</span></span>

<span data-ttu-id="7d0b8-277">Pour supprimer un tableau, assignez une valeur `$null` au tableau.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-277">To delete an array, assign a value of `$null` to the array.</span></span> <span data-ttu-id="7d0b8-278">La commande suivante supprime le tableau dans la `$a` variable.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-278">The following command deletes the array in the `$a` variable.</span></span>

`$a = $null`

<span data-ttu-id="7d0b8-279">Vous pouvez également utiliser l' `Remove-Item` applet de commande, mais l’affectation d’une valeur `$null` à est plus rapide, en particulier pour les grands tableaux.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-279">You can also use the `Remove-Item` cmdlet, but assigning a value of `$null` is faster, especially for large arrays.</span></span>

## <a name="arrays-of-zero-or-one"></a><span data-ttu-id="7d0b8-280">Tableaux de zéro ou un</span><span class="sxs-lookup"><span data-stu-id="7d0b8-280">Arrays of zero or one</span></span>

<span data-ttu-id="7d0b8-281">À compter de Windows PowerShell 3,0, une collection de zéro ou un objet a la propriété Count et length.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-281">Beginning in Windows PowerShell 3.0, a collection of zero or one object has the Count and Length property.</span></span> <span data-ttu-id="7d0b8-282">En outre, vous pouvez indexer dans un tableau d’un objet.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-282">Also, you can index into an array of one object.</span></span> <span data-ttu-id="7d0b8-283">Cette fonctionnalité vous aide à éviter les erreurs de script qui se produisent lorsqu’une commande qui attend une collection reçoit moins de deux éléments.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-283">This feature helps you to avoid scripting errors that occur when a command that expects a collection gets fewer than two items.</span></span>

<span data-ttu-id="7d0b8-284">Les exemples suivants illustrent cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-284">The following examples demonstrate this feature.</span></span>

### <a name="zero-objects"></a><span data-ttu-id="7d0b8-285">Zéro objet</span><span class="sxs-lookup"><span data-stu-id="7d0b8-285">Zero objects</span></span>

```powershell
$a = $null
$a.Count
$a.Length
```

```Output
0
0
```

### <a name="one-object"></a><span data-ttu-id="7d0b8-286">Un objet</span><span class="sxs-lookup"><span data-stu-id="7d0b8-286">One object</span></span>

```powershell
$a = 4
$a.Count
$a.Length
$a[0]
$a[-1]
```

```Output
1
1
4
4
```

## <a name="indexing-support-for-systemtuple-objects"></a><span data-ttu-id="7d0b8-287">Prise en charge de l’indexation pour les objets System. Tuple</span><span class="sxs-lookup"><span data-stu-id="7d0b8-287">Indexing support for System.Tuple objects</span></span>

<span data-ttu-id="7d0b8-288">PowerShell 6,1 a ajouté la prise en charge de l’accès indexé des objets **Tuple** , comme les tableaux.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-288">PowerShell 6.1 added the support for indexed access of **Tuple** objects, similar to arrays.</span></span>
<span data-ttu-id="7d0b8-289">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7d0b8-289">For example:</span></span>

```powershell
PS> $tuple = [Tuple]::Create(1, 'test')
PS> $tuple[0]
1
PS> $tuple[1]
test
PS> $tuple[0..1]
1
test
PS> $tuple[-1]
test
```

<span data-ttu-id="7d0b8-290">Contrairement aux tableaux et autres objets de collection, les objets **Tuple** sont traités comme un objet unique lorsqu’ils sont transmis via le pipeline ou par des paramètres qui prennent en charge des tableaux d’objets.</span><span class="sxs-lookup"><span data-stu-id="7d0b8-290">Unlike arrays and other collection objects, **Tuple** objects are treated as a single object when passed through the pipeline or by parameters that support arrays of objects.</span></span>

<span data-ttu-id="7d0b8-291">Pour plus d’informations, consultez [System. Tuple](/dotnet/api/system.tuple).</span><span class="sxs-lookup"><span data-stu-id="7d0b8-291">For more information, see [System.Tuple](/dotnet/api/system.tuple).</span></span>

## <a name="see-also"></a><span data-ttu-id="7d0b8-292">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d0b8-292">See also</span></span>

- [<span data-ttu-id="7d0b8-293">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="7d0b8-293">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)
- [<span data-ttu-id="7d0b8-294">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="7d0b8-294">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="7d0b8-295">about_Operators</span><span class="sxs-lookup"><span data-stu-id="7d0b8-295">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="7d0b8-296">about_For</span><span class="sxs-lookup"><span data-stu-id="7d0b8-296">about_For</span></span>](about_For.md)
- [<span data-ttu-id="7d0b8-297">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="7d0b8-297">about_Foreach</span></span>](about_Foreach.md)
- [<span data-ttu-id="7d0b8-298">about_While</span><span class="sxs-lookup"><span data-stu-id="7d0b8-298">about_While</span></span>](about_While.md)
