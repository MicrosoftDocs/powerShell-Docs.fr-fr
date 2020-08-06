---
title: Élément CustomEntry pour CustomEntries pour CustomControl pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a13e83ec941bed80eaab02e40131054432fcce00
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785878"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>CustomEntry, élément pour CustomEntries pour CustomControl pour View (Format)

Fournit une définition de l’affichage de contrôle personnalisé.

Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour View (format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomEntry` élément. Vous devez spécifier les éléments affichés par la définition.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour CustomEntry pour View (format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Définit les types .NET qui utilisent la définition de l’affichage de contrôle personnalisé ou la condition qui doit exister pour que cette définition soit utilisée.|
|[Élément CustomItem pour CustomEntry pour View (format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Définit un contrôle pour la définition de contrôle personnalisé.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomEntries, élément pour CustomControl pour View (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Fournit les définitions de l’affichage de contrôle personnalisé. L’affichage de contrôle personnalisé doit spécifier une ou plusieurs définitions.|

## <a name="remarks"></a>Notes

Dans la plupart des cas, une seule définition est requise pour chaque affichage de contrôle personnalisé, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher différents objets .NET. Dans ce cas, vous pouvez fournir une définition distincte pour chaque objet ou ensemble d’objets.

## <a name="see-also"></a>Voir aussi

[CustomControl, élément pour View (Format)](./customcontrol-element-for-view-format.md)

[Élément CustomItem pour CustomEntry pour View (format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Élément EntrySelectedBy pour CustomEntry pour View (format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
