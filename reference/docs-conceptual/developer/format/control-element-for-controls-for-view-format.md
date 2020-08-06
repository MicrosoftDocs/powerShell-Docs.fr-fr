---
title: Control, élément de Controls pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13ea2f09aec7fea8e5460197f133b5f5219cd369
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783804"
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
