---
title: Nom d’élément pour le contrôle pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065091"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Name, élément pour Control pour Controls pour View (Format)

Spécifie le nom du contrôle.

Configuration élément (Format) ViewDefinitions (Format) vue élément (Format) Controls, élément (Format) contrôle élément pour les contrôles pour l’élément de nom d’affichage (Format) pour le contrôle de vue (Format)

## <a name="syntax"></a>Syntaxe

```xml
<Name>ControlName</Name>
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
|[Élément de contrôle pour les contrôles de vue (Format)](./control-element-for-controls-for-view-format.md)|Définit un contrôle qui peut être utilisé par la vue et le nom qui est utilisé pour référencer le contrôle.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom qui est utilisé pour référencer le contrôle.

## <a name="remarks"></a>Remarques

Le nom spécifié ici peut être utilisé dans les éléments suivants pour référencer ce contrôle.

- Lorsque vous créez une table, la liste, l’affichage de contrôle de larges ou personnalisés, le contrôle peut être spécifié par l’élément suivant : [Élément GroupBy de vue (Format)](./groupby-element-for-view-format.md)

- Lors de la création d’un autre contrôle qui peut être utilisé par une vue, ce contrôle peut être spécifié par l’élément suivant : [Élément ExpressionBinding pour CustomItem pour les contrôles de vue (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[Élément GroupBy de vue (Format)](./groupby-element-for-view-format.md)

[Élément ExpressionBinding pour CustomItem pour les contrôles de vue (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Élément de contrôle pour les contrôles de vue (Format)](./control-element-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
