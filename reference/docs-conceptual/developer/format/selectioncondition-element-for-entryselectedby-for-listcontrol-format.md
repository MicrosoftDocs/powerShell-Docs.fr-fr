---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)
description: SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)
ms.openlocfilehash: e93499691dd0046265e43abd26497b2974546083
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655096"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)

Définit la condition qui doit exister pour utiliser cette définition de la vue liste. Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour une définition de liste.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)

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
|[PropertyName, élément de SelectionCondition pour EntrySelectedBy pour ListEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET qui déclenche la condition.|
|[Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|
|[SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|Élément facultatif.<br /><br /> Spécifie l’ensemble des types .NET qui déclenchent la condition.|
|[Élément TypeName pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour TableRowEntry (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Définit les types .NET qui utilisent cette entrée de table ou la condition qui doit exister pour que cette entrée soit utilisée.|

## <a name="remarks"></a>Notes

lWhen vous définissez une condition de sélection, les conditions suivantes s’appliquent :

- La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.

- La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.

Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur les autres composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue de liste](./creating-a-list-view.md)

[Définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md)

[Élément ListEntry (format)](./listentry-element-for-listcontrol-format.md)

[Élément SelectionSetName pour EntrySelectedBy pour ListEntry (format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Élément TypeName pour EntrySelectedBy pour ListEntry (format)](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
