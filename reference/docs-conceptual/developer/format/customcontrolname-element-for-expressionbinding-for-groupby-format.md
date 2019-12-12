---
title: Élément CustomControlName pour ExpressionBinding pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368908"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)

Spécifie le nom d’un contrôle commun ou d’un contrôle View. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format) élément CustomItem pour CustomEntry pour GroupBy (format) élément ExpressionBinding pour CustomItem pour l’élément GroupBy (format) CustomControlName pour l’élément ExpressionBinding pour GroupBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `CustomControlName`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ExpressionBinding pour CustomItem pour GroupBy (format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Définit les données affichées par le contrôle.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom du contrôle.

## <a name="remarks"></a>Remarks

Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique. Les éléments suivants spécifient les noms de ces contrôles :

- [Élément Name pour le contrôle des contrôles pour la configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Élément Name pour le contrôle des contrôles pour View (format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[Élément Name pour le contrôle des contrôles pour la configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Élément Name pour le contrôle des contrôles pour View (format)](./name-element-for-control-for-controls-for-view-format.md)

[Élément ExpressionBinding pour CustomItem pour GroupBy (format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
