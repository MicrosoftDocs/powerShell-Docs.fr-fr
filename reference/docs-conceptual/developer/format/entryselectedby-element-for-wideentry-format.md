---
title: Élément EntrySelectedBy pour WideEntry (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363328"
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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `EntrySelectedBy`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour cette définition de vue étendue à utiliser.|
|[Élément SelectionSetName pour EntrySelectedBy pour WideEntry (format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition de vue étendue.|
|[Élément TypeName pour EntrySelectedBy pour WideEntry (format)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition de vue étendue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideEntry (format)](./wideentry-element-for-widecontrol-format.md)|Fournit une définition de la vue étendue.|

## <a name="remarks"></a>Remarks

Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition de vue étendue. Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.

Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou de script spécifique prend la valeur `true`. Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).

## <a name="see-also"></a>Voir aussi

[Élément WideEntry (format)](./wideentry-element-for-widecontrol-format.md)

[Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Élément SelectionSetName pour EntrySelectedBy pour WideEntry (format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Élément TypeName pour EntrySelectedBy pour WideEntry (format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Création d’un affichage étendu](./creating-a-wide-view.md)

[Définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
