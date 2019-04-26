---
title: Élément EntrySelectedBy pour CustomEntry pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066224"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="e0c84-102">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0c84-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="e0c84-103">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e0c84-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="e0c84-104">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="e0c84-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e0c84-105">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de EntrySelectedBy GroupBy (Format) pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0c84-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e0c84-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0c84-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0c84-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="e0c84-107">Attributes and Elements</span></span>

<span data-ttu-id="e0c84-108">Les sections suivantes décrivent des attributs, éléments enfants et élément parent de la `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="e0c84-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="e0c84-109">Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection d’une définition.</span><span class="sxs-lookup"><span data-stu-id="e0c84-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="e0c84-110">Il n’existe aucune limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="e0c84-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0c84-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="e0c84-111">Attributes</span></span>

<span data-ttu-id="e0c84-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e0c84-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e0c84-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e0c84-113">Child Elements</span></span>

|<span data-ttu-id="e0c84-114">Élément</span><span class="sxs-lookup"><span data-stu-id="e0c84-114">Element</span></span>|<span data-ttu-id="e0c84-115">Description</span><span class="sxs-lookup"><span data-stu-id="e0c84-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0c84-116">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0c84-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="e0c84-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e0c84-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e0c84-118">Définit la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e0c84-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="e0c84-119">Élément SelectionSetName pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0c84-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="e0c84-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e0c84-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e0c84-121">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="e0c84-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="e0c84-122">Élément TypeName pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0c84-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="e0c84-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e0c84-123">Optional element.</span></span><br /><br /> <span data-ttu-id="e0c84-124">Spécifie un type .NET qui utilise cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="e0c84-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e0c84-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e0c84-125">Parent Elements</span></span>

|<span data-ttu-id="e0c84-126">Élément</span><span class="sxs-lookup"><span data-stu-id="e0c84-126">Element</span></span>|<span data-ttu-id="e0c84-127">Description</span><span class="sxs-lookup"><span data-stu-id="e0c84-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0c84-128">Élément CustomEntry pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0c84-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="e0c84-129">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="e0c84-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e0c84-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="e0c84-130">Remarks</span></span>

<span data-ttu-id="e0c84-131">Conditions de sélection permettent de définir une condition qui doit exister pour la définition à utiliser, par exemple quand un objet possède une propriété spécifique ou lorsqu’une valeur de propriété spécifique ou de script prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="e0c84-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="e0c84-132">Pour plus d’informations sur les conditions de sélection, consultez [définition Conditions pour lorsqu’une entrée de la vue ou d’élément est utilisé](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e0c84-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0c84-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0c84-133">See Also</span></span>

[<span data-ttu-id="e0c84-134">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0c84-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="e0c84-135">Élément SelectionSetName pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0c84-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="e0c84-136">Élément TypeName pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0c84-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="e0c84-137">Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="e0c84-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="e0c84-138">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0c84-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
