---
title: Élément ScriptBlock pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229326"
---
# <a name="scriptblock-element-for-groupby-format"></a>ScriptBlock, élément pour GroupBy (Format)

Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.

Configuration élément (Format) élément ViewDefinitions (Format) élément (Format) GroupBy élément d’affichage pour l’élément ScriptBlock de vue (Format) pour GroupBy (Format)

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
|[Élément GroupBy de vue (Format)](./groupby-element-for-view-format.md)|Définit la façon dont un groupe d’objets .NET est affiché.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Remarques

PowerShell démarre un nouveau groupe chaque fois que la valeur de ce script change.

Lorsque cet élément est spécifié, vous ne pouvez pas spécifier le [PropertyName](propertyname-element-for-groupby-format.md) élément pour démarrer un nouveau groupe.

## <a name="see-also"></a>Voir aussi

[Élément PropertyName pour GroupBy (Format)](propertyname-element-for-groupby-format.md)

[Élément GroupBy de vue (Format)](groupby-element-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](writing-a-powershell-formatting-file.md)
