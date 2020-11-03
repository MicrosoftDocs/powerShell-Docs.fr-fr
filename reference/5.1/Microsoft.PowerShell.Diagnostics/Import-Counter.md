---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/import-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Counter
ms.openlocfilehash: 837f6b4b3b2869c6f74b3b02904dd43b73f6bcd5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202622"
---
# <span data-ttu-id="e8cfb-103">Import-Counter</span><span class="sxs-lookup"><span data-stu-id="e8cfb-103">Import-Counter</span></span>

## <span data-ttu-id="e8cfb-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e8cfb-104">SYNOPSIS</span></span>
<span data-ttu-id="e8cfb-105">Importe les fichiers journaux des compteurs de performance et crée les objets qui représentent chaque échantillon de compteur dans le journal.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-105">Imports performance counter log files and creates the objects that represent each counter sample in the log.</span></span>

## <span data-ttu-id="e8cfb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e8cfb-106">SYNTAX</span></span>

### <span data-ttu-id="e8cfb-107">GetCounterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="e8cfb-107">GetCounterSet (Default)</span></span>

```
Import-Counter [-Path] <String[]> [-StartTime <DateTime>] [-EndTime <DateTime>] [-Counter <String[]>]
 [-MaxSamples <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="e8cfb-108">ListSetSet</span><span class="sxs-lookup"><span data-stu-id="e8cfb-108">ListSetSet</span></span>

```
Import-Counter [-Path] <String[]> -ListSet <String[]> [<CommonParameters>]
```

### <span data-ttu-id="e8cfb-109">SummarySet</span><span class="sxs-lookup"><span data-stu-id="e8cfb-109">SummarySet</span></span>

```
Import-Counter [-Path] <String[]> [-Summary] [<CommonParameters>]
```

## <span data-ttu-id="e8cfb-110">Description</span><span class="sxs-lookup"><span data-stu-id="e8cfb-110">DESCRIPTION</span></span>

<span data-ttu-id="e8cfb-111">L’applet de commande **Import-Counter** importe les données des compteurs de performances à partir des fichiers journaux des compteurs de performances et crée des objets pour chaque échantillon de compteur dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-111">The **Import-Counter** cmdlet imports performance counter data from performance counter log files and creates objects for each counter sample in the file.</span></span>
<span data-ttu-id="e8cfb-112">Les objets **PerformanceCounterSampleSet** qu’il crée sont identiques aux objets que la méthode **obten-Counter** retourne lorsqu’il collecte des données de compteurs de performances.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-112">The **PerformanceCounterSampleSet** objects that it creates are identical to the objects that **Get-Counter** returns when it collects performance counter data.</span></span>

<span data-ttu-id="e8cfb-113">Vous pouvez importer des données à partir de fichiers journaux de performances comportant des valeurs séparées par des virgules (.csv), des valeur séparées par des tabulations (.tsv) et des enregistrements de performances binaires (.blg).</span><span class="sxs-lookup"><span data-stu-id="e8cfb-113">You can import data from comma-separated value (.csv), tab-separated value ( .tsv), and binary performance log (.blg) performance log files.</span></span>
<span data-ttu-id="e8cfb-114">Si vous utilisez des fichiers. BLG, vous pouvez importer jusqu’à 32 fichiers dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-114">If you are using .blg files, you can import up to 32 files in each command.</span></span>
<span data-ttu-id="e8cfb-115">Vous pouvez utiliser les paramètres d' **Import-Counter** pour filtrer les données que vous importez.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-115">You can use the parameters of **Import-Counter** to filter the data that you import.</span></span>

<span data-ttu-id="e8cfb-116">Outre les applets de commande Get-Counter et Export-Counter, cette fonctionnalité vous permet de collecter, d’exporter, d’importer, de combiner, de filtrer, de manipuler et de réexporter les données des compteurs de performances dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-116">Along with the Get-Counter and Export-Counter cmdlets, this feature lets you collect, export, import, combine, filter, manipulate, and re-export performance counter data within Windows PowerShell.</span></span>

## <span data-ttu-id="e8cfb-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e8cfb-117">EXAMPLES</span></span>

### <span data-ttu-id="e8cfb-118">Exemple 1 : importer toutes les données de compteur à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="e8cfb-118">Example 1: Import all counter data from a file</span></span>

```powershell
$Data = Import-Counter -Path ProcessorData.csv
```

<span data-ttu-id="e8cfb-119">Cette commande importe toutes les données de compteur à partir du fichier ProcessorData.csv dans la variable $Data.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-119">This command imports all counter data from the ProcessorData.csv file into the $Data variable.</span></span>

### <span data-ttu-id="e8cfb-120">Exemple 2 : importer des données de compteur spécifiques à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="e8cfb-120">Example 2: Import specific counter data from a file</span></span>

```
PS C:\> $I = Import-Counter -Path "ProcessorData.blg" -Counter "\\SERVER01\Processor(_Total)\Interrupts/sec"
```

<span data-ttu-id="e8cfb-121">Cette commande importe uniquement les données de compteur **« processeur (_Total) \ interruptions/s »** à partir du fichier ProcessorData. BLG dans la variable $I.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-121">This command imports only the **"Processor(_total)\Interrupts/sec"** counter data from the ProcessorData.blg file into the $I variable.</span></span>

### <span data-ttu-id="e8cfb-122">Exemple 3 : sélectionner des données à partir d’un compteur de performances, puis les exporter vers un fichier</span><span class="sxs-lookup"><span data-stu-id="e8cfb-122">Example 3: Select data from a performance counter then export it to a file</span></span>

```
The first command uses **Import-Counter** to import all of the performance counter data from the ProcessorData.blg files. The command saves the data in the $Data variable.
PS C:\> $Data = Import-Counter .\ProcessorData.blg

The second command displays the counter paths in the $Data variable. To get the display shown in the command output, the example uses the Format-Table cmdlet to format as a table the counter paths of the first counter in the $Data variable.
PS C:\> $Data[0].CounterSamples | Format-Table -Property Path

Path
----
\\SERVER01\Processor(_Total)\DPC Rate
\\SERVER01\Processor(1)\DPC Rate
\\SERVER01\Processor(0)\DPC Rate
\\SERVER01\Processor(_Total)\% Idle Time
\\SERVER01\Processor(1)\% Idle Time
\\SERVER01\Processor(0)\% Idle Time
\\SERVER01\Processor(_Total)\% C3 Time
\\SERVER01\Processor(1)\% C3 Time

The third command gets the counter paths that end in "Interrupts/sec" and saves the paths in the $IntCtrs variable. It uses the Where-Object cmdlet to filter the counter paths and the ForEach-Object cmdlet to get only the value of the **Path** property of each selected path object.
PS C:\> $IntCtrs = $Data[0].Countersamples | Where-Object {$_.Path -like "*Interrupts/sec"} | ForEach-Object {$_.Path}

The fourth command displays the selected counter paths in the $IntCtrs variable.
PS C:\> $IntCtrs

\\SERVER01\Processor(_Total)\Interrupts/sec
\\SERVER01\Processor(1)\Interrupts/sec
\\SERVER01\Processor(0)\Interrupts/sec

The fifth command uses the **Import-Counter** cmdlet to import the data. It uses the $IntCtrs variable as the value of the *Counter* parameter to import only data for the counter paths in $IntCtrs.
PS C:\> $I = Import-Counter -Path .\ProcessorData.blg -Counter $intCtrs

The sixth command uses the Export-Counter cmdlet to export the data to the Interrupts.csv file.
PS C:\> $I | Export-Counter -Path .\Interrupts.csv -Format CSV
```

<span data-ttu-id="e8cfb-123">Cet exemple montre comment sélectionner des données dans un fichier journal de compteurs de performances (.blg), puis exporter les données sélectionnées dans un fichier .csv.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-123">This example shows how to select data from a performance counter log file (.blg) and then export the selected data to a .csv file.</span></span>
<span data-ttu-id="e8cfb-124">Les quatre premières commandes récupèrent les chemins d’accès des compteurs à partir du fichier et les enregistrent dans la variable nommée $Data.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-124">The first four commands get the counter paths from the file and save them in the variable named $Data.</span></span>
<span data-ttu-id="e8cfb-125">Au cours des deux dernières commandes, les données sélectionnées sont importées, puis exportées.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-125">The last two commands import selected data and then export only the selected data.</span></span>

### <span data-ttu-id="e8cfb-126">Exemple 4 : afficher tous les chemins de compteur dans un groupe d’ensembles de compteurs importés</span><span class="sxs-lookup"><span data-stu-id="e8cfb-126">Example 4: Display all counter paths in a group of imported counter sets</span></span>

```
The first command uses the *ListSet* parameter of the **Import-Counter** cmdlet to get all of the counter sets that are represented in a counter data file.
PS C:\> Import-Counter -Path ProcessorData.csv -ListSet *

CounterSetName     : Processor
MachineName        : \\SERVER01
CounterSetType     : MultiInstance
Description        :
Paths              : {\\SERVER01\Processor(*)\DPC Rate, \\SERVER01\Processor(*)\% Idle Time, \\SERVER01
\Processor(*)\% C3 Time, \\SERVER01\Processor(*)\% Interrupt Time...}
PathsWithInstances : {\\SERVER01\Processor(_Total)\DPC Rate, \\SERVER01\Processor(1)\DPC Rate, \\SERVER01
\Processor(0)\DPC Rate, \\SERVER01\Processor(_Total)\% Idle Time...}
Counter            : {\\SERVER01\Processor(*)\DPC Rate, \\SERVER01\Processor(*)\% Idle Time, \\SERVER01
\Processor(*)\% C3 Time, \\SERVER01\Processor(*)\% Interrupt Time...}

The second command gets all of the counter paths from the list set.
PS C:\> Import-Counter -Path ProcessorData.csv -ListSet * | ForEach-Object {$_.Paths}

\\SERVER01\Processor(*)\DPC Rate
\\SERVER01\Processor(*)\% Idle Time
\\SERVER01\Processor(*)\% C3 Time
\\SERVER01\Processor(*)\% Interrupt Time
\\SERVER01\Processor(*)\% C2 Time
\\SERVER01\Processor(*)\% User Time
\\SERVER01\Processor(*)\% C1 Time
\\SERVER01\Processor(*)\% Processor Time
\\SERVER01\Processor(*)\C1 Transitions/sec
\\SERVER01\Processor(*)\% DPC Time
\\SERVER01\Processor(*)\C2 Transitions/sec
\\SERVER01\Processor(*)\% Privileged Time
\\SERVER01\Processor(*)\C3 Transitions/sec
\\SERVER01\Processor(*)\DPCs Queued/sec
\\SERVER01\Processor(*)\Interrupts/sec
```

<span data-ttu-id="e8cfb-127">Cet exemple montre comment afficher tous les chemins de compteur dans un groupe d'ensembles de compteurs importés.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-127">This example shows how to display all the counter paths in a group of imported counter sets.</span></span>

### <span data-ttu-id="e8cfb-128">Exemple 5 : importer des données de compteur à partir d’une plage d’horodatages</span><span class="sxs-lookup"><span data-stu-id="e8cfb-128">Example 5: Import counter data from a range of time stamps</span></span>

```
The first command lists in a table the time stamps of all of the data in the ProcessorData.blg file.
PS C:\> Import-Counter -Path ".\disk.blg" | Format-Table -Property Timestamp

The second command saves particular time stamps in the $Start and $End variables. The strings are cast to **DateTime** objects.
PS C:\> $Start = [datetime]"7/9/2008 3:47:00 PM"; $End = [datetime]"7/9/2008 3:47:59 PM"

The third command uses the **Import-Counter** cmdlet to get only counter data that has a time stamp between the start and end times (inclusive). The command uses the *StartTime* and *EndTime* parameters of **Import-Counter** to specify the range.
PS C:\> Import-Counter -Path Disk.blg -StartTime $start -EndTime $end
```

<span data-ttu-id="e8cfb-129">Cet exemple importe uniquement les données de compteur dont l'horodatage se situe entre les plages de début et de fin spécifiées dans la commande.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-129">This example imports only the counter data that has a time stamp between the starting an ending ranges specified in the command.</span></span>

### <span data-ttu-id="e8cfb-130">Exemple 6 : importer un nombre spécifié d’échantillons les plus anciens à partir d’un fichier journal de compteur de performances</span><span class="sxs-lookup"><span data-stu-id="e8cfb-130">Example 6: Import a specified number of the oldest samples from a performance counter log file</span></span>

```
The first command uses the **Import-Counter** cmdlet to import the first (oldest) five samples from the Disk.blg file. The command uses the *MaxSamples* parameter to limit the import to five counter samples.
PS C:\> Import-Counter -Path "Disk.blg" -MaxSamples 5

The second command uses array notation and the Windows PowerShell range operator (..) to get the last five counter samples from the file. These are the five newest samples.
PS C:\> (Import-Counter -Path Disk.blg)[-1 .. -5]
```

<span data-ttu-id="e8cfb-131">Cet exemple montre comment importer les cinq échantillons les plus anciens et les cinq les plus récents d'un fichier journal de compteurs de performances.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-131">This example shows how to import the five oldest and five newest samples from a performance counter log file.</span></span>

### <span data-ttu-id="e8cfb-132">Exemple 7 : obtenir un résumé des données de compteur à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="e8cfb-132">Example 7: Get a summary of counter data from a file</span></span>

```
PS C:\> Import-Counter "D:\Samples\Memory.blg" -Summary

OldestRecord            NewestRecord            SampleCount
------------            ------------            -----------
7/10/2008 2:59:18 PM    7/10/2008 3:00:27 PM    1000
```

<span data-ttu-id="e8cfb-133">Cette commande utilise le paramètre *Summary* de l'applet de commande **Import-Counter** pour obtenir un résumé des données de compteur dans le fichier Memory.blg.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-133">This command uses the *Summary* parameter of the **Import-Counter** cmdlet to get a summary of the counter data in the Memory.blg file.</span></span>

### <span data-ttu-id="e8cfb-134">Exemple 8 : mettre à jour un fichier journal de compteur de performances</span><span class="sxs-lookup"><span data-stu-id="e8cfb-134">Example 8: Update a performance counter log file</span></span>

```
The first command uses the *ListSet* parameter of **Import-Counter** to get the counters in OldData.blg, an existing counter log file. The command uses a pipeline operator (|) to send the data to a ForEach-Object command that gets only the values of the **PathsWithInstances** property of each object
PS C:\> $Counters = Import-Counter OldData.blg -ListSet * | ForEach-Object {$_.PathsWithInstances}

The second command gets updated data for the counters in the $Counters variable. It uses the Get-Counter cmdlet to get a current sample, and then export the results to the NewData.blg file.
PS C:\> Get-Counter -Counter $Counters -MaxSamples 20 | Export-Counter C:\Logs\NewData.blg
```

<span data-ttu-id="e8cfb-135">Cet exemple met à jour un fichier journal de compteurs de performances.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-135">This example updates a performance counter log file.</span></span>

### <span data-ttu-id="e8cfb-136">Exemple 9 : importer des données de journaux de performances à partir de plusieurs fichiers, puis les enregistrer</span><span class="sxs-lookup"><span data-stu-id="e8cfb-136">Example 9: Import performance log data from multiple files and then save it</span></span>

```
PS C:\> $Counters = "D:\test\pdata.blg", "D:\samples\netlog.blg" | Import-Counter
```

<span data-ttu-id="e8cfb-137">Cette commande importe les données de deux journaux de performances et les enregistre dans la variable $Counters.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-137">This command imports performance log data from two logs and saves the data in the $Counters variable.</span></span>
<span data-ttu-id="e8cfb-138">Cette commande utilise un opérateur pipeline pour envoyer les chemins d'accès des journaux de performances à Import-Counter, qui importe les données à partir des chemins d'accès spécifiés.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-138">The command uses a pipeline operator to send the performance log paths to Import-Counter, which imports the data from the specified paths.</span></span>

<span data-ttu-id="e8cfb-139">Notez que chaque chemin d'accès est placé entre guillemets et que les chemins d'accès sont séparés par une virgule.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-139">Notice that each path is enclosed in quotation marks and that the paths are separated from each other by a comma.</span></span>

## <span data-ttu-id="e8cfb-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e8cfb-140">PARAMETERS</span></span>

### <span data-ttu-id="e8cfb-141">-Compteur</span><span class="sxs-lookup"><span data-stu-id="e8cfb-141">-Counter</span></span>

<span data-ttu-id="e8cfb-142">Spécifie, sous la forme d’un tableau de chaînes, les compteurs de performances.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-142">Specifies, as a string array, the performance counters.</span></span>
<span data-ttu-id="e8cfb-143">Par défaut, **Import-Counter** importe toutes les données de tous les compteurs dans les fichiers d’entrée.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-143">By default, **Import-Counter** imports all data from all counters in the input files.</span></span>
<span data-ttu-id="e8cfb-144">Entrez un ou plusieurs chemins de compteur.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-144">Enter one or more counter paths.</span></span>
<span data-ttu-id="e8cfb-145">Les caractères génériques sont autorisés dans la partie Instance du chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-145">Wildcards are permitted in the Instance part of the path.</span></span>

<span data-ttu-id="e8cfb-146">Chaque chemin de compteur a le format ci-après.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-146">Each counter path has the following format.</span></span>
<span data-ttu-id="e8cfb-147">La valeur ComputerName est requise dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-147">The ComputerName value is required in the path.</span></span>
<span data-ttu-id="e8cfb-148">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e8cfb-148">For instance:</span></span>

- `\\<ComputerName>\<CounterSet>(<Instance>)\<CounterName>`

<span data-ttu-id="e8cfb-149">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e8cfb-149">For example:</span></span>

- `\\Server01\Processor(2)\% User Time`
- `\\Server01\Processor(*)\% Processor Time`

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: All counter
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e8cfb-150">-EndTime</span><span class="sxs-lookup"><span data-stu-id="e8cfb-150">-EndTime</span></span>

<span data-ttu-id="e8cfb-151">Spécifie une date et une heure de fin pendant lesquelles cette applet de commande importe des données de compteur entre l’heure de *début* et les horodateurs de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-151">Specifies an end date and time that this cmdlet imports counter data between the *StartTime* and this parameter timestamps.</span></span>
<span data-ttu-id="e8cfb-152">Entrez un objet **DateTime** , tel que celui créé par l’applet de commande Get-Date.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-152">Enter a **DateTime** object, such as one created by the Get-Date cmdlet.</span></span>
<span data-ttu-id="e8cfb-153">Par défaut, **Import-Counter** importe toutes les données de compteur dans les fichiers spécifiés par le paramètre *path* .</span><span class="sxs-lookup"><span data-stu-id="e8cfb-153">By default, **Import-Counter** imports all counter data in the files specified by the *Path* parameter.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No end time
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8cfb-154">-ListSet</span><span class="sxs-lookup"><span data-stu-id="e8cfb-154">-ListSet</span></span>

<span data-ttu-id="e8cfb-155">Spécifie les ensembles de compteurs de performance qui sont représentés dans les fichiers exportés.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-155">Specifies the performance counter sets that are represented in the exported files.</span></span>
<span data-ttu-id="e8cfb-156">Les commandes contenant ce paramètre n'importent pas de données.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-156">Commands with this parameter do not import any data.</span></span>

<span data-ttu-id="e8cfb-157">Entrez un ou plusieurs noms d'ensemble de compteurs.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-157">Enter one or more counter set names.</span></span>
<span data-ttu-id="e8cfb-158">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-158">Wildcards are permitted.</span></span>
<span data-ttu-id="e8cfb-159">Pour récupérer tous les ensembles de compteurs dans le fichier, tapez `Import-Counter -ListSet *` .</span><span class="sxs-lookup"><span data-stu-id="e8cfb-159">To get all counter sets in the file, type `Import-Counter -ListSet *`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e8cfb-160">-MaxSamples</span><span class="sxs-lookup"><span data-stu-id="e8cfb-160">-MaxSamples</span></span>

<span data-ttu-id="e8cfb-161">Spécifie le nombre maximal d'échantillons de chaque compteur à importer.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-161">Specifies the maximum number of samples of each counter to import.</span></span>
<span data-ttu-id="e8cfb-162">Par défaut, l’option **de récupération d’un compteur** importe toutes les données dans les fichiers spécifiés par le paramètre *path* .</span><span class="sxs-lookup"><span data-stu-id="e8cfb-162">By default, **Get-Counter** imports all of the data in the files specified by the *Path* parameter.</span></span>

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No maximum
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8cfb-163">-Path</span><span class="sxs-lookup"><span data-stu-id="e8cfb-163">-Path</span></span>

<span data-ttu-id="e8cfb-164">Spécifie les chemins d'accès des fichiers à importer.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-164">Specifies the file paths of the files to be imported.</span></span>
<span data-ttu-id="e8cfb-165">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-165">This parameter is required.</span></span>

<span data-ttu-id="e8cfb-166">Entrez le chemin d’accès et le nom du fichier. csv,,. TSV ou. BLG que vous avez exporté à l’aide de l’applet de commande **Export-Counter** .</span><span class="sxs-lookup"><span data-stu-id="e8cfb-166">Enter the path and file name of a, .csv,, .tsv, or .blg file that you exported by using the **Export-Counter** cmdlet.</span></span>
<span data-ttu-id="e8cfb-167">Vous ne pouvez spécifier qu'un seul fichier .csv ou .tsv, mais vous pouvez indiquer plusieurs fichiers .blg (jusqu'à 32) par commande.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-167">You can specify only one .csv or .tsv file, but you can specify multiple .blg files (up to 32) in each command.</span></span>
<span data-ttu-id="e8cfb-168">Vous pouvez également diriger les chaînes de chemin d’accès de fichier (entre guillemets) vers **Import-Counter** .</span><span class="sxs-lookup"><span data-stu-id="e8cfb-168">You can also pipe file path strings (in quotation marks) to **Import-Counter** .</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="e8cfb-169">-StartTime</span><span class="sxs-lookup"><span data-stu-id="e8cfb-169">-StartTime</span></span>

<span data-ttu-id="e8cfb-170">Spécifie la date et l’heure de début auxquelles cette applet de commande obtient les données de compteur.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-170">Specifies the start date and time in which this cmdlet gets counter data.</span></span>
<span data-ttu-id="e8cfb-171">Entrez un objet **DateTime** , tel que celui créé par l’applet de commande **obtenir-date** .</span><span class="sxs-lookup"><span data-stu-id="e8cfb-171">Enter a **DateTime** object, such as one created by the **Get-Date** cmdlet.</span></span>
<span data-ttu-id="e8cfb-172">Par défaut, **Import-Counter** importe toutes les données de compteur dans les fichiers spécifiés par le paramètre *path* .</span><span class="sxs-lookup"><span data-stu-id="e8cfb-172">By default, **Import-Counter** imports all counter data in the files specified by the *Path* parameter.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No start time
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8cfb-173">-Summary</span><span class="sxs-lookup"><span data-stu-id="e8cfb-173">-Summary</span></span>

<span data-ttu-id="e8cfb-174">Indique que cette applet de commande obtient un résumé des données importées, au lieu d’obtenir des échantillons de données de compteurs individuels.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-174">Indicates that this cmdlet gets a summary of the imported data, instead of getting individual counter data samples.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SummarySet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8cfb-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e8cfb-175">CommonParameters</span></span>

<span data-ttu-id="e8cfb-176">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e8cfb-177">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e8cfb-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e8cfb-178">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e8cfb-178">INPUTS</span></span>

### <span data-ttu-id="e8cfb-179">System.String</span><span class="sxs-lookup"><span data-stu-id="e8cfb-179">System.String</span></span>

<span data-ttu-id="e8cfb-180">Vous pouvez diriger les chemins d’accès du journal des compteurs de performances vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-180">You can pipe performance counter log paths to this cmdlet.</span></span>

## <span data-ttu-id="e8cfb-181">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e8cfb-181">OUTPUTS</span></span>

### <span data-ttu-id="e8cfb-182">Microsoft. PowerShell. Commands. GetCounter. PerformanceCounterSampleSet, Microsoft. PowerShell. Commands. GetCounter. CounterSet, Microsoft. PowerShell. Commands. GetCounter. CounterFileInfo</span><span class="sxs-lookup"><span data-stu-id="e8cfb-182">Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet, Microsoft.PowerShell.Commands.GetCounter.CounterSet, Microsoft.PowerShell.Commands.GetCounter.CounterFileInfo</span></span>

<span data-ttu-id="e8cfb-183">Cette applet de commande retourne un **Microsoft. PowerShell. Commands. GetCounter. PerformanceCounterSampleSet** .</span><span class="sxs-lookup"><span data-stu-id="e8cfb-183">This cmdlet returns a **Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet** .</span></span>
<span data-ttu-id="e8cfb-184">Si vous utilisez le paramètre *ListSet* , cette applet de commande retourne un objet **Microsoft. PowerShell. Commands. GetCounter. CounterSet** .</span><span class="sxs-lookup"><span data-stu-id="e8cfb-184">If you use the *ListSet* parameter, this cmdlet returns a **Microsoft.PowerShell.Commands.GetCounter.CounterSet** object.</span></span>
<span data-ttu-id="e8cfb-185">Si vous utilisez le paramètre *Summary* , cette applet de commande retourne un objet **Microsoft. PowerShell. Commands. GetCounter. CounterFileInfo** .</span><span class="sxs-lookup"><span data-stu-id="e8cfb-185">If you use the *Summary* parameter, this cmdlet returns a **Microsoft.PowerShell.Commands.GetCounter.CounterFileInfo** object.</span></span>

## <span data-ttu-id="e8cfb-186">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e8cfb-186">NOTES</span></span>

* <span data-ttu-id="e8cfb-187">Cette applet de commande n’a pas de paramètre *ComputerName* .</span><span class="sxs-lookup"><span data-stu-id="e8cfb-187">This cmdlet does not have a *ComputerName* parameter.</span></span> <span data-ttu-id="e8cfb-188">Toutefois, si l’ordinateur est configuré pour la communication à distance Windows PowerShell, vous pouvez utiliser l’applet de commande Invoke-Command pour exécuter une commande **Import-Counter** sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e8cfb-188">However, if the computer is configured for Windows PowerShell remoting, you can use the Invoke-Command cmdlet to run an **Import-Counter** command on a remote computer.</span></span>

## <span data-ttu-id="e8cfb-189">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e8cfb-189">RELATED LINKS</span></span>

[<span data-ttu-id="e8cfb-190">Export-Counter</span><span class="sxs-lookup"><span data-stu-id="e8cfb-190">Export-Counter</span></span>](Export-Counter.md)

[<span data-ttu-id="e8cfb-191">Get-Counter</span><span class="sxs-lookup"><span data-stu-id="e8cfb-191">Get-Counter</span></span>](Get-Counter.md)
