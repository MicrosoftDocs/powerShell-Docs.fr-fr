---
title: Élément EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856835"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="9a431-102">EnumerableExpansion, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="9a431-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="9a431-103">Définit des collection .NET façon dont certains objets sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="9a431-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="9a431-104">Configuration élément (Format) élément DefaultSettings (Format) EnumerableExpansions (Format) EnumerableExpansion élément (Format)</span><span class="sxs-lookup"><span data-stu-id="9a431-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9a431-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a431-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a431-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="9a431-106">Attributes and Elements</span></span>

<span data-ttu-id="9a431-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `EnumerableExpansion` élément.</span><span class="sxs-lookup"><span data-stu-id="9a431-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a431-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="9a431-108">Attributes</span></span>

<span data-ttu-id="9a431-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="9a431-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9a431-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9a431-110">Child Elements</span></span>

|<span data-ttu-id="9a431-111">Élément</span><span class="sxs-lookup"><span data-stu-id="9a431-111">Element</span></span>|<span data-ttu-id="9a431-112">Description</span><span class="sxs-lookup"><span data-stu-id="9a431-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a431-113">Élément EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="9a431-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="9a431-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="9a431-114">Optional element.</span></span><br /><br /> <span data-ttu-id="9a431-115">Définit les objets de collection .NET sont développées par cette définition.</span><span class="sxs-lookup"><span data-stu-id="9a431-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="9a431-116">Développez l’élément (Format)</span><span class="sxs-lookup"><span data-stu-id="9a431-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="9a431-117">Spécifie la façon dont l’objet de collection est développé pour cette définition.</span><span class="sxs-lookup"><span data-stu-id="9a431-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9a431-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9a431-118">Parent Elements</span></span>

|<span data-ttu-id="9a431-119">Élément</span><span class="sxs-lookup"><span data-stu-id="9a431-119">Element</span></span>|<span data-ttu-id="9a431-120">Description</span><span class="sxs-lookup"><span data-stu-id="9a431-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a431-121">Élément EnumerableExpansions (Format)</span><span class="sxs-lookup"><span data-stu-id="9a431-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="9a431-122">Définit les différentes façons de cette collection .NET objets sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="9a431-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9a431-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="9a431-123">Remarks</span></span>

<span data-ttu-id="9a431-124">Cet élément est utilisé pour définir l’affichent des objets de collection et les objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="9a431-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="9a431-125">Dans ce cas, un objet de collection fait référence à n’importe quel objet qui prend en charge la **System.Collections.ICollection** interface.</span><span class="sxs-lookup"><span data-stu-id="9a431-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="9a431-126">Le comportement par défaut consiste à afficher uniquement les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="9a431-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a431-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a431-127">See Also</span></span>

[<span data-ttu-id="9a431-128">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a431-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
