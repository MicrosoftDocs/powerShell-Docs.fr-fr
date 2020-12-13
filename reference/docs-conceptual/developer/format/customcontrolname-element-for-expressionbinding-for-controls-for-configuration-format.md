---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControlName, élément pour ExpressionBinding pour Controls pour Configuration (Format)
description: CustomControlName, élément pour ExpressionBinding pour Controls pour Configuration (Format)
ms.openlocfilehash: 3815956f59f19c0215aaf26b94dede656b9453cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648320"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a>CustomControlName, élément pour ExpressionBinding pour Controls pour Configuration (Format)

Spécifie le nom d’un contrôle commun. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format), élément CustomItem pour CustomEntry pour les contrôles de l’élément de configuration ExpressionBinding pour CustomItem pour les contrôles de configuration (format) CustomControlName élément pour ExpressionBinding pour les contrôles de configuration (format)

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
|[ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Définit les données affichées par le contrôle.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du contrôle.

## <a name="remarks"></a>Notes

Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique. Les éléments suivants spécifient les noms de ces contrôles :

- [Name, élément pour Control pour Controls pour Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name, élément pour Control pour Controls pour View (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[Name, élément pour Control pour Controls pour Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name, élément pour Control pour Controls pour View (Format)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
