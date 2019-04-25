---
title: Élément ExpressionBinding pour CustomItem pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065918"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)

Définit les données qui sont affichées par le contrôle. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) CustomControl élément pour élément d’affichage (Format) de CustomEntries pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour CustomControl pour la vue ( Format), élément CustomItem pour CustomEntry pour CustomControl pour élément d’affichage (Format) de ExpressionBinding pour CustomItem pour CustomControl de vue (Format)

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
|[Élément CustomControlName pour ExpressionBinding pour CustomControl de vue (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nom d’un contrôle commun ou un contrôle d’affichage.|
|[Élément EnumerateCollection pour ExpressionBinding pour CustomControl de vue (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifié que les éléments des collections sont affichés.|
|[Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl de vue (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour ce contrôle à utiliser.|
|[Élément PropertyName pour ExpressionBinding pour CustomControl de vue (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET dont la valeur est affichée par le contrôle.|
|[Élément ScriptBlock pour ExpressionBinding pour CustomCustomControl pour la vue (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le script dont la valeur est affichée par le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomItem pour CustomEntry pour CustomControl de vue (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Définit les données affichées par la vue de contrôle personnalisé et comment il est affiché.|

## <a name="remarks"></a>Remarques

## <a name="see-also"></a>Voir aussi

[Élément CustomControlName pour ExpressionBinding pour CustomControl de vue (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Élément EnumerateCollection pour ExpressionBinding pour CustomControl de vue (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl de vue (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Élément PropertyName pour ExpressionBinding pour CustomControl de vue (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Élément ScriptBlock pour ExpressionBinding pour CustomControl de vue (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Élément CustomItem pour CustomEntry pour CustomControl de vue (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
