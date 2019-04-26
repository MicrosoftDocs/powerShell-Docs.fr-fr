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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066326"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="6804f-102">Définition de conditions pour l’affichage de données</span><span class="sxs-lookup"><span data-stu-id="6804f-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="6804f-103">Lorsque vous définissez les données affichées par une vue ou d’un contrôle, vous pouvez spécifier une condition qui doit exister pour les données à afficher.</span><span class="sxs-lookup"><span data-stu-id="6804f-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="6804f-104">La condition peut être déclenchée par une propriété spécifique, ou lorsqu’un script ou valeur de propriété a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="6804f-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="6804f-105">Lorsque la condition de sélection est remplie, la définition de la vue ou le contrôle est utilisée.</span><span class="sxs-lookup"><span data-stu-id="6804f-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="6804f-106">Spécification d’une Condition de sélection d’une définition</span><span class="sxs-lookup"><span data-stu-id="6804f-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="6804f-107">Lors de la création d’une définition pour un contrôle, ou un affichage le `EntrySelectedBy` élément est utilisé pour spécifier les objets qui utilisera la définition ou quelle condition doit exister pour la définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="6804f-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="6804f-108">La condition est spécifiée par le `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="6804f-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="6804f-109">Dans l’exemple suivant, une condition de sélection est spécifiée pour une définition d’une vue de table.</span><span class="sxs-lookup"><span data-stu-id="6804f-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="6804f-110">Dans cet exemple, la définition est utilisée uniquement lorsque le script spécifié est évalué à `true`.</span><span class="sxs-lookup"><span data-stu-id="6804f-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="6804f-111">Il n’existe aucune limite au nombre de conditions de sélection que vous pouvez spécifier une définition d’un contrôle ou un affichage.</span><span class="sxs-lookup"><span data-stu-id="6804f-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="6804f-112">Les seules conditions requises sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6804f-112">The only requirements are the following:</span></span>

- <span data-ttu-id="6804f-113">La condition de sélection doit spécifier un nom de propriété ou de script pour déclencher la condition, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="6804f-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="6804f-114">La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="6804f-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="6804f-115">Spécification d’une Condition de sélection d’un élément</span><span class="sxs-lookup"><span data-stu-id="6804f-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="6804f-116">Vous pouvez également spécifier quand un élément d’un affichage de liste ou d’un contrôle est utilisé en incluant le `ItemSelectionCondition` élément dans la définition d’élément.</span><span class="sxs-lookup"><span data-stu-id="6804f-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="6804f-117">Dans l’exemple suivant, une condition de sélection est spécifiée pour un élément d’une vue liste.</span><span class="sxs-lookup"><span data-stu-id="6804f-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="6804f-118">Dans cet exemple, l’élément est utilisé uniquement lorsque le script est évalué à `true`.</span><span class="sxs-lookup"><span data-stu-id="6804f-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="6804f-119">Vous pouvez spécifier le critère de seule sélection pour un élément.</span><span class="sxs-lookup"><span data-stu-id="6804f-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="6804f-120">Et la condition doit spécifier un nom de propriété ou de script pour déclencher la condition, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="6804f-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="6804f-121">Éléments XML</span><span class="sxs-lookup"><span data-stu-id="6804f-121">XML Elements</span></span>

 <span data-ttu-id="6804f-122">Les éléments XML suivants sont utilisés pour créer une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="6804f-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="6804f-123">Les éléments suivants spécifient les conditions de sélection pour afficher les définitions de :</span><span class="sxs-lookup"><span data-stu-id="6804f-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="6804f-124">Élément SelectionCondition pour EntrySelectedBy pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="6804f-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="6804f-125">Élément SelectionCondition pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6804f-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="6804f-126">Élément SelectionCondition pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6804f-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="6804f-127">Élément SelectionCondition pour EntrySelectedBy pour CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6804f-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="6804f-128">Les éléments suivants spécifient la sélection conditions communes et vue contrôlent des définitions :</span><span class="sxs-lookup"><span data-stu-id="6804f-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="6804f-129">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="6804f-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="6804f-130">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="6804f-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="6804f-131">L’élément suivant spécifie la condition de sélection pour le développement d’objets de collection :</span><span class="sxs-lookup"><span data-stu-id="6804f-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="6804f-132">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6804f-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="6804f-133">L’élément suivant spécifie la condition de sélection pour l’affichage d’un nouveau groupe de données :</span><span class="sxs-lookup"><span data-stu-id="6804f-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="6804f-134">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6804f-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="6804f-135">L’élément suivant indique une condition de sélection d’élément pour un affichage de liste :</span><span class="sxs-lookup"><span data-stu-id="6804f-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="6804f-136">Élément ItemSelectionCondition pour ListItem pour un objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6804f-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="6804f-137">Les éléments suivants spécifient une condition de sélection d’élément pour les contrôles :</span><span class="sxs-lookup"><span data-stu-id="6804f-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="6804f-138">Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="6804f-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="6804f-139">Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="6804f-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="6804f-140">Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6804f-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="6804f-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6804f-141">See Also</span></span>

[<span data-ttu-id="6804f-142">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="6804f-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
