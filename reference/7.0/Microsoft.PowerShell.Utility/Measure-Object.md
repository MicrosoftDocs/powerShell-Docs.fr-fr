---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: 37fa83b804516cacf0c1cc1b0a2f4d6b5949178b
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93206005"
---
# Measure-Object

## SYNOPSIS
Calcule les propriétés numériques des objets et les caractères, les mots et les lignes dans les objets de chaîne, par exemple les fichiers de texte.

## SYNTAX

### GenericMeasure (par défaut)

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-StandardDeviation]
 [-Sum] [-AllStats] [-Average] [-Maximum] [-Minimum] [<CommonParameters>]
```

### TextMeasure

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-Line] [-Word]
 [-Character] [-IgnoreWhiteSpace] [<CommonParameters>]
```

## Description

L' `Measure-Object` applet de commande calcule les valeurs de propriété de certains types d’objets.
`Measure-Object` effectue trois types de mesures, selon les paramètres de la commande.

L' `Measure-Object` applet de commande effectue des calculs sur les valeurs de propriété des objets. Vous pouvez utiliser `Measure-Object` pour compter les objets ou compter les objets avec une **propriété** spécifiée. Vous pouvez également utiliser `Measure-Object` pour calculer la valeur **minimale** , la **valeur maximale** , la **somme** , la **StandardDeviation** et la **moyenne** des valeurs numériques. Pour les objets **String** , vous pouvez également utiliser `Measure-Object` pour compter le nombre de lignes, de mots et de caractères.

## EXEMPLES

### Exemple 1 : compter les fichiers et les dossiers dans un répertoire

Cette commande compte les fichiers et dossiers dans le répertoire actif.

```powershell
Get-ChildItem | Measure-Object
```

### Exemple 2 : mesure des fichiers dans un répertoire

Cette commande affiche la **valeur minimale** , la **valeur maximale** et la **somme** des tailles de tous les fichiers dans le répertoire actif, ainsi que la taille moyenne d’un fichier dans le répertoire.

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### Exemple 3 : mesure du texte dans un fichier texte

Cette commande affiche le nombre de caractères, de mots et de lignes dans le fichier Text.txt.
Sans le paramètre **RAW** , `Get-Content` génère le fichier sous la forme d’un tableau de lignes.

La première commande utilise `Set-Content` pour ajouter du texte par défaut à un fichier.

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### Exemple 4 : mesurer des objets contenant une propriété spécifiée

Cet exemple compte le nombre d’objets qui ont une propriété **DisplayName** . Les deux premières commandes récupèrent tous les services et processus sur l’ordinateur local. La troisième commande compte le nombre combiné de services et de processus. La dernière commande combine les deux collections et envoie le résultat à `Measure-Object` .

L’objet **System. Diagnostics. Process** n’a pas de propriété **DisplayName** et n’est pas extrait du nombre final.

```powershell
$services = Get-Service
$processes = Get-Process
$services + $processes | Measure-Object
$services + $processes | Measure-Object -Property DisplayName
```

```Output
Count    : 682
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

Count    : 290
Average  :
Sum      :
Maximum  :
Minimum  :
Property : DisplayName
```

### Exemple 5 : mesurer le contenu d’un fichier CSV

Cette commande calcule les années de service en moyenne des employés d'une société.

Le `ServiceYrs.csv` fichier est un fichier CSV qui contient le numéro d’employé et les années de service de chaque employé. La première ligne de la table est une ligne d’en-tête de **matemp** , **years** .

Lorsque vous utilisez `Import-Csv` pour importer le fichier, le résultat est un **PSCustomObject** avec les propriétés de note **matemp** et **years** .
Vous pouvez utiliser `Measure-Object` pour calculer les valeurs de ces propriétés, comme n’importe quelle autre propriété d’un objet.

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### Exemple 6 : mesurer des valeurs booléennes

Cet exemple montre comment `Measure-Object` peut mesurer des valeurs booléennes.
Dans ce cas, elle utilise la propriété **booléenne** **PSIsContainer** pour mesurer l’incidence des dossiers (par rapport aux fichiers) dans le répertoire actif.

```powershell
Get-ChildItem | Measure-Object -Property psiscontainer -Maximum -Sum -Minimum -Average
```

```Output
Count             : 126
Average           : 0.0634920634920635
Sum               : 8
Maximum           : 1
Minimum           : 0
StandardDeviation :
Property          : PSIsContainer
```

### Exemple 7 : chaînes de mesure

L’exemple suivant mesure le nombre de lignes, d’abord une chaîne unique, puis entre plusieurs chaînes. Le caractère de saut de ligne <code>`n</code> sépare les chaînes en plusieurs lignes.

```powershell
# The newline character `n separates the string into separate lines, as shown in the output.
"One`nTwo`nThree"
"One`nTwo`nThree" | Measure-Object -Line
```

```Output
One
Two
Three


Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The first string counts as a single line.
# The second string is separated into two lines by the newline character.
"One", "Two`nThree" | Measure-Object -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The Word switch counts the number of words in each InputObject
# Each InputObject is treated as a single line.
"One, Two", "Three", "Four Five" | Measure-Object -Word -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3     5
```

### Exemple 8 : mesurer toutes les valeurs

À compter de PowerShell 6, le paramètre **AllStats** de `Measure-Object` vous permet de mesurer toutes les statistiques ensemble.

```powershell
1..5 | Measure-Object -AllStats
```

```output
Count             : 5
Average           : 3
Sum               : 15
Maximum           : 5
Minimum           : 1
StandardDeviation : 1.58113883008419
Property          :
```

### Exemple 9 : mesurer à l’aide des propriétés scriptblock

À compter de PowerShell 6, `Measure-Object` prend en charge les propriétés **scriptblock** . L’exemple suivant montre comment utiliser une propriété **scriptblock** pour déterminer la taille, en mégaoctets, de tous les fichiers d’un répertoire.

```powershell
Get-ChildItem | Measure-Object -Sum {$_.Length/1MB}
```

### Exemple 10 : opérations de tables de hachage

À compter de PowerShell 6, `Measure-Object` prend en charge la mesure de l’entrée de la **Hashtable** . L’exemple suivant détermine la plus grande valeur pour la `num` clé de 3 objets **Hashtable** .

```powershell
@{num=3}, @{num=4}, @{num=5} | Measure-Object -Maximum Num
```

```output
Count             : 3
Average           :
Sum               :
Maximum           : 5
Minimum           :
StandardDeviation :
Property          : num
```

### Exemple 11 : mesurer l’écart type

À compter de PowerShell 6, `Measure-Object` prend en charge le `-StandardDeviation` paramètre. L’exemple suivant détermine l' *écart type* pour le processeur utilisé par tous les processus. Un écart important indique un petit nombre de processus consommant le plus d’UC.

```powershell
Get-Process | Measure-Object -Average -StandardDeviation CPU
```

```output
Count             : 303
Average           : 163.032384488449
Sum               :
Maximum           :
Minimum           :
StandardDeviation : 859.444048419069
Property          : CPU
```

### Exemple 12 : mesurer à l’aide de caractères génériques

À compter de PowerShell 6, `Measure-Object` prend en charge la mesure des objets à l’aide de caractères génériques dans les noms de propriété. L’exemple suivant détermine la valeur maximale de tout type d’utilisation de la mémoire paginée parmi un ensemble de processus.

```powershell
Get-Process | Measure-Object -Maximum *paged*memory*size
```

```output
Count             : 303
Average           :
Sum               :
Maximum           : 735784
Minimum           :
StandardDeviation :
Property          : NonpagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 352104448
Minimum           :
StandardDeviation :
Property          : PagedMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 2201968
Minimum           :
StandardDeviation :
Property          : PagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 719032320
Minimum           :
StandardDeviation :
Property          : PeakPagedMemorySize
```

## PARAMETERS

### -Moyenne

Indique que l’applet de commande affiche la valeur moyenne des propriétés spécifiées.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Caractère

Indique que l’applet de commande compte le nombre de caractères dans les objets d’entrée.

> [!NOTE]
> Le **nombre de** commutateurs de **caractères** et de **lignes** *dans* chaque objet d’entrée, ainsi que *sur* les objets d’entrée. Voir l’exemple 7.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IgnoreWhiteSpace

Indique que l’applet de commande ignore les espaces blancs dans le nombre de caractères.
Par défaut, les espaces ne sont pas ignorés.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie les objets à mesurer.
Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

Quand vous utilisez le paramètre **InputObject** avec `Measure-Object` , au lieu de rediriger les résultats de la commande vers `Measure-Object` , la valeur **InputObject** est traitée comme un objet unique.

Il est recommandé `Measure-Object` d’utiliser dans le pipeline si vous souhaitez mesurer une collection d’objets selon que les objets ont des valeurs spécifiques dans les propriétés définies.

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

### -Ligne

Indique que l’applet de commande compte le nombre de lignes dans les objets d’entrée.

> [!NOTE]
> Le **nombre de** commutateurs de **caractères** et de **lignes** *dans* chaque objet d’entrée, ainsi que *sur* les objets d’entrée. Voir l’exemple 7.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Maximum

Indique que l’applet de commande affiche la valeur maximale des propriétés spécifiées.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minimum

Indique que l’applet de commande affiche la valeur minimale des propriétés spécifiées.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Propriété

Spécifie une ou plusieurs propriétés à mesurer. Si vous ne spécifiez aucune autre mesure, `Measure-Object` compte les objets qui ont les propriétés que vous spécifiez.

La valeur du paramètre **Property** peut être une nouvelle propriété calculée. La propriété calculée doit être un bloc de script. Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -StandardDeviation

Indique que l’applet de commande affiche l’écart type des valeurs des propriétés spécifiées.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sum

Indique que l’applet de commande affiche la somme des valeurs des propriétés spécifiées.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllStats

Indique que l’applet de commande affiche toutes les statistiques des propriétés spécifiées.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Word

Indique que l’applet de commande compte le nombre de mots dans les objets d’entrée.

> [!NOTE]
> Le **nombre de** commutateurs de **caractères** et de **lignes** *dans* chaque objet d’entrée, ainsi que *sur* les objets d’entrée. Voir l’exemple 7.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger les objets vers `Measure-Object` .

## SORTIES

### Microsoft. PowerShell. Commands. GenericMeasureInfo

### Microsoft. PowerShell. Commands. TextMeasureInfo

Si vous utilisez le paramètre **Word** , `Measure-Object` retourne un objet **TextMeasureInfo** .
Sinon, elle retourne un objet **GenericMeasureInfo** .

## REMARQUES

## LIENS CONNEXES

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
