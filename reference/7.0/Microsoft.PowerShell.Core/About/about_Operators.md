---
description: Décrit les opérateurs pris en charge par PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/28/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: d442a64be77934cef4636e905c098d9630451b8f
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "93208938"
---
# <a name="about-operators"></a><span data-ttu-id="dc462-104">À propos des opérateurs</span><span class="sxs-lookup"><span data-stu-id="dc462-104">About Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="dc462-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="dc462-105">Short description</span></span>
<span data-ttu-id="dc462-106">Décrit les opérateurs pris en charge par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc462-106">Describes the operators that are supported by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="dc462-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="dc462-107">Long description</span></span>

<span data-ttu-id="dc462-108">Un opérateur est un élément de langage que vous pouvez utiliser dans une commande ou une expression.</span><span class="sxs-lookup"><span data-stu-id="dc462-108">An operator is a language element that you can use in a command or expression.</span></span>
<span data-ttu-id="dc462-109">PowerShell prend en charge plusieurs types d’opérateurs pour vous aider à manipuler des valeurs.</span><span class="sxs-lookup"><span data-stu-id="dc462-109">PowerShell supports several types of operators to help you manipulate values.</span></span>

### <a name="arithmetic-operators"></a><span data-ttu-id="dc462-110">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="dc462-110">Arithmetic Operators</span></span>

<span data-ttu-id="dc462-111">Utilisez les opérateurs arithmétiques ( `+` , `-` ,, `*` `/` , `%` ) pour calculer des valeurs dans une commande ou une expression.</span><span class="sxs-lookup"><span data-stu-id="dc462-111">Use arithmetic operators (`+`, `-`, `*`, `/`, `%`) to calculate values in a command or expression.</span></span> <span data-ttu-id="dc462-112">À l’aide de ces opérateurs, vous pouvez ajouter, soustraire, multiplier ou diviser des valeurs, et calculer le reste (modulo) d’une opération de division.</span><span class="sxs-lookup"><span data-stu-id="dc462-112">With these operators, you can add, subtract, multiply, or divide values, and calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="dc462-113">L’opérateur d’addition concatène les éléments.</span><span class="sxs-lookup"><span data-stu-id="dc462-113">The addition operator concatenates elements.</span></span> <span data-ttu-id="dc462-114">L’opérateur de multiplication retourne le nombre spécifié de copies de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="dc462-114">The multiplication operator returns the specified number of copies of each element.</span></span> <span data-ttu-id="dc462-115">Vous pouvez utiliser des opérateurs arithmétiques sur tout type .net qui les implémente, tels que les tableaux suivants : `Int` ,,,, `String` `DateTime` `Hashtable` et.</span><span class="sxs-lookup"><span data-stu-id="dc462-115">You can use arithmetic operators on any .NET type that implements them, such as: `Int`, `String`, `DateTime`, `Hashtable`, and Arrays.</span></span>

<span data-ttu-id="dc462-116">Les opérateurs au niveau du bit ( `-band` , `-bor` ,, `-bxor` `-bnot` , `-shl` , `-shr` ) manipulent les modèles binaires dans les valeurs.</span><span class="sxs-lookup"><span data-stu-id="dc462-116">Bitwise operators (`-band`, `-bor`, `-bxor`, `-bnot`, `-shl`, `-shr`) manipulate the bit patterns in values.</span></span>

<span data-ttu-id="dc462-117">Pour plus d’informations, consultez [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc462-117">For more information, see [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span></span>

### <a name="assignment-operators"></a><span data-ttu-id="dc462-118">Opérateurs d'assignation</span><span class="sxs-lookup"><span data-stu-id="dc462-118">Assignment Operators</span></span>

<span data-ttu-id="dc462-119">Utilisez les opérateurs d’assignation ( `=` , `+=` , `-=` , `*=` , `/=` , `%=` ) pour assigner, modifier ou ajouter des valeurs à des variables.</span><span class="sxs-lookup"><span data-stu-id="dc462-119">Use assignment operators (`=`, `+=`, `-=`, `*=`, `/=`, `%=`) to assign, change, or append values to variables.</span></span> <span data-ttu-id="dc462-120">Vous pouvez combiner des opérateurs arithmétiques avec l’assignation pour assigner le résultat de l’opération arithmétique à une variable.</span><span class="sxs-lookup"><span data-stu-id="dc462-120">You can combine arithmetic operators with assignment to assign the result of the arithmetic operation to a variable.</span></span>

<span data-ttu-id="dc462-121">Pour plus d’informations, consultez [about_Assignment_Operators](about_Assignment_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc462-121">For more information, see [about_Assignment_Operators](about_Assignment_Operators.md).</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="dc462-122">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="dc462-122">Comparison Operators</span></span>

<span data-ttu-id="dc462-123">Utilisez des opérateurs de comparaison ( `-eq` , `-ne` , `-gt` , `-lt` , `-le` , `-ge` ) pour comparer des valeurs et des conditions de test.</span><span class="sxs-lookup"><span data-stu-id="dc462-123">Use comparison operators (`-eq`, `-ne`, `-gt`, `-lt`, `-le`, `-ge`) to compare values and test conditions.</span></span> <span data-ttu-id="dc462-124">Par exemple, vous pouvez comparer deux valeurs de chaîne pour déterminer si elles sont égales.</span><span class="sxs-lookup"><span data-stu-id="dc462-124">For example, you can compare two string values to determine whether they are equal.</span></span>

<span data-ttu-id="dc462-125">Les opérateurs de comparaison incluent également des opérateurs qui recherchent ou remplacent des modèles dans du texte.</span><span class="sxs-lookup"><span data-stu-id="dc462-125">The comparison operators also include operators that find or replace patterns in text.</span></span> <span data-ttu-id="dc462-126">Les `-match` opérateurs (, `-notmatch` , `-replace` ) utilisent des expressions régulières, et ( `-like` , `-notlike` ) utilisent des caractères génériques `*` .</span><span class="sxs-lookup"><span data-stu-id="dc462-126">The (`-match`, `-notmatch`, `-replace`) operators use regular expressions, and (`-like`, `-notlike`) use wildcards `*`.</span></span>

<span data-ttu-id="dc462-127">Les opérateurs de comparaison de relation contenant-contenu déterminent si une valeur de test apparaît dans un jeu de référence ( `-in` , `-notin` , `-contains` , `-notcontains` ).</span><span class="sxs-lookup"><span data-stu-id="dc462-127">Containment comparison operators determine whether a test value appears in a reference set (`-in`, `-notin`, `-contains`, `-notcontains`).</span></span>

<span data-ttu-id="dc462-128">Les opérateurs de comparaison `-is` de type (, `-isnot` ) déterminent si un objet est d’un type donné.</span><span class="sxs-lookup"><span data-stu-id="dc462-128">Type comparison operators (`-is`, `-isnot`) determine whether an object is of a given type.</span></span>

<span data-ttu-id="dc462-129">Pour plus d’informations, consultez [about_Comparison_Operators](about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc462-129">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span>

### <a name="logical-operators"></a><span data-ttu-id="dc462-130">Opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="dc462-130">Logical Operators</span></span>

<span data-ttu-id="dc462-131">Utilisez des opérateurs logiques ( `-and` , `-or` ,, `-xor` `-not` , `!` ) pour connecter des instructions conditionnelles à un seul conditionnel complexe.</span><span class="sxs-lookup"><span data-stu-id="dc462-131">Use logical operators (`-and`, `-or`, `-xor`, `-not`, `!`) to connect conditional statements into a single complex conditional.</span></span> <span data-ttu-id="dc462-132">Par exemple, vous pouvez utiliser un `-and` opérateur logique pour créer un filtre d’objets avec deux conditions différentes.</span><span class="sxs-lookup"><span data-stu-id="dc462-132">For example, you can use a logical `-and` operator to create an object filter with two different conditions.</span></span>

<span data-ttu-id="dc462-133">Pour plus d’informations, consultez [about_Logical_Operators](about_logical_operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc462-133">For more information, see [about_Logical_Operators](about_logical_operators.md).</span></span>

### <a name="redirection-operators"></a><span data-ttu-id="dc462-134">Opérateurs de redirection</span><span class="sxs-lookup"><span data-stu-id="dc462-134">Redirection Operators</span></span>

<span data-ttu-id="dc462-135">Utilisez les opérateurs de redirection ( `>` , `>>` ,, `2>` `2>>` et `2>&1` ) pour envoyer la sortie d’une commande ou d’une expression à un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="dc462-135">Use redirection operators (`>`, `>>`, `2>`, `2>>`, and `2>&1`) to send the output of a command or expression to a text file.</span></span> <span data-ttu-id="dc462-136">Les opérateurs de redirection fonctionnent comme l' `Out-File` applet de commande (sans paramètres), mais ils vous permettent également de rediriger la sortie d’erreur vers les fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="dc462-136">The redirection operators work like the `Out-File` cmdlet (without parameters) but they also let you redirect error output to specified files.</span></span> <span data-ttu-id="dc462-137">Vous pouvez également utiliser l' `Tee-Object` applet de commande pour rediriger la sortie.</span><span class="sxs-lookup"><span data-stu-id="dc462-137">You can also use the `Tee-Object` cmdlet to redirect output.</span></span>

<span data-ttu-id="dc462-138">Pour plus d’informations, consultez [about_Redirection](about_Redirection.md)</span><span class="sxs-lookup"><span data-stu-id="dc462-138">For more information, see [about_Redirection](about_Redirection.md)</span></span>

### <a name="split-and-join-operators"></a><span data-ttu-id="dc462-139">Opérateurs Split et Join</span><span class="sxs-lookup"><span data-stu-id="dc462-139">Split and Join Operators</span></span>

<span data-ttu-id="dc462-140">Les `-split` `-join` opérateurs et divisent et combinent des sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="dc462-140">The `-split` and `-join` operators divide and combine substrings.</span></span> <span data-ttu-id="dc462-141">L' `-split` opérateur fractionne une chaîne en sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="dc462-141">The `-split` operator splits a string into substrings.</span></span> <span data-ttu-id="dc462-142">L' `-join` opérateur concatène plusieurs chaînes en une seule chaîne.</span><span class="sxs-lookup"><span data-stu-id="dc462-142">The `-join` operator concatenates multiple strings into a single string.</span></span>

<span data-ttu-id="dc462-143">Pour plus d’informations, consultez [about_Split](about_Split.md) et [about_Join](about_Join.md).</span><span class="sxs-lookup"><span data-stu-id="dc462-143">For more information, see [about_Split](about_Split.md) and [about_Join](about_Join.md).</span></span>

### <a name="type-operators"></a><span data-ttu-id="dc462-144">Opérateurs de type</span><span class="sxs-lookup"><span data-stu-id="dc462-144">Type Operators</span></span>

<span data-ttu-id="dc462-145">Utilisez les opérateurs de type ( `-is` , `-isnot` , `-as` ) pour rechercher ou modifier le type de .NET Framework d’un objet.</span><span class="sxs-lookup"><span data-stu-id="dc462-145">Use the type operators (`-is`, `-isnot`, `-as`) to find or change the .NET Framework type of an object.</span></span>

<span data-ttu-id="dc462-146">Pour plus d’informations, consultez [about_Type_Operators](about_Type_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc462-146">For more information, see [about_Type_Operators](about_Type_Operators.md).</span></span>

### <a name="unary-operators"></a><span data-ttu-id="dc462-147">Opérateurs unaires</span><span class="sxs-lookup"><span data-stu-id="dc462-147">Unary Operators</span></span>

<span data-ttu-id="dc462-148">Utilisez des opérateurs unaires pour incrémenter ou décrémenter des variables ou des propriétés d’objet et pour définir des entiers avec des nombres positifs ou négatifs.</span><span class="sxs-lookup"><span data-stu-id="dc462-148">Use unary operators to increment or decrement variables or object properties and to set integers to positive or negative numbers.</span></span> <span data-ttu-id="dc462-149">Par exemple, pour incrémenter la variable `$a` de `9` à `10` , vous tapez `$a++` .</span><span class="sxs-lookup"><span data-stu-id="dc462-149">For example, to increment the variable `$a` from `9` to `10`, you type `$a++`.</span></span>

### <a name="special-operators"></a><span data-ttu-id="dc462-150">Opérateurs spéciaux</span><span class="sxs-lookup"><span data-stu-id="dc462-150">Special Operators</span></span>

<span data-ttu-id="dc462-151">Les opérateurs spéciaux ont des cas d’usage spécifiques qui ne rentrent dans aucun autre groupe d’opérateurs.</span><span class="sxs-lookup"><span data-stu-id="dc462-151">Special operators have specific use-cases that do not fit into any other operator group.</span></span> <span data-ttu-id="dc462-152">Par exemple, les opérateurs spéciaux vous permettent d’exécuter des commandes, de modifier le type de données d’une valeur ou de récupérer des éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="dc462-152">For example, special operators allow you to run commands, change a value's data type, or retrieve elements from an array.</span></span>

#### <a name="grouping-operator--"></a><span data-ttu-id="dc462-153">Opérateur de regroupement `( )`</span><span class="sxs-lookup"><span data-stu-id="dc462-153">Grouping operator `( )`</span></span>

<span data-ttu-id="dc462-154">Comme dans d’autres langages, `(...)` sert à remplacer la priorité des opérateurs dans les expressions.</span><span class="sxs-lookup"><span data-stu-id="dc462-154">As in other languages, `(...)` serves to override operator precedence in expressions.</span></span> <span data-ttu-id="dc462-155">Par exemple : `(1 + 2) / 3`</span><span class="sxs-lookup"><span data-stu-id="dc462-155">For example: `(1 + 2) / 3`</span></span>

<span data-ttu-id="dc462-156">Toutefois, dans PowerShell, il existe des comportements supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="dc462-156">However, in PowerShell, there are additional behaviors.</span></span>

- <span data-ttu-id="dc462-157">`(...)` vous permet de laisser la sortie d’une _commande_ participer à une expression.</span><span class="sxs-lookup"><span data-stu-id="dc462-157">`(...)` allows you to let output from a _command_ participate in an expression.</span></span> <span data-ttu-id="dc462-158">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="dc462-158">For example:</span></span>

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- <span data-ttu-id="dc462-159">Lorsqu’il est utilisé comme premier segment d’un pipeline, l’encapsulation d’une commande ou d’une expression entre parenthèses provoque invariablement l' _énumération_ du résultat de l’expression.</span><span class="sxs-lookup"><span data-stu-id="dc462-159">When used as the first segment of a pipeline, wrapping a command or expression in parentheses invariably causes _enumeration_ of the expression result.</span></span> <span data-ttu-id="dc462-160">Si les parenthèses encapsulent une _commande_ , elles sont exécutées jusqu’à la fin avec toute la sortie _collectée en mémoire_ avant que les résultats ne soient envoyés via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="dc462-160">If the parentheses wrap a _command_ , it is run to completion with all output _collected in memory_ before the results are sent through the pipeline.</span></span>

#### <a name="subexpression-operator--"></a><span data-ttu-id="dc462-161">Opérateur de sous-expression `$( )`</span><span class="sxs-lookup"><span data-stu-id="dc462-161">Subexpression operator `$( )`</span></span>

<span data-ttu-id="dc462-162">Retourne le résultat d’une ou plusieurs instructions.</span><span class="sxs-lookup"><span data-stu-id="dc462-162">Returns the result of one or more statements.</span></span> <span data-ttu-id="dc462-163">Pour un résultat unique, retourne un scalaire.</span><span class="sxs-lookup"><span data-stu-id="dc462-163">For a single result, returns a scalar.</span></span> <span data-ttu-id="dc462-164">Pour plusieurs résultats, retourne un tableau.</span><span class="sxs-lookup"><span data-stu-id="dc462-164">For multiple results, returns an array.</span></span> <span data-ttu-id="dc462-165">Utilisez cette valeur lorsque vous souhaitez utiliser une expression dans une autre expression.</span><span class="sxs-lookup"><span data-stu-id="dc462-165">Use this when you want to use an expression within another expression.</span></span> <span data-ttu-id="dc462-166">Par exemple, pour incorporer les résultats de la commande dans une expression de chaîne.</span><span class="sxs-lookup"><span data-stu-id="dc462-166">For example, to embed the results of command in a string expression.</span></span>

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a><span data-ttu-id="dc462-167">Opérateur de sous-expression de tableau `@( )`</span><span class="sxs-lookup"><span data-stu-id="dc462-167">Array subexpression operator `@( )`</span></span>

<span data-ttu-id="dc462-168">Retourne le résultat d’une ou plusieurs instructions sous la forme d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="dc462-168">Returns the result of one or more statements as an array.</span></span> <span data-ttu-id="dc462-169">S’il n’y a qu’un seul élément, le tableau ne possède qu’un seul membre.</span><span class="sxs-lookup"><span data-stu-id="dc462-169">If there is only one item, the array has only one member.</span></span>

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="call-operator-"></a><span data-ttu-id="dc462-170">Opérateur d’appel `&`</span><span class="sxs-lookup"><span data-stu-id="dc462-170">Call operator `&`</span></span>

<span data-ttu-id="dc462-171">Exécute une commande, un script ou un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="dc462-171">Runs a command, script, or script block.</span></span> <span data-ttu-id="dc462-172">L’opérateur d’appel, également appelé « opérateur d’appel », vous permet d’exécuter des commandes qui sont stockées dans des variables et représentées par des chaînes ou des blocs de script.</span><span class="sxs-lookup"><span data-stu-id="dc462-172">The call operator, also known as the "invocation operator", lets you run commands that are stored in variables and represented by strings or script blocks.</span></span> <span data-ttu-id="dc462-173">L’opérateur d’appel s’exécute dans une portée enfant.</span><span class="sxs-lookup"><span data-stu-id="dc462-173">The call operator executes in a child scope.</span></span> <span data-ttu-id="dc462-174">Pour plus d’informations sur les étendues, consultez [about_Scopes](about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="dc462-174">For more about scopes, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="dc462-175">Cet exemple stocke une commande dans une chaîne et l’exécute à l’aide de l’opérateur d’appel.</span><span class="sxs-lookup"><span data-stu-id="dc462-175">This example stores a command in a string and executes it using the call operator.</span></span>

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

<span data-ttu-id="dc462-176">L’opérateur d’appel n’analyse pas les chaînes.</span><span class="sxs-lookup"><span data-stu-id="dc462-176">The call operator does not parse strings.</span></span> <span data-ttu-id="dc462-177">Cela signifie que vous ne pouvez pas utiliser de paramètres de commande dans une chaîne lorsque vous utilisez l’opérateur d’appel.</span><span class="sxs-lookup"><span data-stu-id="dc462-177">This means that you cannot use command parameters within a string when you use the call operator.</span></span>

```
PS> $c = "Get-Service -Name Spooler"
PS> $c
Get-Service -Name Spooler
PS> & $c
& : The term 'Get-Service -Name Spooler' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of
the name, or if a path was included, verify that the path is correct and
try again.
```

<span data-ttu-id="dc462-178">L’applet de commande [Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) peut exécuter du code qui provoque des erreurs d’analyse lors de l’utilisation de l’opérateur d’appel.</span><span class="sxs-lookup"><span data-stu-id="dc462-178">The [Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) cmdlet can execute code that causes parsing errors when using the call operator.</span></span>

```
PS> & "1+1"
& : The term '1+1' is not recognized as the name of a cmdlet, function, script
file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:2
+ & "1+1"
+  ~~~~~
    + CategoryInfo          : ObjectNotFound: (1+1:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
PS> Invoke-Expression "1+1"
2
```

<span data-ttu-id="dc462-179">Vous pouvez utiliser l’opérateur d’appel pour exécuter des scripts à l’aide de leurs noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="dc462-179">You can use the call operator to execute scripts using their filenames.</span></span> <span data-ttu-id="dc462-180">L’exemple ci-dessous montre un nom de fichier de script qui contient des espaces.</span><span class="sxs-lookup"><span data-stu-id="dc462-180">The example below shows a script filename that contains spaces.</span></span> <span data-ttu-id="dc462-181">Lorsque vous essayez d’exécuter le script, PowerShell affiche à la place le contenu de la chaîne entre guillemets contenant le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="dc462-181">When you try to execute the script, PowerShell instead displays the contents of the quoted string containing the filename.</span></span> <span data-ttu-id="dc462-182">L’opérateur d’appel vous permet d’exécuter le contenu de la chaîne contenant le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="dc462-182">The call operator allows you to execute the contents of the string containing the filename.</span></span>

```
PS C:\Scripts> Get-ChildItem

    Directory: C:\Scripts


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/28/2018   1:36 PM             58 script name with spaces.ps1

PS C:\Scripts> ".\script name with spaces.ps1"
.\script name with spaces.ps1
PS C:\Scripts> & ".\script name with spaces.ps1"
Hello World!
```

<span data-ttu-id="dc462-183">Pour plus d’informations sur les blocs de script, consultez [about_Script_Blocks](about_Script_Blocks.md).</span><span class="sxs-lookup"><span data-stu-id="dc462-183">For more about script blocks, see [about_Script_Blocks](about_Script_Blocks.md).</span></span>

#### <a name="background-operator-"></a><span data-ttu-id="dc462-184">Opérateur d’arrière-plan `&`</span><span class="sxs-lookup"><span data-stu-id="dc462-184">Background operator `&`</span></span>

<span data-ttu-id="dc462-185">Exécute le pipeline avant de l’exécuter en arrière-plan, dans un travail PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc462-185">Runs the pipeline before it in the background, in a PowerShell job.</span></span> <span data-ttu-id="dc462-186">Cet opérateur agit de la même façon que l’opérateur de contrôle UNIX perluète ( `&` ), qui exécute la commande avant de l’exécuter de manière asynchrone dans subshell en tant que tâche.</span><span class="sxs-lookup"><span data-stu-id="dc462-186">This operator acts similarly to the UNIX control operator ampersand (`&`), which runs the command before it asynchronously in subshell as a job.</span></span>

<span data-ttu-id="dc462-187">Cet opérateur est fonctionnellement équivalent à `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="dc462-187">This operator is functionally equivalent to `Start-Job`.</span></span> <span data-ttu-id="dc462-188">Par défaut, l’opérateur d’arrière-plan démarre les tâches dans le répertoire de travail actuel de l’appelant qui a démarré les tâches parallèles.</span><span class="sxs-lookup"><span data-stu-id="dc462-188">By default, the background operator starts the jobs in the current working directory of the caller that started the parallel tasks.</span></span> <span data-ttu-id="dc462-189">L’exemple suivant illustre l’utilisation de base de l’opérateur de travail en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="dc462-189">The following example demonstrates basic usage of the background job operator.</span></span>

```powershell
Get-Process -Name pwsh &
```

<span data-ttu-id="dc462-190">Cette commande est fonctionnellement équivalente à l’utilisation suivante de `Start-Job` :</span><span class="sxs-lookup"><span data-stu-id="dc462-190">That command is functionally equivalent to the following usage of `Start-Job`:</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process -Name pwsh}
```

<span data-ttu-id="dc462-191">Tout comme `Start-Job` , l' `&` opérateur d’arrière-plan retourne un `Job` objet.</span><span class="sxs-lookup"><span data-stu-id="dc462-191">Just like `Start-Job`, the `&` background operator returns a `Job` object.</span></span> <span data-ttu-id="dc462-192">Cet objet peut être utilisé avec `Receive-Job` et `Remove-Job` , comme si vous aviez utilisé `Start-Job` pour démarrer le travail.</span><span class="sxs-lookup"><span data-stu-id="dc462-192">This object can be used with `Receive-Job` and `Remove-Job`, just as if you had used `Start-Job` to start the job.</span></span>

```powershell
$job = Get-Process -Name pwsh &
Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

```powershell
Remove-Job $job
```

<span data-ttu-id="dc462-193">L' `&` opérateur d’arrière-plan est également un terminateur d’instruction, tout comme l’opérateur de contrôle UNIX perluète ( `&` ).</span><span class="sxs-lookup"><span data-stu-id="dc462-193">The `&` background operator is also a statement terminator, just like the UNIX control operator ampersand (`&`).</span></span> <span data-ttu-id="dc462-194">Cela vous permet d’appeler des commandes supplémentaires après l' `&` opérateur d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="dc462-194">This allows you to invoke additional commands after the `&` background operator.</span></span> <span data-ttu-id="dc462-195">L’exemple suivant illustre l’appel de commandes supplémentaires après l' `&` opérateur d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="dc462-195">The following example demonstrates the invocation of additional commands after the `&` background operator.</span></span>

```powershell
$job = Get-Process -Name pwsh & Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

<span data-ttu-id="dc462-196">Cela équivaut au script suivant :</span><span class="sxs-lookup"><span data-stu-id="dc462-196">This is equivalent to the following script:</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process -Name pwsh}
Receive-Job $job -Wait
```

<span data-ttu-id="dc462-197">Si vous souhaitez exécuter plusieurs commandes, chacune dans son propre processus en arrière-plan, mais sur une seule ligne, placez- `&` la simplement entre et après chacune des commandes.</span><span class="sxs-lookup"><span data-stu-id="dc462-197">If you want to run multiple commands, each in their own background process but all on one line, simply place `&` between and after each of the commands.</span></span>

```powershell
Get-Process -Name pwsh & Get-Service -Name BITS & Get-CimInstance -ClassName Win32_ComputerSystem &
```

<span data-ttu-id="dc462-198">Pour plus d’informations sur les travaux PowerShell, consultez [about_Jobs](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="dc462-198">For more information on PowerShell jobs, see [about_Jobs](about_Jobs.md).</span></span>

#### <a name="cast-operator--"></a><span data-ttu-id="dc462-199">Cast, opérateur `[ ]`</span><span class="sxs-lookup"><span data-stu-id="dc462-199">Cast operator `[ ]`</span></span>

<span data-ttu-id="dc462-200">Convertit ou limite les objets au type spécifié.</span><span class="sxs-lookup"><span data-stu-id="dc462-200">Converts or limits objects to the specified type.</span></span> <span data-ttu-id="dc462-201">Si les objets ne peuvent pas être convertis, PowerShell génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="dc462-201">If the objects cannot be converted, PowerShell generates an error.</span></span>

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

<span data-ttu-id="dc462-202">Un cast peut également être effectué quand une variable est assignée à l’aide d’une [notation de cast](about_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="dc462-202">A cast can also be performed when a variable is assigned to using [cast notation](about_Variables.md).</span></span>

#### <a name="comma-operator-"></a><span data-ttu-id="dc462-203">Virgule (opérateur) `,`</span><span class="sxs-lookup"><span data-stu-id="dc462-203">Comma operator `,`</span></span>

<span data-ttu-id="dc462-204">En tant qu’opérateur binaire, la virgule crée un tableau ou ajoute au tableau en cours de création.</span><span class="sxs-lookup"><span data-stu-id="dc462-204">As a binary operator, the comma creates an array or appends to the array being created.</span></span> <span data-ttu-id="dc462-205">En mode expression, en tant qu’opérateur unaire, la virgule crée un tableau avec un seul membre.</span><span class="sxs-lookup"><span data-stu-id="dc462-205">In expression mode, as a unary operator, the comma creates an array with just one member.</span></span> <span data-ttu-id="dc462-206">Placez la virgule avant le membre.</span><span class="sxs-lookup"><span data-stu-id="dc462-206">Place the comma before the member.</span></span>

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

<span data-ttu-id="dc462-207">Étant donné que `Write-Object` attend un argument, vous devez placer l’expression entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="dc462-207">Since `Write-Object` expects an argument, you must put the expression in parentheses.</span></span>

#### <a name="dot-sourcing-operator-"></a><span data-ttu-id="dc462-208">Opérateur d’approvisionnement en points `.`</span><span class="sxs-lookup"><span data-stu-id="dc462-208">Dot sourcing operator `.`</span></span>

<span data-ttu-id="dc462-209">Exécute un script dans l’étendue actuelle afin que toutes les fonctions, tous les alias et toutes les variables créés par le script soient ajoutés à la portée actuelle, en substituant ceux qui existent déjà.</span><span class="sxs-lookup"><span data-stu-id="dc462-209">Runs a script in the current scope so that any functions, aliases, and variables that the script creates are added to the current scope, overriding existing ones.</span></span> <span data-ttu-id="dc462-210">Les paramètres déclarés par le script deviennent des variables.</span><span class="sxs-lookup"><span data-stu-id="dc462-210">Parameters declared by the script become variables.</span></span> <span data-ttu-id="dc462-211">Les paramètres pour lesquels aucune valeur n’a été donnée deviennent des variables sans valeur.</span><span class="sxs-lookup"><span data-stu-id="dc462-211">Parameters for which no value has been given become variables with no value.</span></span> <span data-ttu-id="dc462-212">Toutefois, la variable automatique `$args` est conservée.</span><span class="sxs-lookup"><span data-stu-id="dc462-212">However, the automatic variable `$args` is preserved.</span></span>

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> <span data-ttu-id="dc462-213">L’opérateur de source de points est suivi d’un espace.</span><span class="sxs-lookup"><span data-stu-id="dc462-213">The dot sourcing operator is followed by a space.</span></span> <span data-ttu-id="dc462-214">Utilisez l’espace pour distinguer le point du symbole point ( `.` ) qui représente le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="dc462-214">Use the space to distinguish the dot from the dot (`.`) symbol that represents the current directory.</span></span>
>
> <span data-ttu-id="dc462-215">Dans l’exemple suivant, le script Sample.ps1 dans le répertoire actif est exécuté dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="dc462-215">In the following example, the Sample.ps1 script in the current directory is run in the current scope.</span></span>
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a><span data-ttu-id="dc462-216">Format, opérateur `-f`</span><span class="sxs-lookup"><span data-stu-id="dc462-216">Format operator `-f`</span></span>

<span data-ttu-id="dc462-217">Met en forme des chaînes à l’aide de la méthode format des objets String.</span><span class="sxs-lookup"><span data-stu-id="dc462-217">Formats strings by using the format method of string objects.</span></span> <span data-ttu-id="dc462-218">Entrez la chaîne de format sur le côté gauche de l’opérateur et les objets à mettre en forme à droite de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="dc462-218">Enter the format string on the left side of the operator and the objects to be formatted on the right side of the operator.</span></span>

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

<span data-ttu-id="dc462-219">Si vous devez conserver les accolades ( `{}` ) dans la chaîne mise en forme, vous pouvez les placer dans une séquence d’échappement en doublant les accolades.</span><span class="sxs-lookup"><span data-stu-id="dc462-219">If you need to keep the curly braces (`{}`) in the formatted string, you can escape them by doubling the curly braces.</span></span>

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

<span data-ttu-id="dc462-220">Pour plus d’informations, consultez la méthode [String. format](/dotnet/api/system.string.format) et la [mise en forme composite](/dotnet/standard/base-types/composite-formatting).</span><span class="sxs-lookup"><span data-stu-id="dc462-220">For more information, see the [String.Format](/dotnet/api/system.string.format) method and [Composite Formatting](/dotnet/standard/base-types/composite-formatting).</span></span>

#### <a name="index-operator--"></a><span data-ttu-id="dc462-221">Index (opérateur) `[ ]`</span><span class="sxs-lookup"><span data-stu-id="dc462-221">Index operator `[ ]`</span></span>

<span data-ttu-id="dc462-222">Sélectionne des objets dans des collections indexées, telles que des tableaux et des tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="dc462-222">Selects objects from indexed collections, such as arrays and hash tables.</span></span> <span data-ttu-id="dc462-223">Les index de tableau sont de base zéro, donc le premier objet est indexé en tant que `[0]` .</span><span class="sxs-lookup"><span data-stu-id="dc462-223">Array indexes are zero-based, so the first object is indexed as `[0]`.</span></span> <span data-ttu-id="dc462-224">Pour les tableaux (uniquement), vous pouvez également utiliser des index négatifs pour obtenir les dernières valeurs.</span><span class="sxs-lookup"><span data-stu-id="dc462-224">For arrays (only), you can also use negative indexes to get the last values.</span></span> <span data-ttu-id="dc462-225">Les tables de hachage sont indexées par valeur de clé.</span><span class="sxs-lookup"><span data-stu-id="dc462-225">Hash tables are indexed by key value.</span></span>

```
PS> $a = 1, 2, 3
PS> $a[0]
1
PS> $a[-1]
3
```

```powershell
(Get-HotFix | Sort-Object installedOn)[-1]
```

```powershell
$h = @{key="value"; name="PowerShell"; version="2.0"}
$h["name"]
```

```output
PowerShell
```

```powershell
$x = [xml]"<doc><intro>Once upon a time...</intro></doc>"
$x["doc"]
```

```output
intro
-----
Once upon a time...
```

#### <a name="pipeline-operator-"></a><span data-ttu-id="dc462-226">Opérateur de pipeline `|`</span><span class="sxs-lookup"><span data-stu-id="dc462-226">Pipeline operator `|`</span></span>

<span data-ttu-id="dc462-227">Envoie (« Pipes ») la sortie de la commande qui la précède à la commande qui la suit.</span><span class="sxs-lookup"><span data-stu-id="dc462-227">Sends ("pipes") the output of the command that precedes it to the command that follows it.</span></span> <span data-ttu-id="dc462-228">Lorsque la sortie comprend plusieurs objets (une « collection »), l’opérateur de pipeline envoie les objets un par un.</span><span class="sxs-lookup"><span data-stu-id="dc462-228">When the output includes more than one object (a "collection"), the pipeline operator sends the objects one at a time.</span></span>

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="pipeline-chain-operators--and-"></a><span data-ttu-id="dc462-229">Opérateurs de chaîne `&&` de pipeline et `||`</span><span class="sxs-lookup"><span data-stu-id="dc462-229">Pipeline chain operators `&&` and `||`</span></span>

<span data-ttu-id="dc462-230">Exécuter de manière conditionnelle le pipeline de droite en fonction de la réussite du pipeline de gauche.</span><span class="sxs-lookup"><span data-stu-id="dc462-230">Conditionally execute the right-hand side pipeline based on the success of the left-hand side pipeline.</span></span>

```powershell
# If Get-Process successfully finds a process called notepad,
# Stop-Process -Name notepad is called
Get-Process notepad && Stop-Process -Name notepad
```

```powershell
# If npm install fails, the node_modules directory is removed
npm install || Remove-Item -Recurse ./node_modules
```

<span data-ttu-id="dc462-231">Pour plus d’informations, consultez [About_Pipeline_Chain_Operators](About_Pipeline_Chain_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc462-231">For more information, see [About_Pipeline_Chain_Operators](About_Pipeline_Chain_Operators.md).</span></span>

#### <a name="range-operator-"></a><span data-ttu-id="dc462-232">Opérateur de plage `..`</span><span class="sxs-lookup"><span data-stu-id="dc462-232">Range operator `..`</span></span>

<span data-ttu-id="dc462-233">Représente les entiers séquentiels dans un tableau d’entiers, en fonction d’une limite supérieure et inférieure.</span><span class="sxs-lookup"><span data-stu-id="dc462-233">Represents the sequential integers in an integer array, given an upper, and lower boundary.</span></span>

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

<span data-ttu-id="dc462-234">Vous pouvez également créer des plages dans l’ordre inverse.</span><span class="sxs-lookup"><span data-stu-id="dc462-234">You can also create ranges in reverse order.</span></span>

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

<span data-ttu-id="dc462-235">À compter de PowerShell 6, l’opérateur Range fonctionne avec des **caractères** et des **entiers**.</span><span class="sxs-lookup"><span data-stu-id="dc462-235">Beginning in PowerShell 6, the range operator works with **Characters** as well as **Integers**.</span></span>

<span data-ttu-id="dc462-236">Pour créer une plage de caractères, placez les caractères de la limite entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="dc462-236">To create a range of characters, enclose the boundary characters in quotes.</span></span>

```powershell
PS> 'a'..'f'
a
b
c
d
e
f
```

```powershell
PS> 'F'..'A'
F
E
D
C
B
A
```

#### <a name="member-access-operator-"></a><span data-ttu-id="dc462-237">Opérateur d’accès aux membres `.`</span><span class="sxs-lookup"><span data-stu-id="dc462-237">Member access operator `.`</span></span>

<span data-ttu-id="dc462-238">Accède aux propriétés et aux méthodes d’un objet.</span><span class="sxs-lookup"><span data-stu-id="dc462-238">Accesses the properties and methods of an object.</span></span> <span data-ttu-id="dc462-239">Le nom de membre peut être une expression.</span><span class="sxs-lookup"><span data-stu-id="dc462-239">The member name may be an expression.</span></span>

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a><span data-ttu-id="dc462-240">Opérateur de membre statique `::`</span><span class="sxs-lookup"><span data-stu-id="dc462-240">Static member operator `::`</span></span>

<span data-ttu-id="dc462-241">Appelle les propriétés et les méthodes statiques d’une classe .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc462-241">Calls the static properties and methods of a .NET Framework class.</span></span> <span data-ttu-id="dc462-242">Pour rechercher les propriétés et les méthodes statiques d’un objet, utilisez le paramètre static de l’applet de commande `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="dc462-242">To find the static properties and methods of an object, use the Static parameter of the `Get-Member` cmdlet.</span></span>  <span data-ttu-id="dc462-243">Le nom de membre peut être une expression.</span><span class="sxs-lookup"><span data-stu-id="dc462-243">The member name may be an expression.</span></span>

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

#### <a name="ternary-operator--if-true--if-false"></a><span data-ttu-id="dc462-244">Ternaire, opérateur `? <if-true> : <if-false>`</span><span class="sxs-lookup"><span data-stu-id="dc462-244">Ternary operator `? <if-true> : <if-false>`</span></span>

<span data-ttu-id="dc462-245">Vous pouvez utiliser l’opérateur ternaire comme remplacement de l' `if-else` instruction dans des cas conditionnels simples.</span><span class="sxs-lookup"><span data-stu-id="dc462-245">You can use the ternary operator as a replacement for the `if-else` statement in simple conditional cases.</span></span>

<span data-ttu-id="dc462-246">Pour plus d’informations, consultez [about_If](about_If.md).</span><span class="sxs-lookup"><span data-stu-id="dc462-246">For more information, see [about_If](about_If.md).</span></span>

#### <a name="null-coalescing-operator-"></a><span data-ttu-id="dc462-247">Opérateur de fusion Null `??`</span><span class="sxs-lookup"><span data-stu-id="dc462-247">Null-coalescing operator `??`</span></span>

<span data-ttu-id="dc462-248">L’opérateur de coalescence Null `??` retourne la valeur de son opérande gauche s’il n’est pas Null.</span><span class="sxs-lookup"><span data-stu-id="dc462-248">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't null.</span></span> <span data-ttu-id="dc462-249">Dans le cas contraire, il évalue l’opérande droit et retourne son résultat.</span><span class="sxs-lookup"><span data-stu-id="dc462-249">Otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="dc462-250">L’opérateur `??` n’évalue pas son opérande droit si l’opérande gauche a la valeur non Null.</span><span class="sxs-lookup"><span data-stu-id="dc462-250">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ?? 100
```

```Output
100
```

<span data-ttu-id="dc462-251">Dans l’exemple suivant, l’opérande de droite n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="dc462-251">In the following example, the right-hand operand won't be evaluated.</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-coalescing-assignment-operator-"></a><span data-ttu-id="dc462-252">Opérateur d’assignation de fusion Null `??=`</span><span class="sxs-lookup"><span data-stu-id="dc462-252">Null-coalescing assignment operator `??=`</span></span>

<span data-ttu-id="dc462-253">L’opérateur d’assignation de fusion Null `??=` affecte la valeur de son opérande de droite à son opérande de gauche uniquement si l’opérande de gauche a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="dc462-253">The null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to null.</span></span> <span data-ttu-id="dc462-254">L’opérateur `??=` n’évalue pas son opérande droit si l’opérande gauche a la valeur non null.</span><span class="sxs-lookup"><span data-stu-id="dc462-254">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ??= 100
$x
```

```Output
100
```

<span data-ttu-id="dc462-255">Dans l’exemple suivant, l’opérande de droite n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="dc462-255">In the following example, the right-hand operand won't be evaluated.</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-conditional-operators--and-"></a><span data-ttu-id="dc462-256">Opérateurs conditionnels null `?.` et `?[]`</span><span class="sxs-lookup"><span data-stu-id="dc462-256">Null-conditional operators `?.` and `?[]`</span></span>

> [!NOTE]
> <span data-ttu-id="dc462-257">Il s’agit d’une fonctionnalité expérimentale.</span><span class="sxs-lookup"><span data-stu-id="dc462-257">This is an experimental feature.</span></span> <span data-ttu-id="dc462-258">Pour plus d’informations, consultez [about_Experimental_Features](about_Experimental_Features.md).</span><span class="sxs-lookup"><span data-stu-id="dc462-258">For more information see [about_Experimental_Features](about_Experimental_Features.md).</span></span>

<span data-ttu-id="dc462-259">Un opérateur conditionnel null applique un accès de membre, `?.` ou à l’élément, `?[]` , à son opérande uniquement si cet opérande a la valeur non NULL ; sinon, il retourne la valeur null.</span><span class="sxs-lookup"><span data-stu-id="dc462-259">A null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns null.</span></span>

<span data-ttu-id="dc462-260">Étant donné que PowerShell permet à `?` de faire partie du nom de la variable, la spécification formelle du nom de la variable est requise pour l’utilisation de ces opérateurs.</span><span class="sxs-lookup"><span data-stu-id="dc462-260">Since PowerShell allows `?` to be part of the variable name, formal specification of the variable name is required for using these operators.</span></span> <span data-ttu-id="dc462-261">Il est donc nécessaire d’utiliser `{}` autour des noms de variables comme `${a}` ou lorsque `?` fait partie du nom de la variable `${a?}`.</span><span class="sxs-lookup"><span data-stu-id="dc462-261">So it is required to use `{}` around the variable names like `${a}` or when `?` is part of the variable name `${a?}`.</span></span>

<span data-ttu-id="dc462-262">Dans l’exemple suivant, la valeur de **propName** est retournée.</span><span class="sxs-lookup"><span data-stu-id="dc462-262">In the following example, the value of **PropName** is returned.</span></span>

```powershell
$a = @{ PropName = 100 }
${a}?.PropName
```

```Output
100
```

<span data-ttu-id="dc462-263">L’exemple suivant retourne null, sans essayer d’accéder au nom de membre **propName**.</span><span class="sxs-lookup"><span data-stu-id="dc462-263">The following example will return null, without trying to access the member name **PropName**.</span></span>

```powershell
$a = $null
${a}?.PropName
```

<span data-ttu-id="dc462-264">De même, la valeur de l’élément est retournée.</span><span class="sxs-lookup"><span data-stu-id="dc462-264">Similarly, the value of the element will be returned.</span></span>

```powershell
$a = 1..10
${a}?[0]
```

```Output
1
```

<span data-ttu-id="dc462-265">Et lorsque l’opérande a la valeur null, l’élément n’est pas accessible et la valeur null est retournée.</span><span class="sxs-lookup"><span data-stu-id="dc462-265">And when the operand is null, the element isn't accessed and null is returned.</span></span>

```PowerShell
$a = $null
${a}?[0]
```

## <a name="see-also"></a><span data-ttu-id="dc462-266">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc462-266">See also</span></span>

[<span data-ttu-id="dc462-267">about_Arithmetic_Operators</span><span class="sxs-lookup"><span data-stu-id="dc462-267">about_Arithmetic_Operators</span></span>](about_Arithmetic_Operators.md)

[<span data-ttu-id="dc462-268">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="dc462-268">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="dc462-269">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="dc462-269">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="dc462-270">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="dc462-270">about_Logical_Operators</span></span>](about_logical_operators.md)

[<span data-ttu-id="dc462-271">about_Operator_Precedence</span><span class="sxs-lookup"><span data-stu-id="dc462-271">about_Operator_Precedence</span></span>](about_operator_precedence.md)

[<span data-ttu-id="dc462-272">about_Type_Operators</span><span class="sxs-lookup"><span data-stu-id="dc462-272">about_Type_Operators</span></span>](about_Type_Operators.md)

[<span data-ttu-id="dc462-273">about_Pipeline_Chain_Operators</span><span class="sxs-lookup"><span data-stu-id="dc462-273">about_Pipeline_Chain_Operators</span></span>](about_Pipeline_Chain_Operators.md)

[<span data-ttu-id="dc462-274">about_Split</span><span class="sxs-lookup"><span data-stu-id="dc462-274">about_Split</span></span>](about_Split.md)

[<span data-ttu-id="dc462-275">about_Join</span><span class="sxs-lookup"><span data-stu-id="dc462-275">about_Join</span></span>](about_Join.md)

[<span data-ttu-id="dc462-276">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="dc462-276">about_Redirection</span></span>](about_Redirection.md)
