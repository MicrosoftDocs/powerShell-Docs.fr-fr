---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)
description: ScriptBlock, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)
ms.openlocfilehash: 853130da4489e571d7f4026a8d65d029d1889f9b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665222"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>ScriptBlock, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)

Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément CustomItem pour CustomEntry pour les contrôles de l’élément ExpressionBinding de configuration pour CustomItem pour les contrôles pour la configuration (format) ItemSelectionCondition élément pour ExpressionBinding pour les contrôles de configuration (format) élément ScriptBlock pour ItemSelectionCondition pour les contrôles de configuration (format)

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
|[ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Définit la condition qui doit exister pour que ce contrôle soit utilisé.|

## <a name="text-value"></a>Valeur texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Notes

Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) lors de la définition de la condition de sélection.

## <a name="see-also"></a>Voir aussi

[PropertyName, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
