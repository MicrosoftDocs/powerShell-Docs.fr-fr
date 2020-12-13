---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)
description: ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)
ms.openlocfilehash: ec7691358d0ff3758411317a349221e1704a1895
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659899"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)

Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et l’entrée de liste est utilisée.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionCondition pour EntrySelectedBy pour ListEntry (format) élément ScriptBlock pour SelectionCondition pour ListEntry (format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Définit la condition qui doit exister pour que cette entrée de liste soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Notes

La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux. (Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).)

Pour plus d’informations sur les autres composants d’un affichage de liste, consultez [affichage de liste](./creating-a-list-view.md).

## <a name="see-also"></a>Voir aussi

[Élément ListEntry (format)](./listentry-element-for-listcontrol-format.md)

[PropertyName, élément de SelectionCondition pour EntrySelectedBy pour ListEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Mode liste](./creating-a-list-view.md)

[Définition des conditions d’utilisation d’une entrée ou d’un élément d’une vue](./defining-conditions-for-displaying-data.md)

[Écriture d’un fichier de mise en forme et de types Windows PowerShell](./writing-a-powershell-formatting-file.md)
