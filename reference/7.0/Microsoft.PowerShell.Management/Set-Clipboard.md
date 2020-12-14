---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: efb24b14122ad37043636d999afaa4199eb3097b
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564371"
---
# Set-Clipboard

## SYNOPSIS
Définit le contenu du presse-papiers.

## SYNTAXE

```
Set-Clipboard [-Value] <string[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
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

### Exemple 2 : copier le contenu d’un fichier dans le presse-papiers

Cet exemple canalise le contenu d’un fichier dans le presse-papiers. Dans cet exemple, nous obtenons une clé SSH publique pour pouvoir la coller dans une autre application, par exemple GitHub.

```powershell
Get-Content C:\Users\user1\.ssh\id_ed25519.pub | Set-Clipboard
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
