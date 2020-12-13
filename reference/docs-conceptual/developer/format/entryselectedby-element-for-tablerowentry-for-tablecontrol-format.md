---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy, élément pour TableRowEntry pour TableControl (Format)
description: EntrySelectedBy, élément pour TableRowEntry pour TableControl (Format)
ms.openlocfilehash: 1b7fc60b6fa9864b66e9edfebb3e4a86e287f3f8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645891"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>EntrySelectedBy, élément pour TableRowEntry pour TableControl (Format)

Définit les types .NET qui utilisent cette définition de la vue table ou la condition qui doit exister pour que cette définition soit utilisée.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry, élément (format) EntrySelectedBy, élément (format)

## <a name="syntax"></a>Syntaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[SelectionCondition, élément pour EntrySelectedBy pour TableControl (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour que cette définition de vue de table soit utilisée.|
|[SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition de vue de table.|
|[TypeName, élément pour EntrySelectedBy pour TableControl (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition de vue de table.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableRowEntry pour table ((format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Définit les données affichées dans une ligne de la table.|

## <a name="remarks"></a>Notes

Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition d’affichage de table. Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.

Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou un script spécifique prend la valeur `true` . Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `TableRowEntry` élément qui est utilisé pour afficher les propriétés de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de table](./creating-a-table-view.md)

[SelectionCondition, élément pour EntrySelectedBy pour TableControl (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[Élément TableRowEntry pour table ((format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[TypeName, élément pour EntrySelectedBy pour TableControl (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
