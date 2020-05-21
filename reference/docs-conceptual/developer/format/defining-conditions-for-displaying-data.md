---
title: Définition des conditions d’affichage des données | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 6036f30816e253b3f0c40c6b916279d0643acdb8
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692489"
---
# <a name="defining-conditions-for-displaying-data"></a>Définition de conditions pour l’affichage de données

Lorsque vous définissez les données affichées par un affichage ou un contrôle, vous pouvez spécifier une condition qui doit exister pour que les données soient affichées. La condition peut être déclenchée par une propriété spécifique, ou lorsqu’un script ou une valeur de propriété prend la valeur `true` . Lorsque la condition de sélection est remplie, la définition de la vue ou du contrôle est utilisée.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Spécification d’une condition de sélection pour une définition

Lorsque vous créez une définition pour une vue ou un contrôle, l' `EntrySelectedBy` élément est utilisé pour spécifier les objets qui utiliseront la définition ou la condition qui doit exister pour la définition à utiliser. La condition est spécifiée par l' `SelectionCondition` élément.

Dans l’exemple suivant, une condition de sélection est spécifiée pour une définition d’une vue de table. Dans cet exemple, la définition est utilisée uniquement lorsque le script spécifié est évalué `true` .

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

Il n’existe aucune limite au nombre de conditions de sélection que vous pouvez spécifier pour une définition d’une vue ou d’un contrôle. Les seules conditions requises sont les suivantes :

- La condition de sélection doit spécifier un nom de propriété ou un script pour déclencher la condition, mais ne peut pas spécifier les deux.

- La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.

## <a name="specifying-a-selection-condition-for-an-item"></a>Spécification d’une condition de sélection pour un élément

Vous pouvez également spécifier quand un élément d’un contrôle ou d’un contrôle List est utilisé en incluant l' `ItemSelectionCondition` élément dans la définition de l’élément. Dans l’exemple suivant, une condition de sélection est spécifiée pour un élément d’un affichage de liste. Dans cet exemple, l’élément est utilisé uniquement lorsque le script est évalué à `true` .

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

Vous ne pouvez spécifier qu’une seule condition de sélection pour un élément. Et la condition doit spécifier un nom de propriété ou un script pour déclencher la condition, mais ne peut pas spécifier les deux.

## <a name="xml-elements"></a>Éléments XML

 Les éléments XML suivants sont utilisés pour créer une condition de sélection.

- Les éléments suivants spécifient des conditions de sélection pour les définitions de vues :

  - [SelectionCondition, élément pour EntrySelectedBy pour TableControl (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

  - [SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

  - [SelectionCondition, élément pour EntrySelectedBy pour WideControl (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

  - [SelectionCondition, élément pour EntrySelectedBy pour CustomControl (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- Les éléments suivants spécifient des conditions de sélection pour les définitions courantes et de contrôle d’affichage :

  - [SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

  - [SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- L’élément suivant spécifie la condition de sélection pour le développement des objets de collection :

  - [SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- L’élément suivant spécifie la condition de sélection pour l’affichage d’un nouveau groupe de données :

  - [SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- L’élément suivant spécifie une condition de sélection d’élément pour un mode liste :

  - [ItemSelectionCondition, élément pour ListItem pour ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Les éléments suivants spécifient une condition de sélection d’élément pour les contrôles :

  - [ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

  - [ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour View (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

  - [ItemSelectionCondition, élément pour ExpressionBinding pour CustomControl (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
