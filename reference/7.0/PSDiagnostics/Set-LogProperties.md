---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/set-logproperties?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LogProperties
ms.openlocfilehash: baf737a649e96488aff10959e02b59a0323e3ac4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201273"
---
# Set-LogProperties

## SYNOPSIS
Modifie les propriétés d’un journal des événements Windows.

## SYNTAX

```
Set-LogProperties [-LogDetails] <LogDetails> [-Force] [<CommonParameters>]
```

## Description

Cette applet de commande modifie les paramètres de configuration d’un journal des événements Windows. Cette applet de commande est utilisée par les `Enable-PSTrace` applets de commande et `Disable-PSTrace` .

Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.

## EXEMPLES

### Exemple 1 : modifier le paramètre de rétention du journal des événements Windows PowerShell

```powershell
$logDetails = Get-LogProperties 'Windows PowerShell'
$logDetails.Retention = $True
Set-LogProperties -LogDetails $logDetails
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : True
AutoBackup : False
MaxLogSize : 15728640
```

## PARAMETERS

### -Force

Utilisé pour forcer la modification sans demander confirmation.

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

### -LogDetails

Paramètres de configuration mis à jour à assigner au journal des événements.

```yaml
Type: Microsoft.PowerShell.Diagnostics.LogDetails
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

### Microsoft. PowerShell. Diagnostics. LogDetails

Vous devez transmettre un objet **LogDetails** entièrement configuré à l' `Set-LogProperties` applet de commande.
Par conséquent, pour modifier un paramètre, vous devez utiliser `Get-LogProperties` pour récupérer la configuration actuelle.

## SORTIES

### Aucun

## REMARQUES

Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.

## LIENS CONNEXES

[Get-LogProperties](Get-LogProperties.md)

[Enable-PSTrace](Enable-PSTrace.md)

[Disable-PSTrace](Disable-PSTrace.md)
