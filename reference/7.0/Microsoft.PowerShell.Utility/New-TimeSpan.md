---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-timespan?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TimeSpan
ms.openlocfilehash: 7e96437c67180eaac0e3163eaf799b34de2b903f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201461"
---
# New-TimeSpan

## SYNOPSIS
Crée un objet TimeSpan.

## SYNTAX

### Date (par défaut)

```
New-TimeSpan [[-Start] <DateTime>] [[-End] <DateTime>] [<CommonParameters>]
```

### Heure

```
New-TimeSpan [-Days <Int32>] [-Hours <Int32>] [-Minutes <Int32>] [-Seconds <Int32>] [<CommonParameters>]
```

## Description

L' `New-TimeSpan` applet de commande crée un objet **TimeSpan** qui représente un intervalle de temps.
Vous pouvez utiliser un objet **TimeSpan** pour ajouter ou soustraire du temps à des objets **DateTime** .

Sans paramètres, une `New-TimeSpan` commande retourne un objet **TimeSpan** qui représente un intervalle de temps égal à zéro.

## EXEMPLES

### Exemple 1 : créer un objet TimeSpan pour une durée spécifiée

Cette commande crée un objet **TimeSpan** avec une durée de 1 heure et 25 minutes et le stocke dans une variable nommée `$TimeSpan` . Elle affiche une représentation de l’objet **TimeSpan** .

```powershell
$TimeSpan = New-TimeSpan -Hours 1 -Minutes 25
$TimeSpan
```

```Output
Days              : 0
Hours             : 1
Minutes           : 25
Seconds           : 0
Milliseconds      : 0
Ticks             : 51000000000
TotalDays         : 0.0590277777777778
TotalHours        : 1.41666666666667
TotalMinutes      : 85
TotalSeconds      : 5100
TotalMilliseconds : 5100000
```

### Exemple 2 : créer un objet TimeSpan pour un intervalle de temps

Cet exemple crée un nouvel objet **TimeSpan** qui représente l’intervalle entre l’exécution de la commande et le 1er janvier 2010.

Cette commande ne nécessite pas le paramètre **Start** , car la valeur par défaut du paramètre **Start** correspond à la date et à l’heure actuelles.

```powershell
New-TimeSpan -End (Get-Date -Year 2010 -Month 1 -Day 1)
```

### Exemple 3 : récupérer la date 90 jours à partir de la date actuelle

```powershell
$90days = New-TimeSpan -Days 90
(Get-Date) + $90days
```

Ces commandes retournent la date située 90 jours après la date actuelle.

### Exemple 4 : découvrir la période depuis la mise à jour d’un fichier

Cette commande vous indique le temps écoulé depuis la dernière mise à jour du fichier d’aide [about_Remote](../Microsoft.PowerShell.Core/About/about_Remote.md) .
Vous pouvez utiliser ce format de commande sur n’importe quel fichier ou tout autre objet qui possède une propriété **LastWriteTime** .

Cette commande fonctionne parce que le paramètre de **démarrage** de `New-TimeSpan` a un alias **LastWriteTime** . Quand vous dirigez un objet qui a une propriété **LastWriteTime** vers `New-TimeSpan` , PowerShell utilise la valeur de la propriété **LastWriteTime** comme valeur du paramètre **Start** .

```powershell
Get-ChildItem $PSHOME\en-us\about_remote.help.txt | New-TimeSpan
```

```Output
Days              : 321
Hours             : 21
Minutes           : 59
Seconds           : 22
Milliseconds      : 312
Ticks             : 278135623127728
TotalDays         : 321.916230471907
TotalHours        : 7725.98953132578
TotalMinutes      : 463559.371879547
TotalSeconds      : 27813562.3127728
TotalMilliseconds : 27813562312.7728
```

## PARAMETERS

### -Days

Spécifie les jours dans l’intervalle de temps.
La valeur par défaut est 0.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fin

Spécifie la fin d’un intervalle de temps.
La valeur par défaut est l'horodatage actuel.

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: False
Position: 1
Default value: Current date and time
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### Heures d’ouverture

Spécifie les heures dans l’intervalle de temps.
La valeur par défaut est zéro.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minutes

Spécifie les minutes dans l’intervalle de temps.
La valeur par défaut est 0.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Secondes

Spécifie la longueur de l’intervalle de temps en secondes.
La valeur par défaut est 0.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Start

Spécifie le début d’un intervalle de temps.
Entrez une chaîne qui représente la date et l’heure, par exemple « 3/15/09 » ou un objet **DateTime** , tel que celui d’une `Get-Date` commande. La valeur par défaut est l'horodatage actuel.

Vous pouvez utiliser **Start** ou son alias, **LastWriteTime** .
L’alias **LastWriteTime** vous permet de diriger des objets qui ont une propriété **LastWriteTime** , tels que des fichiers dans le système de fichiers `[System.Io.FileIO]` , vers le paramètre de **démarrage** de `New-TimeSpan` .

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases: LastWriteTime

Required: False
Position: 0
Default value: Current date and time
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.DateTime

Vous pouvez diriger un objet **DateTime** qui représente cette heure de début vers `New-TimeSpan` .

## SORTIES

### System.TimeSpan

`New-TimeSpan` retourne un objet qui représente l’intervalle de temps.

## REMARQUES

## LIENS CONNEXES

[Obtient la date](Get-Date.md)

[Set-Date](Set-Date.md)
