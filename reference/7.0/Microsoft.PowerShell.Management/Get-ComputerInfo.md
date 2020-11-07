---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: e9170a8023977f485a99e5e7fc59fb2280a8081e
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347582"
---
# Get-ComputerInfo

## SYNOPSIS
Obtient un objet consolidé des propriétés système et du système d’exploitation.

## SYNTAXE

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## DESCRIPTION

L' `Get-ComputerInfo` applet de commande obtient un objet consolidé des propriétés système et du système d’exploitation.
Cette applet de commande a été introduite dans Windows PowerShell 5,1.

## EXEMPLES

### Exemple 1 : récupération de toutes les propriétés de l’ordinateur

```powershell
Get-ComputerInfo
```

Cette commande obtient toutes les propriétés système et système d’exploitation de l’ordinateur.

### Exemple 2 : récupération de toutes les propriétés du système d’exploitation de l’ordinateur

```powershell
Get-ComputerInfo -Property "os*"
```

Cette commande obtient toutes les propriétés du système d’exploitation de l’ordinateur.

## PARAMÈTRES

### -Propriété

Spécifie, sous forme de tableau de chaînes, les propriétés de l’ordinateur que cette applet de commande affiche.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String[]

## SORTIES

### Microsoft. PowerShell. Management. ComputerInfo

## REMARQUES

Cette applet de commande est disponible uniquement sur les plateformes Windows.

## LIENS CONNEXES
