---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-unique?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Unique
ms.openlocfilehash: f0233e24e82ce5f0ef2113f65d19134833d75cb1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202793"
---
# <span data-ttu-id="b4338-103">Get-Unique</span><span class="sxs-lookup"><span data-stu-id="b4338-103">Get-Unique</span></span>

## <span data-ttu-id="b4338-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b4338-104">SYNOPSIS</span></span>
<span data-ttu-id="b4338-105">Retourne les éléments uniques d'une liste triée.</span><span class="sxs-lookup"><span data-stu-id="b4338-105">Returns unique items from a sorted list.</span></span>

## <span data-ttu-id="b4338-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b4338-106">SYNTAX</span></span>

### <span data-ttu-id="b4338-107">AsString (par défaut)</span><span class="sxs-lookup"><span data-stu-id="b4338-107">AsString (Default)</span></span>

```
Get-Unique [-InputObject <PSObject>] [-AsString] [<CommonParameters>]
```

### <span data-ttu-id="b4338-108">UniqueByType</span><span class="sxs-lookup"><span data-stu-id="b4338-108">UniqueByType</span></span>

```
Get-Unique [-InputObject <PSObject>] [-OnType] [<CommonParameters>]
```

## <span data-ttu-id="b4338-109">Description</span><span class="sxs-lookup"><span data-stu-id="b4338-109">DESCRIPTION</span></span>

<span data-ttu-id="b4338-110">L' `Get-Unique` applet de commande compare chaque élément d’une liste triée à l’élément suivant, élimine les doublons et ne retourne qu’une seule instance de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="b4338-110">The `Get-Unique` cmdlet compares each item in a sorted list to the next item, eliminates duplicates, and returns only one instance of each item.</span></span> <span data-ttu-id="b4338-111">La liste doit être triée pour que l'applet de commande fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="b4338-111">The list must be sorted for the cmdlet to work properly.</span></span>

<span data-ttu-id="b4338-112">`Get-Unique` respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="b4338-112">`Get-Unique` is case-sensitive.</span></span> <span data-ttu-id="b4338-113">Par conséquent, les chaînes qui diffèrent uniquement par la casse sont considérées comme uniques.</span><span class="sxs-lookup"><span data-stu-id="b4338-113">As a result, strings that differ only in character casing are considered to be unique.</span></span>

## <span data-ttu-id="b4338-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b4338-114">EXAMPLES</span></span>

### <span data-ttu-id="b4338-115">Exemple 1 : obtenir des mots uniques dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="b4338-115">Example 1: Get unique words in a text file</span></span>

<span data-ttu-id="b4338-116">Ces commandes recherchent le nombre de mots uniques dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="b4338-116">These commands find the number of unique words in a text file.</span></span>

```powershell
$A = $( foreach ($line in Get-Content C:\Test1\File1.txt) {
    $line.tolower().split(" ")
  }) | Sort-Object | Get-Unique
$A.count
```

<span data-ttu-id="b4338-117">La première commande obtient le contenu du fichier Fichier.txt.</span><span class="sxs-lookup"><span data-stu-id="b4338-117">The first command gets the content of the File.txt file.</span></span> <span data-ttu-id="b4338-118">Elle convertit chaque ligne de texte en lettres minuscules, puis répartit chaque mot sur une ligne distincte au niveau de l'espace (« »).</span><span class="sxs-lookup"><span data-stu-id="b4338-118">It converts each line of text to lowercase letters and then splits each word onto a separate line at the space (" ").</span></span> <span data-ttu-id="b4338-119">Ensuite, elle trie la liste résultante par ordre alphabétique (valeur par défaut) et utilise l' `Get-Unique` applet de commande pour éliminer les mots en double.</span><span class="sxs-lookup"><span data-stu-id="b4338-119">Then, it sorts the resulting list alphabetically (the default) and uses the `Get-Unique` cmdlet to eliminate any duplicate words.</span></span> <span data-ttu-id="b4338-120">Les résultats sont stockés dans la `$A` variable.</span><span class="sxs-lookup"><span data-stu-id="b4338-120">The results are stored in the `$A` variable.</span></span>

<span data-ttu-id="b4338-121">La deuxième commande utilise la propriété **Count** de la collection de chaînes dans `$A` pour déterminer le nombre d’éléments dans `$A` .</span><span class="sxs-lookup"><span data-stu-id="b4338-121">The second command uses the **Count** property of the collection of strings in `$A` to determine how many items are in `$A`.</span></span>

### <span data-ttu-id="b4338-122">Exemple 2 : récupérer des entiers uniques dans un tableau</span><span class="sxs-lookup"><span data-stu-id="b4338-122">Example 2: Get unique integers in an array</span></span>

<span data-ttu-id="b4338-123">Cette commande recherche les membres uniques de l'ensemble d'entiers.</span><span class="sxs-lookup"><span data-stu-id="b4338-123">This command finds the unique members of the set of integers.</span></span>

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

<span data-ttu-id="b4338-124">La première commande utilise un tableau d’entiers tapés sur la ligne de commande, les dirige vers l' `Sort-Object` applet de commande à trier, puis les transfère vers `Get-Unique` , ce qui élimine les entrées en double.</span><span class="sxs-lookup"><span data-stu-id="b4338-124">The first command takes an array of integers typed at the command line, pipes them to the `Sort-Object` cmdlet to be sorted, and then pipes them to `Get-Unique`, which eliminates duplicate entries.</span></span>

### <span data-ttu-id="b4338-125">Exemple 3 : obtenir les types d’objets uniques dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="b4338-125">Example 3: Get unique object types in a directory</span></span>

<span data-ttu-id="b4338-126">Cette commande utilise l' `Get-ChildItem` applet de commande pour récupérer le contenu du répertoire local, qui comprend les fichiers et les répertoires.</span><span class="sxs-lookup"><span data-stu-id="b4338-126">This command uses the `Get-ChildItem` cmdlet to retrieve the contents of the local directory, which includes files and directories.</span></span>

```powershell
Get-ChildItem | Sort-Object {$_.GetType()} | Get-Unique -OnType
```

<span data-ttu-id="b4338-127">L’opérateur de pipeline (|) envoie les résultats à l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="b4338-127">The pipeline operator (|) sends the results to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="b4338-128">L' `$_.GetType()` instruction applique la méthode **GetType** à chaque fichier ou répertoire.</span><span class="sxs-lookup"><span data-stu-id="b4338-128">The `$_.GetType()` statement applies the **GetType** method to each file or directory.</span></span> <span data-ttu-id="b4338-129">Trie ensuite `Sort-Object` les éléments par type.</span><span class="sxs-lookup"><span data-stu-id="b4338-129">Then, `Sort-Object` sorts the items by type.</span></span> <span data-ttu-id="b4338-130">Un autre opérateur de pipeline envoie les résultats à `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="b4338-130">Another pipeline operator sends the results to `Get-Unique`.</span></span> <span data-ttu-id="b4338-131">Le paramètre **OnType** indique `Get-Unique` à de ne retourner qu’un seul objet de chaque type.</span><span class="sxs-lookup"><span data-stu-id="b4338-131">The **OnType** parameter directs `Get-Unique` to return only one object of each type.</span></span>

### <span data-ttu-id="b4338-132">Exemple 4 : récupération d’un processus unique</span><span class="sxs-lookup"><span data-stu-id="b4338-132">Example 4: Get unique processes</span></span>

<span data-ttu-id="b4338-133">Cette commande obtient les noms des processus qui s'exécutent sur l'ordinateur sans doublon.</span><span class="sxs-lookup"><span data-stu-id="b4338-133">This command gets the names of processes running on the computer with duplicates eliminated.</span></span>

```powershell
Get-Process | Sort-Object | Select-Object processname | Get-Unique -AsString
```

<span data-ttu-id="b4338-134">La `Get-Process` commande obtient tous les processus sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b4338-134">The `Get-Process` command gets all of the processes on the computer.</span></span> <span data-ttu-id="b4338-135">L’opérateur de pipeline (|) passe le résultat à `Sort-Object` , qui, par défaut, trie les processus par ordre alphabétique par ProcessName.</span><span class="sxs-lookup"><span data-stu-id="b4338-135">The pipeline operator (|) passes the result to `Sort-Object`, which, by default, sorts the processes alphabetically by ProcessName.</span></span> <span data-ttu-id="b4338-136">Les résultats sont dirigés vers l’applet de commande `Select-Object` , qui sélectionne uniquement les valeurs de la propriété ProcessName de chaque objet.</span><span class="sxs-lookup"><span data-stu-id="b4338-136">The results are piped to the `Select-Object` cmdlet, which selects only the values of the ProcessName property of each object.</span></span> <span data-ttu-id="b4338-137">Les résultats sont ensuite redirigés vers `Get-Unique` pour éliminer les doublons.</span><span class="sxs-lookup"><span data-stu-id="b4338-137">The results are then piped to `Get-Unique` to eliminate duplicates.</span></span>

<span data-ttu-id="b4338-138">Le paramètre **AsString** indique `Get-Unique` à de traiter les valeurs **ProcessName** en tant que chaînes.</span><span class="sxs-lookup"><span data-stu-id="b4338-138">The **AsString** parameter tells `Get-Unique` to treat the **ProcessName** values as strings.</span></span>
<span data-ttu-id="b4338-139">Sans ce paramètre, `Get-Unique` traite les valeurs **ProcessName** en tant qu’objets et ne retourne qu’une seule instance de l’objet, autrement dit, le premier nom de processus de la liste.</span><span class="sxs-lookup"><span data-stu-id="b4338-139">Without this parameter, `Get-Unique` treats the **ProcessName** values as objects and returns only one instance of the object, that is, the first process name in the list.</span></span>

## <span data-ttu-id="b4338-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b4338-140">PARAMETERS</span></span>

### <span data-ttu-id="b4338-141">-AsString</span><span class="sxs-lookup"><span data-stu-id="b4338-141">-AsString</span></span>

<span data-ttu-id="b4338-142">Indique que cette applet de commande utilise les données en tant que chaîne.</span><span class="sxs-lookup"><span data-stu-id="b4338-142">Indicates that this cmdlet uses the data as a string.</span></span> <span data-ttu-id="b4338-143">Sans ce paramètre, les données sont traitées comme un objet. par conséquent, lorsque vous envoyez une collection d’objets du même type à `Get-Unique` , par exemple une collection de fichiers, elle ne retourne qu’un seul (le premier).</span><span class="sxs-lookup"><span data-stu-id="b4338-143">Without this parameter, data is treated as an object, so when you submit a collection of objects of the same type to `Get-Unique`, such as a collection of files, it returns just one (the first).</span></span> <span data-ttu-id="b4338-144">Vous pouvez utiliser ce paramètre pour rechercher les valeurs uniques des propriétés de l'objet, telles que les noms de fichier uniques.</span><span class="sxs-lookup"><span data-stu-id="b4338-144">You can use this parameter to find the unique values of object properties, such as the file names.</span></span>

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

### <span data-ttu-id="b4338-145">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b4338-145">-InputObject</span></span>

<span data-ttu-id="b4338-146">Spécifie l’entrée pour `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="b4338-146">Specifies input for `Get-Unique`.</span></span> <span data-ttu-id="b4338-147">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient.</span><span class="sxs-lookup"><span data-stu-id="b4338-147">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="b4338-148">Cette applet de commande traite l’entrée envoyée en utilisant **InputObject** comme collection.</span><span class="sxs-lookup"><span data-stu-id="b4338-148">This cmdlet treats the input submitted by using **InputObject** as a collection.</span></span> <span data-ttu-id="b4338-149">Il n’énumère pas les éléments individuels dans la collection.</span><span class="sxs-lookup"><span data-stu-id="b4338-149">it does not enumerate individual items in the collection.</span></span> <span data-ttu-id="b4338-150">Étant donné que la collection est un élément unique, l’entrée envoyée à l’aide d' **InputObject** est toujours retournée inchangée.</span><span class="sxs-lookup"><span data-stu-id="b4338-150">Because the collection is a single item, input submitted by using **InputObject** is always returned unchanged.</span></span>

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

### <span data-ttu-id="b4338-151">-OnType</span><span class="sxs-lookup"><span data-stu-id="b4338-151">-OnType</span></span>

<span data-ttu-id="b4338-152">Indique que cette applet de commande ne retourne qu’un seul objet de chaque type.</span><span class="sxs-lookup"><span data-stu-id="b4338-152">Indicates that this cmdlet returns only one object of each type.</span></span>

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

### <span data-ttu-id="b4338-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b4338-153">CommonParameters</span></span>

<span data-ttu-id="b4338-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b4338-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b4338-155">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b4338-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b4338-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b4338-156">INPUTS</span></span>

### <span data-ttu-id="b4338-157">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="b4338-157">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b4338-158">Vous pouvez diriger tout type d’objet vers `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="b4338-158">You can pipe any type of object to `Get-Unique`.</span></span>

## <span data-ttu-id="b4338-159">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b4338-159">OUTPUTS</span></span>

### <span data-ttu-id="b4338-160">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="b4338-160">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b4338-161">Le type d’objet `Get-Unique` retourné est déterminé par l’entrée.</span><span class="sxs-lookup"><span data-stu-id="b4338-161">The type of object that `Get-Unique` returns is determined by the input.</span></span>

## <span data-ttu-id="b4338-162">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b4338-162">NOTES</span></span>

<span data-ttu-id="b4338-163">Vous pouvez également faire référence à `Get-Unique` par son alias intégré, `gu` .</span><span class="sxs-lookup"><span data-stu-id="b4338-163">You can also refer to `Get-Unique` by its built-in alias, `gu`.</span></span> <span data-ttu-id="b4338-164">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="b4338-164">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="b4338-165">Pour trier une liste, utilisez Sort-Object.</span><span class="sxs-lookup"><span data-stu-id="b4338-165">To sort a list, use Sort-Object.</span></span> <span data-ttu-id="b4338-166">Vous pouvez également utiliser le paramètre **unique** de `Sort-Object` pour rechercher les éléments uniques dans une liste.</span><span class="sxs-lookup"><span data-stu-id="b4338-166">You can also use the **Unique** parameter of `Sort-Object` to find the unique items in a list.</span></span>

## <span data-ttu-id="b4338-167">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b4338-167">RELATED LINKS</span></span>

[<span data-ttu-id="b4338-168">Select-Object</span><span class="sxs-lookup"><span data-stu-id="b4338-168">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="b4338-169">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="b4338-169">Sort-Object</span></span>](Sort-Object.md)

