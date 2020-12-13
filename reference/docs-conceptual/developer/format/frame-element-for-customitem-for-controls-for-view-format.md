---
ms.date: 09/13/2016
ms.topic: reference
title: Frame, élément pour CustomItem pour Controls pour View (Format)
description: Frame, élément pour CustomItem pour Controls pour View (Format)
ms.openlocfilehash: 6f26e19a6894ac213b924108a56cb80f9ffd1143
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652211"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Frame, élément pour CustomItem pour Controls pour View (Format)

Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour les contrôles pour la vue (format) CustomItem, élément pour CustomEntry pour les contrôles pour l’élément Frame (format) pour CustomItem pour les contrôles pour View (format)

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

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Frame` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|`CustomItem Element`|Élément requis|
|[Élément FirstLineHanging de frame de contrôles de vue (format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères que la première ligne est décalée vers la gauche.|
|[Élément FirstLineIndent de frame de contrôles de vue (format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères que la première ligne est décalée vers la droite.|
|[LeftIndent, élément de frame de contrôles de vue (format)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche.|
|[Élément RightIndent du frame des contrôles de vue (format)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomItem, élément pour CustomEntry pour Controls pour View (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Définit les données affichées par le contrôle et leur mode d’affichage.|

## <a name="remarks"></a>Notes

Vous ne pouvez pas spécifier les éléments [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) dans le même `Frame` élément.

## <a name="see-also"></a>Voir aussi

[Élément FirstLineHanging de frame de contrôles de vue (format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Élément FirstLineIndent de frame de contrôles de vue (format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[LeftIndent, élément de frame de contrôles de vue (format)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[Élément RightIndent du frame des contrôles de vue (format)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[CustomItem, élément pour CustomEntry pour Controls pour View (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
