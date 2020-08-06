---
title: Élément SelectionCondition pour EntrySelectedBy pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1c14b2638249bdbfe25f7a96e917d66ea10ed239
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787578"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)

Définit une condition qui doit exister pour que la définition de contrôle soit utilisée. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour les contrôles pour l’élément d’affichage (format) CustomEntry pour CustomEntries pour les contrôles de l’élément EntrySelectedBy (format) pour CustomEntry pour les contrôles de l’élément View (format) SelectionCondition pour les contrôles pour View (format)

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
|[PropertyName, élément pour SelectionCondition pour Controls pour View (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie une propriété .NET qui déclenche la condition.|
|[ScriptBlock, élément pour SelectionCondition pour Controls pour View (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|
|[SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie l’ensemble des types .NET qui déclenchent la condition.|
|[TypeName, élément pour SelectionCondition pour Controls pour View (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.|

## <a name="remarks"></a>Notes

Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :

- La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.

- La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.

Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[PropertyName, élément pour SelectionCondition pour Controls pour View (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[ScriptBlock, élément pour SelectionCondition pour Controls pour View (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[TypeName, élément pour SelectionCondition pour Controls pour View (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
