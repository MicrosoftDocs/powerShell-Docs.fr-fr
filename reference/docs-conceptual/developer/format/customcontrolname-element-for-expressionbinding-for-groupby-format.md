---
title: Élément CustomControlName pour ExpressionBinding pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 06e612b25accf81467108ca48500943153efd575
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785997"
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
