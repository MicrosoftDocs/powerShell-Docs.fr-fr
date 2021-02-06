---
description: L' `enum` instruction est utilisée pour déclarer une énumération. Une énumération est un type distinct qui se compose d’un ensemble d’étiquettes nommées appelé liste d’énumérateurs.
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_enum?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: À propos de l’énumération
ms.openlocfilehash: 5572a717bbf9b546a30b227b3baf215196c4145d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597542"
---
# <a name="about-enum"></a><span data-ttu-id="ffdff-104">À propos de enum</span><span class="sxs-lookup"><span data-stu-id="ffdff-104">About Enum</span></span>

## <a name="short-description"></a><span data-ttu-id="ffdff-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="ffdff-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ffdff-106">L' `enum` instruction est utilisée pour déclarer une énumération.</span><span class="sxs-lookup"><span data-stu-id="ffdff-106">The `enum` statement is used to declare an enumeration.</span></span> <span data-ttu-id="ffdff-107">Une énumération est un type distinct qui se compose d’un ensemble d’étiquettes nommées appelé liste d’énumérateurs.</span><span class="sxs-lookup"><span data-stu-id="ffdff-107">An enumeration is a distinct type that consists of a set of named labels called the enumerator list.</span></span>

## <a name="long-description"></a><span data-ttu-id="ffdff-108">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="ffdff-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="ffdff-109">L' `enum` instruction vous permet de créer un jeu d’étiquettes fortement typé.</span><span class="sxs-lookup"><span data-stu-id="ffdff-109">The `enum` statement allows you to create a strongly typed set of labels.</span></span> <span data-ttu-id="ffdff-110">Cette énumération peut être utilisée dans le code sans avoir à analyser ou vérifier les fautes d’orthographe.</span><span class="sxs-lookup"><span data-stu-id="ffdff-110">That enumeration can be used in the code without having to parse or check for spelling errors.</span></span>

<span data-ttu-id="ffdff-111">Les énumérations sont représentées en interne en tant qu’entiers avec une valeur de départ de zéro.</span><span class="sxs-lookup"><span data-stu-id="ffdff-111">Enumerations are internally represented as integers with a starting value of zero.</span></span> <span data-ttu-id="ffdff-112">La valeur zéro est assignée à la première étiquette de la liste.</span><span class="sxs-lookup"><span data-stu-id="ffdff-112">The first label in the list is assigned the value zero.</span></span> <span data-ttu-id="ffdff-113">Les étiquettes restantes sont assignées avec des nombres consécutifs.</span><span class="sxs-lookup"><span data-stu-id="ffdff-113">The remaining labels are assigned with consecutive numbers.</span></span>

<span data-ttu-id="ffdff-114">Dans la définition, les étiquettes peuvent recevoir toute valeur entière.</span><span class="sxs-lookup"><span data-stu-id="ffdff-114">In the definition, labels can be given any integer value.</span></span> <span data-ttu-id="ffdff-115">Les étiquettes sans valeur assignée prennent la valeur entière suivante.</span><span class="sxs-lookup"><span data-stu-id="ffdff-115">Labels with no value assigned take the next integer value.</span></span>

## <a name="syntax-basic"></a><span data-ttu-id="ffdff-116">Syntaxe (de base)</span><span class="sxs-lookup"><span data-stu-id="ffdff-116">Syntax (basic)</span></span>

```syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

## <a name="usage-example"></a><span data-ttu-id="ffdff-117">Exemple d’utilisation</span><span class="sxs-lookup"><span data-stu-id="ffdff-117">Usage example</span></span>

<span data-ttu-id="ffdff-118">L’exemple suivant illustre une énumération d’objets qui peuvent être affichés en tant que fichiers multimédias.</span><span class="sxs-lookup"><span data-stu-id="ffdff-118">The following example shows an enumeration of objects that can be seen as media files.</span></span> <span data-ttu-id="ffdff-119">La définition assigne des valeurs explicites aux valeurs sous-jacentes de `music` , `picture` , `video` .</span><span class="sxs-lookup"><span data-stu-id="ffdff-119">The definition assigns explicit values to the underlying values of `music`, `picture`, `video`.</span></span> <span data-ttu-id="ffdff-120">Les étiquettes qui suivent immédiatement une assignation explicite obtiennent la valeur entière suivante.</span><span class="sxs-lookup"><span data-stu-id="ffdff-120">Labels immediately following an explicit assignment get the next integer value.</span></span> <span data-ttu-id="ffdff-121">Vous pouvez créer des synonymes en assignant la même valeur à une autre étiquette. consultez les valeurs construites pour : `ogg` , `oga` , `mogg` , ou `jpg` , `jpeg` ou `mpg` `mpeg` .</span><span class="sxs-lookup"><span data-stu-id="ffdff-121">Synonyms can be created by assigning the same value to another label; see the constructed values for: `ogg`, `oga`, `mogg`, or `jpg`, `jpeg`, or `mpg`, `mpeg`.</span></span>

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

<span data-ttu-id="ffdff-122">La `GetEnumNames()` méthode retourne la liste des étiquettes pour l’énumération.</span><span class="sxs-lookup"><span data-stu-id="ffdff-122">The `GetEnumNames()` method returns the list of the labels for the enumeration.</span></span>

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

<span data-ttu-id="ffdff-123">La `GetEnumValues()` méthode retourne la liste des valeurs de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="ffdff-123">The `GetEnumValues()` method returns the list of the values for the enumeration.</span></span>

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

<span data-ttu-id="ffdff-124">**Remarque**: GetEnumNames () et GetEnumValues () semblent retourner les mêmes résultats.</span><span class="sxs-lookup"><span data-stu-id="ffdff-124">**Note**: GetEnumNames() and GetEnumValues() seem to return the same results.</span></span>
<span data-ttu-id="ffdff-125">Toutefois, en interne, PowerShell change les valeurs en étiquettes.</span><span class="sxs-lookup"><span data-stu-id="ffdff-125">However, internally, PowerShell is changing values into labels.</span></span> <span data-ttu-id="ffdff-126">Lisez attentivement la liste et vous remarquerez que `oga` et `mogg` sont mentionnés sous les résultats « obtenir les noms », mais pas sous la sortie similaire « obtenir les valeurs » pour `jpg` , `jpeg` et `mpg` `mpeg` .</span><span class="sxs-lookup"><span data-stu-id="ffdff-126">Read the list carefully and you'll notice that `oga` and `mogg` are mentioned under the 'Get Names' results, but not under the 'Get Values' similar output for `jpg`, `jpeg`, and `mpg`, `mpeg`.</span></span>

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

## <a name="enumerations-as-flags"></a><span data-ttu-id="ffdff-127">Énumérations en tant qu’indicateurs</span><span class="sxs-lookup"><span data-stu-id="ffdff-127">Enumerations as flags</span></span>

<span data-ttu-id="ffdff-128">Les énumérations peuvent être définies comme une collection d’indicateurs binaires.</span><span class="sxs-lookup"><span data-stu-id="ffdff-128">Enumerations can be defined as a collection of bit flags.</span></span>
<span data-ttu-id="ffdff-129">Où, à un point donné, l’énumération représente un ou plusieurs de ces indicateurs activés.</span><span class="sxs-lookup"><span data-stu-id="ffdff-129">Where, at any given point the enumeration represents one or more of those flags turned on.</span></span>

<span data-ttu-id="ffdff-130">Pour que les énumérations en tant qu’indicateurs fonctionnent correctement, chaque étiquette doit avoir une puissance de deux valeurs.</span><span class="sxs-lookup"><span data-stu-id="ffdff-130">For enumerations as flags to work properly, each label should have a power of two value.</span></span>

## <a name="syntax-flags"></a><span data-ttu-id="ffdff-131">Syntaxe (indicateurs)</span><span class="sxs-lookup"><span data-stu-id="ffdff-131">Syntax (flags)</span></span>

```syntax
[Flags()] enum <enum-name> {
    <label 0> [= 1]
    <label 1> [= 2]
    <label 2> [= 4]
    <label 3> [= 8]
    ...
}
```

## <a name="flags-usage-example"></a><span data-ttu-id="ffdff-132">Exemple d’utilisation des indicateurs</span><span class="sxs-lookup"><span data-stu-id="ffdff-132">Flags usage example</span></span>

<span data-ttu-id="ffdff-133">Dans l’exemple suivant, l’énumération *FileAttributes* est créée.</span><span class="sxs-lookup"><span data-stu-id="ffdff-133">In the following example the *FileAttributes* enumeration is created.</span></span>

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

<span data-ttu-id="ffdff-134">Pour vérifier qu’un spécifique est défini, vous pouvez utiliser l’opérateur de comparaison binaire `-band` .</span><span class="sxs-lookup"><span data-stu-id="ffdff-134">To test that a specific is set, you can use the binary comparison operator `-band`.</span></span> <span data-ttu-id="ffdff-135">Dans cet exemple, nous testons l' **appareil** et les attributs d' **Archive** dans la valeur de `$file2` .</span><span class="sxs-lookup"><span data-stu-id="ffdff-135">In this example, we test for the **Device** and the **Archive** attributes in the value of `$file2`.</span></span>

```
PS > ($file2 -band [FileAttributes]::Device) -eq [FileAttributes]::Device
True

PS > ($file2 -band [FileAttributes]::Archive) -eq [FileAttributes]::Archive
False
```

