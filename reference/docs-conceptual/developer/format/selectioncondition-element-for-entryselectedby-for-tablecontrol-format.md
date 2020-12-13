---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition, élément pour EntrySelectedBy pour TableControl (Format)
description: SelectionCondition, élément pour EntrySelectedBy pour TableControl (Format)
ms.openlocfilehash: 22f304615c6433ffb67f3b4046b645d0c37be8a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645759"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="48b6b-103">SelectionCondition, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="48b6b-103">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="48b6b-104">Définit la condition qui doit exister pour être utilisée pour cette définition de la vue de table.</span><span class="sxs-lookup"><span data-stu-id="48b6b-104">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="48b6b-105">Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour une définition de table.</span><span class="sxs-lookup"><span data-stu-id="48b6b-105">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="48b6b-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry élément (format) EntrySelectedBy élément pour TableRowEntry (format) SelectionCondition élément pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="48b6b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="48b6b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48b6b-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="48b6b-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="48b6b-108">Attributes and Elements</span></span>

<span data-ttu-id="48b6b-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément SelectionCondition.</span><span class="sxs-lookup"><span data-stu-id="48b6b-109">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="48b6b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="48b6b-110">Attributes</span></span>

<span data-ttu-id="48b6b-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="48b6b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="48b6b-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="48b6b-112">Child Elements</span></span>

|<span data-ttu-id="48b6b-113">Élément</span><span class="sxs-lookup"><span data-stu-id="48b6b-113">Element</span></span>|<span data-ttu-id="48b6b-114">Description</span><span class="sxs-lookup"><span data-stu-id="48b6b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48b6b-115">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="48b6b-115">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="48b6b-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="48b6b-116">Optional element.</span></span><br /><br /> <span data-ttu-id="48b6b-117">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="48b6b-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="48b6b-118">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="48b6b-118">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="48b6b-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="48b6b-119">Optional element.</span></span><br /><br /> <span data-ttu-id="48b6b-120">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="48b6b-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="48b6b-121">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="48b6b-121">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="48b6b-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="48b6b-122">Optional element.</span></span><br /><br /> <span data-ttu-id="48b6b-123">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="48b6b-123">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="48b6b-124">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="48b6b-124">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="48b6b-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="48b6b-125">Optional element.</span></span><br /><br /> <span data-ttu-id="48b6b-126">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="48b6b-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="48b6b-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="48b6b-127">Parent Elements</span></span>

|<span data-ttu-id="48b6b-128">Élément</span><span class="sxs-lookup"><span data-stu-id="48b6b-128">Element</span></span>|<span data-ttu-id="48b6b-129">Description</span><span class="sxs-lookup"><span data-stu-id="48b6b-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48b6b-130">Élément EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="48b6b-130">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="48b6b-131">Définit les types .NET qui utilisent cette entrée de table ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="48b6b-131">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="48b6b-132">Notes</span><span class="sxs-lookup"><span data-stu-id="48b6b-132">Remarks</span></span>

<span data-ttu-id="48b6b-133">Au moins un nom de type, un jeu de sélection ou une condition de sélection doivent être définis pour chaque entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="48b6b-133">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="48b6b-134">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="48b6b-134">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="48b6b-135">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="48b6b-135">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="48b6b-136">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="48b6b-136">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="48b6b-137">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="48b6b-137">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="48b6b-138">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="48b6b-138">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="48b6b-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48b6b-139">See Also</span></span>

[<span data-ttu-id="48b6b-140">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="48b6b-140">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="48b6b-141">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="48b6b-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="48b6b-142">Élément EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="48b6b-142">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="48b6b-143">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="48b6b-143">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="48b6b-144">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="48b6b-144">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="48b6b-145">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="48b6b-145">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="48b6b-146">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="48b6b-146">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="48b6b-147">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="48b6b-147">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
