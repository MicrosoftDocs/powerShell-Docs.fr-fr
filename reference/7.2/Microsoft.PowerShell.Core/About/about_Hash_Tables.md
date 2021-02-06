---
description: Décrit comment créer, utiliser et trier des tables de hachage dans PowerShell.
Locale: en-US
ms.date: 11/28/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hash_Tables
ms.openlocfilehash: dec2683acfa4fcf79419beea9e0840387d3d43d1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598343"
---
# <a name="about-hash-tables"></a><span data-ttu-id="7db9a-103">À propos des tables de hachage</span><span class="sxs-lookup"><span data-stu-id="7db9a-103">About Hash Tables</span></span>

## <a name="short-description"></a><span data-ttu-id="7db9a-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="7db9a-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="7db9a-105">Décrit comment créer, utiliser et trier des tables de hachage dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7db9a-105">Describes how to create, use, and sort hash tables in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="7db9a-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="7db9a-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="7db9a-107">Une table de hachage, également appelée un dictionnaire ou un tableau associatif, est une structure de données compacte qui stocke une ou plusieurs paires clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="7db9a-107">A hash table, also known as a dictionary or associative array, is a compact data structure that stores one or more key/value pairs.</span></span> <span data-ttu-id="7db9a-108">Par exemple, une table de hachage peut contenir une série d’adresses IP et de noms d’ordinateurs, où les adresses IP sont les clés et les noms d’ordinateur sont les valeurs, ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="7db9a-108">For example, a hash table might contain a series of IP addresses and computer names, where the IP addresses are the keys and the computer names are the values, or vice versa.</span></span>

<span data-ttu-id="7db9a-109">Dans PowerShell, chaque table de hachage est un objet Hashtable (System. Collections. Hashtable).</span><span class="sxs-lookup"><span data-stu-id="7db9a-109">In PowerShell, each hash table is a Hashtable (System.Collections.Hashtable) object.</span></span> <span data-ttu-id="7db9a-110">Vous pouvez utiliser les propriétés et les méthodes des objets Hashtable dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7db9a-110">You can use the properties and methods of Hashtable objects in PowerShell.</span></span>

<span data-ttu-id="7db9a-111">À compter de PowerShell 3,0, vous pouvez utiliser l’attribut [Ordered] pour créer un dictionnaire ordonné (System. Collections. Specialized. OrderedDictionary) dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7db9a-111">Beginning in PowerShell 3.0, you can use the [ordered] attribute to create an ordered dictionary (System.Collections.Specialized.OrderedDictionary) in PowerShell.</span></span>

<span data-ttu-id="7db9a-112">Les dictionnaires ordonnés diffèrent des tables de hachage dans le sens où les clés apparaissent toujours dans l’ordre dans lequel vous les répertoriez.</span><span class="sxs-lookup"><span data-stu-id="7db9a-112">Ordered dictionaries differ from hash tables in that the keys always appear in the order in which you list them.</span></span> <span data-ttu-id="7db9a-113">L’ordre des clés dans une table de hachage n’est pas déterminé.</span><span class="sxs-lookup"><span data-stu-id="7db9a-113">The order of keys in a hash table is not determined.</span></span>

<span data-ttu-id="7db9a-114">Les clés et la valeur des tables de hachage sont également des objets .NET.</span><span class="sxs-lookup"><span data-stu-id="7db9a-114">The keys and value in hash tables are also .NET objects.</span></span> <span data-ttu-id="7db9a-115">Ils sont le plus souvent des chaînes ou des entiers, mais ils peuvent avoir n’importe quel type d’objet.</span><span class="sxs-lookup"><span data-stu-id="7db9a-115">They are most often strings or integers, but they can have any object type.</span></span> <span data-ttu-id="7db9a-116">Vous pouvez également créer des tables de hachage imbriquées, dans lesquelles la valeur d’une clé est une autre table de hachage.</span><span class="sxs-lookup"><span data-stu-id="7db9a-116">You can also create nested hash tables, in which the value of a key is another hash table.</span></span>

<span data-ttu-id="7db9a-117">Les tables de hachage sont fréquemment utilisées, car elles sont très efficaces pour rechercher et récupérer des données.</span><span class="sxs-lookup"><span data-stu-id="7db9a-117">Hash tables are frequently used because they are very efficient for finding and retrieving data.</span></span> <span data-ttu-id="7db9a-118">Vous pouvez utiliser des tables de hachage pour stocker des listes et créer des propriétés calculées dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7db9a-118">You can use hash tables to store lists and to create calculated properties in PowerShell.</span></span> <span data-ttu-id="7db9a-119">Et PowerShell a une applet de commande, ConvertFrom-StringData, qui convertit les chaînes en une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="7db9a-119">And, PowerShell has a cmdlet, ConvertFrom-StringData, that converts strings to a hash table.</span></span>

### <a name="syntax"></a><span data-ttu-id="7db9a-120">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7db9a-120">Syntax</span></span>

<span data-ttu-id="7db9a-121">La syntaxe d’une table de hachage est la suivante :</span><span class="sxs-lookup"><span data-stu-id="7db9a-121">The syntax of a hash table is as follows:</span></span>

```powershell
@{ <name> = <value>; [<name> = <value> ] ...}
```

<span data-ttu-id="7db9a-122">La syntaxe d’un dictionnaire ordonné est la suivante :</span><span class="sxs-lookup"><span data-stu-id="7db9a-122">The syntax of an ordered dictionary is as follows:</span></span>

```powershell
[ordered]@{ <name> = <value>; [<name> = <value> ] ...}
```

<span data-ttu-id="7db9a-123">L’attribut [Ordered] a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="7db9a-123">The [ordered] attribute was introduced in PowerShell 3.0.</span></span>

### <a name="creating-hash-tables"></a><span data-ttu-id="7db9a-124">Création de tables de hachage</span><span class="sxs-lookup"><span data-stu-id="7db9a-124">Creating Hash Tables</span></span>

<span data-ttu-id="7db9a-125">Pour créer une table de hachage, suivez les instructions ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="7db9a-125">To create a hash table, follow these guidelines:</span></span>

- <span data-ttu-id="7db9a-126">Commencez la table de hachage par un arobase (@).</span><span class="sxs-lookup"><span data-stu-id="7db9a-126">Begin the hash table with an at sign (@).</span></span>
- <span data-ttu-id="7db9a-127">Placez la table de hachage entre accolades ( {} ).</span><span class="sxs-lookup"><span data-stu-id="7db9a-127">Enclose the hash table in braces ({}).</span></span>
- <span data-ttu-id="7db9a-128">Entrez une ou plusieurs paires clé/valeur pour le contenu de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="7db9a-128">Enter one or more key/value pairs for the content of the hash table.</span></span>
- <span data-ttu-id="7db9a-129">Utilisez un signe égal (=) pour séparer chaque clé de sa valeur.</span><span class="sxs-lookup"><span data-stu-id="7db9a-129">Use an equal sign (=) to separate each key from its value.</span></span>
- <span data-ttu-id="7db9a-130">Utilisez un point-virgule (;) ou un saut de ligne pour séparer les paires clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="7db9a-130">Use a semicolon (;) or a line break to separate the key/value pairs.</span></span>
- <span data-ttu-id="7db9a-131">La clé qui contient des espaces doit être placée entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="7db9a-131">Key that contains spaces must be enclosed in quotation marks.</span></span> <span data-ttu-id="7db9a-132">Les valeurs doivent être des expressions PowerShell valides.</span><span class="sxs-lookup"><span data-stu-id="7db9a-132">Values must be valid PowerShell expressions.</span></span> <span data-ttu-id="7db9a-133">Les chaînes doivent apparaître entre guillemets, même si elles n’incluent pas d’espaces.</span><span class="sxs-lookup"><span data-stu-id="7db9a-133">Strings must appear in quotation marks, even if they do not include spaces.</span></span>
- <span data-ttu-id="7db9a-134">Pour gérer la table de hachage, enregistrez-la dans une variable.</span><span class="sxs-lookup"><span data-stu-id="7db9a-134">To manage the hash table, save it in a variable.</span></span>
- <span data-ttu-id="7db9a-135">Lorsque vous assignez une table de hachage triée à une variable, placez l’attribut [Ordered] avant le symbole « @ ».</span><span class="sxs-lookup"><span data-stu-id="7db9a-135">When assigning an ordered hash table to a variable, place the [ordered] attribute before the "@" symbol.</span></span> <span data-ttu-id="7db9a-136">Si vous le placez avant le nom de la variable, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="7db9a-136">If you place it before the variable name, the command fails.</span></span>

<span data-ttu-id="7db9a-137">Pour créer une table de hachage vide dans la valeur de $hash, tapez :</span><span class="sxs-lookup"><span data-stu-id="7db9a-137">To create an empty hash table in the value of $hash, type:</span></span>

```powershell
$hash = @{}
```

<span data-ttu-id="7db9a-138">Vous pouvez également ajouter des clés et des valeurs à une table de hachage quand vous la créez.</span><span class="sxs-lookup"><span data-stu-id="7db9a-138">You can also add keys and values to a hash table when you create it.</span></span> <span data-ttu-id="7db9a-139">Par exemple, l’instruction suivante crée une table de hachage avec trois clés.</span><span class="sxs-lookup"><span data-stu-id="7db9a-139">For example, the following statement creates a hash table with three keys.</span></span>

```powershell
$hash = @{ Number = 1; Shape = "Square"; Color = "Blue"}
```

### <a name="creating-ordered-dictionaries"></a><span data-ttu-id="7db9a-140">Création de dictionnaires ordonnés</span><span class="sxs-lookup"><span data-stu-id="7db9a-140">Creating Ordered Dictionaries</span></span>

<span data-ttu-id="7db9a-141">Vous pouvez créer un dictionnaire ordonné en ajoutant un objet de type OrderedDictionary, mais le moyen le plus simple de créer un dictionnaire ordonné est d’utiliser l’attribut [Ordered].</span><span class="sxs-lookup"><span data-stu-id="7db9a-141">You can create an ordered dictionary by adding an object of the OrderedDictionary type, but the easiest way to create an ordered dictionary is use the [Ordered] attribute.</span></span>

<span data-ttu-id="7db9a-142">L’attribut [Ordered] est introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="7db9a-142">The [ordered] attribute is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="7db9a-143">Placez l’attribut juste avant le symbole « @ ».</span><span class="sxs-lookup"><span data-stu-id="7db9a-143">Place the attribute immediately before the "@" symbol.</span></span>

```powershell
$hash = [ordered]@{ Number = 1; Shape = "Square"; Color = "Blue"}
```

<span data-ttu-id="7db9a-144">Vous pouvez utiliser des dictionnaires ordonnés de la même façon que vous utilisez des tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="7db9a-144">You can use ordered dictionaries in the same way that you use hash tables.</span></span>
<span data-ttu-id="7db9a-145">L’un ou l’autre type peut être utilisé comme valeur des paramètres qui acceptent une table de hachage ou un dictionnaire (iDictionary).</span><span class="sxs-lookup"><span data-stu-id="7db9a-145">Either type can be used as the value of parameters that take a hash table or dictionary (iDictionary).</span></span>

<span data-ttu-id="7db9a-146">Vous ne pouvez pas utiliser l’attribut [Ordered] pour convertir ou caster une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="7db9a-146">You cannot use the [ordered] attribute to convert or cast a hash table.</span></span> <span data-ttu-id="7db9a-147">Si vous placez l’attribut ordered avant le nom de la variable, la commande échoue avec le message d’erreur suivant.</span><span class="sxs-lookup"><span data-stu-id="7db9a-147">If you place the ordered attribute before the variable name, the command fails with the following error message.</span></span>

```powershell
PS C:\> [ordered]$hash = @{}
At line:1 char:1
+ [ordered]$hash = @{}
+ [!INCLUDE[]()]
The ordered attribute can be specified only on a hash literal node.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordExc
eption
+ FullyQualifiedErrorId : OrderedAttributeOnlyOnHashLiteralNode
```

<span data-ttu-id="7db9a-148">Pour corriger l’expression, déplacez l’attribut [Ordered].</span><span class="sxs-lookup"><span data-stu-id="7db9a-148">To correct the expression, move the [ordered] attribute.</span></span>

```powershell
PS C:\> $hash = [ordered]@{}
```

<span data-ttu-id="7db9a-149">Vous pouvez convertir un dictionnaire ordonné en table de hachage, mais vous ne pouvez pas récupérer l’attribut ordonné, même si vous effacez la variable et entrez de nouvelles valeurs.</span><span class="sxs-lookup"><span data-stu-id="7db9a-149">You can cast an ordered dictionary to a hash table, but you cannot recover the ordered attribute, even if you clear the variable and enter new values.</span></span> <span data-ttu-id="7db9a-150">Pour rétablir la commande, vous devez supprimer et recréer la variable.</span><span class="sxs-lookup"><span data-stu-id="7db9a-150">To re-establish the order, you must remove and recreate the variable.</span></span>

```
PS C:\> [hashtable]$hash = [ordered]@{
>> Number = 1; Shape = "Square"; Color = "Blue"}
PS C:\> $hash

Name                           Value
----                           -----
Color                          Blue
Shape                          Square
Number                         1
```

### <a name="displaying-hash-tables"></a><span data-ttu-id="7db9a-151">Affichage des tables de hachage</span><span class="sxs-lookup"><span data-stu-id="7db9a-151">Displaying Hash Tables</span></span>

<span data-ttu-id="7db9a-152">Pour afficher une table de hachage qui est enregistrée dans une variable, tapez le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="7db9a-152">To display a hash table that is saved in a variable, type the variable name.</span></span>
<span data-ttu-id="7db9a-153">Par défaut, les tables de hachage sont affichées sous la forme d’une table avec une colonne pour les clés et une pour les valeurs.</span><span class="sxs-lookup"><span data-stu-id="7db9a-153">By default, a hash tables is displayed as a table with one column for keys and one for values.</span></span>

```powershell
C:\PS> $hash

Name                           Value
----                           -----
Shape                          Square
Color                          Blue
Number                         1
```

<span data-ttu-id="7db9a-154">Les tables de hachage ont des propriétés Keys et values.</span><span class="sxs-lookup"><span data-stu-id="7db9a-154">Hash tables have Keys and Values properties.</span></span> <span data-ttu-id="7db9a-155">Utilisez la notation par points pour afficher toutes les clés ou toutes les valeurs.</span><span class="sxs-lookup"><span data-stu-id="7db9a-155">Use dot notation to display all of the keys or all of the values.</span></span>

```powershell
C:\PS> $hash.keys
Number
Shape
Color

C:\PS> $hash.values
1
Square
Blue
```

<span data-ttu-id="7db9a-156">Chaque nom de clé est également une propriété de la table de hachage, et sa valeur est la valeur de la propriété Key-Name.</span><span class="sxs-lookup"><span data-stu-id="7db9a-156">Each key name is also a property of the hash table, and its value is the value of the key-name property.</span></span> <span data-ttu-id="7db9a-157">Utilisez le format suivant pour afficher les valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="7db9a-157">Use the following format to display the property values.</span></span>

```powershell
$hashtable.<key>
<value>
```

<span data-ttu-id="7db9a-158">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7db9a-158">For example:</span></span>

```powershell
C:\PS> $hash.Number
1

C:\PS> $hash.Color
Blue
```

<span data-ttu-id="7db9a-159">Si le nom de la clé est en conflit avec l’un des noms de propriété du type HashTable, vous pouvez utiliser `PSBase` pour accéder à ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="7db9a-159">If the key name collides with one of the property names of the HashTable type, you can use `PSBase` to access those properties.</span></span> <span data-ttu-id="7db9a-160">Par exemple, si le nom de clé est `keys` et que vous souhaitez retourner la collection de clés, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="7db9a-160">For example, if the key name is `keys` and you want to return the collection of Keys, use this syntax:</span></span>

```powershell
$hashtable.PSBase.Keys
```

<span data-ttu-id="7db9a-161">Les tables de hachage ont une propriété Count qui indique le nombre de paires clé-valeur dans la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="7db9a-161">Hash tables have a Count property that indicates the number of key-value pairs in the hash table.</span></span>

```powershell
C:\PS> $hash.count
3
```

<span data-ttu-id="7db9a-162">Les tables de table de hachage ne sont pas des tableaux. vous ne pouvez donc pas utiliser un entier comme index dans la table de hachage, mais vous pouvez utiliser un nom de clé pour indexer la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="7db9a-162">Hash table tables are not arrays, so you cannot use an integer as an index into the hash table, but you can use a key name to index into the hash table.</span></span>
<span data-ttu-id="7db9a-163">Si la clé est une valeur de chaîne, mettez le nom de la clé entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="7db9a-163">If the key is a string value, enclose the key name in quotation marks.</span></span>

<span data-ttu-id="7db9a-164">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7db9a-164">For example:</span></span>

```powershell
C:\PS> $hash["Number"]
1
```

### <a name="adding-and-removing-keys-and-values"></a><span data-ttu-id="7db9a-165">Ajout et suppression de clés et de valeurs</span><span class="sxs-lookup"><span data-stu-id="7db9a-165">Adding and Removing Keys and Values</span></span>

<span data-ttu-id="7db9a-166">Pour ajouter des clés et des valeurs à une table de hachage, utilisez le format de commande suivant.</span><span class="sxs-lookup"><span data-stu-id="7db9a-166">To add keys and values to a hash table, use the following command format.</span></span>

```powershell
$hash["<key>"] = "<value>"
```

<span data-ttu-id="7db9a-167">Par exemple, pour ajouter une clé « Time » avec la valeur « Now » à la table de hachage, utilisez le format d’instruction suivant.</span><span class="sxs-lookup"><span data-stu-id="7db9a-167">For example, to add a "Time" key with a value of "Now" to the hash table, use the following statement format.</span></span>

```powershell
$hash["Time"] = "Now"
```

<span data-ttu-id="7db9a-168">Vous pouvez également ajouter des clés et des valeurs à une table de hachage à l’aide de la méthode Add de l’objet System. Collections. Hashtable.</span><span class="sxs-lookup"><span data-stu-id="7db9a-168">You can also add keys and values to a hash table by using the Add method of the System.Collections.Hashtable object.</span></span> <span data-ttu-id="7db9a-169">La méthode Add a la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="7db9a-169">The Add method has the following syntax:</span></span>

```powershell
Add(Key, Value)
```

<span data-ttu-id="7db9a-170">Par exemple, pour ajouter une clé « Time » avec la valeur « Now » à la table de hachage, utilisez le format d’instruction suivant.</span><span class="sxs-lookup"><span data-stu-id="7db9a-170">For example, to add a "Time" key with a value of "Now" to the hash table, use the following statement format.</span></span>

```powershell
$hash.Add("Time", "Now")
```

<span data-ttu-id="7db9a-171">En outre, vous pouvez ajouter des clés et des valeurs à une table de hachage en utilisant l’opérateur d’addition (+) pour ajouter une table de hachage à une table de hachage existante.</span><span class="sxs-lookup"><span data-stu-id="7db9a-171">And, you can add keys and values to a hash table by using the addition operator (+) to add a hash table to an existing hash table.</span></span> <span data-ttu-id="7db9a-172">Par exemple, l’instruction suivante ajoute une clé « Time » avec la valeur « Now » à la table de hachage dans la variable $hash.</span><span class="sxs-lookup"><span data-stu-id="7db9a-172">For example, the following statement adds a "Time" key with a value of "Now" to the hash table in the $hash variable.</span></span>

```powershell
$hash = $hash + @{Time="Now"}
```

<span data-ttu-id="7db9a-173">Vous pouvez également ajouter des valeurs stockées dans des variables.</span><span class="sxs-lookup"><span data-stu-id="7db9a-173">You can also add values that are stored in variables.</span></span>

```powershell
$t = "Today"
$now = (Get-Date)

$hash.Add($t, $now)
```

<span data-ttu-id="7db9a-174">Vous ne pouvez pas utiliser un opérateur de soustraction pour supprimer une paire clé/valeur d’une table de hachage, mais vous pouvez utiliser la méthode Remove de l’objet Hashtable.</span><span class="sxs-lookup"><span data-stu-id="7db9a-174">You cannot use a subtraction operator to remove a key/value pair from a hash table, but you can use the Remove method of the Hashtable object.</span></span> <span data-ttu-id="7db9a-175">La méthode Remove prend la clé comme valeur.</span><span class="sxs-lookup"><span data-stu-id="7db9a-175">The Remove method takes the key as its value.</span></span>

<span data-ttu-id="7db9a-176">La méthode Remove a la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="7db9a-176">The Remove method has the following syntax:</span></span>

```
Remove(Key)
```

<span data-ttu-id="7db9a-177">Par exemple, pour supprimer la paire clé/valeur de date/heure de la table de hachage dans la valeur de la variable $hash, tapez :</span><span class="sxs-lookup"><span data-stu-id="7db9a-177">For example, to remove the Time=Now key/value pair from the hash table in the value of the $hash variable, type:</span></span>

```powershell
$hash.Remove("Time")
```

<span data-ttu-id="7db9a-178">Vous pouvez utiliser toutes les propriétés et méthodes des objets Hashtable dans PowerShell, y compris Contains, Clear, clone et CopyTo.</span><span class="sxs-lookup"><span data-stu-id="7db9a-178">You can use all of the properties and methods of Hashtable objects in PowerShell, including Contains, Clear, Clone, and CopyTo.</span></span> <span data-ttu-id="7db9a-179">Pour plus d’informations sur les objets Hashtable, consultez [System. Collections. Hashtable](/dotnet/api/system.collections.hashtable).</span><span class="sxs-lookup"><span data-stu-id="7db9a-179">For more information about Hashtable objects, see [System.Collections.Hashtable](/dotnet/api/system.collections.hashtable).</span></span>

### <a name="object-types-in-hashtables"></a><span data-ttu-id="7db9a-180">Types d’objets dans les tables de hachage</span><span class="sxs-lookup"><span data-stu-id="7db9a-180">Object Types in HashTables</span></span>

<span data-ttu-id="7db9a-181">Les clés et les valeurs d’une table de hachage peuvent avoir n’importe quel type d’objet .NET, et une seule table de hachage peut avoir des clés et des valeurs de plusieurs types.</span><span class="sxs-lookup"><span data-stu-id="7db9a-181">The keys and values in a hash table can have any .NET object type, and a single hash table can have keys and values of multiple types.</span></span>

<span data-ttu-id="7db9a-182">L’instruction suivante crée une table de hachage de chaînes de nom de processus et traite les valeurs d’objet et les enregistre dans la `$p` variable.</span><span class="sxs-lookup"><span data-stu-id="7db9a-182">The following statement creates a hash table of process name strings and process object values and saves it in the `$p` variable.</span></span>

```powershell
$p = @{"PowerShell" = (Get-Process PowerShell);
"Notepad" = (Get-Process notepad)}
```

<span data-ttu-id="7db9a-183">Vous pouvez afficher la table de hachage dans `$p` et utiliser les propriétés Key-Name pour afficher les valeurs.</span><span class="sxs-lookup"><span data-stu-id="7db9a-183">You can display the hash table in `$p` and use the key-name properties to display the values.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)

C:\PS> $p.PowerShell

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    441      24    54196      54012   571     5.10   1788 PowerShell

C:\PS> $p.keys | foreach {$p.$_.handles}
441
251
```

<span data-ttu-id="7db9a-184">Les clés d’une table de hachage peuvent également être de n’importe quel type .NET.</span><span class="sxs-lookup"><span data-stu-id="7db9a-184">The keys in a hash table can also be any .NET type.</span></span> <span data-ttu-id="7db9a-185">L’instruction suivante ajoute une paire clé/valeur à la table de hachage dans la `$p` variable.</span><span class="sxs-lookup"><span data-stu-id="7db9a-185">The following statement adds a key/value pair to the hash table in the `$p` variable.</span></span> <span data-ttu-id="7db9a-186">La clé est un objet de service qui représente le service WinRM et la valeur est l’état actuel du service.</span><span class="sxs-lookup"><span data-stu-id="7db9a-186">The key is a Service object that represents the WinRM service, and the value is the current status of the service.</span></span>

```powershell
C:\PS> $p = $p + @{(Get-Service WinRM) = ((Get-Service WinRM).Status)}
```

<span data-ttu-id="7db9a-187">Vous pouvez afficher la nouvelle paire clé/valeur et y accéder à l’aide des mêmes méthodes que celles que vous utilisez pour d’autres paires dans la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="7db9a-187">You can display and access the new key/value pair by using the same methods that you use for other pairs in the hash table.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running

C:\PS> $p.keys
PowerShell
Notepad

Status   Name               DisplayName
------   ----               -----------
Running  winrm              Windows Remote Management (WS-Manag...

C:\PS> $p.keys | foreach {$_.name}
winrm
```

<span data-ttu-id="7db9a-188">Les clés et les valeurs d’une table de hachage peuvent également être des objets Hashtable.</span><span class="sxs-lookup"><span data-stu-id="7db9a-188">The keys and values in a hash table can also be Hashtable objects.</span></span> <span data-ttu-id="7db9a-189">L’instruction suivante ajoute une paire clé/valeur à la table de hachage dans la `$p` variable dans laquelle la clé est une chaîne, Hash2, et la valeur est une table de hachage avec trois paires clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="7db9a-189">The following statement adds key/value pair to the hash table in the `$p` variable in which the key is a string, Hash2, and the value is a hash table with three key/value pairs.</span></span>

```powershell
C:\PS> $p = $p + @{"Hash2"= @{a=1; b=2; c=3}}
```

<span data-ttu-id="7db9a-190">Vous pouvez afficher les nouvelles valeurs et y accéder à l’aide des mêmes méthodes.</span><span class="sxs-lookup"><span data-stu-id="7db9a-190">You can display and access the new values by using the same methods.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
Hash2                          {a, b, c}

C:\PS> $p.Hash2

Name                           Value
----                           -----
a                              1
b                              2
c                              3

C:\PS> $p.Hash2.b
2
```

### <a name="sorting-keys-and-values"></a><span data-ttu-id="7db9a-191">Tri des clés et des valeurs</span><span class="sxs-lookup"><span data-stu-id="7db9a-191">Sorting Keys and Values</span></span>

<span data-ttu-id="7db9a-192">Les éléments d’une table de hachage ne sont pas triés intrinsèquement.</span><span class="sxs-lookup"><span data-stu-id="7db9a-192">The items in a hash table are intrinsically unordered.</span></span> <span data-ttu-id="7db9a-193">Les paires clé/valeur peuvent apparaître dans un ordre différent chaque fois que vous les affichez.</span><span class="sxs-lookup"><span data-stu-id="7db9a-193">The key/value pairs might appear in a different order each time that you display them.</span></span>

<span data-ttu-id="7db9a-194">Bien que vous ne puissiez pas trier une table de hachage, vous pouvez utiliser la méthode GetEnumerator des tables de hachage pour énumérer les clés et les valeurs, puis utiliser l’applet de commande Sort-Object pour trier les valeurs énumérées à afficher.</span><span class="sxs-lookup"><span data-stu-id="7db9a-194">Although you cannot sort a hash table, you can use the GetEnumerator method of hash tables to enumerate the keys and values, and then use the Sort-Object cmdlet to sort the enumerated values for display.</span></span>

<span data-ttu-id="7db9a-195">Par exemple, les commandes suivantes énumèrent les clés et les valeurs de la table de hachage dans la `$p` variable, puis trient les clés par ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="7db9a-195">For example, the following commands enumerate the keys and values in the hash table in the `$p` variable and then sort the keys in alphabetical order.</span></span>

```powershell
C:\PS> $p.GetEnumerator() | Sort-Object -Property key

Name                           Value
----                           -----
Notepad                        System.Diagnostics.Process (notepad)
PowerShell                     System.Diagnostics.Process (PowerShell)
System.ServiceProcess.Servi... Running
```

<span data-ttu-id="7db9a-196">La commande suivante utilise la même procédure pour trier les valeurs de hachage dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="7db9a-196">The following command uses the same procedure to sort the hash values in descending order.</span></span>

```powershell
C:\PS> $p.getenumerator() | Sort-Object -Property Value -Descending

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
```

### <a name="creating-objects-from-hash-tables"></a><span data-ttu-id="7db9a-197">Création d’objets à partir de tables de hachage</span><span class="sxs-lookup"><span data-stu-id="7db9a-197">Creating Objects from Hash Tables</span></span>

<span data-ttu-id="7db9a-198">À compter de PowerShell 3,0, vous pouvez créer un objet à partir d’une table de hachage de propriétés et de valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="7db9a-198">Beginning in PowerShell 3.0, you can create an object from a hash table of properties and property values.</span></span>

<span data-ttu-id="7db9a-199">La syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="7db9a-199">The syntax is as follows:</span></span>

```powershell
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

<span data-ttu-id="7db9a-200">Cette méthode fonctionne uniquement pour les classes qui ont un constructeur null, autrement dit, un constructeur qui n’a aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="7db9a-200">This method works only for classes that have a null constructor, that is, a constructor that has no parameters.</span></span> <span data-ttu-id="7db9a-201">Les propriétés de l’objet doivent être publiques et définissables.</span><span class="sxs-lookup"><span data-stu-id="7db9a-201">The object properties must be public and settable.</span></span>

<span data-ttu-id="7db9a-202">Pour plus d’informations, consultez [about_Object_Creation](about_Object_Creation.md).</span><span class="sxs-lookup"><span data-stu-id="7db9a-202">For more information, see [about_Object_Creation](about_Object_Creation.md).</span></span>

### <a name="convertfrom-stringdata"></a><span data-ttu-id="7db9a-203">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="7db9a-203">ConvertFrom-StringData</span></span>

<span data-ttu-id="7db9a-204">L' `ConvertFrom-StringData` applet de commande convertit une chaîne ou une chaîne ici de paires clé/valeur en une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="7db9a-204">The `ConvertFrom-StringData` cmdlet converts a string or a here-string of key/value pairs into a hash table.</span></span> <span data-ttu-id="7db9a-205">Vous pouvez utiliser l' `ConvertFrom-StringData` applet de commande en toute sécurité dans la section des données d’un script, et vous pouvez l’utiliser avec l' `Import-LocalizedData` applet de commande pour afficher les messages utilisateur dans la culture de l’interface utilisateur (IU) de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="7db9a-205">You can use the `ConvertFrom-StringData` cmdlet safely in the Data section of a script, and you can use it with the `Import-LocalizedData` cmdlet to display user messages in the user-interface (UI) culture of the current user.</span></span>

<span data-ttu-id="7db9a-206">Ici-les chaînes sont particulièrement utiles lorsque les valeurs de la table de hachage sont des guillemets.</span><span class="sxs-lookup"><span data-stu-id="7db9a-206">Here-strings are especially useful when the values in the hash table include quotation marks.</span></span> <span data-ttu-id="7db9a-207">Pour plus d’informations sur les chaînes ici, consultez [about_Quoting_Rules](about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="7db9a-207">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

<span data-ttu-id="7db9a-208">L’exemple suivant montre comment créer une chaîne « ici- » des messages utilisateur dans l’exemple précédent et comment utiliser `ConvertFrom-StringData` pour les convertir d’une chaîne en une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="7db9a-208">The following example shows how to create a here-string of the user messages in the previous example and how to use `ConvertFrom-StringData` to convert them from a string into a hash table.</span></span>

<span data-ttu-id="7db9a-209">La commande suivante crée une chaîne ici-String des paires clé/valeur, puis l’enregistre dans la \$ variable chaîne.</span><span class="sxs-lookup"><span data-stu-id="7db9a-209">The following command creates a here-string of the key/value pairs and then saves it in the \$string variable.</span></span>

```powershell
C:\PS> $string = @"
Msg1 = Type "Windows".
Msg2 = She said, "Hello, World."
Msg3 = Enter an alias (or "nickname").
"@
```

<span data-ttu-id="7db9a-210">Cette commande utilise l’applet de commande ConvertFrom-StringData pour convertir la chaîne here en une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="7db9a-210">This command uses the ConvertFrom-StringData cmdlet to convert the here-string into a hash table.</span></span>

```powershell
C:\PS> ConvertFrom-StringData $string

Name                           Value
----                           -----
Msg3                           Enter an alias (or "nickname").
Msg2                           She said, "Hello, World."
Msg1                           Type "Windows".
```

<span data-ttu-id="7db9a-211">Pour plus d’informations sur les chaînes ici, consultez [about_Quoting_Rules](about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="7db9a-211">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7db9a-212">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="7db9a-212">SEE ALSO</span></span>

[<span data-ttu-id="7db9a-213">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="7db9a-213">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="7db9a-214">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="7db9a-214">about_Object_Creation</span></span>](about_Object_Creation.md)

[<span data-ttu-id="7db9a-215">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="7db9a-215">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="7db9a-216">about_Script_Internationalization</span><span class="sxs-lookup"><span data-stu-id="7db9a-216">about_Script_Internationalization</span></span>](about_Script_Internationalization.md)

[<span data-ttu-id="7db9a-217">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="7db9a-217">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[<span data-ttu-id="7db9a-218">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="7db9a-218">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

[<span data-ttu-id="7db9a-219">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="7db9a-219">System.Collections.Hashtable</span></span>](/dotnet/api/system.collections.hashtable)
