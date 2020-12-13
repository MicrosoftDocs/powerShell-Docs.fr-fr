---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)
description: SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)
ms.openlocfilehash: 0c9372113a79f75cfbda67acf869164fde894ee3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651589"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)

Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand l’un des types de cet ensemble est présent, la condition est remplie.

Élément de configuration élément DefaultSettings (format) élément EnumerableExpansions (format) élément EnumerableExpansions (format) élément EntrySelectedBy pour EnumerableExpansion (format) élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) SelectionSetName élément pour SelectionCondition pour EntrySelectedBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Définit la condition qui doit exister pour développer les objets de collection de cette définition.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du jeu de sélection.

## <a name="remarks"></a>Notes

La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux. Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme. Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).

## <a name="see-also"></a>Voir aussi

[Définition de jeux de sélections](./defining-selection-sets.md)

[SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
