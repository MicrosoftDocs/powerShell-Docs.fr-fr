---
title: Élément EntrySelectedBy pour CustomEntry pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 75a0f42e7722b54791a873200a35c8fcbbd665b1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774131"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="64497-102">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="64497-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="64497-103">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="64497-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="64497-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="64497-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="64497-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) EntrySelectedBy élément pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="64497-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="64497-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64497-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="64497-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="64497-107">Attributes and Elements</span></span>

<span data-ttu-id="64497-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="64497-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="64497-109">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition.</span><span class="sxs-lookup"><span data-stu-id="64497-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="64497-110">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="64497-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="64497-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="64497-111">Attributes</span></span>

<span data-ttu-id="64497-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="64497-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="64497-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="64497-113">Child Elements</span></span>

|<span data-ttu-id="64497-114">Élément</span><span class="sxs-lookup"><span data-stu-id="64497-114">Element</span></span>|<span data-ttu-id="64497-115">Description</span><span class="sxs-lookup"><span data-stu-id="64497-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64497-116">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="64497-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="64497-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="64497-117">Optional element.</span></span><br /><br /> <span data-ttu-id="64497-118">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="64497-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="64497-119">SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="64497-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="64497-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="64497-120">Optional element.</span></span><br /><br /> <span data-ttu-id="64497-121">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="64497-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="64497-122">TypeName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="64497-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="64497-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="64497-123">Optional element.</span></span><br /><br /> <span data-ttu-id="64497-124">Spécifie un type .NET qui utilise cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="64497-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="64497-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="64497-125">Parent Elements</span></span>

|<span data-ttu-id="64497-126">Élément</span><span class="sxs-lookup"><span data-stu-id="64497-126">Element</span></span>|<span data-ttu-id="64497-127">Description</span><span class="sxs-lookup"><span data-stu-id="64497-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64497-128">CustomEntry, élément pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="64497-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="64497-129">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="64497-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="64497-130">Notes</span><span class="sxs-lookup"><span data-stu-id="64497-130">Remarks</span></span>

<span data-ttu-id="64497-131">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou lorsqu’une valeur de propriété ou un script spécifique prend la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="64497-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="64497-132">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="64497-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="64497-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64497-133">See Also</span></span>

[<span data-ttu-id="64497-134">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="64497-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="64497-135">SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="64497-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="64497-136">TypeName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="64497-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="64497-137">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="64497-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="64497-138">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="64497-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
