---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 10/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/export-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Counter
ms.openlocfilehash: 54498eb504a1d13a5b96a2583b5e5d6e4c08735e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206674"
---
# Export-Counter

## SYNOPSIS
Exporte les données des compteurs de performances dans les fichiers journaux.

## SYNTAX

```
Export-Counter [-Path] <String> [-FileFormat <String>] [-MaxSize <UInt32>]
 -InputObject <PerformanceCounterSampleSet[]> [-Force] [-Circular] [<CommonParameters>]
```

## Description

L' `Export-Counter` applet de commande exporte les données du compteur de performance (objets PerformanceCounterSampleSet) dans les fichiers journaux au format journal de performances binaire (. BLG), de valeurs séparées par des virgules (. csv) ou de valeurs séparées par des tabulations (. TSV). Utilisez cette applet de commande pour consigner les données des compteurs de performances.

L' `Export-Counter` applet de commande est conçue pour exporter les données retournées par les `Get-Counter` applets de commande et `Import-Counter` .

Cette applet de commande s’exécute uniquement sur Windows 7, Windows Server 2008 R2 et les versions ultérieures de Windows.

## EXEMPLES

### EXEMPLE 1 : exporter des données de compteur dans un fichier

Cet exemple exporte des données de compteur dans un fichier BLG.

```powershell
Get-Counter "\Processor(*)\% Processor Time" | Export-Counter -Path $home\Counters.blg
```

La commande utilise l' `Get-Counter` applet de commande pour collecter les données de temps processeur. Elle utilise un opérateur de pipeline (|) pour envoyer les données à l’applet de commande `Export-Counter` . La `Export-Counter` commande utilise la variable **path** pour spécifier le fichier de sortie.

Étant donné que le jeu de données peut être très volumineux, cet exemple envoie les données vers `Export-Counter` via le pipeline. Si les données ont été enregistrées dans une variable, vous pouvez utiliser une quantité disproportionnée de mémoire.

### Exemple 2 : exporter un fichier vers un format de fichier de compteur

Cet exemple convertit un fichier CSV en un format de données de compteur.

L' `Import-Counter` applet de commande importe les données du compteur de performance à partir du `Threads.csv` fichier. L’exemple suppose que ce fichier a été précédemment exporté à l’aide de l’applet de commande `Export-Counter` . Un opérateur de pipeline ( `|` ) envoie les données importées à l’applet de commande `Export-Counter` . La commande utilise le paramètre **Path** pour spécifier l'emplacement du fichier de sortie. Elle utilise les paramètres **circulaires** et **MaxSize** pour indiquer à l' `Export-Counter` applet de commande de créer un journal circulaire qui encapsule 1 Go. Le paramètre **MaxSize** est exprimé en mégaoctets.

```powershell
$1GBInMB = 1024 # 1GB = 1024MB
Import-Counter Threads.csv | Export-Counter -Path ThreadTest.blg -Circular -MaxSize $1GBInMB
```

### Exemple 3 : obtenir des données de compteur à partir d’un ordinateur distant et enregistrer les données dans un fichier

Cet exemple montre comment obtenir les données de compteur de performances d'un ordinateur distant, et les enregistrer dans un fichier sur l'ordinateur distant.

La première commande utilise l' `Get-Counter` applet de commande pour collecter les données de compteur de jeu de travail à partir de Serveur01, un ordinateur distant. La commande enregistre les données dans la `$C` variable.

La deuxième commande utilise un opérateur de pipeline ( `|` ) pour envoyer les données dans `$C` l’applet de commande `Export-Counter` , ce qui l’enregistre dans le `Workingset.blg` fichier du partage de performances de l’ordinateur SERVEUR01.

```powershell
$C = Get-Counter -ComputerName Server01 -Counter "\Process(*)\Working Set - Private" -MaxSamples $C | Export-Counter -Path \\Server01\Perf\WorkingSet.blg
```

```Output
20
```

### Exemple 4 : rejournalisation des données existantes

Cet exemple montre comment utiliser les `Import-Counter` applets de commande et `Export-Counter` pour rejournaliser les données existantes.

La première commande utilise l' `Import-Counter` applet de commande pour importer des données de compteur de performance à partir du journal de l’enregistrement de fichier. BLG. Elle enregistre les données dans la `$All` variable. Ce fichier contient des exemples du compteur « \% espace libre du disque logique » sur plus de 200 ordinateurs distants dans l’entreprise.

La deuxième commande utilise l' `Where-Object` applet de commande pour sélectionner des objets dont le **CookedValue** est inférieur à 15 (en pourcentage). La commande enregistre les résultats dans la `$LowSpace` variable.

La troisième commande utilise un opérateur de pipeline ( `|` ) pour envoyer les données de la `$LowSpace` variable à l’applet de commande `Export-Counter` . La commande utilise le paramètre **Path** pour indiquer que les données sélectionnées doivent être journalisées dans le fichier LowDiskSpace.blg.

```powershell
$All = Import-Counter DiskSpace.blg
$LowSpace = $All | Where-Object {$_.CounterSamples.CookedValue -lt 15}
$LowSpace | Export-Counter -Path LowDiskSpace.blg
```

## PARAMETERS

### -Circulaire

Indique que le fichier de sortie est un journal circulaire avec le format premier entré, premier sorti (FIFO).
Quand vous incluez ce paramètre, le paramètre **MaxSize** est obligatoire.

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

### -FileFormat

Spécifie le format de sortie du fichier journal de sortie.

Les valeurs valides pour ce paramètre sont :

- CSV
- TSV
- BLG

La valeur par défaut est BLG.

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

### -Force

Remplace et remplace un fichier existant s’il existe dans l’emplacement spécifié par le paramètre **path** .

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

### -InputObject

Spécifie, sous forme de tableau, les données de compteur à exporter. Entrez une variable qui contient les données ou une commande qui obtient les données, telles que l' `Get-Counter` applet de commande ou `Import-Counter` .

```yaml
Type: Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -MaxSize

Spécifie la taille maximale du fichier de sortie en mégaoctets (Mo).

Si le paramètre **circulaire** est spécifié, quand le fichier journal atteint la taille maximale spécifiée, les entrées les plus anciennes sont supprimées, car les plus récentes sont ajoutées. Si le paramètre **circulaire** n’est pas spécifié, quand le fichier journal atteint la taille maximale spécifiée, aucune nouvelle donnée n’est ajoutée et l’applet de commande génère une erreur sans fin d’achèvement.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d'accès et le nom de fichier du fichier de sortie. Entrez un chemin d’accès relatif ou absolu sur l’ordinateur local, ou un chemin d’accès UNC (Uniform Naming Convention) à un ordinateur distant, tel que `\\Computer\Share\file.blg` . Ce paramètre est obligatoire.

Le format de fichier est déterminé par la valeur du paramètre **FileFormat** , et non par l’extension de nom de fichier dans le chemin d’accès.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Microsoft. PowerShell. Commands. GetCounter. PerformanceCounterSampleSet

Vous pouvez diriger les données du compteur de performance à partir de `Get-Counter` ou `Import-Counter` vers cette applet de commande.

## SORTIES

### Aucun

## REMARQUES

Le générateur de fichier journal s'attend à ce que tous les objets d'entrée aient le même chemin d'accès de compteur, et que ces objets soient regroupés par ordre chronologie croissant.

Le type et le chemin d'accès de compteur du premier objet d'entrée déterminent les propriétés enregistrées dans le fichier journal. Si d'autres objets d'entrée n'ont pas de valeur pour une propriété enregistrée, le champ de propriété est vide. Si les objets ont des valeurs de propriété qui n'étaient pas enregistrées, les valeurs de propriété supplémentaires sont ignorées.

L’analyseur de performances risque de ne pas pouvoir lire tous les journaux `Export-Counter` générés par. Par exemple, l’analyseur de performances nécessite que tous les objets aient le même chemin et que tous les objets soient séparés par le même intervalle de temps.

L' `Import-Counter` applet de commande n’a pas de paramètre **ComputerName** . Toutefois, si l’ordinateur est configuré pour Windows PowerShell Windows PowerShell à distance, vous pouvez utiliser la `Invoke-Command` cmdlet pour exécuter une `Import-Counter` commande sur un ordinateur distant.

## LIENS CONNEXES

[Get-Counter](Get-Counter.md)

[Import-Counter](Import-Counter.md)
