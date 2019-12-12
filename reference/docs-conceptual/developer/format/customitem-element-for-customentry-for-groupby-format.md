---
title: Élément CustomItem pour CustomEntry pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363878"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>CustomItem, élément pour CustomEntry pour GroupBy (Format)

Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomItem GroupBy (format) pour CustomEntry pour GroupBy (format)

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

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `CustomItem`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément ExpressionBinding pour CustomItem pour GroupBy (format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit les données affichées par le contrôle.|
|[Élément Frame pour CustomItem pour GroupBy (format)](./frame-element-for-customitem-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.|
|[Élément NewLine pour CustomItem pour GroupBy (format)](./newline-element-for-customitem-for-groupby-format.md)|Élément facultatif.<br /><br /> Ajoute une ligne vide à l’affichage du contrôle.|
|[Élément Text pour CustomItem pour GroupBy (format)](./text-element-for-customitem-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie du texte supplémentaire pour les données affichées par le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomControl pour GroupBy (format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Fournit une définition de l’affichage de contrôle personnalisé.|

## <a name="remarks"></a>Remarks

## <a name="see-also"></a>Voir aussi

[Élément CustomEntry pour CustomControl pour GroupBy (format)](./customentry-element-for-customcontrol-for-groupby-format.md)

[Élément ExpressionBinding pour CustomItem pour GroupBy (format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Élément Frame pour CustomItem pour GroupBy (format)](./frame-element-for-customitem-for-groupby-format.md)

[Élément NewLine pour CustomItem pour GroupBy (format)](./newline-element-for-customitem-for-groupby-format.md)

[Élément Text pour CustomItem pour GroupBy (format)](./text-element-for-customitem-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
