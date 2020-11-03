---
description: Décrit comment utiliser la projection pour passer des paramètres à des commandes dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_splatting?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Splatting
ms.openlocfilehash: a64cbbe5edd40bf4fc7f9b7347421988d225e666
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207278"
---
# <a name="about-splatting"></a><span data-ttu-id="f225d-104">À propos de la projection</span><span class="sxs-lookup"><span data-stu-id="f225d-104">About Splatting</span></span>

## <a name="short-description"></a><span data-ttu-id="f225d-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="f225d-105">Short description</span></span>

<span data-ttu-id="f225d-106">Décrit comment utiliser la projection pour passer des paramètres à des commandes dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f225d-106">Describes how to use splatting to pass parameters to commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="f225d-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="f225d-107">Long description</span></span>

<span data-ttu-id="f225d-108">La projection est une méthode de transmission d’une collection de valeurs de paramètre à une commande en tant qu’unité.</span><span class="sxs-lookup"><span data-stu-id="f225d-108">Splatting is a method of passing a collection of parameter values to a command as a unit.</span></span> <span data-ttu-id="f225d-109">PowerShell associe chaque valeur de la collection à un paramètre de commande.</span><span class="sxs-lookup"><span data-stu-id="f225d-109">PowerShell associates each value in the collection with a command parameter.</span></span> <span data-ttu-id="f225d-110">Les valeurs de paramètres réintégrés sont stockées dans des variables de projection nommées, qui ressemblent à des variables standard, mais commencent par un symbole arobase ( `@` ) au lieu d’un signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="f225d-110">Splatted parameter values are stored in named splatting variables, which look like standard variables, but begin with an At symbol (`@`) instead of a dollar sign (`$`).</span></span> <span data-ttu-id="f225d-111">Le symbole at indique à PowerShell que vous passez une collection de valeurs, au lieu d’une seule valeur.</span><span class="sxs-lookup"><span data-stu-id="f225d-111">The At symbol tells PowerShell that you are passing a collection of values, instead of a single value.</span></span>

<span data-ttu-id="f225d-112">La projection rend vos commandes plus courtes et plus faciles à lire.</span><span class="sxs-lookup"><span data-stu-id="f225d-112">Splatting makes your commands shorter and easier to read.</span></span> <span data-ttu-id="f225d-113">Vous pouvez réutiliser les valeurs de réorganisation dans des appels de commande différents et utiliser la projection pour passer des valeurs de paramètre de la `$PSBoundParameters` variable automatique à d’autres scripts et fonctions.</span><span class="sxs-lookup"><span data-stu-id="f225d-113">You can reuse the splatting values in different command calls and use splatting to pass parameter values from the `$PSBoundParameters` automatic variable to other scripts and functions.</span></span>

<span data-ttu-id="f225d-114">À compter de Windows PowerShell 3,0, vous pouvez également utiliser la projection pour représenter tous les paramètres d’une commande.</span><span class="sxs-lookup"><span data-stu-id="f225d-114">Beginning in Windows PowerShell 3.0, you can also use splatting to represent all parameters of a command.</span></span>

## <a name="syntax"></a><span data-ttu-id="f225d-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f225d-115">Syntax</span></span>

```
<CommandName> <optional parameters> @<HashTable> <optional parameters>
<CommandName> <optional parameters> @<Array> <optional parameters>
```

<span data-ttu-id="f225d-116">Pour fournir des valeurs de paramètre pour les paramètres positionnels, dans lesquelles les noms de paramètres ne sont pas requis, utilisez la syntaxe de tableau.</span><span class="sxs-lookup"><span data-stu-id="f225d-116">To provide parameter values for positional parameters, in which parameter names are not required, use the array syntax.</span></span> <span data-ttu-id="f225d-117">Pour fournir des paires nom de paramètre/valeur, utilisez la syntaxe de table de hachage.</span><span class="sxs-lookup"><span data-stu-id="f225d-117">To provide parameter name and value pairs, use the hash table syntax.</span></span> <span data-ttu-id="f225d-118">La valeur de la projection peut apparaître n’importe où dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f225d-118">The splatted value can appear anywhere in the parameter list.</span></span>

<span data-ttu-id="f225d-119">Lors de la projection, vous n’avez pas besoin d’utiliser une table de hachage ou un tableau pour passer tous les paramètres.</span><span class="sxs-lookup"><span data-stu-id="f225d-119">When splatting, you do not need to use a hash table or an array to pass all parameters.</span></span> <span data-ttu-id="f225d-120">Vous pouvez passer certains paramètres en utilisant la projection et en passer d’autres par position ou par nom de paramètre.</span><span class="sxs-lookup"><span data-stu-id="f225d-120">You may pass some parameters by using splatting and pass others by position or by parameter name.</span></span> <span data-ttu-id="f225d-121">En outre, vous pouvez se terminant par plusieurs objets dans une même commande afin de ne pas transmettre plus d’une valeur pour chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="f225d-121">Also, you can splat multiple objects in a single command so you don't pass more than one value for each parameter.</span></span>

<span data-ttu-id="f225d-122">À partir de PowerShell 7,1, vous pouvez substituer un paramètre de la manière explicite en définissant explicitement un paramètre dans une commande.</span><span class="sxs-lookup"><span data-stu-id="f225d-122">As of PowerShell 7.1, you can override a splatted parameter by explicitly defining a parameter in a command.</span></span>

## <a name="splatting-with-hash-tables"></a><span data-ttu-id="f225d-123">Projection avec des tables de hachage</span><span class="sxs-lookup"><span data-stu-id="f225d-123">Splatting with hash tables</span></span>

<span data-ttu-id="f225d-124">Utilisez une table de hachage pour se terminant par les paires nom de paramètre/valeur.</span><span class="sxs-lookup"><span data-stu-id="f225d-124">Use a hash table to splat parameter name and value pairs.</span></span> <span data-ttu-id="f225d-125">Vous pouvez utiliser ce format pour tous les types de paramètres, y compris les paramètres positionnels et de commutateur.</span><span class="sxs-lookup"><span data-stu-id="f225d-125">You can use this format for all parameter types, including positional and switch parameters.</span></span>
<span data-ttu-id="f225d-126">Les paramètres positionnels doivent être attribués par nom.</span><span class="sxs-lookup"><span data-stu-id="f225d-126">Positional parameters must be assigned by name.</span></span>

<span data-ttu-id="f225d-127">Les exemples suivants comparent deux `Copy-Item` commandes qui copient le fichier Test.txt dans le fichier Test2.txt dans le même répertoire.</span><span class="sxs-lookup"><span data-stu-id="f225d-127">The following examples compare two `Copy-Item` commands that copy the Test.txt file to the Test2.txt file in the same directory.</span></span>

<span data-ttu-id="f225d-128">Le premier exemple utilise le format traditionnel dans lequel les noms de paramètres sont inclus.</span><span class="sxs-lookup"><span data-stu-id="f225d-128">The first example uses the traditional format in which parameter names are included.</span></span>

```powershell
Copy-Item -Path "test.txt" -Destination "test2.txt" -WhatIf
```

<span data-ttu-id="f225d-129">Le deuxième exemple utilise la projection de table de hachage.</span><span class="sxs-lookup"><span data-stu-id="f225d-129">The second example uses hash table splatting.</span></span> <span data-ttu-id="f225d-130">La première commande crée une table de hachage de paires paramètre-nom et paramètre-valeur et la stocke dans la `$HashArguments` variable.</span><span class="sxs-lookup"><span data-stu-id="f225d-130">The first command creates a hash table of parameter-name and parameter-value pairs and stores it in the `$HashArguments` variable.</span></span> <span data-ttu-id="f225d-131">La deuxième commande utilise la `$HashArguments` variable dans une commande avec projection.</span><span class="sxs-lookup"><span data-stu-id="f225d-131">The second command uses the `$HashArguments` variable in a command with splatting.</span></span> <span data-ttu-id="f225d-132">Le symbole arobase ( `@HashArguments` ) remplace le signe dollar ( `$HashArguments` ) dans la commande.</span><span class="sxs-lookup"><span data-stu-id="f225d-132">The At symbol (`@HashArguments`) replaces the dollar sign (`$HashArguments`) in the command.</span></span>

<span data-ttu-id="f225d-133">Pour fournir une valeur pour le paramètre de commutateur **WhatIf** , utilisez `$True` ou `$False` .</span><span class="sxs-lookup"><span data-stu-id="f225d-133">To provide a value for the **WhatIf** switch parameter, use `$True` or `$False`.</span></span>

```powershell
$HashArguments = @{
  Path = "test.txt"
  Destination = "test2.txt"
  WhatIf = $true
}
Copy-Item @HashArguments
```

> [!NOTE]
> <span data-ttu-id="f225d-134">Dans la première commande, le symbole arobase ( `@` ) indique une table de hachage, et non une valeur à la fois.</span><span class="sxs-lookup"><span data-stu-id="f225d-134">In the first command, the At symbol (`@`) indicates a hash table, not a splatted value.</span></span> <span data-ttu-id="f225d-135">La syntaxe des tables de hachage dans PowerShell est la suivante : `@{<name>=<value>; <name>=<value>; ...}`</span><span class="sxs-lookup"><span data-stu-id="f225d-135">The syntax for hash tables in PowerShell is: `@{<name>=<value>; <name>=<value>; ...}`</span></span>

## <a name="splatting-with-arrays"></a><span data-ttu-id="f225d-136">Projection avec des tableaux</span><span class="sxs-lookup"><span data-stu-id="f225d-136">Splatting with arrays</span></span>

<span data-ttu-id="f225d-137">Utilisez un tableau pour se terminant par des valeurs pour les paramètres positionnels, qui ne nécessitent pas de noms de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f225d-137">Use an array to splat values for positional parameters, which do not require parameter names.</span></span> <span data-ttu-id="f225d-138">Les valeurs doivent être dans l’ordre de numéro de position dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="f225d-138">The values must be in position-number order in the array.</span></span>

<span data-ttu-id="f225d-139">Les exemples suivants comparent deux `Copy-Item` commandes qui copient le fichier Test.txt dans le fichier Test2.txt dans le même répertoire.</span><span class="sxs-lookup"><span data-stu-id="f225d-139">The following examples compare two `Copy-Item` commands that copy the Test.txt file to the Test2.txt file in the same directory.</span></span>

<span data-ttu-id="f225d-140">Le premier exemple utilise le format traditionnel dans lequel les noms de paramètres sont omis.</span><span class="sxs-lookup"><span data-stu-id="f225d-140">The first example uses the traditional format in which parameter names are omitted.</span></span> <span data-ttu-id="f225d-141">Les valeurs des paramètres apparaissent dans l’ordre de position dans la commande.</span><span class="sxs-lookup"><span data-stu-id="f225d-141">The parameter values appear in position order in the command.</span></span>

```powershell
Copy-Item "test.txt" "test2.txt" -WhatIf
```

<span data-ttu-id="f225d-142">Le deuxième exemple utilise la projection de tableau.</span><span class="sxs-lookup"><span data-stu-id="f225d-142">The second example uses array splatting.</span></span> <span data-ttu-id="f225d-143">La première commande crée un tableau des valeurs de paramètre et les stocke dans la `$ArrayArguments` variable.</span><span class="sxs-lookup"><span data-stu-id="f225d-143">The first command creates an array of the parameter values and stores it in the `$ArrayArguments` variable.</span></span> <span data-ttu-id="f225d-144">Les valeurs sont dans l’ordre de position dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="f225d-144">The values are in position order in the array.</span></span> <span data-ttu-id="f225d-145">La deuxième commande utilise la `$ArrayArguments` variable dans une commande en cours de projection.</span><span class="sxs-lookup"><span data-stu-id="f225d-145">The second command uses the `$ArrayArguments` variable in a command in splatting.</span></span> <span data-ttu-id="f225d-146">Le symbole arobase ( `@ArrayArguments` ) remplace le signe dollar ( `$ArrayArguments` ) dans la commande.</span><span class="sxs-lookup"><span data-stu-id="f225d-146">The At symbol (`@ArrayArguments`) replaces the dollar sign (`$ArrayArguments`) in the command.</span></span>

```powershell
$ArrayArguments = "test.txt", "test2.txt"
Copy-Item @ArrayArguments -WhatIf
```

### <a name="using-the-argumentlist-parameter"></a><span data-ttu-id="f225d-147">Utilisation du paramètre ArgumentList</span><span class="sxs-lookup"><span data-stu-id="f225d-147">Using the ArgumentList parameter</span></span>

<span data-ttu-id="f225d-148">Plusieurs applets de commande ont un paramètre **argumentlist** qui est utilisé pour passer des valeurs de paramètre à un bloc de script qui est exécuté par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f225d-148">Several cmdlets have an **ArgumentList** parameter that is used to pass parameter values to a script block that is executed by the cmdlet.</span></span> <span data-ttu-id="f225d-149">Le paramètre **argumentlist** prend un tableau de valeurs qui est passé au bloc de script.</span><span class="sxs-lookup"><span data-stu-id="f225d-149">The **ArgumentList** parameter takes an array of values that is passed to the script block.</span></span> <span data-ttu-id="f225d-150">PowerShell utilise en fait la projection de tableau pour lier les valeurs aux paramètres du bloc de script.</span><span class="sxs-lookup"><span data-stu-id="f225d-150">PowerShell is effectively using array splatting to bind the values to the parameters of the script block.</span></span> <span data-ttu-id="f225d-151">Lorsque vous utilisez **argumentlist** , si vous devez passer un tableau en tant qu’objet unique lié à un seul paramètre, vous devez encapsuler le tableau comme seul élément d’un autre tableau.</span><span class="sxs-lookup"><span data-stu-id="f225d-151">When using **ArgumentList** , if you need to pass an array as a single object bound to a single parameter, you must wrap the array as the only element of another array.</span></span>

<span data-ttu-id="f225d-152">L’exemple suivant a un bloc de script qui accepte un paramètre unique qui est un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="f225d-152">The following example has a script block that takes a single parameter that is an array of strings.</span></span>

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList $array
```
<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->
<span data-ttu-id="f225d-153">Dans cet exemple, seul le premier élément de `$array` est passé au bloc de script.</span><span class="sxs-lookup"><span data-stu-id="f225d-153">In this example, only the first item in `$array` is passed to the script block.</span></span>

```Output
Hello
```

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
} -ArgumentList (,$array)
```

<span data-ttu-id="f225d-154">Dans cet exemple, `$array` est encapsulé dans un tableau afin que le tableau entier soit passé au bloc de script sous la forme d’un objet unique.</span><span class="sxs-lookup"><span data-stu-id="f225d-154">In this example, `$array` is wrapped in an array so that the entire array is passed to the script block as a single object.</span></span>

```Output
Hello World!
```

## <a name="examples"></a><span data-ttu-id="f225d-155">Exemples</span><span class="sxs-lookup"><span data-stu-id="f225d-155">Examples</span></span>

### <a name="example-1-reuse-splatted-parameters-in-different-commands"></a><span data-ttu-id="f225d-156">Exemple 1 : réutiliser des paramètres réintégrés dans des commandes différentes</span><span class="sxs-lookup"><span data-stu-id="f225d-156">Example 1: Reuse splatted parameters in different commands</span></span>

<span data-ttu-id="f225d-157">Cet exemple montre comment réutiliser des valeurs réintégrées dans des commandes différentes.</span><span class="sxs-lookup"><span data-stu-id="f225d-157">This example shows how to reuse splatted values in different commands.</span></span> <span data-ttu-id="f225d-158">Dans cet exemple, les commandes utilisent l' `Write-Host` applet de commande pour écrire des messages dans la console du programme hôte.</span><span class="sxs-lookup"><span data-stu-id="f225d-158">The commands in this example use the `Write-Host` cmdlet to write messages to the host program console.</span></span> <span data-ttu-id="f225d-159">Elle utilise la projection pour spécifier les couleurs de premier plan et d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="f225d-159">It uses splatting to specify the foreground and background colors.</span></span>

<span data-ttu-id="f225d-160">Pour modifier les couleurs de toutes les commandes, il vous suffit de modifier la valeur de la `$Colors` variable.</span><span class="sxs-lookup"><span data-stu-id="f225d-160">To change the colors of all commands, just change the value of the `$Colors` variable.</span></span>

<span data-ttu-id="f225d-161">La première commande crée une table de hachage de noms et de valeurs de paramètres et stocke la table de hachage dans la `$Colors` variable.</span><span class="sxs-lookup"><span data-stu-id="f225d-161">The first command creates a hash table of parameter names and values and stores the hash table in the `$Colors` variable.</span></span>

```powershell
$Colors = @{ForegroundColor = "black"; BackgroundColor = "white"}
```

<span data-ttu-id="f225d-162">Les deuxième et troisième commandes utilisent la `$Colors` variable pour la projection dans une `Write-Host` commande.</span><span class="sxs-lookup"><span data-stu-id="f225d-162">The second and third commands use the `$Colors` variable for splatting in a `Write-Host` command.</span></span> <span data-ttu-id="f225d-163">Pour utiliser le `$Colors variable` , remplacez le signe dollar ( `$Colors` ) par un symbole arobase ( `@Colors` ).</span><span class="sxs-lookup"><span data-stu-id="f225d-163">To use the `$Colors variable`, replace the dollar sign (`$Colors`) with an At symbol (`@Colors`).</span></span>

```powershell
#Write a message with the colors in $Colors
Write-Host "This is a test." @Colors

#Write second message with same colors. The position of splatted
#hash table does not matter.
Write-Host @Colors "This is another test."
```

### <a name="example-2-forward-parameters-using-psboundparameters"></a><span data-ttu-id="f225d-164">Exemple 2 : transférer des paramètres à l’aide de $PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="f225d-164">Example 2: Forward parameters using $PSBoundParameters</span></span>

<span data-ttu-id="f225d-165">Cet exemple montre comment transférer leurs paramètres à d’autres commandes à l’aide de la variable de projection et de la `$PSBoundParameters` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="f225d-165">This example shows how to forward their parameters to other commands by using splatting and the `$PSBoundParameters` automatic variable.</span></span>

<span data-ttu-id="f225d-166">La `$PSBoundParameters` variable automatique est un objet dictionnaire (System. Collections. Generic. Dictionary) qui contient tous les noms et valeurs de paramètres utilisés lors de l’exécution d’un script ou d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="f225d-166">The `$PSBoundParameters` automatic variable is a dictionary object (System.Collections.Generic.Dictionary) that contains all the parameter names and values that are used when a script or function is run.</span></span>

<span data-ttu-id="f225d-167">Dans l’exemple suivant, nous utilisons la `$PSBoundParameters` variable pour transférer les valeurs de paramètres passées à un script ou à une fonction de `Test2` la fonction à la `Test1` fonction.</span><span class="sxs-lookup"><span data-stu-id="f225d-167">In the following example, we use the `$PSBoundParameters` variable to forward the parameters values passed to a script or function from `Test2` function to the `Test1` function.</span></span> <span data-ttu-id="f225d-168">Les deux appels à la `Test1` fonction à partir de `Test2` utilisent la projection.</span><span class="sxs-lookup"><span data-stu-id="f225d-168">Both calls to the `Test1` function from `Test2` use splatting.</span></span>

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

### <a name="example-3-override-splatted-parameters-with-explicitly-defined-parameters"></a><span data-ttu-id="f225d-169">Exemple 3 : remplacement de paramètres à l’aide de paramètres définis de manière explicite</span><span class="sxs-lookup"><span data-stu-id="f225d-169">Example 3: Override splatted parameters with explicitly defined parameters</span></span>

<span data-ttu-id="f225d-170">Cet exemple montre comment substituer un paramètre de projection à l’aide de paramètres définis de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="f225d-170">This example shows how to override a splatted parameter using explicitly defined parameters.</span></span> <span data-ttu-id="f225d-171">Cela est utile lorsque vous ne souhaitez pas créer de nouvelle Hashtable ou modifier une valeur dans la Hashtable que vous utilisez pour se terminant par.</span><span class="sxs-lookup"><span data-stu-id="f225d-171">This is useful when you don't want to build a new hashtable or change a value in the hashtable you are using to splat.</span></span>

<span data-ttu-id="f225d-172">La `$commonParams` variable stocke les paramètres pour créer des ordinateurs virtuels à l' `East US` emplacement.</span><span class="sxs-lookup"><span data-stu-id="f225d-172">The `$commonParams` variable stores the parameters to create virtual machines in the `East US` location.</span></span> <span data-ttu-id="f225d-173">La `$allVms` variable est une liste de machines virtuelles à créer.</span><span class="sxs-lookup"><span data-stu-id="f225d-173">The `$allVms` variable is a list of virtual machines to create.</span></span> <span data-ttu-id="f225d-174">Nous parcourons la liste et utilisons `$commonParams` pour se terminant par les paramètres afin de créer chaque machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="f225d-174">We loop through the list and use `$commonParams` to splat the parameters to create each virtual machine.</span></span> <span data-ttu-id="f225d-175">Toutefois, nous voulons `myVM2` créer dans une région différente de celle des autres machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="f225d-175">However, we want `myVM2` to be created in a different region than the other virtual machines.</span></span> <span data-ttu-id="f225d-176">Au lieu d’ajuster la `$commonParams` Hashtable, vous pouvez définir explicitement le paramètre **location** dans `New-AzVm` pour remplacer la valeur de la `Location` clé dans `$commonParams` .</span><span class="sxs-lookup"><span data-stu-id="f225d-176">Instead of adjusting the `$commonParams` hashtable, you can explicitly define the **Location** parameter in `New-AzVm` to supersede the value of the `Location` key in `$commonParams`.</span></span>

```powershell
$commonParams = @{
    ResourceGroupName = "myResourceGroup"
    Location = "East US"
    VirtualNetworkName = "myVnet"
    SubnetName = "mySubnet"
    SecurityGroupName = "myNetworkSecurityGroup"
    PublicIpAddressName = "myPublicIpAddress"
}

$allVms = @('myVM1','myVM2','myVM3',)

foreach ($vm in $allVms)
{
    if ($vm -eq 'myVM2')
    {
        New-AzVm @commonParams -Name $vm -Location "West US"
    }
    else
    {
        New-AzVm @commonParams -Name $vm
    }
}
```

## <a name="splatting-command-parameters"></a><span data-ttu-id="f225d-177">Paramètres de commande de projection</span><span class="sxs-lookup"><span data-stu-id="f225d-177">Splatting command parameters</span></span>

<span data-ttu-id="f225d-178">Vous pouvez utiliser la projection pour représenter les paramètres d’une commande.</span><span class="sxs-lookup"><span data-stu-id="f225d-178">You can use splatting to represent the parameters of a command.</span></span> <span data-ttu-id="f225d-179">Cette technique est utile lorsque vous créez une fonction proxy, c’est-à-dire une fonction qui appelle une autre commande.</span><span class="sxs-lookup"><span data-stu-id="f225d-179">This technique is useful when you are creating a proxy function, that is, a function that calls another command.</span></span> <span data-ttu-id="f225d-180">Cette fonctionnalité est introduite dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f225d-180">This feature is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="f225d-181">Pour se terminant par les paramètres d’une commande, utilisez `@Args` pour représenter les paramètres de commande.</span><span class="sxs-lookup"><span data-stu-id="f225d-181">To splat the parameters of a command, use `@Args` to represent the command parameters.</span></span> <span data-ttu-id="f225d-182">Cette technique est plus facile que l’énumération des paramètres de commande et elle fonctionne sans révision même si les paramètres de la commande appelée changent.</span><span class="sxs-lookup"><span data-stu-id="f225d-182">This technique is easier than enumerating command parameters and it works without revision even if the parameters of the called command change.</span></span>

<span data-ttu-id="f225d-183">La fonctionnalité utilise la `$Args` variable automatique, qui contient toutes les valeurs de paramètre non assignées.</span><span class="sxs-lookup"><span data-stu-id="f225d-183">The feature uses the `$Args` automatic variable, which contains all unassigned parameter values.</span></span>

<span data-ttu-id="f225d-184">Par exemple, la fonction suivante appelle l' `Get-Process` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f225d-184">For example, the following function calls the `Get-Process` cmdlet.</span></span> <span data-ttu-id="f225d-185">Dans cette fonction, `@Args` représente tous les paramètres de l' `Get-Process` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f225d-185">In this function, `@Args` represents all the parameters of the `Get-Process` cmdlet.</span></span>

```powershell
function Get-MyProcess { Get-Process @Args }
```

<span data-ttu-id="f225d-186">Lorsque vous utilisez la `Get-MyProcess` fonction, tous les paramètres et valeurs de paramètre non assignés sont passés à `@Args` , comme indiqué dans les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f225d-186">When you use the `Get-MyProcess` function, all unassigned parameters and parameter values are passed to `@Args`, as shown in the following commands.</span></span>

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

<span data-ttu-id="f225d-187">Vous pouvez utiliser `@Args` dans une fonction qui a des paramètres déclarés explicitement.</span><span class="sxs-lookup"><span data-stu-id="f225d-187">You can use `@Args` in a function that has explicitly declared parameters.</span></span> <span data-ttu-id="f225d-188">Vous pouvez l’utiliser plusieurs fois dans une fonction, mais tous les paramètres que vous entrez sont passés à toutes les instances de `@Args` , comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f225d-188">You can use it more than once in a function, but all parameters that you enter are passed to all instances of `@Args`, as shown in the following example.</span></span>

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

## <a name="notes"></a><span data-ttu-id="f225d-189">Notes</span><span class="sxs-lookup"><span data-stu-id="f225d-189">Notes</span></span>

<span data-ttu-id="f225d-190">Si vous faites une fonction dans une fonction avancée à l’aide des attributs **CmdletBinding** ou **Parameter** , la `$args` variable automatique n’est plus disponible dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="f225d-190">If you make a function into an advanced function by using either the **CmdletBinding** or **Parameter** attributes, the `$args` automatic variable is no longer available in the function.</span></span> <span data-ttu-id="f225d-191">Les fonctions avancées nécessitent une définition de paramètre explicite.</span><span class="sxs-lookup"><span data-stu-id="f225d-191">Advanced functions require explicit parameter definition.</span></span>

<span data-ttu-id="f225d-192">La configuration d’état souhaité (DSC) PowerShell n’a pas été conçue pour utiliser la projection.</span><span class="sxs-lookup"><span data-stu-id="f225d-192">PowerShell Desired State Configuration (DSC) was not designed to use splatting.</span></span>
<span data-ttu-id="f225d-193">Vous ne pouvez pas utiliser la projection pour passer des valeurs dans une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="f225d-193">You cannot use splatting to pass values into a DSC resource.</span></span> <span data-ttu-id="f225d-194">Pour plus d’informations, consultez l’article intitulé « [Pseudo-relatting DSC](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/)» de gael Colas.</span><span class="sxs-lookup"><span data-stu-id="f225d-194">For more information, see Gael Colas' article [Pseudo-Splatting DSC Resources](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/).</span></span>

## <a name="see-also"></a><span data-ttu-id="f225d-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f225d-195">See also</span></span>

[<span data-ttu-id="f225d-196">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="f225d-196">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="f225d-197">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="f225d-197">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="f225d-198">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="f225d-198">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="f225d-199">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="f225d-199">about_Parameters</span></span>](about_Parameters.md)
