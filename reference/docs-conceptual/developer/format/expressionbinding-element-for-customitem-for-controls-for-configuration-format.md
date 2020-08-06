---
title: Élément ExpressionBinding pour CustomItem pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1ad83fa9d915822eaefb490658f8a219defdddf2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773910"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)

Définit les données affichées par le contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) Controls, élément de configuration (format), élément de contrôle pour la configuration (format) CustomControl, élément de Control pour configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément CustomItem pour CustomEntry pour les contrôles pour la configuration (format)

## <a name="syntax"></a>Syntaxe

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ExpressionBinding` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|`CustomControl Element`|Élément facultatif.<br /><br /> Définit un contrôle qui est utilisé par ce contrôle.|
|[CustomControlName, élément pour ExpressionBinding pour Controls pour Configuration (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le nom d’un contrôle commun ou d’un contrôle View.|
|[EnumerateCollection, élément pour ExpressionBinding pour Controls pour Configuration (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie que les éléments des collections sont affichés par le contrôle.|
|[ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour que ce contrôle commun soit utilisé.|
|[PropertyName, élément pour ExpressionBinding pour Controls pour Configuration (Format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET dont la valeur est affichée par le contrôle commun.|
|[ScriptBlock, élément pour ExpressionBinding pour Controls pour Configuration (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le script dont la valeur est affichée par le contrôle commun.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomItem pour CustomEntry pour les contrôles de configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.|

## <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Élément CustomItem pour CustomEntry pour les contrôles de configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
