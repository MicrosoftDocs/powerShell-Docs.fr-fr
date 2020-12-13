---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSet, élément (Format)
description: SelectionSet, élément (Format)
ms.openlocfilehash: 944aa83569ad8ca789746a71f60e5da5c19fbf01
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647871"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="bfb23-103">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="bfb23-103">SelectionSet Element (Format)</span></span>

<span data-ttu-id="bfb23-104">Définit un ensemble d’objets .NET qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="bfb23-104">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="bfb23-105">Élément de configuration (format) élément SelectionSets (format) SelectionSet, élément (format)</span><span class="sxs-lookup"><span data-stu-id="bfb23-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bfb23-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfb23-106">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bfb23-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bfb23-107">Attributes and Elements</span></span>

<span data-ttu-id="bfb23-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSet` élément.</span><span class="sxs-lookup"><span data-stu-id="bfb23-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="bfb23-109">Chaque jeu de sélection doit avoir un nom et doit spécifier les objets .NET de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="bfb23-109">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="bfb23-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="bfb23-110">Attributes</span></span>

<span data-ttu-id="bfb23-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bfb23-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bfb23-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bfb23-112">Child Elements</span></span>

|<span data-ttu-id="bfb23-113">Élément</span><span class="sxs-lookup"><span data-stu-id="bfb23-113">Element</span></span>|<span data-ttu-id="bfb23-114">Description</span><span class="sxs-lookup"><span data-stu-id="bfb23-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bfb23-115">Name, élément pour SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="bfb23-115">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="bfb23-116">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="bfb23-116">Required element.</span></span><br /><br /> <span data-ttu-id="bfb23-117">Spécifie le nom utilisé pour référencer le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="bfb23-117">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="bfb23-118">Élément types (format)</span><span class="sxs-lookup"><span data-stu-id="bfb23-118">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="bfb23-119">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="bfb23-119">Required element.</span></span><br /><br /> <span data-ttu-id="bfb23-120">Définit les objets .NET qui se trouvent dans le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="bfb23-120">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bfb23-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bfb23-121">Parent Elements</span></span>

|<span data-ttu-id="bfb23-122">Élément</span><span class="sxs-lookup"><span data-stu-id="bfb23-122">Element</span></span>|<span data-ttu-id="bfb23-123">Description</span><span class="sxs-lookup"><span data-stu-id="bfb23-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bfb23-124">Format de l’élément SelectionSets</span><span class="sxs-lookup"><span data-stu-id="bfb23-124">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="bfb23-125">Définit les ensembles courants d’objets .NET qui peuvent être utilisés par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="bfb23-125">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bfb23-126">Notes</span><span class="sxs-lookup"><span data-stu-id="bfb23-126">Remarks</span></span>

<span data-ttu-id="bfb23-127">Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage.</span><span class="sxs-lookup"><span data-stu-id="bfb23-127">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="bfb23-128">Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom du jeu de sélection au lieu de répertorier tous les objets dans chaque vue.</span><span class="sxs-lookup"><span data-stu-id="bfb23-128">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="bfb23-129">Les jeux de sélection communs sont spécifiés par leur nom lors de la définition des vues du fichier de mise en forme ou des définitions des vues.</span><span class="sxs-lookup"><span data-stu-id="bfb23-129">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="bfb23-130">Dans ce cas, l' `SelectionSetName` élément enfant des `ViewSelectedBy` éléments et `EntrySelectedBy` spécifie le jeu à utiliser.</span><span class="sxs-lookup"><span data-stu-id="bfb23-130">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="bfb23-131">Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="bfb23-131">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="bfb23-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="bfb23-132">Example</span></span>

<span data-ttu-id="bfb23-133">L’exemple suivant montre un `SelectionSet` élément qui définit quatre types .net.</span><span class="sxs-lookup"><span data-stu-id="bfb23-133">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bfb23-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfb23-134">See Also</span></span>

[<span data-ttu-id="bfb23-135">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="bfb23-135">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="bfb23-136">Élément Name de SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="bfb23-136">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="bfb23-137">SelectionSets, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="bfb23-137">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="bfb23-138">Élément types (format)</span><span class="sxs-lookup"><span data-stu-id="bfb23-138">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="bfb23-139">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="bfb23-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
