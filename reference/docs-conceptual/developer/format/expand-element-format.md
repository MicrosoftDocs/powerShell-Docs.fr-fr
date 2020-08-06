---
title: Expand, élément (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: deee832254bb8a774ee2c1f5bd451d3ced1bd47a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783651"
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

Cet élément est utilisé pour définir le mode d’affichage des objets de collection et des objets de la collection. Dans ce cas, un objet de collection fait référence à tout objet qui prend en charge l’interface **System. Collections. ICollection** .

Le comportement par défaut consiste à afficher uniquement les propriétés des objets dans la collection.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
