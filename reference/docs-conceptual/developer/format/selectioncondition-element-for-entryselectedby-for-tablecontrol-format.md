---
title: Élément SelectionCondition pour EntrySelectedBy pour table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4a829f9daef22c4b3fd6b21dfb3af2f8539bdeb3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780285"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="be4aa-102">SelectionCondition, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="be4aa-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="be4aa-103">Définit la condition qui doit exister pour être utilisée pour cette définition de la vue de table.</span><span class="sxs-lookup"><span data-stu-id="be4aa-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="be4aa-104">Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour une définition de table.</span><span class="sxs-lookup"><span data-stu-id="be4aa-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="be4aa-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry élément (format) EntrySelectedBy élément pour TableRowEntry (format) SelectionCondition élément pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="be4aa-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="be4aa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be4aa-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="be4aa-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="be4aa-107">Attributes and Elements</span></span>

<span data-ttu-id="be4aa-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément SelectionCondition.</span><span class="sxs-lookup"><span data-stu-id="be4aa-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="be4aa-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="be4aa-109">Attributes</span></span>

<span data-ttu-id="be4aa-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="be4aa-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="be4aa-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="be4aa-111">Child Elements</span></span>

|<span data-ttu-id="be4aa-112">Élément</span><span class="sxs-lookup"><span data-stu-id="be4aa-112">Element</span></span>|<span data-ttu-id="be4aa-113">Description</span><span class="sxs-lookup"><span data-stu-id="be4aa-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="be4aa-114">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="be4aa-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="be4aa-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="be4aa-115">Optional element.</span></span><br /><br /> <span data-ttu-id="be4aa-116">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="be4aa-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="be4aa-117">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="be4aa-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="be4aa-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="be4aa-118">Optional element.</span></span><br /><br /> <span data-ttu-id="be4aa-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="be4aa-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="be4aa-120">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="be4aa-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="be4aa-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="be4aa-121">Optional element.</span></span><br /><br /> <span data-ttu-id="be4aa-122">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="be4aa-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="be4aa-123">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="be4aa-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="be4aa-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="be4aa-124">Optional element.</span></span><br /><br /> <span data-ttu-id="be4aa-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="be4aa-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="be4aa-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="be4aa-126">Parent Elements</span></span>

|<span data-ttu-id="be4aa-127">Élément</span><span class="sxs-lookup"><span data-stu-id="be4aa-127">Element</span></span>|<span data-ttu-id="be4aa-128">Description</span><span class="sxs-lookup"><span data-stu-id="be4aa-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="be4aa-129">Élément EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="be4aa-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="be4aa-130">Définit les types .NET qui utilisent cette entrée de table ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="be4aa-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="be4aa-131">Notes</span><span class="sxs-lookup"><span data-stu-id="be4aa-131">Remarks</span></span>

<span data-ttu-id="be4aa-132">Au moins un nom de type, un jeu de sélection ou une condition de sélection doivent être définis pour chaque entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="be4aa-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="be4aa-133">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="be4aa-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="be4aa-134">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="be4aa-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="be4aa-135">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="be4aa-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="be4aa-136">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="be4aa-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="be4aa-137">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="be4aa-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="be4aa-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be4aa-138">See Also</span></span>

[<span data-ttu-id="be4aa-139">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="be4aa-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="be4aa-140">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="be4aa-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="be4aa-141">Élément EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="be4aa-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="be4aa-142">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="be4aa-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="be4aa-143">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="be4aa-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="be4aa-144">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="be4aa-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="be4aa-145">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="be4aa-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="be4aa-146">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="be4aa-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
