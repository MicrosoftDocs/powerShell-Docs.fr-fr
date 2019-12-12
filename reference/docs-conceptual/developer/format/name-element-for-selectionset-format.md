---
title: Élément Name pour SelectionSet (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362668"
---
# <a name="name-element-for-selectionset-format"></a>Name, élément pour SelectionSet (Format)

Spécifie le nom utilisé pour référencer le jeu de sélection.

Élément de configuration (format) élément SelectionSets (format) élément SelectionSet (format) élément Name de SelectionSet (format)

## <a name="syntax"></a>Syntaxe

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Name`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionSet (format)](./selectionset-element-format.md)|Définit un ensemble unique d’objets .NET qui peuvent être référencés par le nom de l’ensemble.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom pour faire référence au jeu de sélection. Il n’existe aucune restriction quant aux caractères qui peuvent être utilisés.

## <a name="remarks"></a>Remarks

Le nom spécifié ici est utilisé dans l’élément `SelectionSetName`. Jeu de sélection qui peut être utilisé par une vue, par une définition d’une vue (les vues peuvent avoir plusieurs définitions) ou lors de la spécification d’une condition de sélection. Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).

## <a name="example"></a>Exemple

Cet exemple montre un élément `SelectionSet` qui définit quatre types .NET. Le nom du jeu de sélection est « FileSystemTypes ».

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

[Élément SelectionSet (format)](./selectionset-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
