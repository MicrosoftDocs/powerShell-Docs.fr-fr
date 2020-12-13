---
ms.date: 09/13/2016
ms.topic: reference
title: ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)
description: ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)
ms.openlocfilehash: 8f4bfef4f6c65c6dabc7a776dda1083bac11fdf7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648191"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)

Définit les données affichées par le contrôle. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour la vue (format) élément CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour CustomControl pour la vue (format) CustomItem élément pour CustomControl pour la vue (format), élément CustomEntry pour CustomControl pour la vue (format)

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
|[CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nom d’un contrôle commun ou d’un contrôle View.|
|[EnumerateCollection, élément pour ExpressionBinding pour CustomControl pour View (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie que les éléments des collections sont affichés.|
|[Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour que ce contrôle soit utilisé.|
|[PropertyName, élément pour ExpressionBinding pour CustomControl pour View (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET dont la valeur est affichée par le contrôle.|
|[Élément ScriptBlock pour ExpressionBinding pour CustomCustomControl pour View (format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le script dont la valeur est affichée par le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomItem, élément pour CustomEntry pour CustomControl pour View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.|

## <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[EnumerateCollection, élément pour ExpressionBinding pour CustomControl pour View (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[PropertyName, élément pour ExpressionBinding pour CustomControl pour View (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ScriptBlock, élément pour ExpressionBinding pour CustomControl pour View (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomItem, élément pour CustomEntry pour CustomControl pour View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
