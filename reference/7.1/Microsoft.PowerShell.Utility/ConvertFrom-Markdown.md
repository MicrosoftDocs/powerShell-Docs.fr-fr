---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: PowerShell, applet de commande, démarque
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-markdown?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Markdown
ms.openlocfilehash: 9f070819491b87b02868dffdfbe25bf5d72ecab8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204765"
---
# ConvertFrom-Markdown

## SYNOPSIS
Convertit le contenu d’une chaîne ou d’un fichier en objet **MarkdownInfo** .

## SYNTAX

### PathParamSet (par défaut)

```
ConvertFrom-Markdown [-Path] <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### LiteralParamSet

```
ConvertFrom-Markdown -LiteralPath <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### InputObjParamSet

```
ConvertFrom-Markdown -InputObject <PSObject> [-AsVT100EncodedString] [<CommonParameters>]
```

## Description

Cette applet de commande convertit le contenu spécifié en **MarkdownInfo** . Quand un chemin d’accès de fichier est spécifié pour le paramètre **path** , le contenu du fichier est converti. L’objet de sortie a trois propriétés :

- La propriété **Token** a l’arborescence de syntaxe abstraite (AST) de l’objet converti
- La propriété **HTML** contient la conversion HTML de l’entrée spécifiée
- La propriété **VT100EncodedString** contient la chaîne convertie avec des séquences d’échappement ANSI (VT100) si le paramètre **AsVT100EncodedString** a été spécifié

Cette applet de commande a été introduite dans PowerShell 6,1.

## EXEMPLES

### Exemple 1 : convertir un fichier contenant le contenu de la démarque en HTML

```powershell
ConvertFrom-Markdown -Path .\README.md
```

L’objet **MarkdownInfo** est retourné. La propriété **tokens** contient l’AST du contenu converti du `README.md` fichier. La propriété **HTML** contient le contenu HTML converti du `README.md` fichier.

### Exemple 2 : convertir un fichier contenant le contenu de la démarque en une chaîne encodée en VT100

```powershell
ConvertFrom-Markdown -Path .\README.md -AsVT100EncodedString
```

L’objet **MarkdownInfo** est retourné. La propriété **tokens** contient l’AST du contenu converti du `README.md` fichier. La valeur de la propriété **VT100EncodedString** de la chaîne encodée en VT100 du fichier est convertie `README.md` .

### Exemple 3 : convertir un objet d’entrée contenant le contenu de la démarque en une chaîne encodée en VT100

```powershell
Get-Item .\README.md | ConvertFrom-Markdown -AsVT100EncodedString
```

L’objet **MarkdownInfo** est retourné. L’objet **FileInfo** de `Get-Item` est converti en une chaîne encodée en VT100. La propriété **tokens** contient l’AST du contenu converti du `README.md` fichier. La valeur de la propriété **VT100EncodedString** de la chaîne encodée en VT100 du fichier est convertie `README.md` .

### Exemple 4 : convertir une chaîne contenant le contenu de la démarque en une chaîne encodée en VT100

```powershell
"**Bold text**" | ConvertFrom-Markdown -AsVT100EncodedString
```

L’objet **MarkdownInfo** est retourné. La chaîne spécifiée `**Bold text**` est convertie en une chaîne encodée en VT100 et disponible dans la propriété **VT100EncodedString** .

## PARAMETERS

### -AsVT100EncodedString

Spécifie si la sortie doit être encodée sous la forme d’une chaîne avec des codes d’échappement VT100.

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

### -InputObject

Spécifie l'objet à convertir. Lorsqu’un objet de type **System. String** est spécifié, la chaîne est convertie. Lorsqu’un objet de type **System. IO. FileInfo** est spécifié, le contenu du fichier spécifié par l’objet est converti. Les objets de tout autre type provoquent une erreur.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObjParamSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie un chemin d’accès au fichier à convertir.

```yaml
Type: System.String[]
Parameter Sets: LiteralParamSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie un chemin d’accès au fichier à convertir.

```yaml
Type: System.String[]
Parameter Sets: PathParamSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

## SORTIES

### Microsoft. PowerShell. MarkdownRender. MarkdownInfo

## REMARQUES

## LIENS CONNEXES

[Analyseur de démarque](https://github.com/lunet-io/markdig)

[Code d’échappement ANSI](https://wikipedia.org/wiki/ANSI_escape_code)

