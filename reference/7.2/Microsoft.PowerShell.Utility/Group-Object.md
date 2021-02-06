---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/group-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Group-Object
ms.openlocfilehash: 6198964f01a4c0dc70584cdb3e5c0e13f3965934
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596318"
---
# <span data-ttu-id="e456e-102">Group-Object</span><span class="sxs-lookup"><span data-stu-id="e456e-102">Group-Object</span></span>

## <span data-ttu-id="e456e-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e456e-103">SYNOPSIS</span></span>
<span data-ttu-id="e456e-104">Groupe les objets qui contiennent la même valeur pour les propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="e456e-104">Groups objects that contain the same value for specified properties.</span></span>

## <span data-ttu-id="e456e-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="e456e-105">SYNTAX</span></span>

### <span data-ttu-id="e456e-106">Hachage</span><span class="sxs-lookup"><span data-stu-id="e456e-106">HashTable</span></span>

```
Group-Object [-NoElement] [-AsHashTable] [-AsString] [-InputObject <PSObject>]
 [[-Property] <Object[]>] [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="e456e-107">Description</span><span class="sxs-lookup"><span data-stu-id="e456e-107">DESCRIPTION</span></span>

<span data-ttu-id="e456e-108">L' `Group-Object` applet de commande affiche les objets dans des groupes en fonction de la valeur d’une propriété spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e456e-108">The `Group-Object` cmdlet displays objects in groups based on the value of a specified property.</span></span>
<span data-ttu-id="e456e-109">`Group-Object` retourne une table avec une ligne pour chaque valeur de propriété et une colonne qui affiche le nombre d’éléments avec cette valeur.</span><span class="sxs-lookup"><span data-stu-id="e456e-109">`Group-Object` returns a table with one row for each property value and a column that displays the number of items with that value.</span></span>

<span data-ttu-id="e456e-110">Si vous spécifiez plusieurs propriétés, vous `Group-Object` les regroupez d’abord selon les valeurs de la première propriété, puis, dans chaque groupe de propriétés, elle est regroupée selon la valeur de la propriété Next.</span><span class="sxs-lookup"><span data-stu-id="e456e-110">If you specify more than one property, `Group-Object` first groups them by the values of the first property, and then, within each property group, it groups by the value of the next property.</span></span>

<span data-ttu-id="e456e-111">À compter de PowerShell 7, `Group-Object` peut combiner les paramètres **CaseSensitive** et **AsHashtable** pour créer une table de hachage qui respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="e456e-111">Beginning in PowerShell 7, `Group-Object` can combine the **CaseSensitive** and **AsHashtable** parameters to create a case-sensitive hash table.</span></span> <span data-ttu-id="e456e-112">Les clés de table de hachage utilisent des comparaisons sensibles à la casse et génèrent un objet **System. Collections. Hashtable** .</span><span class="sxs-lookup"><span data-stu-id="e456e-112">The hash table keys use case-sensitive comparisons and output a **System.Collections.Hashtable** object.</span></span>

## <span data-ttu-id="e456e-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e456e-113">EXAMPLES</span></span>

### <span data-ttu-id="e456e-114">Exemple 1 : regrouper des fichiers par extension</span><span class="sxs-lookup"><span data-stu-id="e456e-114">Example 1: Group files by extension</span></span>

<span data-ttu-id="e456e-115">Cet exemple obtient de manière récursive les fichiers sous `$PSHOME` et les regroupe par extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="e456e-115">This example recursively gets the files under `$PSHOME` and groups them by file name extension.</span></span> <span data-ttu-id="e456e-116">La sortie est envoyée à l' `Sort-Object` applet de commande, qui les trie par nombre de fichiers trouvés pour l’extension donnée.</span><span class="sxs-lookup"><span data-stu-id="e456e-116">The output is sent to the `Sort-Object` cmdlet, which sorts them by the count files found for the given extension.</span></span> <span data-ttu-id="e456e-117">Le **nom** vide représente des répertoires.</span><span class="sxs-lookup"><span data-stu-id="e456e-117">The empty **Name** represents directories.</span></span>

<span data-ttu-id="e456e-118">Cet exemple utilise le paramètre **NoElement** pour omettre les membres du groupe.</span><span class="sxs-lookup"><span data-stu-id="e456e-118">This example uses the **NoElement** parameter to omit the members of the group.</span></span>

```powershell
$files = Get-ChildItem -Path $PSHOME -Recurse
$files | Group-Object -Property extension -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  365 .xml
  231 .cdxml
  197
  169 .ps1xml
  142 .txt
  114 .psd1
   63 .psm1
   49 .xsd
   36 .dll
   15 .mfl
   15 .mof
...
```

### <span data-ttu-id="e456e-119">Exemple 2 : regrouper des entiers par des chances et même</span><span class="sxs-lookup"><span data-stu-id="e456e-119">Example 2: Group integers by odds and evens</span></span>

<span data-ttu-id="e456e-120">Cet exemple montre comment utiliser des blocs de script comme valeur du paramètre **Property** .</span><span class="sxs-lookup"><span data-stu-id="e456e-120">This example shows how to use script blocks as the value of the **Property** parameter.</span></span> <span data-ttu-id="e456e-121">Cette commande affiche les entiers de 1 à 20, regroupés par chances et même.</span><span class="sxs-lookup"><span data-stu-id="e456e-121">This command displays the integers from 1 to 20, grouped by odds and even.</span></span>

```powershell
1..20 | Group-Object -Property {$_ % 2}
```

```Output
Count Name                      Group
----- ----                      -----
   10 0                         {2, 4, 6, 8...}
   10 1                         {1, 3, 5, 7...}
```

### <span data-ttu-id="e456e-122">Exemple 3 : regrouper les événements du journal des événements par EntryType</span><span class="sxs-lookup"><span data-stu-id="e456e-122">Example 3: Group event log events by EntryType</span></span>

<span data-ttu-id="e456e-123">Cet exemple affiche les 1 000 entrées les plus récentes dans le journal des événements système, regroupées par **entryType**.</span><span class="sxs-lookup"><span data-stu-id="e456e-123">This example displays the 1,000 most recent entries in the System event log, grouped by **EntryType**.</span></span>

<span data-ttu-id="e456e-124">Dans la sortie, la colonne **Count** représente le nombre d’entrées dans chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="e456e-124">In the output, the **Count** column represents the number of entries in each group.</span></span> <span data-ttu-id="e456e-125">La colonne **nom** représente les valeurs de **eventType** qui définissent un groupe.</span><span class="sxs-lookup"><span data-stu-id="e456e-125">The **Name** column represents the **EventType** values that define a group.</span></span> <span data-ttu-id="e456e-126">La colonne **groupe** représente les objets de chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="e456e-126">The **Group** column represents the objects in each group.</span></span>

```powershell
Get-WinEvent -LogName System -MaxEvents 1000 | Group-Object -Property LevelDisplayName
```

```Output
Count Name          Group
----- ----          -----
  153 Error         {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  722 Information   {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  125 Warning       {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
```

### <span data-ttu-id="e456e-127">Exemple 4 : regrouper des processus par classe de priorité</span><span class="sxs-lookup"><span data-stu-id="e456e-127">Example 4: Group processes by priority class</span></span>

<span data-ttu-id="e456e-128">Cet exemple illustre l’effet du paramètre **NoElement** .</span><span class="sxs-lookup"><span data-stu-id="e456e-128">This example demonstrates the effect of the **NoElement** parameter.</span></span> <span data-ttu-id="e456e-129">Ces commandes regroupent les processus en cours d'exécution sur l'ordinateur par classe de priorité.</span><span class="sxs-lookup"><span data-stu-id="e456e-129">These commands group the processes on the computer by priority class.</span></span>

<span data-ttu-id="e456e-130">La première commande utilise l' `Get-Process` applet de commande pour récupérer les processus sur l’ordinateur et envoie les objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="e456e-130">The first command uses the `Get-Process` cmdlet to get the processes on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="e456e-131">`Group-Object`regroupe les objets selon la valeur de la propriété **PriorityClass** du processus.</span><span class="sxs-lookup"><span data-stu-id="e456e-131">`Group-Object`groups the objects by the value of the **PriorityClass** property of the process.</span></span>

<span data-ttu-id="e456e-132">Le deuxième exemple utilise le paramètre **NoElement** pour éliminer les membres du groupe de la sortie.</span><span class="sxs-lookup"><span data-stu-id="e456e-132">The second example uses the **NoElement** parameter to eliminate the members of the group from the output.</span></span> <span data-ttu-id="e456e-133">Le résultat est une table avec uniquement la valeur de la propriété **Count** et **Name** .</span><span class="sxs-lookup"><span data-stu-id="e456e-133">The result is a table with only the **Count** and **Name** property value.</span></span>

<span data-ttu-id="e456e-134">Les résultats sont présentés dans l'exemple de sortie suivant.</span><span class="sxs-lookup"><span data-stu-id="e456e-134">The results are shown in the following sample output.</span></span>

```powershell
Get-Process | Group-Object -Property PriorityClass
```

```Output
Count Name         Group
----- ----         -----
   55 Normal       {System.Diagnostics.Process (AdtAgent), System.Diagnosti...
    1              {System.Diagnostics.Process (Idle)}
    3 High         {System.Diagnostics.Process (Newproc), System.Diagnostic...
    2 BelowNormal  {System.Diagnostics.Process (winperf),
```

```powershell
Get-Process | Group-Object -Property PriorityClass -NoElement
```

```Output
Count Name
----- ----
   55 Normal
    1
    3 High
    2 BelowNormal
```

### <span data-ttu-id="e456e-135">Exemple 5 : regrouper les processus par nom</span><span class="sxs-lookup"><span data-stu-id="e456e-135">Example 5: Group processes by name</span></span>

<span data-ttu-id="e456e-136">L’exemple suivant utilise `Group-Object` pour regrouper plusieurs instances de processus en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e456e-136">The following example uses `Group-Object` to group multiple instances of processes running on the local computer.</span></span> <span data-ttu-id="e456e-137">`Where-Object` affiche les processus avec plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="e456e-137">`Where-Object` displays processes with more than one instance.</span></span>

```powershell
Get-Process | Group-Object -Property Name -NoElement | Where-Object {$_.Count -gt 1}
```

```Output
Count Name
----- ----
2     csrss
5     svchost
2     winlogon
2     wmiprvse
```

### <span data-ttu-id="e456e-138">Exemple 6 : regrouper des objets dans une table de hachage</span><span class="sxs-lookup"><span data-stu-id="e456e-138">Example 6: Group objects in a hash table</span></span>

<span data-ttu-id="e456e-139">Cet exemple utilise les paramètres **AsHashTable** et **AsString** pour retourner les groupes dans une table de hachage, sous la forme d’une collection de paires clé-valeur.</span><span class="sxs-lookup"><span data-stu-id="e456e-139">This example uses the **AsHashTable** and **AsString** parameters to return the groups in a hash table, as a collection of key-value pairs.</span></span>

<span data-ttu-id="e456e-140">Dans la table de hachage résultante, chaque valeur de propriété est une clé et les éléments de groupe sont les valeurs.</span><span class="sxs-lookup"><span data-stu-id="e456e-140">In the resulting hash table, each property value is a key, and the group elements are the values.</span></span>
<span data-ttu-id="e456e-141">Comme chaque clé est une propriété de l'objet de table de hachage, vous pouvez utiliser la notation par points pour afficher les valeurs.</span><span class="sxs-lookup"><span data-stu-id="e456e-141">Because each key is a property of the hash table object, you can use dot notation to display the values.</span></span>

<span data-ttu-id="e456e-142">La première commande obtient les `Get` `Set` applets de commande et dans la session, les regroupe par verbe, retourne les groupes sous la forme d’une table de hachage et enregistre la table de hachage dans la `$A` variable.</span><span class="sxs-lookup"><span data-stu-id="e456e-142">The first command gets the `Get` and `Set` cmdlets in the session, groups them by verb, returns the groups as a hash table, and saves the hash table in the `$A` variable.</span></span>

<span data-ttu-id="e456e-143">La deuxième commande affiche la table de hachage dans `$A` .</span><span class="sxs-lookup"><span data-stu-id="e456e-143">The second command displays the hash table in `$A`.</span></span> <span data-ttu-id="e456e-144">Il existe deux paires clé-valeur, une pour les `Get` applets de commande et une pour les `Set` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="e456e-144">There are two key-value pairs, one for the `Get` cmdlets and one for the `Set` cmdlets.</span></span>

<span data-ttu-id="e456e-145">La troisième commande utilise la notation par points `$A.Get` pour afficher les valeurs de la clé d' **extraction** dans `$A` .</span><span class="sxs-lookup"><span data-stu-id="e456e-145">The third command uses dot notation, `$A.Get` to display the values of the **Get** key in `$A`.</span></span> <span data-ttu-id="e456e-146">Les valeurs sont des objets **CmdletInfo** .</span><span class="sxs-lookup"><span data-stu-id="e456e-146">The values are **CmdletInfo** object.</span></span> <span data-ttu-id="e456e-147">Le paramètre **AsString** ne convertit pas les objets des groupes en chaînes.</span><span class="sxs-lookup"><span data-stu-id="e456e-147">The **AsString** parameter doesn't convert the objects in the groups to strings.</span></span>

```powershell
$A = Get-Command Get-*, Set-* -CommandType cmdlet | Group-Object -Property Verb -AsHashTable -AsString
$A
```

```Output
Name     Value
----     -----
Get      {Get-Acl, Get-Alias, Get-AppLockerFileInformation, Get-AppLockerPolicy...}
Set      {Set-Acl, Set-Alias, Set-AppBackgroundTaskResourcePolicy, Set-AppLockerPolicy...}
```

```powershell
$A.Get
```

```Output
CommandType     Name                                Version    Source
-----------     ----                                -------    ------
Cmdlet          Get-Acl                             7.0.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-Alias                           7.0.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-AppLockerFileInformation        2.0.0.0    AppLocker
Cmdlet          Get-AppLockerPolicy                 2.0.0.0    AppLocker
...
```

### <span data-ttu-id="e456e-148">Exemple 7 : créer une table de hachage respectant la casse</span><span class="sxs-lookup"><span data-stu-id="e456e-148">Example 7: Create a case-sensitive hash table</span></span>

<span data-ttu-id="e456e-149">Cet exemple combine les paramètres **CaseSensitive** et **AsHashTable** pour créer une table de hachage qui respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="e456e-149">This example combines the **CaseSensitive** and **AsHashTable** parameters to create a case-sensitive hash table.</span></span> <span data-ttu-id="e456e-150">Les fichiers de l’exemple ont des extensions de `.txt` et `.TXT` .</span><span class="sxs-lookup"><span data-stu-id="e456e-150">The files in the example have extensions of `.txt` and `.TXT`.</span></span>

```powershell
$hash = Get-ChildItem -Path C:\Files | Group-Object -Property Extension -CaseSensitive -AsHashTable
$hash
```

```Output
Name           Value
----           -----
.TXT           {C:\Files\File7.TXT, C:\Files\File8.TXT, C:\Files\File9.TXT}
.txt           {C:\Files\file1.txt, C:\Files\file2.txt, C:\Files\file3.txt}
```

<span data-ttu-id="e456e-151">La `$hash` variable stocke l’objet **System. Collections. Hashtable** .</span><span class="sxs-lookup"><span data-stu-id="e456e-151">The `$hash` variable stores the **System.Collections.Hashtable** object.</span></span> <span data-ttu-id="e456e-152">`Get-ChildItem` Obtient les noms de fichiers à partir du `C:\Files` répertoire et envoie les objets **System. IO. FileInfo** vers le dessous du pipeline.</span><span class="sxs-lookup"><span data-stu-id="e456e-152">`Get-ChildItem` gets the file names from the `C:\Files` directory and sends the **System.IO.FileInfo** objects down the pipeline.</span></span> <span data-ttu-id="e456e-153">`Group-Object`groupe les objets à l’aide de l' **extension** de valeur de **propriété** .</span><span class="sxs-lookup"><span data-stu-id="e456e-153">`Group-Object` groups the objects using the **Property** value **Extension**.</span></span> <span data-ttu-id="e456e-154">Les paramètres **CaseSensitive** et **AsHashTable** créent la table de hachage et les clés sont regroupées à l’aide des clés sensibles à la casse `.txt` et `.TXT` .</span><span class="sxs-lookup"><span data-stu-id="e456e-154">The **CaseSensitive** and **AsHashTable** parameters create the hash table and the keys are grouped using the case-sensitive keys `.txt` and `.TXT`.</span></span>

## <span data-ttu-id="e456e-155">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e456e-155">PARAMETERS</span></span>

### <span data-ttu-id="e456e-156">-AsHashTable</span><span class="sxs-lookup"><span data-stu-id="e456e-156">-AsHashTable</span></span>

<span data-ttu-id="e456e-157">Indique que cette applet de commande retourne le groupe sous la forme d’une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="e456e-157">Indicates that this cmdlet returns the group as a hash table.</span></span> <span data-ttu-id="e456e-158">Les clés de la table de hachage sont les valeurs des propriétés selon lesquelles les objets sont regroupés.</span><span class="sxs-lookup"><span data-stu-id="e456e-158">The keys of the hash table are the property values by which the objects are grouped.</span></span> <span data-ttu-id="e456e-159">Les valeurs de la table de hachage sont les objets qui ont cette valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="e456e-159">The values of the hash table are the objects that have that property value.</span></span>

<span data-ttu-id="e456e-160">En soi, le paramètre **AsHashTable** retourne chaque table de hachage dans laquelle chaque clé est une instance de l’objet groupé.</span><span class="sxs-lookup"><span data-stu-id="e456e-160">By itself, the **AsHashTable** parameter returns each hash table in which each key is an instance of the grouped object.</span></span> <span data-ttu-id="e456e-161">En cas d’utilisation avec le paramètre **AsString** , les clés de la table de hachage sont des chaînes.</span><span class="sxs-lookup"><span data-stu-id="e456e-161">When used with the **AsString** parameter, the keys in the hash table are strings.</span></span>

<span data-ttu-id="e456e-162">À compter de PowerShell 7, pour créer des tables de hachage sensibles à la casse, incluez **CaseSensitive** et **AsHashtable** dans votre commande.</span><span class="sxs-lookup"><span data-stu-id="e456e-162">Beginning in PowerShell 7, to create case-sensitive hash tables, include **CaseSensitive** and **AsHashtable** in your command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: AHT

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e456e-163">-AsString</span><span class="sxs-lookup"><span data-stu-id="e456e-163">-AsString</span></span>

<span data-ttu-id="e456e-164">Indique que cette applet de commande convertit les clés de table de hachage en chaînes.</span><span class="sxs-lookup"><span data-stu-id="e456e-164">Indicates that this cmdlet converts the hash table keys to strings.</span></span> <span data-ttu-id="e456e-165">Par défaut, les clés d'une table de hachage sont des instances de l'objet regroupé.</span><span class="sxs-lookup"><span data-stu-id="e456e-165">By default, the hash table keys are instances of the grouped object.</span></span> <span data-ttu-id="e456e-166">Ce paramètre n’est valide que lorsqu’il est utilisé avec le paramètre **AsHashTable** .</span><span class="sxs-lookup"><span data-stu-id="e456e-166">This parameter is valid only when used with the **AsHashTable** parameter.</span></span>

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

### <span data-ttu-id="e456e-167">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="e456e-167">-CaseSensitive</span></span>

<span data-ttu-id="e456e-168">Indique que cette applet de commande rend le regroupement sensible à la casse.</span><span class="sxs-lookup"><span data-stu-id="e456e-168">Indicates that this cmdlet makes the grouping case-sensitive.</span></span> <span data-ttu-id="e456e-169">Sans ce paramètre, les valeurs des propriétés des objets dans un groupe peuvent avoir des casses différentes.</span><span class="sxs-lookup"><span data-stu-id="e456e-169">Without this parameter, the property values of objects in a group might have different cases.</span></span>

<span data-ttu-id="e456e-170">À compter de PowerShell 7, pour créer des tables de hachage sensibles à la casse, incluez **CaseSensitive** et **AsHashtable** dans votre commande.</span><span class="sxs-lookup"><span data-stu-id="e456e-170">Beginning in PowerShell 7, to create case-sensitive hash tables, include **CaseSensitive** and **AsHashtable** in your command.</span></span>

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

### <span data-ttu-id="e456e-171">-Culture</span><span class="sxs-lookup"><span data-stu-id="e456e-171">-Culture</span></span>

<span data-ttu-id="e456e-172">Spécifie la culture à utiliser lors de la comparaison de chaînes.</span><span class="sxs-lookup"><span data-stu-id="e456e-172">Specifies the culture to use when comparing strings.</span></span>

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

### <span data-ttu-id="e456e-173">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e456e-173">-InputObject</span></span>

<span data-ttu-id="e456e-174">Spécifie les objets à regrouper.</span><span class="sxs-lookup"><span data-stu-id="e456e-174">Specifies the objects to group.</span></span> <span data-ttu-id="e456e-175">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="e456e-175">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="e456e-176">Quand vous utilisez le paramètre **InputObject** pour envoyer une collection d’objets à `Group-Object` , `Group-Object` reçoit un objet qui représente la collection.</span><span class="sxs-lookup"><span data-stu-id="e456e-176">When you use the **InputObject** parameter to submit a collection of objects to `Group-Object`, `Group-Object` receives one object that represents the collection.</span></span> <span data-ttu-id="e456e-177">Elle crée donc un seul groupe avec cet objet comme membre.</span><span class="sxs-lookup"><span data-stu-id="e456e-177">As a result, it creates a single group with that object as its member.</span></span>

<span data-ttu-id="e456e-178">Pour regrouper les objets d’une collection, dirigez les objets vers `Group-Object` .</span><span class="sxs-lookup"><span data-stu-id="e456e-178">To group the objects in a collection, pipe the objects to `Group-Object`.</span></span>

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

### <span data-ttu-id="e456e-179">-NoElement</span><span class="sxs-lookup"><span data-stu-id="e456e-179">-NoElement</span></span>

<span data-ttu-id="e456e-180">Indique que cette applet de commande omet les membres d’un groupe des résultats.</span><span class="sxs-lookup"><span data-stu-id="e456e-180">Indicates that this cmdlet omits the members of a group from the results.</span></span>

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

### <span data-ttu-id="e456e-181">-Propriété</span><span class="sxs-lookup"><span data-stu-id="e456e-181">-Property</span></span>

<span data-ttu-id="e456e-182">Spécifie les propriétés pour le regroupement.</span><span class="sxs-lookup"><span data-stu-id="e456e-182">Specifies the properties for grouping.</span></span> <span data-ttu-id="e456e-183">Les objets sont organisés en groupes en fonction de la valeur de la propriété spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e456e-183">The objects are arranged into groups based on the value of the specified property.</span></span>

<span data-ttu-id="e456e-184">La valeur du paramètre **Property** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="e456e-184">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="e456e-185">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="e456e-185">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="e456e-186">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="e456e-186">Valid key-value pairs are:</span></span>

- <span data-ttu-id="e456e-187">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="e456e-187">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="e456e-188">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="e456e-188">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e456e-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e456e-189">CommonParameters</span></span>

<span data-ttu-id="e456e-190">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e456e-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e456e-191">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e456e-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e456e-192">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e456e-192">INPUTS</span></span>

### <span data-ttu-id="e456e-193">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="e456e-193">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="e456e-194">Vous pouvez diriger n’importe quel objet vers `Group-Object` .</span><span class="sxs-lookup"><span data-stu-id="e456e-194">You can pipe any object to `Group-Object`.</span></span>

## <span data-ttu-id="e456e-195">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e456e-195">OUTPUTS</span></span>

### <span data-ttu-id="e456e-196">Microsoft. PowerShell. Commands. GroupInfo ou System. Collections. Hashtable</span><span class="sxs-lookup"><span data-stu-id="e456e-196">Microsoft.PowerShell.Commands.GroupInfo or System.Collections.Hashtable</span></span>

<span data-ttu-id="e456e-197">Quand vous utilisez le paramètre **AsHashTable** , `Group-Object` retourne un objet **Hashtable** .</span><span class="sxs-lookup"><span data-stu-id="e456e-197">When you use the **AsHashTable** parameter, `Group-Object` returns a **Hashtable** object.</span></span>
<span data-ttu-id="e456e-198">Sinon, elle retourne un objet **GroupInfo** .</span><span class="sxs-lookup"><span data-stu-id="e456e-198">Otherwise, it returns a **GroupInfo** object.</span></span>

## <span data-ttu-id="e456e-199">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e456e-199">NOTES</span></span>

<span data-ttu-id="e456e-200">Vous pouvez utiliser le paramètre **GroupBy** des applets de commande de mise en forme, telles que `Format-Table` et `Format-List` , pour regrouper des objets.</span><span class="sxs-lookup"><span data-stu-id="e456e-200">You can use the **GroupBy** parameter of the formatting cmdlets, such as `Format-Table` and `Format-List`, to group objects.</span></span> <span data-ttu-id="e456e-201">Contrairement à `Group-Object` , qui crée une seule table avec une ligne pour chaque valeur de propriété, les paramètres **GroupBy** créent une table pour chaque valeur de propriété avec une ligne pour chaque élément ayant la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="e456e-201">Unlike `Group-Object`, which creates a single table with a row for each property value, the **GroupBy** parameters create a table for each property value with a row for each item that has the property value.</span></span>

<span data-ttu-id="e456e-202">`Group-Object` n’exige pas que les objets regroupés soient du même Microsoft .NET type de noyau.</span><span class="sxs-lookup"><span data-stu-id="e456e-202">`Group-Object` doesn't require that the objects being grouped are of the same Microsoft .NET Core type.</span></span> <span data-ttu-id="e456e-203">Lors du regroupement d’objets de différents types .NET Core, `Group-Object` utilise les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="e456e-203">When grouping objects of different .NET Core types, `Group-Object` uses the following rules:</span></span>

- <span data-ttu-id="e456e-204">Mêmes noms et types de propriétés.</span><span class="sxs-lookup"><span data-stu-id="e456e-204">Same Property Names and Types.</span></span>

  <span data-ttu-id="e456e-205">Si les objets ont une propriété avec le nom spécifié et que les valeurs de propriété ont le même type .NET Core, les valeurs de propriété sont regroupées à l’aide des mêmes règles que celles utilisées pour les objets du même type.</span><span class="sxs-lookup"><span data-stu-id="e456e-205">If the objects have a property with the specified name, and the property values have the same .NET Core type, the property values are grouped by using the same rules that would be used for objects of the same type.</span></span>

- <span data-ttu-id="e456e-206">Mêmes noms de propriété, types différents.</span><span class="sxs-lookup"><span data-stu-id="e456e-206">Same Property Names, Different Types.</span></span>

  <span data-ttu-id="e456e-207">Si les objets ont une propriété avec le nom spécifié, mais que les valeurs de propriété ont un type .NET Core différent dans des objets différents, `Group-Object` utilise le type .net Core de la première occurrence de la propriété comme type .net Core pour ce groupe de propriétés.</span><span class="sxs-lookup"><span data-stu-id="e456e-207">If the objects have a property with the specified name, but the property values have a different .NET Core type in different objects, `Group-Object` uses the .NET Core type of the first occurrence of the property as the .NET Core type for that property group.</span></span> <span data-ttu-id="e456e-208">Quand un objet a une propriété avec un type différent, la valeur de la propriété est convertie vers le type de ce groupe.</span><span class="sxs-lookup"><span data-stu-id="e456e-208">When an object has a property with a different type, the property value is converted to the type for that group.</span></span> <span data-ttu-id="e456e-209">Si la conversion de type échoue, l’objet n’est pas inclus dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="e456e-209">If the type conversion fails, the object isn't included in the group.</span></span>

- <span data-ttu-id="e456e-210">Propriétés manquantes.</span><span class="sxs-lookup"><span data-stu-id="e456e-210">Missing Properties.</span></span>

  <span data-ttu-id="e456e-211">Les objets qui n’ont pas de propriété spécifiée ne peuvent pas être regroupés.</span><span class="sxs-lookup"><span data-stu-id="e456e-211">Objects that don't have a specified property can't be grouped.</span></span> <span data-ttu-id="e456e-212">Les objets qui ne sont pas regroupés apparaissent dans la sortie finale de l’objet **GroupInfo** dans un groupe nommé `AutomationNull.Value` .</span><span class="sxs-lookup"><span data-stu-id="e456e-212">Objects that aren't grouped appear in the final **GroupInfo** object output in a group named `AutomationNull.Value`.</span></span>

## <span data-ttu-id="e456e-213">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e456e-213">RELATED LINKS</span></span>

[<span data-ttu-id="e456e-214">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="e456e-214">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="e456e-215">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="e456e-215">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="e456e-216">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="e456e-216">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="e456e-217">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="e456e-217">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="e456e-218">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="e456e-218">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="e456e-219">New-Object</span><span class="sxs-lookup"><span data-stu-id="e456e-219">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="e456e-220">Select-Object</span><span class="sxs-lookup"><span data-stu-id="e456e-220">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="e456e-221">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="e456e-221">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="e456e-222">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="e456e-222">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="e456e-223">Where-Object</span><span class="sxs-lookup"><span data-stu-id="e456e-223">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
