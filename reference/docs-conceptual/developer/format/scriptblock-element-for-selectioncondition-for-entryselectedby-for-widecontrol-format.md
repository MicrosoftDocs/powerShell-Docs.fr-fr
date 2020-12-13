---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour WideControl (Format)
description: ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour WideControl (Format)
ms.openlocfilehash: 53d3eba9d453dbcc96afbe8f81a16b61573f2874
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651971"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour WideControl (Format)

Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et la définition d’entrée étendue est utilisée.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) élément SelectionCondition pour EntrySelectedBy pour WideEntry (format) élément ScriptBlock pour SelectionCondition pour EntrySelectedBy (format)

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
|[Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Définit la condition qui doit exister pour que cette définition soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Notes

La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux. Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur les autres composants d’une vue étendue, consultez [vue étendue](./creating-a-wide-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue large](./creating-a-wide-view.md)

[Définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md)

[PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
