---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 86903ca648ff3ee58ec939143b7881741827f453
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200990"
---
# Stop-Transcript

## SYNOPSIS
Arrête une transcription.

## SYNTAX

```
Stop-Transcript [<CommonParameters>]
```

## Description

L' `Stop-Transcript` applet de commande arrête une transcription qui a été démarrée par l’applet de commande `Start-Transcript` .
Vous pouvez également mettre fin à une session pour arrêter une transcription.

## EXEMPLES

### Exemple 1 : arrêter toutes les transcriptions

```powershell
Stop-Transcript
```

Cette commande arrête toutes les transcriptions.

## PARAMETERS

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System.String

Cette applet de commande retourne une chaîne qui contient un message d’État et le chemin d’accès au fichier de sortie.

## REMARQUES

* Si une transcription n'a pas été démarrée, la commande échoue.

*

## LIENS CONNEXES

[Start-Transcript](Start-Transcript.md)

