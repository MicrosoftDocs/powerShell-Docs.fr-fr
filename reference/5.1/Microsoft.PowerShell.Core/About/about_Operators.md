---
description: Décrit les opérateurs pris en charge par PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/28/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: a8c9c60c9c1513e1ee4ce71c8c880e20bf1df7b3
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "93208926"
---
# <a name="about-operators"></a><span data-ttu-id="88057-104">À propos des opérateurs</span><span class="sxs-lookup"><span data-stu-id="88057-104">About Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="88057-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="88057-105">Short description</span></span>
<span data-ttu-id="88057-106">Décrit les opérateurs pris en charge par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88057-106">Describes the operators that are supported by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="88057-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="88057-107">Long description</span></span>

<span data-ttu-id="88057-108">Un opérateur est un élément de langage que vous pouvez utiliser dans une commande ou une expression.</span><span class="sxs-lookup"><span data-stu-id="88057-108">An operator is a language element that you can use in a command or expression.</span></span>
<span data-ttu-id="88057-109">PowerShell prend en charge plusieurs types d’opérateurs pour vous aider à manipuler des valeurs.</span><span class="sxs-lookup"><span data-stu-id="88057-109">PowerShell supports several types of operators to help you manipulate values.</span></span>

### <a name="arithmetic-operators"></a><span data-ttu-id="88057-110">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="88057-110">Arithmetic Operators</span></span>

<span data-ttu-id="88057-111">Utilisez les opérateurs arithmétiques ( `+` , `-` ,, `*` `/` , `%` ) pour calculer des valeurs dans une commande ou une expression.</span><span class="sxs-lookup"><span data-stu-id="88057-111">Use arithmetic operators (`+`, `-`, `*`, `/`, `%`) to calculate values in a command or expression.</span></span> <span data-ttu-id="88057-112">À l’aide de ces opérateurs, vous pouvez ajouter, soustraire, multiplier ou diviser des valeurs, et calculer le reste (modulo) d’une opération de division.</span><span class="sxs-lookup"><span data-stu-id="88057-112">With these operators, you can add, subtract, multiply, or divide values, and calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="88057-113">L’opérateur d’addition concatène les éléments.</span><span class="sxs-lookup"><span data-stu-id="88057-113">The addition operator concatenates elements.</span></span> <span data-ttu-id="88057-114">L’opérateur de multiplication retourne le nombre spécifié de copies de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="88057-114">The multiplication operator returns the specified number of copies of each element.</span></span> <span data-ttu-id="88057-115">Vous pouvez utiliser des opérateurs arithmétiques sur tout type .net qui les implémente, tels que les tableaux suivants : `Int` ,,,, `String` `DateTime` `Hashtable` et.</span><span class="sxs-lookup"><span data-stu-id="88057-115">You can use arithmetic operators on any .NET type that implements them, such as: `Int`, `String`, `DateTime`, `Hashtable`, and Arrays.</span></span>

<span data-ttu-id="88057-116">Les opérateurs au niveau du bit ( `-band` , `-bor` ,, `-bxor` `-bnot` , `-shl` , `-shr` ) manipulent les modèles binaires dans les valeurs.</span><span class="sxs-lookup"><span data-stu-id="88057-116">Bitwise operators (`-band`, `-bor`, `-bxor`, `-bnot`, `-shl`, `-shr`) manipulate the bit patterns in values.</span></span>

<span data-ttu-id="88057-117">Pour plus d’informations, consultez [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="88057-117">For more information, see [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span></span>

### <a name="assignment-operators"></a><span data-ttu-id="88057-118">Opérateurs d'assignation</span><span class="sxs-lookup"><span data-stu-id="88057-118">Assignment Operators</span></span>

<span data-ttu-id="88057-119">Utilisez les opérateurs d’assignation ( `=` , `+=` , `-=` , `*=` , `/=` , `%=` ) pour assigner, modifier ou ajouter des valeurs à des variables.</span><span class="sxs-lookup"><span data-stu-id="88057-119">Use assignment operators (`=`, `+=`, `-=`, `*=`, `/=`, `%=`) to assign, change, or append values to variables.</span></span> <span data-ttu-id="88057-120">Vous pouvez combiner des opérateurs arithmétiques avec l’assignation pour assigner le résultat de l’opération arithmétique à une variable.</span><span class="sxs-lookup"><span data-stu-id="88057-120">You can combine arithmetic operators with assignment to assign the result of the arithmetic operation to a variable.</span></span>

<span data-ttu-id="88057-121">Pour plus d’informations, consultez [about_Assignment_Operators](about_Assignment_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="88057-121">For more information, see [about_Assignment_Operators](about_Assignment_Operators.md).</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="88057-122">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="88057-122">Comparison Operators</span></span>

<span data-ttu-id="88057-123">Utilisez des opérateurs de comparaison ( `-eq` , `-ne` , `-gt` , `-lt` , `-le` , `-ge` ) pour comparer des valeurs et des conditions de test.</span><span class="sxs-lookup"><span data-stu-id="88057-123">Use comparison operators (`-eq`, `-ne`, `-gt`, `-lt`, `-le`, `-ge`) to compare values and test conditions.</span></span> <span data-ttu-id="88057-124">Par exemple, vous pouvez comparer deux valeurs de chaîne pour déterminer si elles sont égales.</span><span class="sxs-lookup"><span data-stu-id="88057-124">For example, you can compare two string values to determine whether they are equal.</span></span>

<span data-ttu-id="88057-125">Les opérateurs de comparaison incluent également des opérateurs qui recherchent ou remplacent des modèles dans du texte.</span><span class="sxs-lookup"><span data-stu-id="88057-125">The comparison operators also include operators that find or replace patterns in text.</span></span> <span data-ttu-id="88057-126">Les `-match` opérateurs (, `-notmatch` , `-replace` ) utilisent des expressions régulières, et ( `-like` , `-notlike` ) utilisent des caractères génériques `*` .</span><span class="sxs-lookup"><span data-stu-id="88057-126">The (`-match`, `-notmatch`, `-replace`) operators use regular expressions, and (`-like`, `-notlike`) use wildcards `*`.</span></span>

<span data-ttu-id="88057-127">Les opérateurs de comparaison de relation contenant-contenu déterminent si une valeur de test apparaît dans un jeu de référence ( `-in` , `-notin` , `-contains` , `-notcontains` ).</span><span class="sxs-lookup"><span data-stu-id="88057-127">Containment comparison operators determine whether a test value appears in a reference set (`-in`, `-notin`, `-contains`, `-notcontains`).</span></span>

<span data-ttu-id="88057-128">Les opérateurs de comparaison `-is` de type (, `-isnot` ) déterminent si un objet est d’un type donné.</span><span class="sxs-lookup"><span data-stu-id="88057-128">Type comparison operators (`-is`, `-isnot`) determine whether an object is of a given type.</span></span>

<span data-ttu-id="88057-129">Pour plus d’informations, consultez [about_Comparison_Operators](about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="88057-129">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span>

### <a name="logical-operators"></a><span data-ttu-id="88057-130">Opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="88057-130">Logical Operators</span></span>

<span data-ttu-id="88057-131">Utilisez des opérateurs logiques ( `-and` , `-or` ,, `-xor` `-not` , `!` ) pour connecter des instructions conditionnelles à un seul conditionnel complexe.</span><span class="sxs-lookup"><span data-stu-id="88057-131">Use logical operators (`-and`, `-or`, `-xor`, `-not`, `!`) to connect conditional statements into a single complex conditional.</span></span> <span data-ttu-id="88057-132">Par exemple, vous pouvez utiliser un `-and` opérateur logique pour créer un filtre d’objets avec deux conditions différentes.</span><span class="sxs-lookup"><span data-stu-id="88057-132">For example, you can use a logical `-and` operator to create an object filter with two different conditions.</span></span>

<span data-ttu-id="88057-133">Pour plus d’informations, consultez [about_Logical_Operators](about_logical_operators.md).</span><span class="sxs-lookup"><span data-stu-id="88057-133">For more information, see [about_Logical_Operators](about_logical_operators.md).</span></span>

### <a name="redirection-operators"></a><span data-ttu-id="88057-134">Opérateurs de redirection</span><span class="sxs-lookup"><span data-stu-id="88057-134">Redirection Operators</span></span>

<span data-ttu-id="88057-135">Utilisez les opérateurs de redirection ( `>` , `>>` ,, `2>` `2>>` et `2>&1` ) pour envoyer la sortie d’une commande ou d’une expression à un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="88057-135">Use redirection operators (`>`, `>>`, `2>`, `2>>`, and `2>&1`) to send the output of a command or expression to a text file.</span></span> <span data-ttu-id="88057-136">Les opérateurs de redirection fonctionnent comme l' `Out-File` applet de commande (sans paramètres), mais ils vous permettent également de rediriger la sortie d’erreur vers les fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="88057-136">The redirection operators work like the `Out-File` cmdlet (without parameters) but they also let you redirect error output to specified files.</span></span> <span data-ttu-id="88057-137">Vous pouvez également utiliser l' `Tee-Object` applet de commande pour rediriger la sortie.</span><span class="sxs-lookup"><span data-stu-id="88057-137">You can also use the `Tee-Object` cmdlet to redirect output.</span></span>

<span data-ttu-id="88057-138">Pour plus d’informations, consultez [about_Redirection](about_Redirection.md)</span><span class="sxs-lookup"><span data-stu-id="88057-138">For more information, see [about_Redirection](about_Redirection.md)</span></span>

### <a name="split-and-join-operators"></a><span data-ttu-id="88057-139">Opérateurs Split et Join</span><span class="sxs-lookup"><span data-stu-id="88057-139">Split and Join Operators</span></span>

<span data-ttu-id="88057-140">Les `-split` `-join` opérateurs et divisent et combinent des sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="88057-140">The `-split` and `-join` operators divide and combine substrings.</span></span> <span data-ttu-id="88057-141">L' `-split` opérateur fractionne une chaîne en sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="88057-141">The `-split` operator splits a string into substrings.</span></span> <span data-ttu-id="88057-142">L' `-join` opérateur concatène plusieurs chaînes en une seule chaîne.</span><span class="sxs-lookup"><span data-stu-id="88057-142">The `-join` operator concatenates multiple strings into a single string.</span></span>

<span data-ttu-id="88057-143">Pour plus d’informations, consultez [about_Split](about_Split.md) et [about_Join](about_Join.md).</span><span class="sxs-lookup"><span data-stu-id="88057-143">For more information, see [about_Split](about_Split.md) and [about_Join](about_Join.md).</span></span>

### <a name="type-operators"></a><span data-ttu-id="88057-144">Opérateurs de type</span><span class="sxs-lookup"><span data-stu-id="88057-144">Type Operators</span></span>

<span data-ttu-id="88057-145">Utilisez les opérateurs de type ( `-is` , `-isnot` , `-as` ) pour rechercher ou modifier le type de .NET Framework d’un objet.</span><span class="sxs-lookup"><span data-stu-id="88057-145">Use the type operators (`-is`, `-isnot`, `-as`) to find or change the .NET Framework type of an object.</span></span>

<span data-ttu-id="88057-146">Pour plus d’informations, consultez [about_Type_Operators](about_Type_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="88057-146">For more information, see [about_Type_Operators](about_Type_Operators.md).</span></span>

### <a name="unary-operators"></a><span data-ttu-id="88057-147">Opérateurs unaires</span><span class="sxs-lookup"><span data-stu-id="88057-147">Unary Operators</span></span>

<span data-ttu-id="88057-148">Utilisez des opérateurs unaires pour incrémenter ou décrémenter des variables ou des propriétés d’objet et pour définir des entiers avec des nombres positifs ou négatifs.</span><span class="sxs-lookup"><span data-stu-id="88057-148">Use unary operators to increment or decrement variables or object properties and to set integers to positive or negative numbers.</span></span> <span data-ttu-id="88057-149">Par exemple, pour incrémenter la variable `$a` de `9` à `10` , vous tapez `$a++` .</span><span class="sxs-lookup"><span data-stu-id="88057-149">For example, to increment the variable `$a` from `9` to `10`, you type `$a++`.</span></span>

### <a name="special-operators"></a><span data-ttu-id="88057-150">Opérateurs spéciaux</span><span class="sxs-lookup"><span data-stu-id="88057-150">Special Operators</span></span>

<span data-ttu-id="88057-151">Les opérateurs spéciaux ont des cas d’usage spécifiques qui ne rentrent dans aucun autre groupe d’opérateurs.</span><span class="sxs-lookup"><span data-stu-id="88057-151">Special operators have specific use-cases that do not fit into any other operator group.</span></span> <span data-ttu-id="88057-152">Par exemple, les opérateurs spéciaux vous permettent d’exécuter des commandes, de modifier le type de données d’une valeur ou de récupérer des éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="88057-152">For example, special operators allow you to run commands, change a value's data type, or retrieve elements from an array.</span></span>

#### <a name="grouping-operator--"></a><span data-ttu-id="88057-153">Opérateur de regroupement `( )`</span><span class="sxs-lookup"><span data-stu-id="88057-153">Grouping operator `( )`</span></span>

<span data-ttu-id="88057-154">Comme dans d’autres langages, `(...)` sert à remplacer la priorité des opérateurs dans les expressions.</span><span class="sxs-lookup"><span data-stu-id="88057-154">As in other languages, `(...)` serves to override operator precedence in expressions.</span></span> <span data-ttu-id="88057-155">Par exemple : `(1 + 2) / 3`</span><span class="sxs-lookup"><span data-stu-id="88057-155">For example: `(1 + 2) / 3`</span></span>

<span data-ttu-id="88057-156">Toutefois, dans PowerShell, il existe des comportements supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="88057-156">However, in PowerShell, there are additional behaviors.</span></span>

- <span data-ttu-id="88057-157">`(...)` vous permet de laisser la sortie d’une _commande_ participer à une expression.</span><span class="sxs-lookup"><span data-stu-id="88057-157">`(...)` allows you to let output from a _command_ participate in an expression.</span></span> <span data-ttu-id="88057-158">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="88057-158">For example:</span></span>

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- <span data-ttu-id="88057-159">Lorsqu’il est utilisé comme premier segment d’un pipeline, l’encapsulation d’une commande ou d’une expression entre parenthèses provoque invariablement l' _énumération_ du résultat de l’expression.</span><span class="sxs-lookup"><span data-stu-id="88057-159">When used as the first segment of a pipeline, wrapping a command or expression in parentheses invariably causes _enumeration_ of the expression result.</span></span> <span data-ttu-id="88057-160">Si les parenthèses encapsulent une _commande_ , elles sont exécutées jusqu’à la fin avec toute la sortie _collectée en mémoire_ avant que les résultats ne soient envoyés via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="88057-160">If the parentheses wrap a _command_ , it is run to completion with all output _collected in memory_ before the results are sent through the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="88057-161">Si vous encapsulez une commande entre parenthèses, la variable automatique `$?` est définie sur `$true` , même lorsque la commande placée elle-même a la valeur `$?` `$false` .</span><span class="sxs-lookup"><span data-stu-id="88057-161">Wrapping a command in parentheses causes the automatic variable `$?` to be set to `$true`, even when the enclosed command itself set `$?` to `$false`.</span></span>
> <span data-ttu-id="88057-162">Par exemple, `(Get-Item /Nosuch); $?` génère de façon inattendue la **valeur true**.</span><span class="sxs-lookup"><span data-stu-id="88057-162">For example, `(Get-Item /Nosuch); $?` unexpectedly yields **True**.</span></span> <span data-ttu-id="88057-163">Pour plus d’informations sur `$?` , consultez [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="88057-163">For more information about `$?`, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

#### <a name="subexpression-operator--"></a><span data-ttu-id="88057-164">Opérateur de sous-expression `$( )`</span><span class="sxs-lookup"><span data-stu-id="88057-164">Subexpression operator `$( )`</span></span>

<span data-ttu-id="88057-165">Retourne le résultat d’une ou plusieurs instructions.</span><span class="sxs-lookup"><span data-stu-id="88057-165">Returns the result of one or more statements.</span></span> <span data-ttu-id="88057-166">Pour un résultat unique, retourne un scalaire.</span><span class="sxs-lookup"><span data-stu-id="88057-166">For a single result, returns a scalar.</span></span> <span data-ttu-id="88057-167">Pour plusieurs résultats, retourne un tableau.</span><span class="sxs-lookup"><span data-stu-id="88057-167">For multiple results, returns an array.</span></span> <span data-ttu-id="88057-168">Utilisez cette valeur lorsque vous souhaitez utiliser une expression dans une autre expression.</span><span class="sxs-lookup"><span data-stu-id="88057-168">Use this when you want to use an expression within another expression.</span></span> <span data-ttu-id="88057-169">Par exemple, pour incorporer les résultats de la commande dans une expression de chaîne.</span><span class="sxs-lookup"><span data-stu-id="88057-169">For example, to embed the results of command in a string expression.</span></span>

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a><span data-ttu-id="88057-170">Opérateur de sous-expression de tableau `@( )`</span><span class="sxs-lookup"><span data-stu-id="88057-170">Array subexpression operator `@( )`</span></span>

<span data-ttu-id="88057-171">Retourne le résultat d’une ou plusieurs instructions sous la forme d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="88057-171">Returns the result of one or more statements as an array.</span></span> <span data-ttu-id="88057-172">S’il n’y a qu’un seul élément, le tableau ne possède qu’un seul membre.</span><span class="sxs-lookup"><span data-stu-id="88057-172">If there is only one item, the array has only one member.</span></span>

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="call-operator-"></a><span data-ttu-id="88057-173">Opérateur d’appel `&`</span><span class="sxs-lookup"><span data-stu-id="88057-173">Call operator `&`</span></span>

<span data-ttu-id="88057-174">Exécute une commande, un script ou un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="88057-174">Runs a command, script, or script block.</span></span> <span data-ttu-id="88057-175">L’opérateur d’appel, également appelé « opérateur d’appel », vous permet d’exécuter des commandes qui sont stockées dans des variables et représentées par des chaînes ou des blocs de script.</span><span class="sxs-lookup"><span data-stu-id="88057-175">The call operator, also known as the "invocation operator", lets you run commands that are stored in variables and represented by strings or script blocks.</span></span> <span data-ttu-id="88057-176">L’opérateur d’appel s’exécute dans une portée enfant.</span><span class="sxs-lookup"><span data-stu-id="88057-176">The call operator executes in a child scope.</span></span> <span data-ttu-id="88057-177">Pour plus d’informations sur les étendues, consultez [about_Scopes](about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="88057-177">For more about scopes, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="88057-178">Cet exemple stocke une commande dans une chaîne et l’exécute à l’aide de l’opérateur d’appel.</span><span class="sxs-lookup"><span data-stu-id="88057-178">This example stores a command in a string and executes it using the call operator.</span></span>

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

<span data-ttu-id="88057-179">L’opérateur d’appel n’analyse pas les chaînes.</span><span class="sxs-lookup"><span data-stu-id="88057-179">The call operator does not parse strings.</span></span> <span data-ttu-id="88057-180">Cela signifie que vous ne pouvez pas utiliser de paramètres de commande dans une chaîne lorsque vous utilisez l’opérateur d’appel.</span><span class="sxs-lookup"><span data-stu-id="88057-180">This means that you cannot use command parameters within a string when you use the call operator.</span></span>

```
PS> $c = "Get-Service -Name Spooler"
PS> $c
Get-Service -Name Spooler
PS> & $c
& : The term 'Get-Service -Name Spooler' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of
the name, or if a path was included, verify that the path is correct and
try again.
At line:1 char:2
+ & $c
+  ~~
    + CategoryInfo          : ObjectNotFound: (Get-Service -Name Spooler:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

<span data-ttu-id="88057-181">L’applet de commande [Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) peut exécuter du code qui provoque des erreurs d’analyse lors de l’utilisation de l’opérateur d’appel.</span><span class="sxs-lookup"><span data-stu-id="88057-181">The [Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) cmdlet can execute code that causes parsing errors when using the call operator.</span></span>

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

<span data-ttu-id="88057-182">Vous pouvez utiliser l’opérateur d’appel pour exécuter des scripts à l’aide de leurs noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="88057-182">You can use the call operator to execute scripts using their filenames.</span></span> <span data-ttu-id="88057-183">L’exemple ci-dessous montre un nom de fichier de script qui contient des espaces.</span><span class="sxs-lookup"><span data-stu-id="88057-183">The example below shows a script filename that contains spaces.</span></span> <span data-ttu-id="88057-184">Lorsque vous essayez d’exécuter le script, PowerShell affiche à la place le contenu de la chaîne entre guillemets contenant le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="88057-184">When you try to execute the script, PowerShell instead displays the contents of the quoted string containing the filename.</span></span> <span data-ttu-id="88057-185">L’opérateur d’appel vous permet d’exécuter le contenu de la chaîne contenant le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="88057-185">The call operator allows you to execute the contents of the string containing the filename.</span></span>

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

<span data-ttu-id="88057-186">Pour plus d’informations sur les blocs de script, consultez [about_Script_Blocks](about_Script_Blocks.md).</span><span class="sxs-lookup"><span data-stu-id="88057-186">For more about script blocks, see [about_Script_Blocks](about_Script_Blocks.md).</span></span>

#### <a name="cast-operator--"></a><span data-ttu-id="88057-187">Cast, opérateur `[ ]`</span><span class="sxs-lookup"><span data-stu-id="88057-187">Cast operator `[ ]`</span></span>

<span data-ttu-id="88057-188">Convertit ou limite les objets au type spécifié.</span><span class="sxs-lookup"><span data-stu-id="88057-188">Converts or limits objects to the specified type.</span></span> <span data-ttu-id="88057-189">Si les objets ne peuvent pas être convertis, PowerShell génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="88057-189">If the objects cannot be converted, PowerShell generates an error.</span></span>

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

<span data-ttu-id="88057-190">Un cast peut également être effectué quand une variable est assignée à l’aide d’une [notation de cast](about_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="88057-190">A cast can also be performed when a variable is assigned to using [cast notation](about_Variables.md).</span></span>

#### <a name="comma-operator-"></a><span data-ttu-id="88057-191">Virgule (opérateur) `,`</span><span class="sxs-lookup"><span data-stu-id="88057-191">Comma operator `,`</span></span>

<span data-ttu-id="88057-192">En tant qu’opérateur binaire, la virgule crée un tableau ou ajoute au tableau en cours de création.</span><span class="sxs-lookup"><span data-stu-id="88057-192">As a binary operator, the comma creates an array or appends to the array being created.</span></span> <span data-ttu-id="88057-193">En mode expression, en tant qu’opérateur unaire, la virgule crée un tableau avec un seul membre.</span><span class="sxs-lookup"><span data-stu-id="88057-193">In expression mode, as a unary operator, the comma creates an array with just one member.</span></span> <span data-ttu-id="88057-194">Placez la virgule avant le membre.</span><span class="sxs-lookup"><span data-stu-id="88057-194">Place the comma before the member.</span></span>

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

<span data-ttu-id="88057-195">Étant donné que `Write-Object` attend un argument, vous devez placer l’expression entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="88057-195">Since `Write-Object` expects an argument, you must put the expression in parentheses.</span></span>

#### <a name="dot-sourcing-operator-"></a><span data-ttu-id="88057-196">Opérateur d’approvisionnement en points `.`</span><span class="sxs-lookup"><span data-stu-id="88057-196">Dot sourcing operator `.`</span></span>

<span data-ttu-id="88057-197">Exécute un script dans l’étendue actuelle afin que toutes les fonctions, tous les alias et toutes les variables créés par le script soient ajoutés à la portée actuelle, en substituant ceux qui existent déjà.</span><span class="sxs-lookup"><span data-stu-id="88057-197">Runs a script in the current scope so that any functions, aliases, and variables that the script creates are added to the current scope, overriding existing ones.</span></span> <span data-ttu-id="88057-198">Les paramètres déclarés par le script deviennent des variables.</span><span class="sxs-lookup"><span data-stu-id="88057-198">Parameters declared by the script become variables.</span></span> <span data-ttu-id="88057-199">Les paramètres pour lesquels aucune valeur n’a été donnée deviennent des variables sans valeur.</span><span class="sxs-lookup"><span data-stu-id="88057-199">Parameters for which no value has been given become variables with no value.</span></span> <span data-ttu-id="88057-200">Toutefois, la variable automatique `$args` est conservée.</span><span class="sxs-lookup"><span data-stu-id="88057-200">However, the automatic variable `$args` is preserved.</span></span>

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> <span data-ttu-id="88057-201">L’opérateur de source de points est suivi d’un espace.</span><span class="sxs-lookup"><span data-stu-id="88057-201">The dot sourcing operator is followed by a space.</span></span> <span data-ttu-id="88057-202">Utilisez l’espace pour distinguer le point du symbole point ( `.` ) qui représente le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="88057-202">Use the space to distinguish the dot from the dot (`.`) symbol that represents the current directory.</span></span>
>
> <span data-ttu-id="88057-203">Dans l’exemple suivant, le script Sample.ps1 dans le répertoire actif est exécuté dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="88057-203">In the following example, the Sample.ps1 script in the current directory is run in the current scope.</span></span>
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a><span data-ttu-id="88057-204">Format, opérateur `-f`</span><span class="sxs-lookup"><span data-stu-id="88057-204">Format operator `-f`</span></span>

<span data-ttu-id="88057-205">Met en forme des chaînes à l’aide de la méthode format des objets String.</span><span class="sxs-lookup"><span data-stu-id="88057-205">Formats strings by using the format method of string objects.</span></span> <span data-ttu-id="88057-206">Entrez la chaîne de format sur le côté gauche de l’opérateur et les objets à mettre en forme à droite de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="88057-206">Enter the format string on the left side of the operator and the objects to be formatted on the right side of the operator.</span></span>

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

<span data-ttu-id="88057-207">Si vous devez conserver les accolades ( `{}` ) dans la chaîne mise en forme, vous pouvez les placer dans une séquence d’échappement en doublant les accolades.</span><span class="sxs-lookup"><span data-stu-id="88057-207">If you need to keep the curly braces (`{}`) in the formatted string, you can escape them by doubling the curly braces.</span></span>

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

<span data-ttu-id="88057-208">Pour plus d’informations, consultez la méthode [String. format](/dotnet/api/system.string.format) et la [mise en forme composite](/dotnet/standard/base-types/composite-formatting).</span><span class="sxs-lookup"><span data-stu-id="88057-208">For more information, see the [String.Format](/dotnet/api/system.string.format) method and [Composite Formatting](/dotnet/standard/base-types/composite-formatting).</span></span>

#### <a name="index-operator--"></a><span data-ttu-id="88057-209">Index (opérateur) `[ ]`</span><span class="sxs-lookup"><span data-stu-id="88057-209">Index operator `[ ]`</span></span>

<span data-ttu-id="88057-210">Sélectionne des objets dans des collections indexées, telles que des tableaux et des tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="88057-210">Selects objects from indexed collections, such as arrays and hash tables.</span></span> <span data-ttu-id="88057-211">Les index de tableau sont de base zéro, donc le premier objet est indexé en tant que `[0]` .</span><span class="sxs-lookup"><span data-stu-id="88057-211">Array indexes are zero-based, so the first object is indexed as `[0]`.</span></span> <span data-ttu-id="88057-212">Pour les tableaux (uniquement), vous pouvez également utiliser des index négatifs pour obtenir les dernières valeurs.</span><span class="sxs-lookup"><span data-stu-id="88057-212">For arrays (only), you can also use negative indexes to get the last values.</span></span> <span data-ttu-id="88057-213">Les tables de hachage sont indexées par valeur de clé.</span><span class="sxs-lookup"><span data-stu-id="88057-213">Hash tables are indexed by key value.</span></span>

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

#### <a name="pipeline-operator-"></a><span data-ttu-id="88057-214">Opérateur de pipeline `|`</span><span class="sxs-lookup"><span data-stu-id="88057-214">Pipeline operator `|`</span></span>

<span data-ttu-id="88057-215">Envoie (« Pipes ») la sortie de la commande qui la précède à la commande qui la suit.</span><span class="sxs-lookup"><span data-stu-id="88057-215">Sends ("pipes") the output of the command that precedes it to the command that follows it.</span></span> <span data-ttu-id="88057-216">Lorsque la sortie comprend plusieurs objets (une « collection »), l’opérateur de pipeline envoie les objets un par un.</span><span class="sxs-lookup"><span data-stu-id="88057-216">When the output includes more than one object (a "collection"), the pipeline operator sends the objects one at a time.</span></span>

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="range-operator-"></a><span data-ttu-id="88057-217">Opérateur de plage `..`</span><span class="sxs-lookup"><span data-stu-id="88057-217">Range operator `..`</span></span>

<span data-ttu-id="88057-218">Représente les entiers séquentiels dans un tableau d’entiers, en fonction d’une limite supérieure et inférieure.</span><span class="sxs-lookup"><span data-stu-id="88057-218">Represents the sequential integers in an integer array, given an upper, and lower boundary.</span></span>

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

<span data-ttu-id="88057-219">Vous pouvez également créer des plages dans l’ordre inverse.</span><span class="sxs-lookup"><span data-stu-id="88057-219">You can also create ranges in reverse order.</span></span>

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

#### <a name="member-access-operator-"></a><span data-ttu-id="88057-220">Opérateur d’accès aux membres `.`</span><span class="sxs-lookup"><span data-stu-id="88057-220">Member access operator `.`</span></span>

<span data-ttu-id="88057-221">Accède aux propriétés et aux méthodes d’un objet.</span><span class="sxs-lookup"><span data-stu-id="88057-221">Accesses the properties and methods of an object.</span></span> <span data-ttu-id="88057-222">Le nom de membre peut être une expression.</span><span class="sxs-lookup"><span data-stu-id="88057-222">The member name may be an expression.</span></span>

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a><span data-ttu-id="88057-223">Opérateur de membre statique `::`</span><span class="sxs-lookup"><span data-stu-id="88057-223">Static member operator `::`</span></span>

<span data-ttu-id="88057-224">Appelle les propriétés et les méthodes statiques d’une classe .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="88057-224">Calls the static properties and methods of a .NET Framework class.</span></span> <span data-ttu-id="88057-225">Pour rechercher les propriétés et les méthodes statiques d’un objet, utilisez le paramètre static de l’applet de commande `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="88057-225">To find the static properties and methods of an object, use the Static parameter of the `Get-Member` cmdlet.</span></span>  <span data-ttu-id="88057-226">Le nom de membre peut être une expression.</span><span class="sxs-lookup"><span data-stu-id="88057-226">The member name may be an expression.</span></span>

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

## <a name="see-also"></a><span data-ttu-id="88057-227">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88057-227">See also</span></span>

[<span data-ttu-id="88057-228">about_Arithmetic_Operators</span><span class="sxs-lookup"><span data-stu-id="88057-228">about_Arithmetic_Operators</span></span>](about_Arithmetic_Operators.md)

[<span data-ttu-id="88057-229">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="88057-229">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="88057-230">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="88057-230">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="88057-231">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="88057-231">about_Logical_Operators</span></span>](about_logical_operators.md)

[<span data-ttu-id="88057-232">about_Operator_Precedence</span><span class="sxs-lookup"><span data-stu-id="88057-232">about_Operator_Precedence</span></span>](about_operator_precedence.md)

[<span data-ttu-id="88057-233">about_Type_Operators</span><span class="sxs-lookup"><span data-stu-id="88057-233">about_Type_Operators</span></span>](about_Type_Operators.md)

[<span data-ttu-id="88057-234">about_Split</span><span class="sxs-lookup"><span data-stu-id="88057-234">about_Split</span></span>](about_Split.md)

[<span data-ttu-id="88057-235">about_Join</span><span class="sxs-lookup"><span data-stu-id="88057-235">about_Join</span></span>](about_Join.md)

[<span data-ttu-id="88057-236">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="88057-236">about_Redirection</span></span>](about_Redirection.md)
