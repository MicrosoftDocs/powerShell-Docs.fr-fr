---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)
description: EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)
ms.openlocfilehash: 5af4abe081ca268699d281a1b586a584107b9a83
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652361"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="0003d-103">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0003d-103">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="0003d-104">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="0003d-104">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="0003d-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="0003d-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="0003d-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) EntrySelectedBy élément pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0003d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0003d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0003d-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0003d-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0003d-108">Attributes and Elements</span></span>

<span data-ttu-id="0003d-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="0003d-109">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="0003d-110">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition.</span><span class="sxs-lookup"><span data-stu-id="0003d-110">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="0003d-111">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="0003d-111">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="0003d-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="0003d-112">Attributes</span></span>

<span data-ttu-id="0003d-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0003d-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0003d-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0003d-114">Child Elements</span></span>

|<span data-ttu-id="0003d-115">Élément</span><span class="sxs-lookup"><span data-stu-id="0003d-115">Element</span></span>|<span data-ttu-id="0003d-116">Description</span><span class="sxs-lookup"><span data-stu-id="0003d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0003d-117">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0003d-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="0003d-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0003d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0003d-119">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="0003d-119">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="0003d-120">SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0003d-120">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="0003d-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0003d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="0003d-122">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="0003d-122">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="0003d-123">TypeName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0003d-123">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="0003d-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0003d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="0003d-125">Spécifie un type .NET qui utilise cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="0003d-125">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0003d-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0003d-126">Parent Elements</span></span>

|<span data-ttu-id="0003d-127">Élément</span><span class="sxs-lookup"><span data-stu-id="0003d-127">Element</span></span>|<span data-ttu-id="0003d-128">Description</span><span class="sxs-lookup"><span data-stu-id="0003d-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0003d-129">CustomEntry, élément pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0003d-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="0003d-130">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="0003d-130">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0003d-131">Notes</span><span class="sxs-lookup"><span data-stu-id="0003d-131">Remarks</span></span>

<span data-ttu-id="0003d-132">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou lorsqu’une valeur de propriété ou un script spécifique prend la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="0003d-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="0003d-133">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0003d-133">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0003d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0003d-134">See Also</span></span>

[<span data-ttu-id="0003d-135">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0003d-135">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="0003d-136">SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0003d-136">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="0003d-137">TypeName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0003d-137">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="0003d-138">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="0003d-138">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="0003d-139">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0003d-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
