---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Where-Object
ms.openlocfilehash: b5f4a64cceffa1f4f9884bb4de3211e129871ba7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205101"
---
# <span data-ttu-id="8c3bd-103">Where-Object</span><span class="sxs-lookup"><span data-stu-id="8c3bd-103">Where-Object</span></span>

## <span data-ttu-id="8c3bd-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8c3bd-104">SYNOPSIS</span></span>
<span data-ttu-id="8c3bd-105">Sélectionne les objets d'une collection en fonction de leurs valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-105">Selects objects from a collection based on their property values.</span></span>

## <span data-ttu-id="8c3bd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8c3bd-106">SYNTAX</span></span>

### <span data-ttu-id="8c3bd-107">EqualSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8c3bd-107">EqualSet (Default)</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-EQ]
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-108">ScriptBlockSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-108">ScriptBlockSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-FilterScript] <ScriptBlock> [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-109">MatchSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-109">MatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Match
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-110">CaseSensitiveEqualSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-110">CaseSensitiveEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CEQ
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-111">NotEqualSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-111">NotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NE
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-112">CaseSensitiveNotEqualSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-112">CaseSensitiveNotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNE
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-113">GreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-113">GreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GT
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-114">CaseSensitiveGreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-114">CaseSensitiveGreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGT
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-115">LessThanSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-115">LessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LT
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-116">CaseSensitiveLessThanSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-116">CaseSensitiveLessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLT
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-117">GreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-117">GreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GE
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-118">CaseSensitiveGreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-118">CaseSensitiveGreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGE
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-119">LessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-119">LessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LE
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-120">CaseSensitiveLessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-120">CaseSensitiveLessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLE
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-121">LikeSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-121">LikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Like
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-122">CaseSensitiveLikeSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-122">CaseSensitiveLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLike
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-123">NotLikeSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-123">NotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotLike
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-124">CaseSensitiveNotLikeSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-124">CaseSensitiveNotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotLike
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-125">CaseSensitiveMatchSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-125">CaseSensitiveMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CMatch
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-126">NotMatchSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-126">NotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotMatch
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-127">CaseSensitiveNotMatchSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-127">CaseSensitiveNotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotMatch
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-128">ContainsSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-128">ContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Contains
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-129">CaseSensitiveContainsSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-129">CaseSensitiveContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CContains
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-130">NotContainsSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-130">NotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotContains
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-131">CaseSensitiveNotContainsSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-131">CaseSensitiveNotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotContains
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-132">Incrustation</span><span class="sxs-lookup"><span data-stu-id="8c3bd-132">InSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -In
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-133">CaseSensitiveInSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-133">CaseSensitiveInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CIn
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-134">NotInSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-134">NotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotIn
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-135">CaseSensitiveNotInSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-135">CaseSensitiveNotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotIn
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-136">IsSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-136">IsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Is
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-137">IsNotSet</span><span class="sxs-lookup"><span data-stu-id="8c3bd-137">IsNotSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -IsNot
 [<CommonParameters>]
```

### <span data-ttu-id="8c3bd-138">Not</span><span class="sxs-lookup"><span data-stu-id="8c3bd-138">Not</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> -Not [<CommonParameters>]
```

## <span data-ttu-id="8c3bd-139">Description</span><span class="sxs-lookup"><span data-stu-id="8c3bd-139">DESCRIPTION</span></span>

<span data-ttu-id="8c3bd-140">L' `Where-Object` applet de commande sélectionne des objets qui ont des valeurs de propriété particulières de la collection d’objets qui lui sont passés.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-140">The `Where-Object` cmdlet selects objects that have particular property values from the collection of objects that are passed to it.</span></span> <span data-ttu-id="8c3bd-141">Par exemple, vous pouvez utiliser l' `Where-Object` applet de commande pour sélectionner des fichiers qui ont été créés après une certaine date, des événements avec un ID particulier ou des ordinateurs qui utilisent une version particulière de Windows.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-141">For example, you can use the `Where-Object` cmdlet to select files that were created after a certain date, events with a particular ID, or computers that use a particular version of Windows.</span></span>

<span data-ttu-id="8c3bd-142">À compter de Windows PowerShell 3,0, il existe deux façons de construire une `Where-Object` commande.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-142">Starting in Windows PowerShell 3.0, there are two different ways to construct a `Where-Object` command.</span></span>

- <span data-ttu-id="8c3bd-143">**Bloc de script** .</span><span class="sxs-lookup"><span data-stu-id="8c3bd-143">**Script block** .</span></span> <span data-ttu-id="8c3bd-144">Vous pouvez utiliser un bloc de script pour spécifier le nom de propriété, un opérateur de comparaison et une valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-144">You can use a script block to specify the property name, a comparison operator, and a property value.</span></span> <span data-ttu-id="8c3bd-145">`Where-Object` retourne tous les objets pour lesquels l’instruction de bloc de script a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-145">`Where-Object` returns all objects for which the script block statement is true.</span></span>

  <span data-ttu-id="8c3bd-146">Par exemple, la commande suivante obtient les processus dans la classe de priorité normale, autrement dit, les processus où la valeur de la propriété **PriorityClass** est égale à normal.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-146">For example, the following command gets processes in the Normal priority class, that is, processes where the value of the **PriorityClass** property equals Normal.</span></span>

  `Get-Process | Where-Object {$_.PriorityClass -eq "Normal"}`

  <span data-ttu-id="8c3bd-147">Tous les opérateurs de comparaison PowerShell sont valides dans le format de bloc de script.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-147">All PowerShell comparison operators are valid in the script block format.</span></span> <span data-ttu-id="8c3bd-148">Pour plus d’informations sur les opérateurs de comparaison, consultez [about_Comparison_Operators](./About/about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="8c3bd-148">For more information about comparison operators, see [about_Comparison_Operators](./About/about_Comparison_Operators.md).</span></span>

- <span data-ttu-id="8c3bd-149">**Instruction de comparaison** .</span><span class="sxs-lookup"><span data-stu-id="8c3bd-149">**Comparison statement** .</span></span> <span data-ttu-id="8c3bd-150">Vous pouvez également écrire une instruction de comparaison, laquelle se rapproche beaucoup plus du langage naturel.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-150">You can also write a comparison statement, which is much more like natural language.</span></span> <span data-ttu-id="8c3bd-151">Les instructions de comparaison ont été introduites dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-151">Comparison statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="8c3bd-152">Par exemple, les commandes suivantes obtiennent également les processus dont la classe de priorité est normal.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-152">For example, the following commands also get processes that have a priority class of Normal.</span></span> <span data-ttu-id="8c3bd-153">Ces commandes sont équivalentes et peuvent être utilisées de manière interchangeable.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-153">These commands are equivalent and can be used interchangeably.</span></span>

  `Get-Process | Where-Object -Property PriorityClass -eq -Value "Normal"`

  `Get-Process | Where-Object PriorityClass -eq "Normal"`

  <span data-ttu-id="8c3bd-154">À compter de Windows PowerShell 3,0, `Where-Object` ajoute des opérateurs de comparaison comme paramètres dans une `Where-Object` commande.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-154">Starting in Windows PowerShell 3.0, `Where-Object` adds comparison operators as parameters in a `Where-Object` command.</span></span> <span data-ttu-id="8c3bd-155">Sauf indication contraire, tous les opérateurs respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-155">Unless specified, all operators are case-insensitive.</span></span> <span data-ttu-id="8c3bd-156">Avant Windows PowerShell 3,0, les opérateurs de comparaison dans le langage PowerShell pouvaient être utilisés uniquement dans les blocs de script.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-156">Prior to Windows PowerShell 3.0, the comparison operators in the PowerShell language could be used only in script blocks.</span></span>

<span data-ttu-id="8c3bd-157">Lorsque vous fournissez une **propriété** unique à `Where-Object` , la valeur de la propriété est traitée comme une expression booléenne.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-157">When you provide a single **Property** to `Where-Object`, the value of the property is treated as a boolean expression.</span></span> <span data-ttu-id="8c3bd-158">Lorsque la valeur de **Length** n’est pas égale à zéro, l’expression prend la valeur **true** .</span><span class="sxs-lookup"><span data-stu-id="8c3bd-158">When the value of **Length** is not zero, the expression evaluates to **True** .</span></span> <span data-ttu-id="8c3bd-159">Par exemple : `('hi', '', 'there') | Where-Object Length`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-159">For example: `('hi', '', 'there') | Where-Object Length`</span></span>

<span data-ttu-id="8c3bd-160">L’exemple précédent est fonctionnellement équivalent à :</span><span class="sxs-lookup"><span data-stu-id="8c3bd-160">The previous example is functionally equivalent to:</span></span>

- `('hi', '', 'there') | Where-Object Length -GT 0`
- `('hi', '', 'there') | Where-Object {$_.Length -gt 0}`

## <span data-ttu-id="8c3bd-161">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8c3bd-161">EXAMPLES</span></span>

### <span data-ttu-id="8c3bd-162">Exemple 1 : accéder aux services arrêtés</span><span class="sxs-lookup"><span data-stu-id="8c3bd-162">Example 1: Get stopped services</span></span>

<span data-ttu-id="8c3bd-163">Ces commandes obtiennent une liste de tous les services qui sont actuellement arrêtés.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-163">These commands get a list of all services that are currently stopped.</span></span> <span data-ttu-id="8c3bd-164">La `$_` variable automatique représente chaque objet passé à l’applet de commande `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="8c3bd-164">The `$_` automatic variable represents each object that is passed to the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="8c3bd-165">La première commande utilise le format de bloc de script, la deuxième commande utilise le format d’instruction de comparaison.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-165">The first command uses the script block format, the second command uses the comparison statement format.</span></span> <span data-ttu-id="8c3bd-166">Les commandes sont équivalentes et peuvent être utilisées indifféremment.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-166">The commands are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Stopped"}
Get-Service | where Status -eq "Stopped"
```

### <span data-ttu-id="8c3bd-167">Exemple 2 : récupérer des processus en fonction de la plage de travail</span><span class="sxs-lookup"><span data-stu-id="8c3bd-167">Example 2: Get processes based on working set</span></span>

<span data-ttu-id="8c3bd-168">Ces commandes répertorient les processus dont la plage de travail est supérieure à 250 mégaoctets (Ko).</span><span class="sxs-lookup"><span data-stu-id="8c3bd-168">These commands list processes that have a working set greater than 250 megabytes (KB).</span></span> <span data-ttu-id="8c3bd-169">La syntaxe du scriptblock et de l’instruction sont équivalentes et peuvent être utilisées indifféremment.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-169">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.WorkingSet -GT 250MB}
Get-Process | Where-Object WorkingSet -GT (250MB)
```

### <span data-ttu-id="8c3bd-170">Exemple 3 : récupérer des processus en fonction du nom du processus</span><span class="sxs-lookup"><span data-stu-id="8c3bd-170">Example 3: Get processes based on process name</span></span>

<span data-ttu-id="8c3bd-171">Ces commandes obtiennent les processus qui ont une valeur de propriété **ProcessName** qui commence par la lettre `p` .</span><span class="sxs-lookup"><span data-stu-id="8c3bd-171">These commands get the processes that have a **ProcessName** property value that begins with the letter `p`.</span></span> <span data-ttu-id="8c3bd-172">L’opérateur **match** vous permet d’utiliser des correspondances d’expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-172">The **Match** operator lets you use regular expression matches.</span></span>

<span data-ttu-id="8c3bd-173">La syntaxe du scriptblock et de l’instruction sont équivalentes et peuvent être utilisées indifféremment.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-173">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.ProcessName -Match "^p.*"}
Get-Process | Where-Object ProcessName -Match "^p.*"
```

### <span data-ttu-id="8c3bd-174">Exemple 4 : utiliser le format d’instruction de comparaison</span><span class="sxs-lookup"><span data-stu-id="8c3bd-174">Example 4: Use the comparison statement format</span></span>

<span data-ttu-id="8c3bd-175">Cet exemple montre comment utiliser le nouveau format d’instruction de comparaison de l’applet de commande `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="8c3bd-175">This example shows how to use the new comparison statement format of the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="8c3bd-176">La première commande utilise le format d'instruction de comparaison.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-176">The first command uses the comparison statement format.</span></span>
<span data-ttu-id="8c3bd-177">Dans cette commande, aucun alias n'est utilisé. En outre, tous les paramètres incluent le nom de paramètre.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-177">In this command, no aliases are used and all parameters include the parameter name.</span></span>

<span data-ttu-id="8c3bd-178">La deuxième commande représente l'utilisation la plus naturelle du format de commande de comparaison.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-178">The second command is the more natural use of the comparison command format.</span></span> <span data-ttu-id="8c3bd-179">L' `where` alias est remplacé par le nom de l’applet de commande `Where-Object` et tous les noms de paramètres facultatifs sont omis.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-179">The `where` alias is substituted for the `Where-Object` cmdlet name and all optional parameter names are omitted.</span></span>

```powershell
Get-Process | Where-Object -Property Handles -GE -Value 1000
Get-Process | where Handles -GE 1000
```

### <span data-ttu-id="8c3bd-180">Exemple 5 : récupérer des commandes basées sur des propriétés</span><span class="sxs-lookup"><span data-stu-id="8c3bd-180">Example 5: Get commands based on properties</span></span>

<span data-ttu-id="8c3bd-181">Cet exemple montre comment écrire des commandes qui retournent des éléments ayant la valeur true ou false, ou ayant une valeur correspondant à une propriété spécifique.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-181">This example shows how to write commands that return items that are true or false or have any value for a specified property.</span></span> <span data-ttu-id="8c3bd-182">Chaque exemple montre les formats de bloc de script et d’instruction de comparaison pour la commande.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-182">Each example shows both the script block and comparison statement formats for the command.</span></span>

```powershell
# Use Where-Object to get commands that have any value for the OutputType property of the command.
# This omits commands that do not have an OutputType property and those that have an OutputType property, but no property value.
Get-Command | where OutputType
Get-Command | where {$_.OutputType}
```

```powershell
# Use Where-Object to get objects that are containers.
# This gets objects that have the **PSIsContainer** property with a value of $True and excludes all others.
Get-ChildItem | where PSIsContainer
Get-ChildItem | where {$_.PSIsContainer}
```

```powershell
# Finally, use the Not operator (!) to get objects that are not containers.
# This gets objects that do have the **PSIsContainer** property and those that have a value of $False for the **PSIsContainer** property.
Get-ChildItem | where {!$_.PSIsContainer}
# You cannot use the Not operator (!) in the comparison statement format of the command.
Get-ChildItem | where PSIsContainer -eq $False
```

### <span data-ttu-id="8c3bd-183">Exemple 6 : utiliser plusieurs conditions</span><span class="sxs-lookup"><span data-stu-id="8c3bd-183">Example 6: Use multiple conditions</span></span>

```powershell
Get-Module -ListAvailable | where {($_.Name -notlike "Microsoft*" -and $_.Name -notlike "PS*") -and $_.HelpInfoUri}
```

<span data-ttu-id="8c3bd-184">Cet exemple montre comment créer une `Where-Object` commande avec plusieurs conditions.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-184">This example shows how to create a `Where-Object` command with multiple conditions.</span></span>

<span data-ttu-id="8c3bd-185">Cette commande obtient les modules qui ne sont pas des modules de base et qui prennent en charge la fonctionnalité d'aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-185">This command gets non-core modules that support the Updatable Help feature.</span></span> <span data-ttu-id="8c3bd-186">La commande utilise le paramètre **listAvailable** de l' `Get-Module` applet de commande pour récupérer tous les modules sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-186">The command uses the **ListAvailable** parameter of the `Get-Module` cmdlet to get all modules on the computer.</span></span> <span data-ttu-id="8c3bd-187">Un opérateur de pipeline ( `|` ) envoie les modules à l’applet de commande `Where-Object` , qui obtient les modules dont les noms ne commencent pas par Microsoft ou PS, et qui ont une valeur pour la propriété **HelpInfoURI** , qui indique à PowerShell où trouver les fichiers d’aide mis à jour pour le module.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-187">A pipeline operator (`|`) sends the modules to the `Where-Object` cmdlet, which gets modules whose names do not begin with Microsoft or PS, and have a value for the **HelpInfoURI** property, which tells PowerShell where to find updated help files for the module.</span></span> <span data-ttu-id="8c3bd-188">Les instructions de comparaison sont connectées par l’opérateur logique **and** .</span><span class="sxs-lookup"><span data-stu-id="8c3bd-188">The comparison statements are connected by the **And** logical operator.</span></span>

<span data-ttu-id="8c3bd-189">L'exemple utilise le format de commande de bloc de script.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-189">The example uses the script block command format.</span></span> <span data-ttu-id="8c3bd-190">Les opérateurs logiques, tels que **and** et **or** , sont valides uniquement dans les blocs de script.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-190">Logical operators, such as **And** and **Or** , are valid only in script blocks.</span></span> <span data-ttu-id="8c3bd-191">Vous ne pouvez pas les utiliser dans le format d’instruction de comparaison d’une `Where-Object` commande.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-191">You cannot use them in the comparison statement format of a `Where-Object` command.</span></span>

- <span data-ttu-id="8c3bd-192">Pour plus d’informations sur les opérateurs logiques PowerShell, consultez [about_Logical_Operators](./About/about_logical_operators.md).</span><span class="sxs-lookup"><span data-stu-id="8c3bd-192">For more information about PowerShell logical operators, see [about_Logical_Operators](./About/about_logical_operators.md).</span></span>
- <span data-ttu-id="8c3bd-193">Pour plus d’informations sur la fonctionnalité d’aide actualisable, consultez [about_Updatable_Help](./About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="8c3bd-193">For more information about the Updatable Help feature, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

## <span data-ttu-id="8c3bd-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8c3bd-194">PARAMETERS</span></span>

### <span data-ttu-id="8c3bd-195">-Contient</span><span class="sxs-lookup"><span data-stu-id="8c3bd-195">-CContains</span></span>

<span data-ttu-id="8c3bd-196">Indique que cette applet de commande obtient des objets d’une collection si la valeur de propriété de l’objet correspond exactement à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-196">Indicates that this cmdlet gets objects from a collection if the property value of the object is an exact match for the specified value.</span></span> <span data-ttu-id="8c3bd-197">Cette opération respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-197">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c3bd-198">Par exemple : `Get-Process | where ProcessName -CContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-198">For example: `Get-Process | where ProcessName -CContains "svchost"`</span></span>

<span data-ttu-id="8c3bd-199">**Contient** fait référence à une collection de valeurs et a la valeur true si la collection contient un élément qui correspond exactement à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-199">**CContains** refers to a collection of values and is true if the collection contains an item that is an exact match for the specified value.</span></span> <span data-ttu-id="8c3bd-200">Si l’entrée est un objet unique, PowerShell la convertit en collection d’un seul objet.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-200">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="8c3bd-201">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-201">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-202">-CEQ</span><span class="sxs-lookup"><span data-stu-id="8c3bd-202">-CEQ</span></span>

<span data-ttu-id="8c3bd-203">Indique que cette applet de commande obtient des objets si la valeur de propriété est identique à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-203">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>
<span data-ttu-id="8c3bd-204">Cette opération respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-204">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c3bd-205">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-205">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-206">-CGE MySQL</span><span class="sxs-lookup"><span data-stu-id="8c3bd-206">-CGE</span></span>

<span data-ttu-id="8c3bd-207">Indique que cette applet de commande obtient des objets si la valeur de propriété est supérieure ou égale à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-207">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span> <span data-ttu-id="8c3bd-208">Cette opération respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-208">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c3bd-209">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-209">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-210">-CGT</span><span class="sxs-lookup"><span data-stu-id="8c3bd-210">-CGT</span></span>

<span data-ttu-id="8c3bd-211">Indique que cette applet de commande obtient des objets si la valeur de propriété est supérieure à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-211">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>
<span data-ttu-id="8c3bd-212">Cette opération respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-212">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c3bd-213">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-213">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-214">-CIn</span><span class="sxs-lookup"><span data-stu-id="8c3bd-214">-CIn</span></span>

<span data-ttu-id="8c3bd-215">Indique que cette applet de commande obtient des objets si la valeur de propriété comprend la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-215">Indicates that this cmdlet gets objects if the property value includes the specified value.</span></span> <span data-ttu-id="8c3bd-216">Cette opération respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-216">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c3bd-217">Par exemple : `Get-Process | where -Value "svchost" -CIn ProcessName`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-217">For example: `Get-Process | where -Value "svchost" -CIn ProcessName`</span></span>

<span data-ttu-id="8c3bd-218">**CIN** ressemble à **contient** , à ceci près que les positions des propriétés et des valeurs sont inversées.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-218">**CIn** resembles **CContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="8c3bd-219">Par exemple, les instructions suivantes sont toutes les deux vraies.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-219">For example, the following statements are both true.</span></span>

`"abc", "def" -CContains "abc"`

`"abc" -CIn "abc", "def"`

<span data-ttu-id="8c3bd-220">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-220">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-221">-CLE</span><span class="sxs-lookup"><span data-stu-id="8c3bd-221">-CLE</span></span>

<span data-ttu-id="8c3bd-222">Indique que cette applet de commande obtient des objets si la valeur de propriété est inférieure ou égale à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-222">Indicates that this cmdlet gets objects if the property value is less-than or equal to the specified value.</span></span> <span data-ttu-id="8c3bd-223">Cette opération respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-223">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c3bd-224">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-224">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-225">-CLik</span><span class="sxs-lookup"><span data-stu-id="8c3bd-225">-CLike</span></span>

<span data-ttu-id="8c3bd-226">Indique que cette applet de commande obtient des objets si la valeur de propriété correspond à une valeur qui comprend des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-226">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span> <span data-ttu-id="8c3bd-227">Cette opération respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-227">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c3bd-228">Par exemple : `Get-Process | where ProcessName -CLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-228">For example: `Get-Process | where ProcessName -CLike "*host"`</span></span>

<span data-ttu-id="8c3bd-229">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-229">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-230">-CLT</span><span class="sxs-lookup"><span data-stu-id="8c3bd-230">-CLT</span></span>

<span data-ttu-id="8c3bd-231">Indique que cette applet de commande obtient des objets si la valeur de propriété est inférieure à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-231">Indicates that this cmdlet gets objects if the property value is less-than the specified value.</span></span> <span data-ttu-id="8c3bd-232">Cette opération respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-232">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c3bd-233">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-233">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-234">-CMatch</span><span class="sxs-lookup"><span data-stu-id="8c3bd-234">-CMatch</span></span>

<span data-ttu-id="8c3bd-235">Indique que cette applet de commande obtient des objets si la valeur de propriété correspond à l’expression régulière spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-235">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="8c3bd-236">Cette opération respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-236">This operation is case-sensitive.</span></span> <span data-ttu-id="8c3bd-237">Quand l’entrée est scalaire, la valeur correspondante est enregistrée dans la `$Matches` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-237">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="8c3bd-238">Par exemple : `Get-Process | where ProcessName -CMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-238">For example: `Get-Process | where ProcessName -CMatch "Shell"`</span></span>

<span data-ttu-id="8c3bd-239">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-239">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-240">-CNE</span><span class="sxs-lookup"><span data-stu-id="8c3bd-240">-CNE</span></span>

<span data-ttu-id="8c3bd-241">Indique que cette applet de commande obtient des objets si la valeur de propriété est différente de la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-241">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>
<span data-ttu-id="8c3bd-242">Cette opération respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-242">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c3bd-243">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-243">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-244">-Cnotcontains font</span><span class="sxs-lookup"><span data-stu-id="8c3bd-244">-CNotContains</span></span>

<span data-ttu-id="8c3bd-245">Indique que cette applet de commande obtient des objets si la valeur de propriété de l’objet ne correspond pas exactement à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-245">Indicates that this cmdlet gets objects if the property value of the object is not an exact match for the specified value.</span></span> <span data-ttu-id="8c3bd-246">Cette opération respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-246">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c3bd-247">Par exemple : `Get-Process | where ProcessName -CNotContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-247">For example: `Get-Process | where ProcessName -CNotContains "svchost"`</span></span>

<span data-ttu-id="8c3bd-248">**NotContains** et **cnotcontains font** font référence à une collection de valeurs et ont la valeur true lorsque la collection ne contient aucun élément qui correspond exactement à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-248">**NotContains** and **CNotContains** refer to a collection of values and are true when the collection does not contains any items that are an exact match for the specified value.</span></span> <span data-ttu-id="8c3bd-249">Si l’entrée est un objet unique, PowerShell la convertit en collection d’un seul objet.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-249">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="8c3bd-250">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-250">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-251">-CNotIn</span><span class="sxs-lookup"><span data-stu-id="8c3bd-251">-CNotIn</span></span>

<span data-ttu-id="8c3bd-252">Indique que cette applet de commande obtient des objets si la valeur de propriété n’est pas une correspondance exacte pour la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-252">Indicates that this cmdlet gets objects if the property value is not an exact match for the specified value.</span></span> <span data-ttu-id="8c3bd-253">Cette opération respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-253">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c3bd-254">Par exemple : `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-254">For example: `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span></span>

<span data-ttu-id="8c3bd-255">Les opérateurs **NotIn** et **CNotIn** ressemblent à **NotContains** et **cnotcontains font** , à ceci près que les positions des propriétés et des valeurs sont inversées.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-255">**NotIn** and **CNotIn** operators resemble **NotContains** and **CNotContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="8c3bd-256">Par exemple, les instructions suivantes sont vraies.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-256">For example, the following statements are true.</span></span>

`"abc", "def" -CNotContains "Abc"`

`"abc" -CNotIn "Abc", "def"`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-257">-CNotLike</span><span class="sxs-lookup"><span data-stu-id="8c3bd-257">-CNotLike</span></span>

<span data-ttu-id="8c3bd-258">Indique que cette applet de commande obtient des objets si la valeur de propriété ne correspond pas à une valeur qui comprend des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-258">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span> <span data-ttu-id="8c3bd-259">Cette opération respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-259">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c3bd-260">Par exemple : `Get-Process | where ProcessName -CNotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-260">For example: `Get-Process | where ProcessName -CNotLike "*host"`</span></span>

<span data-ttu-id="8c3bd-261">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-262">-CNotMatch</span><span class="sxs-lookup"><span data-stu-id="8c3bd-262">-CNotMatch</span></span>

<span data-ttu-id="8c3bd-263">Indique que cette applet de commande obtient des objets si la valeur de propriété ne correspond pas à l’expression régulière spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-263">Indicates that this cmdlet gets objects if the property value does not match the specified regular expression.</span></span> <span data-ttu-id="8c3bd-264">Cette opération respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-264">This operation is case-sensitive.</span></span> <span data-ttu-id="8c3bd-265">Quand l’entrée est scalaire, la valeur correspondante est enregistrée dans la `$Matches` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-265">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="8c3bd-266">Par exemple : `Get-Process | where ProcessName -CNotMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-266">For example: `Get-Process | where ProcessName -CNotMatch "Shell"`</span></span>

<span data-ttu-id="8c3bd-267">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-267">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-268">-Contient</span><span class="sxs-lookup"><span data-stu-id="8c3bd-268">-Contains</span></span>

<span data-ttu-id="8c3bd-269">Indique que cette applet de commande obtient des objets si un élément de la valeur de propriété de l’objet correspond exactement à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-269">Indicates that this cmdlet gets objects if any item in the property value of the object is an exact match for the specified value.</span></span>

<span data-ttu-id="8c3bd-270">Par exemple : `Get-Process | where ProcessName -Contains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-270">For example: `Get-Process | where ProcessName -Contains "Svchost"`</span></span>

<span data-ttu-id="8c3bd-271">Si la valeur de propriété contient un objet unique, PowerShell la convertit en une collection d’un objet.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-271">If the property value contains a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="8c3bd-272">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-272">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainsSet
Aliases: IContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-273">-EQ</span><span class="sxs-lookup"><span data-stu-id="8c3bd-273">-EQ</span></span>

<span data-ttu-id="8c3bd-274">Indique que cette applet de commande obtient des objets si la valeur de propriété est identique à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-274">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>

<span data-ttu-id="8c3bd-275">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-275">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: EqualSet
Aliases: IEQ

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-276">-FilterScript</span><span class="sxs-lookup"><span data-stu-id="8c3bd-276">-FilterScript</span></span>

<span data-ttu-id="8c3bd-277">Spécifie le bloc de script utilisé pour filtrer les objets.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-277">Specifies the script block that is used to filter the objects.</span></span> <span data-ttu-id="8c3bd-278">Placez le bloc de script entre accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="8c3bd-278">Enclose the script block in braces (`{}`).</span></span>

<span data-ttu-id="8c3bd-279">Le nom de paramètre, **FilterScript** , est facultatif.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-279">The parameter name, **FilterScript** , is optional.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-280">-GE</span><span class="sxs-lookup"><span data-stu-id="8c3bd-280">-GE</span></span>

<span data-ttu-id="8c3bd-281">Indique que cette applet de commande obtient des objets si la valeur de propriété est supérieure ou égale à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-281">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span>

<span data-ttu-id="8c3bd-282">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-282">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterOrEqualSet
Aliases: IGE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-283">-GT</span><span class="sxs-lookup"><span data-stu-id="8c3bd-283">-GT</span></span>

<span data-ttu-id="8c3bd-284">Indique que cette applet de commande obtient des objets si la valeur de propriété est supérieure à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-284">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>

<span data-ttu-id="8c3bd-285">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-285">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterThanSet
Aliases: IGT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-286">-In</span><span class="sxs-lookup"><span data-stu-id="8c3bd-286">-In</span></span>

<span data-ttu-id="8c3bd-287">Indique que cette applet de commande obtient des objets si la valeur de propriété correspond à l’une des valeurs spécifiées.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-287">Indicates that this cmdlet gets objects if the property value matches any of the specified values.</span></span>
<span data-ttu-id="8c3bd-288">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8c3bd-288">For example:</span></span>

`Get-Process | where -Property ProcessName -in -Value "Svchost", "TaskHost", "WsmProvHost"`

<span data-ttu-id="8c3bd-289">Si la valeur du paramètre de **valeur** est un objet unique, PowerShell le convertit en une collection d’un objet.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-289">If the value of the **Value** parameter is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="8c3bd-290">Si la valeur de propriété d’un objet est un tableau, PowerShell utilise l’égalité des références pour déterminer une correspondance.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-290">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="8c3bd-291">`Where-Object` retourne l’objet uniquement si la valeur du paramètre de **propriété** et toute valeur de **valeur** sont la même instance d’un objet.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-291">`Where-Object` returns the object only if the value of the **Property** parameter and any value of **Value** are the same instance of an object.</span></span>

<span data-ttu-id="8c3bd-292">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-292">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InSet
Aliases: IIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-293">-InputObject</span><span class="sxs-lookup"><span data-stu-id="8c3bd-293">-InputObject</span></span>

<span data-ttu-id="8c3bd-294">Spécifie les objets à filtrer.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-294">Specifies the objects to be filtered.</span></span> <span data-ttu-id="8c3bd-295">Vous pouvez également diriger les objets vers `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="8c3bd-295">You can also pipe the objects to `Where-Object`.</span></span>

<span data-ttu-id="8c3bd-296">Quand vous utilisez le paramètre **InputObject** avec `Where-Object` , au lieu de rediriger les résultats de la commande vers `Where-Object` , la valeur **InputObject** est traitée comme un objet unique.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-296">When you use the **InputObject** parameter with `Where-Object`, instead of piping command results to `Where-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="8c3bd-297">Cela est vrai même si la valeur est une collection qui est le résultat d’une commande, telle que `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="8c3bd-297">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span> <span data-ttu-id="8c3bd-298">Étant donné que **InputObject** ne peut pas retourner des propriétés individuelles d’un tableau ou d’une collection d’objets, nous vous recommandons, si vous utilisez `Where-Object` pour filtrer une collection d’objets pour les objets qui ont des valeurs spécifiques dans les propriétés définies, d’utiliser `Where-Object` dans le pipeline, comme indiqué dans les exemples de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-298">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that, if you use `Where-Object` to filter a collection of objects for those objects that have specific values in defined properties, you use `Where-Object` in the pipeline, as shown in the examples in this topic.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-299">-Est</span><span class="sxs-lookup"><span data-stu-id="8c3bd-299">-Is</span></span>

<span data-ttu-id="8c3bd-300">Indique que cette applet de commande obtient des objets si la valeur de propriété est une instance du type .NET spécifié.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-300">Indicates that this cmdlet gets objects if the property value is an instance of the specified .NET type.</span></span> <span data-ttu-id="8c3bd-301">Placez le nom du type entre crochets.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-301">Enclose the type name in square brackets.</span></span>

<span data-ttu-id="8c3bd-302">Par exemple : `Get-Process | where StartTime -Is [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-302">For example, `Get-Process | where StartTime -Is [DateTime]`</span></span>

<span data-ttu-id="8c3bd-303">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-303">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-304">-IsNot</span><span class="sxs-lookup"><span data-stu-id="8c3bd-304">-IsNot</span></span>

<span data-ttu-id="8c3bd-305">Indique que cette applet de commande obtient des objets si la valeur de propriété n’est pas une instance du type .NET spécifié.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-305">Indicates that this cmdlet gets objects if the property value is not an instance of the specified .NET type.</span></span>

<span data-ttu-id="8c3bd-306">Par exemple : `Get-Process | where StartTime -IsNot [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-306">For example, `Get-Process | where StartTime -IsNot [DateTime]`</span></span>

<span data-ttu-id="8c3bd-307">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-307">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsNotSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-308">-LE</span><span class="sxs-lookup"><span data-stu-id="8c3bd-308">-LE</span></span>

<span data-ttu-id="8c3bd-309">Indique que cette applet de commande obtient des objets si la valeur de propriété est inférieure ou égale à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-309">Indicates that this cmdlet gets objects if the property value is less than or equal to the specified value.</span></span>

<span data-ttu-id="8c3bd-310">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-310">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessOrEqualSet
Aliases: ILE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-311">-Like</span><span class="sxs-lookup"><span data-stu-id="8c3bd-311">-Like</span></span>

<span data-ttu-id="8c3bd-312">Indique que cette applet de commande obtient des objets si la valeur de propriété correspond à une valeur qui comprend des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-312">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span>

<span data-ttu-id="8c3bd-313">Par exemple : `Get-Process | where ProcessName -Like "*host"`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-313">For example: `Get-Process | where ProcessName -Like "*host"`</span></span>

<span data-ttu-id="8c3bd-314">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-314">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LikeSet
Aliases: ILike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-315">-LT</span><span class="sxs-lookup"><span data-stu-id="8c3bd-315">-LT</span></span>

<span data-ttu-id="8c3bd-316">Indique que cette applet de commande obtient des objets si la valeur de propriété est inférieure à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-316">Indicates that this cmdlet gets objects if the property value is less than the specified value.</span></span>

<span data-ttu-id="8c3bd-317">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-317">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessThanSet
Aliases: ILT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-318">-Match</span><span class="sxs-lookup"><span data-stu-id="8c3bd-318">-Match</span></span>

<span data-ttu-id="8c3bd-319">Indique que cette applet de commande obtient des objets si la valeur de propriété correspond à l’expression régulière spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-319">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="8c3bd-320">Quand l’entrée est scalaire, la valeur correspondante est enregistrée dans la `$Matches` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-320">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="8c3bd-321">Par exemple : `Get-Process | where ProcessName -Match "shell"`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-321">For example: `Get-Process | where ProcessName -Match "shell"`</span></span>

<span data-ttu-id="8c3bd-322">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-322">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MatchSet
Aliases: IMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-323">-Ne</span><span class="sxs-lookup"><span data-stu-id="8c3bd-323">-NE</span></span>

<span data-ttu-id="8c3bd-324">Indique que cette applet de commande obtient des objets si la valeur de propriété est différente de la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-324">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>

<span data-ttu-id="8c3bd-325">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-325">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotEqualSet
Aliases: INE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-326">-Non</span><span class="sxs-lookup"><span data-stu-id="8c3bd-326">-Not</span></span>

<span data-ttu-id="8c3bd-327">Indique que cette applet de commande obtient des objets si la propriété n’existe pas ou a une valeur null ou false.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-327">Indicates that this cmdlet gets objects if the property does not exist or has a value of null or false.</span></span>

<span data-ttu-id="8c3bd-328">Par exemple : `Get-Service | where -Not "DependentServices"`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-328">For example: `Get-Service | where -Not "DependentServices"`</span></span>

<span data-ttu-id="8c3bd-329">Ce paramètre a été introduit dans Windows PowerShell 6,1.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-329">This parameter was introduced in Windows PowerShell 6.1.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Not
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-330">-NotContains</span><span class="sxs-lookup"><span data-stu-id="8c3bd-330">-NotContains</span></span>

<span data-ttu-id="8c3bd-331">Indique que cette applet de commande obtient des objets si aucun des éléments de la valeur de propriété ne correspond exactement à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-331">Indicates that this cmdlet gets objects if none of the items in the property value is an exact match for the specified value.</span></span>

<span data-ttu-id="8c3bd-332">Par exemple : `Get-Process | where ProcessName -NotContains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-332">For example: `Get-Process | where ProcessName -NotContains "Svchost"`</span></span>

<span data-ttu-id="8c3bd-333">**NotContains** fait référence à une collection de valeurs et a la valeur true si la collection ne contient aucun élément qui correspond exactement à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-333">**NotContains** refers to a collection of values and is true if the collection does not contain any items that are an exact match for the specified value.</span></span> <span data-ttu-id="8c3bd-334">Si l’entrée est un objet unique, PowerShell la convertit en collection d’un seul objet.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-334">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="8c3bd-335">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-335">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotContainsSet
Aliases: INotContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-336">-NotIn</span><span class="sxs-lookup"><span data-stu-id="8c3bd-336">-NotIn</span></span>

<span data-ttu-id="8c3bd-337">Indique que cette applet de commande obtient des objets si la valeur de propriété n’est pas une correspondance exacte pour l’une des valeurs spécifiées.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-337">Indicates that this cmdlet gets objects if the property value is not an exact match for any of the specified values.</span></span>

<span data-ttu-id="8c3bd-338">Par exemple : `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-338">For example: `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span></span>

<span data-ttu-id="8c3bd-339">Si la valeur de la **valeur** est un objet unique, PowerShell la convertit en collection d’un seul objet.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-339">If the value of **Value** is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="8c3bd-340">Si la valeur de propriété d’un objet est un tableau, PowerShell utilise l’égalité des références pour déterminer une correspondance.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-340">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="8c3bd-341">`Where-Object` retourne l’objet uniquement si la valeur de la **propriété** et toute valeur de **value** ne sont pas la même instance d’un objet.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-341">`Where-Object` returns the object only if the value of **Property** and any value of **Value** are not the same instance of an object.</span></span>

<span data-ttu-id="8c3bd-342">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-342">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotInSet
Aliases: INotIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-343">-NotLike</span><span class="sxs-lookup"><span data-stu-id="8c3bd-343">-NotLike</span></span>

<span data-ttu-id="8c3bd-344">Indique que cette applet de commande obtient des objets si la valeur de propriété ne correspond pas à une valeur qui comprend des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-344">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span>

<span data-ttu-id="8c3bd-345">Par exemple : `Get-Process | where ProcessName -NotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-345">For example: `Get-Process | where ProcessName -NotLike "*host"`</span></span>

<span data-ttu-id="8c3bd-346">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-346">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotLikeSet
Aliases: INotLike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-347">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="8c3bd-347">-NotMatch</span></span>

<span data-ttu-id="8c3bd-348">Indique que cette applet de commande obtient des objets quand la valeur de propriété ne correspond pas à l’expression régulière spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-348">Indicates that this cmdlet gets objects when the property value does not match the specified regular expression.</span></span> <span data-ttu-id="8c3bd-349">Quand l’entrée est scalaire, la valeur correspondante est enregistrée dans la `$Matches` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-349">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="8c3bd-350">Par exemple : `Get-Process | where ProcessName -NotMatch "PowerShell"`</span><span class="sxs-lookup"><span data-stu-id="8c3bd-350">For example: `Get-Process | where ProcessName -NotMatch "PowerShell"`</span></span>

<span data-ttu-id="8c3bd-351">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-351">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotMatchSet
Aliases: INotMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-352">-Propriété</span><span class="sxs-lookup"><span data-stu-id="8c3bd-352">-Property</span></span>

<span data-ttu-id="8c3bd-353">Spécifie le nom d'une propriété d'objet.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-353">Specifies the name of an object property.</span></span> <span data-ttu-id="8c3bd-354">Le nom du paramètre, **Property** , est facultatif.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-354">The parameter name, **Property** , is optional.</span></span>

<span data-ttu-id="8c3bd-355">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-355">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: EqualSet, LessOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet, Not
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c3bd-356">-Value</span><span class="sxs-lookup"><span data-stu-id="8c3bd-356">-Value</span></span>

<span data-ttu-id="8c3bd-357">Spécifie une valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-357">Specifies a property value.</span></span> <span data-ttu-id="8c3bd-358">Le nom du paramètre, **value** , est facultatif.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-358">The parameter name, **Value** , is optional.</span></span> <span data-ttu-id="8c3bd-359">Ce paramètre accepte les caractères génériques lorsqu’il est utilisé avec les paramètres de comparaison suivants :</span><span class="sxs-lookup"><span data-stu-id="8c3bd-359">This parameter accepts wildcard characters when used with the following comparison parameters:</span></span>

- <span data-ttu-id="8c3bd-360">**CLik**</span><span class="sxs-lookup"><span data-stu-id="8c3bd-360">**CLike**</span></span>
- <span data-ttu-id="8c3bd-361">**CNotLike**</span><span class="sxs-lookup"><span data-stu-id="8c3bd-361">**CNotLike**</span></span>
- <span data-ttu-id="8c3bd-362">**Parent**</span><span class="sxs-lookup"><span data-stu-id="8c3bd-362">**Like**</span></span>
- <span data-ttu-id="8c3bd-363">**NotLike**</span><span class="sxs-lookup"><span data-stu-id="8c3bd-363">**NotLike**</span></span>

<span data-ttu-id="8c3bd-364">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-364">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: EqualSet, LessOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8c3bd-365">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8c3bd-365">CommonParameters</span></span>

<span data-ttu-id="8c3bd-366">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-366">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8c3bd-367">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8c3bd-367">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8c3bd-368">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8c3bd-368">INPUTS</span></span>

### <span data-ttu-id="8c3bd-369">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="8c3bd-369">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="8c3bd-370">Vous pouvez diriger les objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-370">You can pipe the objects to this cmdlet.</span></span>

## <span data-ttu-id="8c3bd-371">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8c3bd-371">OUTPUTS</span></span>

### <span data-ttu-id="8c3bd-372">Object</span><span class="sxs-lookup"><span data-stu-id="8c3bd-372">Object</span></span>

<span data-ttu-id="8c3bd-373">Cette applet de commande retourne les éléments sélectionnés dans le jeu d’objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-373">This cmdlet returns selected items from the input object set.</span></span>

## <span data-ttu-id="8c3bd-374">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8c3bd-374">NOTES</span></span>

<span data-ttu-id="8c3bd-375">À compter de Windows PowerShell 4,0, `Where` les `ForEach` méthodes et ont été ajoutées pour être utilisées avec les collections.</span><span class="sxs-lookup"><span data-stu-id="8c3bd-375">Starting in Windows PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span>

<span data-ttu-id="8c3bd-376">Vous pouvez en savoir plus sur ces nouvelles méthodes ici [about_Arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="8c3bd-376">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

## <span data-ttu-id="8c3bd-377">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8c3bd-377">RELATED LINKS</span></span>

[<span data-ttu-id="8c3bd-378">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="8c3bd-378">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="8c3bd-379">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="8c3bd-379">ForEach-Object</span></span>](ForEach-Object.md)

[<span data-ttu-id="8c3bd-380">Group-Object</span><span class="sxs-lookup"><span data-stu-id="8c3bd-380">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="8c3bd-381">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="8c3bd-381">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="8c3bd-382">New-Object</span><span class="sxs-lookup"><span data-stu-id="8c3bd-382">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="8c3bd-383">Select-Object</span><span class="sxs-lookup"><span data-stu-id="8c3bd-383">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="8c3bd-384">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="8c3bd-384">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="8c3bd-385">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="8c3bd-385">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)

