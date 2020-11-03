---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/21/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-csv?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Csv
ms.openlocfilehash: 68b101d0ff36fe9417118dd97d112c070672c9b7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204706"
---
# ConvertFrom-Csv

## SYNOPSIS
Convertit les propriétés d'un objet au format CSV (valeurs séparées par des virgules) en versions CSV des objets d'origine.

## SYNTAX

### DelimiterPath (par défaut)

```
ConvertFrom-Csv [[-Delimiter] <Char>] [-InputObject] <PSObject[]> [-Header <String[]>]
 [<CommonParameters>]
```

### CultureLiteralPath

```
ConvertFrom-Csv -UseCulture [-InputObject] <PSObject[]> [-Header <String[]>] [<CommonParameters>]
```

### CulturePath

```
ConvertFrom-Csv -UseCulture [-InputObject] <PSObject[]> [-Header <String[]>] [<CommonParameters>]
```

## Description

L' `ConvertFrom-Csv` applet de commande crée des objets à partir de chaînes CSV de longueur variable générées par l’applet de commande `ConvertTo-Csv` .

Vous pouvez utiliser les paramètres de cette applet de commande pour spécifier la ligne d’en-tête de colonne, qui détermine les noms de propriété des objets résultants, pour spécifier le délimiteur d’élément, ou pour indiquer à cette applet de commande d’utiliser le séparateur de liste pour la culture actuelle comme délimiteur.

Les objets `ConvertFrom-Csv` créés sont des versions CSV des objets d’origine. Les valeurs de propriété des objets CSV sont des versions sous forme de chaîne des valeurs de propriété des objets d'origine. Les versions CSV des objets ne possèdent aucune méthode.

Vous pouvez également utiliser les `Export-Csv` applets de commande et `Import-Csv` pour convertir des objets en chaînes CSV dans un fichier (et inversement). Ces applets de commande sont les mêmes que les `ConvertTo-Csv` applets de commande et `ConvertFrom-Csv` , à ceci près qu’elles enregistrent les chaînes CSV dans un fichier.

## EXEMPLES

### Exemple 1 : convertir les processus sur l’ordinateur local au format CSV

Cet exemple montre comment convertir les processus sur l’ordinateur local au format CSV, puis les restaurer sous forme d’objet.

```powershell
$P = Get-Process | ConvertTo-Csv
$P | ConvertFrom-Csv
```

L' `Get-Process` applet de commande envoie les processus dans le pipeline à `ConvertTo-Csv` . L' `ConvertTo-Csv` applet de commande convertit les objets processus en une série de chaînes CSV. L' `ConvertFrom-Csv` applet de commande convertit les chaînes CSV en versions CSV des objets processus d’origine. Les chaînes CSV sont enregistrées dans la `$P` variable.

### Exemple 2 : convertir un objet de données au format CSV, puis au format d’objet CSV

Cet exemple montre comment convertir un objet de données au format CSV, puis au format d’objet CSV.

```powershell
$Date = Get-Date | ConvertTo-Csv -Delimiter ';'
ConvertFrom-Csv -InputObject $Date -Delimiter ';'
```

La première commande utilise `Get-Date` pour envoyer la date et l’heure actuelles vers le pipeline `ConvertTo-Csv` . L' `ConvertTo-Csv` applet de commande convertit l’objet date en une série de chaînes CSV.
Le paramètre **Delimiter** est utilisé pour spécifier un délimiteur de point-virgule. Les chaînes sont enregistrées dans la `$Date` variable.

### Exemple 3 : utiliser le paramètre Header pour modifier les noms des propriétés

Cet exemple montre comment utiliser le paramètre **header** de `ConvertFrom-Csv` pour modifier les noms des propriétés dans l’objet importé résultant.

```powershell
$J = Start-Job -ScriptBlock { Get-Process } | ConvertTo-Csv  -NoTypeInformation
$Header = 'State', 'MoreData', 'StatusMessage', 'Location', 'Command', 'StateInfo', 'Finished', 'InstanceId', 'Id', 'Name', 'ChildJobs', 'BeginTime', 'EndTime', 'JobType', 'Output', 'Error', 'Progress', 'Verbose', 'Debug', 'Warning', 'Information'
# Delete the default header from $J
$J = $J[1..($J.count - 1)]
$J | ConvertFrom-Csv -Header $Header
```

```Output
State         : Running
MoreData      : True
StatusMessage :
Location      : localhost
Command       : Get-Process
StateInfo     : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : a259eb63-6824-4b97-a033-305108ae1c2e
Id            : 1
Name          : Job1
ChildJobs     : System.Collections.Generic.List`1[System.Management.Automation.Job]
BeginTime     : 12/20/2018 18:59:57
EndTime       :
JobType       : BackgroundJob
Output        : System.Management.Automation.PSDataCollection`1[System.Management.Automation.PSObject]
Error         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ErrorRecord]
Progress      : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ProgressRecord]
Verbose       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.VerboseRecord]
Debug         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.DebugRecord]
Warning       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.WarningRecord]
Information   : System.Management.Automation.PSDataCollection`1[System.Management.Automation.InformationRecord]
```

L' `Start-Job` applet de commande démarre une tâche en arrière-plan qui s’exécute `Get-Process` . Un objet de traitement est envoyé vers le pipeline `ConvertTo-Csv` et converti en une chaîne CSV. Le paramètre **NoTypeInformation** supprime l’en-tête d’informations de type de la sortie CSV et est facultatif dans PowerShell Core. La `$Header` variable contient un en-tête personnalisé qui remplace les valeurs par défaut suivantes : **HasMoreData** , **JobStateInfo** , **PSBeginTime** , **PSEndTime** et **PSJobTypeName** . La `$J` variable contient la chaîne CSV et est utilisée pour supprimer l’en-tête par défaut. L' `ConvertFrom-Csv` applet de commande convertit la chaîne CSV en **PSCustomObject** et utilise le paramètre d' **en-tête** pour appliquer la `$Header` variable.

### Exemple 4 : convertir des chaînes CSV d’objets de service

Cet exemple montre comment utiliser l' `ConvertFrom-Csv` applet de commande avec le paramètre **UseCulture** .

```powershell
(Get-Culture).TextInfo.ListSeparator
$Services = (Get-Service | ConvertTo-Csv)
ConvertFrom-Csv -InputObject $Services -UseCulture
```

L' `Get-Culture` applet de commande utilise les propriétés imbriquées **TextInfo** et **ListSeparator** pour récupérer le séparateur de liste par défaut de la culture actuelle. L' `Get-Service` applet de commande envoie les objets de service dans le pipeline à `ConvertTo-Csv` . `ConvertTo-Csv`Convertit les objets de service en une série de chaînes CSV. Les chaînes CSV sont stockées dans la `$Services` variable. L' `ConvertFrom-Csv` applet de commande utilise le paramètre **InputObject** et convertit les chaînes CSV de la `$Services` variable. Le paramètre **UseCulture** utilise le séparateur de liste par défaut de la culture actuelle.

Lorsque le paramètre **UseCulture** est utilisé, assurez-vous que le séparateur de liste par défaut de la culture actuelle correspond au délimiteur utilisé dans les chaînes CSV. Dans le cas contraire, `ConvertFrom-Csv` ne peut pas générer d’objets à partir des chaînes CSV.

## PARAMETERS

### -Délimiteur

Spécifie le délimiteur qui sépare les valeurs de propriété dans les chaînes CSV.
La valeur par défaut est une virgule (,).

Entrez un caractère, tel qu'un signe deux-points (:).
Pour spécifier un point-virgule (;) Placez-le entre guillemets simples.

Si vous spécifiez un caractère autre que le délimiteur de chaîne réel dans le fichier, `ConvertFrom-Csv` ne peut pas créer les objets à partir des chaînes CSV et renverra les chaînes CSV.

```yaml
Type: System.Char
Parameter Sets: DelimiterPath
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -En-tête

Spécifie une autre ligne d'en-tête de colonne pour la chaîne importée. L’en-tête de colonne détermine les noms des propriétés des objets créés par `ConvertFrom-Csv` .

Entrez les en-têtes de colonne sous la forme d’une liste séparée par des virgules. Ne placez pas la chaîne d'en-tête entre guillemets. Mettez chaque en-tête de colonne entre guillemets simples.

Si vous entrez moins d’en-têtes de colonnes qu’il n’y a de colonnes de données, les colonnes de données restantes sont ignorées. Si vous entrez davantage d’en-têtes de colonne qu’il n’y a de colonnes de données, les en-têtes de colonne supplémentaires sont créés avec des colonnes de données vides.

Quand vous utilisez le paramètre **header** , omettez la chaîne d’en-tête de colonne des chaînes CSV. Sinon, cette applet de commande crée un objet supplémentaire à partir des éléments de la ligne d’en-tête.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie les chaînes CSV à convertir en objets. Entrez une variable contenant les chaînes CSV, ou tapez une commande ou une expression qui les obtient. Vous pouvez également diriger les chaînes CSV vers `ConvertFrom-Csv` .

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseCulture

Utilise le séparateur de liste pour la culture actuelle comme délimiteur d’élément. Pour rechercher le séparateur de liste pour une culture, utilisez la commande suivante : `(Get-Culture).TextInfo.ListSeparator` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CultureLiteralPath, CulturePath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger les chaînes CSV vers cette applet de commande.

## SORTIES

### System. Management. Automation. PSObject

Cette applet de commande retourne les objets décrits par les propriétés dans les chaînes CSV.

## REMARQUES

Étant donné que les objets importés sont des versions CSV du type d’objet, ils ne sont pas reconnus ni mis en forme par les entrées de mise en forme de type PowerShell qui mettent en forme les versions non-CSV du type d’objet.

Au format CSV, chaque objet est représenté par une liste séparée par des virgules des valeurs de propriété de l'objet. Les valeurs de propriété sont converties en chaînes (à l’aide de la méthode **ToString ()** de l’objet). elles sont donc représentées par le nom de la valeur de propriété. Cette applet de commande n’exporte pas les méthodes de l’objet.

## LIENS CONNEXES

[ConvertTo-Csv](ConvertTo-Csv.md)

[Export-Csv](Export-Csv.md)

[Import-Csv](Import-Csv.md)
