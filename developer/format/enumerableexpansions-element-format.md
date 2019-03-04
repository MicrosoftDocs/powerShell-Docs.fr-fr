---
title: Élément EnumerableExpansions (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860255"
---
# <a name="enumerableexpansions-element-format"></a>EnumerableExpansions, élément (Format)

Définit comment les objets de collection .NET sont développés lorsqu’ils sont affichés dans une vue.

Configuration élément (Format) DefaultSettings (Format) EnumerableExpansions élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `EnumerableExpansions` élément. Il n’existe aucune limite au nombre d’éléments enfants que vous pouvez utiliser.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément EnumerableExpansion (Format)](./enumerableexpansion-element-format.md)|Élément facultatif.<br /><br /> Définit les objets de collection .NET spécifiques qui sont développés lorsqu’ils sont affichés dans une vue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément DefaultSettings (Format)](./defaultsettings-element-format.md)|Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.|

## <a name="remarks"></a>Remarques

Cet élément est utilisé pour définir l’affichent des objets de collection et les objets dans la collection. Dans ce cas, un objet de collection fait référence à n’importe quel objet qui prend en charge la **System.Collections.ICollection** interface.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
