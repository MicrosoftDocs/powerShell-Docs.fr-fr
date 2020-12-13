---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)
description: PropertyName, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)
ms.openlocfilehash: 860683eb54b2a3579767640c1d3f0937897b8f8e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655121"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>PropertyName, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)

Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de CustomItem, élément de configuration (format) pour CustomEntry pour les contrôles de l’élément de configuration ExpressionBinding pour CustomItem pour les contrôles de configuration (format) ItemSelectionCondition, élément pour ExpressionBinding pour les contrôles de configuration (format) PropertyName, élément pour ItemSeclectionCondition pour les contrôles de configuration (format)

## <a name="syntax"></a>Syntaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Définit la condition qui doit exister pour que ce contrôle soit utilisé.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom de la propriété .NET qui déclenche la condition.

## <a name="remarks"></a>Notes

Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) lors de la définition de la condition de sélection.

## <a name="see-also"></a>Voir aussi

[ScriptBlock, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
