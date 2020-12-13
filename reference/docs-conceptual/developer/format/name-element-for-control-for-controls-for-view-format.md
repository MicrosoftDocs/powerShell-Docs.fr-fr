---
ms.date: 09/13/2016
ms.topic: reference
title: Name, élément pour Control pour Controls pour View (Format)
description: Name, élément pour Control pour Controls pour View (Format)
ms.openlocfilehash: 52b7170777a35596767c34f2d58106dfa6479567
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666482"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Name, élément pour Control pour Controls pour View (Format)

Spécifie le nom du contrôle.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour l’élément View (format) Name pour le contrôle pour View (format)

## <a name="syntax"></a>Syntaxe

```xml
<Name>ControlName</Name>
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
|[Control, élément de Controls pour View (format)](./control-element-for-controls-for-view-format.md)|Définit un contrôle qui peut être utilisé par la vue et le nom utilisé pour référencer le contrôle.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom utilisé pour référencer le contrôle.

## <a name="remarks"></a>Notes

Le nom spécifié ici peut être utilisé dans les éléments suivants pour référencer ce contrôle.

- Lorsque vous créez une vue de contrôle de table, de liste, étendue ou personnalisée, le contrôle peut être spécifié par l’élément suivant : [GroupBy, élément de View (format)](./groupby-element-for-view-format.md)

- Lorsque vous créez un autre contrôle qui peut être utilisé par une vue, ce contrôle peut être spécifié par l’élément suivant : [ExpressionBinding élément pour CustomItem pour les contrôles pour View (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[GroupBy, élément pour View (Format)](./groupby-element-for-view-format.md)

[ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Control, élément de Controls pour View (format)](./control-element-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
