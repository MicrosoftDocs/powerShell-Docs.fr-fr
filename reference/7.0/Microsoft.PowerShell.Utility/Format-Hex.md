---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 6cb02f1c6f2583ce4146356fac3553e99a54c7c2
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201802"
---
# Format-Hex

## SYNOPSIS

Affiche un fichier ou une autre entrée au format hexadécimal.

## SYNTAX

### Chemin d’accès (par défaut)

```
Format-Hex [-Path] <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### LiteralPath

```
Format-Hex -LiteralPath <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### ByInputObject
```
Format-Hex -InputObject <PSObject> [-Encoding <Encoding>] [-Count <Int64>] [-Offset <Int64>] [-Raw]
 [<CommonParameters>]
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
   Label: String (System.String) <2944BEC3>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 48 65 6C 6C 6F 20 57 6F 72 6C 64                Hello World
```

La chaîne **Hello World** est envoyée à l’applet de commande via le pipeline `Format-Hex` . La sortie hexadécimale de `Format-Hex` indique les valeurs de chaque caractère de la chaîne.

### Exemple 2 : Rechercher un type de fichier à partir d’une sortie hexadécimale

Cet exemple utilise la sortie hexadécimale pour déterminer le type de fichier. L’applet de commande affiche le chemin d’accès complet du fichier et les valeurs hexadécimales.

Pour tester la commande suivante, effectuez une copie d’un fichier PDF existant sur votre ordinateur local et renommez le fichier copié `File.t7f` .

```powershell
Format-Hex -Path .\File.t7f -Count 48
```

```Output
   Label: C:\Test\File.t7f

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 25 50 44 46 2D 31 2E 35 0D 0A 25 B5 B5 B5 B5 0D %PDF-1.5..%????.
0000000000000010 0A 31 20 30 20 6F 62 6A 0D 0A 3C 3C 2F 54 79 70 .1 0 obj..<</Typ
0000000000000020 65 2F 43 61 74 61 6C 6F 67 2F 50 61 67 65 73 20 e/Catalog/Pages
```

L' `Format-Hex` applet de commande utilise le paramètre **path** pour spécifier un nom de fichier dans le répertoire actif, `File.t7f` . L’extension de fichier `.t7f` est rare, mais la sortie hexadécimale `%PDF` indique qu’il s’agit d’un fichier PDF. Dans cet exemple, le paramètre **Count** est utilisé pour limiter la sortie aux 48 premiers octets du fichier.

### Exemple 3 : mettre en forme un tableau de types de données différents

Cet exemple utilise un tableau de types de données différents pour mettre `Format-Hex` en évidence comment les gère dans le pipeline.

Il passera chaque objet via le pipeline et le processus individuellement. Toutefois, s’il s’agit de données numériques et que l’objet adjacent est également numérique, il les regroupe dans un bloc de sortie unique.

```powershell
'Hello world!', 1, 1138, 'foo', 'bar', 0xdeadbeef, 1gb, 0b1101011100 , $true, $false | Format-Hex
```

```Output
   Label: String (System.String) <24F1F0A3>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 48 65 6C 6C 6F 20 77 6F 72 6C 64 21             Hello world!

   Label: Int32 (System.Int32) <2EB933C5>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 72 04 00 00                         �   r�

   Label: String (System.String) <4078B66C>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 66 6F 6F                                        foo

   Label: String (System.String) <51E4A317>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 62 61 72                                        bar

   Label: Int32 (System.Int32) <5ADF167B>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 EF BE AD DE 00 00 00 40 5C 03 00 00             ï¾­Þ   @\�

   Label: Boolean (System.Boolean) <7D8C4C1D>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 00 00 00 00                         �
```

## PARAMETERS

### -Encoding

Spécifie l’encodage des chaînes d’entrée. Cela s’applique uniquement à l' `[string]` entrée. Le paramètre n’a aucun effet sur les types numériques. La valeur de sortie est toujours `utf8NoBOM` .

Les valeurs acceptables pour ce paramètre sont les suivantes :

- `ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).
- `bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).
- `oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.
- `unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).
- `utf7`: Encode au format UTF-7.
- `utf8`: Encode au format UTF-8.
- `utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)
- `utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)
- `utf32`: Encode au format UTF-32.

À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ). Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).

```yaml
Type: System.Text.Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Utilisé pour l’entrée de pipeline. L’entrée de pipeline prend en charge uniquement certains types scalaires et `[system.io.fileinfo]` instances pour le canalisation à partir de `Get-ChildItem` .

Les types scalaires pris en charge sont les suivants :

- `[string]`, `[char]`
- `[byte]`, `[sbyte]`
- `[int16]`, `[uint16]`, `[short]`, `[ushort]`
- `[int]`, `[uint]`, `[int32]`, `[uint32]`,
- `[long]`, `[ulong]`, `[int64]`, `[uint64]`
- `[single]`, `[float]`, `[double]`
- `[boolean]`

Avant PowerShell 6,2, `Format-Hex` gérerait une entrée de pipeline avec plusieurs types d’entrée en regroupant tous les objets similaires. À présent, il traite chaque objet individuel lorsqu’il passe par le pipeline et ne regroupe pas les objets, sauf si les objets like sont adjacents.

```yaml
Type: System.Management.Automation.PSObject
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
Aliases: PSPath, LP

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

Ce paramètre n’effectue plus aucune action. Elle est conservée pour la compatibilité de script.

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

### -Offset

Cela représente le nombre d’octets à ignorer pour faire partie de la sortie hex.

Ce paramètre a été introduit dans PowerShell 6,2.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -Nombre

Cela représente le nombre d’octets à inclure dans la sortie hex.

Ce paramètre a été introduit dans PowerShell 6,2.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Int64.MaxValue
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

Cette applet de commande retourne un **ByteCollection** . Cet objet représente une collection d’octets. Il comprend des méthodes qui convertissent la collection d’octets en une chaîne mise en forme comme chaque ligne de sortie retournée par `Format-Hex` . La sortie indique également qu’il s’agit d’un type d’octets en cours de traitement. Si vous spécifiez le **chemin d’accès** ou le paramètre **LiteralPath** , l’objet contient le chemin d’accès du fichier qui contient chaque octet. Si vous transmettez une chaîne, une valeur booléenne, un entier, etc., elle est étiquetée de manière appropriée.

## REMARQUES

La colonne la plus à droite de la sortie tente de restituer les octets sous forme de caractères ASCII :

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
