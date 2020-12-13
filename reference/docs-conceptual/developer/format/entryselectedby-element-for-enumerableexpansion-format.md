---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy, élément pour EnumerableExpansion (Format)
description: EntrySelectedBy, élément pour EnumerableExpansion (Format)
ms.openlocfilehash: 8b2fff2d0b14d0622d0be2c5af3a95194c733a73
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652324"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="6c15c-103">EntrySelectedBy, élément pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c15c-103">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="6c15c-104">Définit les types .NET qui utilisent cette définition ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="6c15c-104">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="6c15c-105">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) EntrySelectedBy élément pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="6c15c-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6c15c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c15c-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6c15c-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6c15c-107">Attributes and Elements</span></span>

<span data-ttu-id="6c15c-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="6c15c-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6c15c-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="6c15c-109">Attributes</span></span>

<span data-ttu-id="6c15c-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6c15c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6c15c-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6c15c-111">Child Elements</span></span>

|<span data-ttu-id="6c15c-112">Élément</span><span class="sxs-lookup"><span data-stu-id="6c15c-112">Element</span></span>|<span data-ttu-id="6c15c-113">Description</span><span class="sxs-lookup"><span data-stu-id="6c15c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6c15c-114">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c15c-114">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="6c15c-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6c15c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6c15c-116">Définit la condition qui doit exister pour développer les objets de collection de cette définition.</span><span class="sxs-lookup"><span data-stu-id="6c15c-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="6c15c-117">SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c15c-117">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="6c15c-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6c15c-118">Optional element.</span></span><br /><br /> <span data-ttu-id="6c15c-119">Spécifie un ensemble de types .NET qui utilisent cette définition de la façon dont les objets de collection sont développés.</span><span class="sxs-lookup"><span data-stu-id="6c15c-119">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="6c15c-120">TypeName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c15c-120">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="6c15c-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6c15c-121">Optional element.</span></span><br /><br /> <span data-ttu-id="6c15c-122">Spécifie un type .NET qui utilise cette définition de la façon dont les objets de la collection sont développés.</span><span class="sxs-lookup"><span data-stu-id="6c15c-122">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6c15c-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6c15c-123">Parent Elements</span></span>

|<span data-ttu-id="6c15c-124">Élément</span><span class="sxs-lookup"><span data-stu-id="6c15c-124">Element</span></span>|<span data-ttu-id="6c15c-125">Description</span><span class="sxs-lookup"><span data-stu-id="6c15c-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6c15c-126">EnumerableExpansion, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="6c15c-126">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="6c15c-127">Définit la façon dont des objets de collection .NET spécifiques sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="6c15c-127">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6c15c-128">Notes</span><span class="sxs-lookup"><span data-stu-id="6c15c-128">Remarks</span></span>

<span data-ttu-id="6c15c-129">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une entrée de définition.</span><span class="sxs-lookup"><span data-stu-id="6c15c-129">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="6c15c-130">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="6c15c-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="6c15c-131">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou un script spécifique prend la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="6c15c-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="6c15c-132">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6c15c-132">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c15c-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c15c-133">See Also</span></span>

[<span data-ttu-id="6c15c-134">Définition de conditions pour l’affichage de données</span><span class="sxs-lookup"><span data-stu-id="6c15c-134">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6c15c-135">EnumerableExpansion, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="6c15c-135">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="6c15c-136">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c15c-136">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="6c15c-137">SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c15c-137">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="6c15c-138">TypeName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c15c-138">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="6c15c-139">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="6c15c-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
