---
title: Élément CustomControlName pour ExpressionBinding pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854295"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)

Spécifie le nom d’un contrôle commun ou un contrôle d’affichage. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de CustomItem GroupBy (Format) pour CustomEntry d’élément de ExpressionBinding GroupBy (Format) pour CustomItem d’élément de CustomControlName GroupBy (Format) pour ExpressionBinding pour GroupBy (Format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomControlName` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ExpressionBinding pour CustomItem pour GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Définit les données qui sont affichées par le contrôle.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom du contrôle.

## <a name="remarks"></a>Remarques

Vous pouvez créer des contrôles communs qui peuvent être utilisées par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisées par une vue spécifique. Les éléments suivants spécifient les noms de ces contrôles :

- [Name, élément pour le contrôle pour les contrôles de Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name, élément pour le contrôle pour les contrôles de vue (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[Name, élément pour le contrôle pour les contrôles de Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name, élément pour le contrôle pour les contrôles de vue (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Élément ExpressionBinding pour CustomItem pour GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
