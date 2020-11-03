---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/compare-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compare-Object
ms.openlocfilehash: c72cde8e626993726ae1a52206c88e20c3a7c588
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "93208902"
---
# <span data-ttu-id="01ac2-103">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="01ac2-103">Compare-Object</span></span>

## <span data-ttu-id="01ac2-104">Synopsis</span><span class="sxs-lookup"><span data-stu-id="01ac2-104">Synopsis</span></span>
<span data-ttu-id="01ac2-105">Compare deux ensembles d'objets.</span><span class="sxs-lookup"><span data-stu-id="01ac2-105">Compares two sets of objects.</span></span>

## <span data-ttu-id="01ac2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01ac2-106">Syntax</span></span>

```
Compare-Object [-ReferenceObject] <PSObject[]> [-DifferenceObject] <PSObject[]>
 [-SyncWindow <Int32>] [-Property <Object[]>] [-ExcludeDifferent] [-IncludeEqual] [-PassThru]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="01ac2-107">Description</span><span class="sxs-lookup"><span data-stu-id="01ac2-107">Description</span></span>

<span data-ttu-id="01ac2-108">L' `Compare-Object` applet de commande compare deux ensembles d’objets.</span><span class="sxs-lookup"><span data-stu-id="01ac2-108">The `Compare-Object` cmdlet compares two sets of objects.</span></span> <span data-ttu-id="01ac2-109">Un ensemble d’objets est la **référence** , et l’autre ensemble d’objets est la **différence**.</span><span class="sxs-lookup"><span data-stu-id="01ac2-109">One set of objects is the **reference** , and the other set of objects is the **difference**.</span></span>

<span data-ttu-id="01ac2-110">`Compare-Object` recherche les méthodes disponibles pour comparer un objet entier.</span><span class="sxs-lookup"><span data-stu-id="01ac2-110">`Compare-Object` checks for available methods of comparing a whole object.</span></span> <span data-ttu-id="01ac2-111">S’il ne trouve pas de méthode appropriée, il appelle les méthodes **ToString ()** des objets d’entrée et compare les résultats de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="01ac2-111">If it can't find a suitable method, it calls the **ToString()** methods of the input objects and compares the string results.</span></span> <span data-ttu-id="01ac2-112">Vous pouvez fournir une ou plusieurs propriétés à utiliser pour la comparaison.</span><span class="sxs-lookup"><span data-stu-id="01ac2-112">You can provide one or more properties to be used for comparison.</span></span> <span data-ttu-id="01ac2-113">Lorsque les propriétés sont fournies, l’applet de commande compare les valeurs de ces propriétés uniquement.</span><span class="sxs-lookup"><span data-stu-id="01ac2-113">When properties are provided, the cmdlet compares the values of those properties only.</span></span>

<span data-ttu-id="01ac2-114">Le résultat de la comparaison indique si une valeur de propriété apparaît uniquement dans l’objet de **référence** ( `<=` ) ou uniquement dans l’objet de **différence** ( `=>` ).</span><span class="sxs-lookup"><span data-stu-id="01ac2-114">The result of the comparison indicates whether a property value appeared only in the **reference** object (`<=`) or only in the **difference** object (`=>`).</span></span> <span data-ttu-id="01ac2-115">Si le paramètre **includeequal** est utilisé, ( `==` ) indique que la valeur se trouve dans les deux objets.</span><span class="sxs-lookup"><span data-stu-id="01ac2-115">If the **IncludeEqual** parameter is used, (`==`) indicates the value is in both objects.</span></span>

<span data-ttu-id="01ac2-116">Si la **référence** ou les objets de **différence** sont null ( `$null` ), `Compare-Object` génère une erreur de fin.</span><span class="sxs-lookup"><span data-stu-id="01ac2-116">If the **reference** or the **difference** objects are null (`$null`), `Compare-Object` generates a terminating error.</span></span>

<span data-ttu-id="01ac2-117">Certains exemples utilisent la projection pour réduire la longueur de ligne des exemples de code.</span><span class="sxs-lookup"><span data-stu-id="01ac2-117">Some examples use splatting to reduce the line length of the code samples.</span></span> <span data-ttu-id="01ac2-118">Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="01ac2-118">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="01ac2-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="01ac2-119">Examples</span></span>

### <span data-ttu-id="01ac2-120">Exemple 1 : comparer le contenu de deux fichiers texte</span><span class="sxs-lookup"><span data-stu-id="01ac2-120">Example 1 - Compare the content of two text files</span></span>

<span data-ttu-id="01ac2-121">Cet exemple compare le contenu de deux fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="01ac2-121">This example compares the contents of two text files.</span></span> <span data-ttu-id="01ac2-122">L’exemple utilise les deux fichiers texte suivants, avec chaque valeur sur une ligne distincte.</span><span class="sxs-lookup"><span data-stu-id="01ac2-122">The example uses the following two text files, with each value on a separate line.</span></span>

- <span data-ttu-id="01ac2-123">`Testfile1.txt` contient les valeurs : Dog, Squirrel et oiseau.</span><span class="sxs-lookup"><span data-stu-id="01ac2-123">`Testfile1.txt` contains the values: dog, squirrel, and bird.</span></span>
- <span data-ttu-id="01ac2-124">`Testfile2.txt` contient les valeurs : Cat, oiseau et Racoon.</span><span class="sxs-lookup"><span data-stu-id="01ac2-124">`Testfile2.txt` contains the values: cat, bird, and racoon.</span></span>

<span data-ttu-id="01ac2-125">La sortie affiche uniquement les lignes qui sont différentes entre les fichiers.</span><span class="sxs-lookup"><span data-stu-id="01ac2-125">The output displays only the lines that are different between the files.</span></span> <span data-ttu-id="01ac2-126">`Testfile1.txt` est l’objet de **référence** ( `<=` ) et `Testfile2.txt` est l’objet de **différence** ( `=>` ).</span><span class="sxs-lookup"><span data-stu-id="01ac2-126">`Testfile1.txt` is the **reference** object (`<=`) and `Testfile2.txt`is the **difference** object (`=>`).</span></span> <span data-ttu-id="01ac2-127">Les lignes dont le contenu apparaît dans les deux fichiers ne sont pas affichées.</span><span class="sxs-lookup"><span data-stu-id="01ac2-127">Lines with content that appear in both files aren't displayed.</span></span>

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

### <span data-ttu-id="01ac2-128">Exemple 2 : comparer chaque ligne de contenu et exclure les différences</span><span class="sxs-lookup"><span data-stu-id="01ac2-128">Example 2 - Compare each line of content and exclude the differences</span></span>

<span data-ttu-id="01ac2-129">Cet exemple utilise les paramètres **includeequal** et **ExcludeDifferent** pour comparer chaque ligne de contenu dans deux fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="01ac2-129">This example uses the **IncludeEqual** and **ExcludeDifferent** parameters to compare each line of content in two text files.</span></span>

<span data-ttu-id="01ac2-130">Étant donné que la commande utilise le paramètre **ExcludeDifferent** , la sortie contient uniquement les lignes contenues dans les deux fichiers, comme indiqué par **SideIndicator** ( `==` ).</span><span class="sxs-lookup"><span data-stu-id="01ac2-130">Because the command uses the **ExcludeDifferent** parameter, the output only contains lines contained in both files, as shown by the **SideIndicator** (`==`).</span></span>

```powershell
$objects = @{
  ReferenceObject = (Get-Content -Path C:\Test\Testfile1.txt)
  DifferenceObject = (Get-Content -Path C:\Test\Testfile2.txt)
}
Compare-Object @objects -IncludeEqual -ExcludeDifferent
```

```Output
InputObject SideIndicator
----------- -------------
bird        ==
```

<a id="ex3" />

### <span data-ttu-id="01ac2-131">Exemple 3 : afficher la différence lors de l’utilisation du paramètre PassThru</span><span class="sxs-lookup"><span data-stu-id="01ac2-131">Example 3 - Show the difference when using the PassThru parameter</span></span>

<span data-ttu-id="01ac2-132">Normalement, `Compare-Object` retourne un type **PSCustomObject** avec les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="01ac2-132">Normally, `Compare-Object` returns a **PSCustomObject** type with the following properties:</span></span>

- <span data-ttu-id="01ac2-133">**InputObject** qui est comparé</span><span class="sxs-lookup"><span data-stu-id="01ac2-133">The **InputObject** being compared</span></span>
- <span data-ttu-id="01ac2-134">Propriété **SideIndicator** indiquant l’objet d’entrée auquel la sortie appartient</span><span class="sxs-lookup"><span data-stu-id="01ac2-134">The **SideIndicator** property showing which input object the output belongs to</span></span>

<span data-ttu-id="01ac2-135">Quand vous utilisez le paramètre **PassThru** , le **type** de l’objet n’est pas modifié, mais l’instance de l’objet retourné a un **NoteProperty** ajouté nommé **SideIndicator**.</span><span class="sxs-lookup"><span data-stu-id="01ac2-135">When you use the **PassThru** parameter, the **Type** of the object is not changed but the instance of the object returned has an added **NoteProperty** named **SideIndicator**.</span></span> <span data-ttu-id="01ac2-136">**SideIndicator** affiche l’objet d’entrée auquel la sortie appartient.</span><span class="sxs-lookup"><span data-stu-id="01ac2-136">**SideIndicator** shows which input object the output belongs to.</span></span>

<span data-ttu-id="01ac2-137">Les exemples suivants illustrent les différents types de sortie.</span><span class="sxs-lookup"><span data-stu-id="01ac2-137">The following examples shows the different output types.</span></span>

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

<span data-ttu-id="01ac2-138">Lors de l’utilisation de **PassThru** , le type d’objet d’origine ( **System. Boolean** ) est retourné.</span><span class="sxs-lookup"><span data-stu-id="01ac2-138">When using **PassThru** , the original object type ( **System.Boolean** ) is returned.</span></span> <span data-ttu-id="01ac2-139">Notez que la sortie affichée par le format par défaut pour les objets **System. Boolean** n’a pas affiché la propriété **SideIndicator** .</span><span class="sxs-lookup"><span data-stu-id="01ac2-139">Note how the output displayed by the default format for **System.Boolean** objects didn't display the **SideIndicator** property.</span></span> <span data-ttu-id="01ac2-140">Toutefois, l’objet **System. Boolean** retourné a le **NoteProperty** ajouté.</span><span class="sxs-lookup"><span data-stu-id="01ac2-140">However, the returned **System.Boolean** object has the added **NoteProperty**.</span></span>

### <span data-ttu-id="01ac2-141">Exemple 4-comparer deux objets simples à l’aide de propriétés</span><span class="sxs-lookup"><span data-stu-id="01ac2-141">Example 4 - Compare two simple objects using properties</span></span>

<span data-ttu-id="01ac2-142">Dans cet exemple, nous comparons deux chaînes différentes qui ont la même longueur.</span><span class="sxs-lookup"><span data-stu-id="01ac2-142">In this example, we compare two different string that have the same length.</span></span>

```powershell
Compare-Object -ReferenceObject 'abc' -DifferenceObject 'xyz' -Property Length -IncludeEqual
```

```Output
Length SideIndicator
------ -------------
     3 ==
```

### <span data-ttu-id="01ac2-143">Exemple 5 : comparaison d’objets complexes à l’aide de propriétés</span><span class="sxs-lookup"><span data-stu-id="01ac2-143">Example 5 - Comparing complex objects using properties</span></span>

<span data-ttu-id="01ac2-144">Cet exemple illustre le comportement de la comparaison d’objets complexes.</span><span class="sxs-lookup"><span data-stu-id="01ac2-144">This example shows the behavior when comparing complex objects.</span></span> <span data-ttu-id="01ac2-145">Dans cet exemple, nous stockons deux objets de processus différents pour différentes instances de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01ac2-145">In this example we store two different process objects for different instances of PowerShell.</span></span> <span data-ttu-id="01ac2-146">Les deux variables contiennent des objets de processus portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="01ac2-146">Both variables contain process objects with the same name.</span></span> <span data-ttu-id="01ac2-147">Lorsque les objets sont comparés sans spécifier le paramètre **Property** , l’applet de commande considère que les objets sont égaux.</span><span class="sxs-lookup"><span data-stu-id="01ac2-147">When the objects are compared without specifying the **Property** parameter, the cmdlet considers the objects to be equal.</span></span> <span data-ttu-id="01ac2-148">Notez que la valeur de l' **InputObject** est identique à celle du résultat de la méthode **ToString ()** .</span><span class="sxs-lookup"><span data-stu-id="01ac2-148">Notice that the value of the **InputObject** is the same as the result of the **ToString()** method.</span></span> <span data-ttu-id="01ac2-149">Étant donné que la classe **System. Diagnostics. Process** n’a pas l’interface **IComparable** , l’applet de commande convertit les objets en chaînes, puis compare les résultats.</span><span class="sxs-lookup"><span data-stu-id="01ac2-149">Since the **System.Diagnostics.Process** class does not have the **IComparable** interface, the cmdlet converts the objects to strings then compares the results.</span></span>

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

<span data-ttu-id="01ac2-150">Lorsque vous spécifiez des propriétés à comparer, l’applet de commande affiche les différences.</span><span class="sxs-lookup"><span data-stu-id="01ac2-150">When you specify properties to be compared, the cmdlet shows the differences.</span></span>

### <span data-ttu-id="01ac2-151">Exemple 6 : comparaison d’objets complexes qui implémentent IComparable</span><span class="sxs-lookup"><span data-stu-id="01ac2-151">Example 6 - Comparing complex objects that implement IComparable</span></span>

<span data-ttu-id="01ac2-152">Si l’objet implémente **IComparable** , l’applet de commande recherche les façons de comparer les objets. Si les objets sont de types différents, l’objet de **différence** est converti en type de **ReferenceObject** , puis comparé.</span><span class="sxs-lookup"><span data-stu-id="01ac2-152">If the object implements **IComparable** , the cmdlet searches for ways to compare the objects.If the objects are different types, the **Difference** object is converted to the type of the **ReferenceObject** then compared.</span></span>

<span data-ttu-id="01ac2-153">Dans cet exemple, nous comparons une chaîne à un objet **TimeSpan** .</span><span class="sxs-lookup"><span data-stu-id="01ac2-153">In this example, we are comparing a string to a **TimeSpan** object.</span></span> <span data-ttu-id="01ac2-154">Dans le premier cas, la chaîne est convertie en **intervalle** de temps, de sorte que les objets sont égaux.</span><span class="sxs-lookup"><span data-stu-id="01ac2-154">In the first case, the string is converted to a **TimeSpan** so the objects are equal.</span></span>

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

<span data-ttu-id="01ac2-155">Dans le deuxième cas, la valeur **TimeSpan** est convertie en une chaîne, de sorte que l’objet est différent.</span><span class="sxs-lookup"><span data-stu-id="01ac2-155">In the second case, the **TimeSpan** is converted to a string so the object are different.</span></span>

## <span data-ttu-id="01ac2-156">Paramètres</span><span class="sxs-lookup"><span data-stu-id="01ac2-156">Parameters</span></span>

### <span data-ttu-id="01ac2-157">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="01ac2-157">-CaseSensitive</span></span>

<span data-ttu-id="01ac2-158">Indique que les comparaisons doivent respecter la casse.</span><span class="sxs-lookup"><span data-stu-id="01ac2-158">Indicates that comparisons should be case-sensitive.</span></span>

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

### <span data-ttu-id="01ac2-159">-Culture</span><span class="sxs-lookup"><span data-stu-id="01ac2-159">-Culture</span></span>

<span data-ttu-id="01ac2-160">Spécifie la culture à utiliser pour les comparaisons.</span><span class="sxs-lookup"><span data-stu-id="01ac2-160">Specifies the culture to use for comparisons.</span></span>

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

### <span data-ttu-id="01ac2-161">-DifferenceObject</span><span class="sxs-lookup"><span data-stu-id="01ac2-161">-DifferenceObject</span></span>

<span data-ttu-id="01ac2-162">Spécifie les objets qui sont comparés aux objets de **référence** .</span><span class="sxs-lookup"><span data-stu-id="01ac2-162">Specifies the objects that are compared to the **reference** objects.</span></span>

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

### <span data-ttu-id="01ac2-163">-ExcludeDifferent</span><span class="sxs-lookup"><span data-stu-id="01ac2-163">-ExcludeDifferent</span></span>

<span data-ttu-id="01ac2-164">Indique que cette applet de commande affiche uniquement les caractéristiques des objets comparés qui sont égaux.</span><span class="sxs-lookup"><span data-stu-id="01ac2-164">Indicates that this cmdlet displays only the characteristics of compared objects that are equal.</span></span> <span data-ttu-id="01ac2-165">Les différences entre les objets sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="01ac2-165">The differences between the objects are discarded.</span></span>

<span data-ttu-id="01ac2-166">Utilisez **ExcludeDifferent** avec **includeequal** pour afficher uniquement les lignes qui correspondent entre les objets de **référence** et les objets de **différence** .</span><span class="sxs-lookup"><span data-stu-id="01ac2-166">Use **ExcludeDifferent** with **IncludeEqual** to display only the lines that match between the **reference** and **difference** objects.</span></span>

<span data-ttu-id="01ac2-167">Si **ExcludeDifferent** est spécifié sans **includeequal** , il n’y a pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="01ac2-167">If **ExcludeDifferent** is specified without **IncludeEqual** , there's no output.</span></span>

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

### <span data-ttu-id="01ac2-168">-IncludeEqual</span><span class="sxs-lookup"><span data-stu-id="01ac2-168">-IncludeEqual</span></span>

<span data-ttu-id="01ac2-169">**Includeequal** affiche les correspondances entre les objets de **référence** et les objets de **différence** .</span><span class="sxs-lookup"><span data-stu-id="01ac2-169">**IncludeEqual** displays the matches between the **reference** and **difference** objects.</span></span>

<span data-ttu-id="01ac2-170">Par défaut, la sortie comprend également les différences entre les objets de **référence** et les objets de **différence** .</span><span class="sxs-lookup"><span data-stu-id="01ac2-170">By default, the output also includes the differences between the **reference** and **difference** objects.</span></span>

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

### <span data-ttu-id="01ac2-171">-PassThru</span><span class="sxs-lookup"><span data-stu-id="01ac2-171">-PassThru</span></span>

<span data-ttu-id="01ac2-172">Quand vous utilisez le paramètre **PassThru** , `Compare-Object` omet le wrapper **PSCustomObject** autour des objets comparés et retourne les objets différents, inchangés.</span><span class="sxs-lookup"><span data-stu-id="01ac2-172">When you use the **PassThru** parameter, `Compare-Object` omits the **PSCustomObject** wrapper around the compared objects and returns the differing objects, unchanged.</span></span>

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

### <span data-ttu-id="01ac2-173">-Propriété</span><span class="sxs-lookup"><span data-stu-id="01ac2-173">-Property</span></span>

<span data-ttu-id="01ac2-174">Spécifie un tableau de propriétés des objets de **référence** et de **différence** à comparer.</span><span class="sxs-lookup"><span data-stu-id="01ac2-174">Specifies an array of properties of the **reference** and **difference** objects to compare.</span></span>

<span data-ttu-id="01ac2-175">La valeur du paramètre **Property** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="01ac2-175">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="01ac2-176">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="01ac2-176">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="01ac2-177">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="01ac2-177">Valid key-value pairs are:</span></span>

- <span data-ttu-id="01ac2-178">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="01ac2-178">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="01ac2-179">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="01ac2-179">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="01ac2-180">-ReferenceObject</span><span class="sxs-lookup"><span data-stu-id="01ac2-180">-ReferenceObject</span></span>

<span data-ttu-id="01ac2-181">Spécifie un tableau d’objets utilisés comme référence pour la comparaison.</span><span class="sxs-lookup"><span data-stu-id="01ac2-181">Specifies an array of objects used as a reference for comparison.</span></span>

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

### <span data-ttu-id="01ac2-182">-SyncWindow</span><span class="sxs-lookup"><span data-stu-id="01ac2-182">-SyncWindow</span></span>

<span data-ttu-id="01ac2-183">Spécifie le nombre d’objets adjacents `Compare-Object` inspectés lors de la recherche d’une correspondance dans une collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="01ac2-183">Specifies the number of adjacent objects that `Compare-Object` inspects while looking for a match in a collection of objects.</span></span> <span data-ttu-id="01ac2-184">`Compare-Object` examine les objets adjacents lorsqu’il ne trouve pas l’objet à la même position dans une collection.</span><span class="sxs-lookup"><span data-stu-id="01ac2-184">`Compare-Object` examines adjacent objects when it doesn't find the object in the same position in a collection.</span></span> <span data-ttu-id="01ac2-185">La valeur par défaut est, ce qui `[Int32]::MaxValue` signifie que `Compare-Object` examine la collection d’objets entière.</span><span class="sxs-lookup"><span data-stu-id="01ac2-185">The default value is `[Int32]::MaxValue`, which means that `Compare-Object` examines the entire object collection.</span></span>

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

### <span data-ttu-id="01ac2-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="01ac2-186">CommonParameters</span></span>

<span data-ttu-id="01ac2-187">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="01ac2-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="01ac2-188">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="01ac2-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="01ac2-189">Entrées</span><span class="sxs-lookup"><span data-stu-id="01ac2-189">Inputs</span></span>

### <span data-ttu-id="01ac2-190">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="01ac2-190">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="01ac2-191">Vous pouvez envoyer un objet dans le pipeline au paramètre **differenceobject** .</span><span class="sxs-lookup"><span data-stu-id="01ac2-191">You can send an object down the pipeline to the **DifferenceObject** parameter.</span></span>

## <span data-ttu-id="01ac2-192">Sorties</span><span class="sxs-lookup"><span data-stu-id="01ac2-192">Outputs</span></span>

### <span data-ttu-id="01ac2-193">Aucun</span><span class="sxs-lookup"><span data-stu-id="01ac2-193">None</span></span>

<span data-ttu-id="01ac2-194">Si l’objet de **référence** et l’objet de **différence** sont identiques, il n’y a pas de sortie, sauf si vous utilisez le paramètre **includeequal** .</span><span class="sxs-lookup"><span data-stu-id="01ac2-194">If the **reference** object and the **difference** object are the same, there's no output, unless you use the **IncludeEqual** parameter.</span></span>

### <span data-ttu-id="01ac2-195">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="01ac2-195">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="01ac2-196">Si les objets sont différents, `Compare-Object` encapsule les objets qui diffèrent dans un `PSCustomObject` wrapper avec une propriété **SideIndicator** pour référencer les différences.</span><span class="sxs-lookup"><span data-stu-id="01ac2-196">If the objects are different, `Compare-Object` wraps the differing objects in a `PSCustomObject` wrapper with a **SideIndicator** property to reference the differences.</span></span>

<span data-ttu-id="01ac2-197">Quand vous utilisez le paramètre **PassThru** , le **type** de l’objet n’est pas modifié, mais l’instance de l’objet retourné a un **NoteProperty** ajouté nommé **SideIndicator**.</span><span class="sxs-lookup"><span data-stu-id="01ac2-197">When you use the **PassThru** parameter, the **Type** of the object is not changed but the instance of the object returned has an added **NoteProperty** named **SideIndicator**.</span></span> <span data-ttu-id="01ac2-198">**SideIndicator** affiche l’objet d’entrée auquel la sortie appartient.</span><span class="sxs-lookup"><span data-stu-id="01ac2-198">**SideIndicator** shows which input object the output belongs to.</span></span>

## <span data-ttu-id="01ac2-199">Notes</span><span class="sxs-lookup"><span data-stu-id="01ac2-199">Notes</span></span>

<span data-ttu-id="01ac2-200">Lors de l’utilisation du paramètre **PassThru** , la sortie affichée dans la console peut ne pas inclure la propriété **SideIndicator** .</span><span class="sxs-lookup"><span data-stu-id="01ac2-200">When using the **PassThru** parameter, the output displayed in the console may not include the **SideIndicator** property.</span></span> <span data-ttu-id="01ac2-201">L’affichage de format par défaut de pour le type d’objet généré par `Compare-Object` n’inclut pas la propriété **SideIndicator** .</span><span class="sxs-lookup"><span data-stu-id="01ac2-201">The default format view of the for the object type output by `Compare-Object` does not include the **SideIndicator** property.</span></span> <span data-ttu-id="01ac2-202">Pour plus d’informations, consultez l' [exemple 3](#ex3) de cet article.</span><span class="sxs-lookup"><span data-stu-id="01ac2-202">For more information see [Example 3](#ex3) in this article.</span></span>

## <span data-ttu-id="01ac2-203">Liens connexes</span><span class="sxs-lookup"><span data-stu-id="01ac2-203">Related links</span></span>

[<span data-ttu-id="01ac2-204">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="01ac2-204">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="01ac2-205">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="01ac2-205">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="01ac2-206">Group-Object</span><span class="sxs-lookup"><span data-stu-id="01ac2-206">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="01ac2-207">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="01ac2-207">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="01ac2-208">New-Object</span><span class="sxs-lookup"><span data-stu-id="01ac2-208">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="01ac2-209">Select-Object</span><span class="sxs-lookup"><span data-stu-id="01ac2-209">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="01ac2-210">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="01ac2-210">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="01ac2-211">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="01ac2-211">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="01ac2-212">Where-Object</span><span class="sxs-lookup"><span data-stu-id="01ac2-212">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

[<span data-ttu-id="01ac2-213">Get-Process</span><span class="sxs-lookup"><span data-stu-id="01ac2-213">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)
