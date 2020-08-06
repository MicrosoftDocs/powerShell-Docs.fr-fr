---
title: Élément Name pour SelectionSet (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1fc33eeb87a6912ed6793629ab1969cd65b5f0c5
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773298"
---
# <a name="name-element-for-selectionset-format"></a>Name, élément pour SelectionSet (Format)

Spécifie le nom utilisé pour référencer le jeu de sélection.

Élément de configuration (format) élément SelectionSets (format) élément SelectionSet (format) élément Name de SelectionSet (format)

## <a name="syntax"></a>Syntaxe

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Name` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[SelectionSet, élément (Format)](./selectionset-element-format.md)|Définit un ensemble unique d’objets .NET qui peuvent être référencés par le nom de l’ensemble.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom pour faire référence au jeu de sélection. Il n’existe aucune restriction quant aux caractères qui peuvent être utilisés.

## <a name="remarks"></a>Notes

Le nom spécifié ici est utilisé dans l' `SelectionSetName` élément. Jeu de sélection qui peut être utilisé par une vue, par une définition d’une vue (les vues peuvent avoir plusieurs définitions) ou lors de la spécification d’une condition de sélection. Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).

## <a name="example"></a>Exemple

Cet exemple montre un `SelectionSet` élément qui définit quatre types .net. Le nom du jeu de sélection est « FileSystemTypes ».

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

[SelectionSet, élément (Format)](./selectionset-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
