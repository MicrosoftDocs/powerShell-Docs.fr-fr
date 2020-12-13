---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour EntrySelectedBy pour WideControl (Format)
description: SelectionSetName, élément pour EntrySelectedBy pour WideControl (Format)
ms.openlocfilehash: bf6a44bb733421f36a9140d0ec10e61aedfbda6a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651687"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>SelectionSetName, élément pour EntrySelectedBy pour WideControl (Format)

Spécifie un jeu d’objets .NET pour la définition. La définition est utilisée chaque fois que l’un de ces objets est affiché.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) EntrySelectedBy élément pour WideEntry (format) SelectionSetName élément pour EntrySelectedBy (format)

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
|[EntrySelectedBy, élément pour WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Définit les types .NET qui utilisent cette entrée étendue ou la condition qui doit exister pour que cette entrée soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du jeu de sélection.

## <a name="remarks"></a>Notes

Chaque définition doit spécifier un nom de type, un jeu de sélection ou une condition de sélection.

Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues. Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets. Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux d’objets pour une vue](./defining-selection-sets.md).

Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue large](./creating-a-wide-view.md)

[Définition de jeux de sélections](./defining-selection-sets.md)

[EntrySelectedBy, élément pour WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
