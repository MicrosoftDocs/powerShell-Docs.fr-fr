---
title: Élément FirstLineHanging pour Frame pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858715"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a>FirstLineHanging, élément pour Frame pour Controls pour View (Format)

Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles d’élément de CustomItem vue (Format) pour CustomEntry pour les contrôles d’élément de Frame de vue (Format) pour CustomItem pour les contrôles d’élément de FirstLineHanging vue (Format) de Cadre de contrôles de vue (Format)

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
|[Élément de frame pour CustomItem pour les contrôles de vue (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nombre de caractères que vous souhaitez déplacer la première ligne des données.

## <a name="remarks"></a>Remarques

Si cet élément est spécifié, vous ne pouvez pas spécifier le [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) élément.

## <a name="see-also"></a>Voir aussi

[Élément FirstLineIndent pour Frame pour les contrôles de vue (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[Élément de frame pour CustomItem pour les contrôles de vue (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
