---
title: Élément CustomEntry pour CustomEntries pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861815"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>CustomEntry, élément pour CustomEntries pour CustomControl pour View (Format)

Fournit une définition de la vue de contrôle personnalisé.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour la vue (Format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomEntry` élément. Vous devez spécifier les éléments affichés par la définition.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour CustomEntry pour la vue (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Définit les types .NET qui utilisent la définition de la vue de contrôle personnalisé ou de la condition qui doit exister pour cette définition à utiliser.|
|[Élément CustomItem pour CustomEntry pour la vue (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Définit un contrôle pour la définition du contrôle personnalisé.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntries pour CustomControl de vue (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Fournit les définitions de la vue de contrôle personnalisé. L’affichage de contrôle personnalisé doit spécifier une ou plusieurs définitions.|

## <a name="remarks"></a>Remarques

Dans la plupart des cas, qu’une seule définition est requise pour chaque affichage de contrôle personnalisé, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher les différents objets .NET. Dans ce cas, vous pouvez fournir une définition séparée pour chaque objet ou un ensemble d’objets.

## <a name="see-also"></a>Voir aussi

[Élément CustomControl de vue (Format)](./customcontrol-element-for-view-format.md)

[Élément CustomItem pour CustomEntry pour la vue (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Élément EntrySelectedBy pour CustomEntry pour la vue (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
