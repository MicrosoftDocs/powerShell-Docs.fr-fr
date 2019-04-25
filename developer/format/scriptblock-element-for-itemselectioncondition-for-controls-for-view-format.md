---
title: Élément ScriptBlock pour ItemSelectionCondition pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064711"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a>ScriptBlock, élément pour ItemSelectionCondition pour Controls pour View (Format)

Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie, et le contrôle est utilisé. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour les contrôles d’élément de ExpressionBinding vue (Format) pour CustomItem pour les contrôles de vue (Format) Élément ItemSelectionCondition de ExpressionBinding pour les contrôles d’élément ScriptBlock de vue (Format) pour ItemSelectionCondition pour les contrôles de vue (Format)

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
|[Élément ItemSelectionCondition de ExpressionBinding pour les contrôles de vue (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Définit la condition qui doit exister pour ce contrôle à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Remarques

Si cet élément est utilisé, vous ne pouvez pas spécifier le [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) élément lors de la définition de la condition de sélection.

## <a name="see-also"></a>Voir aussi

[Élément PropertyName pour ItemSelectionCondition pour les contrôles de vue (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Élément ItemSelectionCondition de ExpressionBinding pour les contrôles de vue (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
