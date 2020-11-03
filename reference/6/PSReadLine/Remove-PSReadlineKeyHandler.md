---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/remove-psreadlinekeyhandler?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSReadLineKeyHandler
ms.openlocfilehash: 6a15e829f589fbccf0da3479a22f24cdf3fc81ae
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203737"
---
# Remove-PSReadLineKeyHandler

## SYNOPSIS
Supprime une combinaison de touches.

## SYNTAX

```
Remove-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

## Description

L' `Remove-PSReadLineKeyHandler` applet de commande supprime une combinaison de touches spécifiée.

## EXEMPLES

### Exemple 1 : supprimer une liaison

```powershell
Remove-PSReadLineKeyHandler -Chord Ctrl+B
```

Cette commande supprime la liaison de la combinaison de touches, ou corde `Ctrl+B` . Le `Ctrl+B` segment est créé dans l' `Set-PSReadLineKeyHandler` article.

## PARAMETERS

### -Corde

Spécifie un tableau de clés ou de séquences de clés à supprimer. Une seule liaison est spécifiée à l’aide d’une chaîne unique. Si la liaison est une séquence de clés, séparez les clés par une virgule, comme dans l’exemple suivant :

`Ctrl+x,Ctrl+l`

Ce paramètre accepte un tableau de chaînes. Chaque chaîne est une liaison distincte, et non une séquence de clés pour une seule liaison.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViMode

Spécifiez le mode VI auquel la liaison s’applique. Les valeurs possibles sont : Insert, Command.

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:
Accepted values: Insert, Command

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas rediriger des objets vers cette applet de commande.

## SORTIES

### Aucun

## REMARQUES

## LIENS CONNEXES

[PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[PSReadLineOption](Get-PSReadLineOption.md)

[Set-PSReadLineOption](Set-PSReadLineOption.md)

[Set-PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)
