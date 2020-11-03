---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 644663c8871233bae84288f83492b518405d14ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202805"
---
# <span data-ttu-id="8e507-103">Get-Random</span><span class="sxs-lookup"><span data-stu-id="8e507-103">Get-Random</span></span>

## <span data-ttu-id="8e507-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8e507-104">SYNOPSIS</span></span>
<span data-ttu-id="8e507-105">Obtient un nombre aléatoire ou sélectionne de façon aléatoire des objets d'une collection.</span><span class="sxs-lookup"><span data-stu-id="8e507-105">Gets a random number, or selects objects randomly from a collection.</span></span>

## <span data-ttu-id="8e507-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8e507-106">SYNTAX</span></span>

### <span data-ttu-id="8e507-107">RandomNumberParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8e507-107">RandomNumberParameterSet (Default)</span></span>

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="8e507-108">RandomListItemParameterSet</span><span class="sxs-lookup"><span data-stu-id="8e507-108">RandomListItemParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="8e507-109">ShuffleParameterSet</span><span class="sxs-lookup"><span data-stu-id="8e507-109">ShuffleParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Shuffle] [<CommonParameters>]
```

## <span data-ttu-id="8e507-110">Description</span><span class="sxs-lookup"><span data-stu-id="8e507-110">DESCRIPTION</span></span>

<span data-ttu-id="8e507-111">L' `Get-Random` applet de commande obtient un nombre sélectionné de façon aléatoire.</span><span class="sxs-lookup"><span data-stu-id="8e507-111">The `Get-Random` cmdlet gets a randomly selected number.</span></span> <span data-ttu-id="8e507-112">Si vous envoyez une collection d’objets à `Get-Random` , elle obtient un ou plusieurs objets sélectionnés de façon aléatoire dans la collection.</span><span class="sxs-lookup"><span data-stu-id="8e507-112">If you submit a collection of objects to `Get-Random`, it gets one or more randomly selected objects from the collection.</span></span>

<span data-ttu-id="8e507-113">Sans paramètres ou en entrée, une `Get-Random` commande retourne un entier non signé 32 bits sélectionné de façon aléatoire entre 0 (zéro) et **Int32. MaxValue** ( `0x7FFFFFFF` , `2,147,483,647` ).</span><span class="sxs-lookup"><span data-stu-id="8e507-113">Without parameters or input, a `Get-Random` command returns a randomly selected 32-bit unsigned integer between 0 (zero) and **Int32.MaxValue** (`0x7FFFFFFF`, `2,147,483,647`).</span></span>

<span data-ttu-id="8e507-114">Vous pouvez utiliser les paramètres de `Get-Random` pour spécifier un nombre de départ, des valeurs minimales et maximales, le nombre d’objets retournés à partir d’une collection soumise et la collection entière dans un ordre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="8e507-114">You can use the parameters of `Get-Random` to specify a seed number, minimum and maximum values, the number of objects returned from a submitted collection, and the entire collection in a random order.</span></span>

## <span data-ttu-id="8e507-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8e507-115">EXAMPLES</span></span>

### <span data-ttu-id="8e507-116">Exemple 1 : obtenir un entier aléatoire</span><span class="sxs-lookup"><span data-stu-id="8e507-116">Example 1: Get a random integer</span></span>

<span data-ttu-id="8e507-117">Cette commande obtient un entier aléatoire compris entre 0 (zéro) et **Int32. MaxValue** .</span><span class="sxs-lookup"><span data-stu-id="8e507-117">This command gets a random integer between 0 (zero) and **Int32.MaxValue** .</span></span>

```powershell
Get-Random
```

```Output
3951433
```

### <span data-ttu-id="8e507-118">Exemple 2 : obtenir un entier aléatoire compris entre 0 et 99</span><span class="sxs-lookup"><span data-stu-id="8e507-118">Example 2: Get a random integer between 0 and 99</span></span>

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### <span data-ttu-id="8e507-119">Exemple 3 : obtenir un entier aléatoire compris entre-100 et 99</span><span class="sxs-lookup"><span data-stu-id="8e507-119">Example 3: Get a random integer between -100 and 99</span></span>

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### <span data-ttu-id="8e507-120">Exemple 4 : obtenir un nombre à virgule flottante aléatoire</span><span class="sxs-lookup"><span data-stu-id="8e507-120">Example 4: Get a random floating-point number</span></span>

<span data-ttu-id="8e507-121">Cette commande obtient un nombre à virgule flottante aléatoire supérieur ou égal à 10,7 et inférieur à 20,92.</span><span class="sxs-lookup"><span data-stu-id="8e507-121">This command gets a random floating-point number greater than or equal to 10.7 and less than 20.92.</span></span>

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### <span data-ttu-id="8e507-122">Exemple 5 : obtenir un entier aléatoire à partir d’un tableau</span><span class="sxs-lookup"><span data-stu-id="8e507-122">Example 5: Get a random integer from an array</span></span>

<span data-ttu-id="8e507-123">Cette commande obtient un nombre sélectionné de façon aléatoire dans le tableau spécifié.</span><span class="sxs-lookup"><span data-stu-id="8e507-123">This command gets a randomly selected number from the specified array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### <span data-ttu-id="8e507-124">Exemple 6 : récupération de plusieurs entiers aléatoires à partir d’un tableau</span><span class="sxs-lookup"><span data-stu-id="8e507-124">Example 6: Get several random integers from an array</span></span>

<span data-ttu-id="8e507-125">Cette commande obtient trois nombres sélectionnés de façon aléatoire dans un ordre aléatoire à partir d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="8e507-125">This command gets three randomly selected numbers in random order from an array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### <span data-ttu-id="8e507-126">Exemple 7 : randomiser une collection entière</span><span class="sxs-lookup"><span data-stu-id="8e507-126">Example 7: Randomize an entire collection</span></span>

<span data-ttu-id="8e507-127">À compter de PowerShell 7,1, vous pouvez utiliser le paramètre de **lecture** aléatoire pour retourner la collection entière dans un ordre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="8e507-127">Starting in PowerShell 7.1, you can use the **Shuffle** parameter to return the entire collection in a random order.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Shuffle
```

```Output
2
3
5
1
8
13
```

### <span data-ttu-id="8e507-128">Exemple 8 : obtenir une valeur non numérique aléatoire</span><span class="sxs-lookup"><span data-stu-id="8e507-128">Example 8: Get a random non-numeric value</span></span>

<span data-ttu-id="8e507-129">Cette commande retourne une valeur aléatoire depuis une collection non numérique.</span><span class="sxs-lookup"><span data-stu-id="8e507-129">This command returns a random value from a non-numeric collection.</span></span>

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### <span data-ttu-id="8e507-130">Exemple 9 : utiliser le paramètre SetSeed</span><span class="sxs-lookup"><span data-stu-id="8e507-130">Example 9: Use the SetSeed parameter</span></span>

<span data-ttu-id="8e507-131">Cet exemple montre l'utilisation du paramètre **SetSeed** .</span><span class="sxs-lookup"><span data-stu-id="8e507-131">This example shows the effect of using the **SetSeed** parameter.</span></span>

<span data-ttu-id="8e507-132">Comme **setseed** produit un comportement non aléatoire, il est généralement utilisé uniquement pour reproduire les résultats, par exemple lors du débogage ou de l’analyse d’un script.</span><span class="sxs-lookup"><span data-stu-id="8e507-132">Because **SetSeed** produces non-random behavior, it's typically used only to reproduce results, such as when debugging or analyzing a script.</span></span>

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

### <span data-ttu-id="8e507-133">Exemple 10 : récupération de fichiers aléatoires</span><span class="sxs-lookup"><span data-stu-id="8e507-133">Example 10: Get random files</span></span>

<span data-ttu-id="8e507-134">Ces commandes obtiennent un exemple sélectionné de manière aléatoire de fichiers 50 à partir du `C:` lecteur de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8e507-134">These commands get a randomly selected sample of 50 files from the `C:` drive of the local computer.</span></span>

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### <span data-ttu-id="8e507-135">Exemple 11 : roulements de dés équitables</span><span class="sxs-lookup"><span data-stu-id="8e507-135">Example 11: Roll fair dice</span></span>

<span data-ttu-id="8e507-136">Cet exemple annule une matrice de 1200 fois et compte les résultats.</span><span class="sxs-lookup"><span data-stu-id="8e507-136">This example rolls a fair die 1200 times and counts the outcomes.</span></span> <span data-ttu-id="8e507-137">La première commande `For-EachObject` répète l’appel à `Get-Random` à partir des numéros dirigés (1-6).</span><span class="sxs-lookup"><span data-stu-id="8e507-137">The first command, `For-EachObject` repeats the call to `Get-Random` from the piped in numbers (1-6).</span></span> <span data-ttu-id="8e507-138">Les résultats sont regroupés par valeur avec `Group-Object` et mis en forme en tant que table avec `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="8e507-138">The results are grouped by their value with `Group-Object` and formatted as a table with `Select-Object`.</span></span>

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

### <span data-ttu-id="8e507-139">Exemple 12 : utiliser le paramètre count</span><span class="sxs-lookup"><span data-stu-id="8e507-139">Example 12: Use the Count parameter</span></span>

<span data-ttu-id="8e507-140">Vous pouvez maintenant utiliser le paramètre **Count** sans rediriger les objets vers `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="8e507-140">You can now use the **Count** parameter without piping objects to `Get-Random`.</span></span>
<span data-ttu-id="8e507-141">L’exemple suivant obtient trois nombres aléatoires inférieurs à 10.</span><span class="sxs-lookup"><span data-stu-id="8e507-141">The following example gets three random numbers less than 10.</span></span>

```powershell
Get-Random -Count 3 -Maximum 10
```

```Output
9
0
8
```

### <span data-ttu-id="8e507-142">Exemple 13 : utiliser le paramètre InputObject avec une chaîne vide ou $null</span><span class="sxs-lookup"><span data-stu-id="8e507-142">Example 13: Use the InputObject parameter with an empty string or $null</span></span>

<span data-ttu-id="8e507-143">Dans cet exemple, le paramètre **InputObject** spécifie un tableau qui contient une chaîne vide ( `''` ) et `$null` .</span><span class="sxs-lookup"><span data-stu-id="8e507-143">In this example, the **InputObject** parameter specifies an array that contains an empty string (`''`) and `$null`.</span></span>

```powershell
Get-Random -InputObject @('a','',$null)
```

<span data-ttu-id="8e507-144">`Get-Random` retourne une `a` chaîne vide, ou `$null` .</span><span class="sxs-lookup"><span data-stu-id="8e507-144">`Get-Random` will return either `a`, empty string, or `$null`.</span></span> <span data-ttu-id="8e507-145">La chaîne vide s’affiche sous la forme d’une ligne vide et `$null` retourne à une invite de commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e507-145">The empty sting displays as a blank line and `$null` returns to a PowerShell prompt.</span></span>

## <span data-ttu-id="8e507-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8e507-146">PARAMETERS</span></span>

### <span data-ttu-id="8e507-147">-Nombre</span><span class="sxs-lookup"><span data-stu-id="8e507-147">-Count</span></span>

<span data-ttu-id="8e507-148">Spécifie le nombre d’objets ou de nombres aléatoires à retourner.</span><span class="sxs-lookup"><span data-stu-id="8e507-148">Specifies the number of random objects or numbers to return.</span></span> <span data-ttu-id="8e507-149">La valeur par défaut est 1.</span><span class="sxs-lookup"><span data-stu-id="8e507-149">The default is 1.</span></span>

<span data-ttu-id="8e507-150">Lorsqu' `InputObject` il est utilisé avec, si la valeur de **Count** dépasse le nombre d’objets de la collection, `Get-Random` retourne tous les objets dans l’ordre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="8e507-150">When used with `InputObject`, if the value of **Count** exceeds the number of objects in the collection, `Get-Random` returns all of the objects in random order.</span></span>

```yaml
Type: System.Int32
Parameter Sets: RandomNumberParameterSet, RandomListItemParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8e507-151">-InputObject</span><span class="sxs-lookup"><span data-stu-id="8e507-151">-InputObject</span></span>

<span data-ttu-id="8e507-152">Spécifie une collection d'objets.</span><span class="sxs-lookup"><span data-stu-id="8e507-152">Specifies a collection of objects.</span></span> <span data-ttu-id="8e507-153">`Get-Random` obtient des objets sélectionnés aléatoirement dans l’ordre aléatoire à partir de la collection jusqu’au nombre spécifié par **Count** .</span><span class="sxs-lookup"><span data-stu-id="8e507-153">`Get-Random` gets randomly selected objects in random order from the collection up to the number specified by **Count** .</span></span> <span data-ttu-id="8e507-154">Entrez les objets, une variable contenant les objets, ou bien tapez une commande ou une expression qui obtient les objets.</span><span class="sxs-lookup"><span data-stu-id="8e507-154">Enter the objects, a variable that contains the objects, or a command or expression that gets the objects.</span></span> <span data-ttu-id="8e507-155">Vous pouvez également diriger une collection d’objets vers `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="8e507-155">You can also pipe a collection of objects to `Get-Random`.</span></span>

<span data-ttu-id="8e507-156">À compter de PowerShell 7, le paramètre **InputObject** accepte des tableaux qui peuvent contenir une chaîne vide ou `$null` .</span><span class="sxs-lookup"><span data-stu-id="8e507-156">Beginning in PowerShell 7, the **InputObject** parameter accepts arrays that can contain an empty string or `$null`.</span></span> <span data-ttu-id="8e507-157">Le tableau peut être envoyé dans le pipeline ou en tant que valeur de paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="8e507-157">The array can be sent down the pipeline or as an **InputObject** parameter value.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: RandomListItemParameterSet, ShuffleParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8e507-158">-Maximum</span><span class="sxs-lookup"><span data-stu-id="8e507-158">-Maximum</span></span>

<span data-ttu-id="8e507-159">Spécifie une valeur maximale pour le nombre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="8e507-159">Specifies a maximum value for the random number.</span></span> <span data-ttu-id="8e507-160">`Get-Random` retourne une valeur inférieure à la valeur maximale (non égal à).</span><span class="sxs-lookup"><span data-stu-id="8e507-160">`Get-Random` returns a value that is less than the maximum (not equal).</span></span> <span data-ttu-id="8e507-161">Entrez un entier, un nombre à virgule flottante double précision ou un objet qui peut être converti en entier ou double, par exemple une chaîne numérique (« 100 »).</span><span class="sxs-lookup"><span data-stu-id="8e507-161">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span>

<span data-ttu-id="8e507-162">La valeur de **Maximum** doit être supérieure à (différente de) la valeur de **Minimum** .</span><span class="sxs-lookup"><span data-stu-id="8e507-162">The value of **Maximum** must be greater than (not equal to) the value of **Minimum** .</span></span> <span data-ttu-id="8e507-163">Si la valeur de **maximum** ou **minimum** est un nombre à virgule flottante, `Get-Random` retourne un nombre à virgule flottante sélectionné de façon aléatoire.</span><span class="sxs-lookup"><span data-stu-id="8e507-163">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

<span data-ttu-id="8e507-164">Sur un ordinateur 64 bits, si la valeur **minimale** est un entier 32 bits, la valeur par défaut de **maximum** est **Int32. MaxValue** .</span><span class="sxs-lookup"><span data-stu-id="8e507-164">On a 64-bit computer, if the value of **Minimum** is a 32-bit integer, the default value of **Maximum** is **Int32.MaxValue** .</span></span>

<span data-ttu-id="8e507-165">Si la valeur de **minimum** est un double (un nombre à virgule flottante), la valeur par défaut de **maximum** est **double. MaxValue** .</span><span class="sxs-lookup"><span data-stu-id="8e507-165">If the value of **Minimum** is a double (a floating-point number), the default value of **Maximum** is **Double.MaxValue** .</span></span> <span data-ttu-id="8e507-166">Dans le cas contraire, la valeur par défaut est **Int32. MaxValue** .</span><span class="sxs-lookup"><span data-stu-id="8e507-166">Otherwise, the default value is **Int32.MaxValue** .</span></span>

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

### <span data-ttu-id="8e507-167">-Minimum</span><span class="sxs-lookup"><span data-stu-id="8e507-167">-Minimum</span></span>

<span data-ttu-id="8e507-168">Spécifie une valeur minimale pour le nombre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="8e507-168">Specifies a minimum value for the random number.</span></span> <span data-ttu-id="8e507-169">Entrez un entier, un nombre à virgule flottante double précision ou un objet qui peut être converti en entier ou double, par exemple une chaîne numérique (« 100 »).</span><span class="sxs-lookup"><span data-stu-id="8e507-169">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span> <span data-ttu-id="8e507-170">La valeur par défaut est 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="8e507-170">The default value is 0 (zero).</span></span>

<span data-ttu-id="8e507-171">La valeur de **Minimum** doit être inférieure à (différente de) la valeur de **Maximum** .</span><span class="sxs-lookup"><span data-stu-id="8e507-171">The value of **Minimum** must be less than (not equal to) the value of **Maximum** .</span></span> <span data-ttu-id="8e507-172">Si la valeur de **maximum** ou **minimum** est un nombre à virgule flottante, `Get-Random` retourne un nombre à virgule flottante sélectionné de façon aléatoire.</span><span class="sxs-lookup"><span data-stu-id="8e507-172">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

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

### <span data-ttu-id="8e507-173">-SetSeed</span><span class="sxs-lookup"><span data-stu-id="8e507-173">-SetSeed</span></span>

<span data-ttu-id="8e507-174">Spécifie une valeur de départ pour le générateur de nombres aléatoires.</span><span class="sxs-lookup"><span data-stu-id="8e507-174">Specifies a seed value for the random number generator.</span></span> <span data-ttu-id="8e507-175">Cette valeur de départ est utilisée pour la commande actuelle et pour toutes les `Get-Random` commandes suivantes dans la session active jusqu’à ce que vous réutilisiez **setseed** ou fermiez la session.</span><span class="sxs-lookup"><span data-stu-id="8e507-175">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="8e507-176">Vous ne pouvez pas réinitialiser la valeur de départ à sa valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8e507-176">You can't reset the seed to its default value.</span></span>

<span data-ttu-id="8e507-177">Le paramètre **setseed** n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8e507-177">The **SetSeed** parameter is not required.</span></span> <span data-ttu-id="8e507-178">Par défaut, `Get-Random` utilise la méthode [RandomNumberGenerator ()](/dotnet/api/system.security.cryptography.randomnumbergenerator) pour générer une valeur de départ.</span><span class="sxs-lookup"><span data-stu-id="8e507-178">By default, `Get-Random` uses the [RandomNumberGenerator()](/dotnet/api/system.security.cryptography.randomnumbergenerator) method to generate a seed value.</span></span> <span data-ttu-id="8e507-179">Comme **setseed** entraîne un comportement non aléatoire, il est généralement utilisé uniquement lors de la tentative de reproduction du comportement, par exemple lors du débogage ou de l’analyse d’un script qui comprend des `Get-Random` commandes.</span><span class="sxs-lookup"><span data-stu-id="8e507-179">Because **SetSeed** results in non-random behavior, it's typically used only when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>

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

### <span data-ttu-id="8e507-180">-Lecture aléatoire</span><span class="sxs-lookup"><span data-stu-id="8e507-180">-Shuffle</span></span>

<span data-ttu-id="8e507-181">Retourne la collection entière dans un ordre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="8e507-181">Returns the entire collection in a randomized order.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShuffleParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8e507-182">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8e507-182">CommonParameters</span></span>

<span data-ttu-id="8e507-183">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8e507-183">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8e507-184">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8e507-184">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8e507-185">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8e507-185">INPUTS</span></span>

### <span data-ttu-id="8e507-186">System.Object</span><span class="sxs-lookup"><span data-stu-id="8e507-186">System.Object</span></span>

<span data-ttu-id="8e507-187">Vous pouvez diriger un ou plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="8e507-187">You can pipe one or more objects.</span></span> <span data-ttu-id="8e507-188">`Get-Random` sélectionne les valeurs de façon aléatoire à partir des objets dirigés.</span><span class="sxs-lookup"><span data-stu-id="8e507-188">`Get-Random` selects values randomly from the piped objects.</span></span>

## <span data-ttu-id="8e507-189">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8e507-189">OUTPUTS</span></span>

### <span data-ttu-id="8e507-190">System. Int32, System. Int64, System. double</span><span class="sxs-lookup"><span data-stu-id="8e507-190">System.Int32, System.Int64, System.Double</span></span>

<span data-ttu-id="8e507-191">`Get-Random` retourne un entier ou un nombre à virgule flottante, ou un objet sélectionné de façon aléatoire à partir d’une collection soumise.</span><span class="sxs-lookup"><span data-stu-id="8e507-191">`Get-Random` returns an integer or floating-point number, or an object selected randomly from a submitted collection.</span></span>

## <span data-ttu-id="8e507-192">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8e507-192">NOTES</span></span>

<span data-ttu-id="8e507-193">`Get-Random` définit une valeur de départ par défaut pour chaque session en fonction de l’horloge système au démarrage de la session.</span><span class="sxs-lookup"><span data-stu-id="8e507-193">`Get-Random` sets a default seed for each session based on the system time clock when the session starts.</span></span>

<span data-ttu-id="8e507-194">`Get-Random` ne retourne pas toujours le même type de données que la valeur d’entrée.</span><span class="sxs-lookup"><span data-stu-id="8e507-194">`Get-Random` does not alway return the same data type as the input value.</span></span> <span data-ttu-id="8e507-195">Le tableau suivant indique le type de sortie pour chacun des types d’entrée numériques.</span><span class="sxs-lookup"><span data-stu-id="8e507-195">The following table shows the output type for each of the numeric input types.</span></span>

| <span data-ttu-id="8e507-196">Type d’entrée</span><span class="sxs-lookup"><span data-stu-id="8e507-196">Input Type</span></span> | <span data-ttu-id="8e507-197">Type de sortie</span><span class="sxs-lookup"><span data-stu-id="8e507-197">Output Type</span></span> |
| :--------: | :---------: |
|   <span data-ttu-id="8e507-198">SByte</span><span class="sxs-lookup"><span data-stu-id="8e507-198">SByte</span></span>    |   <span data-ttu-id="8e507-199">Double</span><span class="sxs-lookup"><span data-stu-id="8e507-199">Double</span></span>    |
|    <span data-ttu-id="8e507-200">Byte</span><span class="sxs-lookup"><span data-stu-id="8e507-200">Byte</span></span>    |   <span data-ttu-id="8e507-201">Double</span><span class="sxs-lookup"><span data-stu-id="8e507-201">Double</span></span>    |
|   <span data-ttu-id="8e507-202">Int16</span><span class="sxs-lookup"><span data-stu-id="8e507-202">Int16</span></span>    |   <span data-ttu-id="8e507-203">Double</span><span class="sxs-lookup"><span data-stu-id="8e507-203">Double</span></span>    |
|   <span data-ttu-id="8e507-204">UInt16</span><span class="sxs-lookup"><span data-stu-id="8e507-204">UInt16</span></span>   |   <span data-ttu-id="8e507-205">Double</span><span class="sxs-lookup"><span data-stu-id="8e507-205">Double</span></span>    |
|   <span data-ttu-id="8e507-206">Int32</span><span class="sxs-lookup"><span data-stu-id="8e507-206">Int32</span></span>    |    <span data-ttu-id="8e507-207">Int32</span><span class="sxs-lookup"><span data-stu-id="8e507-207">Int32</span></span>    |
|   <span data-ttu-id="8e507-208">UInt32</span><span class="sxs-lookup"><span data-stu-id="8e507-208">UInt32</span></span>   |   <span data-ttu-id="8e507-209">Double</span><span class="sxs-lookup"><span data-stu-id="8e507-209">Double</span></span>    |
|   <span data-ttu-id="8e507-210">Int64</span><span class="sxs-lookup"><span data-stu-id="8e507-210">Int64</span></span>    |    <span data-ttu-id="8e507-211">Int64</span><span class="sxs-lookup"><span data-stu-id="8e507-211">Int64</span></span>    |
|   <span data-ttu-id="8e507-212">UInt64</span><span class="sxs-lookup"><span data-stu-id="8e507-212">UInt64</span></span>   |   <span data-ttu-id="8e507-213">Double</span><span class="sxs-lookup"><span data-stu-id="8e507-213">Double</span></span>    |
|   <span data-ttu-id="8e507-214">Double</span><span class="sxs-lookup"><span data-stu-id="8e507-214">Double</span></span>   |   <span data-ttu-id="8e507-215">Double</span><span class="sxs-lookup"><span data-stu-id="8e507-215">Double</span></span>    |
|   <span data-ttu-id="8e507-216">Single</span><span class="sxs-lookup"><span data-stu-id="8e507-216">Single</span></span>   |   <span data-ttu-id="8e507-217">Double</span><span class="sxs-lookup"><span data-stu-id="8e507-217">Double</span></span>    |

<span data-ttu-id="8e507-218">À compter de Windows PowerShell 3,0, `Get-Random` prend en charge les entiers 64 bits.</span><span class="sxs-lookup"><span data-stu-id="8e507-218">Beginning in Windows PowerShell 3.0, `Get-Random` supports 64-bit integers.</span></span> <span data-ttu-id="8e507-219">Dans Windows PowerShell 2,0, toutes les valeurs sont converties en **System. Int32** .</span><span class="sxs-lookup"><span data-stu-id="8e507-219">In Windows PowerShell 2.0, all values are cast to **System.Int32** .</span></span>

<span data-ttu-id="8e507-220">À compter de PowerShell 7, le paramètre **InputObject** dans le jeu de paramètres **RandomListItemParameterSet** accepte des tableaux qui contiennent une chaîne vide ou `$null` .</span><span class="sxs-lookup"><span data-stu-id="8e507-220">Beginning in PowerShell 7, the **InputObject** parameter in the **RandomListItemParameterSet** parameter set accepts arrays that contain an empty string or `$null`.</span></span> <span data-ttu-id="8e507-221">Dans les versions antérieures de PowerShell, seul le paramètre **maximum** dans le jeu de paramètres **RandomNumberParameterSet** acceptait une chaîne vide ou `$null` .</span><span class="sxs-lookup"><span data-stu-id="8e507-221">In earlier PowerShell versions, only the **Maximum** parameter in the **RandomNumberParameterSet** parameter set accepted an empty string or `$null`.</span></span>

## <span data-ttu-id="8e507-222">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8e507-222">RELATED LINKS</span></span>

