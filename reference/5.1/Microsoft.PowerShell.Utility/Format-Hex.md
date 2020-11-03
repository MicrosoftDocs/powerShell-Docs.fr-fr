---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 514a66ebee3827de998622a738c75d4f8e0c7279
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203301"
---
# Format-Hex

## SYNOPSIS

Affiche un fichier ou une autre entrée au format hexadécimal.

## SYNTAX

### Chemin d’accès (par défaut)

```
Format-Hex [-Path] <string[]> [<CommonParameters>]
```

### LiteralPath

```
Format-Hex -LiteralPath <string[]> [<CommonParameters>]
```

### ByInputObject

```
Format-Hex -InputObject <Object> [-Encoding <string>] [-Raw] [<CommonParameters>]
```

## Description

L' `Format-Hex` applet de commande affiche un fichier ou une autre entrée sous forme de valeurs hexadécimales. Pour déterminer le décalage d’un caractère à partir de la sortie, ajoutez le nombre situé à l’extrême gauche de la ligne au nombre situé en haut de la colonne pour ce caractère.

L' `Format-Hex` applet de commande peut vous aider à déterminer le type de fichier d’un fichier endommagé ou d’un fichier qui n’a peut-être pas une extension de nom de fichier. Vous pouvez exécuter cette applet de commande, puis lire la sortie hexadécimale pour obtenir des informations sur le fichier.

Lors de l’utilisation `Format-Hex` de sur un fichier, l’applet de commande ignore les caractères de saut de ligne et retourne tout le contenu d’un fichier dans une chaîne avec les caractères de saut de ligne conservés.

## EXEMPLES

### Exemple 1 : obtenir la représentation hexadécimale d’une chaîne

Cette commande retourne les valeurs hexadécimales d’une chaîne.

```powershell
'Hello World' | Format-Hex
```

```Output
           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   48 65 6C 6C 6F 20 57 6F 72 6C 64                 Hello World
```

La chaîne **Hello World** est envoyée à l’applet de commande via le pipeline `Format-Hex` . La sortie hexadécimale de `Format-Hex` indique les valeurs de chaque caractère de la chaîne.

### Exemple 2 : Rechercher un type de fichier à partir d’une sortie hexadécimale

Cet exemple utilise la sortie hexadécimale pour déterminer le type de fichier. L’applet de commande affiche le chemin d’accès complet du fichier et les valeurs hexadécimales.

Pour tester la commande suivante, effectuez une copie d’un fichier PDF existant sur votre ordinateur local et renommez le fichier copié en **file. T7f** .

```powershell
Format-Hex -Path .\File.t7f
```

```Output
           Path: C:\Test\File.t7f

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   25 50 44 46 2D 31 2E 35 0D 0A 25 B5 B5 B5 B5 0D  %PDF-1.5..%????.
00000010   0A 31 20 30 20 6F 62 6A 0D 0A 3C 3C 2F 54 79 70  .1 0 obj..<</Typ
00000020   65 2F 43 61 74 61 6C 6F 67 2F 50 61 67 65 73 20  e/Catalog/Pages
```

L' `Format-Hex` applet de commande utilise le paramètre **path** pour spécifier un nom de fichier dans le répertoire actif, `File.t7f` . L’extension de fichier `.t7f` est rare, mais la sortie hexadécimale `%PDF` indique qu’il s’agit d’un fichier PDF.

### Exemple 3 : afficher une sortie hexadécimale brute

Par défaut, `Format-Hex` opte pour la sortie compacte des types de données numériques : les séquences codées sur un octet ou sur deux octets sont utilisées si la valeur est suffisamment petite. Le paramètre **RAW** désactive ce comportement.

```
PS> 1,2,3,1000 | Format-Hex

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 02 03 E8 03                                   ...è.


PS> 1,2,3,1000 | Format-Hex -Raw

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 00 00 00 02 00 00 00 03 00 00 00 E8 03 00 00  ............è...
```

Notez la différence de sortie. Le paramètre **RAW** affiche les nombres sous la forme de valeurs de 4 octets, true pour leurs types **Int32** .

## PARAMETERS

### -Encoding

Spécifie l’encodage de la sortie. Cela s’applique uniquement à l' `[string]` entrée. Le paramètre n’a aucun effet sur les types numériques. La valeur par défaut est `ASCII`.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- `Ascii` Utilise le jeu de caractères ASCII (7 bits).
- `BigEndianUnicode` Utilise UTF-16 avec l’ordre des octets de poids fort (Big-endian).
- `Unicode` Utilise UTF-16 avec l’ordre de primauté des octets de poids faible (Little-endian).
- `UTF7` Utilise UTF-7.
- `UTF8` Utilise UTF-8.
- `UTF32` Utilise UTF-32 avec l’ordre de primauté des octets de poids faible (Little-endian).

Les caractères non-ASCII dans l’entrée sont générés en tant que caractères littéraux, `?` ce qui entraîne une perte d’informations.

```yaml
Type: System.String
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: ASCII
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Utilisé pour l’entrée de pipeline. L’entrée de pipeline prend en charge uniquement certains types scalaires et `[system.io.fileinfo]` instances pour le canalisation à partir de `Get-ChildItem` .

Les types scalaires pris en charge sont les suivants :

- `[string]`
- `[byte]`
- `[int]`, `[int32]`
- `[long]`, `[int64]`

```yaml
Type: System.Object
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le chemin d’accès complet à un fichier. La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.
Ce paramètre n’accepte pas les caractères génériques. Pour spécifier plusieurs chemins d’accès aux fichiers, séparez les chemins d’accès par une virgule. Si le paramètre **LiteralPath** contient des caractères d’échappement, mettez-le entre des guillemets simples. PowerShell n’interprète pas les caractères d’une chaîne entre guillemets simples comme des séquences d’échappement. Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d’accès aux fichiers. Utilisez un point ( `.` ) pour spécifier l’emplacement actuel. Le caractère générique ( `*` ) est accepté et peut être utilisé pour spécifier tous les éléments d’un emplacement. Si le paramètre **path** contient des caractères d’échappement, mettez-le entre des guillemets simples. Pour spécifier plusieurs chemins d’accès aux fichiers, séparez les chemins d’accès par une virgule.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -RAW

Par défaut, `Format-Hex` opte pour la sortie compacte des types de données numériques : les séquences codées sur un octet ou sur deux octets sont utilisées si la valeur est suffisamment petite. Le paramètre **RAW** désactive ce comportement.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByInputObject
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

### System.String

Vous pouvez diriger une chaîne vers cette applet de commande.

## SORTIES

### Microsoft. PowerShell. Commands. ByteCollection

Cette applet de commande retourne un **ByteCollection** . Cet objet représente une collection d’octets. Il comprend des méthodes qui convertissent la collection d’octets en une chaîne mise en forme comme chaque ligne de sortie retournée par `Format-Hex` . Si vous spécifiez le **chemin d’accès** ou le paramètre **LiteralPath** , l’objet contient également le chemin d’accès du fichier qui contient chaque octet.

## REMARQUES

La colonne la plus à droite de la sortie tente de restituer les octets sous forme de caractères :

En règle générale, chaque octet est interprété comme un point de code Unicode, ce qui signifie que :

- Les caractères ASCII imprimables sont toujours restitués correctement
- Les caractères UTF-8 codés sur plusieurs octets ne s’affichent pas correctement
- Les caractères UTF-16 s’affichent correctement uniquement si leur octet de poids fort se produit `NUL` .

## LIENS CONNEXES

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[Format-Custom](Format-Custom.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)
