---
title: Élément ExpressionBinding pour CustomItem pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5b0017e487aab4ffcbf901cd44aad9b275b22832
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773723"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>ExpressionBinding, élément pour CustomItem pour GroupBy (Format)

Définit les données affichées par le contrôle. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) CustomItem élément pour CustomEntry pour GroupBy (format) élément ExpressionBinding pour GroupBy (format)

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
|[CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le nom d’un contrôle commun ou d’un contrôle View.|
|[Élément EnumerateCollection pour ExpressionBinding pour GroupBy (format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Élément EnumerateCollection pour ExpressionBinding pour GroupBy (format)|Élément facultatif.<br /><br /> Spécifie que les éléments des collections sont affichés.|
|[ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour que ce contrôle soit utilisé.|
|[PropertyName, élément pour ExpressionBinding pour GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET dont la valeur est affichée par le contrôle.|
|[ScriptBlock, élément pour ExpressionBinding pour GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le script dont la valeur est affichée par le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomItem, élément pour CustomEntry pour GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.|

## <a name="see-also"></a>Voir aussi

[CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[EnumerateCollection, élément pour ExpressionBinding pour GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[PropertyName, élément pour ExpressionBinding pour GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[ScriptBlock, élément pour ExpressionBinding pour GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[CustomItem, élément pour CustomEntry pour GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
