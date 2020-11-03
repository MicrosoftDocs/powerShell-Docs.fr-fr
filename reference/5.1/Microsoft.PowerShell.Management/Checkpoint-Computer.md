---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/checkpoint-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Checkpoint-Computer
ms.openlocfilehash: 61f8d626cd45cfe47f0e65a3043696a01c97ca20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204090"
---
# Checkpoint-Computer

## SYNOPSIS
Crée un point de restauration système sur l'ordinateur local.

## SYNTAX

```
Checkpoint-Computer [-Description] <String> [[-RestorePointType] <String>] [<CommonParameters>]
```

## Description

L' `Checkpoint-Computer` applet de commande crée un point de restauration système sur l’ordinateur local.

Les points de restauration système et l' `Checkpoint-Computer` applet de commande sont pris en charge uniquement sur les systèmes d’exploitation clients, tels que Windows 8, Windows 7, Windows Vista et Windows XP.

À compter de Windows 8, `Checkpoint-Computer` ne peut pas créer plus d’un point de contrôle par jour.

## EXEMPLES

### Exemple 1 : créer un point de restauration système

```powershell
Checkpoint-Computer -Description "Install MyApp"
```

Cette commande crée un point de restauration système appelé install MyApp.
Elle utilise le type de point de restauration par défaut APPLICATION_INSTALL.

### Exemple 2 : créer un point de restauration système MODIFY_SETTINGS

```powershell
Checkpoint-Computer -Description "ChangeNetSettings" -RestorePointType MODIFY_SETTINGS
```

Cette commande crée un point de restauration système MODIFY_SETTINGS appelé « ChangeNetSettings ».

## PARAMETERS

### Description

Spécifie un nom descriptif pour le point de restauration.
Ce paramètre est obligatoire.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RestorePointType

Spécifie le type de point de restauration.
La valeur par défaut est APPLICATION_INSTALL.

Les valeurs valides pour ce paramètre sont :

- APPLICATION_INSTALL
- APPLICATION_UNINSTALL
- DEVICE_DRIVER_INSTALL
- MODIFY_SETTINGS
- CANCELLED_OPERATION

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RPT
Accepted values: APPLICATION_INSTALL, APPLICATION_UNINSTALL, DEVICE_DRIVER_INSTALL, MODIFY_SETTINGS, CANCELLED_OPERATION

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d’objets vers `Checkpoint-Computer` .

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

- Cette applet de commande utilise la méthode **CreateRestorePoint** de la classe **SystemRestore** avec un événement **BEGIN_SYSTEM_CHANGE** .
- À compter de Windows 8, `Checkpoint-Computer` ne peut pas créer plus d’un point de restauration système par jour. Si vous essayez de créer un point de restauration avant l'expiration du délai de 24 heures, Windows PowerShell génère l'erreur suivante :

  `"A new system restore point cannot be created because one has already been created within the past 24 hours.
  Please try again later."`

## LIENS CONNEXES

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Enable-ComputerRestore](Enable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Restore-Computer](Restore-Computer.md)
