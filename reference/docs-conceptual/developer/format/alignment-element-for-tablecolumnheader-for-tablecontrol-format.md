---
ms.date: 09/13/2016
ms.topic: reference
title: Alignment, élément pour TableColumnHeader pour TableControl (Format)
description: Alignment, élément pour TableColumnHeader pour TableControl (Format)
ms.openlocfilehash: cf8b90c12c28951283b5870186e2c88d427318a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666822"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Alignment, élément pour TableColumnHeader pour TableControl (Format)

Définit le mode d’affichage des données dans un en-tête de colonne.

Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément table ((format) élément TableHeaders (format) TableColumnHeader élément (format) élément d’alignement pour TableColumnHeader (format)

## <a name="syntax"></a>Syntaxe

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Alignment` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TableColumnHeader, élément (Format)](./tablecolumnheader-element-format.md)|Définit une étiquette, la largeur et l’alignement des données pour une colonne de la table.|

## <a name="text-value"></a>Valeur texte

Spécifiez l’une des valeurs suivantes. Ces valeurs ne respectent pas la casse.

Aligner à gauche aligne les données affichées dans la colonne de gauche. il s’agit de la valeur par défaut si cet élément n’est pas spécifié.

Aligne à droite les données affichées dans la colonne de droite.

Centre Centre les données affichées dans la colonne.

## <a name="remarks"></a>Notes

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

Cet exemple montre un `TableColumnHeader` élément dont les données sont alignées à gauche.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de table](./creating-a-table-view.md)

[TableColumnHeader, élément (Format)](./tablecolumnheader-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
