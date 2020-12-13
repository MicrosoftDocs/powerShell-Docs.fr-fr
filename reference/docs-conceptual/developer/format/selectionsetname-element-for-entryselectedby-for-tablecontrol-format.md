---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)
description: SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)
ms.openlocfilehash: a5a395f718d0e1a2d7f33d120ce4fd2ff787cc34
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651783"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)

Spécifie un ensemble de types .NET utilisés par cette entrée de la vue table. Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry élément (format) EntrySelectedBy élément (format) SelectionSetName élément pour EntrySelectedBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Définit les types .NET qui utilisent cette entrée ou la condition qui doit exister pour que cette entrée soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du jeu de sélection.

## <a name="remarks"></a>Notes

Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues. Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets. Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux d’objets pour une vue](./defining-selection-sets.md).

Si vous spécifiez un jeu de sélection pour une entrée, vous ne pouvez pas spécifier un nom de type. Pour plus d’informations sur la spécification d’un type .NET, consultez [élément TypeName pour EntrySelectedBy pour TableRowEntry (format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).

## <a name="see-also"></a>Voir aussi

[Élément EntrySelectedBy (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Définition de jeux d’objets pour une vue](./defining-selection-sets.md)

[Création d’une vue de table](./creating-a-table-view.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
