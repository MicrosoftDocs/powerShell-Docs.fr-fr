---
title: Control, élément pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858885"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Control, élément pour Controls pour Configuration (Format)

Définit un contrôle commun qui peut être utilisé par toutes les vues de la mise en forme du fichier et le nom qui est utilisé pour référencer le contrôle.

Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles de Configuration (Format)

## <a name="syntax"></a>Syntaxe

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et l’élément parent de la `Control` élément. Vous devez spécifier un seul de chaque élément enfant.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément CustomControl pour le contrôle pour les contrôles de Configuration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Élément requis.<br /><br /> Définit le contrôle.|
|[Name, élément pour le contrôle de Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)|Élément requis.<br /><br /> Spécifie le nom utilisé pour référencer le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de contrôles de Configuration (Format)](./controls-element-for-configuration-format.md)|Définit les contrôles communs qui peuvent être utilisées par toutes les vues du fichier de mise en forme ou par d’autres contrôles.|

## <a name="remarks"></a>Remarques

Le nom donné à ce contrôle peut être référencé dans les éléments suivants :

- [Élément ExpressionBinding pour CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [Élément GroupBy pour View(Format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[Élément de contrôles de Configuration (Format)](./controls-element-for-configuration-format.md)

[Élément CustomControl pour le contrôle de Configuration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Élément ExpressionBinding pour CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Élément GroupBy pour View(Format)](./groupby-element-for-view-format.md)

[Name, élément pour le contrôle pour les contrôles de Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
