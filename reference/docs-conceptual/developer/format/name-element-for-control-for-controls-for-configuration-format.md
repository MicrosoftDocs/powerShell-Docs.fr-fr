---
ms.date: 09/13/2016
ms.topic: reference
title: Name, élément pour Control pour Controls pour Configuration (Format)
description: Name, élément pour Control pour Controls pour Configuration (Format)
ms.openlocfilehash: 0c1c83f827482886ca742f2c0174e8383f87fb52
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666499"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Name, élément pour Control pour Controls pour Configuration (Format)

Spécifie le nom du contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) contrôle l’élément de configuration (format) élément Control pour les contrôles de configuration (format) élément Name pour le contrôle des contrôles pour la configuration (format)

## <a name="syntax"></a>Syntaxe

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Name` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Control, élément pour Controls pour Configuration (Format)](./control-element-for-controls-for-configuration-format.md)|Définit un contrôle commun qui peut être utilisé par toutes les vues du fichier de mise en forme et le nom utilisé pour référencer le contrôle.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom utilisé pour référencer ce contrôle.

## <a name="remarks"></a>Notes

Le nom spécifié ici peut être utilisé dans les éléments suivants pour référencer ce contrôle.

- Lorsque vous créez une vue de contrôle de table, de liste, étendue ou personnalisée, le contrôle peut être spécifié par l’élément suivant : [GroupBy, élément de View (format)](./groupby-element-for-view-format.md)

- Lors de la création d’un autre contrôle commun, ce contrôle peut être spécifié par l’élément suivant : [ExpressionBinding pour CustomItem pour les contrôles de configuration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- Lorsque vous créez un contrôle qui peut être utilisé par une vue, ce contrôle peut être spécifié par l’élément suivant : [ExpressionBinding élément pour CustomItem pour les contrôles pour View (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[Control, élément pour Controls pour Configuration (Format)](./control-element-for-controls-for-configuration-format.md)

[ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[GroupBy, élément pour View (Format)](./groupby-element-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
