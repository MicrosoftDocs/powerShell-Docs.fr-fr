---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: c45b234445a7bc2b54aefb080d2d3da65433d412
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201666"
---
# <span data-ttu-id="c854a-103">Get-Random</span><span class="sxs-lookup"><span data-stu-id="c854a-103">Get-Random</span></span>

## <span data-ttu-id="c854a-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c854a-104">SYNOPSIS</span></span>
<span data-ttu-id="c854a-105">Obtient un nombre aléatoire ou sélectionne de façon aléatoire des objets d'une collection.</span><span class="sxs-lookup"><span data-stu-id="c854a-105">Gets a random number, or selects objects randomly from a collection.</span></span>

## <span data-ttu-id="c854a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c854a-106">SYNTAX</span></span>

### <span data-ttu-id="c854a-107">RandomNumberParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="c854a-107">RandomNumberParameterSet (Default)</span></span>

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="c854a-108">RandomListItemParameterSet</span><span class="sxs-lookup"><span data-stu-id="c854a-108">RandomListItemParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="c854a-109">Description</span><span class="sxs-lookup"><span data-stu-id="c854a-109">DESCRIPTION</span></span>

<span data-ttu-id="c854a-110">L' `Get-Random` applet de commande obtient un nombre sélectionné de façon aléatoire.</span><span class="sxs-lookup"><span data-stu-id="c854a-110">The `Get-Random` cmdlet gets a randomly selected number.</span></span> <span data-ttu-id="c854a-111">Si vous envoyez une collection d’objets à `Get-Random` , elle obtient un ou plusieurs objets sélectionnés de façon aléatoire dans la collection.</span><span class="sxs-lookup"><span data-stu-id="c854a-111">If you submit a collection of objects to `Get-Random`, it gets one or more randomly selected objects from the collection.</span></span>

<span data-ttu-id="c854a-112">Sans paramètres ou en entrée, une `Get-Random` commande retourne un entier non signé 32 bits sélectionné de façon aléatoire entre 0 (zéro) et **Int32. MaxValue** ( `0x7FFFFFFF` , `2,147,483,647` ).</span><span class="sxs-lookup"><span data-stu-id="c854a-112">Without parameters or input, a `Get-Random` command returns a randomly selected 32-bit unsigned integer between 0 (zero) and **Int32.MaxValue** (`0x7FFFFFFF`, `2,147,483,647`).</span></span>

<span data-ttu-id="c854a-113">Vous pouvez utiliser les paramètres de `Get-Random` pour spécifier un nombre de départ, des valeurs minimales et maximales, ainsi que le nombre d’objets retournés à partir d’une collection soumise.</span><span class="sxs-lookup"><span data-stu-id="c854a-113">You can use the parameters of `Get-Random` to specify a seed number, minimum and maximum values, and the number of objects returned from a submitted collection.</span></span>

## <span data-ttu-id="c854a-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c854a-114">EXAMPLES</span></span>

### <span data-ttu-id="c854a-115">Exemple 1 : obtenir un entier aléatoire</span><span class="sxs-lookup"><span data-stu-id="c854a-115">Example 1: Get a random integer</span></span>

<span data-ttu-id="c854a-116">Cette commande obtient un entier aléatoire compris entre 0 (zéro) et **Int32. MaxValue** .</span><span class="sxs-lookup"><span data-stu-id="c854a-116">This command gets a random integer between 0 (zero) and **Int32.MaxValue** .</span></span>

```powershell
Get-Random
```

```Output
3951433
```

### <span data-ttu-id="c854a-117">Exemple 2 : obtenir un entier aléatoire compris entre 0 et 99</span><span class="sxs-lookup"><span data-stu-id="c854a-117">Example 2: Get a random integer between 0 and 99</span></span>

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### <span data-ttu-id="c854a-118">Exemple 3 : obtenir un entier aléatoire compris entre-100 et 99</span><span class="sxs-lookup"><span data-stu-id="c854a-118">Example 3: Get a random integer between -100 and 99</span></span>

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### <span data-ttu-id="c854a-119">Exemple 4 : obtenir un nombre à virgule flottante aléatoire</span><span class="sxs-lookup"><span data-stu-id="c854a-119">Example 4: Get a random floating-point number</span></span>

<span data-ttu-id="c854a-120">Cette commande obtient un nombre à virgule flottante aléatoire supérieur ou égal à 10,7 et inférieur à 20,92.</span><span class="sxs-lookup"><span data-stu-id="c854a-120">This command gets a random floating-point number greater than or equal to 10.7 and less than 20.92.</span></span>

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### <span data-ttu-id="c854a-121">Exemple 5 : obtenir un entier aléatoire à partir d’un tableau</span><span class="sxs-lookup"><span data-stu-id="c854a-121">Example 5: Get a random integer from an array</span></span>

<span data-ttu-id="c854a-122">Cette commande obtient un nombre sélectionné de façon aléatoire dans le tableau spécifié.</span><span class="sxs-lookup"><span data-stu-id="c854a-122">This command gets a randomly selected number from the specified array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### <span data-ttu-id="c854a-123">Exemple 6 : récupération de plusieurs entiers aléatoires à partir d’un tableau</span><span class="sxs-lookup"><span data-stu-id="c854a-123">Example 6: Get several random integers from an array</span></span>

<span data-ttu-id="c854a-124">Cette commande obtient trois nombres sélectionnés de façon aléatoire dans un ordre aléatoire à partir d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="c854a-124">This command gets three randomly selected numbers in random order from an array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### <span data-ttu-id="c854a-125">Exemple 7 : randomiser une collection entière</span><span class="sxs-lookup"><span data-stu-id="c854a-125">Example 7: Randomize an entire collection</span></span>

<span data-ttu-id="c854a-126">Cette commande retourne la collection entière dans un ordre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="c854a-126">This command returns the entire collection in random order.</span></span>

<span data-ttu-id="c854a-127">La valeur du paramètre **Count** est la propriété statique **MaxValue** des entiers.</span><span class="sxs-lookup"><span data-stu-id="c854a-127">The value of the **Count** parameter is the **MaxValue** static property of integers.</span></span>

<span data-ttu-id="c854a-128">Pour retourner une collection entière dans un ordre aléatoire, entrez un nombre qui est supérieur ou égal au nombre d'objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="c854a-128">To return an entire collection in random order, enter any number that is greater than or equal to the number of objects in the collection.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count ([int]::MaxValue)
```

```Output
2
3
5
1
8
13
```

### <span data-ttu-id="c854a-129">Exemple 8 : obtenir une valeur non numérique aléatoire</span><span class="sxs-lookup"><span data-stu-id="c854a-129">Example 8: Get a random non-numeric value</span></span>

<span data-ttu-id="c854a-130">Cette commande retourne une valeur aléatoire depuis une collection non numérique.</span><span class="sxs-lookup"><span data-stu-id="c854a-130">This command returns a random value from a non-numeric collection.</span></span>

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### <span data-ttu-id="c854a-131">Exemple 9 : utiliser le paramètre SetSeed</span><span class="sxs-lookup"><span data-stu-id="c854a-131">Example 9: Use the SetSeed parameter</span></span>

<span data-ttu-id="c854a-132">Cet exemple montre l'utilisation du paramètre **SetSeed** .</span><span class="sxs-lookup"><span data-stu-id="c854a-132">This example shows the effect of using the **SetSeed** parameter.</span></span>

<span data-ttu-id="c854a-133">Comme **setseed** produit un comportement non aléatoire, il est généralement utilisé uniquement pour reproduire les résultats, par exemple lors du débogage ou de l’analyse d’un script.</span><span class="sxs-lookup"><span data-stu-id="c854a-133">Because **SetSeed** produces non-random behavior, it's typically used only to reproduce results, such as when debugging or analyzing a script.</span></span>

```powershell
# Commands with the default seed are pseudorandom
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

```powershell
# Commands with the same seed are not random
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
```

```Output
74
74
74
```

```powershell
# SetSeed results in a repeatable series
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

### <span data-ttu-id="c854a-134">Exemple 10 : récupération de fichiers aléatoires</span><span class="sxs-lookup"><span data-stu-id="c854a-134">Example 10: Get random files</span></span>

<span data-ttu-id="c854a-135">Ces commandes obtiennent un exemple sélectionné de manière aléatoire de fichiers 50 à partir du `C:` lecteur de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c854a-135">These commands get a randomly selected sample of 50 files from the `C:` drive of the local computer.</span></span>

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### <span data-ttu-id="c854a-136">Exemple 11 : roulements de dés équitables</span><span class="sxs-lookup"><span data-stu-id="c854a-136">Example 11: Roll fair dice</span></span>

<span data-ttu-id="c854a-137">Cet exemple annule une matrice de 1200 fois et compte les résultats.</span><span class="sxs-lookup"><span data-stu-id="c854a-137">This example rolls a fair die 1200 times and counts the outcomes.</span></span> <span data-ttu-id="c854a-138">La première commande `For-EachObject` répète l’appel à `Get-Random` à partir des numéros dirigés (1-6).</span><span class="sxs-lookup"><span data-stu-id="c854a-138">The first command, `For-EachObject` repeats the call to `Get-Random` from the piped in numbers (1-6).</span></span> <span data-ttu-id="c854a-139">Les résultats sont regroupés par valeur avec `Group-Object` et mis en forme en tant que table avec `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="c854a-139">The results are grouped by their value with `Group-Object` and formatted as a table with `Select-Object`.</span></span>

```powershell
1..1200 | ForEach-Object {
    1..6 | Get-Random
} | Group-Object | Select-Object Name,Count
```

```Output
Name Count
---- -----
1      206
2      199
3      196
4      226
5      185
6      188
```

### <span data-ttu-id="c854a-140">Exemple 12 : utiliser le paramètre count</span><span class="sxs-lookup"><span data-stu-id="c854a-140">Example 12: Use the Count parameter</span></span>

<span data-ttu-id="c854a-141">Vous pouvez maintenant utiliser le paramètre **Count** sans rediriger les objets vers `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="c854a-141">You can now use the **Count** parameter without piping objects to `Get-Random`.</span></span>
<span data-ttu-id="c854a-142">L’exemple suivant obtient trois nombres aléatoires inférieurs à 10.</span><span class="sxs-lookup"><span data-stu-id="c854a-142">The following example gets three random numbers less than 10.</span></span>

```powershell
Get-Random -Count 3 -Maximum 10
```

```Output
9
0
8
```

### <span data-ttu-id="c854a-143">Exemple 13 : utiliser le paramètre InputObject avec une chaîne vide ou $null</span><span class="sxs-lookup"><span data-stu-id="c854a-143">Example 13: Use the InputObject parameter with an empty string or $null</span></span>

<span data-ttu-id="c854a-144">Dans cet exemple, le paramètre **InputObject** spécifie un tableau qui contient une chaîne vide ( `''` ) et `$null` .</span><span class="sxs-lookup"><span data-stu-id="c854a-144">In this example, the **InputObject** parameter specifies an array that contains an empty string (`''`) and `$null`.</span></span>

```powershell
Get-Random -InputObject @('a','',$null)
```

<span data-ttu-id="c854a-145">`Get-Random` retourne une `a` chaîne vide, ou `$null` .</span><span class="sxs-lookup"><span data-stu-id="c854a-145">`Get-Random` will return either `a`, empty string, or `$null`.</span></span> <span data-ttu-id="c854a-146">La chaîne vide s’affiche sous la forme d’une ligne vide et `$null` retourne à une invite de commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c854a-146">The empty sting displays as a blank line and `$null` returns to a PowerShell prompt.</span></span>

## <span data-ttu-id="c854a-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c854a-147">PARAMETERS</span></span>

### <span data-ttu-id="c854a-148">-Nombre</span><span class="sxs-lookup"><span data-stu-id="c854a-148">-Count</span></span>

<span data-ttu-id="c854a-149">Spécifie le nombre d’objets ou de nombres aléatoires à retourner.</span><span class="sxs-lookup"><span data-stu-id="c854a-149">Specifies the number of random objects or numbers to return.</span></span> <span data-ttu-id="c854a-150">La valeur par défaut est 1.</span><span class="sxs-lookup"><span data-stu-id="c854a-150">The default is 1.</span></span>

<span data-ttu-id="c854a-151">Lorsqu' `InputObject` il est utilisé avec, si la valeur de **Count** dépasse le nombre d’objets de la collection, `Get-Random` retourne tous les objets dans l’ordre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="c854a-151">When used with `InputObject`, if the value of **Count** exceeds the number of objects in the collection, `Get-Random` returns all of the objects in random order.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c854a-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c854a-152">-InputObject</span></span>

<span data-ttu-id="c854a-153">Spécifie une collection d'objets.</span><span class="sxs-lookup"><span data-stu-id="c854a-153">Specifies a collection of objects.</span></span> <span data-ttu-id="c854a-154">`Get-Random` obtient des objets sélectionnés aléatoirement dans l’ordre aléatoire à partir de la collection jusqu’au nombre spécifié par **Count** .</span><span class="sxs-lookup"><span data-stu-id="c854a-154">`Get-Random` gets randomly selected objects in random order from the collection up to the number specified by **Count** .</span></span> <span data-ttu-id="c854a-155">Entrez les objets, une variable contenant les objets, ou bien tapez une commande ou une expression qui obtient les objets.</span><span class="sxs-lookup"><span data-stu-id="c854a-155">Enter the objects, a variable that contains the objects, or a command or expression that gets the objects.</span></span> <span data-ttu-id="c854a-156">Vous pouvez également diriger une collection d’objets vers `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="c854a-156">You can also pipe a collection of objects to `Get-Random`.</span></span>

<span data-ttu-id="c854a-157">À compter de PowerShell 7, le paramètre **InputObject** accepte des tableaux qui peuvent contenir une chaîne vide ou `$null` .</span><span class="sxs-lookup"><span data-stu-id="c854a-157">Beginning in PowerShell 7, the **InputObject** parameter accepts arrays that can contain an empty string or `$null`.</span></span> <span data-ttu-id="c854a-158">Le tableau peut être envoyé dans le pipeline ou en tant que valeur de paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="c854a-158">The array can be sent down the pipeline or as an **InputObject** parameter value.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: RandomListItemParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c854a-159">-Maximum</span><span class="sxs-lookup"><span data-stu-id="c854a-159">-Maximum</span></span>

<span data-ttu-id="c854a-160">Spécifie une valeur maximale pour le nombre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="c854a-160">Specifies a maximum value for the random number.</span></span> <span data-ttu-id="c854a-161">`Get-Random` retourne une valeur inférieure à la valeur maximale (non égal à).</span><span class="sxs-lookup"><span data-stu-id="c854a-161">`Get-Random` returns a value that is less than the maximum (not equal).</span></span> <span data-ttu-id="c854a-162">Entrez un entier, un nombre à virgule flottante double précision ou un objet qui peut être converti en entier ou double, par exemple une chaîne numérique (« 100 »).</span><span class="sxs-lookup"><span data-stu-id="c854a-162">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span>

<span data-ttu-id="c854a-163">La valeur de **Maximum** doit être supérieure à (différente de) la valeur de **Minimum** .</span><span class="sxs-lookup"><span data-stu-id="c854a-163">The value of **Maximum** must be greater than (not equal to) the value of **Minimum** .</span></span> <span data-ttu-id="c854a-164">Si la valeur de **maximum** ou **minimum** est un nombre à virgule flottante, `Get-Random` retourne un nombre à virgule flottante sélectionné de façon aléatoire.</span><span class="sxs-lookup"><span data-stu-id="c854a-164">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

<span data-ttu-id="c854a-165">Sur un ordinateur 64 bits, si la valeur **minimale** est un entier 32 bits, la valeur par défaut de **maximum** est **Int32. MaxValue** .</span><span class="sxs-lookup"><span data-stu-id="c854a-165">On a 64-bit computer, if the value of **Minimum** is a 32-bit integer, the default value of **Maximum** is **Int32.MaxValue** .</span></span>

<span data-ttu-id="c854a-166">Si la valeur de **minimum** est un double (un nombre à virgule flottante), la valeur par défaut de **maximum** est **double. MaxValue** .</span><span class="sxs-lookup"><span data-stu-id="c854a-166">If the value of **Minimum** is a double (a floating-point number), the default value of **Maximum** is **Double.MaxValue** .</span></span> <span data-ttu-id="c854a-167">Dans le cas contraire, la valeur par défaut est **Int32. MaxValue** .</span><span class="sxs-lookup"><span data-stu-id="c854a-167">Otherwise, the default value is **Int32.MaxValue** .</span></span>

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c854a-168">-Minimum</span><span class="sxs-lookup"><span data-stu-id="c854a-168">-Minimum</span></span>

<span data-ttu-id="c854a-169">Spécifie une valeur minimale pour le nombre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="c854a-169">Specifies a minimum value for the random number.</span></span> <span data-ttu-id="c854a-170">Entrez un entier, un nombre à virgule flottante double précision ou un objet qui peut être converti en entier ou double, par exemple une chaîne numérique (« 100 »).</span><span class="sxs-lookup"><span data-stu-id="c854a-170">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span> <span data-ttu-id="c854a-171">La valeur par défaut est 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="c854a-171">The default value is 0 (zero).</span></span>

<span data-ttu-id="c854a-172">La valeur de **Minimum** doit être inférieure à (différente de) la valeur de **Maximum** .</span><span class="sxs-lookup"><span data-stu-id="c854a-172">The value of **Minimum** must be less than (not equal to) the value of **Maximum** .</span></span> <span data-ttu-id="c854a-173">Si la valeur de **maximum** ou **minimum** est un nombre à virgule flottante, `Get-Random` retourne un nombre à virgule flottante sélectionné de façon aléatoire.</span><span class="sxs-lookup"><span data-stu-id="c854a-173">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c854a-174">-SetSeed</span><span class="sxs-lookup"><span data-stu-id="c854a-174">-SetSeed</span></span>

<span data-ttu-id="c854a-175">Spécifie une valeur de départ pour le générateur de nombres aléatoires.</span><span class="sxs-lookup"><span data-stu-id="c854a-175">Specifies a seed value for the random number generator.</span></span> <span data-ttu-id="c854a-176">Cette valeur de départ est utilisée pour la commande actuelle et pour toutes les `Get-Random` commandes suivantes dans la session active jusqu’à ce que vous réutilisiez **setseed** ou fermiez la session.</span><span class="sxs-lookup"><span data-stu-id="c854a-176">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="c854a-177">Vous ne pouvez pas réinitialiser la valeur de départ à sa valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c854a-177">You can't reset the seed to its default value.</span></span>

<span data-ttu-id="c854a-178">Le paramètre **setseed** n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c854a-178">The **SetSeed** parameter is not required.</span></span> <span data-ttu-id="c854a-179">Par défaut, `Get-Random` utilise la méthode [RandomNumberGenerator ()](/dotnet/api/system.security.cryptography.randomnumbergenerator) pour générer une valeur de départ.</span><span class="sxs-lookup"><span data-stu-id="c854a-179">By default, `Get-Random` uses the [RandomNumberGenerator()](/dotnet/api/system.security.cryptography.randomnumbergenerator) method to generate a seed value.</span></span> <span data-ttu-id="c854a-180">Comme **setseed** entraîne un comportement non aléatoire, il est généralement utilisé uniquement lors de la tentative de reproduction du comportement, par exemple lors du débogage ou de l’analyse d’un script qui comprend des `Get-Random` commandes.</span><span class="sxs-lookup"><span data-stu-id="c854a-180">Because **SetSeed** results in non-random behavior, it's typically used only when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c854a-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c854a-181">CommonParameters</span></span>

<span data-ttu-id="c854a-182">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c854a-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c854a-183">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c854a-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c854a-184">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c854a-184">INPUTS</span></span>

### <span data-ttu-id="c854a-185">System.Object</span><span class="sxs-lookup"><span data-stu-id="c854a-185">System.Object</span></span>

<span data-ttu-id="c854a-186">Vous pouvez diriger un ou plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="c854a-186">You can pipe one or more objects.</span></span> <span data-ttu-id="c854a-187">`Get-Random` sélectionne les valeurs de façon aléatoire à partir des objets dirigés.</span><span class="sxs-lookup"><span data-stu-id="c854a-187">`Get-Random` selects values randomly from the piped objects.</span></span>

## <span data-ttu-id="c854a-188">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c854a-188">OUTPUTS</span></span>

### <span data-ttu-id="c854a-189">System. Int32, System. Int64, System. double</span><span class="sxs-lookup"><span data-stu-id="c854a-189">System.Int32, System.Int64, System.Double</span></span>

<span data-ttu-id="c854a-190">`Get-Random` retourne un entier ou un nombre à virgule flottante, ou un objet sélectionné de façon aléatoire à partir d’une collection soumise.</span><span class="sxs-lookup"><span data-stu-id="c854a-190">`Get-Random` returns an integer or floating-point number, or an object selected randomly from a submitted collection.</span></span>

## <span data-ttu-id="c854a-191">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c854a-191">NOTES</span></span>

<span data-ttu-id="c854a-192">`Get-Random` définit une valeur de départ par défaut pour chaque session en fonction de l’horloge système au démarrage de la session.</span><span class="sxs-lookup"><span data-stu-id="c854a-192">`Get-Random` sets a default seed for each session based on the system time clock when the session starts.</span></span>

<span data-ttu-id="c854a-193">`Get-Random` ne retourne pas toujours le même type de données que la valeur d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c854a-193">`Get-Random` does not alway return the same data type as the input value.</span></span> <span data-ttu-id="c854a-194">Le tableau suivant indique le type de sortie pour chacun des types d’entrée numériques.</span><span class="sxs-lookup"><span data-stu-id="c854a-194">The following table shows the output type for each of the numeric input types.</span></span>

| <span data-ttu-id="c854a-195">Type d’entrée</span><span class="sxs-lookup"><span data-stu-id="c854a-195">Input Type</span></span> | <span data-ttu-id="c854a-196">Type de sortie</span><span class="sxs-lookup"><span data-stu-id="c854a-196">Output Type</span></span> |
| :--------: | :---------: |
|   <span data-ttu-id="c854a-197">SByte</span><span class="sxs-lookup"><span data-stu-id="c854a-197">SByte</span></span>    |   <span data-ttu-id="c854a-198">Double</span><span class="sxs-lookup"><span data-stu-id="c854a-198">Double</span></span>    |
|    <span data-ttu-id="c854a-199">Byte</span><span class="sxs-lookup"><span data-stu-id="c854a-199">Byte</span></span>    |   <span data-ttu-id="c854a-200">Double</span><span class="sxs-lookup"><span data-stu-id="c854a-200">Double</span></span>    |
|   <span data-ttu-id="c854a-201">Int16</span><span class="sxs-lookup"><span data-stu-id="c854a-201">Int16</span></span>    |   <span data-ttu-id="c854a-202">Double</span><span class="sxs-lookup"><span data-stu-id="c854a-202">Double</span></span>    |
|   <span data-ttu-id="c854a-203">UInt16</span><span class="sxs-lookup"><span data-stu-id="c854a-203">UInt16</span></span>   |   <span data-ttu-id="c854a-204">Double</span><span class="sxs-lookup"><span data-stu-id="c854a-204">Double</span></span>    |
|   <span data-ttu-id="c854a-205">Int32</span><span class="sxs-lookup"><span data-stu-id="c854a-205">Int32</span></span>    |    <span data-ttu-id="c854a-206">Int32</span><span class="sxs-lookup"><span data-stu-id="c854a-206">Int32</span></span>    |
|   <span data-ttu-id="c854a-207">UInt32</span><span class="sxs-lookup"><span data-stu-id="c854a-207">UInt32</span></span>   |   <span data-ttu-id="c854a-208">Double</span><span class="sxs-lookup"><span data-stu-id="c854a-208">Double</span></span>    |
|   <span data-ttu-id="c854a-209">Int64</span><span class="sxs-lookup"><span data-stu-id="c854a-209">Int64</span></span>    |    <span data-ttu-id="c854a-210">Int64</span><span class="sxs-lookup"><span data-stu-id="c854a-210">Int64</span></span>    |
|   <span data-ttu-id="c854a-211">UInt64</span><span class="sxs-lookup"><span data-stu-id="c854a-211">UInt64</span></span>   |   <span data-ttu-id="c854a-212">Double</span><span class="sxs-lookup"><span data-stu-id="c854a-212">Double</span></span>    |
|   <span data-ttu-id="c854a-213">Double</span><span class="sxs-lookup"><span data-stu-id="c854a-213">Double</span></span>   |   <span data-ttu-id="c854a-214">Double</span><span class="sxs-lookup"><span data-stu-id="c854a-214">Double</span></span>    |
|   <span data-ttu-id="c854a-215">Single</span><span class="sxs-lookup"><span data-stu-id="c854a-215">Single</span></span>   |   <span data-ttu-id="c854a-216">Double</span><span class="sxs-lookup"><span data-stu-id="c854a-216">Double</span></span>    |

<span data-ttu-id="c854a-217">À compter de Windows PowerShell 3,0, `Get-Random` prend en charge les entiers 64 bits.</span><span class="sxs-lookup"><span data-stu-id="c854a-217">Beginning in Windows PowerShell 3.0, `Get-Random` supports 64-bit integers.</span></span> <span data-ttu-id="c854a-218">Dans Windows PowerShell 2,0, toutes les valeurs sont converties en **System. Int32** .</span><span class="sxs-lookup"><span data-stu-id="c854a-218">In Windows PowerShell 2.0, all values are cast to **System.Int32** .</span></span>

<span data-ttu-id="c854a-219">À compter de PowerShell 7, le paramètre **InputObject** dans le jeu de paramètres **RandomListItemParameterSet** accepte des tableaux qui contiennent une chaîne vide ou `$null` .</span><span class="sxs-lookup"><span data-stu-id="c854a-219">Beginning in PowerShell 7, the **InputObject** parameter in the **RandomListItemParameterSet** parameter set accepts arrays that contain an empty string or `$null`.</span></span> <span data-ttu-id="c854a-220">Dans les versions antérieures de PowerShell, seul le paramètre **maximum** dans le jeu de paramètres **RandomNumberParameterSet** acceptait une chaîne vide ou `$null` .</span><span class="sxs-lookup"><span data-stu-id="c854a-220">In earlier PowerShell versions, only the **Maximum** parameter in the **RandomNumberParameterSet** parameter set accepted an empty string or `$null`.</span></span>

## <span data-ttu-id="c854a-221">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c854a-221">RELATED LINKS</span></span>
