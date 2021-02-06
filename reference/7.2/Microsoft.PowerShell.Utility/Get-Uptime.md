---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uptime?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Uptime
ms.openlocfilehash: 0b71d59175ed56e7aad6a24035d1eff5503e4d88
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595907"
---
# Get-Uptime

## SYNOPSIS
Obtient le **TimeSpan** depuis le dernier démarrage.

## SYNTAXE

### TimeSpan (valeur par défaut)

```
Get-Uptime [<CommonParameters>]
```

### Sa

```
Get-Uptime [-Since] [<CommonParameters>]
```

## Description

Cette applet de commande renvoie la durée écoulée depuis le dernier démarrage du système d’exploitation.

L' `Get-Uptime` applet de commande a été introduite dans PowerShell 6,0.

## EXEMPLES

### Exemple 1 : afficher l’heure depuis le dernier démarrage

```powershell
Get-Uptime
```

```Output
Days              : 9
Hours             : 0
Minutes           : 9
Seconds           : 45
Milliseconds      : 0
Ticks             : 7781850000000
TotalDays         : 9.00677083333333
TotalHours        : 216.1625
TotalMinutes      : 12969.75
TotalSeconds      : 778185
TotalMilliseconds : 778185000
```

### Exemple 2 : afficher l’heure du dernier démarrage

```powershell
Get-Uptime -Since
```

```Output
Tuesday, June 18, 2019 2:34:56 PM
```

## PARAMETERS

### -Depuis

Force l’applet de commande à retourner un objet **DateTime** représentant l’heure du dernier démarrage du système d’exploitation.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Since
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

### None

## SORTIES

### System.TimeSpan

Il s’agit du type de retour par défaut quand aucun paramètre n’est utilisé.

### System.DateTime

Ce type est retourné lors de l’utilisation du paramètre **depuis** .

> [!NOTE]
> Si le démarrage rapide de Windows est activé, Windows ne met pas à jour la valeur stockée dans **LastBootUpTime**. Pour désactiver le démarrage rapide, exécutez la commande suivante : `Powercfg -h off` .
>
> Pour plus d’informations sur le démarrage rapide de Windows, consultez la rubrique [distinction du démarrage rapide de la mise en veille prolongée](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation).

## REMARQUES

Sur Windows, la valeur retournée est la même que la propriété **LastBootUpTime** de la classe **Win32_OperatingSystem** dans WMI.

## LIENS CONNEXES

[Win32_OperatingSystem](/windows/win32/cimwin32prov/win32-operatingsystem#properties)

