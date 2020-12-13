---
ms.date: 09/13/2016
ms.topic: reference
title: TableColumnItems, élément pour TableRowEntry pour TableControl (Format)
description: TableColumnItems, élément pour TableRowEntry pour TableControl (Format)
ms.openlocfilehash: 4d600a366d2be1c453f05b301bdf575351dd51c1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667757"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>TableColumnItems, élément pour TableRowEntry pour TableControl (Format)

Définit les propriétés ou les scripts dont les valeurs sont affichées dans une ligne.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableRowEntries pour table ((format) élément TableRowEntry pour TableRowEntries pour table ((format) TableColumnItems élément pour TableControlEntry (format)

## <a name="syntax"></a>Syntaxe

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableColumnItems` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[TableColumnItem, élément pour TableColumnItems pour TableControl (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Élément requis.<br /><br /> Définit la propriété ou le script dont la valeur est affichée dans une colonne de la ligne.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TableRowEntry, élément pour TableRowEntries pour TableControl (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Définit les données affichées dans une ligne de la table.|

## <a name="remarks"></a>Notes

Un `TableColumnItem` élément est requis pour chaque colonne de la ligne. La première entrée est affichée dans la première colonne, la deuxième entrée de la deuxième colonne, et ainsi de suite.

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `TableColumnItems` élément qui définit trois propriétés de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de table](./creating-a-table-view.md)

[Élément TableColumnItem (format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Élément TableRowEntry (format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
