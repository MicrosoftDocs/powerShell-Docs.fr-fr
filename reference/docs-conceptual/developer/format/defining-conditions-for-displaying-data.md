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
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363898"
---
# <a name="defining-conditions-for-displaying-data"></a>Définition de conditions pour l’affichage de données

Lorsque vous définissez les données affichées par un affichage ou un contrôle, vous pouvez spécifier une condition qui doit exister pour que les données soient affichées. La condition peut être déclenchée par une propriété spécifique, ou lorsqu’un script ou une valeur de propriété prend la valeur `true`. Lorsque la condition de sélection est remplie, la définition de la vue ou du contrôle est utilisée.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Spécification d’une condition de sélection pour une définition

Lorsque vous créez une définition pour une vue ou un contrôle, l’élément `EntrySelectedBy` est utilisé pour spécifier les objets qui utiliseront la définition ou la condition qui doit exister pour la définition à utiliser. La condition est spécifiée par l’élément `SelectionCondition`.

Dans l’exemple suivant, une condition de sélection est spécifiée pour une définition d’une vue de table. Dans cet exemple, la définition est utilisée uniquement lorsque le script spécifié est évalué pour `true`.

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

Vous pouvez également spécifier quand un élément d’un contrôle ou d’un contrôle List est utilisé en incluant l’élément `ItemSelectionCondition` dans la définition de l’élément. Dans l’exemple suivant, une condition de sélection est spécifiée pour un élément d’un affichage de liste. Dans cet exemple, l’élément est utilisé uniquement lorsque le script est évalué pour `true`.

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

    - [Élément SelectionCondition pour EntrySelectedBy pour table ((format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Élément SelectionCondition pour EntrySelectedBy pour ListControl (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [Élément SelectionCondition pour EntrySelectedBy pour WideControl (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [Élément SelectionCondition pour EntrySelectedBy pour CustomControl (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- Les éléments suivants spécifient des conditions de sélection pour les définitions courantes et de contrôle d’affichage :

    - [Élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [Élément SelectionCondition pour EntrySelectedBy pour les contrôles pour View (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- L’élément suivant spécifie la condition de sélection pour le développement des objets de collection :

    - [Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- L’élément suivant spécifie la condition de sélection pour l’affichage d’un nouveau groupe de données :

    - [Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- L’élément suivant spécifie une condition de sélection d’élément pour un mode liste :

    - [Élément ItemSelectionCondition pour ListItem pour ListControl (format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Les éléments suivants spécifient une condition de sélection d’élément pour les contrôles :

    - [Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de configuration (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
