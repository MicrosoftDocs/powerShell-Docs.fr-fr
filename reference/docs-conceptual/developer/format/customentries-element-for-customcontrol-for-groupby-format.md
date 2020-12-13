---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntries, élément pour CustomControl pour GroupBy (Format)
description: CustomEntries, élément pour CustomControl pour GroupBy (Format)
ms.openlocfilehash: cde59d38b83930cb64a3a0040891783e4ab96723
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666788"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>CustomEntries, élément pour CustomControl pour GroupBy (Format)

Fournit les définitions pour le contrôle. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour View (format) CustomControl, élément pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `CustomEntries` élément. Il n’existe pas de limite maximale pour le nombre d’éléments enfants qui peuvent être spécifiés.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[CustomEntry, élément pour CustomControl pour GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Élément requis.<br /><br /> Fournit une définition du contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomControl, élément pour GroupBy (Format)](./customcontrol-element-for-groupby-format.md)|Définit le contrôle personnalisé qui affiche le nouveau groupe.|

## <a name="remarks"></a>Notes

Dans la plupart des cas, un contrôle n’a qu’une seule définition, qui est spécifiée dans un `CustomEntry` élément unique. Toutefois, il est possible de fournir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher des groupes différents. Dans ce cas, vous pouvez définir un `CustomEntry` élément pour un groupe.

## <a name="see-also"></a>Voir aussi

[CustomEntry, élément pour CustomEntries pour Controls pour View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[CustomControl, élément pour GroupBy (Format)](./customcontrol-element-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
