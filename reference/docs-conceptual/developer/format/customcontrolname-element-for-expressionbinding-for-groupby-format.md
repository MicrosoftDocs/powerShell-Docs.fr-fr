---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)
description: CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)
ms.openlocfilehash: bb7dbd449137628da1794628c5a7d7e10158dd46
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655437"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)

Spécifie le nom d’un contrôle commun ou d’un contrôle View. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour la vue (format) CustomControl, élément de GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) CustomItem élément pour CustomEntry pour GroupBy (format)

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
|[ExpressionBinding, élément pour CustomItem pour GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Définit les données affichées par le contrôle.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du contrôle.

## <a name="remarks"></a>Notes

Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique. Les éléments suivants spécifient les noms de ces contrôles :

- [Name, élément pour Control pour Controls pour Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name, élément pour Control pour Controls pour View (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[Name, élément pour Control pour Controls pour Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name, élément pour Control pour Controls pour View (Format)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding, élément pour CustomItem pour GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
