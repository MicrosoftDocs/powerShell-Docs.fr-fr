---
title: Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064371"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)

Spécifie le script qui déclenche la condition.

Configuration élément (Format) élément DefaultSettings (Format) EnumerableExpansions (Format) élément EnumerableExpansion (Format) EntrySelectedBy élément d’élément de SelectionCondition EnumerableExpansion (Format) pour EntrySelectedBy pour Élément de ScriptBlock EnumerableExpansion (Format) pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Définit la condition qui doit exister pour développer la collection d’objets de cette définition.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Remarques

La condition de sélection doit spécifier au moins un nom de script ou une propriété à évaluer, mais vous ne pouvez pas spécifier à la fois. Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md)

[Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
