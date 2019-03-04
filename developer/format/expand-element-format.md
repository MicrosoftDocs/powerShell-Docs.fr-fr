---
title: Développez l’élément (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858575"
---
# <a name="expand-element-format"></a><span data-ttu-id="fd6fb-102">Expand, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="fd6fb-102">Expand Element (Format)</span></span>

<span data-ttu-id="fd6fb-103">Spécifie la façon dont l’objet de collection est développé pour cette définition.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="fd6fb-104">Configuration élément (Format) élément DefaultSettings (Format) EnumerableExpansions (Format) EnumerableExpansion élément (Format) développez l’élément (Format)</span><span class="sxs-lookup"><span data-stu-id="fd6fb-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fd6fb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd6fb-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fd6fb-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="fd6fb-106">Attributes and Elements</span></span>

<span data-ttu-id="fd6fb-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Expand` élément.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fd6fb-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="fd6fb-108">Attributes</span></span>

<span data-ttu-id="fd6fb-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fd6fb-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fd6fb-110">Child Elements</span></span>

<span data-ttu-id="fd6fb-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fd6fb-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fd6fb-112">Parent Elements</span></span>

|<span data-ttu-id="fd6fb-113">Élément</span><span class="sxs-lookup"><span data-stu-id="fd6fb-113">Element</span></span>|<span data-ttu-id="fd6fb-114">Description</span><span class="sxs-lookup"><span data-stu-id="fd6fb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fd6fb-115">Élément EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="fd6fb-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="fd6fb-116">Définit des collection .NET façon dont certains objets sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fd6fb-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="fd6fb-117">Text Value</span></span>

<span data-ttu-id="fd6fb-118">Spécifiez l’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="fd6fb-118">Specify one of the following values:</span></span>

- <span data-ttu-id="fd6fb-119">EnumOnly : Affiche uniquement les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="fd6fb-120">CoreOnly : Affiche uniquement les propriétés de l’objet de collection.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="fd6fb-121">Les deux : Affiche les propriétés des objets dans la collection et les propriétés de l’objet de collection.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="fd6fb-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="fd6fb-122">Remarks</span></span>

<span data-ttu-id="fd6fb-123">Cet élément est utilisé pour définir l’affichent des objets de collection et les objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="fd6fb-124">Dans ce cas, un objet de collection fait référence à n’importe quel objet qui prend en charge la **System.Collections.ICollection** interface.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="fd6fb-125">Le comportement par défaut consiste à afficher uniquement les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd6fb-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd6fb-126">See Also</span></span>

[<span data-ttu-id="fd6fb-127">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd6fb-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
