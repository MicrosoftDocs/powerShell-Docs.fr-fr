---
title: Définition des Conditions pour l’affichage des données | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855645"
---
# <a name="defining-conditions-for-displaying-data"></a>Définition de conditions pour l’affichage de données

Lorsque vous définissez les données affichées par une vue ou d’un contrôle, vous pouvez spécifier une condition qui doit exister pour les données à afficher. La condition peut être déclenchée par une propriété spécifique, ou lorsqu’un script ou valeur de propriété a la valeur `true`. Lorsque la condition de sélection est remplie, la définition de la vue ou le contrôle est utilisée.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Spécification d’une Condition de sélection d’une définition

Lors de la création d’une définition pour un contrôle, ou un affichage le `EntrySelectedBy` élément est utilisé pour spécifier les objets qui utilisera la définition ou quelle condition doit exister pour la définition à utiliser. La condition est spécifiée par le `SelectionCondition` élément.

Dans l’exemple suivant, une condition de sélection est spécifiée pour une définition d’une vue de table. Dans cet exemple, la définition est utilisée uniquement lorsque le script spécifié est évalué à `true`.

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

Il n’existe aucune limite au nombre de conditions de sélection que vous pouvez spécifier une définition d’un contrôle ou un affichage. Les seules conditions requises sont les suivantes :

- La condition de sélection doit spécifier un nom de propriété ou de script pour déclencher la condition, mais ne peut pas spécifier à la fois.

- La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.

## <a name="specifying-a-selection-condition-for-an-item"></a>Spécification d’une Condition de sélection d’un élément

Vous pouvez également spécifier quand un élément d’un affichage de liste ou d’un contrôle est utilisé en incluant le `ItemSelectionCondition` élément dans la définition d’élément. Dans l’exemple suivant, une condition de sélection est spécifiée pour un élément d’une vue liste. Dans cet exemple, l’élément est utilisé uniquement lorsque le script est évalué à `true`.

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

Vous pouvez spécifier le critère de seule sélection pour un élément. Et la condition doit spécifier un nom de propriété ou de script pour déclencher la condition, mais ne peut pas spécifier à la fois.

## <a name="xml-elements"></a>Éléments XML

 Les éléments XML suivants sont utilisés pour créer une condition de sélection.

- Les éléments suivants spécifient les conditions de sélection pour afficher les définitions de :

    - [Élément SelectionCondition pour EntrySelectedBy pour la table (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Élément SelectionCondition pour EntrySelectedBy pour ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [Élément SelectionCondition pour EntrySelectedBy pour WideControl (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [Élément SelectionCondition pour EntrySelectedBy pour CustomControl (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- Les éléments suivants spécifient la sélection conditions communes et vue contrôlent des définitions :

    - [Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [Élément SelectionCondition pour EntrySelectedBy pour les contrôles de vue (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- L’élément suivant spécifie la condition de sélection pour le développement d’objets de collection :

    - [Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- L’élément suivant spécifie la condition de sélection pour l’affichage d’un nouveau groupe de données :

    - [Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- L’élément suivant indique une condition de sélection d’élément pour un affichage de liste :

    - [Élément ItemSelectionCondition pour ListItem pour un objet ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Les éléments suivants spécifient une condition de sélection d’élément pour les contrôles :

    - [Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de Configuration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de vue (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
