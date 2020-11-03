---
external help file: PSDiagnostics-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: 5e91477cd840e895c25207bd5355686e0c24d473
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200998"
---
# Disable-WSManTrace

## SYNOPSIS
Arrêtez la session de journalisation WSMan démarrée par Enable-WSManTrace.

## SYNTAX

```
Disable-WSManTrace [<CommonParameters>]
```

## Description
Cette applet de commande arrête la session de journalisation WSMan démarrée par Enable-WSManTrace.

Cette applet de commande utilise l’applet de commande `Stop-Trace` .

Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.

## EXEMPLES

### Exemple 1 : arrêter une trace WSMan

```powershell
Disable-WSManTrace
```

## PARAMETERS

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

## SORTIES

### Aucun

## REMARQUES

## LIENS CONNEXES

[Suivi d’événements](/windows/desktop/ETW/event-tracing-portal)

[Stop-Trace](stop-trace.md)

[Enable-WSManTrace](Enable-WSManTrace.md)
