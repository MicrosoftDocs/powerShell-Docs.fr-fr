---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)
description: CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)
ms.openlocfilehash: 35e1554a9eed491f37499a7455e9c5cae3cd9e1e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655455"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a>CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)

Spécifie le nom d’un contrôle commun ou d’un contrôle View. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément CustomEntries View (format) pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour les contrôles de l’élément View (format) CustomItem pour CustomEntry pour les contrôles pour l’élément View (format) ExpressionBinding pour les contrôles de l’élément View (format) CustomItem pour CustomControlName pour les contrôles pour View (format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomControlName` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Définit les données affichées par le contrôle.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du contrôle.

## <a name="remarks"></a>Notes

Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique. Les éléments suivants spécifient les noms de ces contrôles :

- [Name, élément pour Control pour Controls pour Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name, élément pour Control pour Controls pour View (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[Name, élément pour Control pour Controls pour Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name, élément pour Control pour Controls pour View (Format)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
