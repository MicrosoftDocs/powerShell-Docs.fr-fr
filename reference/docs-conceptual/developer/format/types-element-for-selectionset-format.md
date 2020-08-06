---
title: Élément types pour SelectionSet (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9978daefb3e97ab131774ca4dff633dde6b4dfbf
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772516"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="2f45c-102">Types, élément pour SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="2f45c-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="2f45c-103">Définit les objets .NET qui se trouvent dans le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="2f45c-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="2f45c-104">Élément de configuration (format) élément SelectionSets (format) élément SelectionSet (format) élément types (format)</span><span class="sxs-lookup"><span data-stu-id="2f45c-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2f45c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f45c-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="2f45c-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2f45c-106">Attributes and Elements</span></span>

<span data-ttu-id="2f45c-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Types` élément.</span><span class="sxs-lookup"><span data-stu-id="2f45c-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="2f45c-108">Il doit y avoir au moins un élément enfant, mais il n’existe pas de limite maximale pour le nombre d’éléments enfants qui peuvent être ajoutés.</span><span class="sxs-lookup"><span data-stu-id="2f45c-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="2f45c-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="2f45c-109">Attributes</span></span>

<span data-ttu-id="2f45c-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2f45c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2f45c-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2f45c-111">Child Elements</span></span>

|<span data-ttu-id="2f45c-112">Élément</span><span class="sxs-lookup"><span data-stu-id="2f45c-112">Element</span></span>|<span data-ttu-id="2f45c-113">Description</span><span class="sxs-lookup"><span data-stu-id="2f45c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f45c-114">Élément TypeName de types (format)</span><span class="sxs-lookup"><span data-stu-id="2f45c-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="2f45c-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="2f45c-115">Required element.</span></span><br /><br /> <span data-ttu-id="2f45c-116">Spécifie l’objet .NET qui appartient au jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="2f45c-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2f45c-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2f45c-117">Parent Elements</span></span>

|<span data-ttu-id="2f45c-118">Élément</span><span class="sxs-lookup"><span data-stu-id="2f45c-118">Element</span></span>|<span data-ttu-id="2f45c-119">Description</span><span class="sxs-lookup"><span data-stu-id="2f45c-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f45c-120">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="2f45c-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="2f45c-121">Définit un ensemble d’objets .NET qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="2f45c-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2f45c-122">Notes</span><span class="sxs-lookup"><span data-stu-id="2f45c-122">Remarks</span></span>

<span data-ttu-id="2f45c-123">Les objets définis par cet élément composent un jeu de sélection qui peut être utilisé par une vue, par une définition d’une vue (les vues peuvent avoir plusieurs définitions) ou lors de la spécification d’une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="2f45c-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="2f45c-124">Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="2f45c-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="2f45c-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f45c-125">Example</span></span>

<span data-ttu-id="2f45c-126">Cet exemple montre un `SelectionSet` élément qui définit quatre types .net.</span><span class="sxs-lookup"><span data-stu-id="2f45c-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2f45c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f45c-127">See Also</span></span>

[<span data-ttu-id="2f45c-128">Définition de jeux d’objets</span><span class="sxs-lookup"><span data-stu-id="2f45c-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="2f45c-129">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="2f45c-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="2f45c-130">Élément TypeName de types (format)</span><span class="sxs-lookup"><span data-stu-id="2f45c-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="2f45c-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f45c-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
