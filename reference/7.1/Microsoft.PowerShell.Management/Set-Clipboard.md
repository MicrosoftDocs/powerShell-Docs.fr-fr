---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/09/2019
online version: https://go.microsoft.com/fwlink/?linkid=526220
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: 6fbe7b1e5534b1227bcfd73fd58f3602186ef8c5
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239670"
---
# Set-Clipboard

## SYNOPSIS
Définit le contenu du presse-papiers.

## SYNTAX

```
Set-Clipboard -Value <String[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Set-Clipboard` applet de commande définit le contenu du presse-papiers.

> [!NOTE]
> Sur Linux, cette applet de commande requiert que l' `xclip` utilitaire se trouve dans le chemin d’accès.

## EXEMPLES

### Exemple 1 : copier du texte dans le presse-papiers

```powershell
Set-Clipboard -Value "This is a test string"
```

## PARAMETERS

### -Append

Indique que l’applet de commande n’efface pas le presse-papiers et y ajoute du contenu.

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

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

Valeurs de chaîne à ajouter au Presse-papiers.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String[]

## SORTIES

## REMARQUES

Dans de rares cas `Set-Clipboard` , lorsque vous utilisez avec un nombre élevé de valeurs en succession rapide, comme dans une boucle, vous pouvez obtenir de manière sporadique une valeur vide à partir du presse-papiers. Cela peut être résolu à l’aide `Start-Sleep -Milliseconds 1` de dans la boucle.

## LIENS CONNEXES

[Get-Clipboard](Get-Clipboard.md)
