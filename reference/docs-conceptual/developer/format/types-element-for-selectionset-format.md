---
ms.date: 09/13/2016
ms.topic: reference
title: Types, élément pour SelectionSet (Format)
description: Types, élément pour SelectionSet (Format)
ms.openlocfilehash: ff3c24e7f52f862dc416b88d50983196ce907012
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645457"
---
# <a name="types-element-for-selectionset-format"></a>Types, élément pour SelectionSet (Format)

Définit les objets .NET qui se trouvent dans le jeu de sélection.

Élément de configuration (format) élément SelectionSets (format) élément SelectionSet (format) élément types (format)

## <a name="syntax"></a>Syntaxe

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Types` élément. Il doit y avoir au moins un élément enfant, mais il n’existe pas de limite maximale pour le nombre d’éléments enfants qui peuvent être ajoutés.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément TypeName de types (format)](./typename-element-for-types-format.md)|Élément requis.<br /><br /> Spécifie l’objet .NET qui appartient au jeu de sélection.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[SelectionSet, élément (Format)](./selectionset-element-format.md)|Définit un ensemble d’objets .NET qui peuvent être référencés par le nom de l’ensemble.|

## <a name="remarks"></a>Notes

Les objets définis par cet élément composent un jeu de sélection qui peut être utilisé par une vue, par une définition d’une vue (les vues peuvent avoir plusieurs définitions) ou lors de la spécification d’une condition de sélection.  Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).

## <a name="example"></a>Exemple

Cet exemple montre un `SelectionSet` élément qui définit quatre types .net.

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

[Définition de jeux d’objets](./defining-selection-sets.md)

[SelectionSet, élément (Format)](./selectionset-element-format.md)

[Élément TypeName de types (format)](./typename-element-for-types-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
