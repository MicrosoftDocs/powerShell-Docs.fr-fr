---
title: Élément CustomEntry pour CustomEntries pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4fc960ab803580f684ce0f224b1db4d7d4af1720
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785895"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a>CustomEntry, élément pour CustomEntries pour Controls pour View (Format)

Fournit une définition du contrôle. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour la vue (format) élément CustomControl pour le contrôle des contrôles pour l’élément View (format) CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour les contrôles pour View (format)

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
|[EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.|
|[CustomItem, élément pour CustomEntry pour Controls pour View (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Élément requis.<br /><br /> Définit le mode d’affichage des données par le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomEntries, élément pour CustomControl pour View (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Fournit les définitions pour le contrôle.|

## <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[CustomEntries, élément pour CustomControl pour View (Format)](./customentries-element-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
