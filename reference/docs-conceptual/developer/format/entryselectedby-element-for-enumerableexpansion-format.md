---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy, élément pour EnumerableExpansion (Format)
description: EntrySelectedBy, élément pour EnumerableExpansion (Format)
ms.openlocfilehash: 8b2fff2d0b14d0622d0be2c5af3a95194c733a73
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652324"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>EntrySelectedBy, élément pour EnumerableExpansion (Format)

Définit les types .NET qui utilisent cette définition ou la condition qui doit exister pour que cette définition soit utilisée.

Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) EntrySelectedBy élément pour EnumerableExpansion (format)

## <a name="syntax"></a>Syntaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour développer les objets de collection de cette définition.|
|[SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition de la façon dont les objets de collection sont développés.|
|[TypeName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition de la façon dont les objets de la collection sont développés.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[EnumerableExpansion, élément (Format)](./enumerableexpansion-element-format.md)|Définit la façon dont des objets de collection .NET spécifiques sont développés lorsqu’ils sont affichés dans une vue.|

## <a name="remarks"></a>Notes

Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une entrée de définition. Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.

Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou un script spécifique prend la valeur `true` . Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Définition de conditions pour l’affichage de données](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion, élément (Format)](./enumerableexpansion-element-format.md)

[SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[TypeName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
