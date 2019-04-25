---
title: Élément ScriptBlock pour ItemSelectionCondition pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064473"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>ScriptBlock, élément pour ItemSelectionCondition pour CustomControl pour View (Format)

Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie, et le contrôle est utilisé. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour élément d’affichage (Format) de ExpressionBinding pour CustomItem pour CustomControl pour l’élément de ItemSelectionCondition d’affichage (Format) pour la liaison d’Expression pour CustomControl pour élément ScriptBlock de vue (Format) pour ItemSelectionCondition pour CustomControl de vue (Format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ItemSelectionCondition pour la liaison d’Expression pour CustomControl de vue (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Définit la condition qui doit exister pour ce contrôle à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Remarques

Si cet élément est utilisé, vous ne pouvez pas spécifier le [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) élément lors de la définition de la condition de sélection.

## <a name="see-also"></a>Voir aussi

[Élément PropertyName pour ItemSelectionCondition pour CustomControl de vue (Format)](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[Élément ItemSelectionCondition pour la liaison d’Expression pour CustomControl de vue (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
