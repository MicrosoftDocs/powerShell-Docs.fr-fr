---
ms.date: 09/13/2016
ms.topic: reference
title: Name, élément pour SelectionSet (Format)
description: Name, élément pour SelectionSet (Format)
ms.openlocfilehash: 98c13be6ea352055231fbdb3a60f0eb508f661b8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666454"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="757af-103">Name, élément pour SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="757af-103">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="757af-104">Spécifie le nom utilisé pour référencer le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="757af-104">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="757af-105">Élément de configuration (format) élément SelectionSets (format) élément SelectionSet (format) élément Name de SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="757af-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="757af-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="757af-106">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="757af-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="757af-107">Attributes and Elements</span></span>

<span data-ttu-id="757af-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Name` élément.</span><span class="sxs-lookup"><span data-stu-id="757af-108">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="757af-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="757af-109">Attributes</span></span>

<span data-ttu-id="757af-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="757af-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="757af-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="757af-111">Child Elements</span></span>

<span data-ttu-id="757af-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="757af-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="757af-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="757af-113">Parent Elements</span></span>

|<span data-ttu-id="757af-114">Élément</span><span class="sxs-lookup"><span data-stu-id="757af-114">Element</span></span>|<span data-ttu-id="757af-115">Description</span><span class="sxs-lookup"><span data-stu-id="757af-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="757af-116">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="757af-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="757af-117">Définit un ensemble unique d’objets .NET qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="757af-117">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="757af-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="757af-118">Text Value</span></span>

<span data-ttu-id="757af-119">Spécifiez le nom pour faire référence au jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="757af-119">Specify the name to reference the selection set.</span></span> <span data-ttu-id="757af-120">Il n’existe aucune restriction quant aux caractères qui peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="757af-120">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="757af-121">Notes</span><span class="sxs-lookup"><span data-stu-id="757af-121">Remarks</span></span>

<span data-ttu-id="757af-122">Le nom spécifié ici est utilisé dans l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="757af-122">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="757af-123">Jeu de sélection qui peut être utilisé par une vue, par une définition d’une vue (les vues peuvent avoir plusieurs définitions) ou lors de la spécification d’une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="757af-123">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="757af-124">Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="757af-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="757af-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="757af-125">Example</span></span>

<span data-ttu-id="757af-126">Cet exemple montre un `SelectionSet` élément qui définit quatre types .net.</span><span class="sxs-lookup"><span data-stu-id="757af-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="757af-127">Le nom du jeu de sélection est « FileSystemTypes ».</span><span class="sxs-lookup"><span data-stu-id="757af-127">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="757af-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="757af-128">See Also</span></span>

[<span data-ttu-id="757af-129">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="757af-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="757af-130">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="757af-130">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="757af-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="757af-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
