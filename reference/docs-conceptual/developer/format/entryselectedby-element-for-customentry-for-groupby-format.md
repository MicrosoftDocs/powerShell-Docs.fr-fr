---
title: Élément EntrySelectedBy pour CustomEntry pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363858"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)

Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format) élément EntrySelectedBy pour CustomEntry pour GroupBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `EntrySelectedBy`. Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition. Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour que cette définition soit utilisée.|
|[Élément SelectionSetName pour EntrySelectedBy pour GroupBy (format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.|
|[Élément TypeName pour EntrySelectedBy pour GroupBy (format)](./typename-element-for-entryselectedby-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition du contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomControl pour GroupBy (format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Fournit une définition du contrôle.|

## <a name="remarks"></a>Remarks

Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou lorsqu’une valeur de propriété ou un script spécifique prend la valeur `true`. Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Élément SelectionSetName pour EntrySelectedBy pour GroupBy (format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[Élément TypeName pour EntrySelectedBy pour GroupBy (format)](./typename-element-for-entryselectedby-for-groupby-format.md)

[Élément CustomEntry pour CustomEntries pour les contrôles pour View (format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
