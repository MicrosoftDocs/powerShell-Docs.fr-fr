---
title: Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863275"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour TableControl (Format)

Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand les types dans cet ensemble sont présents, la condition est remplie, et l’objet est affiché à l’aide de cette définition de la vue de table.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableRowEntries, élément (Format) élément TableRowEntry (Format) EntrySelectedBy élément de configuration pour TableRowEntry (Format) Élément SelectionCondition pour EntrySelectedBy d’élément de SelectionSetName TableRowEntry (Format) pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)

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
|[Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Définit la condition qui doit exister pour pouvoir le pour utiliser pour cette définition de la vue de table.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de l’ensemble de la sélection.

## <a name="remarks"></a>Remarques

La condition de sélection peut spécifier un jeu de sélection ou d’un type .NET, mais ne peut pas spécifier à la fois. Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).

Les jeux de sélection sont courantes groupes d’objets .NET qui peuvent être utilisées par n’importe quelle vue qui définit le fichier de mise en forme. Pour plus d’informations sur la création et en faisant référence à des jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).

Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [création d’une vue de Table](./creating-a-table-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue de Table](./creating-a-table-view.md)

[Définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md)

[Élément TypeName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
