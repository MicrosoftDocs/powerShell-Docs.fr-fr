---
title: Élément d’alignement pour TableColumnHeader pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067006"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Alignment, élément pour TableColumnHeader pour TableControl (Format)

Définit comment les données dans un en-tête de colonne s’affiche.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) élément TableHeaders (Format) TableColumnHeader, élément (Format) alignement élément de configuration pour TableColumnHeader (Format)

## <a name="syntax"></a>Syntaxe

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `Alignment` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableColumnHeader (Format)](./tablecolumnheader-element-format.md)|Définit une étiquette, la largeur et l’alignement des données pour une colonne de la table.|

## <a name="text-value"></a>Valeur de texte

Spécifiez l’une des valeurs suivantes. Ces valeurs ne respectent pas la casse.

Aligne à gauche les données affichées dans la colonne gauche Ceci est la valeur par défaut si cet élément n’est pas spécifié.

Aligne à droite les données affichées dans la colonne de droite.

Centres de centre de données affichées dans la colonne.

## <a name="remarks"></a>Remarques

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).

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

[Création d’une vue de Table](./creating-a-table-view.md)

[Élément TableColumnHeader (Format)](./tablecolumnheader-element-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
