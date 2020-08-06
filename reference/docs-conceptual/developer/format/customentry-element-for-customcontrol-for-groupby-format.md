---
title: Élément CustomEntry pour CustomControl pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4df8e5b96868b3814c6d84fa329950bb5345ef6e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785912"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>CustomEntry, élément pour CustomControl pour GroupBy (Format)

Fournit une définition du contrôle. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `CustomEntry` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.|
|[CustomItem, élément pour CustomEntry pour GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Élément requis.<br /><br /> Définit le mode d’affichage des données par le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomEntries, élément pour CustomControl pour GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)|Fournit les définitions pour le contrôle.|

## <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[CustomItem, élément pour CustomEntry pour GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[CustomEntries, élément pour CustomControl pour GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
