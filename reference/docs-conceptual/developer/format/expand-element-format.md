---
title: Expand, élément (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368738"
---
# <a name="expand-element-format"></a><span data-ttu-id="20808-102">Expand, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="20808-102">Expand Element (Format)</span></span>

<span data-ttu-id="20808-103">Spécifie comment l’objet de collection est développé pour cette définition.</span><span class="sxs-lookup"><span data-stu-id="20808-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="20808-104">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) Expand, élément (format)</span><span class="sxs-lookup"><span data-stu-id="20808-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="20808-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20808-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20808-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="20808-106">Attributes and Elements</span></span>

<span data-ttu-id="20808-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Expand`.</span><span class="sxs-lookup"><span data-stu-id="20808-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="20808-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="20808-108">Attributes</span></span>

<span data-ttu-id="20808-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="20808-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="20808-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="20808-110">Child Elements</span></span>

<span data-ttu-id="20808-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="20808-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="20808-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="20808-112">Parent Elements</span></span>

|<span data-ttu-id="20808-113">Élément</span><span class="sxs-lookup"><span data-stu-id="20808-113">Element</span></span>|<span data-ttu-id="20808-114">Description</span><span class="sxs-lookup"><span data-stu-id="20808-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20808-115">Élément EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="20808-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="20808-116">Définit la façon dont des objets de collection .NET spécifiques sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="20808-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="20808-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="20808-117">Text Value</span></span>

<span data-ttu-id="20808-118">Spécifiez l'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="20808-118">Specify one of the following values:</span></span>

- <span data-ttu-id="20808-119">EnumOnly : affiche uniquement les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="20808-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="20808-120">CoreOnly : affiche uniquement les propriétés de l’objet de collection.</span><span class="sxs-lookup"><span data-stu-id="20808-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="20808-121">Both : affiche les propriétés des objets dans la collection et les propriétés de l’objet de collection.</span><span class="sxs-lookup"><span data-stu-id="20808-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="20808-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="20808-122">Remarks</span></span>

<span data-ttu-id="20808-123">Cet élément est utilisé pour définir le mode d’affichage des objets de collection et des objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="20808-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="20808-124">Dans ce cas, un objet de collection fait référence à tout objet qui prend en charge l’interface **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="20808-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="20808-125">Le comportement par défaut consiste à afficher uniquement les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="20808-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="20808-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20808-126">See Also</span></span>

[<span data-ttu-id="20808-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="20808-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
