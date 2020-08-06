---
title: Élément Frame pour CustomItem pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fa435b8d6b868d2d7c94b7926321d94edc2ec290
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781475"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Frame, élément pour CustomItem pour Controls pour Configuration (Format)

Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) Controls, élément de configuration (format), élément de contrôle pour la configuration (format) CustomControl, élément de Control pour configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément CustomItem pour CustomEntry pour les contrôles de l’élément frame de configuration pour la configuration (format)

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
|[FirstLineHanging, élément pour Frame pour Controls pour Configuration (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche.|
|[FirstLineIndent, élément pour Frame pour Controls pour Configuration (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite.|
|[LeftIndent, élément pour Frame pour Controls pour Configuration (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche.|
|[RightIndent, élément pour Frame pour Controls pour Configuration (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomItem pour CustomEntry pour les contrôles de configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Définit les données affichées par le contrôle et leur mode d’affichage.|

## <a name="remarks"></a>Notes

Vous ne pouvez pas spécifier les éléments [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) dans le même `Frame` élément.

## <a name="see-also"></a>Voir aussi

[FirstLineHanging, élément pour Frame pour Controls pour Configuration (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[FirstLineIndent, élément pour Frame pour Controls pour Configuration (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[LeftIndent, élément pour Frame pour Controls pour Configuration (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[RightIndent, élément pour Frame pour Controls pour Configuration (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[Élément CustomItem pour CustomEntry pour les contrôles de configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
