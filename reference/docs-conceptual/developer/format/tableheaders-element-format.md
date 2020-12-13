---
ms.date: 09/13/2016
ms.topic: reference
title: TableHeaders, élément (Format)
description: TableHeaders, élément (Format)
ms.openlocfilehash: 5ac4dccae746c167ebf95add9f3d18030a2b3a99
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659821"
---
# <a name="tableheaders-element-format"></a>TableHeaders, élément (Format)

Définit les en-têtes pour les colonnes d’une table.

Élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableHeaders pour table ((format)

## <a name="syntax"></a>Syntaxe

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `TableHeaders` élément. Il doit y avoir un élément enfant pour chaque propriété de l’objet qui doit être affiché. Les informations d’en-tête de colonne s’affichent dans l’ordre dans lequel les éléments enfants sont spécifiés.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[TableColumnHeader, élément (Format)](./tablecolumnheader-element-format.md)|Élément facultatif.<br /><br /> Définit l’étiquette, la largeur et l’alignement des données pour une colonne d’une vue de table.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TableControl, élément (Format)](./tablecontrol-element-format.md)|Définit un format de table pour une vue.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

Cet exemple montre un `TableHeaders` élément qui définit deux en-têtes de colonne.

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de table](./creating-a-table-view.md)

[TableColumnHeader, élément (Format)](./tablecolumnheader-element-format.md)

[TableControl, élément (Format)](./tablecontrol-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
