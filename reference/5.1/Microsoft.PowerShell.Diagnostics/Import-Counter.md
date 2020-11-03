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
# Import-Counter

## SYNOPSIS
Importe les fichiers journaux des compteurs de performance et crée les objets qui représentent chaque échantillon de compteur dans le journal.

## SYNTAX

### GetCounterSet (par défaut)

```
Import-Counter [-Path] <String[]> [-StartTime <DateTime>] [-EndTime <DateTime>] [-Counter <String[]>]
 [-MaxSamples <Int64>] [<CommonParameters>]
```

### ListSetSet

```
Import-Counter [-Path] <String[]> -ListSet <String[]> [<CommonParameters>]
```

### SummarySet

```
Import-Counter [-Path] <String[]> [-Summary] [<CommonParameters>]
```

## Description

L’applet de commande **Import-Counter** importe les données des compteurs de performances à partir des fichiers journaux des compteurs de performances et crée des objets pour chaque échantillon de compteur dans le fichier.
Les objets **PerformanceCounterSampleSet** qu’il crée sont identiques aux objets que la méthode **obten-Counter** retourne lorsqu’il collecte des données de compteurs de performances.

Vous pouvez importer des données à partir de fichiers journaux de performances comportant des valeurs séparées par des virgules (.csv), des valeur séparées par des tabulations (.tsv) et des enregistrements de performances binaires (.blg).
Si vous utilisez des fichiers. BLG, vous pouvez importer jusqu’à 32 fichiers dans chaque commande.
Vous pouvez utiliser les paramètres d' **Import-Counter** pour filtrer les données que vous importez.

Outre les applets de commande Get-Counter et Export-Counter, cette fonctionnalité vous permet de collecter, d’exporter, d’importer, de combiner, de filtrer, de manipuler et de réexporter les données des compteurs de performances dans Windows PowerShell.

## EXEMPLES

### Exemple 1 : importer toutes les données de compteur à partir d’un fichier

```powershell
$Data = Import-Counter -Path ProcessorData.csv
```

Cette commande importe toutes les données de compteur à partir du fichier ProcessorData.csv dans la variable $Data.

### Exemple 2 : importer des données de compteur spécifiques à partir d’un fichier

```
PS C:\> $I = Import-Counter -Path "ProcessorData.blg" -Counter "\\SERVER01\Processor(_Total)\Interrupts/sec"
```

Cette commande importe uniquement les données de compteur **« processeur (_Total) \ interruptions/s »** à partir du fichier ProcessorData. BLG dans la variable $I.

### Exemple 3 : sélectionner des données à partir d’un compteur de performances, puis les exporter vers un fichier

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

Cet exemple montre comment sélectionner des données dans un fichier journal de compteurs de performances (.blg), puis exporter les données sélectionnées dans un fichier .csv.
Les quatre premières commandes récupèrent les chemins d’accès des compteurs à partir du fichier et les enregistrent dans la variable nommée $Data.
Au cours des deux dernières commandes, les données sélectionnées sont importées, puis exportées.

### Exemple 4 : afficher tous les chemins de compteur dans un groupe d’ensembles de compteurs importés

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

Cet exemple montre comment afficher tous les chemins de compteur dans un groupe d'ensembles de compteurs importés.

### Exemple 5 : importer des données de compteur à partir d’une plage d’horodatages

```
The first command lists in a table the time stamps of all of the data in the ProcessorData.blg file.
PS C:\> Import-Counter -Path ".\disk.blg" | Format-Table -Property Timestamp

The second command saves particular time stamps in the $Start and $End variables. The strings are cast to **DateTime** objects.
PS C:\> $Start = [datetime]"7/9/2008 3:47:00 PM"; $End = [datetime]"7/9/2008 3:47:59 PM"

The third command uses the **Import-Counter** cmdlet to get only counter data that has a time stamp between the start and end times (inclusive). The command uses the *StartTime* and *EndTime* parameters of **Import-Counter** to specify the range.
PS C:\> Import-Counter -Path Disk.blg -StartTime $start -EndTime $end
```

Cet exemple importe uniquement les données de compteur dont l'horodatage se situe entre les plages de début et de fin spécifiées dans la commande.

### Exemple 6 : importer un nombre spécifié d’échantillons les plus anciens à partir d’un fichier journal de compteur de performances

```
The first command uses the **Import-Counter** cmdlet to import the first (oldest) five samples from the Disk.blg file. The command uses the *MaxSamples* parameter to limit the import to five counter samples.
PS C:\> Import-Counter -Path "Disk.blg" -MaxSamples 5

The second command uses array notation and the Windows PowerShell range operator (..) to get the last five counter samples from the file. These are the five newest samples.
PS C:\> (Import-Counter -Path Disk.blg)[-1 .. -5]
```

Cet exemple montre comment importer les cinq échantillons les plus anciens et les cinq les plus récents d'un fichier journal de compteurs de performances.

### Exemple 7 : obtenir un résumé des données de compteur à partir d’un fichier

```
PS C:\> Import-Counter "D:\Samples\Memory.blg" -Summary

OldestRecord            NewestRecord            SampleCount
------------            ------------            -----------
7/10/2008 2:59:18 PM    7/10/2008 3:00:27 PM    1000
```

Cette commande utilise le paramètre *Summary* de l'applet de commande **Import-Counter** pour obtenir un résumé des données de compteur dans le fichier Memory.blg.

### Exemple 8 : mettre à jour un fichier journal de compteur de performances

```
The first command uses the *ListSet* parameter of **Import-Counter** to get the counters in OldData.blg, an existing counter log file. The command uses a pipeline operator (|) to send the data to a ForEach-Object command that gets only the values of the **PathsWithInstances** property of each object
PS C:\> $Counters = Import-Counter OldData.blg -ListSet * | ForEach-Object {$_.PathsWithInstances}

The second command gets updated data for the counters in the $Counters variable. It uses the Get-Counter cmdlet to get a current sample, and then export the results to the NewData.blg file.
PS C:\> Get-Counter -Counter $Counters -MaxSamples 20 | Export-Counter C:\Logs\NewData.blg
```

Cet exemple met à jour un fichier journal de compteurs de performances.

### Exemple 9 : importer des données de journaux de performances à partir de plusieurs fichiers, puis les enregistrer

```
PS C:\> $Counters = "D:\test\pdata.blg", "D:\samples\netlog.blg" | Import-Counter
```

Cette commande importe les données de deux journaux de performances et les enregistre dans la variable $Counters.
Cette commande utilise un opérateur pipeline pour envoyer les chemins d'accès des journaux de performances à Import-Counter, qui importe les données à partir des chemins d'accès spécifiés.

Notez que chaque chemin d'accès est placé entre guillemets et que les chemins d'accès sont séparés par une virgule.

## PARAMETERS

### -Compteur

Spécifie, sous la forme d’un tableau de chaînes, les compteurs de performances.
Par défaut, **Import-Counter** importe toutes les données de tous les compteurs dans les fichiers d’entrée.
Entrez un ou plusieurs chemins de compteur.
Les caractères génériques sont autorisés dans la partie Instance du chemin d'accès.

Chaque chemin de compteur a le format ci-après.
La valeur ComputerName est requise dans le chemin d’accès.
Exemple :

- `\\<ComputerName>\<CounterSet>(<Instance>)\<CounterName>`

Par exemple :

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

### -EndTime

Spécifie une date et une heure de fin pendant lesquelles cette applet de commande importe des données de compteur entre l’heure de *début* et les horodateurs de ce paramètre.
Entrez un objet **DateTime** , tel que celui créé par l’applet de commande Get-Date.
Par défaut, **Import-Counter** importe toutes les données de compteur dans les fichiers spécifiés par le paramètre *path* .

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

### -ListSet

Spécifie les ensembles de compteurs de performance qui sont représentés dans les fichiers exportés.
Les commandes contenant ce paramètre n'importent pas de données.

Entrez un ou plusieurs noms d'ensemble de compteurs.
Les caractères génériques sont autorisés.
Pour récupérer tous les ensembles de compteurs dans le fichier, tapez `Import-Counter -ListSet *` .

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

### -MaxSamples

Spécifie le nombre maximal d'échantillons de chaque compteur à importer.
Par défaut, l’option **de récupération d’un compteur** importe toutes les données dans les fichiers spécifiés par le paramètre *path* .

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

### -Path

Spécifie les chemins d'accès des fichiers à importer.
Ce paramètre est obligatoire.

Entrez le chemin d’accès et le nom du fichier. csv,,. TSV ou. BLG que vous avez exporté à l’aide de l’applet de commande **Export-Counter** .
Vous ne pouvez spécifier qu'un seul fichier .csv ou .tsv, mais vous pouvez indiquer plusieurs fichiers .blg (jusqu'à 32) par commande.
Vous pouvez également diriger les chaînes de chemin d’accès de fichier (entre guillemets) vers **Import-Counter** .

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

### -StartTime

Spécifie la date et l’heure de début auxquelles cette applet de commande obtient les données de compteur.
Entrez un objet **DateTime** , tel que celui créé par l’applet de commande **obtenir-date** .
Par défaut, **Import-Counter** importe toutes les données de compteur dans les fichiers spécifiés par le paramètre *path* .

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

### -Summary

Indique que cette applet de commande obtient un résumé des données importées, au lieu d’obtenir des échantillons de données de compteurs individuels.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger les chemins d’accès du journal des compteurs de performances vers cette applet de commande.

## SORTIES

### Microsoft. PowerShell. Commands. GetCounter. PerformanceCounterSampleSet, Microsoft. PowerShell. Commands. GetCounter. CounterSet, Microsoft. PowerShell. Commands. GetCounter. CounterFileInfo

Cette applet de commande retourne un **Microsoft. PowerShell. Commands. GetCounter. PerformanceCounterSampleSet** .
Si vous utilisez le paramètre *ListSet* , cette applet de commande retourne un objet **Microsoft. PowerShell. Commands. GetCounter. CounterSet** .
Si vous utilisez le paramètre *Summary* , cette applet de commande retourne un objet **Microsoft. PowerShell. Commands. GetCounter. CounterFileInfo** .

## REMARQUES

* Cette applet de commande n’a pas de paramètre *ComputerName* . Toutefois, si l’ordinateur est configuré pour la communication à distance Windows PowerShell, vous pouvez utiliser l’applet de commande Invoke-Command pour exécuter une commande **Import-Counter** sur un ordinateur distant.

## LIENS CONNEXES

[Export-Counter](Export-Counter.md)

[Get-Counter](Get-Counter.md)
