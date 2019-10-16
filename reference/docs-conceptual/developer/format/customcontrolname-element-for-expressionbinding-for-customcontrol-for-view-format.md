---
title: Élément CustomControlName pour ExpressionBinding pour CustomControl pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364108"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)

Spécifie le nom d’un contrôle commun ou d’un contrôle View. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl pour View (format) CustomEntries element pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour View (format) CustomItem Élément pour CustomEntry pour l’élément ExpressionBinding View (format) pour CustomItem (format) CustomControlName élément pour la liaison d’expression pour CustomItem (format)

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
|[Élément ExpressionBinding pour CustomItem (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Définit les données affichées par le contrôle.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du contrôle.

## <a name="remarks"></a>Remarks

Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique. Les noms de ces contrôles sont spécifiés par les éléments suivants.

- [Élément Name pour le contrôle des contrôles pour la configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Élément Name pour le contrôle des contrôles pour View (format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[Élément Name pour le contrôle des contrôles pour la configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Élément Name pour le contrôle des contrôles pour View (format)](./name-element-for-control-for-controls-for-view-format.md)

[Élément ExpressionBinding pour CustomItem (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
