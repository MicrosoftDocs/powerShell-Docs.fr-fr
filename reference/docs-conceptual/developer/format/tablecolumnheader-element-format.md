---
title: Élément TableColumnHeader (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361848"
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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TableColumnHeader`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément label pour TableColumnHeader pour table ((format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Définit l’étiquette qui s’affiche en haut de la colonne. Si aucune étiquette n’est spécifiée, le nom de la propriété dont la valeur est affichée dans les lignes est utilisé.|
|[Width, élément de TableColumnHeader pour table ((format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|Élément requis.<br /><br /> Spécifie la largeur (en caractères) de la colonne.|
|[Élément Alignment pour TableColumnHeader pour table ((format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le mode d’affichage de l’étiquette de la colonne. Si aucun alignement n’est spécifié, l’étiquette est alignée sur la gauche.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableHeaders (format)](./tableheaders-element-format.md)|Définit les colonnes d’une vue de table.|

## <a name="remarks"></a>Remarks

Spécifiez un en-tête pour chaque colonne de la table. Les colonnes sont affichées dans l’ordre dans lequel les éléments de `TableColumnHeader` sont définis.

Une table doit avoir le même nombre d’éléments `TableColumnHeader` que les éléments `TableRowEntry`. L’en-tête de colonne définit le mode d’affichage du texte en haut de la table. Les entrées de ligne définissent les données qui sont affichées dans les lignes de la table.

Pour plus d’informations sur les composants d’une vue de table, consultez [vue table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre deux éléments `TableColumnHeader`. Le premier élément définit une colonne dont l’étiquette est « colonne 1 », a une largeur de 16 caractères et dont l’étiquette est alignée à gauche. Le deuxième élément définit une colonne dont l’étiquette est « colonne 2 », a une largeur de 10 caractères et dont l’étiquette est centrée dans la colonne.

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

[Élément Alignment pour TableColumnHeader pour table ((format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Création d’une vue de table](./creating-a-table-view.md)

[Élément label pour TableColumnHeader pour table ((format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Élément TableHeaders pour table ((format)](./tableheaders-element-format.md)

[Largeur de TableColumnHeader pour l’élément table ((format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
