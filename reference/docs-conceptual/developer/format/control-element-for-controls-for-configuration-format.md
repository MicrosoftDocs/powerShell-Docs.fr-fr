---
title: Control, élément de contrôles pour la configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369008"
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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Control`. Vous devez spécifier un seul élément enfant.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[CustomControl, élément de Control pour les contrôles de configuration (format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Élément requis.<br /><br /> Définit le contrôle.|
|[Élément Name pour le contrôle de la configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)|Élément requis.<br /><br /> Spécifie le nom utilisé pour référencer le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément Controls de configuration (format)](./controls-element-for-configuration-format.md)|Définit les contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme ou par d’autres contrôles.|

## <a name="remarks"></a>Remarks

Le nom donné à ce contrôle peut être référencé dans les éléments suivants :

- [Élément ExpressionBinding pour CustomItem (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [GroupBy, élément de View (format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[Élément Controls de configuration (format)](./controls-element-for-configuration-format.md)

[CustomControl, élément de Control pour la configuration (format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Élément ExpressionBinding pour CustomItem (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[GroupBy, élément de View (format)](./groupby-element-for-view-format.md)

[Élément Name pour le contrôle des contrôles pour la configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
