---
title: Élément CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066666"
---
# <a name="customcontrol-element-for-view-format"></a>CustomControl, élément pour View (Format)

Définit un format de contrôle personnalisé pour la vue.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) CustomControl élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomControl` élément. Vous devez spécifier un seul élément enfant.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntries pour CustomControl de vue (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Élément requis.<br /><br /> Fournit les définitions de la vue de contrôle personnalisé.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément d’affichage (Format)](./view-element-format.md)|Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.|

## <a name="remarks"></a>Remarques

Dans la plupart des cas, qu’une seule définition est requise pour chaque affichage de contrôle, mais il est possible de fournir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher les différents objets .NET. Dans ce cas, vous pouvez fournir une définition séparée pour chaque objet ou un ensemble d’objets.

## <a name="see-also"></a>Voir aussi

[Élément CustomEntries pour CustomControl de vue (Format)](./customentries-element-for-customcontrol-for-view-format.md)

[Élément d’affichage (Format)](./view-element-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
