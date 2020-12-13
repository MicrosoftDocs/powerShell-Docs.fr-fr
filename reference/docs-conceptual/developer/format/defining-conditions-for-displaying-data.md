---
ms.date: 09/13/2016
ms.topic: reference
title: Définition de conditions pour l’affichage de données
description: Définition de conditions pour l’affichage de données
ms.openlocfilehash: 9a8b7a618da8c64de978c13b527435a2d7793677
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660311"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="5b6bc-103">Définition de conditions pour l’affichage de données</span><span class="sxs-lookup"><span data-stu-id="5b6bc-103">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="5b6bc-104">Lorsque vous définissez les données affichées par un affichage ou un contrôle, vous pouvez spécifier une condition qui doit exister pour que les données soient affichées.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-104">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="5b6bc-105">La condition peut être déclenchée par une propriété spécifique, ou lorsqu’un script ou une valeur de propriété prend la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="5b6bc-105">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="5b6bc-106">Lorsque la condition de sélection est remplie, la définition de la vue ou du contrôle est utilisée.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-106">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="5b6bc-107">Spécification d’une condition de sélection pour une définition</span><span class="sxs-lookup"><span data-stu-id="5b6bc-107">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="5b6bc-108">Lorsque vous créez une définition pour une vue ou un contrôle, l' `EntrySelectedBy` élément est utilisé pour spécifier les objets qui utiliseront la définition ou la condition qui doit exister pour la définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-108">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="5b6bc-109">La condition est spécifiée par l' `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-109">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="5b6bc-110">Dans l’exemple suivant, une condition de sélection est spécifiée pour une définition d’une vue de table.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-110">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="5b6bc-111">Dans cet exemple, la définition est utilisée uniquement lorsque le script spécifié est évalué `true` .</span><span class="sxs-lookup"><span data-stu-id="5b6bc-111">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="5b6bc-112">Il n’existe aucune limite au nombre de conditions de sélection que vous pouvez spécifier pour une définition d’une vue ou d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-112">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="5b6bc-113">Les seules conditions requises sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="5b6bc-113">The only requirements are the following:</span></span>

- <span data-ttu-id="5b6bc-114">La condition de sélection doit spécifier un nom de propriété ou un script pour déclencher la condition, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-114">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="5b6bc-115">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-115">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="5b6bc-116">Spécification d’une condition de sélection pour un élément</span><span class="sxs-lookup"><span data-stu-id="5b6bc-116">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="5b6bc-117">Vous pouvez également spécifier quand un élément d’un contrôle ou d’un contrôle List est utilisé en incluant l' `ItemSelectionCondition` élément dans la définition de l’élément.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-117">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="5b6bc-118">Dans l’exemple suivant, une condition de sélection est spécifiée pour un élément d’un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-118">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="5b6bc-119">Dans cet exemple, l’élément est utilisé uniquement lorsque le script est évalué à `true` .</span><span class="sxs-lookup"><span data-stu-id="5b6bc-119">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="5b6bc-120">Vous ne pouvez spécifier qu’une seule condition de sélection pour un élément.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-120">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="5b6bc-121">Et la condition doit spécifier un nom de propriété ou un script pour déclencher la condition, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-121">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="5b6bc-122">Éléments XML</span><span class="sxs-lookup"><span data-stu-id="5b6bc-122">XML Elements</span></span>

 <span data-ttu-id="5b6bc-123">Les éléments XML suivants sont utilisés pour créer une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-123">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="5b6bc-124">Les éléments suivants spécifient des conditions de sélection pour les définitions de vues :</span><span class="sxs-lookup"><span data-stu-id="5b6bc-124">The following elements specify selection conditions for view definitions:</span></span>

  - [<span data-ttu-id="5b6bc-125">SelectionCondition, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5b6bc-125">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="5b6bc-126">SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5b6bc-126">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

  - [<span data-ttu-id="5b6bc-127">SelectionCondition, élément pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5b6bc-127">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

  - [<span data-ttu-id="5b6bc-128">SelectionCondition, élément pour EntrySelectedBy pour CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5b6bc-128">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="5b6bc-129">Les éléments suivants spécifient des conditions de sélection pour les définitions courantes et de contrôle d’affichage :</span><span class="sxs-lookup"><span data-stu-id="5b6bc-129">The following elements specify selection conditions for common and view control definitions:</span></span>

  - [<span data-ttu-id="5b6bc-130">SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5b6bc-130">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="5b6bc-131">SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="5b6bc-131">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="5b6bc-132">L’élément suivant spécifie la condition de sélection pour le développement des objets de collection :</span><span class="sxs-lookup"><span data-stu-id="5b6bc-132">The following element specifies the selection condition for expanding collection objects:</span></span>

  - [<span data-ttu-id="5b6bc-133">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="5b6bc-133">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="5b6bc-134">L’élément suivant spécifie la condition de sélection pour l’affichage d’un nouveau groupe de données :</span><span class="sxs-lookup"><span data-stu-id="5b6bc-134">The following element specifies the selection condition for displaying a new group of data:</span></span>

  - [<span data-ttu-id="5b6bc-135">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5b6bc-135">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="5b6bc-136">L’élément suivant spécifie une condition de sélection d’élément pour un mode liste :</span><span class="sxs-lookup"><span data-stu-id="5b6bc-136">The following element specifies an item selection condition for a list view:</span></span>

  - [<span data-ttu-id="5b6bc-137">ItemSelectionCondition, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5b6bc-137">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="5b6bc-138">Les éléments suivants spécifient une condition de sélection d’élément pour les contrôles :</span><span class="sxs-lookup"><span data-stu-id="5b6bc-138">The following elements specify an item selection condition for controls:</span></span>

  - [<span data-ttu-id="5b6bc-139">ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5b6bc-139">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="5b6bc-140">ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="5b6bc-140">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

  - [<span data-ttu-id="5b6bc-141">ItemSelectionCondition, élément pour ExpressionBinding pour CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5b6bc-141">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="5b6bc-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b6bc-142">See Also</span></span>

[<span data-ttu-id="5b6bc-143">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="5b6bc-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
