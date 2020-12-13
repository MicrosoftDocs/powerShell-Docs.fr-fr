---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)
description: SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)
ms.openlocfilehash: 16b048e73195b3d6168724714ff223851dc1b20b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664850"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="e66e1-103">SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e66e1-103">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="e66e1-104">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="e66e1-104">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="e66e1-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="e66e1-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e66e1-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour les contrôles pour l’élément d’affichage (format) CustomEntry pour CustomEntries pour les contrôles de l’élément EntrySelectedBy (format) pour CustomEntry pour les contrôles de l’élément View (format) SelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="e66e1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e66e1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e66e1-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e66e1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e66e1-108">Attributes and Elements</span></span>

<span data-ttu-id="e66e1-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="e66e1-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e66e1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="e66e1-110">Attributes</span></span>

<span data-ttu-id="e66e1-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e66e1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e66e1-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e66e1-112">Child Elements</span></span>

|<span data-ttu-id="e66e1-113">Élément</span><span class="sxs-lookup"><span data-stu-id="e66e1-113">Element</span></span>|<span data-ttu-id="e66e1-114">Description</span><span class="sxs-lookup"><span data-stu-id="e66e1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e66e1-115">PropertyName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e66e1-115">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="e66e1-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e66e1-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e66e1-117">Spécifie une propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e66e1-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e66e1-118">ScriptBlock, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e66e1-118">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="e66e1-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e66e1-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e66e1-120">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e66e1-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="e66e1-121">SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e66e1-121">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="e66e1-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e66e1-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e66e1-123">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="e66e1-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="e66e1-124">TypeName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e66e1-124">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="e66e1-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e66e1-125">Optional element.</span></span><br /><br /> <span data-ttu-id="e66e1-126">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e66e1-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e66e1-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e66e1-127">Parent Elements</span></span>

|<span data-ttu-id="e66e1-128">Élément</span><span class="sxs-lookup"><span data-stu-id="e66e1-128">Element</span></span>|<span data-ttu-id="e66e1-129">Description</span><span class="sxs-lookup"><span data-stu-id="e66e1-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e66e1-130">EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e66e1-130">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="e66e1-131">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="e66e1-131">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e66e1-132">Notes</span><span class="sxs-lookup"><span data-stu-id="e66e1-132">Remarks</span></span>

<span data-ttu-id="e66e1-133">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="e66e1-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="e66e1-134">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="e66e1-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="e66e1-135">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="e66e1-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="e66e1-136">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e66e1-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e66e1-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e66e1-137">See Also</span></span>

[<span data-ttu-id="e66e1-138">PropertyName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e66e1-138">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="e66e1-139">ScriptBlock, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e66e1-139">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="e66e1-140">SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e66e1-140">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="e66e1-141">TypeName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e66e1-141">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="e66e1-142">EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e66e1-142">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="e66e1-143">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e66e1-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
