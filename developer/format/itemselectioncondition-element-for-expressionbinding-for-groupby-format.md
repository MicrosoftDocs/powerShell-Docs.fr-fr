---
title: Élément ItemSelectionCondition pour ExpressionBinding pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853135"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)

Définit la condition qui doit exister pour ce contrôle à utiliser. Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour un élément de contrôle. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de CustomItem GroupBy (Format) pour CustomEntry d’élément de ExpressionBinding GroupBy (Format) pour CustomItem d’élément de ItemSelectionCondition GroupBy (Format) pour ExpressionBinding pour GroupBy (Format)

## <a name="syntax"></a>Syntaxe

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ItemSelectionCondition` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément PropertyName pour ItemSelectionCondition pour GroupBy (Format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET qui déclenche la condition.|
|[Élément ScriptBlock pour ItemSelectionCondition pour GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ExpressionBinding pour CustomItem pour GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Définit les données qui sont affichées par le contrôle.|

## <a name="remarks"></a>Remarques

Vous pouvez spécifier un nom de propriété ou un script pour cette condition mais que vous ne pouvez pas spécifier à la fois.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)

[Élément ExpressionBinding pour CustomItem pour GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)
