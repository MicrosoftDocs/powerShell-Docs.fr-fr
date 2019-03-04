---
title: Types d’élément de SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862375"
---
# <a name="types-element-for-selectionset-format"></a>Types, élément pour SelectionSet (Format)

Définit les objets .NET qui sont définies dans la sélection.

Types de configuration élément (Format) SelectionSets (Format) SelectionSet élément (Format) élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Types` élément. Il doit y avoir au moins un élément enfant, mais il n’existe aucune limite maximale pour le nombre d’éléments enfants qui peuvent être ajoutées.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément de TypeName de Types (Format)](./typename-element-for-types-format.md)|Élément requis.<br /><br /> Spécifie l’objet .NET qui appartient au jeu de sélection.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionSet (Format)](./selectionset-element-format.md)|Définit un ensemble d’objets .NET qui peuvent être référencés par le nom de l’ensemble.|

## <a name="remarks"></a>Remarques

Les objets définis par cet élément constituent un ensemble de sélection peut être utilisé par une vue, en une définition d’une vue (vues peuvent avoir plusieurs définitions), ou lorsque vous spécifiez une condition de sélection.  Pour plus d’informations sur les jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).

## <a name="example"></a>Exemple

Cet exemple montre un `SelectionSet` élément qui définit les quatre types de .NET.

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

[Élément SelectionSet (Format)](./selectionset-element-format.md)

[Élément de TypeName de Types (Format)](./typename-element-for-types-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
