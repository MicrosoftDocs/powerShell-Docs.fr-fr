---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)
description: SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)
ms.openlocfilehash: c6466e3ac6e1f194df9172468d26448f9630da6a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655016"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a>SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)

Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de cette définition de la vue étendue.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) élément SelectionCondition pour EntrySelectedBy (format) WideEntry élément pour SelectionSetName pour SelectionCondition (format)

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
|[Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Définit la condition qui doit exister pour que cette définition soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du jeu de sélection.

## <a name="remarks"></a>Notes

La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux. Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme. Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).

Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue large](./creating-a-wide-view.md)

[Définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md)

[Définition de jeux de sélections](./defining-selection-sets.md)

[Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
