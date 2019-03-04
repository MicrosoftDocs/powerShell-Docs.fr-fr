---
title: Élément SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861155"
---
# <a name="selectionset-element-format"></a>SelectionSet, élément (Format)

Définit un ensemble d’objets .NET qui peuvent être référencés par le nom de l’ensemble.

Configuration élément (Format) SelectionSets (Format) SelectionSet élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSet` élément. Chaque jeu de sélection doit avoir un nom, et il doit spécifier les objets .NET de l’ensemble.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Name, élément pour SelectionSet (Format)](./name-element-for-selectionset-format.md)|Élément requis.<br /><br /> Spécifie le nom utilisé pour référencer le jeu de sélection.|
|[Élément de types (Format)](./types-element-for-selectionset-format.md)|Élément requis.<br /><br /> Définit les objets .NET qui sont définies dans la sélection.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Format d’élément de SelectionSets](./selectionsets-element-format.md)|Définit les jeux d’objets .NET qui peuvent être utilisées par toutes les vues du fichier de mise en forme courants.|

## <a name="remarks"></a>Remarques

Vous pouvez utiliser des jeux de sélection lorsque vous avez un ensemble d’objets connexes que vous souhaitez faire référence à l’aide d’un nom unique, comme un ensemble d’objets qui sont liés par héritage. Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom de la sélection définie au lieu de répertorier tous les objets au sein de chaque vue.

Ensembles communs de sélection sont spécifiés par leur nom lorsque vous définissez les vues du fichier de mise en forme ou les définitions des vues. Dans ce cas, le `SelectionSetName` élément enfant de le `ViewSelectedBy` et `EntrySelectedBy` éléments spécifie le jeu à utiliser. Pour plus d’informations sur les jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `SelectionSet` élément qui définit les quatre types de .NET.

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

[Définition de jeux de sélection](./defining-selection-sets.md)

[Name, élément de SelectionSet (Format)](./name-element-for-selectionset-format.md)

[Élément SelectionSets (Format)](./selectionsets-element-format.md)

[Élément de types (Format)](./types-element-for-selectionset-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
