---
title: Élément ExpressionBinding pour CustomItem pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858295"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)

Définit les données qui sont affichées par le contrôle. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour les contrôles d’élément de ExpressionBinding vue (Format) pour CustomItem pour les contrôles de vue (Format)

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
|[Élément CustomControlName pour ExpressionBinding pour les contrôles de vue (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nom d’un contrôle commun ou un contrôle d’affichage.|
|[Élément EnumerateCollection pour ExpressionBinding pour les contrôles de vue (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie que les éléments des collections sont affichés.|
|[Élément ItemSelectionCondition de ExpressionBinding pour les contrôles de vue (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour ce contrôle à utiliser.|
|[Élément PropertyName pour ExpressionBinding pour les contrôles de vue (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET dont la valeur est affichée par le contrôle.|
|[Élément ScriptBlock pour ExpressionBinding pour les contrôles de vue (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le script dont la valeur est affichée par le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomItem pour CustomEntry pour les contrôles de vue (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Définit les données affichées par le contrôle et comment il est affiché.|

## <a name="remarks"></a>Remarques

## <a name="see-also"></a>Voir aussi

[Élément CustomItem pour CustomEntry pour les contrôles de vue (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Élément CustomControlName pour ExpressionBinding pour les contrôles de vue (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Élément EnumerateCollection pour ExpressionBinding pour les contrôles de vue (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[Élément ItemSelectionCondition de ExpressionBinding pour les contrôles de vue (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Élément PropertyName pour ExpressionBinding pour les contrôles de vue (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[Élément ScriptBlock pour ExpressionBinding pour les contrôles de vue (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
