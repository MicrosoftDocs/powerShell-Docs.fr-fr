---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/get-logproperties?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LogProperties
ms.openlocfilehash: 447d8a07c6e5d6ba4f47685819907937c75711db
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193986"
---
# Get-LogProperties

## SYNOPSIS
Récupère les propriétés d’un journal des événements Windows.

## SYNTAX

```
Get-LogProperties [-Name] <string> [<CommonParameters>]
```

## Description

Cette applet de commande obtient les paramètres de configuration d’un journal des événements Windows. Cette applet de commande est utilisée par les `Enable-PSTrace` applets de commande et `Disable-PSTrace` .

## EXEMPLES

### Exemple 1 : récupérer les paramètres de configuration du journal des événements Windows PowerShell

```powershell
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : False
AutoBackup : False
MaxLogSize : 15728640
```

## PARAMETERS

### -Name

Nom du fournisseur d’événements.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.Object

## SORTIES

### Microsoft. PowerShell. Diagnostics. LogDetails

Le module **PSDiagnostics** ajoute la classe **LogDetails** à l' `Microsoft.PowerShell.Diagnostics` espace de noms.

## REMARQUES

## LIENS CONNEXES

[Set-LogProperties](Set-LogProperties.md)

[Enable-PSTrace](Enable-PSTrace.md)

[Disable-PSTrace](Disable-PSTrace.md)
