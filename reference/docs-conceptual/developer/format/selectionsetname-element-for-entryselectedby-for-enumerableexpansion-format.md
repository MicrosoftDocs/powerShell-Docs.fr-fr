---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)
description: SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)
ms.openlocfilehash: 074f810f5a3cbad61ee8be69408967758f0591df
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651884"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)

Spécifie l’ensemble des types .NET développés par cette définition.

Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) élément EntrySelectedBy pour EnumerableExpansion (format) élément SelectionSetName pour EntrySelectedBy pour EnumerableExpansion (format)

## <a name="syntax"></a>Syntaxe

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[EntrySelectedBy, élément pour EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Définit les objets de collection .NET développés par cette définition.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du jeu de sélection.

## <a name="remarks"></a>Notes

Chaque définition doit spécifier un ou plusieurs noms de types, un jeu de sélection ou une condition de sélection.

Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues. Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets. Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux d’objets pour une vue](./defining-selection-sets.md).

## <a name="see-also"></a>Voir aussi

[Définition de jeux de sélections](./defining-selection-sets.md)

[EntrySelectedBy, élément pour EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
