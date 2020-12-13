---
ms.date: 09/13/2016
ms.topic: reference
title: Frame, élément pour CustomItem pour CustomControl pour View (Format)
description: Frame, élément pour CustomItem pour CustomControl pour View (Format)
ms.openlocfilehash: 1ffe071bb6c4f590e4c79803a3faff2108c7b636
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652189"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Frame, élément pour CustomItem pour CustomControl pour View (Format)

Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) CustomControl, élément (format) CustomEntries élément pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour la vue (format) élément CustomItem pour CustomEntry pour CustomControlView (format) élément Frame pour CustomItem pour la vue (format)

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
|[Élément FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche.|
|[Élément FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite.|
|[Élément LeftIndent](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche.|
|[Élément RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomItem pour CustomEntry pour View (format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Définit les données affichées par le contrôle et leur mode d’affichage.|

## <a name="remarks"></a>Notes

Vous ne pouvez pas spécifier les éléments [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) dans le même `Frame` élément.

## <a name="see-also"></a>Voir aussi

[Élément FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Élément FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Élément LeftIndent](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[Élément RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[Élément CustomItem pour CustomEntry pour View (format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
