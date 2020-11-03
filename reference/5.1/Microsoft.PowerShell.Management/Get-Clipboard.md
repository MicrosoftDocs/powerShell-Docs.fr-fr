---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: 2885b2624f8334e8699e0baea5fc41b3f025fe2a
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "93206302"
---
# Get-Clipboard

## SYNOPSIS
Obtient l’entrée actuelle du presse-papiers Windows.

## SYNTAX

```
Get-Clipboard [-Format <ClipboardFormat>] [-TextFormatType <TextDataFormat>] [-Raw] [<CommonParameters>]
```

## Description

L' `Get-Clipboard` applet de commande obtient l’entrée du presse-papiers Windows en cours. Plusieurs lignes de texte sont retournées sous la forme d’un tableau de chaînes similaire à `Get-Content` .

## EXEMPLES

### Exemple 1 : obtenir le contenu du presse-papiers et l’afficher sur la ligne de commande

Dans cet exemple, nous avons cliqué avec le bouton droit sur une image dans un navigateur et choisi l’action de **copie** . La commande suivante affiche le lien, sous la forme d’une URL, de l’image stockée dans le presse-papiers.

```powershell
Get-Clipboard
```

```Output
https://en.wikipedia.org/wiki/PowerShell
```

### Exemple 2 : obtenir le contenu du presse-papiers dans un format spécifique

Dans cet exemple, nous avons copié les fichiers dans le presse-papiers de Windows Explorerby en les sélectionnant et en appuyant sur <kbd>Ctrl + C</kbd>. À l’aide de la commande suivante, vous pouvez accéder au contenu du presse-papiers sous la forme d’une liste de fichiers :

```powershell
Get-Clipboard -Format FileDropList
```

```Output
    Directory: C:\Git\PS-Docs\PowerShell-Docs\wmf

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/7/2019   1:11 PM          10010 TOC.yml
-a----       11/18/2016  10:10 AM             53 md.style
-a----         5/6/2019   9:32 AM           4177 overview.md
-a----        6/28/2018   2:28 PM            345 README.md
```

## PARAMETERS

### -Format

Spécifie le type ou le format du presse-papiers. Les valeurs valides pour ce paramètre sont :

- Texte
- FileDropList
- Image
- Audio

```yaml
Type: Microsoft.PowerShell.Commands.ClipboardFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, FileDropList, Image, Audio

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

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

### -TextFormatType

Spécifie le type de format de données texte du presse-papiers. Les valeurs valides pour ce paramètre sont :

- Texte
- UnicodeText
- RTF
- Html
- CommaSeparatedValue

```yaml
Type: System.Windows.Forms.TextDataFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, UnicodeText, Rtf, Html, CommaSeparatedValue

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

### System. String, System. IO. FileInfo, System. IO. Stream, System. Drawing. image

## REMARQUES

## LIENS CONNEXES

[Set-Clipboard](Set-Clipboard.md)
