---
title: Élément FirstLineHanging pour Frame pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 679c8bcb-b49d-4bb4-91f5-ea1af6c217e3
caps.latest.revision: 8
ms.openlocfilehash: 4553f95e48a2b1440c00b4951bea56376b00628a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065884"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a>FirstLineHanging, élément pour Frame pour Controls pour Configuration (Format)

Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de CustomItem Configuration (Format) pour CustomEntry pour les contrôles d’élément de Frame de Configuration pour CustomItem pour les contrôles d’élément de FirstLineHanging Configuration (Format) pour le Frame pour les contrôles de Configuration (Format)

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
|[Élément de frame pour CustomItem pour les contrôles de Configuration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nombre de caractères que vous souhaitez déplacer la première ligne des données.

## <a name="remarks"></a>Remarques

Si cet élément est spécifié, vous ne pouvez pas spécifier le `FirstLineIndent` élément.

## <a name="see-also"></a>Voir aussi

[Élément de frame pour CustomItem pour les contrôles de Configuration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
