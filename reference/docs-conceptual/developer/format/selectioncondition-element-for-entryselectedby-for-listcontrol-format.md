---
title: Élément SelectionCondition pour EntrySelectedBy pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 29626b181f21d168e1ebf973e01afeb411d9ef54
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772771"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="e8470-102">SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e8470-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="e8470-103">Définit la condition qui doit exister pour utiliser cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="e8470-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="e8470-104">Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour une définition de liste.</span><span class="sxs-lookup"><span data-stu-id="e8470-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="e8470-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e8470-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e8470-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8470-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e8470-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e8470-107">Attributes and Elements</span></span>

<span data-ttu-id="e8470-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="e8470-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e8470-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="e8470-109">Attributes</span></span>

<span data-ttu-id="e8470-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e8470-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e8470-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e8470-111">Child Elements</span></span>

|<span data-ttu-id="e8470-112">Élément</span><span class="sxs-lookup"><span data-stu-id="e8470-112">Element</span></span>|<span data-ttu-id="e8470-113">Description</span><span class="sxs-lookup"><span data-stu-id="e8470-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e8470-114">PropertyName, élément de SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e8470-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="e8470-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e8470-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e8470-116">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e8470-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e8470-117">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e8470-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="e8470-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e8470-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e8470-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e8470-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="e8470-120">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e8470-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="e8470-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e8470-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e8470-122">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="e8470-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="e8470-123">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e8470-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="e8470-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e8470-124">Optional element.</span></span><br /><br /> <span data-ttu-id="e8470-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e8470-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e8470-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e8470-126">Parent Elements</span></span>

|<span data-ttu-id="e8470-127">Élément</span><span class="sxs-lookup"><span data-stu-id="e8470-127">Element</span></span>|<span data-ttu-id="e8470-128">Description</span><span class="sxs-lookup"><span data-stu-id="e8470-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e8470-129">Élément EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e8470-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="e8470-130">Définit les types .NET qui utilisent cette entrée de table ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="e8470-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e8470-131">Notes</span><span class="sxs-lookup"><span data-stu-id="e8470-131">Remarks</span></span>

<span data-ttu-id="e8470-132">lWhen vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="e8470-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="e8470-133">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="e8470-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="e8470-134">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="e8470-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="e8470-135">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e8470-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e8470-136">Pour plus d’informations sur les autres composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e8470-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e8470-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8470-137">See Also</span></span>

[<span data-ttu-id="e8470-138">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="e8470-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e8470-139">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="e8470-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e8470-140">Élément ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e8470-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="e8470-141">Élément SelectionSetName pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e8470-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="e8470-142">Élément TypeName pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e8470-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="e8470-143">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8470-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
