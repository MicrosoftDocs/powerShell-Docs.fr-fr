---
title: Élément PropertyName pour ItemSelectionCondition pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857625"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a>PropertyName, élément pour ItemSelectionCondition pour Controls pour View (Format)

Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie, et le contrôle est utilisé. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour les contrôles d’élément de ExpressionBinding vue (Format) pour CustomItem pour les contrôles de vue (Format) Élément ItemSelectionCondition de ExpressionBinding pour les contrôles d’élément de PropertyName vue (Format) pour ItemSelectionCondition pour les contrôles de vue (Format)

## <a name="syntax"></a>Syntaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ItemSelectionCondition de ExpressionBinding pour les contrôles de vue (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Définit la condition qui doit exister pour ce contrôle à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de la propriété .NET qui déclenche la condition.

## <a name="remarks"></a>Remarques

Si cet élément est utilisé, vous ne pouvez pas spécifier le [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) élément lors de la définition de la condition de sélection.

## <a name="see-also"></a>Voir aussi

[Élément ScriptBlock pour ItemSelectionCondition pour les contrôles de vue (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Élément ItemSelectionCondition de ExpressionBinding pour les contrôles de vue (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
