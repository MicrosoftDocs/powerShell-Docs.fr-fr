---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)
description: SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)
ms.openlocfilehash: 7ebe5d884061243c8b4af196788187d84c15a92e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651851"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a>SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)

Spécifie un ensemble d’objets .NET pour l’entrée de liste. Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) EntrySelectedBy élément pour CustomEntry pour GroupBy (format) élément SelectionSetName pour GroupBy (format)

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
|[EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Définit les types .NET qui utilisent cette entrée personnalisée ou la condition qui doit exister pour que cette entrée soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du jeu de sélection.

## <a name="remarks"></a>Notes

Chaque définition de contrôle personnalisé doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.

Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues. Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets. Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux de sélection](./defining-selection-sets.md).

Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).

## <a name="see-also"></a>Voir aussi

[EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Création de contrôles personnalisés](./creating-custom-controls.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
