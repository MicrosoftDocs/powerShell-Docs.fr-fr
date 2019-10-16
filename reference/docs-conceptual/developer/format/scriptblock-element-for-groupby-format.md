---
title: Élément ScriptBlock pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364928"
---
# <a name="scriptblock-element-for-groupby-format"></a>ScriptBlock, élément pour GroupBy (Format)

Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément d’affichage (format) ScriptBlock pour GroupBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ScriptBlock`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[GroupBy, élément de View (format)](./groupby-element-for-view-format.md)|Définit le mode d’affichage d’un groupe d’objets .NET.|

## <a name="text-value"></a>Valeur texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Remarks

PowerShell démarre un nouveau groupe chaque fois que la valeur de ce script change.

Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [PropertyName](propertyname-element-for-groupby-format.md) pour démarrer un nouveau groupe.

## <a name="see-also"></a>Voir aussi

[PropertyName, élément de GroupBy (format)](propertyname-element-for-groupby-format.md)

[GroupBy, élément de View (format)](groupby-element-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](writing-a-powershell-formatting-file.md)
