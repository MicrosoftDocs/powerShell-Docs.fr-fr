---
title: Des frames élément pour CustomItem pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862975"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Frame, élément pour CustomItem pour Controls pour Configuration (Format)

Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de CustomItem Configuration (Format) pour CustomEntry pour les contrôles d’élément de Frame de Configuration pour CustomItem pour les contrôles de Configuration (Format)

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
|[Élément FirstLineHanging pour Frame pour les contrôles de Configuration (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche.|
|[Élément FirstLineIndent pour Frame pour les contrôles de Configuration (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères la première ligne de données est décalée vers la droite.|
|[Élément Macintosh pour Frame pour les contrôles de Configuration (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères les données s’éloigne de la marge de gauche.|
|[Élément RightIndent pour Frame pour les contrôles de Configuration (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères les données s’éloigne de la marge de droite.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomItem pour CustomEntry pour les contrôles de Configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Définit les données affichées par le contrôle et comment il est affiché.|

## <a name="remarks"></a>Remarques

Vous ne pouvez pas spécifier le [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) éléments dans le même `Frame` élément.

## <a name="see-also"></a>Voir aussi

[Élément FirstLineHanging pour Frame pour les contrôles de Configuration (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Élément FirstLineIndent pour Frame pour les contrôles de Configuration (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[Élément Macintosh pour Frame pour les contrôles de Configuration (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[Élément RightIndent pour Frame pour les contrôles de Configuration (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[Élément CustomItem pour CustomEntry pour les contrôles de Configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
