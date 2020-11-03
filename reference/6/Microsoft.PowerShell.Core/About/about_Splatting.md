---
description: Décrit comment utiliser la projection pour passer des paramètres à des commandes dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_splatting?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Splatting
ms.openlocfilehash: 7c479beffe7e424b7f880c81db7da3b4ec10d817
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206857"
---
# <a name="about-splatting"></a><span data-ttu-id="0b73a-104">À propos de la projection</span><span class="sxs-lookup"><span data-stu-id="0b73a-104">About Splatting</span></span>

## <a name="short-description"></a><span data-ttu-id="0b73a-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="0b73a-105">Short description</span></span>

<span data-ttu-id="0b73a-106">Décrit comment utiliser la projection pour passer des paramètres à des commandes dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b73a-106">Describes how to use splatting to pass parameters to commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="0b73a-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="0b73a-107">Long description</span></span>

<span data-ttu-id="0b73a-108">La projection est une méthode de transmission d’une collection de valeurs de paramètre à une commande en tant qu’unité.</span><span class="sxs-lookup"><span data-stu-id="0b73a-108">Splatting is a method of passing a collection of parameter values to a command as a unit.</span></span> <span data-ttu-id="0b73a-109">PowerShell associe chaque valeur de la collection à un paramètre de commande.</span><span class="sxs-lookup"><span data-stu-id="0b73a-109">PowerShell associates each value in the collection with a command parameter.</span></span> <span data-ttu-id="0b73a-110">Les valeurs de paramètres réintégrés sont stockées dans des variables de projection nommées, qui ressemblent à des variables standard, mais commencent par un symbole arobase ( `@` ) au lieu d’un signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="0b73a-110">Splatted parameter values are stored in named splatting variables, which look like standard variables, but begin with an At symbol (`@`) instead of a dollar sign (`$`).</span></span> <span data-ttu-id="0b73a-111">Le symbole at indique à PowerShell que vous passez une collection de valeurs, au lieu d’une seule valeur.</span><span class="sxs-lookup"><span data-stu-id="0b73a-111">The At symbol tells PowerShell that you are passing a collection of values, instead of a single value.</span></span>

<span data-ttu-id="0b73a-112">La projection rend vos commandes plus courtes et plus faciles à lire.</span><span class="sxs-lookup"><span data-stu-id="0b73a-112">Splatting makes your commands shorter and easier to read.</span></span> <span data-ttu-id="0b73a-113">Vous pouvez réutiliser les valeurs de réorganisation dans des appels de commande différents et utiliser la projection pour passer des valeurs de paramètre de la `$PSBoundParameters` variable automatique à d’autres scripts et fonctions.</span><span class="sxs-lookup"><span data-stu-id="0b73a-113">You can reuse the splatting values in different command calls and use splatting to pass parameter values from the `$PSBoundParameters` automatic variable to other scripts and functions.</span></span>

<span data-ttu-id="0b73a-114">À compter de Windows PowerShell 3,0, vous pouvez également utiliser la projection pour représenter tous les paramètres d’une commande.</span><span class="sxs-lookup"><span data-stu-id="0b73a-114">Beginning in Windows PowerShell 3.0, you can also use splatting to represent all parameters of a command.</span></span>

## <a name="syntax"></a><span data-ttu-id="0b73a-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b73a-115">Syntax</span></span>

```
<CommandName> <optional parameters> @<HashTable> <optional parameters>
<CommandName> <optional parameters> @<Array> <optional parameters>
```

<span data-ttu-id="0b73a-116">Pour fournir des valeurs de paramètre pour les paramètres positionnels, dans lesquelles les noms de paramètres ne sont pas requis, utilisez la syntaxe de tableau.</span><span class="sxs-lookup"><span data-stu-id="0b73a-116">To provide parameter values for positional parameters, in which parameter names are not required, use the array syntax.</span></span> <span data-ttu-id="0b73a-117">Pour fournir des paires nom de paramètre/valeur, utilisez la syntaxe de table de hachage.</span><span class="sxs-lookup"><span data-stu-id="0b73a-117">To provide parameter name and value pairs, use the hash table syntax.</span></span> <span data-ttu-id="0b73a-118">La valeur de la projection peut apparaître n’importe où dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="0b73a-118">The splatted value can appear anywhere in the parameter list.</span></span>

<span data-ttu-id="0b73a-119">Lors de la projection, vous n’avez pas besoin d’utiliser une table de hachage ou un tableau pour passer tous les paramètres.</span><span class="sxs-lookup"><span data-stu-id="0b73a-119">When splatting, you do not need to use a hash table or an array to pass all parameters.</span></span> <span data-ttu-id="0b73a-120">Vous pouvez passer certains paramètres en utilisant la projection et en passer d’autres par position ou par nom de paramètre.</span><span class="sxs-lookup"><span data-stu-id="0b73a-120">You may pass some parameters by using splatting and pass others by position or by parameter name.</span></span> <span data-ttu-id="0b73a-121">En outre, vous pouvez se terminant par plusieurs objets dans une même commande afin de ne pas transmettre plus d’une valeur pour chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="0b73a-121">Also, you can splat multiple objects in a single command so you don't pass more than one value for each parameter.</span></span>

## <a name="splatting-with-hash-tables"></a><span data-ttu-id="0b73a-122">Projection avec des tables de hachage</span><span class="sxs-lookup"><span data-stu-id="0b73a-122">Splatting with hash tables</span></span>

<span data-ttu-id="0b73a-123">Utilisez une table de hachage pour se terminant par les paires nom de paramètre/valeur.</span><span class="sxs-lookup"><span data-stu-id="0b73a-123">Use a hash table to splat parameter name and value pairs.</span></span> <span data-ttu-id="0b73a-124">Vous pouvez utiliser ce format pour tous les types de paramètres, y compris les paramètres positionnels et de commutateur.</span><span class="sxs-lookup"><span data-stu-id="0b73a-124">You can use this format for all parameter types, including positional and switch parameters.</span></span>
<span data-ttu-id="0b73a-125">Les paramètres positionnels doivent être attribués par nom.</span><span class="sxs-lookup"><span data-stu-id="0b73a-125">Positional parameters must be assigned by name.</span></span>

<span data-ttu-id="0b73a-126">Les exemples suivants comparent deux `Copy-Item` commandes qui copient le fichier Test.txt dans le fichier Test2.txt dans le même répertoire.</span><span class="sxs-lookup"><span data-stu-id="0b73a-126">The following examples compare two `Copy-Item` commands that copy the Test.txt file to the Test2.txt file in the same directory.</span></span>

<span data-ttu-id="0b73a-127">Le premier exemple utilise le format traditionnel dans lequel les noms de paramètres sont inclus.</span><span class="sxs-lookup"><span data-stu-id="0b73a-127">The first example uses the traditional format in which parameter names are included.</span></span>

```powershell
Copy-Item -Path "test.txt" -Destination "test2.txt" -WhatIf
```

<span data-ttu-id="0b73a-128">Le deuxième exemple utilise la projection de table de hachage.</span><span class="sxs-lookup"><span data-stu-id="0b73a-128">The second example uses hash table splatting.</span></span> <span data-ttu-id="0b73a-129">La première commande crée une table de hachage de paires paramètre-nom et paramètre-valeur et la stocke dans la `$HashArguments` variable.</span><span class="sxs-lookup"><span data-stu-id="0b73a-129">The first command creates a hash table of parameter-name and parameter-value pairs and stores it in the `$HashArguments` variable.</span></span> <span data-ttu-id="0b73a-130">La deuxième commande utilise la `$HashArguments` variable dans une commande avec projection.</span><span class="sxs-lookup"><span data-stu-id="0b73a-130">The second command uses the `$HashArguments` variable in a command with splatting.</span></span> <span data-ttu-id="0b73a-131">Le symbole arobase ( `@HashArguments` ) remplace le signe dollar ( `$HashArguments` ) dans la commande.</span><span class="sxs-lookup"><span data-stu-id="0b73a-131">The At symbol (`@HashArguments`) replaces the dollar sign (`$HashArguments`) in the command.</span></span>

<span data-ttu-id="0b73a-132">Pour fournir une valeur pour le paramètre de commutateur **WhatIf** , utilisez `$True` ou `$False` .</span><span class="sxs-lookup"><span data-stu-id="0b73a-132">To provide a value for the **WhatIf** switch parameter, use `$True` or `$False`.</span></span>

```powershell
$HashArguments = @{
  Path = "test.txt"
  Destination = "test2.txt"
  WhatIf = $true
}
Copy-Item @HashArguments
```

> [!NOTE]
> <span data-ttu-id="0b73a-133">Dans la première commande, le symbole arobase ( `@` ) indique une table de hachage, et non une valeur à la fois.</span><span class="sxs-lookup"><span data-stu-id="0b73a-133">In the first command, the At symbol (`@`) indicates a hash table, not a splatted value.</span></span> <span data-ttu-id="0b73a-134">La syntaxe des tables de hachage dans PowerShell est la suivante : `@{<name>=<value>; <name>=<value>; ...}`</span><span class="sxs-lookup"><span data-stu-id="0b73a-134">The syntax for hash tables in PowerShell is: `@{<name>=<value>; <name>=<value>; ...}`</span></span>

## <a name="splatting-with-arrays"></a><span data-ttu-id="0b73a-135">Projection avec des tableaux</span><span class="sxs-lookup"><span data-stu-id="0b73a-135">Splatting with arrays</span></span>

<span data-ttu-id="0b73a-136">Utilisez un tableau pour se terminant par des valeurs pour les paramètres positionnels, qui ne nécessitent pas de noms de paramètres.</span><span class="sxs-lookup"><span data-stu-id="0b73a-136">Use an array to splat values for positional parameters, which do not require parameter names.</span></span> <span data-ttu-id="0b73a-137">Les valeurs doivent être dans l’ordre de numéro de position dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="0b73a-137">The values must be in position-number order in the array.</span></span>

<span data-ttu-id="0b73a-138">Les exemples suivants comparent deux `Copy-Item` commandes qui copient le fichier Test.txt dans le fichier Test2.txt dans le même répertoire.</span><span class="sxs-lookup"><span data-stu-id="0b73a-138">The following examples compare two `Copy-Item` commands that copy the Test.txt file to the Test2.txt file in the same directory.</span></span>

<span data-ttu-id="0b73a-139">Le premier exemple utilise le format traditionnel dans lequel les noms de paramètres sont omis.</span><span class="sxs-lookup"><span data-stu-id="0b73a-139">The first example uses the traditional format in which parameter names are omitted.</span></span> <span data-ttu-id="0b73a-140">Les valeurs des paramètres apparaissent dans l’ordre de position dans la commande.</span><span class="sxs-lookup"><span data-stu-id="0b73a-140">The parameter values appear in position order in the command.</span></span>

```powershell
Copy-Item "test.txt" "test2.txt" -WhatIf
```

<span data-ttu-id="0b73a-141">Le deuxième exemple utilise la projection de tableau.</span><span class="sxs-lookup"><span data-stu-id="0b73a-141">The second example uses array splatting.</span></span> <span data-ttu-id="0b73a-142">La première commande crée un tableau des valeurs de paramètre et les stocke dans la `$ArrayArguments` variable.</span><span class="sxs-lookup"><span data-stu-id="0b73a-142">The first command creates an array of the parameter values and stores it in the `$ArrayArguments` variable.</span></span> <span data-ttu-id="0b73a-143">Les valeurs sont dans l’ordre de position dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="0b73a-143">The values are in position order in the array.</span></span> <span data-ttu-id="0b73a-144">La deuxième commande utilise la `$ArrayArguments` variable dans une commande en cours de projection.</span><span class="sxs-lookup"><span data-stu-id="0b73a-144">The second command uses the `$ArrayArguments` variable in a command in splatting.</span></span> <span data-ttu-id="0b73a-145">Le symbole arobase ( `@ArrayArguments` ) remplace le signe dollar ( `$ArrayArguments` ) dans la commande.</span><span class="sxs-lookup"><span data-stu-id="0b73a-145">The At symbol (`@ArrayArguments`) replaces the dollar sign (`$ArrayArguments`) in the command.</span></span>

```powershell
$ArrayArguments = "test.txt", "test2.txt"
Copy-Item @ArrayArguments -WhatIf
```

### <a name="using-the-argumentlist-parameter"></a><span data-ttu-id="0b73a-146">Utilisation du paramètre ArgumentList</span><span class="sxs-lookup"><span data-stu-id="0b73a-146">Using the ArgumentList parameter</span></span>

<span data-ttu-id="0b73a-147">Plusieurs applets de commande ont un paramètre **argumentlist** qui est utilisé pour passer des valeurs de paramètre à un bloc de script qui est exécuté par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0b73a-147">Several cmdlets have an **ArgumentList** parameter that is used to pass parameter values to a script block that is executed by the cmdlet.</span></span> <span data-ttu-id="0b73a-148">Le paramètre **argumentlist** prend un tableau de valeurs qui est passé au bloc de script.</span><span class="sxs-lookup"><span data-stu-id="0b73a-148">The **ArgumentList** parameter takes an array of values that is passed to the script block.</span></span> <span data-ttu-id="0b73a-149">PowerShell utilise en fait la projection de tableau pour lier les valeurs aux paramètres du bloc de script.</span><span class="sxs-lookup"><span data-stu-id="0b73a-149">PowerShell is effectively using array splatting to bind the values to the parameters of the script block.</span></span> <span data-ttu-id="0b73a-150">Lorsque vous utilisez **argumentlist** , si vous devez passer un tableau en tant qu’objet unique lié à un seul paramètre, vous devez encapsuler le tableau comme seul élément d’un autre tableau.</span><span class="sxs-lookup"><span data-stu-id="0b73a-150">When using **ArgumentList** , if you need to pass an array as a single object bound to a single parameter, you must wrap the array as the only element of another array.</span></span>

<span data-ttu-id="0b73a-151">L’exemple suivant a un bloc de script qui accepte un paramètre unique qui est un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="0b73a-151">The following example has a script block that takes a single parameter that is an array of strings.</span></span>

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList $array
```

<span data-ttu-id="0b73a-152">Dans cet exemple, seul le premier élément de `$array` est passé au bloc de script.</span><span class="sxs-lookup"><span data-stu-id="0b73a-152">In this example, only the first item in `$array` is passed to the script block.</span></span>

```Output
Hello
```

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
} -ArgumentList (,$array)
```

<span data-ttu-id="0b73a-153">Dans cet exemple, `$array` est encapsulé dans un tableau afin que le tableau entier soit passé au bloc de script sous la forme d’un objet unique.</span><span class="sxs-lookup"><span data-stu-id="0b73a-153">In this example, `$array` is wrapped in an array so that the entire array is passed to the script block as a single object.</span></span>

```Output
Hello World!
```

## <a name="examples"></a><span data-ttu-id="0b73a-154">Exemples</span><span class="sxs-lookup"><span data-stu-id="0b73a-154">Examples</span></span>

<span data-ttu-id="0b73a-155">Cet exemple montre comment réutiliser des valeurs réintégrées dans des commandes différentes.</span><span class="sxs-lookup"><span data-stu-id="0b73a-155">This example shows how to reuse splatted values in different commands.</span></span> <span data-ttu-id="0b73a-156">Dans cet exemple, les commandes utilisent l' `Write-Host` applet de commande pour écrire des messages dans la console du programme hôte.</span><span class="sxs-lookup"><span data-stu-id="0b73a-156">The commands in this example use the `Write-Host` cmdlet to write messages to the host program console.</span></span> <span data-ttu-id="0b73a-157">Elle utilise la projection pour spécifier les couleurs de premier plan et d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="0b73a-157">It uses splatting to specify the foreground and background colors.</span></span>

<span data-ttu-id="0b73a-158">Pour modifier les couleurs de toutes les commandes, il vous suffit de modifier la valeur de la `$Colors` variable.</span><span class="sxs-lookup"><span data-stu-id="0b73a-158">To change the colors of all commands, just change the value of the `$Colors` variable.</span></span>

<span data-ttu-id="0b73a-159">La première commande crée une table de hachage de noms et de valeurs de paramètres et stocke la table de hachage dans la `$Colors` variable.</span><span class="sxs-lookup"><span data-stu-id="0b73a-159">The first command creates a hash table of parameter names and values and stores the hash table in the `$Colors` variable.</span></span>

```powershell
$Colors = @{ForegroundColor = "black"; BackgroundColor = "white"}
```

<span data-ttu-id="0b73a-160">Les deuxième et troisième commandes utilisent la `$Colors` variable pour la projection dans une `Write-Host` commande.</span><span class="sxs-lookup"><span data-stu-id="0b73a-160">The second and third commands use the `$Colors` variable for splatting in a `Write-Host` command.</span></span> <span data-ttu-id="0b73a-161">Pour utiliser le `$Colors variable` , remplacez le signe dollar ( `$Colors` ) par un symbole arobase ( `@Colors` ).</span><span class="sxs-lookup"><span data-stu-id="0b73a-161">To use the `$Colors variable`, replace the dollar sign (`$Colors`) with an At symbol (`@Colors`).</span></span>

```powershell
#Write a message with the colors in $Colors
Write-Host "This is a test." @Colors

#Write second message with same colors. The position of splatted
#hash table does not matter.
Write-Host @Colors "This is another test."
```

<span data-ttu-id="0b73a-162">Cet exemple montre comment transférer leurs paramètres à d’autres commandes à l’aide de la variable de projection et de la `$PSBoundParameters` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="0b73a-162">This example shows how to forward their parameters to other commands by using splatting and the `$PSBoundParameters` automatic variable.</span></span>

<span data-ttu-id="0b73a-163">La `$PSBoundParameters` variable automatique est un objet dictionnaire (System. Collections. Generic. Dictionary) qui contient tous les noms et valeurs de paramètres utilisés lors de l’exécution d’un script ou d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="0b73a-163">The `$PSBoundParameters` automatic variable is a dictionary object (System.Collections.Generic.Dictionary) that contains all the parameter names and values that are used when a script or function is run.</span></span>

<span data-ttu-id="0b73a-164">Dans l’exemple suivant, nous utilisons la `$PSBoundParameters` variable pour transférer les valeurs de paramètres passées à un script ou à une fonction de `Test2` la fonction à la `Test1` fonction.</span><span class="sxs-lookup"><span data-stu-id="0b73a-164">In the following example, we use the `$PSBoundParameters` variable to forward the parameters values passed to a script or function from `Test2` function to the `Test1` function.</span></span> <span data-ttu-id="0b73a-165">Les deux appels à la `Test1` fonction à partir de `Test2` utilisent la projection.</span><span class="sxs-lookup"><span data-stu-id="0b73a-165">Both calls to the `Test1` function from `Test2` use splatting.</span></span>

```powershell
function Test1
{
    param($a, $b, $c)

    $a
    $b
    $c
}

function Test2
{
    param($a, $b, $c)

    #Call the Test1 function with $a, $b, and $c.
    Test1 @PsBoundParameters

    #Call the Test1 function with $b and $c, but not with $a
    $LimitedParameters = $PSBoundParameters
    $LimitedParameters.Remove("a") | Out-Null
    Test1 @LimitedParameters
}
```

```Output
Test2 -a 1 -b 2 -c 3
1
2
3
2
3
```

## <a name="splatting-command-parameters"></a><span data-ttu-id="0b73a-166">Paramètres de commande de projection</span><span class="sxs-lookup"><span data-stu-id="0b73a-166">Splatting command parameters</span></span>

<span data-ttu-id="0b73a-167">Vous pouvez utiliser la projection pour représenter les paramètres d’une commande.</span><span class="sxs-lookup"><span data-stu-id="0b73a-167">You can use splatting to represent the parameters of a command.</span></span> <span data-ttu-id="0b73a-168">Cette technique est utile lorsque vous créez une fonction proxy, c’est-à-dire une fonction qui appelle une autre commande.</span><span class="sxs-lookup"><span data-stu-id="0b73a-168">This technique is useful when you are creating a proxy function, that is, a function that calls another command.</span></span> <span data-ttu-id="0b73a-169">Cette fonctionnalité est introduite dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0b73a-169">This feature is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="0b73a-170">Pour se terminant par les paramètres d’une commande, utilisez `@Args` pour représenter les paramètres de commande.</span><span class="sxs-lookup"><span data-stu-id="0b73a-170">To splat the parameters of a command, use `@Args` to represent the command parameters.</span></span> <span data-ttu-id="0b73a-171">Cette technique est plus facile que l’énumération des paramètres de commande et elle fonctionne sans révision même si les paramètres de la commande appelée changent.</span><span class="sxs-lookup"><span data-stu-id="0b73a-171">This technique is easier than enumerating command parameters and it works without revision even if the parameters of the called command change.</span></span>

<span data-ttu-id="0b73a-172">La fonctionnalité utilise la `$Args` variable automatique, qui contient toutes les valeurs de paramètre non assignées.</span><span class="sxs-lookup"><span data-stu-id="0b73a-172">The feature uses the `$Args` automatic variable, which contains all unassigned parameter values.</span></span>

<span data-ttu-id="0b73a-173">Par exemple, la fonction suivante appelle l' `Get-Process` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0b73a-173">For example, the following function calls the `Get-Process` cmdlet.</span></span> <span data-ttu-id="0b73a-174">Dans cette fonction, `@Args` représente tous les paramètres de l' `Get-Process` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0b73a-174">In this function, `@Args` represents all the parameters of the `Get-Process` cmdlet.</span></span>

```powershell
function Get-MyProcess { Get-Process @Args }
```

<span data-ttu-id="0b73a-175">Lorsque vous utilisez la `Get-MyProcess` fonction, tous les paramètres et valeurs de paramètre non assignés sont passés à `@Args` , comme indiqué dans les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="0b73a-175">When you use the `Get-MyProcess` function, all unassigned parameters and parameter values are passed to `@Args`, as shown in the following commands.</span></span>

```powershell
Get-MyProcess -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    463      46   225484     237196   719    15.86   3228 powershell
```

```powershell
Get-MyProcess -Name PowerShell_Ise -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.2.9200.16384   6.2.9200.1638... C:\Windows\system32\WindowsPowerShell\...
```

<span data-ttu-id="0b73a-176">Vous pouvez utiliser `@Args` dans une fonction qui a des paramètres déclarés explicitement.</span><span class="sxs-lookup"><span data-stu-id="0b73a-176">You can use `@Args` in a function that has explicitly declared parameters.</span></span> <span data-ttu-id="0b73a-177">Vous pouvez l’utiliser plusieurs fois dans une fonction, mais tous les paramètres que vous entrez sont passés à toutes les instances de `@Args` , comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0b73a-177">You can use it more than once in a function, but all parameters that you enter are passed to all instances of `@Args`, as shown in the following example.</span></span>

```powershell
function Get-MyCommand
{
    Param ([switch]$P, [switch]$C)
    if ($P) { Get-Process @Args }
    if ($C) { Get-Command @Args }
}

Get-MyCommand -P -C -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
408      28    75568      83176   620     1.33   1692 powershell

Path               : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Extension          : .exe
Definition         : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Visibility         : Public
OutputType         : {System.String}
Name               : powershell.exe
CommandType        : Application
ModuleName         :
Module             :
RemotingCapability : PowerShell
Parameters         :
ParameterSets      :
HelpUri            :
FileVersionInfo    : File:             C:\Windows\System32\WindowsPowerShell
                     \v1.0\powershell.exe
                     InternalName:     POWERSHELL
                     OriginalFilename: PowerShell.EXE.MUI
                     FileVersion:      10.0.14393.0 (rs1_release.160715-1616
                     FileDescription:  Windows PowerShell
                     Product:          Microsoft Windows Operating System
                     ProductVersion:   10.0.14393.0
                     Debug:            False
                     Patched:          False
                     PreRelease:       False
                     PrivateBuild:     False
                     SpecialBuild:     False
                     Language:         English (United States)
```

## <a name="notes"></a><span data-ttu-id="0b73a-178">Notes</span><span class="sxs-lookup"><span data-stu-id="0b73a-178">Notes</span></span>

<span data-ttu-id="0b73a-179">Si vous faites une fonction dans une fonction avancée à l’aide des attributs **CmdletBinding** ou **Parameter** , la `$args` variable automatique n’est plus disponible dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="0b73a-179">If you make a function into an advanced function by using either the **CmdletBinding** or **Parameter** attributes, the `$args` automatic variable is no longer available in the function.</span></span> <span data-ttu-id="0b73a-180">Les fonctions avancées nécessitent une définition de paramètre explicite.</span><span class="sxs-lookup"><span data-stu-id="0b73a-180">Advanced functions require explicit parameter definition.</span></span>

<span data-ttu-id="0b73a-181">La configuration d’état souhaité (DSC) PowerShell n’a pas été conçue pour utiliser la projection.</span><span class="sxs-lookup"><span data-stu-id="0b73a-181">PowerShell Desired State Configuration (DSC) was not designed to use splatting.</span></span>
<span data-ttu-id="0b73a-182">Vous ne pouvez pas utiliser la projection pour passer des valeurs dans une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="0b73a-182">You cannot use splatting to pass values into a DSC resource.</span></span> <span data-ttu-id="0b73a-183">Pour plus d’informations, consultez l’article intitulé « [Pseudo-relatting DSC](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/)» de gael Colas.</span><span class="sxs-lookup"><span data-stu-id="0b73a-183">For more information, see Gael Colas' article [Pseudo-Splatting DSC Resources](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/).</span></span>

## <a name="see-also"></a><span data-ttu-id="0b73a-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b73a-184">See also</span></span>

[<span data-ttu-id="0b73a-185">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="0b73a-185">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="0b73a-186">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="0b73a-186">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="0b73a-187">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="0b73a-187">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="0b73a-188">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="0b73a-188">about_Parameters</span></span>](about_Parameters.md)
