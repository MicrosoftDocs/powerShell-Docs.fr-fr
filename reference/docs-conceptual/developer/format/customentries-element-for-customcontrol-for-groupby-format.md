---
title: Élément CustomEntries pour CustomControl pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364088"
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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l’élément `CustomEntries`. Il n’existe pas de limite maximale pour le nombre d’éléments enfants qui peuvent être spécifiés.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomControl pour GroupBy (format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Élément requis.<br /><br /> Fournit une définition du contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomControl, élément de GroupBy (format)](./customcontrol-element-for-groupby-format.md)|Définit le contrôle personnalisé qui affiche le nouveau groupe.|

## <a name="remarks"></a>Remarks

Dans la plupart des cas, un contrôle n’a qu’une seule définition, qui est spécifiée dans un élément `CustomEntry` unique. Toutefois, il est possible de fournir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher des groupes différents. Dans ce cas, vous pouvez définir un élément `CustomEntry` pour un groupe.

## <a name="see-also"></a>Voir aussi

[Élément CustomEntry pour CustomEntries pour les contrôles pour View (format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[CustomControl, élément de GroupBy (format)](./customcontrol-element-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
