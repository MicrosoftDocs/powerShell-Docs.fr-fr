---
description: Décrit comment utiliser des opérateurs pour assigner des valeurs à des variables.
keywords: powershell,applet de commande
ms.date: 04/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_assignment_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Assignment_Operators
ms.openlocfilehash: 06c68066b82bc4d8aec4d1a51c39e16fa52c2956
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207813"
---
# <a name="about-assignment-operators"></a><span data-ttu-id="c4765-104">À propos des opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="c4765-104">About Assignment Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="c4765-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="c4765-105">Short description</span></span>
<span data-ttu-id="c4765-106">Décrit comment utiliser des opérateurs pour assigner des valeurs à des variables.</span><span class="sxs-lookup"><span data-stu-id="c4765-106">Describes how to use operators to assign values to variables.</span></span>

## <a name="long-description"></a><span data-ttu-id="c4765-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="c4765-107">Long description</span></span>

<span data-ttu-id="c4765-108">Les opérateurs d’assignation affectent une ou plusieurs valeurs à une variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-108">Assignment operators assign one or more values to a variable.</span></span> <span data-ttu-id="c4765-109">Ils peuvent effectuer des opérations numériques sur les valeurs avant l’assignation.</span><span class="sxs-lookup"><span data-stu-id="c4765-109">They can perform numeric operations on the values before the assignment.</span></span>

<span data-ttu-id="c4765-110">PowerShell prend en charge les opérateurs d’assignation suivants.</span><span class="sxs-lookup"><span data-stu-id="c4765-110">PowerShell supports the following assignment operators.</span></span>

|<span data-ttu-id="c4765-111">Opérateur</span><span class="sxs-lookup"><span data-stu-id="c4765-111">Operator</span></span>|<span data-ttu-id="c4765-112">Description</span><span class="sxs-lookup"><span data-stu-id="c4765-112">Description</span></span>                                                  |
|--------|-------------------------------------------------------------|
|=       |<span data-ttu-id="c4765-113">Affecte la valeur spécifiée à une variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-113">Sets the value of a variable to the specified value.</span></span>         |
|+=      |<span data-ttu-id="c4765-114">Augmente la valeur d’une variable par la valeur spécifiée, ou</span><span class="sxs-lookup"><span data-stu-id="c4765-114">Increases the value of a variable by the specified value, or</span></span> |
|        |<span data-ttu-id="c4765-115">Ajoute la valeur spécifiée à la valeur existante.</span><span class="sxs-lookup"><span data-stu-id="c4765-115">appends the specified value to the existing value.</span></span>           |
|-=      |<span data-ttu-id="c4765-116">Réduit la valeur d’une variable par la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c4765-116">Decreases the value of a variable by the specified value.</span></span>    |
|*=      |<span data-ttu-id="c4765-117">Multiplie la valeur d’une variable par la valeur spécifiée, ou</span><span class="sxs-lookup"><span data-stu-id="c4765-117">Multiplies the value of a variable by the specified value, or</span></span>|
|        |<span data-ttu-id="c4765-118">Ajoute la valeur spécifiée à la valeur existante.</span><span class="sxs-lookup"><span data-stu-id="c4765-118">appends the specified value to the existing value.</span></span>           |
|/=      |<span data-ttu-id="c4765-119">Divise la valeur d’une variable par la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c4765-119">Divides the value of a variable by the specified value.</span></span>      |
|%=      |<span data-ttu-id="c4765-120">Divise la valeur d’une variable par la valeur spécifiée et</span><span class="sxs-lookup"><span data-stu-id="c4765-120">Divides the value of a variable by the specified value and</span></span>   |
|        |<span data-ttu-id="c4765-121">affecte ensuite le reste (modulo) à la variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-121">then assigns the remainder (modulus) to the variable.</span></span>        |
|++      |<span data-ttu-id="c4765-122">Augmente la valeur d’une variable, d’une propriété qui est assignée ou</span><span class="sxs-lookup"><span data-stu-id="c4765-122">Increases the value of a variable, assignable property, or</span></span>   |
|        |<span data-ttu-id="c4765-123">élément de tableau de 1.</span><span class="sxs-lookup"><span data-stu-id="c4765-123">array element by 1.</span></span>                                          |
|--      |<span data-ttu-id="c4765-124">Diminue la valeur d’une variable, d’une propriété qui est assignée ou</span><span class="sxs-lookup"><span data-stu-id="c4765-124">Decreases the value of a variable, assignable property, or</span></span>   |
|        |<span data-ttu-id="c4765-125">élément de tableau de 1.</span><span class="sxs-lookup"><span data-stu-id="c4765-125">array element by 1.</span></span>                                          |

## <a name="syntax"></a><span data-ttu-id="c4765-126">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4765-126">Syntax</span></span>

<span data-ttu-id="c4765-127">La syntaxe des opérateurs d’assignation est la suivante :</span><span class="sxs-lookup"><span data-stu-id="c4765-127">The syntax of the assignment operators is as follows:</span></span>

<span data-ttu-id="c4765-128">`<assignable-expression>` `<assignment-operator>` `<value>`</span><span class="sxs-lookup"><span data-stu-id="c4765-128">`<assignable-expression>` `<assignment-operator>` `<value>`</span></span>

<span data-ttu-id="c4765-129">Les expressions assignables incluent des variables et des propriétés.</span><span class="sxs-lookup"><span data-stu-id="c4765-129">Assignable expressions include variables and properties.</span></span> <span data-ttu-id="c4765-130">La valeur peut être une valeur unique, un tableau de valeurs, ou une commande, une expression ou une instruction.</span><span class="sxs-lookup"><span data-stu-id="c4765-130">The value can be a single value, an array of values, or a command, expression, or statement.</span></span>

<span data-ttu-id="c4765-131">Les opérateurs d’incrémentation et de décrémentation sont des opérateurs unaires.</span><span class="sxs-lookup"><span data-stu-id="c4765-131">The increment and decrement operators are unary operators.</span></span> <span data-ttu-id="c4765-132">Chaque possède des versions de préfixe et de suffixe.</span><span class="sxs-lookup"><span data-stu-id="c4765-132">Each has prefix and postfix versions.</span></span>

`<assignable-expression><operator>`
`<operator><assignable-expression>`

<span data-ttu-id="c4765-133">L’expression pouvant être assignée doit être un nombre ou être convertible en un nombre.</span><span class="sxs-lookup"><span data-stu-id="c4765-133">The assignable expression must be a number or it must be convertible to a number.</span></span>

## <a name="assigning-values"></a><span data-ttu-id="c4765-134">Assigner des valeurs</span><span class="sxs-lookup"><span data-stu-id="c4765-134">Assigning values</span></span>

<span data-ttu-id="c4765-135">Les variables sont nommées espaces mémoire qui stockent des valeurs.</span><span class="sxs-lookup"><span data-stu-id="c4765-135">Variables are named memory spaces that store values.</span></span> <span data-ttu-id="c4765-136">Vous stockez les valeurs dans des variables à l’aide de l’opérateur d’assignation `=` .</span><span class="sxs-lookup"><span data-stu-id="c4765-136">You store the values in variables by using the assignment operator `=`.</span></span> <span data-ttu-id="c4765-137">La nouvelle valeur peut remplacer la valeur existante de la variable, ou vous pouvez ajouter une nouvelle valeur à la valeur existante.</span><span class="sxs-lookup"><span data-stu-id="c4765-137">The new value can replace the existing value of the variable, or you can append a new value to the existing value.</span></span>

<span data-ttu-id="c4765-138">L’opérateur d’assignation de base est le signe égal `=` `(ASCII 61)` .</span><span class="sxs-lookup"><span data-stu-id="c4765-138">The basic assignment operator is the equal sign `=` `(ASCII 61)`.</span></span> <span data-ttu-id="c4765-139">Par exemple, l’instruction suivante assigne la valeur PowerShell à la `$MyShell` variable :</span><span class="sxs-lookup"><span data-stu-id="c4765-139">For example, the following statement assigns the value PowerShell to the `$MyShell` variable:</span></span>

```powershell
$MyShell = "PowerShell"
```

<span data-ttu-id="c4765-140">Lorsque vous affectez une valeur à une variable dans PowerShell, la variable est créée si elle n’existait pas déjà.</span><span class="sxs-lookup"><span data-stu-id="c4765-140">When you assign a value to a variable in PowerShell, the variable is created if it did not already exist.</span></span> <span data-ttu-id="c4765-141">Par exemple, la première des deux instructions d’assignation suivantes crée la `$a` variable et assigne une valeur de 6 à `$a` .</span><span class="sxs-lookup"><span data-stu-id="c4765-141">For example, the first of the following two assignment statements creates the `$a` variable and assigns a value of 6 to `$a`.</span></span> <span data-ttu-id="c4765-142">La deuxième instruction d’assignation assigne une valeur de 12 à `$a` .</span><span class="sxs-lookup"><span data-stu-id="c4765-142">The second assignment statement assigns a value of 12 to `$a`.</span></span> <span data-ttu-id="c4765-143">La première instruction crée une variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-143">The first statement creates a new variable.</span></span> <span data-ttu-id="c4765-144">La deuxième instruction modifie uniquement sa valeur :</span><span class="sxs-lookup"><span data-stu-id="c4765-144">The second statement changes only its value:</span></span>

```powershell
$a = 6
$a = 12
```

<span data-ttu-id="c4765-145">Les variables dans PowerShell n’ont pas un type de données spécifique, sauf si vous effectuez un cast.</span><span class="sxs-lookup"><span data-stu-id="c4765-145">Variables in PowerShell do not have a specific data type unless you cast them.</span></span>
<span data-ttu-id="c4765-146">Quand une variable contient un seul objet, la variable prend le type de données de cet objet.</span><span class="sxs-lookup"><span data-stu-id="c4765-146">When a variable contains only one object, the variable takes the data type of that object.</span></span> <span data-ttu-id="c4765-147">Quand une variable contient une collection d’objets, la variable a le type de données System. Object.</span><span class="sxs-lookup"><span data-stu-id="c4765-147">When a variable contains a collection of objects, the variable has the System.Object data type.</span></span> <span data-ttu-id="c4765-148">Par conséquent, vous pouvez assigner n’importe quel type d’objet à la collection.</span><span class="sxs-lookup"><span data-stu-id="c4765-148">Therefore, you can assign any type of object to the collection.</span></span> <span data-ttu-id="c4765-149">L’exemple suivant montre que vous pouvez ajouter des objets de processus, des objets de service, des chaînes et des entiers à une variable sans générer d’erreur :</span><span class="sxs-lookup"><span data-stu-id="c4765-149">The following example shows that you can add process objects, service objects, strings, and integers to a variable without generating an error:</span></span>

```powershell
$a = Get-Process
$a += Get-Service
$a += "string"
$a += 12
```

<span data-ttu-id="c4765-150">Étant donné que l’opérateur `=` d’assignation a une priorité inférieure à celle de l’opérateur de pipeline `|` , les parenthèses ne sont pas requises pour assigner le résultat d’un pipeline de commande à une variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-150">Because the assignment operator `=` has a lower precedence than the pipeline operator `|`, parentheses are not required to assign the result of a command pipeline to a variable.</span></span> <span data-ttu-id="c4765-151">Par exemple, la commande suivante trie les services sur l’ordinateur, puis assigne les services triés à la `$a` variable :</span><span class="sxs-lookup"><span data-stu-id="c4765-151">For example, the following command sorts the services on the computer and then assigns the sorted services to the `$a` variable:</span></span>

```powershell
$a = Get-Service | Sort-Object -Property name
```

<span data-ttu-id="c4765-152">Vous pouvez également assigner la valeur créée par une instruction à une variable, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c4765-152">You can also assign the value created by a statement to a variable, as in the following example:</span></span>

```powershell
$a = if ($b -lt 0) { 0 } else { $b }
```

<span data-ttu-id="c4765-153">Cet exemple assigne zéro à la `$a` variable si la valeur de `$b` est inférieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="c4765-153">This example assigns zero to the `$a` variable if the value of `$b` is less than zero.</span></span> <span data-ttu-id="c4765-154">Elle assigne la valeur de `$b` à `$a` si la valeur de `$b` n’est pas inférieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="c4765-154">It assigns the value of `$b` to `$a` if the value of `$b` is not less than zero.</span></span>

### <a name="the-assignment-operator"></a><span data-ttu-id="c4765-155">Opérateur d’assignation</span><span class="sxs-lookup"><span data-stu-id="c4765-155">The assignment operator</span></span>

<span data-ttu-id="c4765-156">L’opérateur `=` d’assignation affecte des valeurs aux variables.</span><span class="sxs-lookup"><span data-stu-id="c4765-156">The assignment operator `=` assigns values to variables.</span></span> <span data-ttu-id="c4765-157">Si la variable a déjà une valeur, l’opérateur d’assignation `=` remplace la valeur sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="c4765-157">If the variable already has a value, the assignment operator `=` replaces the value without warning.</span></span>

<span data-ttu-id="c4765-158">L’instruction suivante assigne la valeur entière 6 à la `$a` variable :</span><span class="sxs-lookup"><span data-stu-id="c4765-158">The following statement assigns the integer value 6 to the `$a` variable:</span></span>

```powershell
$a = 6
```

<span data-ttu-id="c4765-159">Pour assigner une valeur de chaîne à une variable, mettez la valeur de chaîne entre guillemets, comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4765-159">To assign a string value to a variable, enclose the string value in quotation marks, as follows:</span></span>

```powershell
$a = "baseball"
```

<span data-ttu-id="c4765-160">Pour assigner un tableau (plusieurs valeurs) à une variable, séparez les valeurs par des virgules, comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4765-160">To assign an array (multiple values) to a variable, separate the values with commas, as follows:</span></span>

```powershell
$a = "apple", "orange", "lemon", "grape"
```

<span data-ttu-id="c4765-161">Pour affecter une table de hachage à une variable, utilisez la notation de table de hachage standard dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4765-161">To assign a hash table to a variable, use the standard hash table notation in PowerShell.</span></span> <span data-ttu-id="c4765-162">Tapez un arobase `@` suivi de paires clé/valeur séparées par des points-virgules `;` et placées entre accolades `{ }` .</span><span class="sxs-lookup"><span data-stu-id="c4765-162">Type an at sign `@` followed by key/value pairs that are separated by semicolons `;` and enclosed in braces `{ }`.</span></span> <span data-ttu-id="c4765-163">Par exemple, pour affecter une table de hachage à la `$a` variable, tapez :</span><span class="sxs-lookup"><span data-stu-id="c4765-163">For example, to assign a hash table to the `$a` variable, type:</span></span>

```powershell
$a = @{one=1; two=2; three=3}
```

<span data-ttu-id="c4765-164">Pour assigner des valeurs hexadécimales à une variable, faites précéder la valeur de `0x` .</span><span class="sxs-lookup"><span data-stu-id="c4765-164">To assign hexadecimal values to a variable, precede the value with `0x`.</span></span>
<span data-ttu-id="c4765-165">PowerShell convertit la valeur hexadécimale (0x10) en valeur décimale (dans ce cas, 16) et assigne cette valeur à la `$a` variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-165">PowerShell converts the hexadecimal value (0x10) to a decimal value (in this case, 16) and assigns that value to the `$a` variable.</span></span> <span data-ttu-id="c4765-166">Par exemple, pour affecter une valeur de 0x10 à la `$a` variable, tapez :</span><span class="sxs-lookup"><span data-stu-id="c4765-166">For example, to assign a value of 0x10 to the `$a` variable, type:</span></span>

```powershell
$a = 0x10
```

<span data-ttu-id="c4765-167">Pour assigner une valeur exponentielle à une variable, tapez le numéro racine, la lettre `e` et un nombre qui représente un multiple de 10.</span><span class="sxs-lookup"><span data-stu-id="c4765-167">To assign an exponential value to a variable, type the root number, the letter `e`, and a number that represents a multiple of 10.</span></span> <span data-ttu-id="c4765-168">Par exemple, pour affecter la valeur 3,1415 à la puissance 1 000 à la `$a` variable, tapez :</span><span class="sxs-lookup"><span data-stu-id="c4765-168">For example, to assign a value of 3.1415 to the power of 1,000 to the `$a` variable, type:</span></span>

```powershell
$a = 3.1415e3
```

<span data-ttu-id="c4765-169">PowerShell peut également convertir des kilo-octets `KB` , des mégaoctets `MB` et des gigaoctets `GB` en octets.</span><span class="sxs-lookup"><span data-stu-id="c4765-169">PowerShell can also convert kilobytes `KB`, megabytes `MB`, and gigabytes `GB` into bytes.</span></span> <span data-ttu-id="c4765-170">Par exemple, pour affecter une valeur de 10 kilo-octets à la `$a` variable, tapez :</span><span class="sxs-lookup"><span data-stu-id="c4765-170">For example, to assign a value of 10 kilobytes to the `$a` variable, type:</span></span>

```powershell
$a = 10kb
```

### <a name="the-assignment-by-addition-operator"></a><span data-ttu-id="c4765-171">Assignation par l’opérateur d’addition</span><span class="sxs-lookup"><span data-stu-id="c4765-171">The assignment by addition operator</span></span>

<span data-ttu-id="c4765-172">L’opérateur d’assignation d’addition `+=` incrémente la valeur d’une variable ou ajoute la valeur spécifiée à la valeur existante.</span><span class="sxs-lookup"><span data-stu-id="c4765-172">The assignment by addition operator `+=` either increments the value of a variable or appends the specified value to the existing value.</span></span> <span data-ttu-id="c4765-173">L’action varie selon que la variable a un type numérique ou chaîne et si la variable contient une valeur unique (une valeur scalaire) ou plusieurs valeurs (une collection).</span><span class="sxs-lookup"><span data-stu-id="c4765-173">The action depends on whether the variable has a numeric or string type and whether the variable contains a single value (a scalar) or multiple values (a collection).</span></span>

<span data-ttu-id="c4765-174">L' `+=` opérateur combine deux opérations.</span><span class="sxs-lookup"><span data-stu-id="c4765-174">The `+=` operator combines two operations.</span></span> <span data-ttu-id="c4765-175">Tout d’abord, il ajoute, puis il affecte.</span><span class="sxs-lookup"><span data-stu-id="c4765-175">First, it adds, and then it assigns.</span></span>
<span data-ttu-id="c4765-176">Par conséquent, les instructions suivantes sont équivalentes :</span><span class="sxs-lookup"><span data-stu-id="c4765-176">Therefore, the following statements are equivalent:</span></span>

```powershell
$a += 2
$a = ($a + 2)
```

<span data-ttu-id="c4765-177">Lorsque la variable contient une valeur numérique unique, l' `+=` opérateur incrémente la valeur existante de la valeur du côté droit de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="c4765-177">When the variable contains a single numeric value, the `+=` operator increments the existing value by the amount on the right side of the operator.</span></span> <span data-ttu-id="c4765-178">L’opérateur assigne ensuite la valeur résultante à la variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-178">Then, the operator assigns the resulting value to the variable.</span></span> <span data-ttu-id="c4765-179">L’exemple suivant montre comment utiliser l' `+=` opérateur pour augmenter la valeur d’une variable :</span><span class="sxs-lookup"><span data-stu-id="c4765-179">The following example shows how to use the `+=` operator to increase the value of a variable:</span></span>

```powershell
$a = 4
$a += 2
$a
```

```
6
```

<span data-ttu-id="c4765-180">Lorsque la valeur de la variable est une chaîne, la valeur située à droite de l’opérateur est ajoutée à la chaîne, comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4765-180">When the value of the variable is a string, the value on the right side of the operator is appended to the string, as follows:</span></span>

```powershell
$a = "Windows"
$a += " PowerShell"
$a
```

```
Windows PowerShell
```

<span data-ttu-id="c4765-181">Lorsque la valeur de la variable est un tableau, l' `+=` opérateur ajoute les valeurs du côté droit de l’opérateur au tableau.</span><span class="sxs-lookup"><span data-stu-id="c4765-181">When the value of the variable is an array, the `+=` operator appends the values on the right side of the operator to the array.</span></span> <span data-ttu-id="c4765-182">À moins que le tableau ne soit explicitement typé par Cast, vous pouvez ajouter n’importe quel type de valeur au tableau, comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4765-182">Unless the array is explicitly typed by casting, you can append any type of value to the array, as follows:</span></span>

```powershell
$a = 1,2,3
$a += 2
$a
```

```
1
2
3
2
```

<span data-ttu-id="c4765-183">et</span><span class="sxs-lookup"><span data-stu-id="c4765-183">and</span></span>

```powershell
$a += "String"
$a
```

```
1
2
3
2
String
```

<span data-ttu-id="c4765-184">Lorsque la valeur d’une variable est une table de hachage, l' `+=` opérateur ajoute la valeur située à droite de l’opérateur à la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="c4765-184">When the value of a variable is a hash table, the `+=` operator appends the value on the right side of the operator to the hash table.</span></span> <span data-ttu-id="c4765-185">Toutefois, étant donné que le seul type que vous pouvez ajouter à une table de hachage est une autre table de hachage, toutes les autres affectations échouent.</span><span class="sxs-lookup"><span data-stu-id="c4765-185">However, because the only type that you can add to a hash table is another hash table, all other assignments fail.</span></span>

<span data-ttu-id="c4765-186">Par exemple, la commande suivante affecte une table de hachage à la `$a` variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-186">For example, the following command assigns a hash table to the `$a` variable.</span></span>
<span data-ttu-id="c4765-187">Ensuite, il utilise l' `+=` opérateur pour ajouter une autre table de hachage à la table de hachage existante, en ajoutant une nouvelle paire clé/valeur à la table de hachage existante.</span><span class="sxs-lookup"><span data-stu-id="c4765-187">Then, it uses the `+=` operator to append another hash table to the existing hash table, effectively adding a new key/value pair to the existing hash table.</span></span>
<span data-ttu-id="c4765-188">Cette commande fonctionne correctement, comme indiqué dans la sortie :</span><span class="sxs-lookup"><span data-stu-id="c4765-188">This command succeeds, as shown in the output:</span></span>

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += @{mode = "write"}
$a
```

```
Name                           Value
----                           -----
a                              1
b                              2
mode                           write
c                              3
```

<span data-ttu-id="c4765-189">La commande suivante tente d’ajouter un entier « 1 » à la table de hachage dans la `$a` variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-189">The following command attempts to append an integer "1" to the hash table in the `$a` variable.</span></span> <span data-ttu-id="c4765-190">Échec de cette commande :</span><span class="sxs-lookup"><span data-stu-id="c4765-190">This command fails:</span></span>

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += 1
```

```
You can add another hash table only to a hash table.
At line:1 char:6
+ $a += <<<<  1
```

### <a name="the-assignment-by-subtraction-operator"></a><span data-ttu-id="c4765-191">Assignation par l’opérateur de soustraction</span><span class="sxs-lookup"><span data-stu-id="c4765-191">The assignment by subtraction operator</span></span>

<span data-ttu-id="c4765-192">L’opérateur d’assignation par soustraction `-=` décrémente la valeur d’une variable en fonction de la valeur spécifiée sur le côté droit de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="c4765-192">The assignment by subtraction operator `-=` decrements the value of a variable by the value that is specified on the right side of the operator.</span></span> <span data-ttu-id="c4765-193">Cet opérateur ne peut pas être utilisé avec des variables de chaîne et ne peut pas être utilisé pour supprimer un élément d’une collection.</span><span class="sxs-lookup"><span data-stu-id="c4765-193">This operator cannot be used with string variables, and it cannot be used to remove an element from a collection.</span></span>

<span data-ttu-id="c4765-194">L' `-=` opérateur combine deux opérations.</span><span class="sxs-lookup"><span data-stu-id="c4765-194">The `-=` operator combines two operations.</span></span> <span data-ttu-id="c4765-195">En premier lieu, il soustrait, puis il affecte.</span><span class="sxs-lookup"><span data-stu-id="c4765-195">First, it subtracts, and then it assigns.</span></span> <span data-ttu-id="c4765-196">Par conséquent, les instructions suivantes sont équivalentes :</span><span class="sxs-lookup"><span data-stu-id="c4765-196">Therefore, the following statements are equivalent:</span></span>

```powershell
$a -= 2
$a = ($a - 2)
```

<span data-ttu-id="c4765-197">L’exemple suivant montre comment utiliser l' `-=` opérateur pour réduire la valeur d’une variable :</span><span class="sxs-lookup"><span data-stu-id="c4765-197">The following example shows how to use of the `-=` operator to decrease the value of a variable:</span></span>

```powershell
$a = 8
$a -= 2
$a
```

```
6
```

<span data-ttu-id="c4765-198">Vous pouvez également utiliser l' `-=` opérateur d’assignation pour réduire la valeur d’un membre d’un tableau numérique.</span><span class="sxs-lookup"><span data-stu-id="c4765-198">You can also use the `-=` assignment operator to decrease the value of a member of a numeric array.</span></span> <span data-ttu-id="c4765-199">Pour ce faire, spécifiez l’index de l’élément de tableau que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="c4765-199">To do this, specify the index of the array element that you want to change.</span></span> <span data-ttu-id="c4765-200">Dans l’exemple suivant, la valeur du troisième élément d’un tableau (élément 2) est diminuée de 1 :</span><span class="sxs-lookup"><span data-stu-id="c4765-200">In the following example, the value of the third element of an array (element 2) is decreased by 1:</span></span>

```powershell
$a = 1,2,3
$a[2] -= 1
$a
```

```
1
2
2
```

<span data-ttu-id="c4765-201">Vous ne pouvez pas utiliser l' `-=` opérateur pour supprimer les valeurs d’une variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-201">You cannot use the `-=` operator to delete the values of a variable.</span></span> <span data-ttu-id="c4765-202">Pour supprimer toutes les valeurs assignées à une variable, utilisez les applets de [commande Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item) ou [Clear-variable](xref:Microsoft.PowerShell.Utility.Clear-Variable) pour affecter une valeur de `$null` ou `""` à la variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-202">To delete all the values that are assigned to a variable, use the [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item) or [Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable) cmdlets to assign a value of `$null` or `""` to the variable.</span></span>

```powershell
$a = $null
```

<span data-ttu-id="c4765-203">Pour supprimer une valeur particulière d’un tableau, utilisez la notation de tableau pour assigner une valeur `$null` à l’élément particulier.</span><span class="sxs-lookup"><span data-stu-id="c4765-203">To delete a particular value from an array, use array notation to assign a value of `$null` to the particular item.</span></span> <span data-ttu-id="c4765-204">Par exemple, l’instruction suivante supprime la deuxième valeur (position d’index 1) d’un tableau :</span><span class="sxs-lookup"><span data-stu-id="c4765-204">For example, the following statement deletes the second value (index position 1) from an array:</span></span>

```powershell
$a = 1,2,3
$a
```

```
1
2
3
```

```powershell
$a[1] = $null
$a
```

```
1
3
```

<span data-ttu-id="c4765-205">Pour supprimer une variable, utilisez l’applet de commande [Remove-variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) .</span><span class="sxs-lookup"><span data-stu-id="c4765-205">To delete a variable, use the [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) cmdlet.</span></span> <span data-ttu-id="c4765-206">Cette méthode est utile lorsque la variable est explicitement convertie en un type de données particulier et que vous souhaitez une variable non typée.</span><span class="sxs-lookup"><span data-stu-id="c4765-206">This method is useful when the variable is explicitly cast to a particular data type, and you want an untyped variable.</span></span> <span data-ttu-id="c4765-207">La commande suivante supprime la `$a` variable :</span><span class="sxs-lookup"><span data-stu-id="c4765-207">The following command deletes the `$a` variable:</span></span>

```powershell
Remove-Variable -Name a
```

### <a name="the-assignment-by-multiplication-operator"></a><span data-ttu-id="c4765-208">Assignation par opérateur de multiplication</span><span class="sxs-lookup"><span data-stu-id="c4765-208">The assignment by multiplication operator</span></span>

<span data-ttu-id="c4765-209">L’opérateur d’assignation par multiplication `*=` multiplie une valeur numérique ou ajoute le nombre spécifié de copies de la valeur de chaîne d’une variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-209">The assignment by multiplication operator `*=` multiplies a numeric value or appends the specified number of copies of the string value of a variable.</span></span>

<span data-ttu-id="c4765-210">Lorsqu’une variable contient une valeur numérique unique, cette valeur est multipliée par la valeur située à droite de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="c4765-210">When a variable contains a single numeric value, that value is multiplied by the value on the right side of the operator.</span></span> <span data-ttu-id="c4765-211">Par exemple, l’exemple suivant montre comment utiliser l' `*=` opérateur pour multiplier la valeur d’une variable :</span><span class="sxs-lookup"><span data-stu-id="c4765-211">For example, the following example shows how to use the `*=` operator to multiply the value of a variable:</span></span>

```powershell
$a = 3
$a *= 4
$a
```

```
12
```

<span data-ttu-id="c4765-212">Dans ce cas, l' `*=` opérateur combine deux opérations.</span><span class="sxs-lookup"><span data-stu-id="c4765-212">In this case, the `*=` operator combines two operations.</span></span> <span data-ttu-id="c4765-213">Tout d’abord, il multiplie, puis l’assigne.</span><span class="sxs-lookup"><span data-stu-id="c4765-213">First, it multiplies, and then it assigns.</span></span> <span data-ttu-id="c4765-214">Par conséquent, les instructions suivantes sont équivalentes :</span><span class="sxs-lookup"><span data-stu-id="c4765-214">Therefore, the following statements are equivalent:</span></span>

```powershell
$a *= 2
$a = ($a * 2)
```

<span data-ttu-id="c4765-215">Lorsqu’une variable contient une valeur de chaîne, PowerShell ajoute le nombre spécifié de chaînes à la valeur, comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4765-215">When a variable contains a string value, PowerShell appends the specified number of strings to the value, as follows:</span></span>

```powershell
$a = "file"
$a *= 4
$a
```

```
filefilefilefile
```

<span data-ttu-id="c4765-216">Pour multiplier un élément d’un tableau, utilisez un index pour identifier l’élément que vous souhaitez multiplier.</span><span class="sxs-lookup"><span data-stu-id="c4765-216">To multiply an element of an array, use an index to identify the element that you want to multiply.</span></span> <span data-ttu-id="c4765-217">Par exemple, la commande suivante multiplie le premier élément du tableau (position d’index 0) par 2 :</span><span class="sxs-lookup"><span data-stu-id="c4765-217">For example, the following command multiplies the first element in the array (index position 0) by 2:</span></span>

```powershell
$a[0] *= 2
```

### <a name="the-assignment-by-division-operator"></a><span data-ttu-id="c4765-218">Opérateur d’assignation par division</span><span class="sxs-lookup"><span data-stu-id="c4765-218">The assignment by division operator</span></span>

<span data-ttu-id="c4765-219">L’opérateur Assignment par division `/=` divise une valeur numérique par la valeur spécifiée sur le côté droit de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="c4765-219">The assignment by division operator `/=` divides a numeric value by the value that is specified on the right side of the operator.</span></span> <span data-ttu-id="c4765-220">L’opérateur ne peut pas être utilisé avec des variables de chaîne.</span><span class="sxs-lookup"><span data-stu-id="c4765-220">The operator cannot be used with string variables.</span></span>

<span data-ttu-id="c4765-221">L' `/=` opérateur combine deux opérations.</span><span class="sxs-lookup"><span data-stu-id="c4765-221">The `/=` operator combines two operations.</span></span> <span data-ttu-id="c4765-222">Tout d’abord, elle est divisée, puis assignée.</span><span class="sxs-lookup"><span data-stu-id="c4765-222">First, it divides, and then it assigns.</span></span> <span data-ttu-id="c4765-223">Par conséquent, les deux instructions suivantes sont équivalentes :</span><span class="sxs-lookup"><span data-stu-id="c4765-223">Therefore, the following two statements are equivalent:</span></span>

```powershell
$a /= 2
$a = ($a / 2)
```

<span data-ttu-id="c4765-224">Par exemple, la commande suivante utilise l' `/=` opérateur pour diviser la valeur d’une variable :</span><span class="sxs-lookup"><span data-stu-id="c4765-224">For example, the following command uses the `/=` operator to divide the value of a variable:</span></span>

```powershell
$a = 8
$a /=2
$a
```

```
4
```

<span data-ttu-id="c4765-225">Pour diviser un élément d’un tableau, utilisez un index pour identifier l’élément que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="c4765-225">To divide an element of an array, use an index to identify the element that you want to change.</span></span> <span data-ttu-id="c4765-226">Par exemple, la commande suivante divise le deuxième élément du tableau (position d’index 1) par 2 :</span><span class="sxs-lookup"><span data-stu-id="c4765-226">For example, the following command divides the second element in the array (index position 1) by 2:</span></span>

```powershell
$a[1] /= 2
```

### <a name="the-assignment-by-modulus-operator"></a><span data-ttu-id="c4765-227">L’opérateur d’assignation par Modulo</span><span class="sxs-lookup"><span data-stu-id="c4765-227">The assignment by modulus operator</span></span>

<span data-ttu-id="c4765-228">L’opérateur d’assignation par Modulo `%=` divise la valeur d’une variable par la valeur située à droite de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="c4765-228">The assignment by modulus operator `%=` divides the value of a variable by the value on the right side of the operator.</span></span> <span data-ttu-id="c4765-229">L' `%=` opérateur assigne ensuite le reste (appelé modulo) à la variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-229">Then, the `%=` operator assigns the remainder (known as the modulus) to the variable.</span></span> <span data-ttu-id="c4765-230">Vous pouvez utiliser cet opérateur uniquement lorsqu’une variable contient une valeur numérique unique.</span><span class="sxs-lookup"><span data-stu-id="c4765-230">You can use this operator only when a variable contains a single numeric value.</span></span> <span data-ttu-id="c4765-231">Vous ne pouvez pas utiliser cet opérateur quand une variable contient une variable de chaîne ou un tableau.</span><span class="sxs-lookup"><span data-stu-id="c4765-231">You cannot use this operator when a variable contains a string variable or an array.</span></span>

<span data-ttu-id="c4765-232">L' `%=` opérateur combine deux opérations.</span><span class="sxs-lookup"><span data-stu-id="c4765-232">The `%=` operator combines two operations.</span></span> <span data-ttu-id="c4765-233">Tout d’abord, il divise et détermine le reste, puis il assigne le reste à la variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-233">First, it divides and determines the remainder, and then it assigns the remainder to the variable.</span></span> <span data-ttu-id="c4765-234">Par conséquent, les instructions suivantes sont équivalentes :</span><span class="sxs-lookup"><span data-stu-id="c4765-234">Therefore, the following statements are equivalent:</span></span>

```powershell
$a %= 2
$a = ($a % 2)
```

<span data-ttu-id="c4765-235">L’exemple suivant montre comment utiliser l' `%=` opérateur pour enregistrer le modulo d’un quotient :</span><span class="sxs-lookup"><span data-stu-id="c4765-235">The following example shows how to use the `%=` operator to save the modulus of a quotient:</span></span>

```powershell
$a = 7
$a %= 4
$a
```

```
3
```

## <a name="the-increment-and-decrement-operators"></a><span data-ttu-id="c4765-236">Opérateurs d’incrémentation et de décrémentation</span><span class="sxs-lookup"><span data-stu-id="c4765-236">The increment and decrement operators</span></span>

<span data-ttu-id="c4765-237">L’opérateur `++` d’incrément augmente la valeur d’une variable de 1.</span><span class="sxs-lookup"><span data-stu-id="c4765-237">The increment operator `++` increases the value of a variable by 1.</span></span> <span data-ttu-id="c4765-238">Lorsque vous utilisez l’opérateur d’incrément dans une instruction simple, aucune valeur n’est retournée.</span><span class="sxs-lookup"><span data-stu-id="c4765-238">When you use the increment operator in a simple statement, no value is returned.</span></span> <span data-ttu-id="c4765-239">Pour afficher le résultat, affichez la valeur de la variable, comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4765-239">To view the result, display the value of the variable, as follows:</span></span>

```powershell
$a = 7
++$a
$a
```

```
8
```

<span data-ttu-id="c4765-240">Pour forcer le retour d’une valeur, placez la variable et l’opérateur entre parenthèses, comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4765-240">To force a value to be returned, enclose the variable and the operator in parentheses, as follows:</span></span>

```powershell
$a = 7
(++$a)
```

```
8
```

<span data-ttu-id="c4765-241">L’opérateur d’incrément peut être placé avant (préfixe) ou après (postfix) une variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-241">The increment operator can be placed before (prefix) or after (postfix) a variable.</span></span> <span data-ttu-id="c4765-242">La version préfixée de l’opérateur incrémente une variable avant que sa valeur ne soit utilisée dans l’instruction, comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4765-242">The prefix version of the operator increments a variable before its value is used in the statement, as follows:</span></span>

```powershell
$a = 7
$c = ++$a
$a
```

```
8
```

```powershell
$c
```

```
8
```

<span data-ttu-id="c4765-243">La version suffixée de l’opérateur incrémente une variable une fois que sa valeur est utilisée dans l’instruction.</span><span class="sxs-lookup"><span data-stu-id="c4765-243">The postfix version of the operator increments a variable after its value is used in the statement.</span></span> <span data-ttu-id="c4765-244">Dans l’exemple suivant, les `$c` `$a` variables et ont des valeurs différentes, car la valeur est assignée à `$c` avant `$a` les modifications :</span><span class="sxs-lookup"><span data-stu-id="c4765-244">In the following example, the `$c` and `$a` variables have different values because the value is assigned to `$c` before `$a` changes:</span></span>

```powershell
$a = 7
$c = $a++
$a
```

```
8
```

```powershell
$c
```

```
7
```

<span data-ttu-id="c4765-245">L’opérateur `--` de décrémentation réduit la valeur d’une variable de 1.</span><span class="sxs-lookup"><span data-stu-id="c4765-245">The decrement operator `--` decreases the value of a variable by 1.</span></span> <span data-ttu-id="c4765-246">Comme avec l’opérateur d’incrémentation, aucune valeur n’est retournée lorsque vous utilisez l’opérateur dans une instruction simple.</span><span class="sxs-lookup"><span data-stu-id="c4765-246">As with the increment operator, no value is returned when you use the operator in a simple statement.</span></span> <span data-ttu-id="c4765-247">Utilisez des parenthèses pour retourner une valeur, comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4765-247">Use parentheses to return a value, as follows:</span></span>

```powershell
$a = 7
--$a
$a
```

```
6
```

```powershell
(--$a)
```

```
5
```

<span data-ttu-id="c4765-248">La version préfixée de l’opérateur décrémente une variable avant que sa valeur ne soit utilisée dans l’instruction, comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4765-248">The prefix version of the operator decrements a variable before its value is used in the statement, as follows:</span></span>

```powershell
$a = 7
$c = --$a
$a
```

```
6
```

```powershell
$c
```

```
6
```

<span data-ttu-id="c4765-249">La version suffixée de l’opérateur décrémente une variable une fois que sa valeur est utilisée dans l’instruction.</span><span class="sxs-lookup"><span data-stu-id="c4765-249">The postfix version of the operator decrements a variable after its value is used in the statement.</span></span> <span data-ttu-id="c4765-250">Dans l’exemple suivant, les `$d` `$a` variables et ont des valeurs différentes, car la valeur est assignée à `$d` avant `$a` les modifications :</span><span class="sxs-lookup"><span data-stu-id="c4765-250">In the following example, the `$d` and `$a` variables have different values because the value is assigned to `$d` before `$a` changes:</span></span>

```powershell
$a = 7
$d = $a--
$a
```

```
6
```

```powershell
$d
```

```
7
```

## <a name="microsoft-net-framework-types"></a><span data-ttu-id="c4765-251">Types de Framework Microsoft .NET</span><span class="sxs-lookup"><span data-stu-id="c4765-251">Microsoft .NET Framework types</span></span>

<span data-ttu-id="c4765-252">Par défaut, lorsqu’une variable n’a qu’une seule valeur, la valeur assignée à la variable détermine le type de données de la variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-252">By default, when a variable has only one value, the value that is assigned to the variable determines the data type of the variable.</span></span> <span data-ttu-id="c4765-253">Par exemple, la commande suivante crée une variable qui a le type « Integer » (System. Int32) :</span><span class="sxs-lookup"><span data-stu-id="c4765-253">For example, the following command creates a variable that has the "Integer" (System.Int32) type:</span></span>

```powershell
$a = 6
```

<span data-ttu-id="c4765-254">Pour rechercher le type de .NET Framework d’une variable, utilisez la méthode **GetType** et sa propriété **FullName** , comme suit.</span><span class="sxs-lookup"><span data-stu-id="c4765-254">To find the .NET Framework type of a variable, use the **GetType** method and its **FullName** property, as follows.</span></span> <span data-ttu-id="c4765-255">Veillez à inclure les parenthèses après le nom de la méthode **GetType** , même si l’appel de la méthode n’a pas d’argument :</span><span class="sxs-lookup"><span data-stu-id="c4765-255">Be sure to include the parentheses after the **GetType** method name, even though the method call has no arguments:</span></span>

```powershell
$a = 6
$a.GetType().FullName
```

```
System.Int32
```

<span data-ttu-id="c4765-256">Pour créer une variable qui contient une chaîne, assignez une valeur de chaîne à la variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-256">To create a variable that contains a string, assign a string value to the variable.</span></span> <span data-ttu-id="c4765-257">Pour indiquer que la valeur est une chaîne, mettez-la entre guillemets, comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4765-257">To indicate that the value is a string, enclose it in quotation marks, as follows:</span></span>

```powershell
$a = "6"
$a.GetType().FullName
```

```
System.String
```

<span data-ttu-id="c4765-258">Si la première valeur assignée à la variable est une chaîne, PowerShell traite toutes les opérations comme des opérations de chaîne et convertit les nouvelles valeurs en chaînes.</span><span class="sxs-lookup"><span data-stu-id="c4765-258">If the first value that is assigned to the variable is a string, PowerShell treats all operations as string operations and casts new values to strings.</span></span>
<span data-ttu-id="c4765-259">Cela se produit dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c4765-259">This occurs in the following example:</span></span>

```powershell
$a = "file"
$a += 3
$a
```

```
file3
```

<span data-ttu-id="c4765-260">Si la première valeur est un entier, PowerShell traite toutes les opérations comme des opérations d’entiers et convertit les nouvelles valeurs en entiers.</span><span class="sxs-lookup"><span data-stu-id="c4765-260">If the first value is an integer, PowerShell treats all operations as integer operations and casts new values to integers.</span></span> <span data-ttu-id="c4765-261">Cela se produit dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c4765-261">This occurs in the following example:</span></span>

```powershell
$a = 6
$a += "3"
$a
```

```
9
```

<span data-ttu-id="c4765-262">Vous pouvez effectuer un cast d’une nouvelle variable scalaire en tout type de .NET Framework en plaçant le nom du type entre crochets qui précèdent le nom de la variable ou la première valeur de l’affectation.</span><span class="sxs-lookup"><span data-stu-id="c4765-262">You can cast a new scalar variable as any .NET Framework type by placing the type name in brackets that precede either the variable name or the first assignment value.</span></span> <span data-ttu-id="c4765-263">Lorsque vous effectuez un cast d’une variable, vous pouvez déterminer les types de données qui peuvent être stockés dans la variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-263">When you cast a variable, you can determine the types of data that can be stored in the variable.</span></span> <span data-ttu-id="c4765-264">Et vous pouvez déterminer le comportement de la variable lorsque vous la manipulez.</span><span class="sxs-lookup"><span data-stu-id="c4765-264">And, you can determine how the variable behaves when you manipulate it.</span></span>

<span data-ttu-id="c4765-265">Par exemple, la commande suivante convertit la variable en type chaîne :</span><span class="sxs-lookup"><span data-stu-id="c4765-265">For example, the following command casts the variable as a string type:</span></span>

```powershell
[string]$a = 27
$a += 3
$a
```

```
273
```

<span data-ttu-id="c4765-266">L’exemple suivant convertit la première valeur, au lieu de convertir la variable :</span><span class="sxs-lookup"><span data-stu-id="c4765-266">The following example casts the first value, instead of casting the variable:</span></span>

```powershell
$a = [string]27
```

<span data-ttu-id="c4765-267">Lorsque vous effectuez un cast d’une variable en un type spécifique, la Convention courante consiste à effectuer un cast de la variable, et non la valeur.</span><span class="sxs-lookup"><span data-stu-id="c4765-267">When you cast a variable to a specific type, the common convention is to cast the variable, not the value.</span></span> <span data-ttu-id="c4765-268">Toutefois, vous ne pouvez pas reconvertir le type de données d’une variable existante si sa valeur ne peut pas être convertie dans le nouveau type de données.</span><span class="sxs-lookup"><span data-stu-id="c4765-268">However, you cannot recast the data type of an existing variable if its value cannot be converted to the new data type.</span></span> <span data-ttu-id="c4765-269">Pour modifier le type de données, vous devez remplacer sa valeur, comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4765-269">To change the data type, you must replace its value, as follows:</span></span>

```powershell
$a = "string"
[int]$a
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input string was
not in a correct format." At line:1 char:8 + [int]$a <<<<
```

```powershell
[int]$a = 3
```

<span data-ttu-id="c4765-270">En outre, lorsque vous faites précéder un nom de variable d’un type de données, le type de cette variable est verrouillé, sauf si vous substituez explicitement le type en spécifiant un autre type de données.</span><span class="sxs-lookup"><span data-stu-id="c4765-270">In addition, when you precede a variable name with a data type, the type of that variable is locked unless you explicitly override the type by specifying another data type.</span></span> <span data-ttu-id="c4765-271">Si vous essayez d’assigner une valeur qui n’est pas compatible avec le type existant et que vous ne substituez pas explicitement le type, PowerShell affiche une erreur, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c4765-271">If you try to assign a value that is incompatible with the existing type, and you do not explicitly override the type, PowerShell displays an error, as shown in the following example:</span></span>

```powershell
$a = 3
$a = "string"
[int]$a = 3
$a = "string"
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input
string was not in a correct format."
At line:1 char:3
+ $a <<<<  = "string"
```

```powershell
[string]$a = "string"
```

<span data-ttu-id="c4765-272">Dans PowerShell, les types de données des variables qui contiennent plusieurs éléments d’un tableau sont gérés différemment des types de données des variables qui contiennent un seul élément.</span><span class="sxs-lookup"><span data-stu-id="c4765-272">In PowerShell, the data types of variables that contain multiple items in an array are handled differently from the data types of variables that contain a single item.</span></span> <span data-ttu-id="c4765-273">À moins qu’un type de données ne soit spécifiquement affecté à une variable tableau, le type de données est toujours `System.Object []` .</span><span class="sxs-lookup"><span data-stu-id="c4765-273">Unless a data type is specifically assigned to an array variable, the data type is always `System.Object []`.</span></span> <span data-ttu-id="c4765-274">Ce type de données est spécifique aux tableaux.</span><span class="sxs-lookup"><span data-stu-id="c4765-274">This data type is specific to arrays.</span></span>

<span data-ttu-id="c4765-275">Parfois, vous pouvez remplacer le type par défaut en spécifiant un autre type.</span><span class="sxs-lookup"><span data-stu-id="c4765-275">Sometimes, you can override the default type by specifying another type.</span></span> <span data-ttu-id="c4765-276">Par exemple, la commande suivante convertit la variable en `string []` type de tableau :</span><span class="sxs-lookup"><span data-stu-id="c4765-276">For example, the following command casts the variable as a `string []` array type:</span></span>

```powershell
[string []] $a = "one", "two", "three"
```

<span data-ttu-id="c4765-277">Les variables PowerShell peuvent être n’importe quel type de données .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4765-277">PowerShell variables can be any .NET Framework data type.</span></span> <span data-ttu-id="c4765-278">En outre, vous pouvez assigner n’importe quel type de données .NET Framework complet disponible dans le processus actuel.</span><span class="sxs-lookup"><span data-stu-id="c4765-278">In addition, you can assign any fully qualified .NET Framework data type that is available in the current process.</span></span> <span data-ttu-id="c4765-279">Par exemple, la commande suivante spécifie un `System.DateTime` type de données :</span><span class="sxs-lookup"><span data-stu-id="c4765-279">For example, the following command specifies a `System.DateTime` data type:</span></span>

```powershell
[System.DateTime]$a = "5/31/2005"
```

<span data-ttu-id="c4765-280">Une valeur conforme au type de données est assignée à la variable `System.DateTime` .</span><span class="sxs-lookup"><span data-stu-id="c4765-280">The variable will be assigned a value that conforms to the `System.DateTime` data type.</span></span> <span data-ttu-id="c4765-281">La valeur de la `$a` variable est la suivante :</span><span class="sxs-lookup"><span data-stu-id="c4765-281">The value of the `$a` variable would be the following:</span></span>

```
Tuesday, May 31, 2005 12:00:00 AM
```

## <a name="assigning-multiple-variables"></a><span data-ttu-id="c4765-282">Assignation de plusieurs variables</span><span class="sxs-lookup"><span data-stu-id="c4765-282">Assigning multiple variables</span></span>

<span data-ttu-id="c4765-283">Dans PowerShell, vous pouvez assigner des valeurs à plusieurs variables à l’aide d’une seule commande.</span><span class="sxs-lookup"><span data-stu-id="c4765-283">In PowerShell, you can assign values to multiple variables by using a single command.</span></span> <span data-ttu-id="c4765-284">Le premier élément de la valeur d’assignation est assigné à la première variable, le deuxième élément est assigné à la deuxième variable, le troisième élément à la troisième variable, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="c4765-284">The first element of the assignment value is assigned to the first variable, the second element is assigned to the second variable, the third element to the third variable, and so on.</span></span> <span data-ttu-id="c4765-285">Par exemple, la commande suivante affecte la valeur 1 à la `$a` variable, la valeur 2 à la `$b` variable et la valeur 3 à la `$c` variable :</span><span class="sxs-lookup"><span data-stu-id="c4765-285">For example, the following command assigns the value 1 to the `$a` variable, the value 2 to the `$b` variable, and the value 3 to the `$c` variable:</span></span>

```powershell
$a, $b, $c = 1, 2, 3
```

<span data-ttu-id="c4765-286">Si la valeur d’affectation contient plus d’éléments que de variables, toutes les valeurs restantes sont affectées à la dernière variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-286">If the assignment value contains more elements than variables, all the remaining values are assigned to the last variable.</span></span> <span data-ttu-id="c4765-287">Par exemple, la commande suivante contient trois variables et cinq valeurs :</span><span class="sxs-lookup"><span data-stu-id="c4765-287">For example, the following command contains three variables and five values:</span></span>

```powershell
$a, $b, $c = 1, 2, 3, 4, 5
```

<span data-ttu-id="c4765-288">Par conséquent, PowerShell affecte la valeur 1 à la `$a` variable et la valeur 2 à la `$b` variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-288">Therefore, PowerShell assigns the value 1 to the `$a` variable and the value 2 to the `$b` variable.</span></span> <span data-ttu-id="c4765-289">Elle affecte les valeurs 3, 4 et 5 à la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-289">It assigns the values 3, 4, and 5 to the `$c` variable.</span></span>
<span data-ttu-id="c4765-290">Pour assigner les valeurs de la `$c` variable à trois autres variables, utilisez le format suivant :</span><span class="sxs-lookup"><span data-stu-id="c4765-290">To assign the values in the `$c` variable to three other variables, use the following format:</span></span>

```powershell
$d, $e, $f = $c
```

<span data-ttu-id="c4765-291">Cette commande affecte la valeur 3 à la `$d` variable, la valeur 4 à la `$e` variable et la valeur 5 à la `$f` variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-291">This command assigns the value 3 to the `$d` variable, the value 4 to the `$e` variable, and the value 5 to the `$f` variable.</span></span>

<span data-ttu-id="c4765-292">Si la valeur d’affectation contient moins d’éléments que de variables, aucune valeur n’est affectée à toutes les variables restantes à la fin.</span><span class="sxs-lookup"><span data-stu-id="c4765-292">If the assignment value contains less elements than variables, all the remaining variables at the end are not assigned any values.</span></span> <span data-ttu-id="c4765-293">Par exemple, la commande suivante contient trois variables et deux valeurs :</span><span class="sxs-lookup"><span data-stu-id="c4765-293">For example, the following command contains three variables and two values:</span></span>

```powershell
$a, $b, $c = 1, 2
```

<span data-ttu-id="c4765-294">Par conséquent, PowerShell affecte la valeur 1 à la `$a` variable et la valeur 2 à la `$b` variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-294">Therefore, PowerShell assigns the value 1 to the `$a` variable and the value 2 to the `$b` variable.</span></span> <span data-ttu-id="c4765-295">Aucune valeur n’est assignée à la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-295">It will not assign any value to the `$c` variable.</span></span>

<span data-ttu-id="c4765-296">Vous pouvez également assigner une valeur unique à plusieurs variables en les chaînageant.</span><span class="sxs-lookup"><span data-stu-id="c4765-296">You can also assign a single value to multiple variables by chaining the variables.</span></span> <span data-ttu-id="c4765-297">Par exemple, la commande suivante affecte une valeur « trois » aux quatre variables :</span><span class="sxs-lookup"><span data-stu-id="c4765-297">For example, the following command assigns a value of "three" to all four variables:</span></span>

```powershell
$a = $b = $c = $d = "three"
```

## <a name="variable-related-cmdlets"></a><span data-ttu-id="c4765-298">Applets de commande associées à une variable</span><span class="sxs-lookup"><span data-stu-id="c4765-298">Variable-related cmdlets</span></span>

<span data-ttu-id="c4765-299">Outre l’utilisation d’une opération d’assignation pour définir une valeur de variable, vous pouvez également utiliser l’applet de commande [Set-variable](xref:Microsoft.PowerShell.Utility.Set-Variable) .</span><span class="sxs-lookup"><span data-stu-id="c4765-299">In addition to using an assignment operation to set a variable value, you can also use the [Set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable) cmdlet.</span></span> <span data-ttu-id="c4765-300">Par exemple, la commande suivante utilise `Set-Variable` pour assigner un tableau de 1, 2, 3 à la `$a` variable.</span><span class="sxs-lookup"><span data-stu-id="c4765-300">For example, the following command uses `Set-Variable` to assign an array of 1, 2, 3 to the `$a` variable.</span></span>

```powershell
Set-Variable -Name a -Value 1, 2, 3
```

## <a name="see-also"></a><span data-ttu-id="c4765-301">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4765-301">See also</span></span>

[<span data-ttu-id="c4765-302">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="c4765-302">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="c4765-303">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="c4765-303">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="c4765-304">about_Variables</span><span class="sxs-lookup"><span data-stu-id="c4765-304">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="c4765-305">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="c4765-305">Clear-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Clear-Variable)

[<span data-ttu-id="c4765-306">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="c4765-306">Remove-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Remove-Variable)

[<span data-ttu-id="c4765-307">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="c4765-307">Set-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Set-Variable)
