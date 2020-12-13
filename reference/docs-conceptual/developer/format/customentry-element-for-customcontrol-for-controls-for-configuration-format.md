---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)
description: CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)
ms.openlocfilehash: 3967be86a1d6c12c7215ef19d50bac9fafd5ad6d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648286"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)

Fournit une définition du contrôle commun. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format)

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
|[EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Définit les types .NET qui utilisent la définition du contrôle commun ou la condition qui doit exister pour que ce contrôle soit utilisé.|
|[Élément CustomItem pour CustomEntry pour les contrôles de configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Élément requis.<br /><br /> Définit les données affichées par le contrôle et leur mode d’affichage.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntries pour CustomControl pour la configuration (format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Fournit les définitions du contrôle commun.|

## <a name="remarks"></a>Notes

Dans la plupart des cas, une seule définition est requise pour chaque contrôle personnalisé commun, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher différents objets .NET. Dans ce cas, vous pouvez fournir une définition distincte pour chaque objet ou ensemble d’objets.

## <a name="see-also"></a>Voir aussi

[Élément CustomEntries pour CustomControl pour la configuration (format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[Élément CustomItem pour CustomEntry pour les contrôles de configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
