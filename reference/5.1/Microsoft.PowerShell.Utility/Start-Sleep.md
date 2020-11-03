---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 3/13/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: e4add39c09b6123aaf8c9302529346a6b1dec391
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203118"
---
# Start-Sleep

## SYNOPSIS
Interrompt l'activité dans un script ou une session pour la période spécifiée.

## SYNTAX

### Secondes (par défaut)

```
Start-Sleep [-Seconds] <Int32> [<CommonParameters>]
```

### Millisecondes

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## Description

L' `Start-Sleep` applet de commande suspend l’activité dans un script ou une session pour la période spécifiée.
Vous pouvez l'utiliser pour de nombreuses tâches, comme attendre qu'une opération se termine ou soit suspendue avant de répéter une opération.

## EXEMPLES

### Exemple 1 : mettre en veille toutes les commandes pendant 15 secondes

```powershell
Start-Sleep -s 15
```

Cette commande met en veille toutes les commandes dans la session pendant 15 secondes.

### Exemple 2 : mettre en veille toutes les commandes

```powershell
Start-Sleep -m 500
```

Cette commande met en veille toutes les commandes dans la session pendant une demi-seconde (500 millisecondes).

## PARAMETERS

### -Millisecondes

Spécifie la durée pendant laquelle la ressource reste en veille en millisecondes.
Le paramètre peut être abrégé en **m** .

```yaml
Type: System.Int32
Parameter Sets: Milliseconds
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Secondes

Spécifie la durée pendant laquelle la ressource reste en veille en secondes.
Vous pouvez omettre le nom de paramètre ( **secondes** ), ou vous pouvez l’abréger en tant que **s** .

```yaml
Type: System.Int32
Parameter Sets: Seconds
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.Int32

Vous pouvez diriger le nombre de secondes jusqu’à `Start-Sleep` .

## SORTIES

### Aucun

Cette applet de commande ne retourne aucune sortie.

## REMARQUES

- Vous pouvez également faire référence à `Start-Sleep` par son alias intégré, `sleep` . Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).
- `Ctrl+C` s’arrête sur `Start-Sleep` .
  - `Ctrl+C` ne s’arrête pas `[Threading.Thread]::Sleep` . Pour plus d’informations, consultez [méthode Thread. Sleep](/dotnet/api/system.threading.thread.sleep).

## LIENS CONNEXES
