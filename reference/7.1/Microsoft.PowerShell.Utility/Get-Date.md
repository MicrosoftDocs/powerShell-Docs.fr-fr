---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: 34b0d7833d858a8b71c28d0f872ddb9e4948b76d
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95514981"
---
# Get-Date

## SYNOPSIS
Obtient les date et heure actuelles.

## SYNTAXE

### Date (par défaut)

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### DateUFormat

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

### UnixTimeSeconds

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### UnixTimeSecondsUFormat

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

## Description

L' `Get-Date` applet de commande obtient un objet **DateTime** qui représente la date actuelle ou une date que vous spécifiez. `Get-Date` peut mettre en forme la date et l’heure dans plusieurs formats .NET et UNIX. Vous pouvez utiliser `Get-Date` pour générer une chaîne de caractères de date ou d’heure, puis envoyer la chaîne à d’autres applets de commande ou programmes.

`Get-Date` utilise les paramètres de culture de l’ordinateur pour déterminer comment la sortie est mise en forme. Pour afficher les paramètres de votre ordinateur, utilisez `(Get-Culture).DateTimeFormat` .

## EXEMPLES

### Exemple 1 : récupération de la date et de l’heure actuelles

Dans cet exemple, `Get-Date` affiche la date et l’heure système actuelles. La sortie est dans les formats de date longue et d’heure longue.

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### Exemple 2 : obtient les éléments de la date et de l’heure actuelles

Cet exemple montre comment utiliser `Get-Date` pour récupérer l’élément de date ou d’heure. Le paramètre utilise les arguments **Date**, **Time** ou **DateTime**.

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

`Get-Date` utilise le paramètre **DisplayHint** avec l’argument **Date** pour récupérer uniquement la date.

### Exemple 3 : obtenir la date et l’heure avec un spécificateur de format .NET

Dans cet exemple, un spécificateur de format .NET est utilisé pour personnaliser le format de la sortie. La sortie est un objet **String** .

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

`Get-Date` utilise le paramètre **format** pour spécifier plusieurs spécificateurs de format.

Les spécificateurs de format .NET utilisés dans cet exemple sont définis comme suit :

| Spécificateur |                      Définition                       |
| --------- | ----------------------------------------------------- |
| `dddd`    | Jour de la semaine-Nom complet                           |
| `MM`      | Numéro du mois                                          |
| `dd`      | Jour du mois-2 chiffres                           |
| `yyyy`    | Année au format à 4 chiffres                                |
| `HH:mm`   | Heure au format 24 heures-pas de secondes                    |
| `K`       | Décalage de fuseau horaire par rapport à l’heure UTC (Universal Time Coordinate) |

Pour plus d’informations sur les spécificateurs de format .NET, consultez [chaînes de format de date et d’heure personnalisées](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).

### Exemple 4 : obtenir la date et l’heure avec un spécificateur UFormat

Dans cet exemple, plusieurs spécificateurs de format **UFormat** sont utilisés pour personnaliser le format de la sortie.
La sortie est un objet **String** .

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

`Get-Date` utilise le paramètre **UFormat** pour spécifier plusieurs spécificateurs de format.

Les spécificateurs de format **UFormat** utilisés dans cet exemple sont définis comme suit :

| Spécificateur |                      Définition                       |
| --------- | ----------------------------------------------------- |
| `%A`      | Jour de la semaine-Nom complet                           |
| `%m`      | Numéro du mois                                          |
| `%d`      | Jour du mois-2 chiffres                           |
| `%Y`      | Année au format à 4 chiffres                                |
| `%R`      | Heure au format 24 heures-pas de secondes                    |
| `%Z`      | Décalage de fuseau horaire par rapport à l’heure UTC (Universal Time Coordinate) |

Pour obtenir la liste des spécificateurs de format **UFormat** valides, consultez la section [Remarques](#notes) .

### Exemple 5 : obtenir le jour d’une date de l’année

Dans cet exemple, une propriété est utilisée pour obtenir le nombre de jours de l’année.

Le calendrier grégorien contient 365 jours, à l’exception des années bissextiles qui comportent 366 jours. Par exemple, le 31 décembre 2020 est le jour 366.

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

`Get-Date` utilise trois paramètres pour spécifier la date : **année**, **mois** et **jour**. La commande est entourée de parenthèses afin que le résultat soit évalué par la propriété **DayofYear** .

### Exemple 6 : vérifier si une date est ajustée pour l’heure d’été

Cet exemple utilise une méthode booléenne pour vérifier si une date est ajustée par l’heure d’été.

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

Une variable, `$DST` stocke le résultat de `Get-Date` . `$DST` utilise la méthode **IsDaylightSavingTime** pour tester si la date est ajustée pour l’heure d’été.

### Exemple 7 : convertir l’heure actuelle en heure UTC

Dans cet exemple, l’heure actuelle est convertie en heure UTC. L’offset UTC pour les paramètres régionaux du système est utilisé pour convertir l’heure. Un tableau de la section [Remarques](#notes) répertorie les spécificateurs de format **UFormat** valides.

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

`Get-Date` utilise le paramètre **UFormat** avec des spécificateurs de format pour afficher la date et l’heure système actuelles. Le spécificateur de format **% Z** représente l’offset UTC de **-07**.

La `$Time` variable stocke la date et l’heure système actuelles. `$Time` utilise la méthode **ToUniversalTime ()** pour convertir l’heure en fonction du décalage UTC de l’ordinateur.

### Exemple 8 : créer un horodateur

Dans cet exemple, un spécificateur de format crée un objet de **chaîne** d’horodatage pour un nom de répertoire. L’horodateur contient la date, l’heure et le décalage UTC.

```powershell
$timestamp = Get-Date -Format o | ForEach-Object { $_ -replace ":", "." }
New-Item -Path C:\Test\$timestamp -Type Directory
```

```Output
Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         6/27/2019    07:59                2019-06-27T07.59.24.4603750-07.00
```

La `$timestamp` variable stocke les résultats d’une `Get-Date` commande. `Get-Date` utilise le paramètre de **format** avec le spécificateur de format en minuscules `o` pour créer un objet de **chaîne** d’horodatage. L’objet est envoyé dans le pipeline à `ForEach-Object` . Un **scriptblock** contient la `$_` variable qui représente l’objet de pipeline actuel. La chaîne d’horodatage est délimitée par des signes deux-points qui sont remplacés par des points.

`New-Item` utilise le paramètre **path** pour spécifier l’emplacement d’un nouveau répertoire. Le chemin d’accès comprend la `$timestamp` variable en tant que nom de répertoire. Le paramètre de **type** spécifie qu’un répertoire est créé.

### Exemple 9 : convertir un horodateur UNIX

Cet exemple convertit une heure UNIX (représentée par le nombre de secondes depuis 1970-01-01 0:00:00) en DateTime.

```powershell
Get-Date -UnixTimeSeconds 1577836800
```

```Output
Wednesday, January 01, 2020 12:00:00 AM
```

### Exemple 10 : retourner une valeur de date interprétée comme UTC

Cet exemple montre comment interpréter une valeur de date comme son équivalent UTC. Pour l’exemple, cet ordinateur est défini à l' **heure standard du Pacifique**. Par défaut, `Get-Date` retourne des valeurs pour ce fuseau horaire. Utilisez le paramètre **AsUTC** pour convertir la valeur en heure UTC équivalente.

```powershell
PS> Get-TimeZone

Id                         : Pacific Standard Time
DisplayName                : (UTC-08:00) Pacific Time (US & Canada)
StandardName               : Pacific Standard Time
DaylightName               : Pacific Daylight Time
BaseUtcOffset              : -08:00:00
SupportsDaylightSavingTime : True

PS> (Get-Date -Date "2020-01-01T00:00:00").Kind
Unspecified

PS> Get-Date -Date "2020-01-01T00:00:00"

Wednesday, January 1, 2020 12:00:00 AM

PS> (Get-Date -Date "2020-01-01T00:00:00" -AsUTC).Kind
Utc

PS> Get-Date -Date "2020-01-01T00:00:00" -AsUTC

Wednesday, January 1, 2020 8:00:00 AM
```

## PARAMETERS

### -AsUTC

Convertit la valeur de date en heure équivalente en heure UTC.

Ce paramètre a été introduit dans PowerShell 7,1.

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

### -Date

Spécifie une date et une heure. L’heure est facultative et, si elle n’est pas spécifiée, retourne 00:00:00.

Entrez la date et l’heure dans un format standard pour les paramètres régionaux système.

Par exemple, en anglais (États-Unis) :

`Get-Date -Date "6/25/2019 12:30:22"` retourne mardi 25 juin, 2019 12:30:22

```yaml
Type: System.DateTime
Parameter Sets: DateAndFormat, DateAndUFormat
Aliases: LastWriteTime

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Jour

Spécifie le jour du mois qui s'affiche. Entrez une valeur comprise entre 1 et 31.

Si la valeur spécifiée est supérieure au nombre de jours d’un mois, PowerShell ajoute le nombre de jours au mois. Par exemple, `Get-Date -Month 2 -Day 31` affiche le **3 mars**, et non le **31 février**.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayHint

Détermine les éléments de date et d'heure à afficher.

Les valeurs acceptées sont les suivantes :

- **Date**: affiche uniquement la date
- **Heure**: affiche uniquement l’heure
- **DateTime**: affiche la date et l’heure

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Format

Affiche la date et l'heure dans le format Microsoft .NET Framework indiqué par le spécificateur de format.
Le paramètre **format** génère un objet **String** .

Pour obtenir la liste des spécificateurs de format .NET disponibles, consultez [chaînes de format de date et d’heure personnalisées](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).

Lorsque le paramètre **format** est utilisé, `Get-Date` obtient uniquement les propriétés de l’objet **DateTime** nécessaires à l’affichage de la date. Ainsi, certaines propriétés et méthodes des objets **DateTime** ne sont peut-être pas disponibles.

À compter de PowerShell 5,0, vous pouvez utiliser les formats supplémentaires suivants comme valeurs pour le paramètre **format** .

- **Archivé**. Représentation conviviale d’un fichier ou d’un chemin d’accès de la date actuelle en heure locale. Le format est `yyyyMMdd` (respecte la casse, en utilisant une année à 4 chiffres, un mois à 2 chiffres et un jour à 2 chiffres). Par exemple :
  20190627.

- **FileDateUniversal**. Représentation conviviale d’un fichier ou d’un chemin d’accès de la date actuelle en temps universel (UTC). Le format est `yyyyMMddZ` (respect de la casse, en utilisant une année à 4 chiffres, un mois à 2 chiffres, un jour à 2 chiffres et la lettre `Z` comme indicateur UTC). Par exemple : 20190627Z.

- **FileDateTime**. Représentation conviviale de fichier ou de chemin d’accès de la date et de l’heure en heure locale, au format 24 heures. Le format est `yyyyMMddTHHmmssffff` (respect de la casse, en utilisant une année à 4 chiffres, un mois à 2 chiffres, un jour à 2 chiffres, la lettre `T` comme séparateur horaire, l’heure à 2 chiffres, la minute à 2 chiffres, la seconde à 2 chiffres et la milliseconde sur 4 chiffres). Par exemple : 20190627T0840107271.

- **FileDateTimeUniversal**. Représentation conviviale d’un fichier ou d’un chemin d’accès de la date et de l’heure en temps universel (UTC), au format 24 heures. Le format est `yyyyMMddTHHmmssffffZ` (respect de la casse, en utilisant une année à 4 chiffres, un mois à 2 chiffres, un jour à 2 chiffres, la lettre `T` comme séparateur d’heure, une heure à 2 chiffres, une minute à 2 chiffres, une seconde à 2 chiffres, une milliseconde à 4 chiffres et la lettre `Z` comme indicateur UTC). Par exemple : 20190627T1540500718Z.

```yaml
Type: System.String
Parameter Sets: DateAndFormat, UnixTimeSecondsAndFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Heure

Spécifie l'heure qui s'affiche. Entrez une valeur comprise entre 0 et 23.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Milliseconde

Spécifie le nombre de millisecondes dans la date. Entrez une valeur comprise entre 0 et 999.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minute

Spécifie le nombre de minutes qui s'affiche. Entrez une valeur comprise entre 0 et 59.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Mois

Spécifie le mois qui s'affiche. Entrez une valeur comprise entre 1 et 12.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Seconde

Spécifie le nombre de secondes qui s'affiche. Entrez une valeur comprise entre 0 et 59.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UFormat

Affiche la date et l'heure au format UNIX. Le paramètre **UFormat** génère un objet String.

Les spécificateurs **UFormat** sont précédés d’un signe `%` de pourcentage (), par exemple,, `%m` `%d` et `%Y` . La section [Remarques](#notes) contient un tableau de **spécificateurs UFormat** valides.

Lorsque le paramètre **UFormat** est utilisé, `Get-Date` obtient uniquement les propriétés de l’objet **DateTime** nécessaires à l’affichage de la date. Ainsi, certaines propriétés et méthodes des objets **DateTime** ne sont peut-être pas disponibles.

```yaml
Type: System.String
Parameter Sets: DateAndUFormat, UnixTimeSecondsAndUFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UnixTimeSeconds

Date et heure représentées en secondes depuis le 1er janvier 1970, 0:00:00.

Ce paramètre a été introduit dans PowerShell 7,1.

```yaml
Type: System.Int64
Parameter Sets: UnixTimeSecondsAndFormat, UnixTimeSecondsAndUFormat
Aliases: UnixTime

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Année

Spécifie l'année qui s'affiche. Entrez une valeur comprise entre 1 et 9999.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Entrée de pipeline

`Get-Date` accepte l’entrée de pipeline. Par exemple, `Get-ChildItem | Get-Date`.

## SORTIES

### System. DateTime ou System. String

`Get-Date` retourne un objet **DateTime** sauf lorsque les paramètres **format** et **UFormat** sont utilisés. Les paramètres **format** ou **UFormat** retournent des objets de **chaîne** .

Lorsqu’un objet **DateTime** est envoyé vers le pipeline à une applet de commande, comme `Add-Content` qui attend une entrée de chaîne, PowerShell convertit l’objet en un objet **String** .

La méthode `(Get-Date).ToString()` convertit un objet **DateTime** en objet **String** .

Pour afficher les propriétés et les méthodes d’un objet, envoyez l’objet vers le dessous du pipeline `Get-Member` .
Par exemple, `Get-Date | Get-Member`.

## REMARQUES

Les objets **DateTime** sont dans des formats de date longue et d’heure longue pour les paramètres régionaux système.

Les **spécificateurs UFormat** valides sont affichés dans le tableau suivant :

| Spécificateur de format |                                 Signification                     |         Exemple          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | Jour de la semaine-Nom complet                                             | Lundi                   |
| `%a` | Jour de la semaine-Nom abrégé                                      | Lun                      |
| `%B` | Nom du mois-complet                                                       | Janvier                  |
| `%b` | Nom du mois-abrégé                                                | Jan                      |
| `%C` | Siècle                                                                 | 20 pour 2019              |
| `%c` | Date et heure-abrégé                                             | Jeudi Juin 27 08:44:18 2019 |
| `%D` | Date au format mm/jj/aa                                                 | 06/27/19                 |
| `%d` | Jour du mois-2 chiffres                                             | 05                       |
| `%e` | Jour du mois-précédé d’un espace si seul un chiffre           | \<space\>5,5               |
| `%F` | Date au format aaaa-mm-jj, égale à% Y-% m-% d (le format de date ISO 8601) | 2019-06-27               |
| `%G` | Identique à « Y »                                                             |                          |
| `%g` | Identique à « y »                                                             |                          |
| `%H` | Heure au format 24 heures                                                  | 17                       |
| `%h` | Identique à « b »                                                             |                          |
| `%I` | Heure au format 12 heures                                                  | 05                       |
| `%j` | Jour de l’année                                                         | 1-366                    |
| `%k` | Identique à « H »                                                             |                          |
| `%l` | Identique à « I » (I majuscule)                                              | 05                       |
| `%M` | Minutes                                                                 | 35                       |
| `%m` | Numéro du mois                                                            | 06                       |
| `%n` | caractère de saut de ligne                                                       |                          |
| `%p` | AM ou PM                                                                |                          |
| `%R` | Heure au format 24 heures-pas de secondes                                      | 17:45                    |
| `%r` | Heure au format 12 heures                                                  | 09:15:36              |
| `%S` | Secondes                                                                 | 05                       |
| `%s` | Secondes écoulées depuis le 1er janvier 1970 00:00:00                          | 1150451174               |
| `%t` | Caractère de tabulation horizontale                                                |                          |
| `%T` | Heure au format 24 heures                                                  | 17:45:52                 |
| `%U` | Identique à « W »                                                             |                          |
| `%u` | Jour de la semaine-numéro                                                | Dimanche = 0               |
| `%V` | Semaine de l’année                                                        | 01-53                    |
| `%w` | Identique à « u »                                                             |                          |
| `%W` | Semaine de l’année                                                        | 00-52                    |
| `%X` | Identique à « t »                                                             |                          |
| `%x` | Date au format standard pour les paramètres régionaux                                      | 06/27/19 pour l’anglais (États-Unis)  |
| `%Y` | Année au format à 4 chiffres                                                  | 2019                     |
| `%y` | Année au format à 2 chiffres                                                  | 19                       |
| `%Z` | Décalage de fuseau horaire par rapport à l’heure UTC (Universal Time Coordinate)                   | -07                      |

## LIENS CONNEXES

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-Culture](Get-Culture.md)

[Get-Member](Get-Member.md)

[New-Item](../Microsoft.PowerShell.Management/New-Item.md)

[New-TimeSpan](New-TimeSpan.md)

[Set-Date](Set-Date.md)
