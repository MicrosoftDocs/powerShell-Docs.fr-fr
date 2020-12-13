---
ms.date: 09/13/2016
ms.topic: reference
title: ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)
description: ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)
ms.openlocfilehash: 92120ace5ed316fbfbf1d51422071c27d5a604cf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651976"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)

Définit la condition qui doit exister pour que ce contrôle soit utilisé. Il n’existe pas de limite au nombre de conditions de sélection qui peuvent être spécifiées pour un élément de contrôle. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour la vue (format) CustomControl, élément de GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) CustomItem élément pour CustomEntry pour GroupBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ItemSelectionCondition` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[PropertyName, élément pour ItemSelectionCondition pour GroupBy (Format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET qui déclenche la condition.|
|[ScriptBlock, élément pour ItemSelectionCondition pour GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ExpressionBinding, élément pour CustomItem pour GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Définit les données affichées par le contrôle.|

## <a name="remarks"></a>Notes

Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)

[ExpressionBinding, élément pour CustomItem pour GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)
