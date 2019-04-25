---
title: Élément CustomEntries pour CustomControl pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066578"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>CustomEntries, élément pour CustomControl pour Controls pour View (Format)

Fournit les définitions pour le contrôle. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour les contrôles de vue (Format)

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
|[Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Élément requis.<br /><br /> Fournit une définition du contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomControl pour le contrôle pour les contrôles de vue (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Définit le contrôle utilisé par la vue.|

## <a name="remarks"></a>Remarques

Dans la plupart des cas, un contrôle n'a qu’une seule définition, ce qui est spécifiée dans un seul `CustomEntry` élément. Toutefois, il est possible de fournir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher les différents objets .NET. Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou un ensemble d’objets.

## <a name="see-also"></a>Voir aussi

[Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Élément CustomControl pour le contrôle pour les contrôles de vue (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
