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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363898"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="5df8d-102">Définition de conditions pour l’affichage de données</span><span class="sxs-lookup"><span data-stu-id="5df8d-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="5df8d-103">Lorsque vous définissez les données affichées par un affichage ou un contrôle, vous pouvez spécifier une condition qui doit exister pour que les données soient affichées.</span><span class="sxs-lookup"><span data-stu-id="5df8d-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="5df8d-104">La condition peut être déclenchée par une propriété spécifique, ou lorsqu’un script ou une valeur de propriété prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="5df8d-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="5df8d-105">Lorsque la condition de sélection est remplie, la définition de la vue ou du contrôle est utilisée.</span><span class="sxs-lookup"><span data-stu-id="5df8d-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="5df8d-106">Spécification d’une condition de sélection pour une définition</span><span class="sxs-lookup"><span data-stu-id="5df8d-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="5df8d-107">Lorsque vous créez une définition pour une vue ou un contrôle, l’élément `EntrySelectedBy` est utilisé pour spécifier les objets qui utiliseront la définition ou la condition qui doit exister pour la définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5df8d-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="5df8d-108">La condition est spécifiée par l’élément `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="5df8d-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="5df8d-109">Dans l’exemple suivant, une condition de sélection est spécifiée pour une définition d’une vue de table.</span><span class="sxs-lookup"><span data-stu-id="5df8d-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="5df8d-110">Dans cet exemple, la définition est utilisée uniquement lorsque le script spécifié est évalué à `true`.</span><span class="sxs-lookup"><span data-stu-id="5df8d-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="5df8d-111">Il n’existe aucune limite au nombre de conditions de sélection que vous pouvez spécifier pour une définition d’une vue ou d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="5df8d-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="5df8d-112">Les seules conditions requises sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="5df8d-112">The only requirements are the following:</span></span>

- <span data-ttu-id="5df8d-113">La condition de sélection doit spécifier un nom de propriété ou un script pour déclencher la condition, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="5df8d-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="5df8d-114">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="5df8d-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="5df8d-115">Spécification d’une condition de sélection pour un élément</span><span class="sxs-lookup"><span data-stu-id="5df8d-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="5df8d-116">Vous pouvez également spécifier quand un élément d’un contrôle ou d’un contrôle List est utilisé en incluant l’élément `ItemSelectionCondition` dans la définition de l’élément.</span><span class="sxs-lookup"><span data-stu-id="5df8d-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="5df8d-117">Dans l’exemple suivant, une condition de sélection est spécifiée pour un élément d’un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="5df8d-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="5df8d-118">Dans cet exemple, l’élément est utilisé uniquement lorsque le script est évalué à `true`.</span><span class="sxs-lookup"><span data-stu-id="5df8d-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="5df8d-119">Vous ne pouvez spécifier qu’une seule condition de sélection pour un élément.</span><span class="sxs-lookup"><span data-stu-id="5df8d-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="5df8d-120">Et la condition doit spécifier un nom de propriété ou un script pour déclencher la condition, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="5df8d-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="5df8d-121">Éléments XML</span><span class="sxs-lookup"><span data-stu-id="5df8d-121">XML Elements</span></span>

 <span data-ttu-id="5df8d-122">Les éléments XML suivants sont utilisés pour créer une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="5df8d-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="5df8d-123">Les éléments suivants spécifient des conditions de sélection pour les définitions de vues :</span><span class="sxs-lookup"><span data-stu-id="5df8d-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="5df8d-124">Élément SelectionCondition pour EntrySelectedBy pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="5df8d-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="5df8d-125">Élément SelectionCondition pour EntrySelectedBy pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="5df8d-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="5df8d-126">Élément SelectionCondition pour EntrySelectedBy pour WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="5df8d-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="5df8d-127">Élément SelectionCondition pour EntrySelectedBy pour CustomControl (format)</span><span class="sxs-lookup"><span data-stu-id="5df8d-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="5df8d-128">Les éléments suivants spécifient des conditions de sélection pour les définitions courantes et de contrôle d’affichage :</span><span class="sxs-lookup"><span data-stu-id="5df8d-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="5df8d-129">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5df8d-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="5df8d-130">Élément SelectionCondition pour EntrySelectedBy pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="5df8d-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="5df8d-131">L’élément suivant spécifie la condition de sélection pour le développement des objets de collection :</span><span class="sxs-lookup"><span data-stu-id="5df8d-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="5df8d-132">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="5df8d-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="5df8d-133">L’élément suivant spécifie la condition de sélection pour l’affichage d’un nouveau groupe de données :</span><span class="sxs-lookup"><span data-stu-id="5df8d-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="5df8d-134">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="5df8d-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="5df8d-135">L’élément suivant spécifie une condition de sélection d’élément pour un mode liste :</span><span class="sxs-lookup"><span data-stu-id="5df8d-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="5df8d-136">Élément ItemSelectionCondition pour ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="5df8d-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="5df8d-137">Les éléments suivants spécifient une condition de sélection d’élément pour les contrôles :</span><span class="sxs-lookup"><span data-stu-id="5df8d-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="5df8d-138">Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5df8d-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="5df8d-139">Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="5df8d-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="5df8d-140">Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl (format)</span><span class="sxs-lookup"><span data-stu-id="5df8d-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="5df8d-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5df8d-141">See Also</span></span>

[<span data-ttu-id="5df8d-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="5df8d-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
