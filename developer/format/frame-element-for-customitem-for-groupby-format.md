---
title: Élément des frames pour CustomItem pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854845"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Frame, élément pour CustomItem pour GroupBy (Format)

Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de CustomItem GroupBy (Format) pour CustomEntry d’élément de Frame GroupBy (Format) pour CustomItem pour GroupBy (Format)

## <a name="syntax"></a>Syntaxe

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Frame` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|`CustomItem Element`|Élément requis|
|[Élément FirstLineHanging pour Frame pour GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche.|
|[Élément FirstLineIndent pour Frame pour GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères la première ligne de données est décalée vers la droite.|
|[Élément Macintosh pour Frame pour GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères les données s’éloigne de la marge de gauche.|
|[Élément RightIndent pour Frame pour GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent élément|Élément facultatif.<br /><br /> Spécifie le nombre de caractères les données s’éloigne de la marge de droite.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomItem pour CustomEntry pour GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Définit les données affichées par le contrôle et comment il est affiché.|

## <a name="remarks"></a>Remarques

Vous ne pouvez pas spécifier le [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) éléments dans le même `Frame` élément.

## <a name="see-also"></a>Voir aussi

[Élément FirstLineHanging pour Frame pour GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Élément FirstLineIndent pour Frame pour GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Élément Macintosh pour Frame pour GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md)

[Élément RightIndent pour Frame pour GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)

[Élément CustomItem pour CustomEntry pour GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
