---
title: Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3bfd3efe916b4d88c024de8f959482cab515f777
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781220"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)

Définit la condition qui doit exister pour que ce contrôle soit utilisé. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format), élément CustomItem pour CustomEntry pour les contrôles de l’élément de configuration ExpressionBinding pour CustomItem pour les contrôles de configuration (format) ItemSelectionCondition élément pour ExpressionBinding pour les contrôles de configuration (format)

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
|[PropertyName, élément de ItemSelectionCondition pour les contrôles de configuration (format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET qui déclenche la condition.|
|[Élément ScriptBlock pour ItemSelectionCondition pour les contrôles de configuration (format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Définit les données affichées par le contrôle.|

## <a name="remarks"></a>Notes

Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.

## <a name="see-also"></a>Voir aussi

[PropertyName, élément de ItemSelectionCondition pour les contrôles de configuration (format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Élément ScriptBlock pour ItemSelectionCondition pour les contrôles de configuration (format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
