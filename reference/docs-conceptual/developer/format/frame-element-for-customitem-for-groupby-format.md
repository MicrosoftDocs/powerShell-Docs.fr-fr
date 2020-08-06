---
title: Élément Frame pour CustomItem pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1568236ff7b6142f7e41be70a3ae5e28307cf790
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785759"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Frame, élément pour CustomItem pour GroupBy (Format)

Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) CustomItem élément pour CustomEntry pour l’élément de cadre GroupBy (format) pour l’élément CustomItem pour GroupBy (format)

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
|[FirstLineHanging, élément pour Frame pour GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche.|
|[FirstLineIndent, élément pour Frame pour GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite.|
|[LeftIndent, élément pour Frame pour GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche.|
|[RightIndent, élément de frame pour GroupBy (format)](./rightindent-element-for-frame-for-groupby-format.md) Élément RightIndent|Élément facultatif.<br /><br /> Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomItem, élément pour CustomEntry pour GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Définit les données affichées par le contrôle et leur mode d’affichage.|

## <a name="remarks"></a>Notes

Vous ne pouvez pas spécifier les éléments [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) dans le même `Frame` élément.

## <a name="see-also"></a>Voir aussi

[FirstLineHanging, élément pour Frame pour GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[FirstLineIndent, élément pour Frame pour GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[LeftIndent, élément pour Frame pour GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md)

[RightIndent, élément pour Frame pour GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)

[CustomItem, élément pour CustomEntry pour GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
