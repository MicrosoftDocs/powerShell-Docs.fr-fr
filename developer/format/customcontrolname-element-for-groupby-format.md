---
title: Élément CustomControlName pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066536"
---
# <a name="customcontrolname-element-for-groupby-format"></a>CustomControlName, élément pour GroupBy (Format)

Spécifie le nom d’un contrôle personnalisé qui est utilisé pour afficher le nouveau groupe. Cet élément est utilisé lors de la définition d’une table, la liste, l’affichage de contrôle de larges ou personnalisé.

Configuration élément (Format) élément ViewDefinitions (Format) (Format) d’élément GroupBy élément d’affichage pour élément d’affichage (Format) de CustomControlName de GroupBy (Format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de la `CustomControlName` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément GroupBy de vue (Format)](./groupby-element-for-view-format.md)|Définit la façon dont Windows PowerShell affiche un nouveau groupe d’objets.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom du contrôle personnalisé qui est utilisé pour afficher un nouveau groupe.

## <a name="remarks"></a>Remarques

Vous pouvez créer des contrôles communs qui peuvent être utilisées par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisées par une vue spécifique. Les éléments suivants spécifient les noms de ces contrôles personnalisés :

- [Name, élément pour le contrôle pour les contrôles de Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name, élément pour le contrôle pour les contrôles de vue (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[Élément GroupBy de vue (Format)](./groupby-element-for-view-format.md)

[Name, élément pour le contrôle pour les contrôles de Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name, élément pour le contrôle pour les contrôles de vue (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
