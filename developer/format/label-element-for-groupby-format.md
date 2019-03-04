---
title: L’étiquette d’élément pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862395"
---
# <a name="label-element-for-groupby-format"></a>Label, élément pour GroupBy (Format)

Spécifie une étiquette qui s’affiche lorsqu’un nouveau groupe est rencontré.

Configuration élément (Format) ViewDefinitions, élément (Format) (Format) d’élément GroupBy élément d’affichage pour l’élément Label de vue (Format) pour GroupBy (Format)

## <a name="syntax"></a>Syntaxe

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `Label` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément GroupBy de vue (Format)](./groupby-element-for-view-format.md)|Définit comment un nouveau groupe d’objets est affiché.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le texte qui s’affiche chaque fois que Windows PowerShell rencontre une nouvelle propriété ou la valeur de script.

## <a name="remarks"></a>Remarques

En plus du texte spécifié par cet élément, Windows PowerShell affiche la nouvelle valeur qui démarre le groupe et ajoute une ligne vide avant et après le groupe.

## <a name="example"></a>Exemple

L’exemple suivant montre l’étiquette pour un nouveau groupe. L’étiquette affichée ressemblerait à ceci : `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Pour obtenir un exemple d’un fichier de mise en forme complète qui inclut cet élément, consultez [affichage plus large (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Voir aussi

[Élément GroupBy de vue (Format)](./groupby-element-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
