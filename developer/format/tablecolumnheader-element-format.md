---
title: Élément TableColumnHeader (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063807"
---
# <a name="tablecolumnheader-element-format"></a>TableColumnHeader, élément (Format)

Définit l’étiquette, la largeur de la colonne et l’alignement de l’étiquette pour une colonne de la table.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableHeaders élément de configuration pour élément TableColumnHeader de table (Format) pour TableHeaders pour la table (Format)

## <a name="syntax"></a>Syntaxe

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `TableColumnHeader` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément Label pour TableColumnHeader pour la table (Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Définit l’étiquette qui s’affiche en haut de la colonne. Si aucune étiquette n’est spécifiée, le nom de la propriété dont la valeur est affichée dans les lignes est utilisé.|
|[Élément de la largeur pour TableColumnHeader pour la table (Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|Élément requis.<br /><br /> Spécifie la largeur (en caractères) de la colonne.|
|[Élément d’alignement pour TableColumnHeader pour la table (Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie la façon dont l’étiquette de la colonne est affichée. Si aucun alignement n’est spécifié, l’étiquette est alignée sur la gauche.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableHeaders (Format)](./tableheaders-element-format.md)|Définit les colonnes d’une vue de table.|

## <a name="remarks"></a>Remarques

Spécifier un en-tête pour chaque colonne de la table. Les colonnes sont affichées dans l’ordre dans lequel le `TableColumnHeader` éléments sont définis.

Une table doit avoir le même nombre de `TableColumnHeader` éléments en tant que `TableRowEntry` éléments. L’en-tête de colonne définit la façon dont le texte en haut de la table est affiché. Les entrées de ligne définissent quelles données sont affichées dans les lignes de la table.

Pour plus d’informations sur les composants d’une vue de table, consultez [Table vue](./creating-a-table-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre deux `TableColumnHeader` éléments. Le premier élément définit une colonne dont le nom est « Colonne 1 », a une largeur de 16 caractères et dont l’étiquette est alignée sur la gauche. Le deuxième élément définit une colonne dont le nom est « Colonne 2 », a une largeur de 10 caractères et dont l’étiquette est centrée dans la colonne.

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

[Élément d’alignement pour TableColumnHeader pour la table (Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Création d’une vue de Table](./creating-a-table-view.md)

[Élément Label pour TableColumnHeader pour la table (Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Élément TableHeaders pour la table (Format)](./tableheaders-element-format.md)

[Largeur pour TableColumnHeader pour la table, élément (Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
