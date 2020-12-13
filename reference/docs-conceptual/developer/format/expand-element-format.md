---
ms.date: 09/13/2016
ms.topic: reference
title: Expand, élément (Format)
description: Expand, élément (Format)
ms.openlocfilehash: 518e132e3e74b921d4e51966fc60088a22ef63f1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667944"
---
# <a name="expand-element-format"></a>Expand, élément (Format)

Spécifie comment l’objet de collection est développé pour cette définition.

Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) Expand, élément (format)

## <a name="syntax"></a>Syntaxe

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Expand` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[EnumerableExpansion, élément (Format)](./enumerableexpansion-element-format.md)|Définit la façon dont des objets de collection .NET spécifiques sont développés lorsqu’ils sont affichés dans une vue.|

## <a name="text-value"></a>Valeur texte

Spécifiez l'une des valeurs suivantes :

- EnumOnly : affiche uniquement les propriétés des objets dans la collection.

- CoreOnly : affiche uniquement les propriétés de l’objet de collection.

- Both : affiche les propriétés des objets dans la collection et les propriétés de l’objet de collection.

## <a name="remarks"></a>Notes

Cet élément est utilisé pour définir le mode d’affichage des objets de collection et des objets de la collection. Dans ce cas, un objet de collection fait référence à tout objet qui prend en charge l’interface  **System. Collections. ICollection** .

Le comportement par défaut consiste à afficher uniquement les propriétés des objets dans la collection.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
