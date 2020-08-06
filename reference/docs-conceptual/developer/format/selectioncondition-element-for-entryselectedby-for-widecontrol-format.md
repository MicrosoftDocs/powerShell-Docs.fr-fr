---
title: Élément SelectionCondition pour EntrySelectedBy pour WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4115ad1ee8729ea4fc16bc19698018d2f4ed9be1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772703"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="5114a-102">SelectionCondition, élément pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5114a-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="5114a-103">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="5114a-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="5114a-104">Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour une définition d’entrée étendue.</span><span class="sxs-lookup"><span data-stu-id="5114a-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="5114a-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) EntrySelectedBy élément pour WideEntry (format) SelectionCondition élément pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="5114a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5114a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5114a-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5114a-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5114a-107">Attributes and Elements</span></span>

<span data-ttu-id="5114a-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="5114a-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="5114a-109">Vous devez spécifier un seul `PropertyName` `ScriptBlock` élément ou.</span><span class="sxs-lookup"><span data-stu-id="5114a-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="5114a-110">Les `SelectionSetName` `TypeName` éléments et sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="5114a-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="5114a-111">Vous pouvez spécifier l’un des deux éléments.</span><span class="sxs-lookup"><span data-stu-id="5114a-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5114a-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="5114a-112">Attributes</span></span>

<span data-ttu-id="5114a-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5114a-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5114a-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5114a-114">Child Elements</span></span>

|<span data-ttu-id="5114a-115">Élément</span><span class="sxs-lookup"><span data-stu-id="5114a-115">Element</span></span>|<span data-ttu-id="5114a-116">Description</span><span class="sxs-lookup"><span data-stu-id="5114a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5114a-117">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5114a-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="5114a-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="5114a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5114a-119">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="5114a-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="5114a-120">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="5114a-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="5114a-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="5114a-121">Optional element.</span></span><br /><br /> <span data-ttu-id="5114a-122">Spécifie le bloc de script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="5114a-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="5114a-123">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5114a-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="5114a-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="5114a-124">Optional element.</span></span><br /><br /> <span data-ttu-id="5114a-125">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="5114a-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="5114a-126">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="5114a-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="5114a-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="5114a-127">Optional element.</span></span><br /><br /> <span data-ttu-id="5114a-128">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="5114a-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5114a-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5114a-129">Parent Elements</span></span>

|<span data-ttu-id="5114a-130">Élément</span><span class="sxs-lookup"><span data-stu-id="5114a-130">Element</span></span>|<span data-ttu-id="5114a-131">Description</span><span class="sxs-lookup"><span data-stu-id="5114a-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5114a-132">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5114a-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="5114a-133">Définit les types .NET qui utilisent cette entrée étendue ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="5114a-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5114a-134">Notes</span><span class="sxs-lookup"><span data-stu-id="5114a-134">Remarks</span></span>

<span data-ttu-id="5114a-135">Chaque entrée à largeur unique doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définie.</span><span class="sxs-lookup"><span data-stu-id="5114a-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="5114a-136">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="5114a-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="5114a-137">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="5114a-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="5114a-138">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="5114a-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="5114a-139">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5114a-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="5114a-140">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="5114a-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5114a-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5114a-141">See Also</span></span>

[<span data-ttu-id="5114a-142">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="5114a-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="5114a-143">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="5114a-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5114a-144">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5114a-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="5114a-145">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5114a-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="5114a-146">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="5114a-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="5114a-147">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5114a-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="5114a-148">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="5114a-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="5114a-149">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="5114a-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
