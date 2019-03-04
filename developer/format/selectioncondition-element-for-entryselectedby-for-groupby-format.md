---
title: Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855165"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a>SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)

Définit une condition qui doit exister pour une définition de contrôle à utiliser. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de EntrySelectedBy GroupBy (Format) pour CustomEntry d’élément de SelectionCondition GroupBy (Format) pour EntrySelectedBy pour GroupBy (Format)

## <a name="syntax"></a>Syntaxe

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionCondition` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément PropertyName pour SelectionCondition pour GroupBy (Format)](./propertyname-element-for-selectioncondition-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie une propriété .NET qui déclenche la condition.|
|[Élément ScriptBlock pour SelectionCondition pour GroupBy (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|
|[Élément SelectionSetName pour SelectionCondition pour GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le jeu des types .NET qui déclenche la condition.|
|[Élément TypeName pour SelectionCondition pour GroupBy (Format)](./typename-element-for-selectioncondition-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour CustomEntry pour GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser.|

## <a name="remarks"></a>Remarques

Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :

- La condition de sélection doit spécifier un nom d’un propriété minimum ou un bloc de script, mais vous ne pouvez pas spécifier à la fois.

- La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.

Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Élément PropertyName pour SelectionCondition pour CustomControl de vue (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Élément ScriptBlock pour SelectionCondition pour CustomControl de vue (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Élément SelectionSetName pour SelectionCondition pour un contrôle personnalisé pour la vue (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Élément TypeName pour SelectionCondition pour GroupBy (Format)](./typename-element-for-selectioncondition-for-groupby-format.md)

[Élément EntrySelectedBy pour CustomEntry pour GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
