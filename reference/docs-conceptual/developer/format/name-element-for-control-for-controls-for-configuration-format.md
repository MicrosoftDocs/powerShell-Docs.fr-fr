---
title: Élément Name pour le contrôle des contrôles pour la configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3d45ba98b909ebee18e01d2b6985a48906ce39d9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783532"
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
