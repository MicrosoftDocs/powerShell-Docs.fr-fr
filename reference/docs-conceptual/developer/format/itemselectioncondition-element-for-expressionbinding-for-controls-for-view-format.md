---
title: Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e8e3ea64fd947fbb2b98c410ac08533f386c9505
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781203"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a>ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour View (Format)

Définit la condition qui doit exister pour que ce contrôle soit utilisé. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément CustomEntries View (format) pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour les contrôles de l’élément View (format) CustomItem pour CustomEntry pour les contrôles pour l’élément View (format) ExpressionBinding pour les contrôles pour la vue (format) CustomItem élément de ItemSelectionCondition pour les contrôles pour View (format)

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
|[PropertyName, élément pour ItemSelectionCondition pour Controls pour View (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET qui déclenche la condition.|
|[ScriptBlock, élément pour ItemSelectionCondition pour Controls pour View (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Définit les données affichées par le contrôle.|

## <a name="remarks"></a>Notes

Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.

## <a name="see-also"></a>Voir aussi

[PropertyName, élément pour ItemSelectionCondition pour Controls pour View (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ScriptBlock, élément pour ItemSelectionCondition pour Controls pour View (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
