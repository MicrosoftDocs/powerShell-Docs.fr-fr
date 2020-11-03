---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
Locale: en-US
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/get-logproperties?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LogProperties
ms.openlocfilehash: 08638749b7a5bb57bee804fccf9de17f50fd6736
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201638"
---
# Get-LogProperties

## SYNOPSIS
Récupère les propriétés d’un journal des événements Windows.

## SYNTAX

```
Get-LogProperties [-Name] <Object> [<CommonParameters>]
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

### System.String

## SORTIES

### Microsoft. PowerShell. Diagnostics. LogDetails

Le module **PSDiagnostics** ajoute la classe **LogDetails** à l' `Microsoft.PowerShell.Diagnostics` espace de noms.

## REMARQUES

## LIENS CONNEXES

[Set-LogProperties](Set-LogProperties.md)

[Enable-PSTrace](Enable-PSTrace.md)

[Disable-PSTrace](Disable-PSTrace.md)
