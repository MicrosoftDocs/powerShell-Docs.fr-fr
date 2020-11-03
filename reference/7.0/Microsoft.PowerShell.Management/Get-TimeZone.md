---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: 4ed02426fbce279adc3f30af0c95b11966fe75a5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201774"
---
# Get-TimeZone

## SYNOPSIS
Obtient le fuseau horaire actuel ou une liste de fuseaux horaires disponibles.

## SYNTAX

### Nom (par défaut)

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### Id

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### ListAvailable

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## Description

L’applet de commande **« obtenir-TimeZone »** obtient le fuseau horaire actuel ou une liste des fuseaux horaires disponibles.

## EXEMPLES

### Exemple 1 : récupération du fuseau horaire actuel

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

Cette commande obtient le fuseau horaire actuel.

### Exemple 2 : obtenir les fuseaux horaires qui correspondent à une chaîne spécifiée

```
PS C:\> Get-TimeZone -Name "*pac*"
Pacific Standard Time (Mexico)

(UTC-08:00) Pacific Time (US &amp; Canada)

Pacific Standard Time

SA Pacific Standard Time

Pacific SA Standard Time

West Pacific Standard Time

Central Pacific Standard Time
```

Cette commande obtient tous les fuseaux horaires qui correspondent au caractère générique spécifié.

### Exemple 3 : récupération de tous les fuseaux horaires disponibles

```
PS C:\> Get-TimeZone -ListAvailable
```

Cette commande obtient tous les fuseaux horaires disponibles.

## PARAMETERS

### -Id

Spécifie, sous la forme d’un tableau de chaînes, l’ID ou les ID des fuseaux horaires que cette applet de commande obtient.

```yaml
Type: System.String[]
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ListAvailable

Indique que cette applet de commande obtient tous les fuseaux horaires disponibles.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie, sous forme de tableau de chaînes, le nom ou les noms des fuseaux horaires que cette applet de commande obtient.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String[]

## SORTIES

### System. TimeZoneInfo []

## REMARQUES

## LIENS CONNEXES

[Set-TimeZone](Set-TimeZone.md)