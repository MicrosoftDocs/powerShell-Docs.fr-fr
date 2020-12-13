---
ms.date: 09/13/2016
ms.topic: reference
title: FirstLineHanging, élément pour Frame pour CustomControl pour View (Format)
description: FirstLineHanging, élément pour Frame pour CustomControl pour View (Format)
ms.openlocfilehash: 8b9601b2afd7ab5523e339fb45119f5cf9f4a535
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648137"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a>FirstLineHanging, élément pour Frame pour CustomControl pour View (Format)

Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour la vue (format) élément CustomItem pour CustomEntry pour l’élément Frame CustomControlView (format) pour l’élément CustomItem pour la vue (format)

## <a name="syntax"></a>Syntaxe

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `FirstLineHanging` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Frame, élément pour CustomItem pour CustomControl pour View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nombre de caractères dont vous souhaitez déplacer la première ligne des données.

## <a name="remarks"></a>Notes

Si cet élément est spécifié, vous ne pouvez pas spécifier l’élément [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) .

## <a name="see-also"></a>Voir aussi

[FirstLineIndent, élément pour Frame pour CustomControl pour View (Format)](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Frame, élément pour CustomItem pour CustomControl pour View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
