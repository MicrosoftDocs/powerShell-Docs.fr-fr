---
ms.date: 09/13/2016
ms.topic: reference
title: Expand, élément (Format)
description: Expand, élément (Format)
ms.openlocfilehash: 518e132e3e74b921d4e51966fc60088a22ef63f1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667944"
---
# <a name="expand-element-format"></a><span data-ttu-id="afb02-103">Expand, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="afb02-103">Expand Element (Format)</span></span>

<span data-ttu-id="afb02-104">Spécifie comment l’objet de collection est développé pour cette définition.</span><span class="sxs-lookup"><span data-stu-id="afb02-104">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="afb02-105">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) Expand, élément (format)</span><span class="sxs-lookup"><span data-stu-id="afb02-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="afb02-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afb02-106">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="afb02-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="afb02-107">Attributes and Elements</span></span>

<span data-ttu-id="afb02-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Expand` élément.</span><span class="sxs-lookup"><span data-stu-id="afb02-108">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="afb02-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="afb02-109">Attributes</span></span>

<span data-ttu-id="afb02-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="afb02-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="afb02-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="afb02-111">Child Elements</span></span>

<span data-ttu-id="afb02-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="afb02-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="afb02-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="afb02-113">Parent Elements</span></span>

|<span data-ttu-id="afb02-114">Élément</span><span class="sxs-lookup"><span data-stu-id="afb02-114">Element</span></span>|<span data-ttu-id="afb02-115">Description</span><span class="sxs-lookup"><span data-stu-id="afb02-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="afb02-116">EnumerableExpansion, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="afb02-116">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="afb02-117">Définit la façon dont des objets de collection .NET spécifiques sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="afb02-117">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="afb02-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="afb02-118">Text Value</span></span>

<span data-ttu-id="afb02-119">Spécifiez l'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="afb02-119">Specify one of the following values:</span></span>

- <span data-ttu-id="afb02-120">EnumOnly : affiche uniquement les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="afb02-120">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="afb02-121">CoreOnly : affiche uniquement les propriétés de l’objet de collection.</span><span class="sxs-lookup"><span data-stu-id="afb02-121">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="afb02-122">Both : affiche les propriétés des objets dans la collection et les propriétés de l’objet de collection.</span><span class="sxs-lookup"><span data-stu-id="afb02-122">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="afb02-123">Notes</span><span class="sxs-lookup"><span data-stu-id="afb02-123">Remarks</span></span>

<span data-ttu-id="afb02-124">Cet élément est utilisé pour définir le mode d’affichage des objets de collection et des objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="afb02-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="afb02-125">Dans ce cas, un objet de collection fait référence à tout objet qui prend en charge l’interface  **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="afb02-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="afb02-126">Le comportement par défaut consiste à afficher uniquement les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="afb02-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="afb02-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afb02-127">See Also</span></span>

[<span data-ttu-id="afb02-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="afb02-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
