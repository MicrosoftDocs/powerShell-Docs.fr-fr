---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 4922124569550012223d441099dc94b228fd93d4
ms.sourcegitcommit: fa1a84c81e15f1ffac962110b0b4c850c1b173a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99598785"
---
# <span data-ttu-id="bfd43-102">Get-Random</span><span class="sxs-lookup"><span data-stu-id="bfd43-102">Get-Random</span></span>

## <span data-ttu-id="bfd43-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="bfd43-103">SYNOPSIS</span></span>
<span data-ttu-id="bfd43-104">Obtient un nombre aléatoire ou sélectionne de façon aléatoire des objets d'une collection.</span><span class="sxs-lookup"><span data-stu-id="bfd43-104">Gets a random number, or selects objects randomly from a collection.</span></span>

## <span data-ttu-id="bfd43-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="bfd43-105">SYNTAX</span></span>

### <span data-ttu-id="bfd43-106">RandomNumberParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="bfd43-106">RandomNumberParameterSet (Default)</span></span>

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="bfd43-107">RandomListItemParameterSet</span><span class="sxs-lookup"><span data-stu-id="bfd43-107">RandomListItemParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="bfd43-108">ShuffleParameterSet</span><span class="sxs-lookup"><span data-stu-id="bfd43-108">ShuffleParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Shuffle] [<CommonParameters>]
```

## <span data-ttu-id="bfd43-109">Description</span><span class="sxs-lookup"><span data-stu-id="bfd43-109">DESCRIPTION</span></span>

<span data-ttu-id="bfd43-110">L' `Get-Random` applet de commande obtient un nombre sélectionné de façon aléatoire.</span><span class="sxs-lookup"><span data-stu-id="bfd43-110">The `Get-Random` cmdlet gets a randomly selected number.</span></span> <span data-ttu-id="bfd43-111">Si vous envoyez une collection d’objets à `Get-Random` , elle obtient un ou plusieurs objets sélectionnés de façon aléatoire dans la collection.</span><span class="sxs-lookup"><span data-stu-id="bfd43-111">If you submit a collection of objects to `Get-Random`, it gets one or more randomly selected objects from the collection.</span></span>

<span data-ttu-id="bfd43-112">Sans paramètres ou en entrée, une `Get-Random` commande retourne un entier non signé 32 bits sélectionné de façon aléatoire entre 0 (zéro) et **Int32. MaxValue** ( `0x7FFFFFFF` , `2,147,483,647` ).</span><span class="sxs-lookup"><span data-stu-id="bfd43-112">Without parameters or input, a `Get-Random` command returns a randomly selected 32-bit unsigned integer between 0 (zero) and **Int32.MaxValue** (`0x7FFFFFFF`, `2,147,483,647`).</span></span>

<span data-ttu-id="bfd43-113">Par défaut, `Get-Random` génère un caractère aléatoire sécurisé par chiffrement à l’aide de la classe [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) .</span><span class="sxs-lookup"><span data-stu-id="bfd43-113">By default, `Get-Random` generates cryptographically secure randomness using the [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) class.</span></span>

<span data-ttu-id="bfd43-114">Vous pouvez utiliser les paramètres de `Get-Random` pour spécifier les valeurs minimale et maximale, le nombre d’objets retournés à partir d’une collection ou un numéro de départ.</span><span class="sxs-lookup"><span data-stu-id="bfd43-114">You can use the parameters of `Get-Random` to specify the minimum and maximum values, the number of objects returned from a collection, or a seed number.</span></span>

> [!CAUTION]
> <span data-ttu-id="bfd43-115">La définition délibérément de la valeur de départ entraîne un comportement reproductible et non aléatoire.</span><span class="sxs-lookup"><span data-stu-id="bfd43-115">Setting the seed deliberately results in non-random, repeatable behavior.</span></span> <span data-ttu-id="bfd43-116">Elle doit être utilisée uniquement lorsque vous tentez de reproduire le comportement, par exemple lors du débogage ou de l’analyse d’un script qui comprend des `Get-Random` commandes.</span><span class="sxs-lookup"><span data-stu-id="bfd43-116">It should only be used when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>
>
> <span data-ttu-id="bfd43-117">Cette valeur de départ est utilisée pour la commande actuelle et pour toutes les `Get-Random` commandes suivantes dans la session active jusqu’à ce que vous réutilisiez **setseed** ou fermiez la session.</span><span class="sxs-lookup"><span data-stu-id="bfd43-117">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="bfd43-118">Vous ne pouvez pas réinitialiser la valeur de départ à sa valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="bfd43-118">You can't reset the seed to its default value.</span></span>

## <span data-ttu-id="bfd43-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="bfd43-119">EXAMPLES</span></span>

### <span data-ttu-id="bfd43-120">Exemple 1 : obtenir un entier aléatoire</span><span class="sxs-lookup"><span data-stu-id="bfd43-120">Example 1: Get a random integer</span></span>

<span data-ttu-id="bfd43-121">Cette commande obtient un entier aléatoire compris entre 0 (zéro) et **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="bfd43-121">This command gets a random integer between 0 (zero) and **Int32.MaxValue**.</span></span>

```powershell
Get-Random
```

```Output
3951433
```

### <span data-ttu-id="bfd43-122">Exemple 2 : obtenir un entier aléatoire compris entre 0 et 99</span><span class="sxs-lookup"><span data-stu-id="bfd43-122">Example 2: Get a random integer between 0 and 99</span></span>

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### <span data-ttu-id="bfd43-123">Exemple 3 : obtenir un entier aléatoire compris entre-100 et 99</span><span class="sxs-lookup"><span data-stu-id="bfd43-123">Example 3: Get a random integer between -100 and 99</span></span>

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### <span data-ttu-id="bfd43-124">Exemple 4 : obtenir un nombre à virgule flottante aléatoire</span><span class="sxs-lookup"><span data-stu-id="bfd43-124">Example 4: Get a random floating-point number</span></span>

<span data-ttu-id="bfd43-125">Cette commande obtient un nombre à virgule flottante aléatoire supérieur ou égal à 10,7 et inférieur à 20,92.</span><span class="sxs-lookup"><span data-stu-id="bfd43-125">This command gets a random floating-point number greater than or equal to 10.7 and less than 20.92.</span></span>

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### <span data-ttu-id="bfd43-126">Exemple 5 : obtenir un entier aléatoire à partir d’un tableau</span><span class="sxs-lookup"><span data-stu-id="bfd43-126">Example 5: Get a random integer from an array</span></span>

<span data-ttu-id="bfd43-127">Cette commande obtient un nombre sélectionné de façon aléatoire dans le tableau spécifié.</span><span class="sxs-lookup"><span data-stu-id="bfd43-127">This command gets a randomly selected number from the specified array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### <span data-ttu-id="bfd43-128">Exemple 6 : récupération de plusieurs entiers aléatoires à partir d’un tableau</span><span class="sxs-lookup"><span data-stu-id="bfd43-128">Example 6: Get several random integers from an array</span></span>

<span data-ttu-id="bfd43-129">Cette commande obtient trois nombres sélectionnés de façon aléatoire dans un ordre aléatoire à partir d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="bfd43-129">This command gets three randomly selected numbers in random order from an array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### <span data-ttu-id="bfd43-130">Exemple 7 : randomiser une collection entière</span><span class="sxs-lookup"><span data-stu-id="bfd43-130">Example 7: Randomize an entire collection</span></span>

<span data-ttu-id="bfd43-131">À compter de PowerShell 7,1, vous pouvez utiliser le paramètre de **lecture** aléatoire pour retourner la collection entière dans un ordre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="bfd43-131">Starting in PowerShell 7.1, you can use the **Shuffle** parameter to return the entire collection in a random order.</span></span>

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

### <span data-ttu-id="bfd43-132">Exemple 8 : obtenir une valeur non numérique aléatoire</span><span class="sxs-lookup"><span data-stu-id="bfd43-132">Example 8: Get a random non-numeric value</span></span>

<span data-ttu-id="bfd43-133">Cette commande retourne une valeur aléatoire depuis une collection non numérique.</span><span class="sxs-lookup"><span data-stu-id="bfd43-133">This command returns a random value from a non-numeric collection.</span></span>

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### <span data-ttu-id="bfd43-134">Exemple 9 : utiliser le paramètre SetSeed</span><span class="sxs-lookup"><span data-stu-id="bfd43-134">Example 9: Use the SetSeed parameter</span></span>

<span data-ttu-id="bfd43-135">Cet exemple montre l'utilisation du paramètre **SetSeed**.</span><span class="sxs-lookup"><span data-stu-id="bfd43-135">This example shows the effect of using the **SetSeed** parameter.</span></span>

<span data-ttu-id="bfd43-136">Comme **setseed** produit un comportement non aléatoire, il est généralement utilisé uniquement pour reproduire les résultats, par exemple lors du débogage ou de l’analyse d’un script.</span><span class="sxs-lookup"><span data-stu-id="bfd43-136">Because **SetSeed** produces non-random behavior, it's typically used only to reproduce results, such as when debugging or analyzing a script.</span></span>

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

### <span data-ttu-id="bfd43-137">Exemple 10 : récupération de fichiers aléatoires</span><span class="sxs-lookup"><span data-stu-id="bfd43-137">Example 10: Get random files</span></span>

<span data-ttu-id="bfd43-138">Ces commandes obtiennent un exemple sélectionné de manière aléatoire de fichiers 50 à partir du `C:` lecteur de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="bfd43-138">These commands get a randomly selected sample of 50 files from the `C:` drive of the local computer.</span></span>

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### <span data-ttu-id="bfd43-139">Exemple 11 : roulements de dés équitables</span><span class="sxs-lookup"><span data-stu-id="bfd43-139">Example 11: Roll fair dice</span></span>

<span data-ttu-id="bfd43-140">Cet exemple annule une matrice de 1200 fois et compte les résultats.</span><span class="sxs-lookup"><span data-stu-id="bfd43-140">This example rolls a fair die 1200 times and counts the outcomes.</span></span> <span data-ttu-id="bfd43-141">La première commande `ForEach-Object` répète l’appel à `Get-Random` à partir des numéros dirigés (1-6).</span><span class="sxs-lookup"><span data-stu-id="bfd43-141">The first command, `ForEach-Object` repeats the call to `Get-Random` from the piped in numbers (1-6).</span></span> <span data-ttu-id="bfd43-142">Les résultats sont regroupés par valeur avec `Group-Object` et mis en forme en tant que table avec `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="bfd43-142">The results are grouped by their value with `Group-Object` and formatted as a table with `Select-Object`.</span></span>

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

### <span data-ttu-id="bfd43-143">Exemple 12 : utiliser le paramètre count</span><span class="sxs-lookup"><span data-stu-id="bfd43-143">Example 12: Use the Count parameter</span></span>

<span data-ttu-id="bfd43-144">Vous pouvez maintenant utiliser le paramètre **Count** sans rediriger les objets vers `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="bfd43-144">You can now use the **Count** parameter without piping objects to `Get-Random`.</span></span>
<span data-ttu-id="bfd43-145">L’exemple suivant obtient trois nombres aléatoires inférieurs à 10.</span><span class="sxs-lookup"><span data-stu-id="bfd43-145">The following example gets three random numbers less than 10.</span></span>

```powershell
Get-Random -Count 3 -Maximum 10
```

```Output
9
0
8
```

### <span data-ttu-id="bfd43-146">Exemple 13 : utiliser le paramètre InputObject avec une chaîne vide ou $null</span><span class="sxs-lookup"><span data-stu-id="bfd43-146">Example 13: Use the InputObject parameter with an empty string or $null</span></span>

<span data-ttu-id="bfd43-147">Dans cet exemple, le paramètre **InputObject** spécifie un tableau qui contient une chaîne vide ( `''` ) et `$null` .</span><span class="sxs-lookup"><span data-stu-id="bfd43-147">In this example, the **InputObject** parameter specifies an array that contains an empty string (`''`) and `$null`.</span></span>

```powershell
Get-Random -InputObject @('a','',$null)
```

<span data-ttu-id="bfd43-148">`Get-Random` retourne une `a` chaîne vide, ou `$null` .</span><span class="sxs-lookup"><span data-stu-id="bfd43-148">`Get-Random` will return either `a`, empty string, or `$null`.</span></span> <span data-ttu-id="bfd43-149">La chaîne vide s’affiche sous la forme d’une ligne vide et `$null` retourne à une invite de commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bfd43-149">The empty sting displays as a blank line and `$null` returns to a PowerShell prompt.</span></span>

## <span data-ttu-id="bfd43-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bfd43-150">PARAMETERS</span></span>

### <span data-ttu-id="bfd43-151">-Nombre</span><span class="sxs-lookup"><span data-stu-id="bfd43-151">-Count</span></span>

<span data-ttu-id="bfd43-152">Spécifie le nombre d’objets ou de nombres aléatoires à retourner.</span><span class="sxs-lookup"><span data-stu-id="bfd43-152">Specifies the number of random objects or numbers to return.</span></span> <span data-ttu-id="bfd43-153">La valeur par défaut est 1.</span><span class="sxs-lookup"><span data-stu-id="bfd43-153">The default is 1.</span></span>

<span data-ttu-id="bfd43-154">Lorsqu' `InputObject` il est utilisé avec, si la valeur de **Count** dépasse le nombre d’objets de la collection, `Get-Random` retourne tous les objets dans l’ordre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="bfd43-154">When used with `InputObject`, if the value of **Count** exceeds the number of objects in the collection, `Get-Random` returns all of the objects in random order.</span></span>

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

### <span data-ttu-id="bfd43-155">-InputObject</span><span class="sxs-lookup"><span data-stu-id="bfd43-155">-InputObject</span></span>

<span data-ttu-id="bfd43-156">Spécifie une collection d'objets.</span><span class="sxs-lookup"><span data-stu-id="bfd43-156">Specifies a collection of objects.</span></span> <span data-ttu-id="bfd43-157">`Get-Random` obtient des objets sélectionnés aléatoirement dans l’ordre aléatoire à partir de la collection jusqu’au nombre spécifié par **Count**.</span><span class="sxs-lookup"><span data-stu-id="bfd43-157">`Get-Random` gets randomly selected objects in random order from the collection up to the number specified by **Count**.</span></span> <span data-ttu-id="bfd43-158">Entrez les objets, une variable contenant les objets, ou bien tapez une commande ou une expression qui obtient les objets.</span><span class="sxs-lookup"><span data-stu-id="bfd43-158">Enter the objects, a variable that contains the objects, or a command or expression that gets the objects.</span></span> <span data-ttu-id="bfd43-159">Vous pouvez également diriger une collection d’objets vers `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="bfd43-159">You can also pipe a collection of objects to `Get-Random`.</span></span>

<span data-ttu-id="bfd43-160">À compter de PowerShell 7, le paramètre **InputObject** accepte des tableaux qui peuvent contenir une chaîne vide ou `$null` .</span><span class="sxs-lookup"><span data-stu-id="bfd43-160">Beginning in PowerShell 7, the **InputObject** parameter accepts arrays that can contain an empty string or `$null`.</span></span> <span data-ttu-id="bfd43-161">Le tableau peut être envoyé dans le pipeline ou en tant que valeur de paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="bfd43-161">The array can be sent down the pipeline or as an **InputObject** parameter value.</span></span>

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

### <span data-ttu-id="bfd43-162">-Maximum</span><span class="sxs-lookup"><span data-stu-id="bfd43-162">-Maximum</span></span>

<span data-ttu-id="bfd43-163">Spécifie une valeur maximale pour le nombre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="bfd43-163">Specifies a maximum value for the random number.</span></span> <span data-ttu-id="bfd43-164">`Get-Random` retourne une valeur inférieure à la valeur maximale (non égal à).</span><span class="sxs-lookup"><span data-stu-id="bfd43-164">`Get-Random` returns a value that is less than the maximum (not equal).</span></span> <span data-ttu-id="bfd43-165">Entrez un entier, un nombre à virgule flottante double précision ou un objet qui peut être converti en entier ou double, par exemple une chaîne numérique (« 100 »).</span><span class="sxs-lookup"><span data-stu-id="bfd43-165">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span>

<span data-ttu-id="bfd43-166">La valeur de **Maximum** doit être supérieure à (différente de) la valeur de **Minimum**.</span><span class="sxs-lookup"><span data-stu-id="bfd43-166">The value of **Maximum** must be greater than (not equal to) the value of **Minimum**.</span></span> <span data-ttu-id="bfd43-167">Si la valeur de **maximum** ou **minimum** est un nombre à virgule flottante, `Get-Random` retourne un nombre à virgule flottante sélectionné de façon aléatoire.</span><span class="sxs-lookup"><span data-stu-id="bfd43-167">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

<span data-ttu-id="bfd43-168">Sur un ordinateur 64 bits, si la valeur **minimale** est un entier 32 bits, la valeur par défaut de **maximum** est **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="bfd43-168">On a 64-bit computer, if the value of **Minimum** is a 32-bit integer, the default value of **Maximum** is **Int32.MaxValue**.</span></span>

<span data-ttu-id="bfd43-169">Si la valeur de **minimum** est un double (un nombre à virgule flottante), la valeur par défaut de **maximum** est **double. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="bfd43-169">If the value of **Minimum** is a double (a floating-point number), the default value of **Maximum** is **Double.MaxValue**.</span></span> <span data-ttu-id="bfd43-170">Dans le cas contraire, la valeur par défaut est **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="bfd43-170">Otherwise, the default value is **Int32.MaxValue**.</span></span>

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

### <span data-ttu-id="bfd43-171">-Minimum</span><span class="sxs-lookup"><span data-stu-id="bfd43-171">-Minimum</span></span>

<span data-ttu-id="bfd43-172">Spécifie une valeur minimale pour le nombre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="bfd43-172">Specifies a minimum value for the random number.</span></span> <span data-ttu-id="bfd43-173">Entrez un entier, un nombre à virgule flottante double précision ou un objet qui peut être converti en entier ou double, par exemple une chaîne numérique (« 100 »).</span><span class="sxs-lookup"><span data-stu-id="bfd43-173">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span> <span data-ttu-id="bfd43-174">La valeur par défaut est 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="bfd43-174">The default value is 0 (zero).</span></span>

<span data-ttu-id="bfd43-175">La valeur de **Minimum** doit être inférieure à (différente de) la valeur de **Maximum**.</span><span class="sxs-lookup"><span data-stu-id="bfd43-175">The value of **Minimum** must be less than (not equal to) the value of **Maximum**.</span></span> <span data-ttu-id="bfd43-176">Si la valeur de **maximum** ou **minimum** est un nombre à virgule flottante, `Get-Random` retourne un nombre à virgule flottante sélectionné de façon aléatoire.</span><span class="sxs-lookup"><span data-stu-id="bfd43-176">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

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

### <span data-ttu-id="bfd43-177">-SetSeed</span><span class="sxs-lookup"><span data-stu-id="bfd43-177">-SetSeed</span></span>

<span data-ttu-id="bfd43-178">Spécifie une valeur de départ pour le générateur de nombres aléatoires.</span><span class="sxs-lookup"><span data-stu-id="bfd43-178">Specifies a seed value for the random number generator.</span></span> <span data-ttu-id="bfd43-179">Lorsque vous utilisez **setseed**, l’applet de commande utilise la méthode [System. Random](/dotnet/api/system.random) pour générer des nombres pseudo-aléatoires, ce qui n’est pas sécurisé par chiffrement.</span><span class="sxs-lookup"><span data-stu-id="bfd43-179">When you use **SetSeed**, the cmdlet uses the [System.Random](/dotnet/api/system.random) method to generate pseudorandom numbers, which is not cryptographically secure.</span></span>

> [!CAUTION]
> <span data-ttu-id="bfd43-180">La définition de la valeur initiale entraîne un comportement non aléatoire.</span><span class="sxs-lookup"><span data-stu-id="bfd43-180">Setting the seed results in non-random behavior.</span></span> <span data-ttu-id="bfd43-181">Elle doit être utilisée uniquement lorsque vous tentez de reproduire le comportement, par exemple lors du débogage ou de l’analyse d’un script qui comprend des `Get-Random` commandes.</span><span class="sxs-lookup"><span data-stu-id="bfd43-181">It should only be used when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>
>
> <span data-ttu-id="bfd43-182">Cette valeur de départ est utilisée pour la commande actuelle et pour toutes les `Get-Random` commandes suivantes dans la session active jusqu’à ce que vous réutilisiez **setseed** ou fermiez la session.</span><span class="sxs-lookup"><span data-stu-id="bfd43-182">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="bfd43-183">Vous ne pouvez pas réinitialiser la valeur de départ à sa valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="bfd43-183">You can't reset the seed to its default value.</span></span>

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

### <span data-ttu-id="bfd43-184">-Lecture aléatoire</span><span class="sxs-lookup"><span data-stu-id="bfd43-184">-Shuffle</span></span>

<span data-ttu-id="bfd43-185">Retourne la collection entière dans un ordre aléatoire.</span><span class="sxs-lookup"><span data-stu-id="bfd43-185">Returns the entire collection in a randomized order.</span></span>

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

### <span data-ttu-id="bfd43-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bfd43-186">CommonParameters</span></span>

<span data-ttu-id="bfd43-187">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bfd43-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bfd43-188">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bfd43-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bfd43-189">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="bfd43-189">INPUTS</span></span>

### <span data-ttu-id="bfd43-190">System.Object</span><span class="sxs-lookup"><span data-stu-id="bfd43-190">System.Object</span></span>

<span data-ttu-id="bfd43-191">Vous pouvez diriger un ou plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="bfd43-191">You can pipe one or more objects.</span></span> <span data-ttu-id="bfd43-192">`Get-Random` sélectionne les valeurs de façon aléatoire à partir des objets dirigés.</span><span class="sxs-lookup"><span data-stu-id="bfd43-192">`Get-Random` selects values randomly from the piped objects.</span></span>

## <span data-ttu-id="bfd43-193">SORTIES</span><span class="sxs-lookup"><span data-stu-id="bfd43-193">OUTPUTS</span></span>

### <span data-ttu-id="bfd43-194">System. Int32, System. Int64, System. double</span><span class="sxs-lookup"><span data-stu-id="bfd43-194">System.Int32, System.Int64, System.Double</span></span>

<span data-ttu-id="bfd43-195">`Get-Random` retourne un entier ou un nombre à virgule flottante, ou un objet sélectionné de façon aléatoire à partir d’une collection soumise.</span><span class="sxs-lookup"><span data-stu-id="bfd43-195">`Get-Random` returns an integer or floating-point number, or an object selected randomly from a submitted collection.</span></span>

## <span data-ttu-id="bfd43-196">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="bfd43-196">NOTES</span></span>

<span data-ttu-id="bfd43-197">Par défaut, `Get-Random` génère un caractère aléatoire sécurisé par chiffrement à l’aide de la classe [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) .</span><span class="sxs-lookup"><span data-stu-id="bfd43-197">By default, `Get-Random` generates cryptographically secure randomness using the [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) class.</span></span>

<span data-ttu-id="bfd43-198">`Get-Random` ne retourne pas toujours le même type de données que la valeur d’entrée.</span><span class="sxs-lookup"><span data-stu-id="bfd43-198">`Get-Random` does not alway return the same data type as the input value.</span></span> <span data-ttu-id="bfd43-199">Le tableau suivant indique le type de sortie pour chacun des types d’entrée numériques.</span><span class="sxs-lookup"><span data-stu-id="bfd43-199">The following table shows the output type for each of the numeric input types.</span></span>

| <span data-ttu-id="bfd43-200">Type d’entrée</span><span class="sxs-lookup"><span data-stu-id="bfd43-200">Input Type</span></span> | <span data-ttu-id="bfd43-201">Type de sortie</span><span class="sxs-lookup"><span data-stu-id="bfd43-201">Output Type</span></span> |
| :--------: | :---------: |
|   <span data-ttu-id="bfd43-202">SByte</span><span class="sxs-lookup"><span data-stu-id="bfd43-202">SByte</span></span>    |   <span data-ttu-id="bfd43-203">Double</span><span class="sxs-lookup"><span data-stu-id="bfd43-203">Double</span></span>    |
|    <span data-ttu-id="bfd43-204">Byte</span><span class="sxs-lookup"><span data-stu-id="bfd43-204">Byte</span></span>    |   <span data-ttu-id="bfd43-205">Double</span><span class="sxs-lookup"><span data-stu-id="bfd43-205">Double</span></span>    |
|   <span data-ttu-id="bfd43-206">Int16</span><span class="sxs-lookup"><span data-stu-id="bfd43-206">Int16</span></span>    |   <span data-ttu-id="bfd43-207">Double</span><span class="sxs-lookup"><span data-stu-id="bfd43-207">Double</span></span>    |
|   <span data-ttu-id="bfd43-208">UInt16</span><span class="sxs-lookup"><span data-stu-id="bfd43-208">UInt16</span></span>   |   <span data-ttu-id="bfd43-209">Double</span><span class="sxs-lookup"><span data-stu-id="bfd43-209">Double</span></span>    |
|   <span data-ttu-id="bfd43-210">Int32</span><span class="sxs-lookup"><span data-stu-id="bfd43-210">Int32</span></span>    |    <span data-ttu-id="bfd43-211">Int32</span><span class="sxs-lookup"><span data-stu-id="bfd43-211">Int32</span></span>    |
|   <span data-ttu-id="bfd43-212">UInt32</span><span class="sxs-lookup"><span data-stu-id="bfd43-212">UInt32</span></span>   |   <span data-ttu-id="bfd43-213">Double</span><span class="sxs-lookup"><span data-stu-id="bfd43-213">Double</span></span>    |
|   <span data-ttu-id="bfd43-214">Int64</span><span class="sxs-lookup"><span data-stu-id="bfd43-214">Int64</span></span>    |    <span data-ttu-id="bfd43-215">Int64</span><span class="sxs-lookup"><span data-stu-id="bfd43-215">Int64</span></span>    |
|   <span data-ttu-id="bfd43-216">UInt64</span><span class="sxs-lookup"><span data-stu-id="bfd43-216">UInt64</span></span>   |   <span data-ttu-id="bfd43-217">Double</span><span class="sxs-lookup"><span data-stu-id="bfd43-217">Double</span></span>    |
|   <span data-ttu-id="bfd43-218">Double</span><span class="sxs-lookup"><span data-stu-id="bfd43-218">Double</span></span>   |   <span data-ttu-id="bfd43-219">Double</span><span class="sxs-lookup"><span data-stu-id="bfd43-219">Double</span></span>    |
|   <span data-ttu-id="bfd43-220">Unique</span><span class="sxs-lookup"><span data-stu-id="bfd43-220">Single</span></span>   |   <span data-ttu-id="bfd43-221">Double</span><span class="sxs-lookup"><span data-stu-id="bfd43-221">Double</span></span>    |

<span data-ttu-id="bfd43-222">À compter de Windows PowerShell 3,0, `Get-Random` prend en charge les entiers 64 bits.</span><span class="sxs-lookup"><span data-stu-id="bfd43-222">Beginning in Windows PowerShell 3.0, `Get-Random` supports 64-bit integers.</span></span> <span data-ttu-id="bfd43-223">Dans Windows PowerShell 2,0, toutes les valeurs sont converties en **System. Int32**.</span><span class="sxs-lookup"><span data-stu-id="bfd43-223">In Windows PowerShell 2.0, all values are cast to **System.Int32**.</span></span>

<span data-ttu-id="bfd43-224">À compter de PowerShell 7, le paramètre **InputObject** dans le jeu de paramètres **RandomListItemParameterSet** accepte des tableaux qui contiennent une chaîne vide ou `$null` .</span><span class="sxs-lookup"><span data-stu-id="bfd43-224">Beginning in PowerShell 7, the **InputObject** parameter in the **RandomListItemParameterSet** parameter set accepts arrays that contain an empty string or `$null`.</span></span> <span data-ttu-id="bfd43-225">Dans les versions antérieures de PowerShell, seul le paramètre **maximum** dans le jeu de paramètres **RandomNumberParameterSet** acceptait une chaîne vide ou `$null` .</span><span class="sxs-lookup"><span data-stu-id="bfd43-225">In earlier PowerShell versions, only the **Maximum** parameter in the **RandomNumberParameterSet** parameter set accepted an empty string or `$null`.</span></span>

## <span data-ttu-id="bfd43-226">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="bfd43-226">RELATED LINKS</span></span>

[<span data-ttu-id="bfd43-227">System. Security. Cryptography. RandomNumberGenerator ()</span><span class="sxs-lookup"><span data-stu-id="bfd43-227">System.Security.Cryptography.RandomNumberGenerator()</span></span>](/dotnet/api/system.security.cryptography.randomnumbergenerator)

[<span data-ttu-id="bfd43-228">Système. Random</span><span class="sxs-lookup"><span data-stu-id="bfd43-228">Sytem.Random</span></span>](/dotnet/api/system.random)
