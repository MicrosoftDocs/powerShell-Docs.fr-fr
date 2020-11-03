---
description: L' `enum` instruction est utilisée pour déclarer une énumération. Une énumération est un type distinct qui se compose d’un ensemble d’étiquettes nommées appelé liste d’énumérateurs.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_enum?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos de l’énumération
ms.openlocfilehash: 1ffb18ab98fbd40b407abfe32c71027315b69621
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207338"
---
# <a name="about-enum"></a>À propos de enum

## <a name="short-description"></a>DESCRIPTION COURTE
L' `enum` instruction est utilisée pour déclarer une énumération. Une énumération est un type distinct qui se compose d’un ensemble d’étiquettes nommées appelé liste d’énumérateurs.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

L' `enum` instruction vous permet de créer un jeu d’étiquettes fortement typé. Cette énumération peut être utilisée dans le code sans avoir à analyser ou vérifier les fautes d’orthographe.

Les énumérations sont représentées en interne en tant qu’entiers avec une valeur de départ de zéro. La valeur zéro est assignée à la première étiquette de la liste. Les étiquettes restantes sont assignées avec des nombres consécutifs.

Dans la définition, les étiquettes peuvent recevoir toute valeur entière. Les étiquettes sans valeur assignée prennent la valeur entière suivante.

## <a name="syntax-basic"></a>Syntaxe (de base)

```syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

## <a name="usage-example"></a>Exemple d’utilisation

L’exemple suivant illustre une énumération d’objets qui peuvent être affichés en tant que fichiers multimédias. La définition assigne des valeurs explicites aux valeurs sous-jacentes de `music` , `picture` , `video` . Les étiquettes qui suivent immédiatement une assignation explicite obtiennent la valeur entière suivante. Vous pouvez créer des synonymes en assignant la même valeur à une autre étiquette. consultez les valeurs construites pour : `ogg` , `oga` , `mogg` , ou `jpg` , `jpeg` ou `mpg` `mpeg` .

```powershell
enum MediaTypes {
    unknown
    music = 10
    mp3
    aac
    ogg = 15
    oga = 15
    mogg = 15
    picture = 20
    jpg
    jpeg = 21
    png
    video = 40
    mpg
    mpeg = 41
    avi
    m4v
}
```

La `GetEnumNames()` méthode retourne la liste des étiquettes pour l’énumération.

```powershell
[MediaTypes].GetEnumNames()
unknown
music
mp3
aac
ogg
oga
mogg
picture
jpg
jpeg
png
video
mpg
mpeg
avi
m4v
```

La `GetEnumValues()` méthode retourne la liste des valeurs de l’énumération.

```powershell
[MediaTypes].GetEnumValues()
unknown
music
mp3
aac
oga
oga
oga
picture
jpeg
jpeg
png
video
mpeg
mpeg
avi
m4v
```

**Remarque** : GetEnumNames () et GetEnumValues () semblent retourner les mêmes résultats.
Toutefois, en interne, PowerShell change les valeurs en étiquettes. Lisez attentivement la liste et vous remarquerez que `oga` et `mogg` sont mentionnés sous les résultats « obtenir les noms », mais pas sous la sortie similaire « obtenir les valeurs » pour `jpg` , `jpeg` et `mpg` `mpeg` .

```powershell
[MediaTypes].GetEnumName(15)
oga

[MediaTypes].GetEnumNames() | ForEach-Object {
  "{0,-10} {1}" -f $_,[int]([MediaTypes]::$_)
}
unknown    0
music      10
mp3        11
aac        12
ogg        15
oga        15
mogg       15
picture    20
jpg        21
jpeg       21
png        22
video      40
mpg        41
mpeg       41
avi        42
m4v        43
```

## <a name="enumerations-as-flags"></a>Énumérations en tant qu’indicateurs

Les énumérations peuvent être définies comme une collection d’indicateurs binaires.
Où, à un point donné, l’énumération représente un ou plusieurs de ces indicateurs activés.

Pour que les énumérations en tant qu’indicateurs fonctionnent correctement, chaque étiquette doit avoir une puissance de deux valeurs.

## <a name="syntax-flags"></a>Syntaxe (indicateurs)

```syntax
[Flags()] enum <enum-name> {
    <label 0> [= 1]
    <label 1> [= 2]
    <label 2> [= 4]
    <label 3> [= 8]
    ...
}
```

## <a name="flags-usage-example"></a>Exemple d’utilisation des indicateurs

Dans l’exemple suivant, l’énumération *FileAttributes* est créée.

```powershell
[Flags()] enum FileAttributes {
    Archive = 1
    Compressed = 2
    Device = 4
    Directory = 8
    Encrypted = 16
    Hidden = 32
}

[FileAttributes]$file1 = [FileAttributes]::Archive
[FileAttributes]$file1 +=[FileAttributes]::Compressed
[FileAttributes]$file1 +=  [FileAttributes]::Device
"file1 attributes are: $file1"

[FileAttributes]$file2 = [FileAttributes]28 ## => 16 + 8 + 4
"file2 attributes are: $file2"
```

```output
file1 attributes are: Archive, Compressed, Device
file2 attributes are: Device, Directory, Encrypted
```

Pour vérifier qu’un spécifique est défini, vous pouvez utiliser l’opérateur de comparaison binaire `-band` . Dans cet exemple, nous testons l' **appareil** et les attributs d' **Archive** dans la valeur de `$file2` .

```
PS > ($file2 -band [FileAttributes]::Device) -eq [FileAttributes]::Device
True

PS > ($file2 -band [FileAttributes]::Archive) -eq [FileAttributes]::Archive
False
```

