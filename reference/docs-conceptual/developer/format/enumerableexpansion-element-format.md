---
title: Élément EnumerableExpansion (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 81a8959c19502a2e56f4cfa48a1e480509d84b6e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774046"
---
# <a name="enumerableexpansion-element-format"></a>EnumerableExpansion, élément (Format)

Définit la façon dont des objets de collection .NET spécifiques sont développés lorsqu’ils sont affichés dans une vue.

Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) EnumerableExpansion, élément (format)

## <a name="syntax"></a>Syntaxe

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EnumerableExpansion` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[EntrySelectedBy, élément pour EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Élément facultatif.<br /><br /> Définit les objets de collection .NET développés par cette définition.|
|[Expand, élément (Format)](./expand-element-format.md)|Spécifie comment l’objet de collection est développé pour cette définition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[EnumerableExpansions, élément (Format)](./enumerableexpansions-element-format.md)|Définit les différentes façons dont les objets de collection .NET sont développés lorsqu’ils sont affichés dans une vue.|

## <a name="remarks"></a>Notes

Cet élément est utilisé pour définir le mode d’affichage des objets de collection et des objets de la collection. Dans ce cas, un objet de collection fait référence à tout objet qui prend en charge l’interface **System. Collections. ICollection** .

Le comportement par défaut consiste à afficher uniquement les propriétés des objets dans la collection.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
