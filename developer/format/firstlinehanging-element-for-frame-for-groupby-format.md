---
title: Élément FirstLineHanging pour Frame pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065822"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>FirstLineHanging, élément pour Frame pour GroupBy (Format)

Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de CustomItem GroupBy (Format) pour CustomEntry d’élément de Frame GroupBy (Format) pour CustomItem d’élément de FirstLineHanging GroupBy (Format) pour le Frame pour GroupBy (Format)

## <a name="syntax"></a>Syntaxe

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent des attributs, éléments enfants et élément parent de la `FirstLineHanging` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de frame pour CustomItem pour GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nombre de caractères que vous souhaitez déplacer la première ligne des données.

## <a name="remarks"></a>Remarques

Si cet élément est spécifié, vous ne pouvez pas spécifier le [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) élément.

## <a name="see-also"></a>Voir aussi

[Élément FirstLineIndent pour Frame pour GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Élément de frame pour CustomItem pour GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
