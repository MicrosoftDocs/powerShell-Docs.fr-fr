---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/group-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Group-Object
ms.openlocfilehash: f430dd1f9d9f820dda88ba5ad40023650204604d
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205985"
---
# <span data-ttu-id="fc795-103">Group-Object</span><span class="sxs-lookup"><span data-stu-id="fc795-103">Group-Object</span></span>

## <span data-ttu-id="fc795-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fc795-104">SYNOPSIS</span></span>
<span data-ttu-id="fc795-105">Groupe les objets qui contiennent la même valeur pour les propriétés spécifiées.</span><span class="sxs-lookup"><span data-stu-id="fc795-105">Groups objects that contain the same value for specified properties.</span></span>

## <span data-ttu-id="fc795-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fc795-106">SYNTAX</span></span>

### <span data-ttu-id="fc795-107">Hachage</span><span class="sxs-lookup"><span data-stu-id="fc795-107">HashTable</span></span>

```
Group-Object [-NoElement] [-AsHashTable] [-AsString] [-InputObject <PSObject>]
 [[-Property] <Object[]>] [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="fc795-108">Description</span><span class="sxs-lookup"><span data-stu-id="fc795-108">DESCRIPTION</span></span>

<span data-ttu-id="fc795-109">L' `Group-Object` applet de commande affiche les objets dans des groupes en fonction de la valeur d’une propriété spécifiée.</span><span class="sxs-lookup"><span data-stu-id="fc795-109">The `Group-Object` cmdlet displays objects in groups based on the value of a specified property.</span></span>
<span data-ttu-id="fc795-110">`Group-Object` retourne une table avec une ligne pour chaque valeur de propriété et une colonne qui affiche le nombre d’éléments avec cette valeur.</span><span class="sxs-lookup"><span data-stu-id="fc795-110">`Group-Object` returns a table with one row for each property value and a column that displays the number of items with that value.</span></span>

<span data-ttu-id="fc795-111">Si vous spécifiez plusieurs propriétés, vous `Group-Object` les regroupez d’abord selon les valeurs de la première propriété, puis, dans chaque groupe de propriétés, elle est regroupée selon la valeur de la propriété Next.</span><span class="sxs-lookup"><span data-stu-id="fc795-111">If you specify more than one property, `Group-Object` first groups them by the values of the first property, and then, within each property group, it groups by the value of the next property.</span></span>

## <span data-ttu-id="fc795-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fc795-112">EXAMPLES</span></span>

### <span data-ttu-id="fc795-113">Exemple 1 : regrouper des fichiers par extension</span><span class="sxs-lookup"><span data-stu-id="fc795-113">Example 1: Group files by extension</span></span>

<span data-ttu-id="fc795-114">Cet exemple obtient de manière récursive les fichiers sous `$PSHOME` et les regroupe par extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="fc795-114">This example recursively gets the files under `$PSHOME` and groups them by file name extension.</span></span> <span data-ttu-id="fc795-115">La sortie est envoyée à l' `Sort-Object` applet de commande, qui les trie par nombre de fichiers trouvés pour l’extension donnée.</span><span class="sxs-lookup"><span data-stu-id="fc795-115">The output is sent to the `Sort-Object` cmdlet, which sorts them by the count files found for the given extension.</span></span> <span data-ttu-id="fc795-116">Le **nom** vide représente des répertoires.</span><span class="sxs-lookup"><span data-stu-id="fc795-116">The empty **Name** represents directories.</span></span>

<span data-ttu-id="fc795-117">Cet exemple utilise le paramètre **NoElement** pour omettre les membres du groupe.</span><span class="sxs-lookup"><span data-stu-id="fc795-117">This example uses the **NoElement** parameter to omit the members of the group.</span></span>

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

### <span data-ttu-id="fc795-118">Exemple 2 : regrouper des entiers par des chances et même</span><span class="sxs-lookup"><span data-stu-id="fc795-118">Example 2: Group integers by odds and evens</span></span>

<span data-ttu-id="fc795-119">Cet exemple montre comment utiliser des blocs de script comme valeur du paramètre **Property** .</span><span class="sxs-lookup"><span data-stu-id="fc795-119">This example shows how to use script blocks as the value of the **Property** parameter.</span></span> <span data-ttu-id="fc795-120">Cette commande affiche les entiers de 1 à 20, regroupés par chances et même.</span><span class="sxs-lookup"><span data-stu-id="fc795-120">This command displays the integers from 1 to 20, grouped by odds and even.</span></span>

```powershell
1..20 | Group-Object -Property {$_ % 2}
```

```Output
Count Name                      Group
----- ----                      -----
   10 0                         {2, 4, 6, 8...}
   10 1                         {1, 3, 5, 7...}
```

### <span data-ttu-id="fc795-121">Exemple 3 : regrouper les événements du journal des événements par EntryType</span><span class="sxs-lookup"><span data-stu-id="fc795-121">Example 3: Group event log events by EntryType</span></span>

<span data-ttu-id="fc795-122">Cet exemple affiche les 1 000 entrées les plus récentes dans le journal des événements système, regroupées par **entryType** .</span><span class="sxs-lookup"><span data-stu-id="fc795-122">This example displays the 1,000 most recent entries in the System event log, grouped by **EntryType** .</span></span>

<span data-ttu-id="fc795-123">Dans la sortie, la colonne **Count** représente le nombre d’entrées dans chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="fc795-123">In the output, the **Count** column represents the number of entries in each group.</span></span> <span data-ttu-id="fc795-124">La colonne **nom** représente les valeurs de **eventType** qui définissent un groupe.</span><span class="sxs-lookup"><span data-stu-id="fc795-124">The **Name** column represents the **EventType** values that define a group.</span></span> <span data-ttu-id="fc795-125">La colonne **groupe** représente les objets de chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="fc795-125">The **Group** column represents the objects in each group.</span></span>

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

### <span data-ttu-id="fc795-126">Exemple 4 : regrouper des processus par classe de priorité</span><span class="sxs-lookup"><span data-stu-id="fc795-126">Example 4: Group processes by priority class</span></span>

<span data-ttu-id="fc795-127">Cet exemple illustre l’effet du paramètre **NoElement** .</span><span class="sxs-lookup"><span data-stu-id="fc795-127">This example demonstrates the effect of the **NoElement** parameter.</span></span> <span data-ttu-id="fc795-128">Ces commandes regroupent les processus en cours d'exécution sur l'ordinateur par classe de priorité.</span><span class="sxs-lookup"><span data-stu-id="fc795-128">These commands group the processes on the computer by priority class.</span></span>

<span data-ttu-id="fc795-129">La première commande utilise l' `Get-Process` applet de commande pour récupérer les processus sur l’ordinateur et envoie les objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="fc795-129">The first command uses the `Get-Process` cmdlet to get the processes on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="fc795-130">`Group-Object`regroupe les objets selon la valeur de la propriété **PriorityClass** du processus.</span><span class="sxs-lookup"><span data-stu-id="fc795-130">`Group-Object`groups the objects by the value of the **PriorityClass** property of the process.</span></span>

<span data-ttu-id="fc795-131">Le deuxième exemple utilise le paramètre **NoElement** pour éliminer les membres du groupe de la sortie.</span><span class="sxs-lookup"><span data-stu-id="fc795-131">The second example uses the **NoElement** parameter to eliminate the members of the group from the output.</span></span> <span data-ttu-id="fc795-132">Le résultat est une table avec uniquement la valeur de la propriété **Count** et **Name** .</span><span class="sxs-lookup"><span data-stu-id="fc795-132">The result is a table with only the **Count** and **Name** property value.</span></span>

<span data-ttu-id="fc795-133">Les résultats sont présentés dans l'exemple de sortie suivant.</span><span class="sxs-lookup"><span data-stu-id="fc795-133">The results are shown in the following sample output.</span></span>

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

### <span data-ttu-id="fc795-134">Exemple 5 : regrouper les processus par nom</span><span class="sxs-lookup"><span data-stu-id="fc795-134">Example 5: Group processes by name</span></span>

<span data-ttu-id="fc795-135">L’exemple suivant utilise `Group-Object` pour regrouper plusieurs instances de processus en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fc795-135">The following example uses `Group-Object` to group multiple instances of processes running on the local computer.</span></span> <span data-ttu-id="fc795-136">`Where-Object` affiche les processus avec plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="fc795-136">`Where-Object` displays processes with more than one instance.</span></span>

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

### <span data-ttu-id="fc795-137">Exemple 6 : regrouper des objets dans une table de hachage</span><span class="sxs-lookup"><span data-stu-id="fc795-137">Example 6: Group objects in a hash table</span></span>

<span data-ttu-id="fc795-138">Cet exemple utilise les paramètres **AsHashTable** et **AsString** pour retourner les groupes dans une table de hachage, sous la forme d’une collection de paires clé-valeur.</span><span class="sxs-lookup"><span data-stu-id="fc795-138">This example uses the **AsHashTable** and **AsString** parameters to return the groups in a hash table, as a collection of key-value pairs.</span></span>

<span data-ttu-id="fc795-139">Dans la table de hachage résultante, chaque valeur de propriété est une clé et les éléments de groupe sont les valeurs.</span><span class="sxs-lookup"><span data-stu-id="fc795-139">In the resulting hash table, each property value is a key, and the group elements are the values.</span></span>
<span data-ttu-id="fc795-140">Comme chaque clé est une propriété de l'objet de table de hachage, vous pouvez utiliser la notation par points pour afficher les valeurs.</span><span class="sxs-lookup"><span data-stu-id="fc795-140">Because each key is a property of the hash table object, you can use dot notation to display the values.</span></span>

<span data-ttu-id="fc795-141">La première commande obtient les `Get` `Set` applets de commande et dans la session, les regroupe par verbe, retourne les groupes sous la forme d’une table de hachage et enregistre la table de hachage dans la `$A` variable.</span><span class="sxs-lookup"><span data-stu-id="fc795-141">The first command gets the `Get` and `Set` cmdlets in the session, groups them by verb, returns the groups as a hash table, and saves the hash table in the `$A` variable.</span></span>

<span data-ttu-id="fc795-142">La deuxième commande affiche la table de hachage dans `$A` .</span><span class="sxs-lookup"><span data-stu-id="fc795-142">The second command displays the hash table in `$A`.</span></span> <span data-ttu-id="fc795-143">Il existe deux paires clé-valeur, une pour les `Get` applets de commande et une pour les `Set` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="fc795-143">There are two key-value pairs, one for the `Get` cmdlets and one for the `Set` cmdlets.</span></span>

<span data-ttu-id="fc795-144">La troisième commande utilise la notation par points `$A.Get` pour afficher les valeurs de la clé d' **extraction** dans `$A` .</span><span class="sxs-lookup"><span data-stu-id="fc795-144">The third command uses dot notation, `$A.Get` to display the values of the **Get** key in `$A`.</span></span> <span data-ttu-id="fc795-145">Les valeurs sont des objets **CmdletInfo** .</span><span class="sxs-lookup"><span data-stu-id="fc795-145">The values are **CmdletInfo** object.</span></span> <span data-ttu-id="fc795-146">Le paramètre **AsString** ne convertit pas les objets des groupes en chaînes.</span><span class="sxs-lookup"><span data-stu-id="fc795-146">The **AsString** parameter doesn't convert the objects in the groups to strings.</span></span>

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
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Cmdlet          Get-Acl                            6.1.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-Alias                          6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-AuthenticodeSignature          6.1.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-ChildItem                      6.1.0.0    Microsoft.PowerShell.Management
...
```

## <span data-ttu-id="fc795-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fc795-147">PARAMETERS</span></span>

### <span data-ttu-id="fc795-148">-AsHashTable</span><span class="sxs-lookup"><span data-stu-id="fc795-148">-AsHashTable</span></span>

<span data-ttu-id="fc795-149">Indique que cette applet de commande retourne le groupe sous la forme d’une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="fc795-149">Indicates that this cmdlet returns the group as a hash table.</span></span> <span data-ttu-id="fc795-150">Les clés de la table de hachage sont les valeurs des propriétés selon lesquelles les objets sont regroupés.</span><span class="sxs-lookup"><span data-stu-id="fc795-150">The keys of the hash table are the property values by which the objects are grouped.</span></span> <span data-ttu-id="fc795-151">Les valeurs de la table de hachage sont les objets qui ont cette valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="fc795-151">The values of the hash table are the objects that have that property value.</span></span>

<span data-ttu-id="fc795-152">En soi, le paramètre **AsHashTable** retourne chaque table de hachage dans laquelle chaque clé est une instance de l’objet groupé.</span><span class="sxs-lookup"><span data-stu-id="fc795-152">By itself, the **AsHashTable** parameter returns each hash table in which each key is an instance of the grouped object.</span></span> <span data-ttu-id="fc795-153">En cas d’utilisation avec le paramètre **AsString** , les clés de la table de hachage sont des chaînes.</span><span class="sxs-lookup"><span data-stu-id="fc795-153">When used with the **AsString** parameter, the keys in the hash table are strings.</span></span>

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

### <span data-ttu-id="fc795-154">-AsString</span><span class="sxs-lookup"><span data-stu-id="fc795-154">-AsString</span></span>

<span data-ttu-id="fc795-155">Indique que cette applet de commande convertit les clés de table de hachage en chaînes.</span><span class="sxs-lookup"><span data-stu-id="fc795-155">Indicates that this cmdlet converts the hash table keys to strings.</span></span> <span data-ttu-id="fc795-156">Par défaut, les clés d'une table de hachage sont des instances de l'objet regroupé.</span><span class="sxs-lookup"><span data-stu-id="fc795-156">By default, the hash table keys are instances of the grouped object.</span></span> <span data-ttu-id="fc795-157">Ce paramètre n’est valide que lorsqu’il est utilisé avec le paramètre **AsHashTable** .</span><span class="sxs-lookup"><span data-stu-id="fc795-157">This parameter is valid only when used with the **AsHashTable** parameter.</span></span>

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

### <span data-ttu-id="fc795-158">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="fc795-158">-CaseSensitive</span></span>

<span data-ttu-id="fc795-159">Indique que cette applet de commande rend le regroupement sensible à la casse.</span><span class="sxs-lookup"><span data-stu-id="fc795-159">Indicates that this cmdlet makes the grouping case-sensitive.</span></span> <span data-ttu-id="fc795-160">Sans ce paramètre, les valeurs des propriétés des objets dans un groupe peuvent avoir des casses différentes.</span><span class="sxs-lookup"><span data-stu-id="fc795-160">Without this parameter, the property values of objects in a group might have different cases.</span></span>

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

### <span data-ttu-id="fc795-161">-Culture</span><span class="sxs-lookup"><span data-stu-id="fc795-161">-Culture</span></span>

<span data-ttu-id="fc795-162">Spécifie la culture à utiliser lors de la comparaison de chaînes.</span><span class="sxs-lookup"><span data-stu-id="fc795-162">Specifies the culture to use when comparing strings.</span></span>

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

### <span data-ttu-id="fc795-163">-InputObject</span><span class="sxs-lookup"><span data-stu-id="fc795-163">-InputObject</span></span>

<span data-ttu-id="fc795-164">Spécifie les objets à regrouper.</span><span class="sxs-lookup"><span data-stu-id="fc795-164">Specifies the objects to group.</span></span> <span data-ttu-id="fc795-165">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="fc795-165">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="fc795-166">Quand vous utilisez le paramètre **InputObject** pour envoyer une collection d’objets à `Group-Object` , `Group-Object` reçoit un objet qui représente la collection.</span><span class="sxs-lookup"><span data-stu-id="fc795-166">When you use the **InputObject** parameter to submit a collection of objects to `Group-Object`, `Group-Object` receives one object that represents the collection.</span></span> <span data-ttu-id="fc795-167">Elle crée donc un seul groupe avec cet objet comme membre.</span><span class="sxs-lookup"><span data-stu-id="fc795-167">As a result, it creates a single group with that object as its member.</span></span>

<span data-ttu-id="fc795-168">Pour regrouper les objets d’une collection, dirigez les objets vers `Group-Object` .</span><span class="sxs-lookup"><span data-stu-id="fc795-168">To group the objects in a collection, pipe the objects to `Group-Object`.</span></span>

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

### <span data-ttu-id="fc795-169">-NoElement</span><span class="sxs-lookup"><span data-stu-id="fc795-169">-NoElement</span></span>

<span data-ttu-id="fc795-170">Indique que cette applet de commande omet les membres d’un groupe des résultats.</span><span class="sxs-lookup"><span data-stu-id="fc795-170">Indicates that this cmdlet omits the members of a group from the results.</span></span>

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

### <span data-ttu-id="fc795-171">-Propriété</span><span class="sxs-lookup"><span data-stu-id="fc795-171">-Property</span></span>

<span data-ttu-id="fc795-172">Spécifie les propriétés pour le regroupement.</span><span class="sxs-lookup"><span data-stu-id="fc795-172">Specifies the properties for grouping.</span></span> <span data-ttu-id="fc795-173">Les objets sont organisés en groupes en fonction de la valeur de la propriété spécifiée.</span><span class="sxs-lookup"><span data-stu-id="fc795-173">The objects are arranged into groups based on the value of the specified property.</span></span>

<span data-ttu-id="fc795-174">La valeur du paramètre **Property** peut être une nouvelle propriété calculée.</span><span class="sxs-lookup"><span data-stu-id="fc795-174">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="fc795-175">La propriété calculée peut être un bloc de script ou une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="fc795-175">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="fc795-176">Les paires clé-valeur valides sont :</span><span class="sxs-lookup"><span data-stu-id="fc795-176">Valid key-value pairs are:</span></span>

- <span data-ttu-id="fc795-177">Expression `<string>` ou `<script block>`</span><span class="sxs-lookup"><span data-stu-id="fc795-177">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="fc795-178">Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="fc795-178">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="fc795-179">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fc795-179">CommonParameters</span></span>

<span data-ttu-id="fc795-180">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fc795-180">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fc795-181">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fc795-181">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fc795-182">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fc795-182">INPUTS</span></span>

### <span data-ttu-id="fc795-183">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="fc795-183">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="fc795-184">Vous pouvez diriger n’importe quel objet vers `Group-Object` .</span><span class="sxs-lookup"><span data-stu-id="fc795-184">You can pipe any object to `Group-Object`.</span></span>

## <span data-ttu-id="fc795-185">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fc795-185">OUTPUTS</span></span>

### <span data-ttu-id="fc795-186">Microsoft. PowerShell. Commands. GroupInfo ou System. Collections. Hashtable</span><span class="sxs-lookup"><span data-stu-id="fc795-186">Microsoft.PowerShell.Commands.GroupInfo or System.Collections.Hashtable</span></span>

<span data-ttu-id="fc795-187">Quand vous utilisez le paramètre **AsHashTable** , `Group-Object` retourne un objet **Hashtable** .</span><span class="sxs-lookup"><span data-stu-id="fc795-187">When you use the **AsHashTable** parameter, `Group-Object` returns a **Hashtable** object.</span></span>
<span data-ttu-id="fc795-188">Sinon, elle retourne un objet **GroupInfo** .</span><span class="sxs-lookup"><span data-stu-id="fc795-188">Otherwise, it returns a **GroupInfo** object.</span></span>

## <span data-ttu-id="fc795-189">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="fc795-189">NOTES</span></span>

<span data-ttu-id="fc795-190">Vous pouvez utiliser le paramètre **GroupBy** des applets de commande de mise en forme, telles que `Format-Table` et `Format-List` , pour regrouper des objets.</span><span class="sxs-lookup"><span data-stu-id="fc795-190">You can use the **GroupBy** parameter of the formatting cmdlets, such as `Format-Table` and `Format-List`, to group objects.</span></span> <span data-ttu-id="fc795-191">Contrairement à `Group-Object` , qui crée une seule table avec une ligne pour chaque valeur de propriété, les paramètres **GroupBy** créent une table pour chaque valeur de propriété avec une ligne pour chaque élément ayant la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="fc795-191">Unlike `Group-Object`, which creates a single table with a row for each property value, the **GroupBy** parameters create a table for each property value with a row for each item that has the property value.</span></span>

<span data-ttu-id="fc795-192">`Group-Object` n’exige pas que les objets regroupés soient du même Microsoft .NET type de noyau.</span><span class="sxs-lookup"><span data-stu-id="fc795-192">`Group-Object` doesn't require that the objects being grouped are of the same Microsoft .NET Core type.</span></span> <span data-ttu-id="fc795-193">Lors du regroupement d’objets de différents types .NET Core, `Group-Object` utilise les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc795-193">When grouping objects of different .NET Core types, `Group-Object` uses the following rules:</span></span>

- <span data-ttu-id="fc795-194">Mêmes noms et types de propriétés.</span><span class="sxs-lookup"><span data-stu-id="fc795-194">Same Property Names and Types.</span></span>

  <span data-ttu-id="fc795-195">Si les objets ont une propriété avec le nom spécifié et que les valeurs de propriété ont le même type .NET Core, les valeurs de propriété sont regroupées à l’aide des mêmes règles que celles utilisées pour les objets du même type.</span><span class="sxs-lookup"><span data-stu-id="fc795-195">If the objects have a property with the specified name, and the property values have the same .NET Core type, the property values are grouped by using the same rules that would be used for objects of the same type.</span></span>

- <span data-ttu-id="fc795-196">Mêmes noms de propriété, types différents.</span><span class="sxs-lookup"><span data-stu-id="fc795-196">Same Property Names, Different Types.</span></span>

  <span data-ttu-id="fc795-197">Si les objets ont une propriété avec le nom spécifié, mais que les valeurs de propriété ont un type .NET Core différent dans des objets différents, `Group-Object` utilise le type .net Core de la première occurrence de la propriété comme type .net Core pour ce groupe de propriétés.</span><span class="sxs-lookup"><span data-stu-id="fc795-197">If the objects have a property with the specified name, but the property values have a different .NET Core type in different objects, `Group-Object` uses the .NET Core type of the first occurrence of the property as the .NET Core type for that property group.</span></span> <span data-ttu-id="fc795-198">Quand un objet a une propriété avec un type différent, la valeur de la propriété est convertie vers le type de ce groupe.</span><span class="sxs-lookup"><span data-stu-id="fc795-198">When an object has a property with a different type, the property value is converted to the type for that group.</span></span> <span data-ttu-id="fc795-199">Si la conversion de type échoue, l’objet n’est pas inclus dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="fc795-199">If the type conversion fails, the object isn't included in the group.</span></span>

- <span data-ttu-id="fc795-200">Propriétés manquantes.</span><span class="sxs-lookup"><span data-stu-id="fc795-200">Missing Properties.</span></span>

  <span data-ttu-id="fc795-201">Les objets qui n’ont pas de propriété spécifiée ne peuvent pas être regroupés.</span><span class="sxs-lookup"><span data-stu-id="fc795-201">Objects that don't have a specified property can't be grouped.</span></span> <span data-ttu-id="fc795-202">Les objets qui ne sont pas regroupés apparaissent dans la sortie finale de l’objet **GroupInfo** dans un groupe nommé `AutomationNull.Value` .</span><span class="sxs-lookup"><span data-stu-id="fc795-202">Objects that aren't grouped appear in the final **GroupInfo** object output in a group named `AutomationNull.Value`.</span></span>

## <span data-ttu-id="fc795-203">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fc795-203">RELATED LINKS</span></span>

[<span data-ttu-id="fc795-204">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="fc795-204">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="fc795-205">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="fc795-205">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="fc795-206">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="fc795-206">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="fc795-207">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="fc795-207">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="fc795-208">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="fc795-208">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="fc795-209">New-Object</span><span class="sxs-lookup"><span data-stu-id="fc795-209">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="fc795-210">Select-Object</span><span class="sxs-lookup"><span data-stu-id="fc795-210">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="fc795-211">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="fc795-211">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="fc795-212">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="fc795-212">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="fc795-213">Where-Object</span><span class="sxs-lookup"><span data-stu-id="fc795-213">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
