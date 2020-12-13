---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour ItemSelectionCondition pour Controls pour View (Format)
description: ScriptBlock, élément pour ItemSelectionCondition pour Controls pour View (Format)
ms.openlocfilehash: c005215f7b7984541806d2f5de47372d536787ff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665196"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a>ScriptBlock, élément pour ItemSelectionCondition pour Controls pour View (Format)

Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour la vue (format) élément CustomControl pour le contrôle des contrôles pour l’élément View (format) CustomEntries pour CustomControl pour l’élément CustomEntry (format) de la vue CustomEntries pour les contrôles pour l’élément CustomItem View (format) pour CustomEntry pour les contrôles pour l’élément ExpressionBinding (format) View pour CustomItem pour les contrôles pour l’élément View (format) ItemSelectionCondition de l’élément ExpressionBinding pour les contrôles pour l’élément ScriptBlock View (format) pour ItemSelectionCondition pour les contrôles pour View (format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Définit la condition qui doit exister pour que ce contrôle soit utilisé.|

## <a name="text-value"></a>Valeur texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Notes

Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) lors de la définition de la condition de sélection.

## <a name="see-also"></a>Voir aussi

[PropertyName, élément pour ItemSelectionCondition pour Controls pour View (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
