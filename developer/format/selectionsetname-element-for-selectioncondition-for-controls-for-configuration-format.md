---
title: Élément SelectionSetName pour SelectionCondition pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064011"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a>SelectionSetName, élément pour SelectionCondition pour Controls pour Configuration (Format)

Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand les types dans cet ensemble sont présents, la condition est remplie, et l’objet est affiché à l’aide de ce contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour les contrôles pour Élément de CustomEntry de CustomControl pour les contrôles d’élément de EntrySelectedBy Configuration (Format) pour CustomEntry pour les contrôles d’élément de SelectionCondition Configuration (Format) pour EntrySelectedBy pour les contrôles de configuration (Format) Élément de configuration (Format) de SelectionSetName pour SelectionCondition pour les contrôles de Configuration (Format)

## <a name="syntax"></a>Syntaxe

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSetName` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Définit une condition qui doit exister pour la définition du contrôle à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de l’ensemble de la sélection.

## <a name="remarks"></a>Remarques

Les jeux de sélection sont courantes groupes d’objets .NET qui peuvent être utilisées par n’importe quelle vue qui définit le fichier de mise en forme. Pour plus d’informations sur la création et en faisant référence à des jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).

La condition de sélection peut spécifier un jeu de sélection ou d’un type .NET, mais ne peut pas spécifier à la fois. Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md)

[Définition de jeux de sélection](./defining-selection-sets.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
