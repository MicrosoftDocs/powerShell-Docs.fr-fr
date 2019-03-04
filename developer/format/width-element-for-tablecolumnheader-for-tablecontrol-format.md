---
title: Élément de la largeur pour TableColumnHeader pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: a38fcbef457e69e3ea08d25ba3a9843621036f1e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853105"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Width, élément pour TableColumnHeader pour TableControl (Format)

Définit la largeur (en caractères) d’une colonne.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableHeaders élément de configuration pour TableHeaders TableColumnHeader élément de table (Format) pour l’élément de la largeur de la table (Format) pour TableColumnHeader pour la table (Format)

## <a name="syntax"></a>Syntaxe

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `Width` élément utilisé lors de la définition des en-têtes de colonne.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableColumnHeader pour TableHeaders pour TbleControl (Format)](./tablecolumnheader-element-format.md)|Définit une étiquette, la largeur et l’alignement des données pour une colonne de la table.|

## <a name="text-value"></a>Valeur de texte

Lorsqu’à cela est possible, spécifiez une largeur (en caractères) qui est supérieure à la longueur des valeurs de propriété affiché.

## <a name="remarks"></a>Remarques

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).

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

[Création d’une vue de Table](./creating-a-table-view.md)

[Élément TableColumnHeader pour TableHeader pour la table (Format)](./tablecolumnheader-element-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
