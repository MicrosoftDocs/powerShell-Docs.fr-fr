---
title: Élément FirstLineIndent pour Frame pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 9ec6caedcb7cf20d4aab2216cd8a9707269d9452
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854955"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>FirstLineIndent, élément pour Frame pour CustomControl pour View (Format)

Spécifie le nombre de caractères la première ligne de données est décalée vers la droite. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour l’élément d’affichage (Format) de CustomItem pour CustomEntry d’élément de Frame CutomControlView (Format) pour CustomItem pour CustomControl pour l’élément d’affichage (Format) de FirstLineIndent

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
|[Élément de frame pour CustomItem pour CustomControl de vue (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nombre de caractères que vous souhaitez déplacer la première ligne des données.

## <a name="remarks"></a>Remarques

Si cet élément est spécifié, vous ne pouvez pas spécifier le [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) élément.

## <a name="see-also"></a>Voir aussi

[Élément FirstLineHanging pour Frame pour CustomControl de vue (Format)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Élément de frame pour CustomItem pour CustomControl de vue (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
