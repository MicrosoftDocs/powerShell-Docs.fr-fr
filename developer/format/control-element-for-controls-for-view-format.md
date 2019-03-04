---
title: Control, élément pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853725"
---
# <a name="control-element-for-controls-for-view--format"></a>Control, élément pour Controls pour View (Format)

Définit un contrôle qui peut être utilisé par la vue et le nom qui est utilisé pour référencer le contrôle.

Configuration élément (Format) ViewDefinitions (Format) vue élément (Format) Controls, élément de contrôle d’élément (Format) pour les contrôles de vue (Format)

## <a name="syntax"></a>Syntaxe

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Control` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Name, élément pour le contrôle de vue (Format)](./name-element-for-control-for-controls-for-view-format.md)|Élément requis.<br /><br /> Spécifie le nom du contrôle.|
|[Élément CustomControl pour le contrôle pour les contrôles de vue (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Élément requis.<br /><br /> Définit le contrôle utilisé par cette vue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de Controls (Format)](./controls-element-for-view-format.md)|Définit les contrôles d’affichage qui peuvent être utilisées par une vue spécifique.|

## <a name="remarks"></a>Remarques

Ce contrôle peut être spécifié par les éléments suivants :

- [Élément CustomControlName pour ExpressionBinding pour les contrôles de vue (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [Élément CustomControlName pour ExpressionBinding pour CustomControl de vue (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [Élément CustomControlName pour ExpressionBinding pour GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [Élément CustomControlName pour GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Voir aussi

[Élément CustomControl pour le contrôle pour les contrôles de vue (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Élément CustomControlName pour ExpressionBinding pour les contrôles de vue (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Élément CustomControlName pour ExpressionBinding pour CustomControl de vue (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Élément CustomControlName pour ExpressionBinding pour GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Élément CustomControlName pour ExpressionBinding pour GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Élément de Controls (Format)](./controls-element-for-view-format.md)

[Name, élément pour le contrôle pour les contrôles de vue (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
