---
external help file: PSDiagnostics-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: 0999c59ab2e27b066dc6afa0b21cce029a9419e1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202137"
---
# Enable-PSWSManCombinedTrace

## SYNOPSIS
Démarrez une session de journalisation avec les fournisseurs WSMan et PowerShell activés.

## SYNTAX

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## Description

Cette applet de commande démarre une session de journalisation avec les fournisseurs PowerShell suivants activés :

- Microsoft-Windows-PowerShell
- Microsoft-Windows-WinRM

La session est nommée « PSTrace ».

Cette applet de commande utilise l’applet de commande `Start-Trace` .

Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.

## EXEMPLES

### Exemple 1 : démarrer une session de journalisation combinée

```powershell
Enable-PSWSManCombinedTrace
```

## PARAMETERS

### -DoNotOverwriteExistingTrace

Par défaut, les événements sont écrits dans « $pshome \Traces\PSTrace.etl ». Lorsque ce paramètre est utilisé, l’applet de commande crée un nom de fichier unique : « $pshome \Traces\ PSTrace_ {GUID}. etl »

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

## LIENS CONNEXES

[Suivi d’événements](/windows/desktop/ETW/event-tracing-portal)

[Start-Trace](start-trace.md)

[Disable-PSWSManCombinedTrace](Disable-PSWSManCombinedTrace.md)

