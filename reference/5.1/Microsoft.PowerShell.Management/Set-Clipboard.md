---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: c1cf126e41a5e918afffbc41d30f957e650efdf5
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564500"
---
# Set-Clipboard

## SYNOPSIS
Définit l’entrée actuelle du presse-papiers Windows.

## SYNTAXE

### Chaîne (valeur par défaut)

```
Set-Clipboard [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Valeur

```
Set-Clipboard [-Value] <String[]> [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Path

```
Set-Clipboard [-Append] -Path <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Set-Clipboard [-Append] -LiteralPath <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Set-Clipboard` applet de commande définit l’entrée actuelle du presse-papiers Windows.

## EXEMPLES

### Exemple 1 : copier du texte dans le presse-papiers

```powershell
Set-Clipboard -Value "This is a test string"
```

### Exemple 2 : copier le contenu d’un répertoire dans le presse-papiers

Cet exemple copie le contenu du dossier spécifié dans le presse-papiers.

```powershell
Set-Clipboard -Path "C:\Staging\"
```

### Exemple 3 : copier le contenu d’un fichier dans le presse-papiers

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

### -AsHtml

Indique que l’applet de commande affiche le contenu au format HTML dans le presse-papiers.

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

### -LiteralPath

Spécifie le chemin d’accès à l’élément copié dans le presse-papiers. Contrairement au paramètre **Path**, la valeur de **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à Windows PowerShell qu’aucun caractère ne doit être interprété en tant que séquence d’échappement.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d’accès à l’élément copié dans le presse-papiers. Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Value

Spécifie, sous forme de tableau de chaînes, le contenu à copier dans le presse-papiers.

```yaml
Type: System.String[]
Parameter Sets: Value
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String[]

## SORTIES

## REMARQUES

Dans de rares cas `Set-Clipboard` , lorsque vous utilisez avec un nombre élevé de valeurs en succession rapide, comme dans une boucle, vous pouvez obtenir de manière sporadique une valeur vide à partir du presse-papiers. Cela peut être résolu à l’aide `Start-Sleep -Milliseconds 1` de dans la boucle.

## LIENS CONNEXES

[Get-Clipboard](Get-Clipboard.md)
