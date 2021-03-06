---
ms.date: 09/13/2016
ms.topic: reference
title: Control, élément pour Controls pour Configuration (Format)
description: Control, élément pour Controls pour Configuration (Format)
ms.openlocfilehash: 43424de025cb89d81533e973abd7c39c09533747
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655656"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Control, élément pour Controls pour Configuration (Format)

Définit un contrôle commun qui peut être utilisé par toutes les vues du fichier de mise en forme et le nom utilisé pour référencer le contrôle.

Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format)

## <a name="syntax"></a>Syntaxe

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Control` élément. Vous devez spécifier un seul élément enfant.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[CustomControl, élément pour Control pour Controls (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Élément requis.<br /><br /> Définit le contrôle.|
|[Élément Name pour le contrôle de la configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)|Élément requis.<br /><br /> Spécifie le nom utilisé pour référencer le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément Controls de configuration (format)](./controls-element-for-configuration-format.md)|Définit les contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme ou par d’autres contrôles.|

## <a name="remarks"></a>Notes

Le nom donné à ce contrôle peut être référencé dans les éléments suivants :

- [Élément ExpressionBinding pour CustomItem (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [GroupBy, élément de View (format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[Élément Controls de configuration (format)](./controls-element-for-configuration-format.md)

[CustomControl, élément de Control pour la configuration (format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Élément ExpressionBinding pour CustomItem (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[GroupBy, élément de View (format)](./groupby-element-for-view-format.md)

[Name, élément pour Control pour Controls pour Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
