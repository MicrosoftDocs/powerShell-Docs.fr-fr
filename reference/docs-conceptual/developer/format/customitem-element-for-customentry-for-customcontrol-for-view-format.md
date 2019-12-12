---
title: Élément CustomItem pour CustomEntry pour CustomControl pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363948"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>CustomItem, élément pour CustomEntry pour CustomControl pour View (Format)

Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour la vue (format) CustomItem, élément de CustomEntry pour la vue (format)

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
|[Élément ExpressionBinding pour CustomItem pour CustomControl pour View (format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Définit les données affichées par le contrôle.|
|[Élément Frame pour CustomItem pour CustomControl pour View (format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.|
|[Élément NewLine pour CustomItem pour un contrôle personnalisé pour View (format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Ajoute une ligne vide à l’affichage du contrôle.|
|[Élément de texte pour CustomItem pour CustomControl pour View (format)](./text-element-for-customitem-for-customview-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie du texte supplémentaire pour les données affichées par le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomEntries pour CustomControl pour View (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Fournit une définition de l’affichage de contrôle personnalisé.|

## <a name="remarks"></a>Remarks

## <a name="see-also"></a>Voir aussi

[Élément CustomEntry pour CustomEntries pour View (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Élément ExpressionBinding pour CustomItem pour CustomControl pour View (format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Élément Frame pour CustomItem pour CustomControl pour View (format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Élément NewLine pour CustomItem pour CustomControl pour View (format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Élément de texte pour CustomItem pour CustomControl pour View (format)](./text-element-for-customitem-for-customview-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
