---
title: Élément ExpressionBinding pour CustomItem pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065901"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>ExpressionBinding, élément pour CustomItem pour GroupBy (Format)

Définit les données qui sont affichées par le contrôle. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de CustomItem GroupBy (Format) pour CustomEntry d’élément de ExpressionBinding GroupBy (Format) pour CustomItem pour GroupBy (Format)

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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ExpressionBinding` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|`CustomControl Element`|Élément facultatif.<br /><br /> Définit un contrôle qui est utilisé par ce contrôle.|
|[Élément CustomControlName pour ExpressionBinding pour GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le nom d’un contrôle commun ou un contrôle d’affichage.|
|[Élément EnumerateCollection pour ExpressionBinding pour GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)élément EnumerateCollection pour ExpressionBinding pour GroupBy (Format)|Élément facultatif.<br /><br /> Spécifié que les éléments des collections sont affichés.|
|[Élément ItemSelectionCondition pour ExpressionBinding pour GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour ce contrôle à utiliser.|
|[Élément PropertyName pour ExpressionBinding pour GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET dont la valeur est affichée par le contrôle.|
|[Élément ScriptBlock pour ExpressionBinding pour GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le script dont la valeur est affichée par le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomItem pour CustomEntry pour GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Définit les données affichées par la vue de contrôle personnalisé et comment il est affiché.|

## <a name="see-also"></a>Voir aussi

[Élément CustomControlName pour ExpressionBinding pour GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Élément EnumerateCollection pour ExpressionBinding pour GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[Élément ItemSelectionCondition pour ExpressionBinding pour GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Élément PropertyName pour ExpressionBinding pour GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[Élément ScriptBlock pour ExpressionBinding pour GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[Élément CustomItem pour CustomEntry pour GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
