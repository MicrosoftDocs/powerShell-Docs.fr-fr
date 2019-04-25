---
title: Élément CustomItem pour CustomEntry pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066394"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>CustomItem, élément pour CustomEntry pour GroupBy (Format)

Définit les données affichées par la vue de contrôle personnalisé et comment il est affiché. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomItem GroupBy (Format) pour CustomEntry pour GroupBy (Format)

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
|[Élément ExpressionBinding pour CustomItem pour GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit les données qui sont affichées par le contrôle.|
|[Élément de frame pour CustomItem pour GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit les données affichées par la vue de contrôle personnalisé et comment il est affiché.|
|[Élément de saut de ligne pour CustomItem pour GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md)|Élément facultatif.<br /><br /> Ajoute une ligne vide à l’affichage du contrôle.|
|[Élément de texte pour CustomItem pour GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le texte supplémentaire pour les données affichées par le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomControl pour GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Fournit une définition de la vue de contrôle personnalisé.|

## <a name="remarks"></a>Remarques

## <a name="see-also"></a>Voir aussi

[Élément CustomEntry pour CustomControl pour GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)

[Élément ExpressionBinding pour CustomItem pour GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Élément de frame pour CustomItem pour GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[Élément de saut de ligne pour CustomItem pour GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md)

[Élément de texte pour CustomItem pour GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
