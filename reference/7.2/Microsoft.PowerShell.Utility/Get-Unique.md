---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-unique?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Unique
ms.openlocfilehash: de827d956e6e813e84d87bb1578ee7d596fe2f15
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603902"
---
# <span data-ttu-id="6e7c2-102">Get-Unique</span><span class="sxs-lookup"><span data-stu-id="6e7c2-102">Get-Unique</span></span>

## <span data-ttu-id="6e7c2-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6e7c2-103">SYNOPSIS</span></span>
<span data-ttu-id="6e7c2-104">Retourne les éléments uniques d'une liste triée.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-104">Returns unique items from a sorted list.</span></span>

## <span data-ttu-id="6e7c2-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="6e7c2-105">SYNTAX</span></span>

### <span data-ttu-id="6e7c2-106">AsString (par défaut)</span><span class="sxs-lookup"><span data-stu-id="6e7c2-106">AsString (Default)</span></span>

```
Get-Unique [-InputObject <PSObject>] [-AsString] [<CommonParameters>]
```

### <span data-ttu-id="6e7c2-107">UniqueByType</span><span class="sxs-lookup"><span data-stu-id="6e7c2-107">UniqueByType</span></span>

```
Get-Unique [-InputObject <PSObject>] [-OnType] [<CommonParameters>]
```

## <span data-ttu-id="6e7c2-108">Description</span><span class="sxs-lookup"><span data-stu-id="6e7c2-108">DESCRIPTION</span></span>

<span data-ttu-id="6e7c2-109">L' `Get-Unique` applet de commande compare chaque élément d’une liste triée à l’élément suivant, élimine les doublons et ne retourne qu’une seule instance de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-109">The `Get-Unique` cmdlet compares each item in a sorted list to the next item, eliminates duplicates, and returns only one instance of each item.</span></span> <span data-ttu-id="6e7c2-110">La liste doit être triée pour que l'applet de commande fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-110">The list must be sorted for the cmdlet to work properly.</span></span>

<span data-ttu-id="6e7c2-111">`Get-Unique` respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-111">`Get-Unique` is case-sensitive.</span></span> <span data-ttu-id="6e7c2-112">Par conséquent, les chaînes qui diffèrent uniquement par la casse sont considérées comme uniques.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-112">As a result, strings that differ only in character casing are considered to be unique.</span></span>

## <span data-ttu-id="6e7c2-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6e7c2-113">EXAMPLES</span></span>

### <span data-ttu-id="6e7c2-114">Exemple 1 : obtenir des mots uniques dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="6e7c2-114">Example 1: Get unique words in a text file</span></span>

<span data-ttu-id="6e7c2-115">Ces commandes recherchent le nombre de mots uniques dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-115">These commands find the number of unique words in a text file.</span></span>

```powershell
$A = $( foreach ($line in Get-Content C:\Test1\File1.txt) {
    $line.tolower().split(" ")
  }) | Sort-Object | Get-Unique
$A.count
```

<span data-ttu-id="6e7c2-116">La première commande obtient le contenu du fichier Fichier.txt.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-116">The first command gets the content of the File.txt file.</span></span> <span data-ttu-id="6e7c2-117">Elle convertit chaque ligne de texte en lettres minuscules, puis répartit chaque mot sur une ligne distincte au niveau de l'espace (« »).</span><span class="sxs-lookup"><span data-stu-id="6e7c2-117">It converts each line of text to lowercase letters and then splits each word onto a separate line at the space (" ").</span></span> <span data-ttu-id="6e7c2-118">Ensuite, elle trie la liste résultante par ordre alphabétique (valeur par défaut) et utilise l' `Get-Unique` applet de commande pour éliminer les mots en double.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-118">Then, it sorts the resulting list alphabetically (the default) and uses the `Get-Unique` cmdlet to eliminate any duplicate words.</span></span> <span data-ttu-id="6e7c2-119">Les résultats sont stockés dans la `$A` variable.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-119">The results are stored in the `$A` variable.</span></span>

<span data-ttu-id="6e7c2-120">La deuxième commande utilise la propriété **Count** de la collection de chaînes dans `$A` pour déterminer le nombre d’éléments dans `$A` .</span><span class="sxs-lookup"><span data-stu-id="6e7c2-120">The second command uses the **Count** property of the collection of strings in `$A` to determine how many items are in `$A`.</span></span>

### <span data-ttu-id="6e7c2-121">Exemple 2 : récupérer des entiers uniques dans un tableau</span><span class="sxs-lookup"><span data-stu-id="6e7c2-121">Example 2: Get unique integers in an array</span></span>

<span data-ttu-id="6e7c2-122">Cette commande recherche les membres uniques de l'ensemble d'entiers.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-122">This command finds the unique members of the set of integers.</span></span>

```powershell
1,1,1,1,12,23,4,5,4643,5,3,3,3,3,3,3,3 | Sort-Object | Get-Unique
```

```Output
1
3
4
5
12
23
4643
```

<span data-ttu-id="6e7c2-123">La première commande utilise un tableau d’entiers tapés sur la ligne de commande, les dirige vers l' `Sort-Object` applet de commande à trier, puis les transfère vers `Get-Unique` , ce qui élimine les entrées en double.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-123">The first command takes an array of integers typed at the command line, pipes them to the `Sort-Object` cmdlet to be sorted, and then pipes them to `Get-Unique`, which eliminates duplicate entries.</span></span>

### <span data-ttu-id="6e7c2-124">Exemple 3 : obtenir les types d’objets uniques dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="6e7c2-124">Example 3: Get unique object types in a directory</span></span>

<span data-ttu-id="6e7c2-125">Cette commande utilise l' `Get-ChildItem` applet de commande pour récupérer le contenu du répertoire local, qui comprend les fichiers et les répertoires.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-125">This command uses the `Get-ChildItem` cmdlet to retrieve the contents of the local directory, which includes files and directories.</span></span>

```powershell
Get-ChildItem | Sort-Object {$_.GetType()} | Get-Unique -OnType
```

<span data-ttu-id="6e7c2-126">L’opérateur de pipeline (|) envoie les résultats à l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="6e7c2-126">The pipeline operator (|) sends the results to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="6e7c2-127">L' `$_.GetType()` instruction applique la méthode **GetType** à chaque fichier ou répertoire.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-127">The `$_.GetType()` statement applies the **GetType** method to each file or directory.</span></span> <span data-ttu-id="6e7c2-128">Trie ensuite `Sort-Object` les éléments par type.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-128">Then, `Sort-Object` sorts the items by type.</span></span> <span data-ttu-id="6e7c2-129">Un autre opérateur de pipeline envoie les résultats à `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="6e7c2-129">Another pipeline operator sends the results to `Get-Unique`.</span></span> <span data-ttu-id="6e7c2-130">Le paramètre **OnType** indique `Get-Unique` à de ne retourner qu’un seul objet de chaque type.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-130">The **OnType** parameter directs `Get-Unique` to return only one object of each type.</span></span>

### <span data-ttu-id="6e7c2-131">Exemple 4 : récupération d’un processus unique</span><span class="sxs-lookup"><span data-stu-id="6e7c2-131">Example 4: Get unique processes</span></span>

<span data-ttu-id="6e7c2-132">Cette commande obtient les noms des processus qui s'exécutent sur l'ordinateur sans doublon.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-132">This command gets the names of processes running on the computer with duplicates eliminated.</span></span>

```powershell
Get-Process | Sort-Object | Select-Object processname | Get-Unique -AsString
```

<span data-ttu-id="6e7c2-133">La `Get-Process` commande obtient tous les processus sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-133">The `Get-Process` command gets all of the processes on the computer.</span></span> <span data-ttu-id="6e7c2-134">L’opérateur de pipeline (|) passe le résultat à `Sort-Object` , qui, par défaut, trie les processus par ordre alphabétique par ProcessName.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-134">The pipeline operator (|) passes the result to `Sort-Object`, which, by default, sorts the processes alphabetically by ProcessName.</span></span> <span data-ttu-id="6e7c2-135">Les résultats sont dirigés vers l’applet de commande `Select-Object` , qui sélectionne uniquement les valeurs de la propriété ProcessName de chaque objet.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-135">The results are piped to the `Select-Object` cmdlet, which selects only the values of the ProcessName property of each object.</span></span> <span data-ttu-id="6e7c2-136">Les résultats sont ensuite redirigés vers `Get-Unique` pour éliminer les doublons.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-136">The results are then piped to `Get-Unique` to eliminate duplicates.</span></span>

<span data-ttu-id="6e7c2-137">Le paramètre **AsString** indique `Get-Unique` à de traiter les valeurs **ProcessName** en tant que chaînes.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-137">The **AsString** parameter tells `Get-Unique` to treat the **ProcessName** values as strings.</span></span>
<span data-ttu-id="6e7c2-138">Sans ce paramètre, `Get-Unique` traite les valeurs **ProcessName** en tant qu’objets et ne retourne qu’une seule instance de l’objet, autrement dit, le premier nom de processus de la liste.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-138">Without this parameter, `Get-Unique` treats the **ProcessName** values as objects and returns only one instance of the object, that is, the first process name in the list.</span></span>

## <span data-ttu-id="6e7c2-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6e7c2-139">PARAMETERS</span></span>

### <span data-ttu-id="6e7c2-140">-AsString</span><span class="sxs-lookup"><span data-stu-id="6e7c2-140">-AsString</span></span>

<span data-ttu-id="6e7c2-141">Indique que cette applet de commande utilise les données en tant que chaîne.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-141">Indicates that this cmdlet uses the data as a string.</span></span> <span data-ttu-id="6e7c2-142">Sans ce paramètre, les données sont traitées comme un objet. par conséquent, lorsque vous envoyez une collection d’objets du même type à `Get-Unique` , par exemple une collection de fichiers, elle ne retourne qu’un seul (le premier).</span><span class="sxs-lookup"><span data-stu-id="6e7c2-142">Without this parameter, data is treated as an object, so when you submit a collection of objects of the same type to `Get-Unique`, such as a collection of files, it returns just one (the first).</span></span> <span data-ttu-id="6e7c2-143">Vous pouvez utiliser ce paramètre pour rechercher les valeurs uniques des propriétés de l'objet, telles que les noms de fichier uniques.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-143">You can use this parameter to find the unique values of object properties, such as the file names.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e7c2-144">-InputObject</span><span class="sxs-lookup"><span data-stu-id="6e7c2-144">-InputObject</span></span>

<span data-ttu-id="6e7c2-145">Spécifie l’entrée pour `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="6e7c2-145">Specifies input for `Get-Unique`.</span></span> <span data-ttu-id="6e7c2-146">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-146">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="6e7c2-147">Cette applet de commande traite l’entrée envoyée en utilisant **InputObject** comme collection.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-147">This cmdlet treats the input submitted by using **InputObject** as a collection.</span></span> <span data-ttu-id="6e7c2-148">Il n’énumère pas les éléments individuels dans la collection.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-148">it does not enumerate individual items in the collection.</span></span> <span data-ttu-id="6e7c2-149">Étant donné que la collection est un élément unique, l’entrée envoyée à l’aide d' **InputObject** est toujours retournée inchangée.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-149">Because the collection is a single item, input submitted by using **InputObject** is always returned unchanged.</span></span>

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

### <span data-ttu-id="6e7c2-150">-OnType</span><span class="sxs-lookup"><span data-stu-id="6e7c2-150">-OnType</span></span>

<span data-ttu-id="6e7c2-151">Indique que cette applet de commande ne retourne qu’un seul objet de chaque type.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-151">Indicates that this cmdlet returns only one object of each type.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UniqueByType
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e7c2-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6e7c2-152">CommonParameters</span></span>

<span data-ttu-id="6e7c2-153">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6e7c2-154">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6e7c2-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6e7c2-155">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6e7c2-155">INPUTS</span></span>

### <span data-ttu-id="6e7c2-156">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="6e7c2-156">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="6e7c2-157">Vous pouvez diriger tout type d’objet vers `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="6e7c2-157">You can pipe any type of object to `Get-Unique`.</span></span>

## <span data-ttu-id="6e7c2-158">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6e7c2-158">OUTPUTS</span></span>

### <span data-ttu-id="6e7c2-159">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="6e7c2-159">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="6e7c2-160">Le type d’objet `Get-Unique` retourné est déterminé par l’entrée.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-160">The type of object that `Get-Unique` returns is determined by the input.</span></span>

## <span data-ttu-id="6e7c2-161">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6e7c2-161">NOTES</span></span>

<span data-ttu-id="6e7c2-162">Vous pouvez également faire référence à `Get-Unique` par son alias intégré, `gu` .</span><span class="sxs-lookup"><span data-stu-id="6e7c2-162">You can also refer to `Get-Unique` by its built-in alias, `gu`.</span></span> <span data-ttu-id="6e7c2-163">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="6e7c2-163">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="6e7c2-164">Pour trier une liste, utilisez Sort-Object.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-164">To sort a list, use Sort-Object.</span></span> <span data-ttu-id="6e7c2-165">Vous pouvez également utiliser le paramètre **unique** de `Sort-Object` pour rechercher les éléments uniques dans une liste.</span><span class="sxs-lookup"><span data-stu-id="6e7c2-165">You can also use the **Unique** parameter of `Sort-Object` to find the unique items in a list.</span></span>

## <span data-ttu-id="6e7c2-166">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6e7c2-166">RELATED LINKS</span></span>

[<span data-ttu-id="6e7c2-167">Select-Object</span><span class="sxs-lookup"><span data-stu-id="6e7c2-167">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="6e7c2-168">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="6e7c2-168">Sort-Object</span></span>](Sort-Object.md)

