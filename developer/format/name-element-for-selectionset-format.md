---
title: Nom d’élément pour SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858165"
---
# <a name="name-element-for-selectionset-format"></a>Name, élément pour SelectionSet (Format)

Spécifie le nom utilisé pour référencer le jeu de sélection.

Configuration (Format) élément SelectionSets (Format) élément SelectionSet (Format) nom Element du SelectionSet (Format)

## <a name="syntax"></a>Syntaxe

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `Name` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionSet (Format)](./selectionset-element-format.md)|Définit un ensemble unique d’objets .NET qui peuvent être référencés par le nom de l’ensemble.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom pour faire référence à l’ensemble de la sélection. Il existe aucune restriction concernant les caractères ne peut être utilisée.

## <a name="remarks"></a>Remarques

Le nom spécifié ici est utilisé dans le `SelectionSetName` élément. Le jeu de sélection qui peut être utilisé par une vue, en une définition d’une vue (vues peuvent avoir plusieurs définitions), ou lorsque vous spécifiez une condition de sélection. Pour plus d’informations sur les jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).

## <a name="example"></a>Exemple

Cet exemple montre un `SelectionSet` élément qui définit les quatre types de .NET. Le nom de l’ensemble de la sélection est « FileSystemTypes ».

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

[Élément SelectionSet (Format)](./selectionset-element-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
