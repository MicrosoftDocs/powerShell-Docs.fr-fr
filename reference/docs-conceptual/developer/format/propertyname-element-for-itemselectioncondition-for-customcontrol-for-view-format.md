---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour ItemSelectionCondition pour CustomControl pour View (Format)
description: PropertyName, élément pour ItemSelectionCondition pour CustomControl pour View (Format)
ms.openlocfilehash: 5687bb781ce2db27b875f829147ee8b436f04adc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666125"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>PropertyName, élément pour ItemSelectionCondition pour CustomControl pour View (Format)

Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour la vue (format) CustomItem, élément de CustomEntry pour l’élément ExpressionBinding View (format) de CustomItem pour CustomControl pour la vue (format) élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour l’élément View (format) PropertyName pour ItemSelectionCondition pour CustomControl pour View (format

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
|[Élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Définit la condition qui doit exister pour que ce contrôle soit utilisé.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom de la propriété .NET qui déclenche la condition.

## <a name="remarks"></a>Notes

Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) lors de la définition de la condition de sélection.

## <a name="see-also"></a>Voir aussi

[ScriptBlock, élément pour ItemSelectionCondition pour CustomControl pour View (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[Élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
