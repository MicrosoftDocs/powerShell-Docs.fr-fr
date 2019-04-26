---
title: Élément CustomEntry pour CustomControl pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066464"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)

Fournit une définition du contrôle commun. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles de Configuration (Format)

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
|[Élément EntrySelectedBy pour CustomEntry pour les contrôles de Configuration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Définit les types .NET qui utilisent la définition du contrôle commun ou la condition qui doit exister pour ce contrôle à utiliser.|
|[Élément CustomItem pour CustomEntry pour les contrôles de Configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Élément requis.<br /><br /> Définit les données affichées par le contrôle et comment il est affiché.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntries pour CustomControl pour la Configuration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Fournit les définitions du contrôle commun.|

## <a name="remarks"></a>Remarques

Dans la plupart des cas, qu’une seule définition est requise pour chaque contrôle personnalisé courants, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher les différents objets .NET. Dans ce cas, vous pouvez fournir une définition séparée pour chaque objet ou un ensemble d’objets.

## <a name="see-also"></a>Voir aussi

[Élément CustomEntries pour CustomControl pour la Configuration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[Élément CustomItem pour CustomEntry pour les contrôles de Configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
