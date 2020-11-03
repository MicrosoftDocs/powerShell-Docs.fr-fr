---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Object
ms.openlocfilehash: 11aedd0f5249153e01382132c9eeb95f0717cda3
ms.sourcegitcommit: f9ae48d026d65833b9c8ca881058dda0bbd067b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "93206330"
---
# <span data-ttu-id="178ce-103">Select-Object</span><span class="sxs-lookup"><span data-stu-id="178ce-103">Select-Object</span></span>

## <span data-ttu-id="178ce-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="178ce-104">SYNOPSIS</span></span>
<span data-ttu-id="178ce-105">Sélectionne des objets ou des propriétés d'objet.</span><span class="sxs-lookup"><span data-stu-id="178ce-105">Selects objects or object properties.</span></span>

## <span data-ttu-id="178ce-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="178ce-106">SYNTAX</span></span>

### <span data-ttu-id="178ce-107">DefaultParameter (par défaut)</span><span class="sxs-lookup"><span data-stu-id="178ce-107">DefaultParameter (Default)</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-Last <Int32>] [-First <Int32>] [-Skip <Int32>] [-Wait]
 [<CommonParameters>]
```

### <span data-ttu-id="178ce-108">SkipLastParameter</span><span class="sxs-lookup"><span data-stu-id="178ce-108">SkipLastParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-SkipLast <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="178ce-109">IndexParameter</span><span class="sxs-lookup"><span data-stu-id="178ce-109">IndexParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [-Unique] [-Wait] [-Index <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="178ce-110">SkipIndexParameter</span><span class="sxs-lookup"><span data-stu-id="178ce-110">SkipIndexParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [-Unique] [-SkipIndex <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="178ce-111">Description</span><span class="sxs-lookup"><span data-stu-id="178ce-111">DESCRIPTION</span></span>

<span data-ttu-id="178ce-112">L' `Select-Object` applet de commande sélectionne les propriétés spécifiées d’un objet ou d’un ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="178ce-112">The `Select-Object` cmdlet selects specified properties of an object or set of objects.</span></span> <span data-ttu-id="178ce-113">Elle peut également sélectionner des objets uniques, un nombre spécifié d'objets ou des objets à une position spécifiée dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="178ce-113">It can also select unique objects, a specified number of objects, or objects in a specified position in an array.</span></span>

<span data-ttu-id="178ce-114">Pour sélectionner des objets dans une collection, utilisez les paramètres **First** , **Last** , **Unique** , **Skip** et **Index** .</span><span class="sxs-lookup"><span data-stu-id="178ce-114">To select objects from a collection, use the **First** , **Last** , **Unique** , **Skip** , and **Index** parameters.</span></span> <span data-ttu-id="178ce-115">Pour sélectionner des propriétés d'objet, utilisez le paramètre **Property** .</span><span class="sxs-lookup"><span data-stu-id="178ce-115">To select object properties, use the **Property** parameter.</span></span> <span data-ttu-id="178ce-116">Lorsque vous sélectionnez Propriétés, `Select-Object` retourne de nouveaux objets qui ont uniquement les propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="178ce-116">When you select properties, `Select-Object` returns new objects that have only the specified properties.</span></span>

<span data-ttu-id="178ce-117">À compter de Windows PowerShell 3,0, `Select-Object` comprend une fonctionnalité d’optimisation qui empêche les commandes de créer et de traiter des objets qui ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="178ce-117">Beginning in Windows PowerShell 3.0, `Select-Object` includes an optimization feature that prevents commands from creating and processing objects that are not used.</span></span>

<span data-ttu-id="178ce-118">Quand vous incluez une `Select-Object` commande avec le **premier** paramètre ou les paramètres d' **index** dans un pipeline de commande, PowerShell arrête la commande qui génère les objets dès que le nombre d’objets sélectionné est généré, même lorsque la commande qui génère les objets apparaît avant la `Select-Object` commande dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="178ce-118">When you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated, even when the command that generates the objects appears before the `Select-Object` command in the pipeline.</span></span> <span data-ttu-id="178ce-119">Pour désactiver ce comportement d'optimisation, utilisez le paramètre **Wait** .</span><span class="sxs-lookup"><span data-stu-id="178ce-119">To turn off this optimizing behavior, use the **Wait** parameter.</span></span>

## <span data-ttu-id="178ce-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="178ce-120">EXAMPLES</span></span>

### <span data-ttu-id="178ce-121">Exemple 1 : sélectionner des objets par propriété</span><span class="sxs-lookup"><span data-stu-id="178ce-121">Example 1: Select objects by property</span></span>

<span data-ttu-id="178ce-122">Cet exemple crée des objets qui ont les propriétés **Name** , **ID** et Working Set ( **WS** ) des objets Process.</span><span class="sxs-lookup"><span data-stu-id="178ce-122">This example creates objects that have the **Name** , **ID** , and working set ( **WS** ) properties of process objects.</span></span>

```powershell
Get-Process | Select-Object -Property ProcessName, Id, WS
```

### <span data-ttu-id="178ce-123">Exemple 2 : sélectionner des objets par propriété et mettre en forme les résultats</span><span class="sxs-lookup"><span data-stu-id="178ce-123">Example 2: Select objects by property and format the results</span></span>

<span data-ttu-id="178ce-124">Cet exemple obtient des informations sur les modules utilisés par les processus sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="178ce-124">This example gets information about the modules used by the processes on the computer.</span></span> <span data-ttu-id="178ce-125">Elle utilise l' `Get-Process` applet de commande pour récupérer le processus sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="178ce-125">It uses `Get-Process` cmdlet to get the process on the computer.</span></span>

<span data-ttu-id="178ce-126">Elle utilise l' `Select-Object` applet de commande pour générer un tableau d' `[System.Diagnostics.ProcessModule]` instances, tel qu’il est contenu dans la propriété **modules** de chaque instance de `System.Diagnostics.Process` sortie de `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="178ce-126">It uses the `Select-Object` cmdlet to output an array of `[System.Diagnostics.ProcessModule]` instances as contained in the **Modules** property of each `System.Diagnostics.Process` instance output by `Get-Process`.</span></span>

<span data-ttu-id="178ce-127">Le paramètre **Property** de l' `Select-Object` applet de commande sélectionne les noms des processus.</span><span class="sxs-lookup"><span data-stu-id="178ce-127">The **Property** parameter of the `Select-Object` cmdlet selects the process names.</span></span> <span data-ttu-id="178ce-128">Cela ajoute un `ProcessName` **NoteProperty** à chaque `[System.Diagnostics.ProcessModule]` instance et le remplit avec la valeur de la propriété **ProcessName** du processus actuel.</span><span class="sxs-lookup"><span data-stu-id="178ce-128">This adds a `ProcessName` **NoteProperty** to every `[System.Diagnostics.ProcessModule]` instance and populates it with the value of current process's **ProcessName** property.</span></span>

<span data-ttu-id="178ce-129">Enfin, `Format-List` l’applet de commande est utilisée pour afficher le nom et les modules de chaque processus dans une liste.</span><span class="sxs-lookup"><span data-stu-id="178ce-129">Finally, `Format-List` cmdlet is used to display the name and modules of each process in a list.</span></span>

```powershell
Get-Process Explorer | Select-Object -Property ProcessName -ExpandProperty Modules | Format-List
```

```Output
ProcessName       : explorer
ModuleName        : explorer.exe
FileName          : C:\WINDOWS\explorer.exe
BaseAddress       : 140697278152704
ModuleMemorySize  : 3919872
EntryPointAddress : 140697278841168
FileVersionInfo   : File:             C:\WINDOWS\explorer.exe
                    InternalName:     explorer
                    OriginalFilename: EXPLORER.EXE.MUI
                    FileVersion:      10.0.17134.1 (WinBuild.160101.0800)
                    FileDescription:  Windows Explorer
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.17134.1
...
```

### <span data-ttu-id="178ce-130">Exemple 3 : sélectionner les processus utilisant le plus de mémoire</span><span class="sxs-lookup"><span data-stu-id="178ce-130">Example 3: Select processes using the most memory</span></span>

<span data-ttu-id="178ce-131">Cet exemple obtient les cinq processus qui utilisent le plus de mémoire.</span><span class="sxs-lookup"><span data-stu-id="178ce-131">This example gets the five processes that are using the most memory.</span></span> <span data-ttu-id="178ce-132">L' `Get-Process` applet de commande obtient les processus sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="178ce-132">The `Get-Process` cmdlet gets the processes on the computer.</span></span> <span data-ttu-id="178ce-133">L' `Sort-Object` applet de commande trie les processus en fonction de l’utilisation de la mémoire (plage de travail), et l’applet de commande `Select-Object` sélectionne uniquement les cinq derniers membres du tableau d’objets résultant.</span><span class="sxs-lookup"><span data-stu-id="178ce-133">The `Sort-Object` cmdlet sorts the processes according to memory (working set) usage, and the `Select-Object` cmdlet selects only the last five members of the resulting array of objects.</span></span>

<span data-ttu-id="178ce-134">Le paramètre **Wait** n’est pas requis dans les commandes qui incluent l’applet de commande `Sort-Object` , car `Sort-Object` traite tous les objets, puis retourne une collection.</span><span class="sxs-lookup"><span data-stu-id="178ce-134">The **Wait** parameter is not required in commands that include the `Sort-Object` cmdlet because `Sort-Object` processes all objects and then returns a collection.</span></span> <span data-ttu-id="178ce-135">L' `Select-Object` optimisation est disponible uniquement pour les commandes qui retournent des objets individuellement au fur et à mesure de leur traitement.</span><span class="sxs-lookup"><span data-stu-id="178ce-135">The `Select-Object` optimization is available only for commands that return objects individually as they are processed.</span></span>

```powershell
Get-Process | Sort-Object -Property WS | Select-Object -Last 5
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VS(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
2866     320       33432      45764   203   222.41   1292 svchost
577      17        23676      50516   265    50.58   4388 WINWORD
826      11        75448      76712   188    19.77   3780 Ps
1367     14        73152      88736   216    61.69    676 Ps
1612     44        66080      92780   380   900.59   6132 INFOPATH
```

### <span data-ttu-id="178ce-136">Exemple 4 : sélectionner des caractères uniques d’un tableau</span><span class="sxs-lookup"><span data-stu-id="178ce-136">Example 4: Select unique characters from an array</span></span>

<span data-ttu-id="178ce-137">Cet exemple utilise le paramètre **unique** de `Select-Object` pour récupérer des caractères uniques à partir d’un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="178ce-137">This example uses the **Unique** parameter of `Select-Object` to get unique characters from an array of characters.</span></span>

```powershell
"a","b","c","a","a","a" | Select-Object -Unique
```

```Output
a
b
c
```

### <span data-ttu-id="178ce-138">Exemple 5 : sélectionner les événements les plus récents et les plus anciens dans le journal des événements</span><span class="sxs-lookup"><span data-stu-id="178ce-138">Example 5: Select newest and oldest events in the event log</span></span>

<span data-ttu-id="178ce-139">Cet exemple obtient le premier (dernier) et le dernier événement (le plus ancien) dans le journal des événements Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="178ce-139">This example gets the first (newest) and last (oldest) events in the Windows PowerShell event log.</span></span>

<span data-ttu-id="178ce-140">`Get-EventLog` Obtient tous les événements dans le journal Windows PowerShell et les enregistre dans la `$a` variable.</span><span class="sxs-lookup"><span data-stu-id="178ce-140">`Get-EventLog` gets all events in the Windows PowerShell log and saves them in the `$a` variable.</span></span>
<span data-ttu-id="178ce-141">Ensuite, `$a` est dirigé vers l' `Select-Object` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="178ce-141">Then, `$a` is piped to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="178ce-142">La `Select-Object` commande utilise le paramètre **index** pour sélectionner des événements dans le tableau d’événements de la `$a` variable.</span><span class="sxs-lookup"><span data-stu-id="178ce-142">The `Select-Object` command uses the **Index** parameter to select events from the array of events in the `$a` variable.</span></span> <span data-ttu-id="178ce-143">L'index du premier événement est 0.</span><span class="sxs-lookup"><span data-stu-id="178ce-143">The index of the first event is 0.</span></span> <span data-ttu-id="178ce-144">L’index du dernier événement est le nombre d’éléments dans `$a` moins 1.</span><span class="sxs-lookup"><span data-stu-id="178ce-144">The index of the last event is the number of items in `$a` minus 1.</span></span>

```powershell
$a = Get-EventLog -LogName "Windows PowerShell"
$a | Select-Object -Index 0, ($A.count - 1)
```

### <span data-ttu-id="178ce-145">Exemple 6 : sélectionner tout, sauf le premier objet</span><span class="sxs-lookup"><span data-stu-id="178ce-145">Example 6: Select all but the first object</span></span>

<span data-ttu-id="178ce-146">Cet exemple crée une session PSSession sur chacun des ordinateurs figurant dans les fichiers de Servers.txt, à l’exception du premier.</span><span class="sxs-lookup"><span data-stu-id="178ce-146">This example creates a new PSSession on each of the computers listed in the Servers.txt files, except for the first one.</span></span>

<span data-ttu-id="178ce-147">`Select-Object` sélectionne tous les ordinateurs sauf le premier dans une liste de noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="178ce-147">`Select-Object` selects all but the first computer in a list of computer names.</span></span> <span data-ttu-id="178ce-148">La liste des ordinateurs qui en résulte est définie en tant que valeur du paramètre **ComputerName** de l’applet de commande `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="178ce-148">The resulting list of computers is set as the value of the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span>

```powershell
New-PSSession -ComputerName (Get-Content Servers.txt | Select-Object -Skip 1)
```

### <span data-ttu-id="178ce-149">Exemple 7 : renommer des fichiers et en sélectionner plusieurs à examiner</span><span class="sxs-lookup"><span data-stu-id="178ce-149">Example 7: Rename files and select several to review</span></span>

<span data-ttu-id="178ce-150">Cet exemple ajoute un suffixe « -RO » aux noms de base des fichiers texte qui ont l’attribut de lecture seule, puis affiche les cinq premiers fichiers pour que l’utilisateur puisse voir un exemple de l’effet.</span><span class="sxs-lookup"><span data-stu-id="178ce-150">This example adds a "-ro" suffix to the base names of text files that have the read-only attribute and then displays the first five files so the user can see a sample of the effect.</span></span>

<span data-ttu-id="178ce-151">`Get-ChildItem` utilise le paramètre dynamique **ReadOnly** pour obtenir les fichiers en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="178ce-151">`Get-ChildItem` uses the **ReadOnly** dynamic parameter to get read-only files.</span></span> <span data-ttu-id="178ce-152">Les fichiers résultants sont dirigés vers l’applet de commande `Rename-Item` , qui renomme le fichier.</span><span class="sxs-lookup"><span data-stu-id="178ce-152">The resulting files are piped to the `Rename-Item` cmdlet, which renames the file.</span></span> <span data-ttu-id="178ce-153">Elle utilise le paramètre **PassThru** de `Rename-Item` pour envoyer les fichiers renommés à l' `Select-Object` applet de commande, qui sélectionne les 5 premiers à afficher.</span><span class="sxs-lookup"><span data-stu-id="178ce-153">It uses the **Passthru** parameter of `Rename-Item` to send the renamed files to the `Select-Object` cmdlet, which selects the first 5 for display.</span></span>

<span data-ttu-id="178ce-154">Le paramètre **Wait** de `Select-Object` empêche PowerShell d’arrêter l' `Get-ChildItem` applet de commande après avoir extrait les cinq premiers fichiers texte en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="178ce-154">The **Wait** parameter of `Select-Object` prevents PowerShell from stopping the `Get-ChildItem` cmdlet after it gets the first five read-only text files.</span></span> <span data-ttu-id="178ce-155">Sans ce paramètre, seuls les cinq premiers fichiers en lecture seule seraient renommés.</span><span class="sxs-lookup"><span data-stu-id="178ce-155">Without this parameter, only the first five read-only files would be renamed.</span></span>

```powershell
Get-ChildItem *.txt -ReadOnly |
    Rename-Item -NewName {$_.BaseName + "-ro.txt"} -PassThru |
    Select-Object -First 5 -Wait
```

### <span data-ttu-id="178ce-156">Exemple 8 : illustrer les subtilités du paramètre-ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="178ce-156">Example 8: Demonstrate the intricacies of the -ExpandProperty parameter</span></span>

<span data-ttu-id="178ce-157">Cet exemple illustre les subtilités du paramètre **ExpandProperty** .</span><span class="sxs-lookup"><span data-stu-id="178ce-157">This example demonstrates the intricacies of the **ExpandProperty** parameter.</span></span>

<span data-ttu-id="178ce-158">Notez que la sortie générée était un tableau d' `[System.Int32]` instances.</span><span class="sxs-lookup"><span data-stu-id="178ce-158">Note that the output generated was an array of `[System.Int32]` instances.</span></span> <span data-ttu-id="178ce-159">Les instances sont conformes aux règles de mise en forme standard de la **vue sortie** .</span><span class="sxs-lookup"><span data-stu-id="178ce-159">The instances conform to standard formatting rules of the **Output View** .</span></span> <span data-ttu-id="178ce-160">Cela est vrai pour toutes les propriétés *développées* .</span><span class="sxs-lookup"><span data-stu-id="178ce-160">This is true for any *Expanded* properties.</span></span> <span data-ttu-id="178ce-161">Si les objets en sortie ont un format standard spécifique, la propriété développée peut ne pas être visible.</span><span class="sxs-lookup"><span data-stu-id="178ce-161">If the outputted objects have a specific standard format, the expanded property might not be visible.</span></span>

```powershell
# Create a custom object to use for the Select-Object example.
$object = [pscustomobject]@{Name="CustomObject";Expand=@(1,2,3,4,5)}
# Use the ExpandProperty parameter to Expand the property.
$object | Select-Object -ExpandProperty Expand -Property Name
```

```Output
1
2
3
4
5
```

```powershell
# The output did not contain the Name property, but it was added successfully.
# Use Get-Member to confirm the Name property was added and populated.
$object | Select-Object -ExpandProperty Expand -Property Name | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType   Definition
----        ----------   ----------
CompareTo   Method       int CompareTo(System.Object value), int CompareTo(int value), int IComparable.CompareTo(System.Object obj)...
Equals      Method       bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int].Equals(int other)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
GetTypeCode Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar      Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime  Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal   Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble    Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16     Method       int16 IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32     Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64     Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte     Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle    Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString    Method       string ToString(), string ToString(string format), string ToString(System.IFormatProvider provider)...
ToType      Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16    Method       uint16 IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32    Method       uint32 IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64    Method       uint64 IConvertible.ToUInt64(System.IFormatProvider provider)
Name        NoteProperty string Name=CustomObject
```

### <span data-ttu-id="178ce-162">Exemple 9 : créer des propriétés personnalisées sur des objets</span><span class="sxs-lookup"><span data-stu-id="178ce-162">Example 9: Create custom properties on objects</span></span>

<span data-ttu-id="178ce-163">L’exemple suivant illustre l’utilisation `Select-Object` de pour ajouter une propriété personnalisée à n’importe quel objet.</span><span class="sxs-lookup"><span data-stu-id="178ce-163">The following example demonstrates using `Select-Object` to add a custom property to any object.</span></span>
<span data-ttu-id="178ce-164">Lorsque vous spécifiez un nom de propriété qui n’existe pas, `Select-Object` crée cette propriété en tant que **NoteProperty** sur chaque objet passé.</span><span class="sxs-lookup"><span data-stu-id="178ce-164">When you specify a property name that does not exist, `Select-Object` creates that property as a **NoteProperty** on each object passed.</span></span>

```powershell
$customObject = 1 | Select-Object -Property MyCustomProperty
$customObject.MyCustomProperty = "New Custom Property"
$customObject
```

```Output
MyCustomProperty
----------------
New Custom Property
```

### <span data-ttu-id="178ce-165">Exemple 10 : créer des propriétés calculées pour chaque InputObject</span><span class="sxs-lookup"><span data-stu-id="178ce-165">Example 10: Create calculated properties for each InputObject</span></span>

<span data-ttu-id="178ce-166">Cet exemple montre comment utiliser `Select-Object` pour ajouter des propriétés calculées à votre entrée.</span><span class="sxs-lookup"><span data-stu-id="178ce-166">This example demonstrates using `Select-Object` to add calculated properties to your input.</span></span> <span data-ttu-id="178ce-167">Le passage d’un **scriptblock** au paramètre **Property** entraîne l' `Select-Object` évaluation de l’expression sur chaque objet passé et l’ajout des résultats à la sortie.</span><span class="sxs-lookup"><span data-stu-id="178ce-167">Passing a **ScriptBlock** to the **Property** parameter causes `Select-Object` to evaluate the expression on each object passed and add the results to the output.</span></span> <span data-ttu-id="178ce-168">Dans le **scriptblock** , vous pouvez utiliser la `$_` variable pour référencer l’objet actuel dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="178ce-168">Within the **ScriptBlock** , you can use the `$_` variable to reference the current object in the pipeline.</span></span>

<span data-ttu-id="178ce-169">Par défaut, `Select-Object` utilise la chaîne **scriptblock** comme nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="178ce-169">By default, `Select-Object` will use the **ScriptBlock** string as the name of the property.</span></span> <span data-ttu-id="178ce-170">À l’aide d’une **Hashtable** , vous pouvez étiqueter la sortie de votre **scriptblock** en tant que propriété personnalisée ajoutée à chaque objet.</span><span class="sxs-lookup"><span data-stu-id="178ce-170">Using a **Hashtable** , you can label the output of your **ScriptBlock** as a custom property added to each object.</span></span> <span data-ttu-id="178ce-171">Vous pouvez ajouter plusieurs propriétés calculées à chaque objet passé à `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="178ce-171">You can add multiple calculated properties to each object passed to `Select-Object`.</span></span>

```powershell
# Create a calculated property called $_.StartTime.DayOfWeek
Get-Process | Select-Object -Property ProcessName,{$_.StartTime.DayOfWeek}
```

```Output
ProcessName  $_.StartTime.DayOfWeek
----         ----------------------
alg                       Wednesday
ati2evxx                  Wednesday
ati2evxx                   Thursday
...
```

```powershell
# Add a custom property to calculate the size in KiloBytes of each FileInfo object you pass in.
# Use the pipeline variable to divide each file's length by 1 KiloBytes
$size = @{label="Size(KB)";expression={$_.length/1KB}}
# Create an additional calculated property with the number of Days since the file was last accessed.
# You can also shorten the key names to be 'l', and 'e', or use Name instead of Label.
$days = @{l="Days";e={((Get-Date) - $_.LastAccessTime).Days}}
# You can also shorten the name of your label key to 'l' and your expression key to 'e'.
Get-ChildItem $PSHOME -File | Select-Object Name, $size, $days
```

```Output
Name                        Size(KB)        Days
----                        --------        ----
Certificate.format.ps1xml   12.5244140625   223
Diagnostics.Format.ps1xml   4.955078125     223
DotNetTypes.format.ps1xml   134.9833984375  223
```

## <span data-ttu-id="178ce-172">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="178ce-172">PARAMETERS</span></span>

### <span data-ttu-id="178ce-173">-ExcludeProperty</span><span class="sxs-lookup"><span data-stu-id="178ce-173">-ExcludeProperty</span></span>

<span data-ttu-id="178ce-174">Spécifie les propriétés que cette applet de commande exclut de l’opération.</span><span class="sxs-lookup"><span data-stu-id="178ce-174">Specifies the properties that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="178ce-175">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="178ce-175">Wildcards are permitted.</span></span>

<span data-ttu-id="178ce-176">À compter de PowerShell 6, il n’est plus nécessaire d’inclure le paramètre **Property** pour que **ExcludeProperty** fonctionne.</span><span class="sxs-lookup"><span data-stu-id="178ce-176">Beginning in PowerShell 6, it is no longer required to include the **Property** parameter for **ExcludeProperty** to work.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="178ce-177">-ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="178ce-177">-ExpandProperty</span></span>

<span data-ttu-id="178ce-178">Spécifie une propriété à sélectionner et indique qu'une tentative doit être effectuée pour développer cette propriété.</span><span class="sxs-lookup"><span data-stu-id="178ce-178">Specifies a property to select, and indicates that an attempt should be made to expand that property.</span></span>

- <span data-ttu-id="178ce-179">Si la propriété spécifiée est un tableau, chaque valeur du tableau est incluse dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="178ce-179">If the specified property is an array, each value of the array is included in the output.</span></span>
- <span data-ttu-id="178ce-180">Si la propriété spécifiée est un objet, les propriétés des objets sont développées pour chaque **InputObject**</span><span class="sxs-lookup"><span data-stu-id="178ce-180">If the specified property is an object, the objects properties are expanded for every **InputObject**</span></span>

<span data-ttu-id="178ce-181">Dans les deux cas, le **type** de sortie d’objets correspondra au **type** de la propriété développée.</span><span class="sxs-lookup"><span data-stu-id="178ce-181">In either case, the **Type** of objects output will match the **Type** of the expanded property.</span></span>

<span data-ttu-id="178ce-182">Si le paramètre **Property** est spécifié, `Select-Object` tente d’ajouter chaque propriété sélectionnée en tant que **NoteProperty** à chaque objet sorti.</span><span class="sxs-lookup"><span data-stu-id="178ce-182">If the **Property** parameter is specified, `Select-Object` will attempt to add each selected property as a **NoteProperty** to every outputted object.</span></span>

> [!WARNING]
> <span data-ttu-id="178ce-183">Si vous recevez l’erreur : la propriété Select : ne peut pas être traitée, car la propriété `<PropertyName>` existe déjà, prenez en compte les éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="178ce-183">If you receive the error: Select : Property cannot be processed because property `<PropertyName>` already exists, consider the following.</span></span>
> <span data-ttu-id="178ce-184">Notez que, lors de l’utilisation `-ExpandProperty` de, `Select-Object` ne peut pas remplacer une propriété existante.</span><span class="sxs-lookup"><span data-stu-id="178ce-184">Note that when using `-ExpandProperty`, `Select-Object` can not replace an existing property.</span></span>
> <span data-ttu-id="178ce-185">La procédure est la suivante :</span><span class="sxs-lookup"><span data-stu-id="178ce-185">This means:</span></span>
>
> - <span data-ttu-id="178ce-186">Si l’objet développé a une propriété du même nom, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="178ce-186">If the expanded object has a property of the same name, an error will occur.</span></span>
> - <span data-ttu-id="178ce-187">Si l’objet *sélectionné* a une propriété du même nom qu’une propriété d’objets *développés* , une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="178ce-187">If the *Selected* object has a property of the same name as an *Expanded* objects property, an error will occur.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="178ce-188">-First</span><span class="sxs-lookup"><span data-stu-id="178ce-188">-First</span></span>

<span data-ttu-id="178ce-189">Spécifie le nombre d'objets à sélectionner à partir du début d'un tableau d'objets d'entrée.</span><span class="sxs-lookup"><span data-stu-id="178ce-189">Specifies the number of objects to select from the beginning of an array of input objects.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="178ce-190">-Index</span><span class="sxs-lookup"><span data-stu-id="178ce-190">-Index</span></span>

<span data-ttu-id="178ce-191">Sélectionne des objets dans un tableau en fonction de leurs valeurs d'index.</span><span class="sxs-lookup"><span data-stu-id="178ce-191">Selects objects from an array based on their index values.</span></span> <span data-ttu-id="178ce-192">Entrez les index dans une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="178ce-192">Enter the indexes in a comma-separated list.</span></span> <span data-ttu-id="178ce-193">Les index d'un tableau commencent à 0, où 0 représente la première valeur et (n-1) représente la dernière valeur.</span><span class="sxs-lookup"><span data-stu-id="178ce-193">Indexes in an array begin with 0, where 0 represents the first value and (n-1) represents the last value.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="178ce-194">-InputObject</span><span class="sxs-lookup"><span data-stu-id="178ce-194">-InputObject</span></span>

<span data-ttu-id="178ce-195">Spécifie des objets à envoyer à l'applet de commande via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="178ce-195">Specifies objects to send to the cmdlet through the pipeline.</span></span> <span data-ttu-id="178ce-196">Ce paramètre vous permet de diriger des objets vers `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="178ce-196">This parameter enables you to pipe objects to `Select-Object`.</span></span>

<span data-ttu-id="178ce-197">Lorsque vous transmettez des objets au paramètre **InputObject** , au lieu d’utiliser le pipeline, `Select-Object` traite l' **InputObject** comme un objet unique, même si la valeur est une collection.</span><span class="sxs-lookup"><span data-stu-id="178ce-197">When you pass objects to the **InputObject** parameter, instead of using the pipeline, `Select-Object` treats the **InputObject** as a single object, even if the value is a collection.</span></span> <span data-ttu-id="178ce-198">Il est recommandé d’utiliser le pipeline lors du passage de collections à `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="178ce-198">It is recommended that you use the pipeline when passing collections to `Select-Object`.</span></span>

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

### <span data-ttu-id="178ce-199">-Dernier</span><span class="sxs-lookup"><span data-stu-id="178ce-199">-Last</span></span>

<span data-ttu-id="178ce-200">Spécifie le nombre d'objets à sélectionner à partir de la fin d'un tableau d'objets d'entrée.</span><span class="sxs-lookup"><span data-stu-id="178ce-200">Specifies the number of objects to select from the end of an array of input objects.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="178ce-201">-Propriété</span><span class="sxs-lookup"><span data-stu-id="178ce-201">-Property</span></span>

<span data-ttu-id="178ce-202">Spécifie les propriétés à sélectionner.</span><span class="sxs-lookup"><span data-stu-id="178ce-202">Specifies the properties to select.</span></span> <span data-ttu-id="178ce-203">Ces propriétés sont ajoutées en tant que membres **NoteProperty** aux objets de sortie.</span><span class="sxs-lookup"><span data-stu-id="178ce-203">These properties are added as **NoteProperty** members to the output objects.</span></span> <span data-ttu-id="178ce-204">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="178ce-204">Wildcards are permitted.</span></span>

<span data-ttu-id="178ce-205">La valeur du paramètre **Property** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="178ce-205">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="178ce-206">Pour créer une propriété calculée, utilisez une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="178ce-206">To create a calculated, property, use a hash table.</span></span>

<span data-ttu-id="178ce-207">Les clés valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="178ce-207">Valid keys are:</span></span>

- <span data-ttu-id="178ce-208">Nom (ou étiquette)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="178ce-208">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="178ce-209">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="178ce-209">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="178ce-210">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="178ce-210">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="178ce-211">-Ignorer</span><span class="sxs-lookup"><span data-stu-id="178ce-211">-Skip</span></span>

<span data-ttu-id="178ce-212">Ignore (ne sélectionne pas) le nombre spécifié d'éléments.</span><span class="sxs-lookup"><span data-stu-id="178ce-212">Skips (does not select) the specified number of items.</span></span> <span data-ttu-id="178ce-213">Par défaut, le paramètre **Skip** est compté à partir du début du tableau ou de la liste d’objets, mais si la commande utilise le **dernier** paramètre, elle est comptabilisée à partir de la fin de la liste ou du tableau.</span><span class="sxs-lookup"><span data-stu-id="178ce-213">By default, the **Skip** parameter counts from the beginning of the array or list of objects, but if the command uses the **Last** parameter, it counts from the end of the list or array.</span></span>

<span data-ttu-id="178ce-214">Contrairement au paramètre **Index** , qui commence le comptage à 0, le paramètre **Skip** commence à 1.</span><span class="sxs-lookup"><span data-stu-id="178ce-214">Unlike the **Index** parameter, which starts counting at 0, the **Skip** parameter begins at 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="178ce-215">-SkipLast</span><span class="sxs-lookup"><span data-stu-id="178ce-215">-SkipLast</span></span>

<span data-ttu-id="178ce-216">Ignore (ne sélectionne pas) le nombre spécifié d’éléments à partir de la fin de la liste ou du tableau.</span><span class="sxs-lookup"><span data-stu-id="178ce-216">Skips (does not select) the specified number of items from the end of the list or array.</span></span> <span data-ttu-id="178ce-217">Fonctionne de la même façon que l’utilisation de **Skip** avec le **dernier** paramètre.</span><span class="sxs-lookup"><span data-stu-id="178ce-217">Works in the same way as using **Skip** together with **Last** parameter.</span></span>

<span data-ttu-id="178ce-218">Contrairement au paramètre **index** , qui commence à compter à 0, le paramètre **SkipLast** commence à 1.</span><span class="sxs-lookup"><span data-stu-id="178ce-218">Unlike the **Index** parameter, which starts counting at 0, the **SkipLast** parameter begins at 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="178ce-219">-Unique</span><span class="sxs-lookup"><span data-stu-id="178ce-219">-Unique</span></span>

<span data-ttu-id="178ce-220">Spécifie que si un sous-ensemble des objets d'entrée a des propriétés et des valeurs identiques, un seul membre du sous-ensemble est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="178ce-220">Specifies that if a subset of the input objects has identical properties and values, only a single member of the subset will be selected.</span></span>

<span data-ttu-id="178ce-221">Ce paramètre respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="178ce-221">This parameter is case-sensitive.</span></span> <span data-ttu-id="178ce-222">Par conséquent, les chaînes qui diffèrent uniquement par la casse sont considérées comme uniques.</span><span class="sxs-lookup"><span data-stu-id="178ce-222">As a result, strings that differ only in character casing are considered to be unique.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="178ce-223">-Wait</span><span class="sxs-lookup"><span data-stu-id="178ce-223">-Wait</span></span>

<span data-ttu-id="178ce-224">Indique que l’applet de commande désactive l’optimisation.</span><span class="sxs-lookup"><span data-stu-id="178ce-224">Indicates that the cmdlet turns off optimization.</span></span> <span data-ttu-id="178ce-225">PowerShell exécute les commandes dans l’ordre dans lequel elles apparaissent dans le pipeline de commande et leur permet de générer tous les objets.</span><span class="sxs-lookup"><span data-stu-id="178ce-225">PowerShell runs commands in the order that they appear in the command pipeline and lets them generate all objects.</span></span> <span data-ttu-id="178ce-226">Par défaut, si vous incluez une `Select-Object` commande avec les paramètres **First** ou **index** dans un pipeline de commande, PowerShell arrête la commande qui génère les objets dès que le nombre d’objets sélectionné est généré.</span><span class="sxs-lookup"><span data-stu-id="178ce-226">By default, if you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated.</span></span>

<span data-ttu-id="178ce-227">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="178ce-227">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultParameter, IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="178ce-228">-SkipIndex</span><span class="sxs-lookup"><span data-stu-id="178ce-228">-SkipIndex</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SkipIndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="178ce-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="178ce-229">CommonParameters</span></span>

<span data-ttu-id="178ce-230">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="178ce-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="178ce-231">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="178ce-231">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="178ce-232">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="178ce-232">INPUTS</span></span>

### <span data-ttu-id="178ce-233">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="178ce-233">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="178ce-234">Vous pouvez diriger n’importe quel objet vers `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="178ce-234">You can pipe any object to `Select-Object`.</span></span>

## <span data-ttu-id="178ce-235">SORTIES</span><span class="sxs-lookup"><span data-stu-id="178ce-235">OUTPUTS</span></span>

### <span data-ttu-id="178ce-236">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="178ce-236">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="178ce-237">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="178ce-237">NOTES</span></span>

- <span data-ttu-id="178ce-238">Vous pouvez également faire référence à l’applet de commande `Select-Object` par son alias intégré, `select` .</span><span class="sxs-lookup"><span data-stu-id="178ce-238">You can also refer to the `Select-Object` cmdlet by its built-in alias, `select`.</span></span> <span data-ttu-id="178ce-239">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="178ce-239">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

- <span data-ttu-id="178ce-240">La fonctionnalité d’optimisation de `Select-Object` est disponible uniquement pour les commandes qui écrivent des objets dans le pipeline au fur et à mesure de leur traitement.</span><span class="sxs-lookup"><span data-stu-id="178ce-240">The optimization feature of `Select-Object` is available only for commands that write objects to the pipeline as they are processed.</span></span> <span data-ttu-id="178ce-241">Elle n'a pas d'effet sur les commandes qui placent les objets traités dans une mémoire tampon et les écrivent sous forme de collection.</span><span class="sxs-lookup"><span data-stu-id="178ce-241">It has no effect on commands that buffer processed objects and write them as a collection.</span></span> <span data-ttu-id="178ce-242">Écrire immédiatement les objets est une pratique recommandée dans la conception des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="178ce-242">Writing objects immediately is a cmdlet design best practice.</span></span> <span data-ttu-id="178ce-243">Pour plus d’informations, consultez _écrire des enregistrements uniques dans le pipeline_ dans [conseils de développement fortement encouragés](/powershell/scripting/developer/windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="178ce-243">For more information, see _Write Single Records to the Pipeline_ in [Strongly Encouraged Development Guidelines](/powershell/scripting/developer/windows-powershell).</span></span>

## <span data-ttu-id="178ce-244">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="178ce-244">RELATED LINKS</span></span>

[<span data-ttu-id="178ce-245">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="178ce-245">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="178ce-246">Group-Object</span><span class="sxs-lookup"><span data-stu-id="178ce-246">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="178ce-247">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="178ce-247">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="178ce-248">Where-Object</span><span class="sxs-lookup"><span data-stu-id="178ce-248">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
