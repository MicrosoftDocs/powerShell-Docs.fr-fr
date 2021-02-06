---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/compare-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compare-Object
ms.openlocfilehash: 6bed0e8d13cb834fab97dc0265ef7d46a2caea97
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598592"
---
# <span data-ttu-id="be664-102">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="be664-102">Compare-Object</span></span>

## <span data-ttu-id="be664-103">Synopsis</span><span class="sxs-lookup"><span data-stu-id="be664-103">Synopsis</span></span>
<span data-ttu-id="be664-104">Compare deux ensembles d'objets.</span><span class="sxs-lookup"><span data-stu-id="be664-104">Compares two sets of objects.</span></span>

## <span data-ttu-id="be664-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be664-105">Syntax</span></span>

```
Compare-Object [-ReferenceObject] <PSObject[]> [-DifferenceObject] <PSObject[]>
 [-SyncWindow <Int32>] [-Property <Object[]>] [-ExcludeDifferent] [-IncludeEqual] [-PassThru]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="be664-106">Description</span><span class="sxs-lookup"><span data-stu-id="be664-106">Description</span></span>

<span data-ttu-id="be664-107">L' `Compare-Object` applet de commande compare deux ensembles d’objets.</span><span class="sxs-lookup"><span data-stu-id="be664-107">The `Compare-Object` cmdlet compares two sets of objects.</span></span> <span data-ttu-id="be664-108">Un ensemble d’objets est la **référence**, et l’autre ensemble d’objets est la **différence**.</span><span class="sxs-lookup"><span data-stu-id="be664-108">One set of objects is the **reference**, and the other set of objects is the **difference**.</span></span>

<span data-ttu-id="be664-109">`Compare-Object` recherche les méthodes disponibles pour comparer un objet entier.</span><span class="sxs-lookup"><span data-stu-id="be664-109">`Compare-Object` checks for available methods of comparing a whole object.</span></span> <span data-ttu-id="be664-110">S’il ne trouve pas de méthode appropriée, il appelle les méthodes **ToString ()** des objets d’entrée et compare les résultats de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="be664-110">If it can't find a suitable method, it calls the **ToString()** methods of the input objects and compares the string results.</span></span> <span data-ttu-id="be664-111">Vous pouvez fournir une ou plusieurs propriétés à utiliser pour la comparaison.</span><span class="sxs-lookup"><span data-stu-id="be664-111">You can provide one or more properties to be used for comparison.</span></span> <span data-ttu-id="be664-112">Lorsque les propriétés sont fournies, l’applet de commande compare les valeurs de ces propriétés uniquement.</span><span class="sxs-lookup"><span data-stu-id="be664-112">When properties are provided, the cmdlet compares the values of those properties only.</span></span>

<span data-ttu-id="be664-113">Le résultat de la comparaison indique si une valeur de propriété apparaît uniquement dans l’objet de **référence** ( `<=` ) ou uniquement dans l’objet de **différence** ( `=>` ).</span><span class="sxs-lookup"><span data-stu-id="be664-113">The result of the comparison indicates whether a property value appeared only in the **reference** object (`<=`) or only in the **difference** object (`=>`).</span></span> <span data-ttu-id="be664-114">Si le paramètre **includeequal** est utilisé, ( `==` ) indique que la valeur se trouve dans les deux objets.</span><span class="sxs-lookup"><span data-stu-id="be664-114">If the **IncludeEqual** parameter is used, (`==`) indicates the value is in both objects.</span></span>

<span data-ttu-id="be664-115">Si la **référence** ou les objets de **différence** sont null ( `$null` ), `Compare-Object` génère une erreur de fin.</span><span class="sxs-lookup"><span data-stu-id="be664-115">If the **reference** or the **difference** objects are null (`$null`), `Compare-Object` generates a terminating error.</span></span>

<span data-ttu-id="be664-116">Certains exemples utilisent la projection pour réduire la longueur de ligne des exemples de code.</span><span class="sxs-lookup"><span data-stu-id="be664-116">Some examples use splatting to reduce the line length of the code samples.</span></span> <span data-ttu-id="be664-117">Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="be664-117">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="be664-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="be664-118">Examples</span></span>

### <span data-ttu-id="be664-119">Exemple 1 : comparer le contenu de deux fichiers texte</span><span class="sxs-lookup"><span data-stu-id="be664-119">Example 1 - Compare the content of two text files</span></span>

<span data-ttu-id="be664-120">Cet exemple compare le contenu de deux fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="be664-120">This example compares the contents of two text files.</span></span> <span data-ttu-id="be664-121">L’exemple utilise les deux fichiers texte suivants, avec chaque valeur sur une ligne distincte.</span><span class="sxs-lookup"><span data-stu-id="be664-121">The example uses the following two text files, with each value on a separate line.</span></span>

- <span data-ttu-id="be664-122">`Testfile1.txt` contient les valeurs : Dog, Squirrel et oiseau.</span><span class="sxs-lookup"><span data-stu-id="be664-122">`Testfile1.txt` contains the values: dog, squirrel, and bird.</span></span>
- <span data-ttu-id="be664-123">`Testfile2.txt` contient les valeurs : Cat, oiseau et Racoon.</span><span class="sxs-lookup"><span data-stu-id="be664-123">`Testfile2.txt` contains the values: cat, bird, and racoon.</span></span>

<span data-ttu-id="be664-124">La sortie affiche uniquement les lignes qui sont différentes entre les fichiers.</span><span class="sxs-lookup"><span data-stu-id="be664-124">The output displays only the lines that are different between the files.</span></span> <span data-ttu-id="be664-125">`Testfile1.txt` est l’objet de **référence** ( `<=` ) et `Testfile2.txt` est l’objet de **différence** ( `=>` ).</span><span class="sxs-lookup"><span data-stu-id="be664-125">`Testfile1.txt` is the **reference** object (`<=`) and `Testfile2.txt`is the **difference** object (`=>`).</span></span> <span data-ttu-id="be664-126">Les lignes dont le contenu apparaît dans les deux fichiers ne sont pas affichées.</span><span class="sxs-lookup"><span data-stu-id="be664-126">Lines with content that appear in both files aren't displayed.</span></span>

```powershell
Compare-Object -ReferenceObject (Get-Content -Path C:\Test\Testfile1.txt) -DifferenceObject (Get-Content -Path C:\Test\Testfile2.txt)
```

```Output
InputObject SideIndicator
----------- -------------
cat         =>
racoon      =>
dog         <=
squirrel    <=
```

### <span data-ttu-id="be664-127">Exemple 2 : comparer chaque ligne de contenu et exclure les différences</span><span class="sxs-lookup"><span data-stu-id="be664-127">Example 2 - Compare each line of content and exclude the differences</span></span>

<span data-ttu-id="be664-128">Cet exemple utilise le paramètre **ExcludeDifferent** pour comparer chaque ligne de contenu dans deux fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="be664-128">This example uses the **ExcludeDifferent** parameter to compare each line of content in two text files.</span></span>

<span data-ttu-id="be664-129">À partir de PowerShell 7,1, lors de l’utilisation du paramètre **ExcludeDifferent** , **includeequal** est déduit et la sortie contient uniquement les lignes contenues dans les deux fichiers, comme le montre le **SideIndicator** ( `==` ).</span><span class="sxs-lookup"><span data-stu-id="be664-129">As of PowerShell 7.1, when using the **ExcludeDifferent** parameter, **IncludeEqual** is inferred and the output only contains lines contained in both files, as shown by the **SideIndicator** (`==`).</span></span>

```powershell
$objects = @{
  ReferenceObject = (Get-Content -Path C:\Test\Testfile1.txt)
  DifferenceObject = (Get-Content -Path C:\Test\Testfile2.txt)
}
Compare-Object @objects -ExcludeDifferent
```

```Output
InputObject SideIndicator
----------- -------------
bird        ==
```

<a id="ex3" />

### <span data-ttu-id="be664-130">Exemple 3 : afficher la différence lors de l’utilisation du paramètre PassThru</span><span class="sxs-lookup"><span data-stu-id="be664-130">Example 3 - Show the difference when using the PassThru parameter</span></span>

<span data-ttu-id="be664-131">Normalement, `Compare-Object` retourne un type **PSCustomObject** avec les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="be664-131">Normally, `Compare-Object` returns a **PSCustomObject** type with the following properties:</span></span>

- <span data-ttu-id="be664-132">**InputObject** qui est comparé</span><span class="sxs-lookup"><span data-stu-id="be664-132">The **InputObject** being compared</span></span>
- <span data-ttu-id="be664-133">Propriété **SideIndicator** indiquant l’objet d’entrée auquel la sortie appartient</span><span class="sxs-lookup"><span data-stu-id="be664-133">The **SideIndicator** property showing which input object the output belongs to</span></span>

<span data-ttu-id="be664-134">Quand vous utilisez le paramètre **PassThru** , le **type** de l’objet n’est pas modifié, mais l’instance de l’objet retourné a un **NoteProperty** ajouté nommé **SideIndicator**.</span><span class="sxs-lookup"><span data-stu-id="be664-134">When you use the **PassThru** parameter, the **Type** of the object is not changed but the instance of the object returned has an added **NoteProperty** named **SideIndicator**.</span></span> <span data-ttu-id="be664-135">**SideIndicator** affiche l’objet d’entrée auquel la sortie appartient.</span><span class="sxs-lookup"><span data-stu-id="be664-135">**SideIndicator** shows which input object the output belongs to.</span></span>

<span data-ttu-id="be664-136">Les exemples suivants illustrent les différents types de sortie.</span><span class="sxs-lookup"><span data-stu-id="be664-136">The following examples shows the different output types.</span></span>

```powershell
$a = $True
Compare-Object -IncludeEqual $a $a
(Compare-Object -IncludeEqual $a $a) | Get-Member
```

```Output
InputObject SideIndicator
----------- -------------
       True ==

   TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
InputObject   NoteProperty System.Boolean InputObject=True
SideIndicator NoteProperty string SideIndicator===
```

```powershell
Compare-Object -IncludeEqual $a $a -PassThru
(Compare-Object -IncludeEqual $a $a -PassThru) | Get-Member
```

```Output
True

   TypeName: System.Boolean
Name          MemberType   Definition
----          ----------   ----------
CompareTo     Method       int CompareTo(System.Object obj), int CompareTo(bool value), int IComparable.CompareTo(Syst
Equals        Method       bool Equals(System.Object obj), bool Equals(bool obj), bool IEquatable[bool].Equals(bool ot
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
GetTypeCode   Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean     Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte        Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar        Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime    Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal     Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble      Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16       Method       short IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32       Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64       Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte       Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle      Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString      Method       string ToString(), string ToString(System.IFormatProvider provider), string IConvertible.To
ToType        Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16      Method       ushort IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32      Method       uint IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64      Method       ulong IConvertible.ToUInt64(System.IFormatProvider provider)
TryFormat     Method       bool TryFormat(System.Span[char] destination, [ref] int charsWritten)
SideIndicator NoteProperty string SideIndicator===
```

<span data-ttu-id="be664-137">Lors de l’utilisation de **PassThru**, le type d’objet d’origine (**System. Boolean**) est retourné.</span><span class="sxs-lookup"><span data-stu-id="be664-137">When using **PassThru**, the original object type (**System.Boolean**) is returned.</span></span> <span data-ttu-id="be664-138">Notez que la sortie affichée par le format par défaut pour les objets **System. Boolean** n’a pas affiché la propriété **SideIndicator** .</span><span class="sxs-lookup"><span data-stu-id="be664-138">Note how the output displayed by the default format for **System.Boolean** objects didn't display the **SideIndicator** property.</span></span> <span data-ttu-id="be664-139">Toutefois, l’objet **System. Boolean** retourné a le **NoteProperty** ajouté.</span><span class="sxs-lookup"><span data-stu-id="be664-139">However, the returned **System.Boolean** object has the added **NoteProperty**.</span></span>

### <span data-ttu-id="be664-140">Exemple 4-comparer deux objets simples à l’aide de propriétés</span><span class="sxs-lookup"><span data-stu-id="be664-140">Example 4 - Compare two simple objects using properties</span></span>

<span data-ttu-id="be664-141">Dans cet exemple, nous comparons deux chaînes différentes qui ont la même longueur.</span><span class="sxs-lookup"><span data-stu-id="be664-141">In this example, we compare two different string that have the same length.</span></span>

```powershell
Compare-Object -ReferenceObject 'abc' -DifferenceObject 'xyz' -Property Length -IncludeEqual
```

```Output
Length SideIndicator
------ -------------
     3 ==
```

### <span data-ttu-id="be664-142">Exemple 5 : comparaison d’objets complexes à l’aide de propriétés</span><span class="sxs-lookup"><span data-stu-id="be664-142">Example 5 - Comparing complex objects using properties</span></span>

<span data-ttu-id="be664-143">Cet exemple illustre le comportement de la comparaison d’objets complexes.</span><span class="sxs-lookup"><span data-stu-id="be664-143">This example shows the behavior when comparing complex objects.</span></span> <span data-ttu-id="be664-144">Dans cet exemple, nous stockons deux objets de processus différents pour différentes instances de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="be664-144">In this example we store two different process objects for different instances of PowerShell.</span></span> <span data-ttu-id="be664-145">Les deux variables contiennent des objets de processus portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="be664-145">Both variables contain process objects with the same name.</span></span> <span data-ttu-id="be664-146">Lorsque les objets sont comparés sans spécifier le paramètre **Property** , l’applet de commande considère que les objets sont égaux.</span><span class="sxs-lookup"><span data-stu-id="be664-146">When the objects are compared without specifying the **Property** parameter, the cmdlet considers the objects to be equal.</span></span> <span data-ttu-id="be664-147">Notez que la valeur de l' **InputObject** est identique à celle du résultat de la méthode **ToString ()** .</span><span class="sxs-lookup"><span data-stu-id="be664-147">Notice that the value of the **InputObject** is the same as the result of the **ToString()** method.</span></span> <span data-ttu-id="be664-148">Étant donné que la classe **System. Diagnostics. Process** n’a pas l’interface **IComparable** , l’applet de commande convertit les objets en chaînes, puis compare les résultats.</span><span class="sxs-lookup"><span data-stu-id="be664-148">Since the **System.Diagnostics.Process** class does not have the **IComparable** interface, the cmdlet converts the objects to strings then compares the results.</span></span>

```powershell
PS> Get-Process pwsh

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    101   123.32     139.10      35.81   11168   1 pwsh
     89   107.55      66.97      11.44   17600   1 pwsh

PS> $a = Get-Process -Id 11168
PS> $b = Get-Process -Id 17600
PS> $a.ToString()
System.Diagnostics.Process (pwsh)
PS> $b.ToString()
System.Diagnostics.Process (pwsh)
PS> Compare-Object $a $b -IncludeEqual

InputObject                       SideIndicator
-----------                       -------------
System.Diagnostics.Process (pwsh) ==

PS> Compare-Object $a $b -Property ProcessName, Id, CPU

ProcessName    Id       CPU SideIndicator
-----------    --       --- -------------
pwsh        17600   11.4375 =>
pwsh        11168 36.203125 <=
```

<span data-ttu-id="be664-149">Lorsque vous spécifiez des propriétés à comparer, l’applet de commande affiche les différences.</span><span class="sxs-lookup"><span data-stu-id="be664-149">When you specify properties to be compared, the cmdlet shows the differences.</span></span>

### <span data-ttu-id="be664-150">Exemple 6 : comparaison d’objets complexes qui implémentent IComparable</span><span class="sxs-lookup"><span data-stu-id="be664-150">Example 6 - Comparing complex objects that implement IComparable</span></span>

<span data-ttu-id="be664-151">Si l’objet implémente **IComparable**, l’applet de commande recherche les façons de comparer les objets. Si les objets sont de types différents, l’objet de **différence** est converti en type de **ReferenceObject** , puis comparé.</span><span class="sxs-lookup"><span data-stu-id="be664-151">If the object implements **IComparable**, the cmdlet searches for ways to compare the objects.If the objects are different types, the **Difference** object is converted to the type of the **ReferenceObject** then compared.</span></span>

<span data-ttu-id="be664-152">Dans cet exemple, nous comparons une chaîne à un objet **TimeSpan** .</span><span class="sxs-lookup"><span data-stu-id="be664-152">In this example, we are comparing a string to a **TimeSpan** object.</span></span> <span data-ttu-id="be664-153">Dans le premier cas, la chaîne est convertie en **intervalle** de temps, de sorte que les objets sont égaux.</span><span class="sxs-lookup"><span data-stu-id="be664-153">In the first case, the string is converted to a **TimeSpan** so the objects are equal.</span></span>

```powershell
Compare-Object ([TimeSpan]"0:0:1") "0:0:1" -IncludeEqual
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    ==
```

```powershell
Compare-Object "0:0:1" ([TimeSpan]"0:0:1")
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    =>
0:0:1       <=
```

<span data-ttu-id="be664-154">Dans le deuxième cas, la valeur **TimeSpan** est convertie en une chaîne, de sorte que l’objet est différent.</span><span class="sxs-lookup"><span data-stu-id="be664-154">In the second case, the **TimeSpan** is converted to a string so the object are different.</span></span>

## <span data-ttu-id="be664-155">Paramètres</span><span class="sxs-lookup"><span data-stu-id="be664-155">Parameters</span></span>

### <span data-ttu-id="be664-156">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="be664-156">-CaseSensitive</span></span>

<span data-ttu-id="be664-157">Indique que les comparaisons doivent respecter la casse.</span><span class="sxs-lookup"><span data-stu-id="be664-157">Indicates that comparisons should be case-sensitive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be664-158">-Culture</span><span class="sxs-lookup"><span data-stu-id="be664-158">-Culture</span></span>

<span data-ttu-id="be664-159">Spécifie la culture à utiliser pour les comparaisons.</span><span class="sxs-lookup"><span data-stu-id="be664-159">Specifies the culture to use for comparisons.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be664-160">-DifferenceObject</span><span class="sxs-lookup"><span data-stu-id="be664-160">-DifferenceObject</span></span>

<span data-ttu-id="be664-161">Spécifie les objets qui sont comparés aux objets de **référence** .</span><span class="sxs-lookup"><span data-stu-id="be664-161">Specifies the objects that are compared to the **reference** objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="be664-162">-ExcludeDifferent</span><span class="sxs-lookup"><span data-stu-id="be664-162">-ExcludeDifferent</span></span>

<span data-ttu-id="be664-163">Indique que cette applet de commande affiche uniquement les caractéristiques des objets comparés qui sont égaux.</span><span class="sxs-lookup"><span data-stu-id="be664-163">Indicates that this cmdlet displays only the characteristics of compared objects that are equal.</span></span> <span data-ttu-id="be664-164">Les différences entre les objets sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="be664-164">The differences between the objects are discarded.</span></span>

<span data-ttu-id="be664-165">Utilisez **ExcludeDifferent** avec **includeequal** pour afficher uniquement les lignes qui correspondent entre les objets de **référence** et les objets de **différence** .</span><span class="sxs-lookup"><span data-stu-id="be664-165">Use **ExcludeDifferent** with **IncludeEqual** to display only the lines that match between the **reference** and **difference** objects.</span></span>

<span data-ttu-id="be664-166">Si **ExcludeDifferent** est spécifié sans **includeequal**, il n’y a pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="be664-166">If **ExcludeDifferent** is specified without **IncludeEqual**, there's no output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be664-167">-IncludeEqual</span><span class="sxs-lookup"><span data-stu-id="be664-167">-IncludeEqual</span></span>

<span data-ttu-id="be664-168">**Includeequal** affiche les correspondances entre les objets de **référence** et les objets de **différence** .</span><span class="sxs-lookup"><span data-stu-id="be664-168">**IncludeEqual** displays the matches between the **reference** and **difference** objects.</span></span>

<span data-ttu-id="be664-169">Par défaut, la sortie comprend également les différences entre les objets de **référence** et les objets de **différence** .</span><span class="sxs-lookup"><span data-stu-id="be664-169">By default, the output also includes the differences between the **reference** and **difference** objects.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be664-170">-PassThru</span><span class="sxs-lookup"><span data-stu-id="be664-170">-PassThru</span></span>

<span data-ttu-id="be664-171">Quand vous utilisez le paramètre **PassThru** , `Compare-Object` omet le wrapper **PSCustomObject** autour des objets comparés et retourne les objets différents, inchangés.</span><span class="sxs-lookup"><span data-stu-id="be664-171">When you use the **PassThru** parameter, `Compare-Object` omits the **PSCustomObject** wrapper around the compared objects and returns the differing objects, unchanged.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be664-172">-Propriété</span><span class="sxs-lookup"><span data-stu-id="be664-172">-Property</span></span>

<span data-ttu-id="be664-173">Spécifie un tableau de propriétés des objets de **référence** et de **différence** à comparer.</span><span class="sxs-lookup"><span data-stu-id="be664-173">Specifies an array of properties of the **reference** and **difference** objects to compare.</span></span>

<span data-ttu-id="be664-174">La valeur du paramètre **Property** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="be664-174">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="be664-175">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="be664-175">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="be664-176">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="be664-176">Valid key-value pairs are:</span></span>

- <span data-ttu-id="be664-177">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="be664-177">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="be664-178">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="be664-178">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be664-179">-ReferenceObject</span><span class="sxs-lookup"><span data-stu-id="be664-179">-ReferenceObject</span></span>

<span data-ttu-id="be664-180">Spécifie un tableau d’objets utilisés comme référence pour la comparaison.</span><span class="sxs-lookup"><span data-stu-id="be664-180">Specifies an array of objects used as a reference for comparison.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be664-181">-SyncWindow</span><span class="sxs-lookup"><span data-stu-id="be664-181">-SyncWindow</span></span>

<span data-ttu-id="be664-182">Spécifie le nombre d’objets adjacents `Compare-Object` inspectés lors de la recherche d’une correspondance dans une collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="be664-182">Specifies the number of adjacent objects that `Compare-Object` inspects while looking for a match in a collection of objects.</span></span> <span data-ttu-id="be664-183">`Compare-Object` examine les objets adjacents lorsqu’il ne trouve pas l’objet à la même position dans une collection.</span><span class="sxs-lookup"><span data-stu-id="be664-183">`Compare-Object` examines adjacent objects when it doesn't find the object in the same position in a collection.</span></span> <span data-ttu-id="be664-184">La valeur par défaut est, ce qui `[Int32]::MaxValue` signifie que `Compare-Object` examine la collection d’objets entière.</span><span class="sxs-lookup"><span data-stu-id="be664-184">The default value is `[Int32]::MaxValue`, which means that `Compare-Object` examines the entire object collection.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: [Int32]::MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be664-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="be664-185">CommonParameters</span></span>

<span data-ttu-id="be664-186">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="be664-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="be664-187">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="be664-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="be664-188">Entrées</span><span class="sxs-lookup"><span data-stu-id="be664-188">Inputs</span></span>

### <span data-ttu-id="be664-189">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="be664-189">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="be664-190">Vous pouvez envoyer un objet dans le pipeline au paramètre **differenceobject** .</span><span class="sxs-lookup"><span data-stu-id="be664-190">You can send an object down the pipeline to the **DifferenceObject** parameter.</span></span>

## <span data-ttu-id="be664-191">Sorties</span><span class="sxs-lookup"><span data-stu-id="be664-191">Outputs</span></span>

### <span data-ttu-id="be664-192">None</span><span class="sxs-lookup"><span data-stu-id="be664-192">None</span></span>

<span data-ttu-id="be664-193">Si l’objet de **référence** et l’objet de **différence** sont identiques, il n’y a pas de sortie, sauf si vous utilisez le paramètre **includeequal** .</span><span class="sxs-lookup"><span data-stu-id="be664-193">If the **reference** object and the **difference** object are the same, there's no output, unless you use the **IncludeEqual** parameter.</span></span>

### <span data-ttu-id="be664-194">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="be664-194">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="be664-195">Si les objets sont différents, `Compare-Object` encapsule les objets qui diffèrent dans un `PSCustomObject` wrapper avec une propriété **SideIndicator** pour référencer les différences.</span><span class="sxs-lookup"><span data-stu-id="be664-195">If the objects are different, `Compare-Object` wraps the differing objects in a `PSCustomObject` wrapper with a **SideIndicator** property to reference the differences.</span></span>

<span data-ttu-id="be664-196">Quand vous utilisez le paramètre **PassThru** , le **type** de l’objet n’est pas modifié, mais l’instance de l’objet retourné a un **NoteProperty** ajouté nommé **SideIndicator**.</span><span class="sxs-lookup"><span data-stu-id="be664-196">When you use the **PassThru** parameter, the **Type** of the object is not changed but the instance of the object returned has an added **NoteProperty** named **SideIndicator**.</span></span> <span data-ttu-id="be664-197">**SideIndicator** affiche l’objet d’entrée auquel la sortie appartient.</span><span class="sxs-lookup"><span data-stu-id="be664-197">**SideIndicator** shows which input object the output belongs to.</span></span>

## <span data-ttu-id="be664-198">Notes</span><span class="sxs-lookup"><span data-stu-id="be664-198">Notes</span></span>

<span data-ttu-id="be664-199">Lors de l’utilisation du paramètre **PassThru** , la sortie affichée dans la console peut ne pas inclure la propriété **SideIndicator** .</span><span class="sxs-lookup"><span data-stu-id="be664-199">When using the **PassThru** parameter, the output displayed in the console may not include the **SideIndicator** property.</span></span> <span data-ttu-id="be664-200">L’affichage de format par défaut de pour le type d’objet généré par `Compare-Object` n’inclut pas la propriété **SideIndicator** .</span><span class="sxs-lookup"><span data-stu-id="be664-200">The default format view of the for the object type output by `Compare-Object` does not include the **SideIndicator** property.</span></span> <span data-ttu-id="be664-201">Pour plus d’informations, consultez l' [exemple 3](#ex3) de cet article.</span><span class="sxs-lookup"><span data-stu-id="be664-201">For more information see [Example 3](#ex3) in this article.</span></span>

## <span data-ttu-id="be664-202">Liens connexes</span><span class="sxs-lookup"><span data-stu-id="be664-202">Related links</span></span>

[<span data-ttu-id="be664-203">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="be664-203">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="be664-204">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="be664-204">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="be664-205">Group-Object</span><span class="sxs-lookup"><span data-stu-id="be664-205">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="be664-206">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="be664-206">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="be664-207">New-Object</span><span class="sxs-lookup"><span data-stu-id="be664-207">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="be664-208">Select-Object</span><span class="sxs-lookup"><span data-stu-id="be664-208">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="be664-209">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="be664-209">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="be664-210">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="be664-210">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="be664-211">Where-Object</span><span class="sxs-lookup"><span data-stu-id="be664-211">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

[<span data-ttu-id="be664-212">Get-Process</span><span class="sxs-lookup"><span data-stu-id="be664-212">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)
