---
title: Élément FirstLineHanging pour Frame pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ea43e025f5f653ff000e1d7591b535e73da5c9e5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065969"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a>FirstLineHanging, élément pour Frame pour CustomControl pour View (Format)

Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour l’élément d’affichage (Format) de CustomItem pour CustomEntry d’élément de Frame CustomControlView (Format) pour CustomItem pour CustomControl pour élément de FirstLineHanging d’affichage (Format) pour le Frame pour CustomControl de vue (Format)

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
|[Élément de frame pour CustomItem pour CustomControl de vue (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nombre de caractères que vous souhaitez déplacer la première ligne des données.

## <a name="remarks"></a>Remarques

Si cet élément est spécifié, vous ne pouvez pas spécifier le [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) élément.

## <a name="see-also"></a>Voir aussi

[Élément FirstLineIndent pour Frame pour CustomControl de vue (Format)](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Élément de frame pour CustomItem pour CustomControl de vue (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
