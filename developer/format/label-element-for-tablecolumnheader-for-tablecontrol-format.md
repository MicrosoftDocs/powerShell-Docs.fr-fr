---
title: L’étiquette d’élément pour TableColumnHeader pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065748"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Label, élément pour TableColumnHeader pour TableControl (Format)

Définit l’étiquette qui s’affiche en haut d’une colonne. Cet élément est utilisé lors de la définition d’une vue de table.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableHeaders élément de configuration pour élément TableColumnHeader de table (Format) pour TableHeaders pour l’élément Label de table (Format) pour TableColumnHeader pour la table (Format)

## <a name="syntax"></a>Syntaxe

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Label` élément. Étiquette qu’un seul est autorisée pour chaque colonne.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableColumnHeader pour TableHeaders pour la table (Format)](./tablecolumnheader-element-format.md)|Définit une étiquette, la largeur et l’alignement des données pour une colonne de la table.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le texte qui s’affiche en haut de la colonne de la table. Il n’existe aucun des caractères non autorisés pour l’étiquette de colonne.

## <a name="remarks"></a>Remarques

Si aucune étiquette n’est spécifiée, le nom de la propriété dont la valeur est affichée dans les lignes est utilisé.

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

Cet exemple montre un `TableColumnHeader` élément dont l’étiquette est « Colonne 1 ».

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de Table](./creating-a-table-view.md)

[Élément TableColumnHeader (Format)](./tablecolumnheader-element-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
