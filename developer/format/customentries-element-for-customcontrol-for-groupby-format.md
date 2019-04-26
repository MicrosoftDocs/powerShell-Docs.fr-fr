---
title: Élément CustomEntries pour CustomControl pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066535"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>CustomEntries, élément pour CustomControl pour GroupBy (Format)

Fournit les définitions pour le contrôle. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

Configuration élément (Format) ViewDefinitions, élément (Format) élément (Format) GroupBy élément d’affichage pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl pour GroupBy (Format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents de la `CustomEntries` élément. Il n’existe aucune limite maximale pour le nombre d’éléments enfants qui peuvent être spécifiées.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomControl pour GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Élément requis.<br /><br /> Fournit une définition du contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomControl pour GroupBy (Format)](./customcontrol-element-for-groupby-format.md)|Définit le contrôle personnalisé qui affiche le nouveau groupe.|

## <a name="remarks"></a>Remarques

Dans la plupart des cas, un contrôle n'a qu’une seule définition, ce qui est spécifiée dans un seul `CustomEntry` élément. Toutefois, il est possible de fournir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher les différents groupes. Dans ce cas, vous pouvez définir un `CustomEntry` élément pour un groupe.

## <a name="see-also"></a>Voir aussi

[Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Élément CustomControl pour GroupBy (Format)](./customcontrol-element-for-groupby-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
