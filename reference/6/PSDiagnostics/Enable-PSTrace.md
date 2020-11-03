---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: d5008d5105b18b5a3d0423cab4282735e3d382d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202529"
---
# Enable-PSTrace

## SYNOPSIS
Active les journaux du fournisseur d’événements Microsoft Windows PowerShell.

## SYNTAX

```
Enable-PSTrace [-Force] [-AnalyticOnly] [<CommonParameters>]
```

## Description

Cette applet de commande active les journaux des événements opérationnels et analytiques du fournisseur d’événements Microsoft-Windows-PowerShell.

Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.

## EXEMPLES

### Exemple 1 : activer le journal des événements d’analyse pour PowerShell

L’exemple suivant active uniquement le journal des événements d’analyse du fournisseur Microsoft-Windows-PowerShell.

```powershell
Enable-PSTrace -AnalyticOnly
```

## PARAMETERS

### -AnalyticOnly

Lorsque ce paramètre est utilisé, l’applet de commande active le journal des événements d’analyse du fournisseur Microsoft Windows PowerShell. Le journal des événements opérationnels n’est pas modifié.

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

### -Force

Utilisé pour forcer la modification sans demander confirmation.

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
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

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

[Disable-PSTrace](Disable-PSTrace.md)
