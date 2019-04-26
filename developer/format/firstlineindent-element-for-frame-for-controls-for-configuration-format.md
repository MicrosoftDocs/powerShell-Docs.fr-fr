---
title: Élément FirstLineIndent pour Frame pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065986"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a>FirstLineIndent, élément pour Frame pour Controls pour Configuration (Format)

Spécifie le nombre de caractères la première ligne de données est décalée vers la droite. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de CustomItem Configuration (Format) pour CustomEntry pour les contrôles d’élément de Frame de Configuration pour CustomItem pour les contrôles d’élément de FirstLineIndent Configuration (Format) pour le Frame pour les contrôles de Configuration (Format)

## <a name="syntax"></a>Syntaxe

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent des attributs, éléments enfants et élément parent de la `FirstLineIndent` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de frame pour CustomItem pour les contrôles de Configuration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nombre de caractères que vous souhaitez déplacer la première ligne des données.

## <a name="remarks"></a>Remarques

Si cet élément est spécifié, vous ne pouvez pas spécifier le [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) élément.

## <a name="see-also"></a>Voir aussi

[Élément FirstLineHanging pour Frame pour les contrôles de Configuration (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Élément de frame pour CustomItem pour les contrôles de Configuration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
