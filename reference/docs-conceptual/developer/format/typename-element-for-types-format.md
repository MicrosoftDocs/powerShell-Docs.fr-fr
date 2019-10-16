---
title: Élément TypeName pour les types (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368028"
---
# <a name="typename-element-for-types-format"></a>TypeName, élément pour Types (Format)

Spécifie le type .NET d’un objet qui appartient au jeu de sélection.

Élément de configuration (format) élément SelectionSets (format) élément SelectionSet (format) types élément (format) TypeName élément de types (format)

## <a name="syntax"></a>Syntaxe

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TypeName`. Au moins un élément `TypeName` doit être inclus dans le jeu de sélection.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément types (format)](./types-element-for-selectionset-format.md)|Définit les objets .NET qui se trouvent dans le jeu de sélection.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom qualifié complet du type .NET.

## <a name="remarks"></a>Remarks

Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage. Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom du jeu de sélection au lieu de répertorier tous les objets dans chaque vue.

Les jeux de sélection communs sont spécifiés par leur nom lors de la définition des vues du fichier de mise en forme. Dans ce cas, l’élément enfant `SelectionSetName` de l’élément `ViewSelectedBy` de la vue spécifie le jeu. Toutefois, différentes entrées d’une vue peuvent également spécifier un jeu de sélection qui s’applique uniquement à cette entrée de la vue. Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un élément `SelectionSet` qui définit quatre types .NET.

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

[Définition des jeux de sélection](./defining-selection-sets.md)

[Élément SelectionSet (format)](./selectionset-element-format.md)

[Élément SelectionSets (format)](./selectionsets-element-format.md)

[Élément types (format)](./types-element-for-selectionset-format.md)

[Écriture d’un fichier de mise en forme Windows PowerShell](./writing-a-powershell-formatting-file.md)
