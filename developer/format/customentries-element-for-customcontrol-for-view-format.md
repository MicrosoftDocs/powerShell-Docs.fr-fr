---
title: Élément CustomEntries pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066513"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>CustomEntries, élément pour CustomControl pour View (Format)

Fournit les définitions de la vue de contrôle personnalisé. L’affichage de contrôle personnalisé doit spécifier une ou plusieurs définitions.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl de vue (Format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomControlEntries` élément. Vous devez spécifier un ou plusieurs éléments enfants.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomEntries pour la vue (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Élément requis.<br /><br /> Fournit une définition de la vue de contrôle personnalisé.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomControl de vue (Format)](./customcontrol-element-for-view-format.md)|Élément requis.<br /><br /> Définit un format de contrôle personnalisé pour la vue.|

## <a name="remarks"></a>Remarques

Dans la plupart des cas, un contrôle n'a qu’une seule définition, ce qui est définie dans un seul `CustomEntry` élément. Toutefois, il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher les différents objets .NET. Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou un ensemble d’objets.

## <a name="see-also"></a>Voir aussi

[Élément CustomControl de vue (Format)](./customcontrol-element-for-view-format.md)

[Élément CustomEntry pour CustomEntries pour la vue (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
