---
ms.date: 09/13/2016
ms.topic: reference
title: Label, élément pour TableColumnHeader pour TableControl (Format)
description: Label, élément pour TableColumnHeader pour TableControl (Format)
ms.openlocfilehash: fe4c209903c04e683b44e2bdcbf381adb6874ace
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667791"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Label, élément pour TableColumnHeader pour TableControl (Format)

Définit l’étiquette qui s’affiche en haut d’une colonne. Cet élément est utilisé lors de la définition d’une vue de table.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableHeaders pour table ((format) élément TableColumnHeader pour TableHeaders pour table ((format) élément label pour TableColumnHeader (format)

## <a name="syntax"></a>Syntaxe

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Label` élément. Une seule étiquette est autorisée pour chaque colonne.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableColumnHeader pour TableHeaders pour table ((format)](./tablecolumnheader-element-format.md)|Définit une étiquette, la largeur et l’alignement des données pour une colonne de la table.|

## <a name="text-value"></a>Valeur texte

Spécifiez le texte affiché en haut de la colonne de la table. Il n’y a pas de caractères restreints pour l’étiquette de colonne.

## <a name="remarks"></a>Notes

Si aucune étiquette n’est spécifiée, le nom de la propriété dont la valeur est affichée dans les lignes est utilisé.

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

Cet exemple montre un `TableColumnHeader` élément dont l’étiquette est « column 1 ».

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
