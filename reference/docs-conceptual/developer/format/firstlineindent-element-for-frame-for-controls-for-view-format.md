---
ms.date: 09/13/2016
ms.topic: reference
title: FirstLineIndent, élément pour Frame pour Controls pour View (Format)
description: FirstLineIndent, élément pour Frame pour Controls pour View (Format)
ms.openlocfilehash: 425cd9ccafb2cbe36f238177fc73923da048f924
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660145"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a>FirstLineIndent, élément pour Frame pour Controls pour View (Format)

Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément CustomEntries View (format) pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour les contrôles de l’élément View (format) CustomItem pour CustomEntry pour les contrôles pour l’élément Frame (format) View pour CustomItem pour les contrôles pour l’élément View (format) FirstLineIndent de frame des contrôles de vue (format)

## <a name="syntax"></a>Syntaxe

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `FirstLineIndent` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Frame, élément pour CustomItem pour Controls pour View (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nombre de caractères dont vous souhaitez déplacer la première ligne des données.

## <a name="remarks"></a>Notes

Si cet élément est spécifié, vous ne pouvez pas spécifier l’élément [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) .

## <a name="see-also"></a>Voir aussi

[FirstLineHanging, élément pour Frame pour Controls pour View (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Frame, élément pour CustomItem pour Controls pour View (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
