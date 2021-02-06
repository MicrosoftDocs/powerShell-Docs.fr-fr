---
description: Définit ce qu’est un bloc de script et explique comment utiliser des blocs de script dans le langage de programmation PowerShell.
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_blocks?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Blocks
ms.openlocfilehash: 1ba5e92bedc03a2d61d528715ab13c5d96eb3075
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601892"
---
# <a name="about-script-blocks"></a><span data-ttu-id="6ca04-103">À propos des blocs de script</span><span class="sxs-lookup"><span data-stu-id="6ca04-103">About Script Blocks</span></span>

## <a name="short-description"></a><span data-ttu-id="6ca04-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="6ca04-104">Short description</span></span>

<span data-ttu-id="6ca04-105">Définit ce qu’est un bloc de script et explique comment utiliser des blocs de script dans le langage de programmation PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6ca04-105">Defines what a script block is and explains how to use script blocks in the PowerShell programming language.</span></span>

## <a name="long-description"></a><span data-ttu-id="6ca04-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="6ca04-106">Long description</span></span>

<span data-ttu-id="6ca04-107">Dans le langage de programmation PowerShell, un bloc de script est une collection d’instructions ou d’expressions qui peuvent être utilisées comme une seule unité.</span><span class="sxs-lookup"><span data-stu-id="6ca04-107">In the PowerShell programming language, a script block is a collection of statements or expressions that can be used as a single unit.</span></span>
<span data-ttu-id="6ca04-108">Un bloc de script peut accepter des arguments et retourner des valeurs.</span><span class="sxs-lookup"><span data-stu-id="6ca04-108">A script block can accept arguments and return values.</span></span>

<span data-ttu-id="6ca04-109">Syntaxiquement, un bloc de script est une liste d’instructions entre accolades, comme illustré dans la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="6ca04-109">Syntactically, a script block is a statement list in braces, as shown in the following syntax:</span></span>

```
{<statement list>}
```

<span data-ttu-id="6ca04-110">Un bloc de script retourne la sortie de toutes les commandes dans le bloc de script, sous la forme d’un objet unique ou d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="6ca04-110">A script block returns the output of all the commands in the script block, either as a single object or as an array.</span></span>

<span data-ttu-id="6ca04-111">Vous pouvez également spécifier une valeur de retour à l’aide du `return` mot clé.</span><span class="sxs-lookup"><span data-stu-id="6ca04-111">You can also specify a return value using the `return` keyword.</span></span> <span data-ttu-id="6ca04-112">Le `return` mot clé n’affecte pas ou ne supprime pas la sortie retournée par votre bloc de script.</span><span class="sxs-lookup"><span data-stu-id="6ca04-112">The `return` keyword does not affect or suppress other output returned from your script block.</span></span> <span data-ttu-id="6ca04-113">Toutefois, le `return` mot clé quitte le bloc de script à cette ligne.</span><span class="sxs-lookup"><span data-stu-id="6ca04-113">However, the `return` keyword exits the script block at that line.</span></span> <span data-ttu-id="6ca04-114">Pour plus d’informations, consultez [about_Return](about_Return.md).</span><span class="sxs-lookup"><span data-stu-id="6ca04-114">For more information, see [about_Return](about_Return.md).</span></span>

<span data-ttu-id="6ca04-115">Comme les fonctions, un bloc de script peut inclure des paramètres.</span><span class="sxs-lookup"><span data-stu-id="6ca04-115">Like functions, a script block can include parameters.</span></span> <span data-ttu-id="6ca04-116">Utilisez le mot clé param pour assigner des paramètres nommés, comme indiqué dans la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="6ca04-116">Use the Param keyword to assign named parameters, as shown in the following syntax:</span></span>

```
{
Param([type]$Parameter1 [,[type]$Parameter2])
<statement list>
}
```

> [!NOTE]
> <span data-ttu-id="6ca04-117">Dans un bloc de script, contrairement à une fonction, vous ne pouvez pas spécifier de paramètres en dehors des accolades.</span><span class="sxs-lookup"><span data-stu-id="6ca04-117">In a script block, unlike a function, you cannot specify parameters outside the braces.</span></span>

<span data-ttu-id="6ca04-118">Comme les fonctions, les blocs de script peuvent inclure les `DynamicParam` `Begin` Mots clés,, `Process` et `End` .</span><span class="sxs-lookup"><span data-stu-id="6ca04-118">Like functions, script blocks can include the `DynamicParam`, `Begin`, `Process`, and `End` keywords.</span></span> <span data-ttu-id="6ca04-119">Pour plus d’informations, consultez [about_Functions](about_Functions.md) et [about_Functions_Advanced](about_Functions_Advanced.md).</span><span class="sxs-lookup"><span data-stu-id="6ca04-119">For more information, see [about_Functions](about_Functions.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

## <a name="using-script-blocks"></a><span data-ttu-id="6ca04-120">Utilisation des blocs de script</span><span class="sxs-lookup"><span data-stu-id="6ca04-120">Using Script Blocks</span></span>

<span data-ttu-id="6ca04-121">Un bloc de script est une instance d’un type Microsoft .NET Framework `System.Management.Automation.ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="6ca04-121">A script block is an instance of a Microsoft .NET Framework type `System.Management.Automation.ScriptBlock`.</span></span> <span data-ttu-id="6ca04-122">Les commandes peuvent avoir des valeurs de paramètre de bloc de script.</span><span class="sxs-lookup"><span data-stu-id="6ca04-122">Commands can have script block parameter values.</span></span> <span data-ttu-id="6ca04-123">Par exemple, l' `Invoke-Command` applet de commande a un `ScriptBlock` paramètre qui prend une valeur de bloc de script, comme illustré dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="6ca04-123">For example, the `Invoke-Command` cmdlet has a `ScriptBlock` parameter that takes a script block value, as shown in this example:</span></span>

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

<span data-ttu-id="6ca04-124">`Invoke-Command` peut également exécuter des blocs de script qui ont des blocs de paramètres.</span><span class="sxs-lookup"><span data-stu-id="6ca04-124">`Invoke-Command` can also execute script blocks that have parameter blocks.</span></span>
<span data-ttu-id="6ca04-125">Les paramètres sont assignés par position à l’aide du paramètre **argumentlist** .</span><span class="sxs-lookup"><span data-stu-id="6ca04-125">Parameters are assigned by position using the **ArgumentList** parameter.</span></span>

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

<span data-ttu-id="6ca04-126">Le bloc de script dans l’exemple précédent utilise le `param` mot clé pour créer `$p1` des paramètres et `$p2` .</span><span class="sxs-lookup"><span data-stu-id="6ca04-126">The script block in the preceding example uses the `param` keyword to create a parameters `$p1` and `$p2`.</span></span> <span data-ttu-id="6ca04-127">La chaîne « First » est liée au premier paramètre ( `$p1` ) et « second » est lié à ( `$p2` ).</span><span class="sxs-lookup"><span data-stu-id="6ca04-127">The string "First" is bound to the first parameter (`$p1`) and "Second" is bound to (`$p2`).</span></span>

<span data-ttu-id="6ca04-128">Pour plus d’informations sur le comportement de **argumentlist**, consultez [about_Splatting](about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="6ca04-128">For more information about the behavior of **ArgumentList**, see [about_Splatting](about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="6ca04-129">Vous pouvez utiliser des variables pour stocker et exécuter des blocs de script.</span><span class="sxs-lookup"><span data-stu-id="6ca04-129">You can use variables to store and execute script blocks.</span></span> <span data-ttu-id="6ca04-130">L’exemple ci-dessous stocke un bloc de script dans une variable et le passe à `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="6ca04-130">The example below stores a script block in a variable and passes it to `Invoke-Command`.</span></span>

```powershell
$a = { Get-Service BITS }
Invoke-Command -ScriptBlock $a
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="6ca04-131">L’opérateur d’appel est une autre façon d’exécuter des blocs de script stockés dans une variable.</span><span class="sxs-lookup"><span data-stu-id="6ca04-131">The call operator is another way to execute script blocks stored in a variable.</span></span>
<span data-ttu-id="6ca04-132">Comme `Invoke-Command` , l’opérateur d’appel exécute le bloc de script dans une étendue enfant.</span><span class="sxs-lookup"><span data-stu-id="6ca04-132">Like `Invoke-Command`, the call operator executes the script block in a child scope.</span></span> <span data-ttu-id="6ca04-133">L’opérateur d’appel peut faciliter l’utilisation de paramètres avec vos blocs de script.</span><span class="sxs-lookup"><span data-stu-id="6ca04-133">The call operator can make it easier for you to use parameters with your script blocks.</span></span>

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

<span data-ttu-id="6ca04-134">Vous pouvez stocker la sortie de vos blocs de script dans une variable à l’aide de l’assignation.</span><span class="sxs-lookup"><span data-stu-id="6ca04-134">You can store the output from your script blocks in a variable using assignment.</span></span>

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

<span data-ttu-id="6ca04-135">Pour plus d’informations sur l’opérateur d’appel, consultez [about_Operators](about_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="6ca04-135">For more information about the call operator, see [about_Operators](about_Operators.md).</span></span>

## <a name="using-delay-bind-script-blocks-with-parameters"></a><span data-ttu-id="6ca04-136">Utilisation de blocs de script de liaison différée avec des paramètres</span><span class="sxs-lookup"><span data-stu-id="6ca04-136">Using delay-bind script blocks with parameters</span></span>

<span data-ttu-id="6ca04-137">Un paramètre typé qui accepte l’entrée de pipeline ( `by Value` ) ou ( `by PropertyName` ) permet d’utiliser des blocs de script de **liaison différée** sur le paramètre.</span><span class="sxs-lookup"><span data-stu-id="6ca04-137">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of **delay-bind** script blocks on the parameter.</span></span>
<span data-ttu-id="6ca04-138">Dans le bloc de script de **liaison différée** , vous pouvez référencer l’objet dirigé dans à l’aide de la variable de pipeline `$_` .</span><span class="sxs-lookup"><span data-stu-id="6ca04-138">Within the **delay-bind** script block, you can reference the piped in object using the pipeline variable `$_`.</span></span>

```powershell
# Renames config.log to old_config.log
dir config.log | Rename-Item -NewName {"old_" + $_.Name}
```

<span data-ttu-id="6ca04-139">Dans les cmdlets plus complexes, les blocs de script de liaison différée permettent la réutilisation d’un objet dirigé dans pour remplir d’autres paramètres.</span><span class="sxs-lookup"><span data-stu-id="6ca04-139">In more complex cmdlets, delay-bind script blocks allow the reuse of one piped in object to populate other parameters.</span></span>

<span data-ttu-id="6ca04-140">Remarques sur les blocs de script de **liaison différée** comme paramètres :</span><span class="sxs-lookup"><span data-stu-id="6ca04-140">Notes on **delay-bind** script blocks as parameters:</span></span>

- <span data-ttu-id="6ca04-141">Vous devez spécifier explicitement les noms de paramètres que vous utilisez avec des blocs de script de **liaison différée** .</span><span class="sxs-lookup"><span data-stu-id="6ca04-141">You must explicitly specify any parameter names you use with **delay-bind** script blocks.</span></span>
- <span data-ttu-id="6ca04-142">Le paramètre ne doit pas être non typé et le type du paramètre ne peut pas être `[scriptblock]` ou `[object]` .</span><span class="sxs-lookup"><span data-stu-id="6ca04-142">The parameter must not be untyped, and the parameter's type cannot be `[scriptblock]` or `[object]`.</span></span>
- <span data-ttu-id="6ca04-143">Vous recevez une erreur si vous utilisez un bloc de script **de liaison différée** sans fournir d’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="6ca04-143">You receive an error if you use a **delay-bind** script block without providing pipeline input.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6ca04-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ca04-144">See Also</span></span>

[<span data-ttu-id="6ca04-145">about_Functions</span><span class="sxs-lookup"><span data-stu-id="6ca04-145">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="6ca04-146">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="6ca04-146">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="6ca04-147">about_Operators</span><span class="sxs-lookup"><span data-stu-id="6ca04-147">about_Operators</span></span>](about_Operators.md)

