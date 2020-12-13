---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion, élément (Format)
description: EnumerableExpansion, élément (Format)
ms.openlocfilehash: 207ad99d5335e99701660159ab77279b55b0b6b5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668012"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="8834d-103">EnumerableExpansion, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="8834d-103">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="8834d-104">Définit la façon dont des objets de collection .NET spécifiques sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="8834d-104">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="8834d-105">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) EnumerableExpansion, élément (format)</span><span class="sxs-lookup"><span data-stu-id="8834d-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8834d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8834d-106">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8834d-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8834d-107">Attributes and Elements</span></span>

<span data-ttu-id="8834d-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EnumerableExpansion` élément.</span><span class="sxs-lookup"><span data-stu-id="8834d-108">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8834d-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="8834d-109">Attributes</span></span>

<span data-ttu-id="8834d-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8834d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8834d-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8834d-111">Child Elements</span></span>

|<span data-ttu-id="8834d-112">Élément</span><span class="sxs-lookup"><span data-stu-id="8834d-112">Element</span></span>|<span data-ttu-id="8834d-113">Description</span><span class="sxs-lookup"><span data-stu-id="8834d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8834d-114">EntrySelectedBy, élément pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="8834d-114">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="8834d-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="8834d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8834d-116">Définit les objets de collection .NET développés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="8834d-116">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="8834d-117">Expand, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="8834d-117">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="8834d-118">Spécifie comment l’objet de collection est développé pour cette définition.</span><span class="sxs-lookup"><span data-stu-id="8834d-118">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8834d-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8834d-119">Parent Elements</span></span>

|<span data-ttu-id="8834d-120">Élément</span><span class="sxs-lookup"><span data-stu-id="8834d-120">Element</span></span>|<span data-ttu-id="8834d-121">Description</span><span class="sxs-lookup"><span data-stu-id="8834d-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8834d-122">EnumerableExpansions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="8834d-122">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="8834d-123">Définit les différentes façons dont les objets de collection .NET sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="8834d-123">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8834d-124">Notes</span><span class="sxs-lookup"><span data-stu-id="8834d-124">Remarks</span></span>

<span data-ttu-id="8834d-125">Cet élément est utilisé pour définir le mode d’affichage des objets de collection et des objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="8834d-125">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="8834d-126">Dans ce cas, un objet de collection fait référence à tout objet qui prend en charge l’interface  **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="8834d-126">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="8834d-127">Le comportement par défaut consiste à afficher uniquement les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="8834d-127">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="8834d-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8834d-128">See Also</span></span>

[<span data-ttu-id="8834d-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="8834d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
