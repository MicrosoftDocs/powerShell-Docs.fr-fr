---
title: Élément de nom de type pour les Types (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057924"
---
# <a name="typename-element-for-types-format"></a>TypeName, élément pour Types (Format)

Spécifie le type .NET d’un objet qui appartient au jeu de sélection.

Types de configuration élément (Format) SelectionSets (Format) SelectionSet élément (Format) (Format) TypeName Element de Types (Format)

## <a name="syntax"></a>Syntaxe

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `TypeName` élément. Au moins un `TypeName` élément doit être inclus dans le jeu de sélection.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de types (Format)](./types-element-for-selectionset-format.md)|Définit les objets .NET qui sont définies dans la sélection.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom qualifié complet pour le type .NET.

## <a name="remarks"></a>Remarques

Vous pouvez utiliser des jeux de sélection lorsque vous avez un ensemble d’objets connexes que vous souhaitez faire référence à l’aide d’un nom unique, comme un ensemble d’objets qui sont liés par héritage. Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom de la sélection définie au lieu de répertorier tous les objets au sein de chaque vue.

Ensembles communs de sélection sont spécifiés par leur nom lorsque vous définissez les vues du fichier de mise en forme. Dans ce cas, le `SelectionSetName` élément enfant de le `ViewSelectedBy` élément pour l’affichage spécifie le jeu. Toutefois, des entrées différentes d’une vue peuvent également spécifier un jeu de sélection s’applique à uniquement l’entrée de la vue. Pour plus d’informations sur les jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `SelectionSet` élément qui définit les quatre types de .NET.

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

[Définition de jeux de sélection](./defining-selection-sets.md)

[Élément SelectionSet (Format)](./selectionset-element-format.md)

[Élément SelectionSets (Format)](./selectionsets-element-format.md)

[Élément de types (Format)](./types-element-for-selectionset-format.md)

[Écriture d’un fichier de mise en forme de PowerShell Windows](./writing-a-powershell-formatting-file.md)
