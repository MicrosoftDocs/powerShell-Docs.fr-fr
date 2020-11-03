---
description: Définit ce qu’est un bloc de script et explique comment utiliser des blocs de script dans le langage de programmation PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_blocks?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Blocks
ms.openlocfilehash: dc3ee050399e92506cabed370e95d03c65652953
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206886"
---
# <a name="about-script-blocks"></a><span data-ttu-id="cfd18-104">À propos des blocs de script</span><span class="sxs-lookup"><span data-stu-id="cfd18-104">About Script Blocks</span></span>

## <a name="short-description"></a><span data-ttu-id="cfd18-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="cfd18-105">Short description</span></span>

<span data-ttu-id="cfd18-106">Définit ce qu’est un bloc de script et explique comment utiliser des blocs de script dans le langage de programmation PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cfd18-106">Defines what a script block is and explains how to use script blocks in the PowerShell programming language.</span></span>

## <a name="long-description"></a><span data-ttu-id="cfd18-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="cfd18-107">Long description</span></span>

<span data-ttu-id="cfd18-108">Dans le langage de programmation PowerShell, un bloc de script est une collection d’instructions ou d’expressions qui peuvent être utilisées comme une seule unité.</span><span class="sxs-lookup"><span data-stu-id="cfd18-108">In the PowerShell programming language, a script block is a collection of statements or expressions that can be used as a single unit.</span></span>
<span data-ttu-id="cfd18-109">Un bloc de script peut accepter des arguments et retourner des valeurs.</span><span class="sxs-lookup"><span data-stu-id="cfd18-109">A script block can accept arguments and return values.</span></span>

<span data-ttu-id="cfd18-110">Syntaxiquement, un bloc de script est une liste d’instructions entre accolades, comme illustré dans la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="cfd18-110">Syntactically, a script block is a statement list in braces, as shown in the following syntax:</span></span>

```
{<statement list>}
```

<span data-ttu-id="cfd18-111">Un bloc de script retourne la sortie de toutes les commandes dans le bloc de script, sous la forme d’un objet unique ou d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="cfd18-111">A script block returns the output of all the commands in the script block, either as a single object or as an array.</span></span>

<span data-ttu-id="cfd18-112">Vous pouvez également spécifier une valeur de retour à l’aide du `return` mot clé.</span><span class="sxs-lookup"><span data-stu-id="cfd18-112">You can also specify a return value using the `return` keyword.</span></span> <span data-ttu-id="cfd18-113">Le `return` mot clé n’affecte pas ou ne supprime pas la sortie retournée par votre bloc de script.</span><span class="sxs-lookup"><span data-stu-id="cfd18-113">The `return` keyword does not affect or suppress other output returned from your script block.</span></span> <span data-ttu-id="cfd18-114">Toutefois, le `return` mot clé quitte le bloc de script à cette ligne.</span><span class="sxs-lookup"><span data-stu-id="cfd18-114">However, the `return` keyword exits the script block at that line.</span></span> <span data-ttu-id="cfd18-115">Pour plus d’informations, consultez [about_Return](about_Return.md).</span><span class="sxs-lookup"><span data-stu-id="cfd18-115">For more information, see [about_Return](about_Return.md).</span></span>

<span data-ttu-id="cfd18-116">Comme les fonctions, un bloc de script peut inclure des paramètres.</span><span class="sxs-lookup"><span data-stu-id="cfd18-116">Like functions, a script block can include parameters.</span></span> <span data-ttu-id="cfd18-117">Utilisez le mot clé param pour assigner des paramètres nommés, comme indiqué dans la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="cfd18-117">Use the Param keyword to assign named parameters, as shown in the following syntax:</span></span>

```
{
Param([type]$Parameter1 [,[type]$Parameter2])
<statement list>
}
```

> [!NOTE]
> <span data-ttu-id="cfd18-118">Dans un bloc de script, contrairement à une fonction, vous ne pouvez pas spécifier de paramètres en dehors des accolades.</span><span class="sxs-lookup"><span data-stu-id="cfd18-118">In a script block, unlike a function, you cannot specify parameters outside the braces.</span></span>

<span data-ttu-id="cfd18-119">Comme les fonctions, les blocs de script peuvent inclure les `DynamicParam` `Begin` Mots clés,, `Process` et `End` .</span><span class="sxs-lookup"><span data-stu-id="cfd18-119">Like functions, script blocks can include the `DynamicParam`, `Begin`, `Process`, and `End` keywords.</span></span> <span data-ttu-id="cfd18-120">Pour plus d’informations, consultez [about_Functions](about_Functions.md) et [about_Functions_Advanced](about_Functions_Advanced.md).</span><span class="sxs-lookup"><span data-stu-id="cfd18-120">For more information, see [about_Functions](about_Functions.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

## <a name="using-script-blocks"></a><span data-ttu-id="cfd18-121">Utilisation des blocs de script</span><span class="sxs-lookup"><span data-stu-id="cfd18-121">Using Script Blocks</span></span>

<span data-ttu-id="cfd18-122">Un bloc de script est une instance d’un type Microsoft .NET Framework `System.Management.Automation.ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="cfd18-122">A script block is an instance of a Microsoft .NET Framework type `System.Management.Automation.ScriptBlock`.</span></span> <span data-ttu-id="cfd18-123">Les commandes peuvent avoir des valeurs de paramètre de bloc de script.</span><span class="sxs-lookup"><span data-stu-id="cfd18-123">Commands can have script block parameter values.</span></span> <span data-ttu-id="cfd18-124">Par exemple, l' `Invoke-Command` applet de commande a un `ScriptBlock` paramètre qui prend une valeur de bloc de script, comme illustré dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="cfd18-124">For example, the `Invoke-Command` cmdlet has a `ScriptBlock` parameter that takes a script block value, as shown in this example:</span></span>

```powershell
Invoke-Command -ScriptBlock { Get-Process }
```

```Output
Handles  NPM(K)    PM(K)     WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----     ----- -----   ------     -- -----------
999          28    39100     45020   262    15.88   1844 communicator
721          28    32696     36536   222    20.84   4028 explorer
...
```

<span data-ttu-id="cfd18-125">`Invoke-Command` peut également exécuter des blocs de script qui ont des blocs de paramètres.</span><span class="sxs-lookup"><span data-stu-id="cfd18-125">`Invoke-Command` can also execute script blocks that have parameter blocks.</span></span>
<span data-ttu-id="cfd18-126">Les paramètres sont assignés par position à l’aide du paramètre **argumentlist** .</span><span class="sxs-lookup"><span data-stu-id="cfd18-126">Parameters are assigned by position using the **ArgumentList** parameter.</span></span>

```powershell
Invoke-Command -ScriptBlock { param($p1, $p2)
"p1: $p1"
"p2: $p2"
} -ArgumentList "First", "Second"
```

```Output
p1: First
p2: Second
```

<span data-ttu-id="cfd18-127">Le bloc de script dans l’exemple précédent utilise le `param` mot clé pour créer `$p1` des paramètres et `$p2` .</span><span class="sxs-lookup"><span data-stu-id="cfd18-127">The script block in the preceding example uses the `param` keyword to create a parameters `$p1` and `$p2`.</span></span> <span data-ttu-id="cfd18-128">La chaîne « First » est liée au premier paramètre ( `$p1` ) et « second » est lié à ( `$p2` ).</span><span class="sxs-lookup"><span data-stu-id="cfd18-128">The string "First" is bound to the first parameter (`$p1`) and "Second" is bound to (`$p2`).</span></span>

<span data-ttu-id="cfd18-129">Pour plus d’informations sur le comportement de **argumentlist** , consultez [about_Splatting](about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="cfd18-129">For more information about the behavior of **ArgumentList** , see [about_Splatting](about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="cfd18-130">Vous pouvez utiliser des variables pour stocker et exécuter des blocs de script.</span><span class="sxs-lookup"><span data-stu-id="cfd18-130">You can use variables to store and execute script blocks.</span></span> <span data-ttu-id="cfd18-131">L’exemple ci-dessous stocke un bloc de script dans une variable et le passe à `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="cfd18-131">The example below stores a script block in a variable and passes it to `Invoke-Command`.</span></span>

```powershell
$a = { Get-Service BITS }
Invoke-Command -ScriptBlock $a
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="cfd18-132">L’opérateur d’appel est une autre façon d’exécuter des blocs de script stockés dans une variable.</span><span class="sxs-lookup"><span data-stu-id="cfd18-132">The call operator is another way to execute script blocks stored in a variable.</span></span>
<span data-ttu-id="cfd18-133">Comme `Invoke-Command` , l’opérateur d’appel exécute le bloc de script dans une étendue enfant.</span><span class="sxs-lookup"><span data-stu-id="cfd18-133">Like `Invoke-Command`, the call operator executes the script block in a child scope.</span></span> <span data-ttu-id="cfd18-134">L’opérateur d’appel peut faciliter l’utilisation de paramètres avec vos blocs de script.</span><span class="sxs-lookup"><span data-stu-id="cfd18-134">The call operator can make it easier for you to use parameters with your script blocks.</span></span>

```powershell
$a ={ param($p1, $p2)
"p1: $p1"
"p2: $p2"
}
&$a -p2 "First" -p1 "Second"
```

```Output
p1: Second
p2: First
```

<span data-ttu-id="cfd18-135">Vous pouvez stocker la sortie de vos blocs de script dans une variable à l’aide de l’assignation.</span><span class="sxs-lookup"><span data-stu-id="cfd18-135">You can store the output from your script blocks in a variable using assignment.</span></span>

```
PS>  $a = { 1 + 1}
PS>  $b = &$a
PS>  $b
2
```

```
PS>  $a = { 1 + 1}
PS>  $b = Invoke-Command $a
PS>  $b
2
```

<span data-ttu-id="cfd18-136">Pour plus d’informations sur l’opérateur d’appel, consultez [about_Operators](about_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="cfd18-136">For more information about the call operator, see [about_Operators](about_Operators.md).</span></span>

## <a name="using-delay-bind-script-blocks-with-parameters"></a><span data-ttu-id="cfd18-137">Utilisation de blocs de script de liaison différée avec des paramètres</span><span class="sxs-lookup"><span data-stu-id="cfd18-137">Using delay-bind script blocks with parameters</span></span>

<span data-ttu-id="cfd18-138">Un paramètre typé qui accepte l’entrée de pipeline ( `by Value` ) ou ( `by PropertyName` ) permet d’utiliser des blocs de script de **liaison différée** sur le paramètre.</span><span class="sxs-lookup"><span data-stu-id="cfd18-138">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of **delay-bind** script blocks on the parameter.</span></span>
<span data-ttu-id="cfd18-139">Dans le bloc de script de **liaison différée** , vous pouvez référencer l’objet dirigé dans à l’aide de la variable de pipeline `$_` .</span><span class="sxs-lookup"><span data-stu-id="cfd18-139">Within the **delay-bind** script block, you can reference the piped in object using the pipeline variable `$_`.</span></span>

```powershell
# Renames config.log to old_config.log
dir config.log | Rename-Item -NewName {"old_" + $_.Name}
```

<span data-ttu-id="cfd18-140">Dans les cmdlets plus complexes, les blocs de script de liaison différée permettent la réutilisation d’un objet dirigé dans pour remplir d’autres paramètres.</span><span class="sxs-lookup"><span data-stu-id="cfd18-140">In more complex cmdlets, delay-bind script blocks allow the reuse of one piped in object to populate other parameters.</span></span>

<span data-ttu-id="cfd18-141">Remarques sur les blocs de script de **liaison différée** comme paramètres :</span><span class="sxs-lookup"><span data-stu-id="cfd18-141">Notes on **delay-bind** script blocks as parameters:</span></span>

- <span data-ttu-id="cfd18-142">Vous devez spécifier explicitement les noms de paramètres que vous utilisez avec des blocs de script de **liaison différée** .</span><span class="sxs-lookup"><span data-stu-id="cfd18-142">You must explicitly specify any parameter names you use with **delay-bind** script blocks.</span></span>
- <span data-ttu-id="cfd18-143">Le paramètre ne doit pas être non typé et le type du paramètre ne peut pas être `[scriptblock]` ou `[object]` .</span><span class="sxs-lookup"><span data-stu-id="cfd18-143">The parameter must not be untyped, and the parameter's type cannot be `[scriptblock]` or `[object]`.</span></span>
- <span data-ttu-id="cfd18-144">Vous recevez une erreur si vous utilisez un bloc de script **de liaison différée** sans fournir d’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="cfd18-144">You receive an error if you use a **delay-bind** script block without providing pipeline input.</span></span>

  ```powershell
  Rename-Item -NewName {$_.Name + ".old"}
  ```

  ```Output
  Rename-Item : Cannot evaluate parameter 'NewName' because its argument is
  specified as a script block and there is no input. A script block cannot
  be evaluated without input.
  At line:1 char:23
  +  Rename-Item -NewName {$_.Name + ".old"}
  +                       ~~~~~~~~~~~~~~~~~~
      + CategoryInfo          : MetadataError: (:) [Rename-Item],
        ParameterBindingException
      + FullyQualifiedErrorId : ScriptBlockArgumentNoInput,
        Microsoft.PowerShell.Commands.RenameItemCommand
  ```

## <a name="see-also"></a><span data-ttu-id="cfd18-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfd18-145">See Also</span></span>

[<span data-ttu-id="cfd18-146">about_Functions</span><span class="sxs-lookup"><span data-stu-id="cfd18-146">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="cfd18-147">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="cfd18-147">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="cfd18-148">about_Operators</span><span class="sxs-lookup"><span data-stu-id="cfd18-148">about_Operators</span></span>](about_Operators.md)
