---
title: Élément TableHeaders (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856875"
---
# <a name="tableheaders-element-format"></a>TableHeaders, élément (Format)

Définit les en-têtes pour les colonnes d’une table.

Élément ViewDefinitions (Format) vue élément (Format) table (Format) TableHeaders élément pour la table (Format)

## <a name="syntax"></a>Syntaxe

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de la `TableHeaders` élément. Il doit être un élément enfant pour chaque propriété de l’objet qui doit être affichée. Les informations d’en-tête de colonne s’affiche dans l’ordre que les éléments enfants sont spécifiées.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément TableColumnHeader (Format)](./tablecolumnheader-element-format.md)|Élément facultatif.<br /><br /> Définit l’étiquette, la largeur et l’alignement des données pour une colonne d’une vue de table.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de table (Format)](./tablecontrol-element-format.md)|Définit un format de table pour une vue.|

## <a name="remarks"></a>Remarques

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).

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

[Création d’une vue de Table](./creating-a-table-view.md)

[Élément TableColumnHeader (Format)](./tablecolumnheader-element-format.md)

[Élément de table (Format)](./tablecontrol-element-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
