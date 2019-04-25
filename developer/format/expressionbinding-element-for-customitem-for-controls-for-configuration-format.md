---
title: Élément ExpressionBinding pour CustomItem pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065938"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)

Définit les données qui sont affichées par le contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de CustomItem Configuration (Format) pour CustomEntry pour les contrôles pour l’élément de Configuration ExpressionBinding CustomItem pour les contrôles de Configuration (Format)

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
|[Élément CustomControlName pour ExpressionBinding pour les contrôles de Configuration (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le nom d’un contrôle commun ou un contrôle d’affichage.|
|[Élément EnumerateCollection pour ExpressionBinding pour les contrôles de Configuration (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifié que les éléments des collections sont affichés par le contrôle.|
|[Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de Configuration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour ce contrôle commun à utiliser.|
|[Élément PropertyName pour ExpressionBinding pour les contrôles de Configuration (Format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET dont la valeur est affichée par le contrôle commun.|
|[Élément ScriptBlock pour ExpressionBinding pour les contrôles de Configuration (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le script dont la valeur est affichée par le contrôle commun.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomItem pour CustomEntry pour les contrôles de Configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Définit les données affichées par la vue de contrôle personnalisé et comment il est affiché.|

## <a name="remarks"></a>Remarques

## <a name="see-also"></a>Voir aussi

[Élément CustomItem pour CustomEntry pour les contrôles de Configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
