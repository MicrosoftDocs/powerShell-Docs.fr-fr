---
title: Élément CustomItem pour CustomEntry pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066411"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>CustomItem, élément pour CustomEntry pour CustomControl pour View (Format)

Définit les données affichées par la vue de contrôle personnalisé et comment il est affiché. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour l’élément d’affichage (Format) de CustomItem pour CustomEntry de vue (Format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomItem` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément ExpressionBinding pour CustomItem pour CustomControl de vue (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Définit les données qui sont affichées par le contrôle.|
|[Élément de frame pour CustomItem pour CustomControl de vue (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Définit les données affichées par la vue de contrôle personnalisé et comment il est affiché.|
|[Élément de saut de ligne pour CustomItem pour un contrôle personnalisé pour la vue (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Ajoute une ligne vide à l’affichage du contrôle.|
|[Élément de texte pour CustomItem pour CustomControl de vue (Format)](./text-element-for-customitem-for-customview-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le texte supplémentaire pour les données affichées par le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomEntries pour CustomControl de vue (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Fournit une définition de la vue de contrôle personnalisé.|

## <a name="remarks"></a>Remarques

## <a name="see-also"></a>Voir aussi

[Élément CustomEntry pour CustomEntries pour la vue (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Élément ExpressionBinding pour CustomItem pour CustomControl de vue (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Élément de frame pour CustomItem pour CustomControl de vue (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Élément de saut de ligne pour CustomItem pour CustomControl de vue (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Élément de texte pour CustomItem pour CustomControl de vue (Format)](./text-element-for-customitem-for-customview-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
