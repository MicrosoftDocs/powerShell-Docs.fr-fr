---
title: Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075509"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a>SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)

Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand les types dans cet ensemble sont présents, la condition est remplie, et l’objet est affiché à l’aide de cette définition de la vue de liste.

Configuration élément (Format) ViewDefinitions, élément (Format) vue (Format) d’élément objet ListControl, élément (Format) situés (Format) ListEntry, élément (Format) EntrySelectedBy élément d’élément de SelectionCondition ListEntry (Format) pour EntrySelectedBy d’élément de SelectionSetName ListEntry (Format) pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)

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
|[Élément SelectionCondition pour EntrySelectedBy pour ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Définit la condition qui doit exister pour pouvoir utiliser cette définition de la vue liste.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de l’ensemble de la sélection.

## <a name="remarks"></a>Remarques

La condition de sélection peut spécifier un jeu de sélection ou d’un type .NET, mais ne peut pas spécifier à la fois. Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).

Les jeux de sélection sont courantes groupes d’objets .NET qui peuvent être utilisées par n’importe quelle vue qui définit le fichier de mise en forme. Pour plus d’informations sur la création et en faisant référence à des jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).

Pour plus d’informations sur d’autres composants d’une vue liste, consultez [création d’une vue liste](./creating-a-list-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue liste](./creating-a-list-view.md)

[Définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md)

[Élément SelectionCondition pour EntrySelectedBy pour ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
