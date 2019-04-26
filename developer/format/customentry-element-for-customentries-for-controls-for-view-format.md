---
title: Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066483"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a>CustomEntry, élément pour CustomEntries pour Controls pour View (Format)

Fournit une définition du contrôle. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles de vue (Format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et les éléments parents de la `CustomEntry` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour CustomEntry pour les contrôles de vue (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser.|
|[Élément CustomItem pour CustomEntry pour les contrôles de vue (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Élément requis.<br /><br /> Définit comment le contrôle affiche les données.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntries pour CustomControl de vue (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Fournit les définitions pour le contrôle.|

## <a name="remarks"></a>Remarques

## <a name="see-also"></a>Voir aussi

[Élément CustomEntries pour CustomControl de vue (Format)](./customentries-element-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
