---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: 535cad057db406eaa48259288e34da6da4ed1cbb
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201361"
---
# Start-Sleep

## SYNOPSIS
Interrompt l'activité dans un script ou une session pour la période spécifiée.

## SYNTAX

### Secondes (par défaut)

```
Start-Sleep [-Seconds] <Double> [<CommonParameters>]
```

### Millisecondes

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## Description

L' `Start-Sleep` applet de commande suspend l’activité dans un script ou une session pour la période spécifiée. Vous pouvez l'utiliser pour de nombreuses tâches, comme attendre qu'une opération se termine ou soit suspendue avant de répéter une opération.

## EXEMPLES

### Exemple 1 : mettre en veille toutes les commandes pendant 15 secondes

```powershell
Start-Sleep -s 15
```

### Exemple 2 : mettre en veille toutes les commandes pendant 1,5 secondes

Dans cet exemple, toutes les commandes de la session sont en veille pendant une demi-seconde.

```powershell
Start-Sleep -Seconds 1.5
```

## PARAMETERS

### -Millisecondes

Spécifie la durée pendant laquelle la ressource reste en veille en millisecondes. Le paramètre peut être abrégé en **m** .

```yaml
Type: System.Int32
Parameter Sets: Milliseconds
Aliases: ms

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Secondes

Spécifie la durée pendant laquelle la ressource reste en veille en secondes. Vous pouvez omettre le nom du paramètre ou vous pouvez l’abréger en tant que **s** . À compter de PowerShell 6.2.0, ce paramètre accepte à présent des valeurs fractionnaires.

```yaml
Type: System.Double
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
