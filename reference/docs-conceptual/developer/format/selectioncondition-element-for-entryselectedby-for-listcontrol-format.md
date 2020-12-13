---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)
description: SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)
ms.openlocfilehash: e93499691dd0046265e43abd26497b2974546083
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655096"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="0239f-103">SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0239f-103">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="0239f-104">Définit la condition qui doit exister pour utiliser cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="0239f-104">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="0239f-105">Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour une définition de liste.</span><span class="sxs-lookup"><span data-stu-id="0239f-105">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="0239f-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0239f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0239f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0239f-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0239f-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0239f-108">Attributes and Elements</span></span>

<span data-ttu-id="0239f-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="0239f-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0239f-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0239f-110">Attributes</span></span>

<span data-ttu-id="0239f-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0239f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0239f-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0239f-112">Child Elements</span></span>

|<span data-ttu-id="0239f-113">Élément</span><span class="sxs-lookup"><span data-stu-id="0239f-113">Element</span></span>|<span data-ttu-id="0239f-114">Description</span><span class="sxs-lookup"><span data-stu-id="0239f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0239f-115">PropertyName, élément de SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0239f-115">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="0239f-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0239f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="0239f-117">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="0239f-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="0239f-118">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0239f-118">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="0239f-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0239f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="0239f-120">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="0239f-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="0239f-121">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0239f-121">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="0239f-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0239f-122">Optional element.</span></span><br /><br /> <span data-ttu-id="0239f-123">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="0239f-123">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="0239f-124">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0239f-124">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="0239f-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0239f-125">Optional element.</span></span><br /><br /> <span data-ttu-id="0239f-126">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="0239f-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0239f-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0239f-127">Parent Elements</span></span>

|<span data-ttu-id="0239f-128">Élément</span><span class="sxs-lookup"><span data-stu-id="0239f-128">Element</span></span>|<span data-ttu-id="0239f-129">Description</span><span class="sxs-lookup"><span data-stu-id="0239f-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0239f-130">Élément EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0239f-130">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="0239f-131">Définit les types .NET qui utilisent cette entrée de table ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="0239f-131">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0239f-132">Notes</span><span class="sxs-lookup"><span data-stu-id="0239f-132">Remarks</span></span>

<span data-ttu-id="0239f-133">lWhen vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="0239f-133">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="0239f-134">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="0239f-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="0239f-135">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="0239f-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="0239f-136">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0239f-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="0239f-137">Pour plus d’informations sur les autres composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="0239f-137">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0239f-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0239f-138">See Also</span></span>

[<span data-ttu-id="0239f-139">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="0239f-139">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0239f-140">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="0239f-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="0239f-141">Élément ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0239f-141">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="0239f-142">Élément SelectionSetName pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0239f-142">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="0239f-143">Élément TypeName pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0239f-143">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="0239f-144">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0239f-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
