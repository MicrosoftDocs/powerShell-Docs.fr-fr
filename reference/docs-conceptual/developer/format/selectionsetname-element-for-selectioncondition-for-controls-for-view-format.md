---
title: Élément SelectionSetName pour SelectionCondition pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0feb23f860487952344680f75ee674e9e0e6dcc6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787527"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a>SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)

Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de ce contrôle. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour View (format) CustomEntries element pour CustomControl pour les contrôles pour View (format) élément CustomEntry pour CustomEntries pour les contrôles de l’élément View (format) EntrySelectedBy pour CustomEntry pour les contrôles pour l’élément View (format) SelectionCondition pour les contrôles de l’élément View (format) EntrySelectedBy pour SelectionSetName pour les contrôles pour View (format)

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
|[SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du jeu de sélection.

## <a name="remarks"></a>Notes

Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme. Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).

La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux. Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md)

[Définition de jeux de sélections](./defining-selection-sets.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
