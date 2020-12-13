---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControl, élément pour View (Format)
description: CustomControl, élément pour View (Format)
ms.openlocfilehash: 41352be55f0c03b2eaca0dbe2d7345e7cf804a7c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655472"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="9bb5e-103">CustomControl, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="9bb5e-103">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="9bb5e-104">Définit un format de contrôle personnalisé pour la vue.</span><span class="sxs-lookup"><span data-stu-id="9bb5e-104">Defines a custom control format for the view.</span></span>

<span data-ttu-id="9bb5e-105">Élément de configuration (format) élément ViewDefinitions (format) élément View (format) CustomControl, élément (format)</span><span class="sxs-lookup"><span data-stu-id="9bb5e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9bb5e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bb5e-106">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9bb5e-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9bb5e-107">Attributes and Elements</span></span>

<span data-ttu-id="9bb5e-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomControl` élément.</span><span class="sxs-lookup"><span data-stu-id="9bb5e-108">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="9bb5e-109">Vous devez spécifier un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="9bb5e-109">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9bb5e-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="9bb5e-110">Attributes</span></span>

<span data-ttu-id="9bb5e-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9bb5e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9bb5e-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9bb5e-112">Child Elements</span></span>

|<span data-ttu-id="9bb5e-113">Élément</span><span class="sxs-lookup"><span data-stu-id="9bb5e-113">Element</span></span>|<span data-ttu-id="9bb5e-114">Description</span><span class="sxs-lookup"><span data-stu-id="9bb5e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9bb5e-115">CustomEntries, élément pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="9bb5e-115">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="9bb5e-116">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="9bb5e-116">Required element.</span></span><br /><br /> <span data-ttu-id="9bb5e-117">Fournit les définitions de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9bb5e-117">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9bb5e-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9bb5e-118">Parent Elements</span></span>

|<span data-ttu-id="9bb5e-119">Élément</span><span class="sxs-lookup"><span data-stu-id="9bb5e-119">Element</span></span>|<span data-ttu-id="9bb5e-120">Description</span><span class="sxs-lookup"><span data-stu-id="9bb5e-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9bb5e-121">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="9bb5e-121">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="9bb5e-122">Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="9bb5e-122">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9bb5e-123">Notes</span><span class="sxs-lookup"><span data-stu-id="9bb5e-123">Remarks</span></span>

<span data-ttu-id="9bb5e-124">Dans la plupart des cas, une seule définition est requise pour chaque vue de contrôle, mais il est possible de fournir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="9bb5e-124">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="9bb5e-125">Dans ce cas, vous pouvez fournir une définition distincte pour chaque objet ou ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="9bb5e-125">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="9bb5e-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9bb5e-126">See Also</span></span>

[<span data-ttu-id="9bb5e-127">CustomEntries, élément pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="9bb5e-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9bb5e-128">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="9bb5e-128">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="9bb5e-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bb5e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
