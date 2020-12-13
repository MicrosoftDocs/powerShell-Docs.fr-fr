---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSet, élément (Format)
description: SelectionSet, élément (Format)
ms.openlocfilehash: 944aa83569ad8ca789746a71f60e5da5c19fbf01
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647871"
---
# <a name="selectionset-element-format"></a>SelectionSet, élément (Format)

Définit un ensemble d’objets .NET qui peuvent être référencés par le nom de l’ensemble.

Élément de configuration (format) élément SelectionSets (format) SelectionSet, élément (format)

## <a name="syntax"></a>Syntaxe

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSet` élément. Chaque jeu de sélection doit avoir un nom et doit spécifier les objets .NET de l’ensemble.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Name, élément pour SelectionSet (Format)](./name-element-for-selectionset-format.md)|Élément requis.<br /><br /> Spécifie le nom utilisé pour référencer le jeu de sélection.|
|[Élément types (format)](./types-element-for-selectionset-format.md)|Élément requis.<br /><br /> Définit les objets .NET qui se trouvent dans le jeu de sélection.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Format de l’élément SelectionSets](./selectionsets-element-format.md)|Définit les ensembles courants d’objets .NET qui peuvent être utilisés par toutes les vues du fichier de mise en forme.|

## <a name="remarks"></a>Notes

Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage. Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom du jeu de sélection au lieu de répertorier tous les objets dans chaque vue.

Les jeux de sélection communs sont spécifiés par leur nom lors de la définition des vues du fichier de mise en forme ou des définitions des vues. Dans ce cas, l' `SelectionSetName` élément enfant des `ViewSelectedBy` éléments et `EntrySelectedBy` spécifie le jeu à utiliser. Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `SelectionSet` élément qui définit quatre types .net.

```xml
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

[Élément Name de SelectionSet (format)](./name-element-for-selectionset-format.md)

[SelectionSets, élément (Format)](./selectionsets-element-format.md)

[Élément types (format)](./types-element-for-selectionset-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
