---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-EventLog
ms.openlocfilehash: e8dbcf1aa4280c0481714a8a9fb24f2e5ef79ffe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203490"
---
# Show-EventLog

## SYNOPSIS
Affiche les journaux des événements de l'ordinateur local ou d'un ordinateur distant dans l'observateur d'événements.

## SYNTAX

```
Show-EventLog [[-ComputerName] <String>] [<CommonParameters>]
```

## Description
L’applet de commande **Show-EventLog** ouvre observateur d’événements sur l’ordinateur local et s’affiche dans tous les journaux des événements classiques sur l’ordinateur local ou sur un ordinateur distant.

Pour ouvrir observateur d’événements sur Windows Vista et les versions ultérieures du système d’exploitation Windows, l’utilisateur actuel doit être membre du groupe Administrateurs sur l’ordinateur local.

Les applets de commande qui contiennent le nom **EventLog** (les applets de commande **EventLog** ) fonctionnent uniquement sur les journaux des événements classiques.
Pour récupérer des événements à partir des journaux qui utilisent la technologie du journal des événements Windows dans Windows Vista et les versions ultérieures du système d’exploitation Windows, utilisez l’applet de commande Get-WinEvent.

## EXEMPLES

### Exemple 1 : afficher les journaux des événements de l’ordinateur local

```
PS C:\> Show-EventLog
```

Cette commande ouvre l'observateur d'événements et y affiche les journaux des événements classiques sur l'ordinateur local.

### Exemple 2 : afficher les journaux des événements pour un ordinateur distant

```
PS C:\> Show-EventLog -ComputerName "Server01"
```

Cette commande ouvre l'observateur d'événements et y affiche les journaux des événements classiques sur l'ordinateur Server01.

## PARAMETERS

### -ComputerName
Spécifie un ordinateur distant.
**Show-EventLog** affiche les journaux des événements de l’ordinateur spécifié dans observateur d’événements sur l’ordinateur local.
La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur distant.

Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.
Vous pouvez utiliser le paramètre *ComputerName* même si votre ordinateur n'est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun
Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Aucun
Cette applet de commande ne génère aucune sortie.

## REMARQUES

* L'invite de commandes de Windows PowerShell retourne des éléments dès que l'observateur d'événements s'ouvre. Vous pouvez travailler dans la session active lorsque l'observateur d'événements est ouvert.

  Comme cette applet de commande requiert une interface utilisateur, elle ne fonctionne pas sur les installations minimales de Windows Server.

*

## LIENS CONNEXES

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Write-EventLog](Write-EventLog.md)
