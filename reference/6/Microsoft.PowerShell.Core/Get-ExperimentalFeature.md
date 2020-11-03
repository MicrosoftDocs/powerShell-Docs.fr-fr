---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 03/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: 993cc47f9c95fc39d717bb3b76b3de01f16ad47e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204902"
---
# Get-ExperimentalFeature

## SYNOPSIS
Obtient des fonctionnalités expérimentales.

## SYNTAX

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## Description

L' `Get-ExperimentalFeature` applet de commande retourne toutes les fonctionnalités expérimentales découvertes par PowerShell.
Les fonctionnalités expérimentales peuvent provenir de modules ou du moteur PowerShell. Les fonctionnalités expérimentales permettent aux utilisateurs de tester en toute sécurité de nouvelles fonctionnalités et de fournir des commentaires (généralement via GitHub) avant que la conception ne soit considérée comme terminée et que toute modification puisse devenir une modification avec rupture.

## EXEMPLES

### Exemple 1

Obtient la liste des fonctionnalités expérimentales actuellement inscrites et leur état actuel.

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## PARAMETERS

### -Name

Nom ou noms de fonctionnalités expérimentales spécifiques à retourner.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String[]

Nom ou noms des fonctionnalités expérimentales à retourner.

## SORTIES

### ExperimentalFeature

Retourne des instances qui correspondent aux noms demandés ou à toutes les fonctionnalités expérimentales si aucun nom n’est spécifié.

## REMARQUES

## LIENS CONNEXES

[Disable-ExperimentalFeature](Disable-ExperimentalFeature.md)

[Enable-ExperimentalFeature](Enable-ExperimentalFeature.md)
