---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 16b41711e98276fee37d56f77f57e7372daa4cf3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597333"
---
# Stop-Transcript

## SYNOPSIS
Arrête une transcription.

## SYNTAXE

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

### None

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System.String

Cette applet de commande retourne une chaîne qui contient un message d’État et le chemin d’accès au fichier de sortie.

## REMARQUES

* Si une transcription n'a pas été démarrée, la commande échoue.

*

## LIENS CONNEXES

[Start-Transcript](Start-Transcript.md)

