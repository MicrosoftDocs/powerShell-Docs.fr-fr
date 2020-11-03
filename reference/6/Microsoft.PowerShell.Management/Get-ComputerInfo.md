---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: 55e7831112d6385b6d449123973ca4b877faa7fd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204458"
---
# Get-ComputerInfo

## SYNOPSIS
Obtient un objet consolidé des propriétés système et du système d’exploitation.

## SYNTAX

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## Description

L' `Get-ComputerInfo` applet de commande obtient un objet consolidé des propriétés système et du système d’exploitation.
Cette applet de commande a été introduite dans Windows PowerShell 5,1.

## EXEMPLES

### Exemple 1 : récupération de toutes les propriétés de l’ordinateur

```powershell
Get-ComputerInfo
```

Cette commande obtient toutes les propriétés système et système d’exploitation de l’ordinateur.

### Exemple 2 : récupération de toutes les propriétés du système d’exploitation de l’ordinateur

```powershell
Get-ComputerInfo -Property "os*"
```

Cette commande obtient toutes les propriétés du système d’exploitation de l’ordinateur.

## PARAMETERS

### -Propriété

Spécifie, sous forme de tableau de chaînes, les propriétés de l’ordinateur que cette applet de commande affiche.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String[]

## SORTIES

### Microsoft. PowerShell. Management. ComputerInfo

## REMARQUES

## LIENS CONNEXES
