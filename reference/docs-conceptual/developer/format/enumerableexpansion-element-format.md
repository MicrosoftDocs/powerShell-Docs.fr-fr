---
title: Élément EnumerableExpansion (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368748"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="e949e-102">EnumerableExpansion, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="e949e-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="e949e-103">Définit la façon dont des objets de collection .NET spécifiques sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="e949e-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="e949e-104">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) EnumerableExpansion, élément (format)</span><span class="sxs-lookup"><span data-stu-id="e949e-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e949e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e949e-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e949e-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="e949e-106">Attributes and Elements</span></span>

<span data-ttu-id="e949e-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `EnumerableExpansion`.</span><span class="sxs-lookup"><span data-stu-id="e949e-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e949e-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="e949e-108">Attributes</span></span>

<span data-ttu-id="e949e-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e949e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e949e-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e949e-110">Child Elements</span></span>

|<span data-ttu-id="e949e-111">Élément</span><span class="sxs-lookup"><span data-stu-id="e949e-111">Element</span></span>|<span data-ttu-id="e949e-112">Description</span><span class="sxs-lookup"><span data-stu-id="e949e-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e949e-113">Élément EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="e949e-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="e949e-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e949e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e949e-115">Définit les objets de collection .NET développés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="e949e-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="e949e-116">Expand, élément (format)</span><span class="sxs-lookup"><span data-stu-id="e949e-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="e949e-117">Spécifie comment l’objet de collection est développé pour cette définition.</span><span class="sxs-lookup"><span data-stu-id="e949e-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e949e-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e949e-118">Parent Elements</span></span>

|<span data-ttu-id="e949e-119">Élément</span><span class="sxs-lookup"><span data-stu-id="e949e-119">Element</span></span>|<span data-ttu-id="e949e-120">Description</span><span class="sxs-lookup"><span data-stu-id="e949e-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e949e-121">Élément EnumerableExpansions (format)</span><span class="sxs-lookup"><span data-stu-id="e949e-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="e949e-122">Définit les différentes façons dont les objets de collection .NET sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="e949e-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e949e-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="e949e-123">Remarks</span></span>

<span data-ttu-id="e949e-124">Cet élément est utilisé pour définir le mode d’affichage des objets de collection et des objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="e949e-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="e949e-125">Dans ce cas, un objet de collection fait référence à tout objet qui prend en charge l’interface **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="e949e-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="e949e-126">Le comportement par défaut consiste à afficher uniquement les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="e949e-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="e949e-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e949e-127">See Also</span></span>

[<span data-ttu-id="e949e-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e949e-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
