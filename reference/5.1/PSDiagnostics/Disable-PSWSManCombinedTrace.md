---
external help file: PSDiagnostics-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pswsmancombinedtrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSWSManCombinedTrace
ms.openlocfilehash: 4a98941de072b9b57b89a25bc180c0ee391d8b63
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203066"
---
# Disable-PSWSManCombinedTrace

## SYNOPSIS
Arrêtez la session de journalisation démarrée par Enable-PSWSManCombinedTrace.

## SYNTAX

```
Disable-PSWSManCombinedTrace [<CommonParameters>]
```

## Description

Cette applet de commande arrête la session de journalisation démarrée par `Enable-PSWSManCombinedTrace` .

Cette applet de commande utilise l’applet de commande `Stop-Trace` .

Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.

## EXEMPLES

### Exemple 1 : désactiver la session de journalisation combinée

```powershell
Disable-PSWSManCombinedTrace
```

## PARAMETERS

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

## SORTIES

### System.Object

## REMARQUES

## LIENS CONNEXES

[Suivi d’événements](/windows/desktop/ETW/event-tracing-portal)

[Stop-Trace](stop-trace.md)

[Enable-PSWSManCombinedTrace](Enable-PSWSManCombinedTrace.md)
