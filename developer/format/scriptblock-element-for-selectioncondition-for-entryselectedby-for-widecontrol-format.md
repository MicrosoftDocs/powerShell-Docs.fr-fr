---
title: Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064320"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour WideControl (Format)

Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie, et la définition de l’entrée large est utilisée.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément WideControl (Format) élément WideEntries (Format) élément WideEntry (Format) EntrySelectedBy élément pour l’élément de SelectionCondition WideEntry (Format) pour EntrySelectedBy pour WideEntry (Format), élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)

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
|[Élément SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Définit la condition qui doit exister pour cette définition à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Remarques

La condition de sélection doit spécifier au moins un nom de script ou une propriété à évaluer, mais vous ne pouvez pas spécifier à la fois. Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [Affichage large](./creating-a-wide-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md)

[Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Élément SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
