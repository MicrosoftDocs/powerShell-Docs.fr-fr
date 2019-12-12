---
title: Control, élément de Controls pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363468"
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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Control`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément Name pour le contrôle pour View (format)](./name-element-for-control-for-controls-for-view-format.md)|Élément requis.<br /><br /> Spécifie le nom du contrôle.|
|[CustomControl, élément de Control pour les contrôles pour View (format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Élément requis.<br /><br /> Définit le contrôle utilisé par cette vue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément Controls (format)](./controls-element-for-view-format.md)|Définit les contrôles d’affichage qui peuvent être utilisés par une vue spécifique.|

## <a name="remarks"></a>Remarks

Ce contrôle peut être spécifié par les éléments suivants :

- [Élément CustomControlName pour ExpressionBinding pour les contrôles pour View (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [Élément CustomControlName pour ExpressionBinding pour CustomControl pour View (format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [Élément CustomControlName pour ExpressionBinding pour GroupBy (format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [Élément CustomControlName pour GroupBy (format)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Voir aussi

[CustomControl, élément de Control pour les contrôles pour View (format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Élément CustomControlName pour ExpressionBinding pour les contrôles pour View (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Élément CustomControlName pour ExpressionBinding pour CustomControl pour View (format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Élément CustomControlName pour ExpressionBinding pour GroupBy (format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Élément CustomControlName pour ExpressionBinding pour GroupBy (format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Élément Controls (format)](./controls-element-for-view-format.md)

[Élément Name pour le contrôle des contrôles pour View (format)](./name-element-for-control-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
