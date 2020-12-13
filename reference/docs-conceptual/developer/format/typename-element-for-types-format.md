---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour Types (Format)
description: TypeName, élément pour Types (Format)
ms.openlocfilehash: c656b8e7e5877b72ff2164e5b417857273cada61
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664617"
---
# <a name="typename-element-for-types-format"></a>TypeName, élément pour Types (Format)

Spécifie le type .NET d’un objet qui appartient au jeu de sélection.

Élément de configuration (format) élément SelectionSets (format) élément SelectionSet (format) types élément (format) TypeName élément de types (format)

## <a name="syntax"></a>Syntaxe

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément. Au moins un `TypeName` élément doit être inclus dans le jeu de sélection.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément types (format)](./types-element-for-selectionset-format.md)|Définit les objets .NET qui se trouvent dans le jeu de sélection.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom qualifié complet du type .NET.

## <a name="remarks"></a>Notes

Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage. Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom du jeu de sélection au lieu de répertorier tous les objets dans chaque vue.

Les jeux de sélection communs sont spécifiés par leur nom lors de la définition des vues du fichier de mise en forme. Dans ce cas, l' `SelectionSetName` élément enfant de l' `ViewSelectedBy` élément de la vue spécifie le jeu. Toutefois, différentes entrées d’une vue peuvent également spécifier un jeu de sélection qui s’applique uniquement à cette entrée de la vue. Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `SelectionSet` élément qui définit quatre types .net.

```
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a>Voir aussi

[Définition de jeux de sélections](./defining-selection-sets.md)

[SelectionSet, élément (Format)](./selectionset-element-format.md)

[SelectionSets, élément (Format)](./selectionsets-element-format.md)

[Élément types (format)](./types-element-for-selectionset-format.md)

[Écriture d’un fichier de mise en forme Windows PowerShell](./writing-a-powershell-formatting-file.md)
