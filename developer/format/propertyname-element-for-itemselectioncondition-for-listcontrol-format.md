---
title: Élément PropertyName pour ItemSelectionCondition pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855535"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>PropertyName, élément pour ItemSelectionCondition pour ListControl (Format)

Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie, et la vue est utilisée. Cet élément est utilisé lors de la définition d’un affichage de liste.

Configuration élément (Format) ViewDefinitions, élément (Format) vue (Format) d’élément objet ListControl, élément (Format) situés (Format) ListEntry élément d’élément de ListItems ListControl (Format) pour ListEntry pour ListControl (Format) ListItem Élément pour ListItems d’élément de ItemSelectionCondition ListControl (Format) pour ListItem pour objets ListControls PropertyName élément pour ItemSelectionCondition pour ListControl (Format)

## <a name="syntax"></a>Syntaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et les éléments parents de la `PropertyName` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ItemSelectionCondition pour ListItem pour un objet ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de la propriété dont la valeur est affichée.

## <a name="remarks"></a>Remarques

Si cet élément est utilisé, vous ne pouvez pas spécifier le [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) élément lors de la définition de la condition de sélection.

## <a name="see-also"></a>Voir aussi

[Élément ScriptBlock pour ItemSelectionCondition pour ListIControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Élément ItemSelectionCondition pour ListItem pour un objet ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
