---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: 50ad2d48faee88c196942b13141d3ad57c51fdeb
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201322"
---
# Disable-PSTrace

## SYNOPSIS
Désactive les journaux du fournisseur d’événements Microsoft Windows PowerShell.

## SYNTAX

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## Description

Cette applet de commande désactive les journaux des événements opérationnels et analytiques du fournisseur d’événements Microsoft-Windows-PowerShell.

Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.

## EXEMPLES

### Exemple 1 : désactiver le journal des événements d’analyse pour PowerShell

L’exemple suivant désactive uniquement le journal des événements d’analyse du fournisseur Microsoft-Windows-PowerShell.

```powershell
Disable-PSTrace -AnalyticOnly
```

## PARAMETERS

### -AnalyticOnly

Lorsque ce paramètre est utilisé, l’applet de commande désactive le journal des événements d’analyse du fournisseur Microsoft Windows PowerShell. Le journal des événements opérationnels n’est pas modifié.

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

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

## SORTIES

### Aucun

## REMARQUES

Cette applet de commande utilise les `Get-LogProperties` applets de commande et `Set-LogProperties` .

Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.

## LIENS CONNEXES

[Get-LogProperties](Get-LogProperties.md)

[Set-LogProperties](Set-LogProperties.md)

[Enable-PSTrace](Enable-PSTrace.md)
