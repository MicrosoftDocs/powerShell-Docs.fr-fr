---
title: Élément PropertyName pour ItemSelectionCondition pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c6517b8f63e0511ce071926ac3ac39ba82e7ed21
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783481"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a>PropertyName, élément pour ItemSelectionCondition pour Controls pour View (Format)

Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour la vue (format) élément CustomControl pour le contrôle des contrôles pour l’élément View (format) CustomEntries pour CustomControl pour l’élément CustomEntry (format) de la vue CustomEntries pour les contrôles pour l’élément CustomItem View (format) pour CustomEntry pour les contrôles pour l’élément ExpressionBinding (format) View pour CustomItem pour les contrôles pour l’élément View (format) ItemSelectionCondition de l’élément ExpressionBinding pour les contrôles pour l’élément View (format) PropertyName pour ItemSelectionCondition pour les contrôles pour View (format)

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
|[Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Définit la condition qui doit exister pour que ce contrôle soit utilisé.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom de la propriété .NET qui déclenche la condition.

## <a name="remarks"></a>Notes

Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) lors de la définition de la condition de sélection.

## <a name="see-also"></a>Voir aussi

[ScriptBlock, élément pour ItemSelectionCondition pour Controls pour View (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
