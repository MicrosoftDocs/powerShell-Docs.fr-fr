---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/new-winevent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WinEvent
ms.openlocfilehash: 202d1792769dcdcda7a156621bfc50c89a1a92ac
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202261"
---
# New-WinEvent

## SYNOPSIS

Crée un événement Windows pour le fournisseur d'événements spécifié.

## SYNTAX

```
New-WinEvent [-ProviderName] <String> [-Id] <Int32> [-Version <Byte>] [[-Payload] <Object[]>]
 [<CommonParameters>]
```

## Description

L'applet de commande **New-WinEvent** crée un événement du Suivi des événements pour Windows (ETW) pour un fournisseur d'événements.
Vous pouvez utiliser cette applet de commande pour ajouter des événements aux canaux ETW à partir de Windows PowerShell.

## EXEMPLES

### Exemple 1

```powershell
PS C:\> New-WinEvent -ProviderName Microsoft-Windows-PowerShell -Id 45090 -Payload @("Workflow", "Running")
```

Cette commande utilise l'applet de commande **New-WinEvent** pour créer un événement 45090 pour le fournisseur Microsoft-Windows-PowerShell.

## PARAMETERS

### -Id

Spécifie un ID d'événement enregistré via un manifeste d'instrumentation.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Charge utile

Spécifie le message de l'événement. Quand l'événement est écrit dans un journal d'événements, la charge utile est stockée dans la propriété **Message** de l'objet d'événement.

Quand la charge utile spécifiée ne correspond pas à la charge utile de la définition de l'événement, Windows PowerShell génère un avertissement, mais n'empêche pas la commande d'aboutir.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

Spécifie le fournisseur d'événements qui écrit l'événement dans un journal d'événements, comme « Microsoft Windows PowerShell ». Un fournisseur d'événements ETW est une entité logique qui écrit des événements dans des sessions ETW.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Version

Spécifie le numéro de version de l'événement. Tapez le numéro d'événement. Windows PowerShell convertit le nombre en type Byte requis.

Ce paramètre vous permet de spécifier un événement quand des versions différentes du même événement sont définies.

```yaml
Type: System.Byte
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

Cette applet de commande n'accepte pas d'entrée provenant du pipeline.

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

* Une fois que le fournisseur a écrit le même dans un journal des événements, vous pouvez utiliser l’applet de commande Get-WinEvent pour récupérer l’événement à partir du journal des événements.

## LIENS CONNEXES

[Get-WinEvent](Get-WinEvent.md)
