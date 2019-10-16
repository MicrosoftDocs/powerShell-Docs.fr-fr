---
title: Élément CustomControlName pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368878"
---
# <a name="customcontrolname-element-for-groupby-format"></a>CustomControlName, élément pour GroupBy (Format)

Spécifie le nom d’un contrôle personnalisé utilisé pour afficher le nouveau groupe. Cet élément est utilisé lors de la définition d’une vue de contrôle de table, de liste, étendue ou personnalisée.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControlName de GroupBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l’élément `CustomControlName`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[GroupBy, élément de View (format)](./groupby-element-for-view-format.md)|Définit la manière dont Windows PowerShell affiche un nouveau groupe d’objets.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du contrôle personnalisé utilisé pour afficher un nouveau groupe.

## <a name="remarks"></a>Remarks

Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique. Les éléments suivants spécifient les noms de ces contrôles personnalisés :

- [Élément Name pour le contrôle des contrôles pour la configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Élément Name pour le contrôle des contrôles pour View (format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Voir aussi

[GroupBy, élément de View (format)](./groupby-element-for-view-format.md)

[Élément Name pour le contrôle des contrôles pour la configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Élément Name pour le contrôle des contrôles pour View (format)](./name-element-for-control-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
