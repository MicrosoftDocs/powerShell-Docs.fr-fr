---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour EntrySelectedBy pour Controls pour View (Format)
description: SelectionSetName, élément pour EntrySelectedBy pour Controls pour View (Format)
ms.openlocfilehash: 3211b7cacd7e57770b48b03f4aade33da506f180
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664736"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a>SelectionSetName, élément pour EntrySelectedBy pour Controls pour View (Format)

Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour les contrôles pour l’élément d’affichage (format) CustomEntry pour CustomEntries pour les contrôles de l’élément EntrySelectedBy (format) pour CustomEntry pour les contrôles de l’élément View (format) SelectionSetName pour les contrôles pour View (format)

## <a name="syntax"></a>Syntaxe

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.

### <a name="attributes"></a>Attributs

None

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du jeu de sélection.

## <a name="remarks"></a>Notes

Chaque définition de contrôle doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.

Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues. Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux de sélection](./defining-selection-sets.md).

## <a name="see-also"></a>Voir aussi

[EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
