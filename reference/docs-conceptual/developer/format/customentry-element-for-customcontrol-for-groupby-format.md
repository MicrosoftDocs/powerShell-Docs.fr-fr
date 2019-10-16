---
title: Élément CustomEntry pour CustomControl pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364058"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>CustomEntry, élément pour CustomControl pour GroupBy (Format)

Fournit une définition du contrôle. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l’élément `CustomEntry`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour CustomEntry pour GroupBy (format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.|
|[Élément CustomItem pour CustomEntry pour GroupBy (format)](./customitem-element-for-customentry-for-groupby-format.md)|Élément requis.<br /><br /> Définit le mode d’affichage des données par le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntries pour CustomControl pour GroupBy (format)](./customentries-element-for-customcontrol-for-groupby-format.md)|Fournit les définitions pour le contrôle.|

## <a name="remarks"></a>Remarks

## <a name="see-also"></a>Voir aussi

[Élément EntrySelectedBy pour CustomEntry pour GroupBy (format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Élément CustomItem pour CustomEntry pour GroupBy (format)](./customitem-element-for-customentry-for-groupby-format.md)

[Élément CustomEntries pour CustomControl pour GroupBy (format)](./customentries-element-for-customcontrol-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
