---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition, élément pour EntrySelectedBy pour WideControl (Format)
description: SelectionCondition, élément pour EntrySelectedBy pour WideControl (Format)
ms.openlocfilehash: 8c51ca72edc6ad174dc289c61a8987e8f9495d19
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655107"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="0511e-103">SelectionCondition, élément pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0511e-103">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="0511e-104">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="0511e-104">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="0511e-105">Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour une définition d’entrée étendue.</span><span class="sxs-lookup"><span data-stu-id="0511e-105">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="0511e-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) EntrySelectedBy élément pour WideEntry (format) SelectionCondition élément pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="0511e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0511e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0511e-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0511e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0511e-108">Attributes and Elements</span></span>

<span data-ttu-id="0511e-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="0511e-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="0511e-110">Vous devez spécifier un seul `PropertyName` `ScriptBlock` élément ou.</span><span class="sxs-lookup"><span data-stu-id="0511e-110">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="0511e-111">Les `SelectionSetName` `TypeName` éléments et sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="0511e-111">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="0511e-112">Vous pouvez spécifier l’un des deux éléments.</span><span class="sxs-lookup"><span data-stu-id="0511e-112">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0511e-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="0511e-113">Attributes</span></span>

<span data-ttu-id="0511e-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0511e-114">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0511e-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0511e-115">Child Elements</span></span>

|<span data-ttu-id="0511e-116">Élément</span><span class="sxs-lookup"><span data-stu-id="0511e-116">Element</span></span>|<span data-ttu-id="0511e-117">Description</span><span class="sxs-lookup"><span data-stu-id="0511e-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0511e-118">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0511e-118">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="0511e-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0511e-119">Optional element.</span></span><br /><br /> <span data-ttu-id="0511e-120">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="0511e-120">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="0511e-121">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0511e-121">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="0511e-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0511e-122">Optional element.</span></span><br /><br /> <span data-ttu-id="0511e-123">Spécifie le bloc de script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="0511e-123">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="0511e-124">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0511e-124">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="0511e-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0511e-125">Optional element.</span></span><br /><br /> <span data-ttu-id="0511e-126">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="0511e-126">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="0511e-127">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0511e-127">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="0511e-128">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0511e-128">Optional element.</span></span><br /><br /> <span data-ttu-id="0511e-129">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="0511e-129">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0511e-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0511e-130">Parent Elements</span></span>

|<span data-ttu-id="0511e-131">Élément</span><span class="sxs-lookup"><span data-stu-id="0511e-131">Element</span></span>|<span data-ttu-id="0511e-132">Description</span><span class="sxs-lookup"><span data-stu-id="0511e-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0511e-133">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0511e-133">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="0511e-134">Définit les types .NET qui utilisent cette entrée étendue ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="0511e-134">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0511e-135">Notes</span><span class="sxs-lookup"><span data-stu-id="0511e-135">Remarks</span></span>

<span data-ttu-id="0511e-136">Chaque entrée à largeur unique doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définie.</span><span class="sxs-lookup"><span data-stu-id="0511e-136">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="0511e-137">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="0511e-137">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="0511e-138">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="0511e-138">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="0511e-139">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="0511e-139">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="0511e-140">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0511e-140">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="0511e-141">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="0511e-141">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0511e-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0511e-142">See Also</span></span>

[<span data-ttu-id="0511e-143">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="0511e-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="0511e-144">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="0511e-144">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="0511e-145">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0511e-145">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="0511e-146">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0511e-146">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="0511e-147">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0511e-147">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="0511e-148">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0511e-148">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="0511e-149">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0511e-149">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="0511e-150">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0511e-150">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
