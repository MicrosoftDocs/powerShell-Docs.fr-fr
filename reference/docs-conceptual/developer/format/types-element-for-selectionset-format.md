---
ms.date: 09/13/2016
ms.topic: reference
title: Types, élément pour SelectionSet (Format)
description: Types, élément pour SelectionSet (Format)
ms.openlocfilehash: ff3c24e7f52f862dc416b88d50983196ce907012
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645457"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="e1fab-103">Types, élément pour SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="e1fab-103">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="e1fab-104">Définit les objets .NET qui se trouvent dans le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="e1fab-104">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="e1fab-105">Élément de configuration (format) élément SelectionSets (format) élément SelectionSet (format) élément types (format)</span><span class="sxs-lookup"><span data-stu-id="e1fab-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1fab-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1fab-106">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1fab-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e1fab-107">Attributes and Elements</span></span>

<span data-ttu-id="e1fab-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Types` élément.</span><span class="sxs-lookup"><span data-stu-id="e1fab-108">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="e1fab-109">Il doit y avoir au moins un élément enfant, mais il n’existe pas de limite maximale pour le nombre d’éléments enfants qui peuvent être ajoutés.</span><span class="sxs-lookup"><span data-stu-id="e1fab-109">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1fab-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="e1fab-110">Attributes</span></span>

<span data-ttu-id="e1fab-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e1fab-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1fab-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e1fab-112">Child Elements</span></span>

|<span data-ttu-id="e1fab-113">Élément</span><span class="sxs-lookup"><span data-stu-id="e1fab-113">Element</span></span>|<span data-ttu-id="e1fab-114">Description</span><span class="sxs-lookup"><span data-stu-id="e1fab-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1fab-115">Élément TypeName de types (format)</span><span class="sxs-lookup"><span data-stu-id="e1fab-115">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="e1fab-116">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="e1fab-116">Required element.</span></span><br /><br /> <span data-ttu-id="e1fab-117">Spécifie l’objet .NET qui appartient au jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="e1fab-117">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e1fab-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e1fab-118">Parent Elements</span></span>

|<span data-ttu-id="e1fab-119">Élément</span><span class="sxs-lookup"><span data-stu-id="e1fab-119">Element</span></span>|<span data-ttu-id="e1fab-120">Description</span><span class="sxs-lookup"><span data-stu-id="e1fab-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1fab-121">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="e1fab-121">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="e1fab-122">Définit un ensemble d’objets .NET qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="e1fab-122">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e1fab-123">Notes</span><span class="sxs-lookup"><span data-stu-id="e1fab-123">Remarks</span></span>

<span data-ttu-id="e1fab-124">Les objets définis par cet élément composent un jeu de sélection qui peut être utilisé par une vue, par une définition d’une vue (les vues peuvent avoir plusieurs définitions) ou lors de la spécification d’une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="e1fab-124">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="e1fab-125">Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e1fab-125">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="e1fab-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1fab-126">Example</span></span>

<span data-ttu-id="e1fab-127">Cet exemple montre un `SelectionSet` élément qui définit quatre types .net.</span><span class="sxs-lookup"><span data-stu-id="e1fab-127">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="e1fab-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1fab-128">See Also</span></span>

[<span data-ttu-id="e1fab-129">Définition de jeux d’objets</span><span class="sxs-lookup"><span data-stu-id="e1fab-129">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e1fab-130">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="e1fab-130">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="e1fab-131">Élément TypeName de types (format)</span><span class="sxs-lookup"><span data-stu-id="e1fab-131">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="e1fab-132">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1fab-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
