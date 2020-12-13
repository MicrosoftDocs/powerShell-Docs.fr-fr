---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy, élément pour CustomEntry pour CustomControl pour View (Format)
description: EntrySelectedBy, élément pour CustomEntry pour CustomControl pour View (Format)
ms.openlocfilehash: 4821f22560f35034f90d018e5a109004f331441f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655353"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="3a31d-103">EntrySelectedBy, élément pour CustomEntry pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3a31d-103">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="3a31d-104">Définit les types .NET qui utilisent cette entrée personnalisée ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="3a31d-104">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="3a31d-105">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour l’élément View (format) EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3a31d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3a31d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a31d-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3a31d-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3a31d-107">Attributes and Elements</span></span>

<span data-ttu-id="3a31d-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="3a31d-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3a31d-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="3a31d-109">Attributes</span></span>

<span data-ttu-id="3a31d-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3a31d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3a31d-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3a31d-111">Child Elements</span></span>

|<span data-ttu-id="3a31d-112">Élément</span><span class="sxs-lookup"><span data-stu-id="3a31d-112">Element</span></span>|<span data-ttu-id="3a31d-113">Description</span><span class="sxs-lookup"><span data-stu-id="3a31d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3a31d-114">Élément SelectionCondition pour EntrySelectedBy pour CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="3a31d-114">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="3a31d-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3a31d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3a31d-116">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="3a31d-116">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="3a31d-117">Élément SelectionSetName pour EntrySelectedBy pour CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="3a31d-117">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="3a31d-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3a31d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3a31d-119">Spécifie un ensemble de types .NET qui utilisent cette définition de l’affichage de contrôle.</span><span class="sxs-lookup"><span data-stu-id="3a31d-119">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="3a31d-120">Élément TypeName pour EntrySelectedBy pour CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="3a31d-120">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="3a31d-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3a31d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3a31d-122">Spécifie un type .NET qui utilise cette définition de l’affichage de contrôle.</span><span class="sxs-lookup"><span data-stu-id="3a31d-122">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3a31d-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3a31d-123">Parent Elements</span></span>

|<span data-ttu-id="3a31d-124">Élément</span><span class="sxs-lookup"><span data-stu-id="3a31d-124">Element</span></span>|<span data-ttu-id="3a31d-125">Description</span><span class="sxs-lookup"><span data-stu-id="3a31d-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3a31d-126">Élément CustomEntry pour CustomEntries pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3a31d-126">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="3a31d-127">Définit les contrôles utilisés par des objets .NET spécifiques.</span><span class="sxs-lookup"><span data-stu-id="3a31d-127">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3a31d-128">Notes</span><span class="sxs-lookup"><span data-stu-id="3a31d-128">Remarks</span></span>

<span data-ttu-id="3a31d-129">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une entrée.</span><span class="sxs-lookup"><span data-stu-id="3a31d-129">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="3a31d-130">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="3a31d-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="3a31d-131">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour l’entrée à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou lorsqu’une valeur de propriété ou un script spécifique prend la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="3a31d-131">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="3a31d-132">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3a31d-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3a31d-133">Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [vue de contrôle personnalisé](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="3a31d-133">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3a31d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a31d-134">See Also</span></span>

[<span data-ttu-id="3a31d-135">Élément SelectionCondition pour EntrySelectedBy pour CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="3a31d-135">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="3a31d-136">Élément SelectionSetName pour EntrySelectedBy pour CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="3a31d-136">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3a31d-137">Élément TypeName pour EntrySelectedBy pour CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="3a31d-137">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3a31d-138">Élément CustomEntry pour CustomEntries pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3a31d-138">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3a31d-139">Affichage de contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="3a31d-139">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="3a31d-140">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a31d-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
