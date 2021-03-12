---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: cd023cb91dd7ae15b2b10954920d133089b7d05c
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103196266"
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

## LIENS CONNEXES

[Disable-ExperimentalFeature](Disable-ExperimentalFeature.md)

[Enable-ExperimentalFeature](Enable-ExperimentalFeature.md)

