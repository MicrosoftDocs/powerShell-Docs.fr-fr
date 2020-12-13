---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour EntrySelectedBy pour CustomControl pour View (Format)
description: SelectionSetName, élément pour EntrySelectedBy pour CustomControl pour View (Format)
ms.openlocfilehash: a158c5476fb3a168a146ce67565c0ed6f7859519
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651918"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>SelectionSetName, élément pour EntrySelectedBy pour CustomControl pour View (Format)

Spécifie un ensemble d’objets .NET pour l’entrée de liste. Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour l’élément View (format) EntrySelectedBy pour CustomEntry pour l’élément View (format) SelectionSetName pour EntrySelectedBy (format)

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
|[Élément EntrySelectedBy pour CustomEntry pour View (format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Définit les types .NET qui utilisent cette entrée personnalisée ou la condition qui doit exister pour que cette entrée soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du jeu de sélection.

## <a name="remarks"></a>Notes

Au moins un nom de type, un jeu de sélection ou une condition de sélection doit être défini pour chaque entrée de contrôle personnalisé.

Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues. Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets. Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux de sélection](./defining-selection-sets.md).

Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).

## <a name="see-also"></a>Voir aussi

[Élément EntrySelectedBy pour CustomEntry pour View (format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Affichage de contrôle personnalisé](./creating-custom-controls.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
