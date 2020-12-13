---
ms.date: 09/13/2016
ms.topic: reference
title: TableColumnHeader, élément (Format)
description: TableColumnHeader, élément (Format)
ms.openlocfilehash: 30368512875b7c5c4cf3c686f3d09540dea1bd26
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651522"
---
# <a name="tablecolumnheader-element-format"></a>TableColumnHeader, élément (Format)

Définit l’étiquette, la largeur de la colonne et l’alignement de l’étiquette pour une colonne de la table.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableHeaders pour table ((format) élément TableColumnHeader pour TableHeaders pour table ((format)

## <a name="syntax"></a>Syntaxe

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableColumnHeader` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément label pour TableColumnHeader pour table ((format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Définit l’étiquette qui s’affiche en haut de la colonne. Si aucune étiquette n’est spécifiée, le nom de la propriété dont la valeur est affichée dans les lignes est utilisé.|
|[Width, élément pour TableColumnHeader pour TableControl (Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|Élément requis.<br /><br /> Spécifie la largeur (en caractères) de la colonne.|
|[Alignment, élément pour TableColumnHeader pour TableControl (Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le mode d’affichage de l’étiquette de la colonne. Si aucun alignement n’est spécifié, l’étiquette est alignée sur la gauche.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TableHeaders, élément (Format)](./tableheaders-element-format.md)|Définit les colonnes d’une vue de table.|

## <a name="remarks"></a>Notes

Spécifiez un en-tête pour chaque colonne de la table. Les colonnes sont affichées dans l’ordre dans lequel les `TableColumnHeader` éléments sont définis.

Une table doit avoir le même nombre d’éléments `TableColumnHeader` que les `TableRowEntry` éléments. L’en-tête de colonne définit le mode d’affichage du texte en haut de la table. Les entrées de ligne définissent les données qui sont affichées dans les lignes de la table.

Pour plus d’informations sur les composants d’une vue de table, consultez [vue table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre deux `TableColumnHeader` éléments. Le premier élément définit une colonne dont l’étiquette est « colonne 1 », a une largeur de 16 caractères et dont l’étiquette est alignée à gauche. Le deuxième élément définit une colonne dont l’étiquette est « colonne 2 », a une largeur de 10 caractères et dont l’étiquette est centrée dans la colonne.

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

[Alignment, élément pour TableColumnHeader pour TableControl (Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Création d’une vue de table](./creating-a-table-view.md)

[Label, élément pour TableColumnHeader pour TableControl (Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Élément TableHeaders pour table ((format)](./tableheaders-element-format.md)

[Largeur de TableColumnHeader pour l’élément table ((format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
