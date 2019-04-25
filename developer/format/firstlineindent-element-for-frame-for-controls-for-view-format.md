---
title: Élément FirstLineIndent pour Frame pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066020"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a>FirstLineIndent, élément pour Frame pour Controls pour View (Format)

Spécifie le nombre de caractères la première ligne de données est décalée vers la droite. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles d’élément de CustomItem vue (Format) pour CustomEntry pour les contrôles d’élément de Frame de vue (Format) pour CustomItem pour les contrôles d’élément de FirstLineIndent vue (Format) du cadre des contrôles de vue (Format)

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
|[Élément de frame pour CustomItem pour les contrôles de vue (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nombre de caractères que vous souhaitez déplacer la première ligne des données.

## <a name="remarks"></a>Remarques

Si cet élément est spécifié, vous ne pouvez pas spécifier le [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) élément.

## <a name="see-also"></a>Voir aussi

[Élément FirstLineHanging pour Frame pour les contrôles de vue (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Élément de frame pour CustomItem pour les contrôles de vue (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
