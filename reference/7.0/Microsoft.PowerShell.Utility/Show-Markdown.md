---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-markdown?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Markdown
ms.openlocfilehash: bb73853c8432bcd4fcc900ee1d6fc620ed883ebb
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201366"
---
# Show-Markdown

## SYNOPSIS
Affiche un fichier de démarque ou une chaîne dans la console d’une manière conviviale à l’aide de séquences d’échappement VT100 ou dans un navigateur à l’aide de HTML.

## SYNTAX

### Chemin d’accès (par défaut)

```
Show-Markdown [-Path] <String[]> [-UseBrowser] [<CommonParameters>]
```

### InputObject

```
Show-Markdown -InputObject <PSObject> [-UseBrowser] [<CommonParameters>]
```

### LiteralPath

```
Show-Markdown -LiteralPath <String[]> [-UseBrowser] [<CommonParameters>]
```

## Description

L' `Show-Markdown` applet de commande est utilisée pour restituer la démarque dans un format lisible par l’utilisateur dans un terminal ou dans un navigateur.

`Show-Markdown` peut retourner une chaîne qui comprend les séquences d’échappement VT100 que le terminal restitue (s’il prend en charge les séquences d’échappement VT100). Il est principalement utilisé pour afficher les fichiers de démarque dans un terminal. Vous pouvez également récupérer cette chaîne via la `ConvertFrom-Markdown` en spécifiant le paramètre **AsVT100EncodedString** .

`Show-Markdown` a également la possibilité d’ouvrir un navigateur et d’afficher une version rendue de la démarque. Il affiche la démarque en le convertissant en HTML et en ouvrant le fichier HTML dans votre navigateur par défaut.

Vous pouvez modifier le `Show-Markdown` rendu du démarque dans un terminal à l’aide de `Set-MarkdownOption` .

Cette applet de commande a été introduite dans PowerShell 6,1.

## EXEMPLES

### Exemple 1 : exemple simple spécifiant un chemin d’accès

```powershell
Show-Markdown -Path ./README.md
```

### Exemple 2 : exemple simple spécifiant une chaîne

```powershell
@"
# Show-Markdown

## Markdown

You can now interact with Markdown via PowerShell!

*stars*
__underlines__
"@ | Show-Markdown
```

### Exemple 2 : ouverture d’une démarque dans un navigateur

```powershell
Show-Markdown -Path ./README.md -UseBrowser
```

## PARAMETERS

### -InputObject

Chaîne de démarque qui s’affiche dans le terminal. Si vous ne transmettez pas un format pris en charge, `Show-Markdown` génère une erreur.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le chemin d’accès à un fichier de démarque. Contrairement au paramètre Path, la valeur du paramètre LiteralPath est utilisée exactement telle que vous la tapez. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d’accès à un fichier de démarques à rendre.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -UseBrowser

Compile l’entrée de la démarque en HTML et l’ouvre dans votre navigateur par défaut.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

### System.String[]

## SORTIES

### System.String

## REMARQUES

## LIENS CONNEXES

[ConvertFrom-Markdown](ConvertFrom-Markdown.md)
