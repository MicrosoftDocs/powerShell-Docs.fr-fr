---
title: Élément SelectionSets (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853565"
---
# <a name="selectionsets-element-format"></a>SelectionSets, élément (Format)

Définit les jeux d’objets .NET qui peuvent être utilisées par toutes les vues du fichier de mise en forme courants. Les vues et les contrôles du fichier de mise en forme peuvent faire référence à l’ensemble complet des objets en utilisant uniquement le nom de l’ensemble de la sélection.

Format d’élément de SelectionSets élément de configuration

## <a name="syntax"></a>Syntaxe

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `SelectionSets` élément. Chaque élément enfant définit un ensemble d’objets qui peuvent être référencés par le nom de l’ensemble. L’ordre des éléments enfants n’est pas significatif.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionSet (Format)](./selectionset-element-format.md)|Élément requis.<br /><br /> Définit un ensemble unique d’objets .NET qui peuvent être référencés par le nom de l’ensemble.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de configuration](./configuration-element-format.md)|Représente l’élément de niveau supérieur d’un fichier de mise en forme.|

## <a name="remarks"></a>Remarques

Vous pouvez utiliser des jeux de sélection lorsque vous avez un ensemble d’objets connexes que vous souhaitez faire référence à l’aide d’un nom unique, comme un ensemble d’objets qui sont liés par héritage. Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom de la sélection définie au lieu de répertorier tous les objets au sein de chaque vue.

Ensembles communs de sélection sont spécifiés par leur nom lorsque vous définissez les vues du fichier de mise en forme ou les définitions des vues. Dans ce cas, le `SelectionSetName` élément enfant de le `ViewSelectedBy` et `EntrySelectedBy` éléments spécifie le jeu à utiliser. Pour plus d’informations sur les jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).

## <a name="see-also"></a>Voir aussi

[Élément de configuration](./configuration-element-format.md)

[Définition de jeux de sélection](./defining-selection-sets.md)

[Élément SelectionSet (Format)](./selectionset-element-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
