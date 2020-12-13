---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSets, élément (Format)
description: SelectionSets, élément (Format)
ms.openlocfilehash: e5c928dfb82bc6963b4a87aef9ec06d34cacfdcb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654932"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="50597-103">SelectionSets, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="50597-103">SelectionSets Element (Format)</span></span>

<span data-ttu-id="50597-104">Définit les ensembles courants d’objets .NET qui peuvent être utilisés par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="50597-104">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="50597-105">Les vues et les contrôles du fichier de mise en forme peuvent faire référence à l’ensemble complet d’objets en utilisant uniquement le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="50597-105">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="50597-106">Format d’élément SelectionSets de l’élément de configuration</span><span class="sxs-lookup"><span data-stu-id="50597-106">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="50597-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50597-107">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="50597-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="50597-108">Attributes and Elements</span></span>

<span data-ttu-id="50597-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSets` élément.</span><span class="sxs-lookup"><span data-stu-id="50597-109">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="50597-110">Chaque élément enfant définit un ensemble d’objets qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="50597-110">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="50597-111">L’ordre des éléments enfants n’est pas significatif.</span><span class="sxs-lookup"><span data-stu-id="50597-111">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="50597-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="50597-112">Attributes</span></span>

<span data-ttu-id="50597-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="50597-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="50597-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="50597-114">Child Elements</span></span>

|<span data-ttu-id="50597-115">Élément</span><span class="sxs-lookup"><span data-stu-id="50597-115">Element</span></span>|<span data-ttu-id="50597-116">Description</span><span class="sxs-lookup"><span data-stu-id="50597-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50597-117">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="50597-117">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="50597-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="50597-118">Required element.</span></span><br /><br /> <span data-ttu-id="50597-119">Définit un ensemble unique d’objets .NET qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="50597-119">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="50597-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="50597-120">Parent Elements</span></span>

|<span data-ttu-id="50597-121">Élément</span><span class="sxs-lookup"><span data-stu-id="50597-121">Element</span></span>|<span data-ttu-id="50597-122">Description</span><span class="sxs-lookup"><span data-stu-id="50597-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50597-123">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="50597-123">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="50597-124">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="50597-124">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="50597-125">Notes</span><span class="sxs-lookup"><span data-stu-id="50597-125">Remarks</span></span>

<span data-ttu-id="50597-126">Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage.</span><span class="sxs-lookup"><span data-stu-id="50597-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="50597-127">Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom du jeu de sélection au lieu de répertorier tous les objets dans chaque vue.</span><span class="sxs-lookup"><span data-stu-id="50597-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="50597-128">Les jeux de sélection communs sont spécifiés par leur nom lors de la définition des vues du fichier de mise en forme ou des définitions des vues.</span><span class="sxs-lookup"><span data-stu-id="50597-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="50597-129">Dans ce cas, l' `SelectionSetName` élément enfant des `ViewSelectedBy` éléments et `EntrySelectedBy` spécifie le jeu à utiliser.</span><span class="sxs-lookup"><span data-stu-id="50597-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="50597-130">Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="50597-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="50597-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50597-131">See Also</span></span>

[<span data-ttu-id="50597-132">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="50597-132">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="50597-133">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="50597-133">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="50597-134">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="50597-134">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="50597-135">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="50597-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
