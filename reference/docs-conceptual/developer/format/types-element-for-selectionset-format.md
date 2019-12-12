---
title: Élément types pour SelectionSet (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367958"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="6761d-102">Types, élément pour SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="6761d-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="6761d-103">Définit les objets .NET qui se trouvent dans le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="6761d-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="6761d-104">Élément de configuration (format) élément SelectionSets (format) élément SelectionSet (format) élément types (format)</span><span class="sxs-lookup"><span data-stu-id="6761d-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6761d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6761d-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="6761d-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="6761d-106">Attributes and Elements</span></span>

<span data-ttu-id="6761d-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Types`.</span><span class="sxs-lookup"><span data-stu-id="6761d-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="6761d-108">Il doit y avoir au moins un élément enfant, mais il n’existe pas de limite maximale pour le nombre d’éléments enfants qui peuvent être ajoutés.</span><span class="sxs-lookup"><span data-stu-id="6761d-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="6761d-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="6761d-109">Attributes</span></span>

<span data-ttu-id="6761d-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="6761d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6761d-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6761d-111">Child Elements</span></span>

|<span data-ttu-id="6761d-112">Élément</span><span class="sxs-lookup"><span data-stu-id="6761d-112">Element</span></span>|<span data-ttu-id="6761d-113">Description</span><span class="sxs-lookup"><span data-stu-id="6761d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6761d-114">Élément TypeName de types (format)</span><span class="sxs-lookup"><span data-stu-id="6761d-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="6761d-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="6761d-115">Required element.</span></span><br /><br /> <span data-ttu-id="6761d-116">Spécifie l’objet .NET qui appartient au jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="6761d-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6761d-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6761d-117">Parent Elements</span></span>

|<span data-ttu-id="6761d-118">Élément</span><span class="sxs-lookup"><span data-stu-id="6761d-118">Element</span></span>|<span data-ttu-id="6761d-119">Description</span><span class="sxs-lookup"><span data-stu-id="6761d-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6761d-120">Élément SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="6761d-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="6761d-121">Définit un ensemble d’objets .NET qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="6761d-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6761d-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="6761d-122">Remarks</span></span>

<span data-ttu-id="6761d-123">Les objets définis par cet élément composent un jeu de sélection qui peut être utilisé par une vue, par une définition d’une vue (les vues peuvent avoir plusieurs définitions) ou lors de la spécification d’une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="6761d-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="6761d-124">Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="6761d-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="6761d-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="6761d-125">Example</span></span>

<span data-ttu-id="6761d-126">Cet exemple montre un élément `SelectionSet` qui définit quatre types .NET.</span><span class="sxs-lookup"><span data-stu-id="6761d-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6761d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6761d-127">See Also</span></span>

[<span data-ttu-id="6761d-128">Définition de jeux d’objets</span><span class="sxs-lookup"><span data-stu-id="6761d-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="6761d-129">Élément SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="6761d-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="6761d-130">Élément TypeName de types (format)</span><span class="sxs-lookup"><span data-stu-id="6761d-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="6761d-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="6761d-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
