---
title: Élément SelectionSets (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 718b08e02220f285ef215fdca727492fd4407466
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785198"
---
# <a name="selectionsets-element-format"></a>SelectionSets, élément (Format)

Définit les ensembles courants d’objets .NET qui peuvent être utilisés par toutes les vues du fichier de mise en forme. Les vues et les contrôles du fichier de mise en forme peuvent faire référence à l’ensemble complet d’objets en utilisant uniquement le nom du jeu de sélection.

Format d’élément SelectionSets de l’élément de configuration

## <a name="syntax"></a>Syntaxe

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSets` élément. Chaque élément enfant définit un ensemble d’objets qui peuvent être référencés par le nom de l’ensemble. L’ordre des éléments enfants n’est pas significatif.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[SelectionSet, élément (Format)](./selectionset-element-format.md)|Élément requis.<br /><br /> Définit un ensemble unique d’objets .NET qui peuvent être référencés par le nom de l’ensemble.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de configuration](./configuration-element-format.md)|Représente l’élément de niveau supérieur d’un fichier de mise en forme.|

## <a name="remarks"></a>Notes

Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage. Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom du jeu de sélection au lieu de répertorier tous les objets dans chaque vue.

Les jeux de sélection communs sont spécifiés par leur nom lors de la définition des vues du fichier de mise en forme ou des définitions des vues. Dans ce cas, l' `SelectionSetName` élément enfant des `ViewSelectedBy` éléments et `EntrySelectedBy` spécifie le jeu à utiliser. Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).

## <a name="see-also"></a>Voir aussi

[Élément de configuration](./configuration-element-format.md)

[Définition de jeux de sélections](./defining-selection-sets.md)

[SelectionSet, élément (Format)](./selectionset-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
