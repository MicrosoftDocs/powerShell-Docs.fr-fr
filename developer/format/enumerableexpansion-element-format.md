---
title: Élément EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856835"
---
# <a name="enumerableexpansion-element-format"></a>EnumerableExpansion, élément (Format)

Définit des collection .NET façon dont certains objets sont développés lorsqu’ils sont affichés dans une vue.

Configuration élément (Format) élément DefaultSettings (Format) EnumerableExpansions (Format) EnumerableExpansion élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `EnumerableExpansion` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Élément facultatif.<br /><br /> Définit les objets de collection .NET sont développées par cette définition.|
|[Développez l’élément (Format)](./expand-element-format.md)|Spécifie la façon dont l’objet de collection est développé pour cette définition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément EnumerableExpansions (Format)](./enumerableexpansions-element-format.md)|Définit les différentes façons de cette collection .NET objets sont développés lorsqu’ils sont affichés dans une vue.|

## <a name="remarks"></a>Remarques

Cet élément est utilisé pour définir l’affichent des objets de collection et les objets dans la collection. Dans ce cas, un objet de collection fait référence à n’importe quel objet qui prend en charge la **System.Collections.ICollection** interface.

Le comportement par défaut consiste à afficher uniquement les propriétés des objets dans la collection.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
