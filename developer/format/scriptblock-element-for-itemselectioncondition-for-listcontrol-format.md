---
title: Élément ScriptBlock pour ItemSelectionCondition pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855415"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>ScriptBlock, élément pour ItemSelectionCondition pour ListControl (Format)

Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie, et l’élément de liste est utilisé. Cet élément est utilisé lors de la définition d’un affichage de liste.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément ListControl (Format) situés élément d’élément de ListEntry ListControl (Format) pour situés d’élément de ListItems ListControl (Format) pour ListEntry élément de ListItem ListControl (Format) pour ListItems d’élément de ItemSelectionCondition (Format) de contrôle de liste pour ListItem pour ListControl (Format), élément ScriptBlock pour ItemSelectionCondition pour ListControl (Format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et les éléments parents de la `ScriptBlock` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ItemSelectionCondition pour ListItem pour un objet ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Définit la condition qui doit exister pour cet élément de liste à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Remarques

Si cet élément est utilisé, vous ne pouvez pas spécifier le `PropertyName` élément lors de la définition de la condition de sélection.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
