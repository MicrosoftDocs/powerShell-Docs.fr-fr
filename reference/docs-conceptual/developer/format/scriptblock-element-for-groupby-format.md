---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour GroupBy (Format)
description: ScriptBlock, élément pour GroupBy (Format)
ms.openlocfilehash: 117cbef93889046626741449886a1caaa39815cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665238"
---
# <a name="scriptblock-element-for-groupby-format"></a>ScriptBlock, élément pour GroupBy (Format)

Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément d’affichage (format) ScriptBlock pour GroupBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[GroupBy, élément pour View (Format)](./groupby-element-for-view-format.md)|Définit le mode d’affichage d’un groupe d’objets .NET.|

## <a name="text-value"></a>Valeur texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Notes

PowerShell démarre un nouveau groupe chaque fois que la valeur de ce script change.

Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [PropertyName](propertyname-element-for-groupby-format.md) pour démarrer un nouveau groupe.

## <a name="see-also"></a>Voir aussi

[PropertyName, élément pour GroupBy (Format)](propertyname-element-for-groupby-format.md)

[GroupBy, élément pour View (Format)](groupby-element-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](writing-a-powershell-formatting-file.md)
