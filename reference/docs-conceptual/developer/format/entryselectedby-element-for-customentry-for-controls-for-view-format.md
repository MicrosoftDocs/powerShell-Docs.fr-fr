---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)
description: EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)
ms.openlocfilehash: 29b0574a95d81962fb3f72a526f89273baeea647
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660261"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="a88c7-103">EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a88c7-103">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="a88c7-104">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="a88c7-104">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="a88c7-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="a88c7-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="a88c7-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour la vue (format) élément CustomControl pour le contrôle pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour les contrôles pour l’élément CustomEntry (format) pour les contrôles pour la vue (format)</span><span class="sxs-lookup"><span data-stu-id="a88c7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a88c7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a88c7-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a88c7-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a88c7-108">Attributes and Elements</span></span>

<span data-ttu-id="a88c7-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="a88c7-109">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="a88c7-110">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition.</span><span class="sxs-lookup"><span data-stu-id="a88c7-110">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="a88c7-111">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="a88c7-111">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="a88c7-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="a88c7-112">Attributes</span></span>

<span data-ttu-id="a88c7-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a88c7-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a88c7-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a88c7-114">Child Elements</span></span>

|<span data-ttu-id="a88c7-115">Élément</span><span class="sxs-lookup"><span data-stu-id="a88c7-115">Element</span></span>|<span data-ttu-id="a88c7-116">Description</span><span class="sxs-lookup"><span data-stu-id="a88c7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a88c7-117">SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a88c7-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="a88c7-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a88c7-118">Optional element.</span></span><br /><br /> <span data-ttu-id="a88c7-119">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="a88c7-119">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="a88c7-120">SelectionSetName, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a88c7-120">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="a88c7-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a88c7-121">Optional element.</span></span><br /><br /> <span data-ttu-id="a88c7-122">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="a88c7-122">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="a88c7-123">TypeName, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a88c7-123">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="a88c7-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a88c7-124">Optional element.</span></span><br /><br /> <span data-ttu-id="a88c7-125">Spécifie un type .NET qui utilise cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="a88c7-125">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a88c7-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a88c7-126">Parent Elements</span></span>

|<span data-ttu-id="a88c7-127">Élément</span><span class="sxs-lookup"><span data-stu-id="a88c7-127">Element</span></span>|<span data-ttu-id="a88c7-128">Description</span><span class="sxs-lookup"><span data-stu-id="a88c7-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a88c7-129">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a88c7-129">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="a88c7-130">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="a88c7-130">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a88c7-131">Notes</span><span class="sxs-lookup"><span data-stu-id="a88c7-131">Remarks</span></span>

<span data-ttu-id="a88c7-132">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou lorsqu’une valeur de propriété ou un script spécifique prend la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="a88c7-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="a88c7-133">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a88c7-133">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a88c7-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a88c7-134">See Also</span></span>

[<span data-ttu-id="a88c7-135">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a88c7-135">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="a88c7-136">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a88c7-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
