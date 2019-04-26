---
title: Élément CustomControlName pour ExpressionBinding pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066615"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)

Spécifie le nom d’un contrôle commun ou un contrôle d’affichage. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) CustomControl élément d’affichage (Format) CustomEntries élément pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour CustomItem de vue (Format) Élément pour CustomEntry pour élément de ExpressionBinding d’affichage (Format) pour l’élément de CustomControlName CustomItem (Format) pour la liaison d’Expression pour CustomItem (Format)

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
|[Élément ExpressionBinding pour CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Définit les données qui sont affichées par le contrôle.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom du contrôle.

## <a name="remarks"></a>Remarques

Vous pouvez créer des contrôles communs qui peuvent être utilisées par toutes les vues d’un fichier de mise en forme et vous pouvez créer des contrôles d’affichage qui peuvent être utilisées par une vue spécifique. Les noms de ces contrôles sont spécifiés par les éléments suivants.

- [Name, élément pour le contrôle pour les contrôles de Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name, élément pour le contrôle pour les contrôles de vue (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[Name, élément pour le contrôle pour les contrôles de Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name, élément pour le contrôle pour les contrôles de vue (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Élément ExpressionBinding pour CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
