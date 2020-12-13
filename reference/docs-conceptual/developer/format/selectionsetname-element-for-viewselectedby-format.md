---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour ViewSelectedBy (Format)
description: SelectionSetName, élément pour ViewSelectedBy (Format)
ms.openlocfilehash: a1a1816761715a138bcb3c2bd4cb9dbbb2f9cb92
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654912"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>SelectionSetName, élément pour ViewSelectedBy (Format)

Spécifie un jeu d’objets .NET qui sont affichés par la vue.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément ViewSelectedBy (format) élément SelectionSetName pour ViewSelectedBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ViewSelectedBy, élément (Format)](./viewselectedby-element-format.md)|Définit les objets .NET affichés par la vue.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du jeu de sélection défini par l' `Name` élément pour le jeu de sélection.

## <a name="remarks"></a>Notes

Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage. Pour plus d’informations sur la définition et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier un jeu de sélection pour un mode liste. Le même schéma est utilisé pour les vues de table, larges et personnalisées.

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Voir aussi

[Définition de jeux de sélections](./defining-selection-sets.md)

[ViewSelectedBy, élément (Format)](./viewselectedby-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
