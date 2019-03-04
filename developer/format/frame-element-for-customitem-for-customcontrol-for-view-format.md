---
title: Des frames élément pour CustomItem pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: a7ee550527ec1cb00b4ed83478992c7ab54dbdb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861705"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Frame, élément pour CustomItem pour CustomControl pour View (Format)

Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour l’élément d’affichage (Format) de CustomItem pour CustomEntry d’élément de Frame CutomControlView (Format) pour CustomItem pour CustomControl de vue (Format)

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
|[Élément de FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche.|
|[Élément de FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères la première ligne de données est décalée vers la droite.|
|[Élément de Macintosh](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères les données s’éloigne de la marge de gauche.|
|[Élément de RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères les données s’éloigne de la marge de droite.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomItem pour CustomEntry pour la vue (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Définit les données affichées par le contrôle et comment il est affiché.|

## <a name="remarks"></a>Remarques

Vous ne pouvez pas spécifier le [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) éléments dans le même `Frame` élément.

## <a name="see-also"></a>Voir aussi

[Élément de FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Élément de FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Élément de Macintosh](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[Élément de RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[Élément CustomItem pour CustomEntry pour la vue (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
