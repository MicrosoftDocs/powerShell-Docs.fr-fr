---
title: Développez l’élément (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066003"
---
# <a name="expand-element-format"></a>Expand, élément (Format)

Spécifie la façon dont l’objet de collection est développé pour cette définition.

Configuration élément (Format) élément DefaultSettings (Format) EnumerableExpansions (Format) EnumerableExpansion élément (Format) développez l’élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Expand` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément EnumerableExpansion (Format)](./enumerableexpansion-element-format.md)|Définit des collection .NET façon dont certains objets sont développés lorsqu’ils sont affichés dans une vue.|

## <a name="text-value"></a>Valeur de texte

Spécifiez l’une des valeurs suivantes :

- EnumOnly : Affiche uniquement les propriétés des objets dans la collection.

- CoreOnly : Affiche uniquement les propriétés de l’objet de collection.

- Les deux : Affiche les propriétés des objets dans la collection et les propriétés de l’objet de collection.

## <a name="remarks"></a>Remarques

Cet élément est utilisé pour définir l’affichent des objets de collection et les objets dans la collection. Dans ce cas, un objet de collection fait référence à n’importe quel objet qui prend en charge la **System.Collections.ICollection** interface.

Le comportement par défaut consiste à afficher uniquement les propriétés des objets dans la collection.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
