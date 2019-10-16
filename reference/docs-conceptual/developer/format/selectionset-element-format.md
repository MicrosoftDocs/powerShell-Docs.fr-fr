---
title: Élément SelectionSet (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368378"
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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSet`. Chaque jeu de sélection doit avoir un nom et doit spécifier les objets .NET de l’ensemble.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément Name pour SelectionSet (format)](./name-element-for-selectionset-format.md)|Élément requis.<br /><br /> Spécifie le nom utilisé pour référencer le jeu de sélection.|
|[Élément types (format)](./types-element-for-selectionset-format.md)|Élément requis.<br /><br /> Définit les objets .NET qui se trouvent dans le jeu de sélection.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Format de l’élément SelectionSets](./selectionsets-element-format.md)|Définit les ensembles courants d’objets .NET qui peuvent être utilisés par toutes les vues du fichier de mise en forme.|

## <a name="remarks"></a>Remarks

Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage. Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom du jeu de sélection au lieu de répertorier tous les objets dans chaque vue.

Les jeux de sélection communs sont spécifiés par leur nom lors de la définition des vues du fichier de mise en forme ou des définitions des vues. Dans ce cas, l’élément enfant `SelectionSetName` des éléments `ViewSelectedBy` et `EntrySelectedBy` spécifie le jeu à utiliser. Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un élément `SelectionSet` qui définit quatre types .NET.

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

[Définition des jeux de sélection](./defining-selection-sets.md)

[Élément Name de SelectionSet (format)](./name-element-for-selectionset-format.md)

[Élément SelectionSets (format)](./selectionsets-element-format.md)

[Élément types (format)](./types-element-for-selectionset-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
