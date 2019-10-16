---
title: Élément ExpressionBinding pour CustomItem pour CustomControl pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363148"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)

Définit les données affichées par le contrôle. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour l’élément View (format) CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour CustomControl pour View ( Format) élément CustomItem pour CustomEntry pour CustomControl pour la vue (format) élément ExpressionBinding pour CustomItem pour CustomControl pour View (format)

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

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ExpressionBinding`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|`CustomControl Element`|Élément facultatif.<br /><br /> Définit un contrôle qui est utilisé par ce contrôle.|
|[Élément CustomControlName pour ExpressionBinding pour CustomControl pour View (format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nom d’un contrôle commun ou d’un contrôle View.|
|[Élément EnumerateCollection pour ExpressionBinding pour CustomControl pour View (format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie que les éléments des collections sont affichés.|
|[Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour que ce contrôle soit utilisé.|
|[Élément PropertyName pour ExpressionBinding pour CustomControl pour View (format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET dont la valeur est affichée par le contrôle.|
|[Élément ScriptBlock pour ExpressionBinding pour CustomCustomControl pour View (format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le script dont la valeur est affichée par le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomItem pour CustomEntry pour CustomControl pour View (format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.|

## <a name="remarks"></a>Remarks

## <a name="see-also"></a>Voir aussi

[Élément CustomControlName pour ExpressionBinding pour CustomControl pour View (format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Élément EnumerateCollection pour ExpressionBinding pour CustomControl pour View (format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Élément PropertyName pour ExpressionBinding pour CustomControl pour View (format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Élément ScriptBlock pour ExpressionBinding pour CustomControl pour View (format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Élément CustomItem pour CustomEntry pour CustomControl pour View (format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
