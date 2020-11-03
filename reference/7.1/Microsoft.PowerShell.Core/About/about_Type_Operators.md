---
description: Décrit les opérateurs qui fonctionnent avec les types de Microsoft .NET.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Operators
ms.openlocfilehash: 829dfbbf2cd02c1bf4f1616b49f01f8f079d7d0e
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208501"
---
# <a name="about-type-operators"></a><span data-ttu-id="024e1-104">À propos des opérateurs de type</span><span class="sxs-lookup"><span data-stu-id="024e1-104">About Type Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="024e1-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="024e1-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="024e1-106">Décrit les opérateurs qui fonctionnent avec les types de Microsoft .NET.</span><span class="sxs-lookup"><span data-stu-id="024e1-106">Describes the operators that work with Microsoft .NET types.</span></span>

## <a name="long-description"></a><span data-ttu-id="024e1-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="024e1-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="024e1-108">Les opérateurs de type booléen ( `-is` et `-isNot` ) indiquent si un objet est une instance d’un type .net spécifié.</span><span class="sxs-lookup"><span data-stu-id="024e1-108">The Boolean type operators (`-is` and `-isNot`) tell whether an object is an instance of a specified .NET type.</span></span> <span data-ttu-id="024e1-109">L' `-is` opérateur retourne la valeur **true** si le type correspond à et la valeur **false** dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="024e1-109">The `-is` operator returns a value of **TRUE** if the type matches and a value of **FALSE** otherwise.</span></span> <span data-ttu-id="024e1-110">L' `-isNot` opérateur retourne la valeur **false** si le type correspond à et la valeur **true** dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="024e1-110">The `-isNot` operator returns a value of **FALSE** if the type matches and a value of **TRUE** otherwise.</span></span>

<span data-ttu-id="024e1-111">L' `-as` opérateur tente de convertir l’objet d’entrée dans le type .net spécifié.</span><span class="sxs-lookup"><span data-stu-id="024e1-111">The `-as` operator tries to convert the input object to the specified .NET type.</span></span> <span data-ttu-id="024e1-112">Si elle réussit, elle retourne l’objet converti.</span><span class="sxs-lookup"><span data-stu-id="024e1-112">If it succeeds, it returns the converted object.</span></span> <span data-ttu-id="024e1-113">En cas d’échec, elle retourne `$null` .</span><span class="sxs-lookup"><span data-stu-id="024e1-113">If it fails, it returns `$null`.</span></span> <span data-ttu-id="024e1-114">Elle ne retourne pas d’erreur.</span><span class="sxs-lookup"><span data-stu-id="024e1-114">It does not return an error.</span></span>

<span data-ttu-id="024e1-115">Le tableau suivant répertorie les opérateurs de type dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="024e1-115">The following table lists the type operators in PowerShell.</span></span>

|<span data-ttu-id="024e1-116">Opérateur</span><span class="sxs-lookup"><span data-stu-id="024e1-116">Operator</span></span>|<span data-ttu-id="024e1-117">Description</span><span class="sxs-lookup"><span data-stu-id="024e1-117">Description</span></span>                |<span data-ttu-id="024e1-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="024e1-118">Example</span></span>                          |
|--------|---------------------------|---------------------------------|
|`-is`   |<span data-ttu-id="024e1-119">Retourne la valeur TRUE lorsque l’entrée</span><span class="sxs-lookup"><span data-stu-id="024e1-119">Returns TRUE when the input</span></span>|`(get-date) -is [DateTime]`      |
|        |<span data-ttu-id="024e1-120">est une instance du</span><span class="sxs-lookup"><span data-stu-id="024e1-120">is an instance of the</span></span>      |`True`                           |
|        |<span data-ttu-id="024e1-121">type .NET spécifié.</span><span class="sxs-lookup"><span data-stu-id="024e1-121">specified .NET type.</span></span>       |                                 |
|`-isNot`|<span data-ttu-id="024e1-122">Retourne la valeur TRUE lorsque l’entrée</span><span class="sxs-lookup"><span data-stu-id="024e1-122">Returns TRUE when the input</span></span>|`(get-date) -isNot [DateTime]`   |
|        |<span data-ttu-id="024e1-123">n’est pas une instance du</span><span class="sxs-lookup"><span data-stu-id="024e1-123">not an instance of the</span></span>     |`False`                          |
|        |<span data-ttu-id="024e1-124">type de specified.NET.</span><span class="sxs-lookup"><span data-stu-id="024e1-124">specified.NET type.</span></span>        |                                 |
|`-as`   |<span data-ttu-id="024e1-125">Convertit l’entrée en</span><span class="sxs-lookup"><span data-stu-id="024e1-125">Converts the input to the</span></span>  |`"5/7/07" -as [DateTime]`        |
|        |<span data-ttu-id="024e1-126">type .NET spécifié.</span><span class="sxs-lookup"><span data-stu-id="024e1-126">specified .NET type.</span></span>       |`Monday, May 7, 2007 12:00:00 AM`|

<span data-ttu-id="024e1-127">La syntaxe des opérateurs de type est la suivante :</span><span class="sxs-lookup"><span data-stu-id="024e1-127">The syntax of the type operators is as follows:</span></span>

```powershell
<input> <operator> [.NET type]
```

<span data-ttu-id="024e1-128">Vous pouvez également utiliser la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="024e1-128">You can also use the following syntax:</span></span>

```powershell
<input> <operator> ".NET type"
```

<span data-ttu-id="024e1-129">Le type .NET peut être écrit sous la forme d’un nom de type entre crochets ou une chaîne, telle que `[DateTime]` ou `"DateTime"` pour **System. DateTime** .</span><span class="sxs-lookup"><span data-stu-id="024e1-129">The .NET type can be written as a type name in brackets or a string, such as `[DateTime]` or `"DateTime"` for **System.DateTime** .</span></span> <span data-ttu-id="024e1-130">Si le type ne se trouve pas à la racine de l’espace de noms System, spécifiez le nom complet du type d’objet.</span><span class="sxs-lookup"><span data-stu-id="024e1-130">If the type is not at the root of the system namespace, specify the full name of the object type.</span></span> <span data-ttu-id="024e1-131">Vous pouvez omettre « System. ».</span><span class="sxs-lookup"><span data-stu-id="024e1-131">You can omit "System.".</span></span> <span data-ttu-id="024e1-132">Par exemple, pour spécifier **System. Diagnostics. Process** , entrez `[System.Diagnostics.Process]` , `[Diagnostics.Process]` ou `"Diagnostics.Process"` .</span><span class="sxs-lookup"><span data-stu-id="024e1-132">For example, to specify **System.Diagnostics.Process** , enter `[System.Diagnostics.Process]`, `[Diagnostics.Process]`, or `"Diagnostics.Process"`.</span></span>

<span data-ttu-id="024e1-133">Les opérateurs de type opèrent toujours sur l’objet d’entrée dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="024e1-133">The type operators always operate on the input object as a whole.</span></span> <span data-ttu-id="024e1-134">Autrement dit, si l’objet d’entrée est une collection, il s’agit du type de _collection_ qui est testé, et non des types des _éléments_ de la collection.</span><span class="sxs-lookup"><span data-stu-id="024e1-134">That is, if the input object is a collection, it is the _collection_ type that is tested, not the types of the collection's _elements_ .</span></span>

### <a name="-isisnot-operators"></a><span data-ttu-id="024e1-135">-is/isNot, opérateurs</span><span class="sxs-lookup"><span data-stu-id="024e1-135">-is/isNot operators</span></span>

<span data-ttu-id="024e1-136">Les opérateurs de type **booléen** ( `-is` et `-isNot` ) retournent toujours une valeur **booléenne** , même si l’entrée est une collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="024e1-136">The **Boolean** type operators (`-is` and `-isNot`) always return a **Boolean** value, even if the input is a collection of objects.</span></span>

<span data-ttu-id="024e1-137">Si `<input>` est un type qui est identique à ou qui est _dérivé_ du type .net, l' `-is` opérateur retourne `$True` .</span><span class="sxs-lookup"><span data-stu-id="024e1-137">If `<input>` is a type that is the same as or is _derived_ from the .NET Type, the `-is` operator returns `$True`.</span></span>

<span data-ttu-id="024e1-138">Par exemple, le type **DirectoryInfo** est dérivé du type **FileSystemInfo** .</span><span class="sxs-lookup"><span data-stu-id="024e1-138">For example, the **DirectoryInfo** type is derived from the **FileSystemInfo** type.</span></span> <span data-ttu-id="024e1-139">Par conséquent, ces deux exemples renvoient la **valeur true** .</span><span class="sxs-lookup"><span data-stu-id="024e1-139">Therefore, both of these examples return **True** .</span></span>

```powershell
PS> (Get-Item /) -is [System.IO.DirectoryInfo]
True
PS> (Get-Item /) -is [System.IO.FileSystemInfo]
True
```

<span data-ttu-id="024e1-140">L' `-is` opérateur peut également faire correspondre des interfaces si `<input>` implémente l’interface dans la comparaison.</span><span class="sxs-lookup"><span data-stu-id="024e1-140">The `-is` operator can also match interfaces if the `<input>` implements the interface in the comparison.</span></span> <span data-ttu-id="024e1-141">Dans cet exemple, l’entrée est un tableau.</span><span class="sxs-lookup"><span data-stu-id="024e1-141">In this example, the input is an array.</span></span> <span data-ttu-id="024e1-142">Les tableaux implémentent l’interface **System. Collections. IList** .</span><span class="sxs-lookup"><span data-stu-id="024e1-142">Arrays implement the **System.Collections.IList** interface.</span></span>

```powershell
PS> 1, 2 -is [System.Collections.IList]
True
```

### <a name="-as-operator"></a><span data-ttu-id="024e1-143">opérateur as</span><span class="sxs-lookup"><span data-stu-id="024e1-143">-as operator</span></span>

<span data-ttu-id="024e1-144">L' `-as` opérateur tente de convertir l’objet d’entrée dans le type .net spécifié.</span><span class="sxs-lookup"><span data-stu-id="024e1-144">The `-as` operator tries to convert the input object to the specified .NET type.</span></span> <span data-ttu-id="024e1-145">Si elle réussit, elle retourne l’objet converti.</span><span class="sxs-lookup"><span data-stu-id="024e1-145">If it succeeds, it returns the converted object.</span></span> <span data-ttu-id="024e1-146">En cas d’échec, elle retourne `$null` .</span><span class="sxs-lookup"><span data-stu-id="024e1-146">It if fails, it returns `$null`.</span></span> <span data-ttu-id="024e1-147">Elle ne retourne pas d’erreur.</span><span class="sxs-lookup"><span data-stu-id="024e1-147">It does not return an error.</span></span>

<span data-ttu-id="024e1-148">Si le `<input>` est un type _dérivé_ du type .net, `-as` _passe par_ l’objet d’entrée retourné inchangé.</span><span class="sxs-lookup"><span data-stu-id="024e1-148">If the `<input>` is a type that is _derived_ from the .NET Type `-as` _passes through_ returns input object unchanged.</span></span> <span data-ttu-id="024e1-149">Par exemple, le type **DirectoryInfo** est dérivé du type **FileSystemInfo** .</span><span class="sxs-lookup"><span data-stu-id="024e1-149">For example, the **DirectoryInfo** type is derived from the **FileSystemInfo** type.</span></span> <span data-ttu-id="024e1-150">Par conséquent, le type d’objet est inchangé dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="024e1-150">Therefore, the object type is unchanged in the following example:</span></span>

```powershell
PS> $fsroot = (Get-Item /) -as [System.IO.FileSystemInfo]
PS> $fsroot.GetType().FullName
System.IO.DirectoryInfo
```

#### <a name="converting-the-datetime-type-is-culture-sensitive"></a><span data-ttu-id="024e1-151">La conversion du type DateTime est dépendante de la culture</span><span class="sxs-lookup"><span data-stu-id="024e1-151">Converting the DateTime type is culture-sensitive</span></span>

<span data-ttu-id="024e1-152">Contrairement au cast de type, `[DateTime]` la conversion en type à l’aide de l' `-as` opérateur fonctionne uniquement avec les chaînes mises en forme selon les règles de la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="024e1-152">Unlike type casting, converting to `[DateTime]` type using the `-as` operator only works with strings that are formatted according to the rules of the current culture.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr-FR'
PS> '13/5/20' -as [datetime]

mercredi 13 mai 2020 00:00:00

PS> '05/13/20' -as [datetime]
PS> [datetime]'05/13/20'

mercredi 13 mai 2020 00:00:00

PS> [datetime]'13/05/20'
InvalidArgument: Cannot convert value "13/05/20" to type "System.DateTime".
Error: "String '13/05/20' was not recognized as a valid DateTime."
```

<span data-ttu-id="024e1-153">Pour rechercher le type .NET d’un objet, utilisez l' `Get-Member` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="024e1-153">To find the .NET type of an object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="024e1-154">Ou bien, utilisez la méthode **GetType** de tous les objets avec la propriété **FullName** de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="024e1-154">Or, use the **GetType** method of all the objects together with the **FullName** property of this method.</span></span> <span data-ttu-id="024e1-155">Par exemple, l’instruction suivante obtient le type de la valeur de retour d’une `Get-Culture` commande :</span><span class="sxs-lookup"><span data-stu-id="024e1-155">For example, the following statement gets the type of the return value of a `Get-Culture` command:</span></span>

```powershell
PS> (Get-Culture).GetType().FullName
System.Globalization.CultureInfo
```

## <a name="examples"></a><span data-ttu-id="024e1-156">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="024e1-156">EXAMPLES</span></span>

<span data-ttu-id="024e1-157">Les exemples suivants illustrent certaines utilisations des opérateurs de type :</span><span class="sxs-lookup"><span data-stu-id="024e1-157">The following examples show some uses of the Type operators:</span></span>

```powershell
PS> 32 -is [Float]
False

PS> 32 -is "int"
True

PS> (get-date) -is [DateTime]
True

PS> "12/31/2007" -is [DateTime]
False

PS> "12/31/2007" -is [String]
True

PS> (get-process PowerShell)[0] -is [System.Diagnostics.Process]
True

PS> (get-command get-member) -is [System.Management.Automation.CmdletInfo]
True
```

<span data-ttu-id="024e1-158">L’exemple suivant montre que lorsque l’entrée est une collection d’objets, le type de correspondance est le type .NET de la collection, et non le type des objets individuels dans la collection.</span><span class="sxs-lookup"><span data-stu-id="024e1-158">The following example shows that when the input is a collection of objects, the matching type is the .NET type of the collection, not the type of the individual objects in the collection.</span></span>

<span data-ttu-id="024e1-159">Dans cet exemple, bien que les `Get-Culture` `Get-UICulture` applets de commande et retournent des objets **System. Globalization. CultureInfo** , une collection de ces objets est un tableau System. Object.</span><span class="sxs-lookup"><span data-stu-id="024e1-159">In this example, although both the `Get-Culture` and `Get-UICulture` cmdlets return **System.Globalization.CultureInfo** objects, a collection of these objects is a System.Object array.</span></span>

```powershell
PS> (get-culture) -is [System.Globalization.CultureInfo]
True

PS> (get-uiculture) -is [System.Globalization.CultureInfo]
True

PS> (get-culture), (get-uiculture) -is [System.Globalization.CultureInfo]
False

PS> (get-culture), (get-uiculture) -is [Array]
True

PS> (get-culture), (get-uiculture) | foreach {
  $_ -is [System.Globalization.CultureInfo])
}
True
True

PS> (get-culture), (get-uiculture) -is [Object]
True
```

<span data-ttu-id="024e1-160">Les exemples suivants montrent comment utiliser l' `-as` opérateur.</span><span class="sxs-lookup"><span data-stu-id="024e1-160">The following examples show how to use the `-as` operator.</span></span>

```powershell
PS> "12/31/07" -is [DateTime]
False

PS> "12/31/07" -as [DateTime]
Monday, December 31, 2007 12:00:00 AM

PS> $date = "12/31/07" -as [DateTime]

C:\PS>$a -is [DateTime]
True

PS> 1031 -as [System.Globalization.CultureInfo]

LCID      Name      DisplayName
----      ----      -----------
1031      de-DE     German (Germany)
```

<span data-ttu-id="024e1-161">L’exemple suivant montre que lorsque l' `-as` opérateur ne peut pas convertir l’objet d’entrée en type .net, il retourne `$null` .</span><span class="sxs-lookup"><span data-stu-id="024e1-161">The following example shows that when the `-as` operator cannot convert the input object to the .NET type, it returns `$null`.</span></span>

```powershell
PS> 1031 -as [System.Diagnostics.Process]
PS>
```

## <a name="see-also"></a><span data-ttu-id="024e1-162">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="024e1-162">SEE ALSO</span></span>

[<span data-ttu-id="024e1-163">about_Operators</span><span class="sxs-lookup"><span data-stu-id="024e1-163">about_Operators</span></span>](about_Operators.md)
