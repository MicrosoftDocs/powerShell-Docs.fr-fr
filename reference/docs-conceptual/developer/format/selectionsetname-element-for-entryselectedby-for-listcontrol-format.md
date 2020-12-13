---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)
description: SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)
ms.openlocfilehash: 413a77f7ba06fe952e574061e58d0b5d80c5b3c4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651828"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a>SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)

Spécifie un ensemble d’objets .NET pour l’entrée de liste. Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionSetName pour EntrySelectedBy pour ListEntry (format)

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
|[Élément EntrySelectedBy pour ListEntry (format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Définit les types .NET qui utilisent cette entrée de liste ou la condition qui doit exister pour que cette entrée soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du jeu de sélection.

## <a name="remarks"></a>Notes

Au moins un nom de type, un jeu de sélection ou une condition de sélection doivent être définis pour chaque entrée de liste.

Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues. Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets. Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux d’objets pour une vue](./defining-selection-sets.md).

Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier un jeu de sélection pour une entrée d’un affichage de liste.

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de liste](./creating-a-list-view.md)

[Élément EntrySelectedBy pour ListEntry (format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
