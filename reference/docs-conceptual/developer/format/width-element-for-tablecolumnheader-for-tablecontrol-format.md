---
title: Width, élément de TableColumnHeader pour table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9540d3d351041ad7cb98a21bb360ebea7eca117
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779911"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Width, élément pour TableColumnHeader pour TableControl (Format)

Définit la largeur (en caractères) d’une colonne.

Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément table ((format) élément TableHeaders pour table ((format) TableColumnHeader élément TableHeaders pour table ((format) élément Width pour TableColumnHeader (format)

## <a name="syntax"></a>Syntaxe

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Width` élément utilisé lors de la définition des en-têtes de colonne.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableColumnHeader pour TableHeaders pour table ((format)](./tablecolumnheader-element-format.md)|Définit une étiquette, une largeur et un alignement des données pour une colonne de la table.|

## <a name="text-value"></a>Valeur texte

Dans la mesure du possible, spécifiez une largeur (en caractères) supérieure à la longueur des valeurs de propriété affichées.

## <a name="remarks"></a>Notes

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `TableColumnHeader` élément dont la largeur est de 16 caractères.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de table](./creating-a-table-view.md)

[Élément TableColumnHeader pour TableHeader pour table ((format)](./tablecolumnheader-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
