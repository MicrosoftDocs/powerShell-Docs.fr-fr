---
title: Nom d’élément pour le contrôle pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860085"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Name, élément pour Control pour Controls pour Configuration (Format)

Spécifie le nom du contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de nom de Configuration (Format) pour le contrôle pour les contrôles de Configuration (Format)

## <a name="syntax"></a>Syntaxe

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Name` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de contrôle pour les contrôles de Configuration (Format)](./control-element-for-controls-for-configuration-format.md)|Définit un contrôle commun qui peut être utilisé par toutes les vues de la mise en forme du fichier et le nom qui est utilisé pour référencer le contrôle.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom qui est utilisé pour référencer ce contrôle.

## <a name="remarks"></a>Remarques

Le nom spécifié ici peut être utilisé dans les éléments suivants pour référencer ce contrôle.

- Lorsque vous créez une table, la liste, l’affichage de contrôle de larges ou personnalisés, le contrôle peut être spécifié par l’élément suivant : [Élément GroupBy de vue (Format)](./groupby-element-for-view-format.md)

- Lorsque vous créez un autre contrôle commun, ce contrôle peut être spécifié par l’élément suivant : [Élément ExpressionBinding pour CustomItem pour les contrôles de Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- Lors de la création d’un contrôle qui peut être utilisé par une vue, ce contrôle peut être spécifié par l’élément suivant : [Élément ExpressionBinding pour CustomItem pour les contrôles de vue (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[Élément de contrôle pour les contrôles de Configuration (Format)](./control-element-for-controls-for-configuration-format.md)

[Élément ExpressionBinding pour CustomItem pour les contrôles de Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Élément ExpressionBinding pour CustomItem pour les contrôles de vue (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Élément GroupBy de vue (Format)](./groupby-element-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
