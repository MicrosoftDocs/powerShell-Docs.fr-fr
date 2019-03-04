---
title: Élément SelectionSetName pour SelectionCondition pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855115"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a>SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)

Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand les types dans cet ensemble sont présents, la condition est remplie et l’objet est affiché à l’aide de ce contrôle. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour les contrôles d’élément de CustomEntry vue (Format) pour CustomEntries pour les contrôles d’élément de EntrySelectedBy vue (Format) pour CustomEntry pour les contrôles d’élément de SelectionCondition vue (Format) pour EntrySelectedBy pour les contrôles pour afficher ( Format), élément SelectionSetName pour SelectionCondition pour les contrôles de vue (Format)

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
|[Élément SelectionCondition pour EntrySelectedBy pour les contrôles de vue (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Définit une condition qui doit exister pour la définition du contrôle à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de l’ensemble de la sélection.

## <a name="remarks"></a>Remarques

Les jeux de sélection sont courantes groupes d’objets .NET qui peuvent être utilisées par n’importe quelle vue qui définit le fichier de mise en forme. Pour plus d’informations sur la création et en faisant référence à des jeux de sélection, consultez [définition sélection définit](./defining-selection-sets.md).

La condition de sélection peut spécifier un jeu de sélection ou d’un type .NET, mais ne peut pas spécifier à la fois. Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Élément SelectionCondition pour EntrySelectedBy pour les contrôles de vue (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md)

[Définition de jeux de sélection](./defining-selection-sets.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
