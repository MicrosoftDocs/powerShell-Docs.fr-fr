---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)
description: SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)
ms.openlocfilehash: f3193799e67706eb07f0fe1c2cd42cce83f7af57
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651541"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a>SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)

Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de cette définition de la vue liste.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionCondition pour EntrySelectedBy pour ListEntry (format) SelectionSetName élément pour SelectionCondition pour ListEntry (format)

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
|[Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Définit la condition qui doit exister pour utiliser cette définition de la vue liste.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du jeu de sélection.

## <a name="remarks"></a>Notes

La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux. Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme. Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).

Pour plus d’informations sur les autres composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue de liste](./creating-a-list-view.md)

[Définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md)

[Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
