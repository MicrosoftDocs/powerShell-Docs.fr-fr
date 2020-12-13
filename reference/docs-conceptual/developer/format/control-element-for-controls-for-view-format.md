---
ms.date: 09/13/2016
ms.topic: reference
title: Control, élément pour Controls pour View (Format)
description: Control, élément pour Controls pour View (Format)
ms.openlocfilehash: c48b8b7ecaebfde5e6ed2123b837d92561551766
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668080"
---
# <a name="control-element-for-controls-for-view--format"></a>Control, élément pour Controls pour View (Format)

Définit un contrôle qui peut être utilisé par la vue et le nom utilisé pour référencer le contrôle.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format)

## <a name="syntax"></a>Syntaxe

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Control` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément Name pour le contrôle pour View (format)](./name-element-for-control-for-controls-for-view-format.md)|Élément requis.<br /><br /> Spécifie le nom du contrôle.|
|[CustomControl, élément pour Control pour View (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Élément requis.<br /><br /> Définit le contrôle utilisé par cette vue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément Controls (format)](./controls-element-for-view-format.md)|Définit les contrôles d’affichage qui peuvent être utilisés par une vue spécifique.|

## <a name="remarks"></a>Notes

Ce contrôle peut être spécifié par les éléments suivants :

- [CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [CustomControlName, élément pour GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Voir aussi

[CustomControl, élément pour Control pour View (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Élément Controls (format)](./controls-element-for-view-format.md)

[Name, élément pour Control pour Controls pour View (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
