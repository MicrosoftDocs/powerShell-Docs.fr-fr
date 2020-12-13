---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)
description: SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)
ms.openlocfilehash: 14c293b6bc6d6accc201de35be9219349079801d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664747"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="1e3e7-103">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1e3e7-103">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="1e3e7-104">Définit une condition qui doit exister pour une définition de contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="1e3e7-104">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="1e3e7-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="1e3e7-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1e3e7-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) EntrySelectedBy élément pour CustomEntry pour GroupBy (format) élément SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="1e3e7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1e3e7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e3e7-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1e3e7-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1e3e7-108">Attributes and Elements</span></span>

<span data-ttu-id="1e3e7-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="1e3e7-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1e3e7-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="1e3e7-110">Attributes</span></span>

<span data-ttu-id="1e3e7-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1e3e7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1e3e7-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1e3e7-112">Child Elements</span></span>

|<span data-ttu-id="1e3e7-113">Élément</span><span class="sxs-lookup"><span data-stu-id="1e3e7-113">Element</span></span>|<span data-ttu-id="1e3e7-114">Description</span><span class="sxs-lookup"><span data-stu-id="1e3e7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e3e7-115">PropertyName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1e3e7-115">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="1e3e7-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1e3e7-116">Optional element.</span></span><br /><br /> <span data-ttu-id="1e3e7-117">Spécifie une propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="1e3e7-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="1e3e7-118">Élément ScriptBlock pour SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="1e3e7-118">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="1e3e7-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1e3e7-119">Optional element.</span></span><br /><br /> <span data-ttu-id="1e3e7-120">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="1e3e7-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="1e3e7-121">SelectionSetName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1e3e7-121">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="1e3e7-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1e3e7-122">Optional element.</span></span><br /><br /> <span data-ttu-id="1e3e7-123">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="1e3e7-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="1e3e7-124">Élément TypeName pour SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="1e3e7-124">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="1e3e7-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1e3e7-125">Optional element.</span></span><br /><br /> <span data-ttu-id="1e3e7-126">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="1e3e7-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1e3e7-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1e3e7-127">Parent Elements</span></span>

|<span data-ttu-id="1e3e7-128">Élément</span><span class="sxs-lookup"><span data-stu-id="1e3e7-128">Element</span></span>|<span data-ttu-id="1e3e7-129">Description</span><span class="sxs-lookup"><span data-stu-id="1e3e7-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e3e7-130">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1e3e7-130">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="1e3e7-131">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="1e3e7-131">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1e3e7-132">Notes</span><span class="sxs-lookup"><span data-stu-id="1e3e7-132">Remarks</span></span>

<span data-ttu-id="1e3e7-133">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="1e3e7-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="1e3e7-134">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="1e3e7-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="1e3e7-135">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="1e3e7-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="1e3e7-136">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1e3e7-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1e3e7-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e3e7-137">See Also</span></span>

[<span data-ttu-id="1e3e7-138">PropertyName, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="1e3e7-138">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1e3e7-139">ScriptBlock, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="1e3e7-139">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1e3e7-140">Élément SelectionSetName pour SelectionCondition pour un contrôle personnalisé pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1e3e7-140">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1e3e7-141">Élément TypeName pour SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="1e3e7-141">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="1e3e7-142">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1e3e7-142">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="1e3e7-143">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e3e7-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
