---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition, élément pour EntrySelectedBy pour CustomControl (Format)
description: SelectionCondition, élément pour EntrySelectedBy pour CustomControl (Format)
ms.openlocfilehash: 6d4cc5a2d5fef0445d586e320b3729d3a7044063
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649773"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>SelectionCondition, élément pour EntrySelectedBy pour CustomControl (Format)

Définit une condition qui doit exister pour une définition de contrôle à utiliser. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour la vue (format) élément CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour CustomControl pour la vue (format) CustomItem élément pour la vue (format) CustomEntry pour CustomControl pour la vue (format)

## <a name="syntax"></a>Syntaxe

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionCondition` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[PropertyName, élément pour SelectionCondition pour CustomControl pour View (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie une propriété .NET qui déclenche la condition.|
|[ScriptBlock, élément pour SelectionCondition pour CustomControl pour View (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|
|[Élément SelectionSetName pour SelectionCondition pour un contrôle personnalisé pour View (format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie l’ensemble des types .NET qui déclenchent la condition.|
|[TypeName, élément pour SelectionCondition pour CustomControl pour View (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[EntrySelectedBy, élément pour CustomEntry pour CustomControl pour View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.|

## <a name="remarks"></a>Notes

Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :

- La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.

- La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.

Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[PropertyName, élément pour SelectionCondition pour CustomControl pour View (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[ScriptBlock, élément pour SelectionCondition pour CustomControl pour View (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Élément SelectionSetName pour SelectionCondition pour un contrôle personnalisé pour View (format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[TypeName, élément pour SelectionCondition pour CustomControl pour View (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[EntrySelectedBy, élément pour CustomEntry pour CustomControl pour View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
