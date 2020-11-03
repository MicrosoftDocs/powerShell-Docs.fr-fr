---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Set-MarkdownOption?view=powershell-7&WT.mc_id=ps-gethelp
ms.date: 01/30/2020
schema: 2.0.0
ms.openlocfilehash: e18cc8e0f5e547c4418f59b6f55109052b69c220
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "93205265"
---
# Set-MarkdownOption

## SYNOPSIS
Définit les couleurs et les styles utilisés pour le rendu du contenu de la démarque dans la console.

## SYNTAX

### IndividualSetting (par défaut)

```
Set-MarkdownOption [-Header1Color <String>] [-Header2Color <String>] [-Header3Color <String>]
 [-Header4Color <String>] [-Header5Color <String>] [-Header6Color <String>] [-Code <String>]
 [-ImageAltTextForegroundColor <String>] [-LinkForegroundColor <String>]
 [-ItalicsForegroundColor <String>] [-BoldForegroundColor <String>] [-PassThru]
 [<CommonParameters>]
```

### Thème

```
Set-MarkdownOption [-PassThru] -Theme <String> [<CommonParameters>]
```

### InputObject

```
Set-MarkdownOption [-PassThru] [-InputObject] <PSObject> [<CommonParameters>]
```

## Description

Définit les couleurs et les styles utilisés pour le rendu du contenu de la démarque dans la console. Ces styles sont définis à l’aide de codes d’échappement ANSI qui modifient la couleur et le style du texte de la démarque en cours de rendu.

Pour plus d’informations sur la démarque, consultez le site Web [CommonMark](https://commonmark.org/) .

> [!NOTE]
> Les valeurs de chaîne utilisées dans les paramètres sont les caractères qui suivent le caractère d' **échappement** ( `[char]0x1B` ) pour la séquence d’échappement ANSI. N’incluez pas le caractère d' **échappement** dans la chaîne. Pour plus d’informations sur le fonctionnement des codes d’échappement ANSI, consultez [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).

## EXEMPLES

### Exemple 1-basculer vers le thème clair

Cet exemple sélectionne le thème **clair** et affiche la nouvelle configuration à l’aide du paramètre **PassThru** .

```powershell
Set-MarkdownOption -Theme Light -PassThru
```

```Output
Header1         : [7m
Header2         : [4;33m
Header3         : [4;34m
Header4         : [4;35m
Header5         : [4;36m
Header6         : [4;30m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

### Exemple 2 : personnaliser les paramètres de couleur et de style

Cet exemple modifie le code d’échappement pour les en-têtes de démarque. La configuration par défaut des en-têtes les restitue sous forme de texte souligné de différentes couleurs. Cette modification supprime le style de soulignement.

```powershell
$mdOptions = Get-MarkdownOption
$mdOptions.Header2 = '[93m'
$mdOptions.Header3 = '[94m'
$mdOptions.Header4 = '[95m'
$mdOptions.Header5 = '[96m'
$mdOptions.Header6 = '[97m'
Set-MarkdownOption -InputObject $mdOptions -PassThru
```

```Output
Header1         : [7m
Header2         : [93m
Header3         : [94m
Header4         : [95m
Header5         : [96m
Header6         : [97m
Code            : [48;2;155;155;155;38;2;30;30;31m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

## PARAMETERS

### -BoldForegroundColor

Définit la couleur de premier plan pour le rendu du texte de démarque gras.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Code

Définit la couleur de rendu des blocs de code et des étendues dans le texte de la démarque.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header1Color

Définit la couleur de rendu des blocs Header1 dans le texte de la démarque.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header2Color

Définit la couleur de rendu des blocs Header2 dans le texte de la démarque.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header3Color

Définit la couleur de rendu des blocs Header3 dans le texte de la démarque.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header4Color

Définit la couleur de rendu des blocs Header4 dans le texte de la démarque.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header5Color

Définit la couleur de rendu des blocs Header5 dans le texte de la démarque.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header6Color

Définit la couleur de rendu des blocs Header6 dans le texte de la démarque.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ImageAltTextForegroundColor

Définit la couleur de premier plan pour le rendu du texte de remplacement d’un élément image dans le texte de démarque.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Objet **PSMarkdownOptionInfo** contenant la configuration à définir.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ItalicsForegroundColor

Définit la couleur de premier plan pour le rendu de l’italique dans le texte de la démarque.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LinkForegroundColor

Définit la couleur de premier plan pour le rendu des liens hypertexte dans le texte de la démarque.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Fait en sorte que l’applet de commande génère un objet **PSMarkdownOptionInfo** contenant la nouvelle configuration.

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

### -Thème

Sélectionne un thème contenant des paramètres de couleur prédéfinis. Les valeurs possibles sont **Dark** et **Light** .

```yaml
Type: System.String
Parameter Sets: Theme
Aliases:
Accepted values: Dark, Light

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

## SORTIES

### Microsoft. PowerShell. MarkdownRender. PSMarkdownOptionInfo

## REMARQUES

Les valeurs de chaîne utilisées pour définir la couleur et le style doivent correspondre à l’expression régulière `^\[*[0-9;]*?m{1}` .

## LIENS CONNEXES

[Get-MarkdownOption](Get-MarkdownOption.md)

[ConvertFrom-Markdown](ConvertFrom-Markdown.md)

[Show-Markdown](Show-Markdown.md)

[ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)

[CommonMark](https://commonmark.org/)
