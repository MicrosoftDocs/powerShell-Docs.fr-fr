---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour ItemSelectionCondition pour GroupBy (Format)
description: PropertyName, élément pour ItemSelectionCondition pour GroupBy (Format)
ms.openlocfilehash: 9667a389ded33d0744f0f7f8d739635a8b21d98b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666108"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a>PropertyName, élément pour ItemSelectionCondition pour GroupBy (Format)

Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour l’élément GroupBy (format) CustomItem pour CustomEntry pour GroupBy (format) élément ExpressionBinding pour CustomItem pour l’élément GroupBy (format) ItemSelectionCondition pour ExpressionBinding pour l’élément GroupBy (format) PropertyName pour ItemSelectionCondition pour GroupBy (format)

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
|[ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Définit la condition qui doit exister pour que ce contrôle soit utilisé.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom de la propriété .NET qui déclenche la condition.

## <a name="remarks"></a>Notes

Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) lors de la définition de la condition de sélection.

## <a name="see-also"></a>Voir aussi

[ScriptBlock, élément pour ItemSelectionCondition pour GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
