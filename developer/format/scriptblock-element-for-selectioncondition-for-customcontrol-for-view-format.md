---
title: Élément ScriptBlock pour SelectionCondition pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857415"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a>ScriptBlock, élément pour SelectionCondition pour CustomControl pour View (Format)

Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie et que la définition est utilisée. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) CustomControl élément pour élément d’affichage (Format) de CustomEntries pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour CustomControl pour la vue ( Format), élément CustomItem pour CustomEntry pour CustomControl pour l’élément d’affichage (Format) de SelectionCondition pour EntrySelectedBy pour CustomControl pour élément ScriptBlock de vue (Format) pour SelectionCondition pour CustomControl de vue (Format)

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
|[Élément SelectionCondition pour EntrySelectedBy pour CustomControl de vue (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Définit une condition qui doit exister pour la définition du contrôle à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Remarques

La condition de sélection doit spécifier un moins un script ou le nom à évaluer, mais vous ne pouvez pas spécifier à la fois. Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Élément SelectionCondition pour EntrySelectedBy pour CustomControl de vue (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
