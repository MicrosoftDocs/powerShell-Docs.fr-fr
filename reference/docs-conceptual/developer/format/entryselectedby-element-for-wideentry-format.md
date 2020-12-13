---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy, élément pour WideEntry (Format)
description: EntrySelectedBy, élément pour WideEntry (Format)
ms.openlocfilehash: 246a1967300ab0551f376c4799deac275068308c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660249"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>EntrySelectedBy, élément pour WideEntry (Format)

Définit les types .NET qui utilisent cette définition de la vue étendue ou de la condition qui doit exister pour que cette définition soit utilisée.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) EntrySelectedBy, élément pour WideEntry (format)

## <a name="syntax"></a>Syntaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour cette définition de vue étendue à utiliser.|
|[Élément SelectionSetName pour EntrySelectedBy pour WideEntry (format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition de vue étendue.|
|[TypeName, élément pour EntrySelectedBy pour WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition de vue étendue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideEntry (format)](./wideentry-element-for-widecontrol-format.md)|Fournit une définition de la vue étendue.|

## <a name="remarks"></a>Notes

Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition de vue étendue. Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.

Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou une valeur de script spécifique prend la valeur `true` . Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).

## <a name="see-also"></a>Voir aussi

[Élément WideEntry (format)](./wideentry-element-for-widecontrol-format.md)

[Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Élément SelectionSetName pour EntrySelectedBy pour WideEntry (format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[TypeName, élément pour EntrySelectedBy pour WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Création d’une vue large](./creating-a-wide-view.md)

[Définition de conditions pour l’affichage de données](./defining-conditions-for-displaying-data.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
