---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: 7d399661e4514c0a39ad00601d554c41c2897ff9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203354"
---
# ConvertTo-Csv

## SYNOPSIS
Convertit des objets .NET en une série de chaînes de valeurs séparées par des virgules (CSV).

## SYNTAX

### Délimiteur (par défaut)

```
ConvertTo-Csv [-InputObject] <psobject> [[-Delimiter] <char>] [-NoTypeInformation]
 [<CommonParameters>]
```

### UseCulture

```
ConvertTo-Csv [-InputObject] <psobject> [-UseCulture] [-NoTypeInformation] [<CommonParameters>]
```

## Description

L' `ConvertTo-CSV` applet de commande retourne une série de chaînes de valeurs séparées par des virgules (CSV) qui représentent les objets que vous envoyez. Vous pouvez ensuite utiliser l' `ConvertFrom-Csv` applet de commande pour recréer des objets à partir des chaînes CSV. Les objets convertis à partir de CSV sont des valeurs de chaîne des objets d’origine qui contiennent des valeurs de propriété et aucune méthode.

Vous pouvez utiliser l' `Export-Csv` applet de commande pour convertir des objets en chaînes CSV. `Export-CSV` est semblable à `ConvertTo-CSV` , à ceci près qu’elle enregistre les chaînes CSV dans un fichier.

L' `ConvertTo-CSV` applet de commande possède des paramètres pour spécifier un délimiteur autre qu’une virgule ou utiliser la culture actuelle comme délimiteur.

## EXEMPLES

### Exemple 1 : convertir un objet au format CSV

Cet exemple convertit un objet **processus** en une chaîne CSV.

```powershell
Get-Process -Name 'PowerShell' | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"powershell","11","691","2204036739072","175943680","132665344","33312", ...
```

L' `Get-Process` applet de commande obtient l’objet **processus** et utilise le paramètre **Name** pour spécifier le processus PowerShell. L’objet processus est envoyé dans le pipeline à l’applet de commande `ConvertTo-CSV` . L' `ConvertTo-CSV` applet de commande convertit l’objet en chaînes CSV. Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV.

### Exemple 2 : convertir un objet DateTime en CSV

Cet exemple convertit un objet **DateTime** en une chaîne CSV.

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

L' `Get-Date` applet de commande obtient l’objet **DateTime** et l’enregistre dans la `$Date` variable. L' `ConvertTo-Csv` applet de commande convertit l’objet **DateTime** en chaînes. Le paramètre **InputObject** utilise l’objet **DateTime** stocké dans la `$Date` variable. Le paramètre **Delimiter** spécifie un point-virgule pour séparer les valeurs de chaîne. Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV.

### Exemple 3 : convertir le journal des événements PowerShell au format CSV

Cet exemple convertit le journal des événements Windows pour PowerShell en une série de chaînes CSV.

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'Windows PowerShell' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error","403",,"0","4","4",,"36028797018963968","46891","PowerShell", ...
```

L' `Get-Culture` applet de commande utilise les propriétés imbriquées **TextInfo** et **ListSeparator** et affiche le séparateur de liste par défaut de la culture actuelle. L' `Get-WinEvent` applet de commande obtient les objets du journal des événements et utilise le paramètre **logname** pour spécifier le nom du fichier journal. Les objets du journal des événements sont envoyés vers l’applet de commande via le pipeline `ConvertTo-Csv` . L' `ConvertTo-Csv` applet de commande convertit les objets du journal des événements en une série de chaînes CSV. Le paramètre **UseCulture** utilise le séparateur de liste par défaut de la culture actuelle comme délimiteur. Le paramètre **NoTypeInformation** supprime l’en-tête d’informations **#TYPE** de la sortie CSV.

## PARAMETERS

### -Délimiteur

Spécifie le délimiteur pour séparer les valeurs de propriété dans les chaînes CSV. La valeur par défaut est une virgule ( `,` ). Entrez un caractère, tel qu’un signe deux-points ( `:` ). Pour spécifier un point-virgule ( `;` ), placez-le entre des guillemets simples.

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie les objets qui sont convertis en chaînes CSV. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui les obtient. Vous pouvez également diriger les objets vers `ConvertTo-CSV` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -NoTypeInformation

Supprime l’en-tête d’informations **#TYPE** de la sortie. Ce paramètre est devenu la valeur par défaut dans PowerShell 6,0 et est inclus à des fins de compatibilité descendante.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

Utilise le séparateur de liste pour la culture actuelle comme délimiteur d’élément. Pour rechercher le séparateur de liste pour une culture, utilisez la commande suivante : `(Get-Culture).TextInfo.ListSeparator` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
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

Vous pouvez diriger n’importe quel objet ayant un adaptateur de système de type étendu (ETS) vers `ConvertTo-CSV` .

## SORTIES

### System.String

La sortie CSV est renvoyée sous forme d'une collection de chaînes.

## REMARQUES

Au format CSV, chaque objet est représenté par une liste séparée par des virgules de sa valeur de propriété. Les valeurs de propriété sont converties en chaînes à l’aide de la méthode **ToString ()** de l’objet. Les chaînes sont représentées par le nom de la valeur de propriété. `ConvertTo-CSV` n’exporte pas les méthodes de l’objet.

Les chaînes CSV sont générées comme suit :

- Par défaut, la première chaîne contient l’en-tête d’informations **#TYPE** , suivi du nom qualifié complet du type d’objet. Par exemple, **#TYPE System. Diagnostics. Process** .
- Si **NoTypeInformation** est utilisé, la première chaîne comprend les en-têtes de colonne. Les en-têtes contiennent les noms de propriété du premier objet sous la forme d’une liste séparée par des virgules.
- Les chaînes restantes contiennent des listes séparées par des virgules des valeurs de propriété de chaque objet.

Lorsque vous envoyez plusieurs objets à `ConvertTo-CSV` , `ConvertTo-CSV` trie les chaînes en fonction des propriétés du premier objet que vous envoyez. Si les objets restants n’ont pas l’une des propriétés spécifiées, la valeur de propriété de cet objet est null, comme représenté par deux virgules consécutives. Si les objets restants ont des propriétés supplémentaires, ces valeurs de propriété sont ignorées.

## LIENS CONNEXES

[ConvertFrom-Csv](ConvertFrom-Csv.md)

[Export-Csv](Export-Csv.md)

[Import-Csv](Import-Csv.md)
