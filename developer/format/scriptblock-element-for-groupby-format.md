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
ms.openlocfilehash: f2f6b9af7740b1231881294c2f32bf97b5a1568b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054423"
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

Windows PowerShell démarre un nouveau groupe chaque fois que la valeur de ce script change.

Lorsque cet élément est spécifié, vous ne pouvez pas spécifier le [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) élément pour démarrer un nouveau groupe.

## <a name="see-also"></a>Voir aussi

[Élément PropertyName pour GroupBy (Format)](./propertyname-element-for-groupby-format.md)

[Élément GroupBy de vue (Format)](./groupby-element-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
