---
ms.date: 09/13/2016
ms.topic: reference
title: FirstLineIndent, élément pour Frame pour GroupBy (Format)
description: FirstLineIndent, élément pour Frame pour GroupBy (Format)
ms.openlocfilehash: 391a6f338e264fd9fdd1948ded74bf022cb114d1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645794"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a>FirstLineIndent, élément pour Frame pour GroupBy (Format)

Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour View (format) CustomControl, élément pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) CustomItem élément pour CustomEntry pour l’élément GroupBy (format)

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
|[Frame, élément pour CustomItem pour GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nombre de caractères dont vous souhaitez déplacer la première ligne des données.

## <a name="remarks"></a>Notes

Si cet élément est spécifié, vous ne pouvez pas spécifier l’élément [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) .

## <a name="see-also"></a>Voir aussi

[FirstLineHanging, élément pour Frame pour GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Frame, élément pour CustomItem pour GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
