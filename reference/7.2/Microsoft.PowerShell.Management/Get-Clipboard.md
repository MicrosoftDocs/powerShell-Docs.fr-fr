---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: b0a9e5d1707e0d2f46c25991ddceff27d1b85287
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596338"
---
# Get-Clipboard

## SYNOPSIS
Obtient le contenu du presse-papiers.

## SYNTAXE

```
Get-Clipboard [-Raw] [<CommonParameters>]
```

## Description

L' `Get-Clipboard` applet de commande obtient le contenu du presse-papiers sous forme de texte. Plusieurs lignes de texte sont retournées sous la forme d’un tableau de chaînes similaire à `Get-Content` .

> [!NOTE]
> Sur Linux, cette applet de commande requiert que l' `xclip` utilitaire se trouve dans le chemin d’accès. Cette applet de commande n’est pas prise en charge sur macOS.

## EXEMPLES

### Exemple 1 : obtenir le contenu du presse-papiers et l’afficher sur la ligne de commande

Dans cet exemple, nous avons copié le texte « Hello » dans le presse-papiers.

```powershell
Get-Clipboard
```

```Output
hello
```

## PARAMETERS

### -RAW

Obtient la totalité du contenu du presse-papiers. Le texte multiligne est retourné sous la forme d’une chaîne multiligne unique plutôt que d’un tableau de chaînes.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

## SORTIES

### System.String

## REMARQUES

## LIENS CONNEXES

[Set-Clipboard](Set-Clipboard.md)
