---
title: Des frames élément pour CustomItem pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065714"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Frame, élément pour CustomItem pour Controls pour View (Format)

Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour les contrôles d’élément de Frame de vue (Format) pour CustomItem pour les contrôles de vue (Format)

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
|[Élément FirstLineHanging du cadre de contrôles de vue (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères la première ligne est décalée vers la gauche.|
|[Élément FirstLineIndent du cadre de contrôles de vue (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères la première ligne est décalée vers la droite.|
|[Élément Macintosh du cadre de contrôles de vue (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères les données s’éloigne de la marge de gauche.|
|[Élément RightIndent du cadre de contrôles de vue (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères les données s’éloigne de la marge de droite.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomItem pour CustomEntry pour les contrôles de vue (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Définit les données affichées par le contrôle et comment il est affiché.|

## <a name="remarks"></a>Remarques

Vous ne pouvez pas spécifier le [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) éléments dans le même `Frame` élément.

## <a name="see-also"></a>Voir aussi

[Élément FirstLineHanging du cadre de contrôles de vue (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Élément FirstLineIndent du cadre de contrôles de vue (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[Élément Macintosh du cadre de contrôles de vue (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[Élément RightIndent du cadre de contrôles de vue (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[Élément CustomItem pour CustomEntry pour les contrôles de vue (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
