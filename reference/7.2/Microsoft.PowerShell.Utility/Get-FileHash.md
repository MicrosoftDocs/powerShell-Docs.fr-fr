---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FileHash
ms.openlocfilehash: 0b31409d1da56979887e606b76ddf20532b188c1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596732"
---
# Get-FileHash

## SYNOPSIS
Calcule la valeur de hachage pour un fichier en utilisant un algorithme de hachage spécifié.

## SYNTAXE

### Chemin d’accès (par défaut)

```
Get-FileHash [-Path] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### LiteralPath

```
Get-FileHash [-LiteralPath] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### StreamParameterSet

```
Get-FileHash [-InputStream] <Stream> [[-Algorithm] <String>] [<CommonParameters>]
```

## Description

L' `Get-FileHash` applet de commande calcule la valeur de hachage d’un fichier à l’aide d’un algorithme de hachage spécifié.
Une valeur de hachage est une valeur unique qui correspond au contenu du fichier. Au lieu d'identifier le contenu d'un fichier par son nom, son extension ou toute autre désignation, un hachage assigne une valeur unique au contenu d'un fichier. Les extensions et les noms de fichiers peuvent être modifiés sans changer le contenu du fichier ni la valeur de hachage. De même, le contenu du fichier peut être modifié sans modification du nom ou de l’extension. Toutefois, la modification d'un seul caractère dans le contenu d'un fichier change la valeur de hachage du fichier.

L'objectif des valeurs de hachage est de fournir un moyen sécurisé par chiffrement de vérifier que le contenu d'un fichier n'a pas été modifié. Bien que certains algorithmes de hachage, y compris MD5 et SHA1, ne soient plus considérés comme sécurisés contre les attaques, l’objectif d’un algorithme de hachage sécurisé est de rendre impossible la modification du contenu d’un fichier, soit par accident, soit par tentative malveillante ou non autorisée et en conservant la même valeur de hachage. Vous pouvez également utiliser des valeurs de hachage pour déterminer si deux fichiers différents ont exactement le même contenu. Si les valeurs de hachage de deux fichiers sont identiques, le contenu des fichiers est aussi identique.

Par défaut, l' `Get-FileHash` applet de commande utilise l’algorithme SHA256, bien qu’un algorithme de hachage pris en charge par le système d’exploitation cible puisse être utilisé.

## EXEMPLES

### Exemple 1 : calculer la valeur de hachage pour un fichier

Cet exemple utilise l' `Get-FileHash` applet de commande pour calculer la valeur de hachage du `/etc/apt/sources.list` fichier. L’algorithme de hachage utilisé est la valeur par défaut, **SHA256**. La sortie est dirigée vers l' `Format-List` applet de commande pour mettre en forme la sortie sous forme de liste.

```powershell
Get-FileHash /etc/apt/sources.list | Format-List
```

```Output
Algorithm : SHA256
Hash      : 3CBCFDDEC145E3382D592266BE193E5BE53443138EE6AB6CA09FF20DF609E268
Path      : /etc/apt/sources.list
```

### Exemple 2 : calculer la valeur de hachage pour un fichier ISO

Cet exemple utilise l' `Get-FileHash` applet de commande et l’algorithme **SHA384** pour calculer la valeur de hachage pour un fichier ISO qu’un administrateur a téléchargé à partir d’Internet. La sortie est dirigée vers l' `Format-List` applet de commande pour mettre en forme la sortie sous forme de liste.

```powershell
Get-FileHash C:\Users\user1\Downloads\Contoso8_1_ENT.iso -Algorithm SHA384 | Format-List
```

```Output
Algorithm : SHA384
Hash      : 20AB1C2EE19FC96A7C66E33917D191A24E3CE9DAC99DB7C786ACCE31E559144FEAFC695C58E508E2EBBC9D3C96F21FA3
Path      : C:\Users\user1\Downloads\Contoso8_1_ENT.iso
```

### Exemple 3 : calculer la valeur de hachage d’un flux

Pour cet exemple, nous obtenons l’utilisation de **System .net. WebClient** pour télécharger un package à partir de la [page de version PowerShell](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4). La page de mise en version documente également le hachage SHA256 de chaque fichier de package. Nous pouvons comparer la valeur de hachage publiée avec celle que nous calculons avec `Get-FileHash` .

```powershell
$wc = [System.Net.WebClient]::new()
$pkgurl = 'https://github.com/PowerShell/PowerShell/releases/download/v6.2.4/powershell_6.2.4-1.debian.9_amd64.deb'
$publishedHash = '8E28E54D601F0751922DE24632C1E716B4684876255CF82304A9B19E89A9CCAC'
$FileHash = Get-FileHash -InputStream ($wc.OpenRead($pkgurl))
$FileHash.Hash -eq $publishedHash
```

```Output
True
```

### Exemple 4 : calculer le hachage d’une chaîne

PowerShell ne fournit pas de cmdlet pour calculer le hachage d’une chaîne. Toutefois, vous pouvez écrire une chaîne dans un flux et utiliser le paramètre **InputStream** de `Get-FileHash` pour obtenir la valeur de hachage.

```powershell
$stringAsStream = [System.IO.MemoryStream]::new()
$writer = [System.IO.StreamWriter]::new($stringAsStream)
$writer.write("Hello world")
$writer.Flush()
$stringAsStream.Position = 0
Get-FileHash -InputStream $stringAsStream | Select-Object Hash
```

```Output
Hash
----
64EC88CA00B268E5BA1A35678A1B5316D212F4F366B2477232534A8AECA37F3C
```

## PARAMETERS

### -Algorithme

Spécifie la fonction de hachage de chiffrement à utiliser pour calculer la valeur de hachage du contenu du fichier ou du flux spécifié. Une fonction de hachage de chiffrement a la propriété qu’il est impossible de trouver deux fichiers différents avec la même valeur de hachage. Les fonctions de hachage sont couramment utilisées avec des signatures numériques et pour l'intégrité des données. Les valeurs valides pour ce paramètre sont :

- SHA1
- SHA256
- SHA384
- SHA512
- MD5

Si aucune valeur n'est spécifiée, ou que le paramètre est omis, la valeur par défaut est SHA256.

Pour des raisons de sécurité, MD5 et SHA1, qui ne sont plus considérées comme sécurisées, ne doivent être utilisées que pour la validation de modifications simples et non pour générer des valeurs de hachage pour des fichiers qui nécessitent une protection contre les attaques ou la falsification.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: SHA1, SHA256, SHA384, SHA512, MD5

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputStream

Spécifie le flux d’entrée.

```yaml
Type: System.IO.Stream
Parameter Sets: StreamParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le chemin d'accès à un fichier. Contrairement au paramètre **Path**, la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n'est interprété en tant que caractère générique. Si le chemin d'accès inclut des caractères d'échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell de ne pas interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d’accès à un ou plusieurs fichiers sous la forme d’un tableau. Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne vers l' `Get-FileHash` applet de commande qui contient un chemin d’accès à un ou plusieurs fichiers.

## SORTIES

### Microsoft. PowerShell. Utility. FileHash

`Get-FileHash` retourne un objet qui représente le chemin d’accès au fichier spécifié, la valeur du hachage calculé et l’algorithme utilisé pour calculer le hachage.

## REMARQUES

## LIENS CONNEXES

[Format-List](Format-List.md)

