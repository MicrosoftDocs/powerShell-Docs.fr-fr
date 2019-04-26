---
title: Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065817"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>ItemSelectionCondition, élément pour ExpressionBinding pour CustomControl (Format)

Définit la condition qui doit exister pour ce contrôle à utiliser. Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour un élément de contrôle. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour élément d’affichage (Format) de ExpressionBinding pour CustomItem pour CustomControl pour l’élément de ItemSelectionCondition d’affichage (Format) pour la liaison d’Expression pour CustomControl de vue (Format)

## <a name="syntax"></a>Syntaxe

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ItemSelectionCondition` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément PropertyName pour ItemSelectionCondition pour CustomControl pour (Format d’affichage](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET qui déclenche la condition.|
|[Élément ScriptBlock pour ItemSelectionCondition pour CustomControl de vue (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ExpressionBinding pour CustomItem pour CustomControl de vue (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Définit les données qui sont affichées par le contrôle.|

## <a name="remarks"></a>Remarques

Vous pouvez spécifier un nom de propriété ou un script pour cette condition mais que vous ne pouvez pas spécifier à la fois.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)

[Élément ExpressionBinding pour CustomItem pour CustomControl de vue (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
