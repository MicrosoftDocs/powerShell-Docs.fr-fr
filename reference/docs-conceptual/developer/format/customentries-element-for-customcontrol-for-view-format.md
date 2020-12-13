---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntries, élément pour CustomControl pour View (Format)
description: CustomEntries, élément pour CustomControl pour View (Format)
ms.openlocfilehash: 6e757bccdface2503667f8786462a2b43134a07d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649972"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="d074e-103">CustomEntries, élément pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d074e-103">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="d074e-104">Fournit les définitions de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d074e-104">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="d074e-105">L’affichage de contrôle personnalisé doit spécifier une ou plusieurs définitions.</span><span class="sxs-lookup"><span data-stu-id="d074e-105">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="d074e-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="d074e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d074e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d074e-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d074e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d074e-108">Attributes and Elements</span></span>

<span data-ttu-id="d074e-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomControlEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="d074e-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="d074e-110">Vous devez spécifier un ou plusieurs éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="d074e-110">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d074e-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="d074e-111">Attributes</span></span>

<span data-ttu-id="d074e-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d074e-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d074e-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d074e-113">Child Elements</span></span>

|<span data-ttu-id="d074e-114">Élément</span><span class="sxs-lookup"><span data-stu-id="d074e-114">Element</span></span>|<span data-ttu-id="d074e-115">Description</span><span class="sxs-lookup"><span data-stu-id="d074e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d074e-116">Élément CustomEntry pour CustomEntries pour View (format)</span><span class="sxs-lookup"><span data-stu-id="d074e-116">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="d074e-117">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="d074e-117">Required element.</span></span><br /><br /> <span data-ttu-id="d074e-118">Fournit une définition de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d074e-118">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d074e-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d074e-119">Parent Elements</span></span>

|<span data-ttu-id="d074e-120">Élément</span><span class="sxs-lookup"><span data-stu-id="d074e-120">Element</span></span>|<span data-ttu-id="d074e-121">Description</span><span class="sxs-lookup"><span data-stu-id="d074e-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d074e-122">CustomControl, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d074e-122">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="d074e-123">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="d074e-123">Required element.</span></span><br /><br /> <span data-ttu-id="d074e-124">Définit un format de contrôle personnalisé pour la vue.</span><span class="sxs-lookup"><span data-stu-id="d074e-124">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d074e-125">Notes</span><span class="sxs-lookup"><span data-stu-id="d074e-125">Remarks</span></span>

<span data-ttu-id="d074e-126">Dans la plupart des cas, un contrôle n’a qu’une seule définition, qui est définie dans un `CustomEntry` élément unique.</span><span class="sxs-lookup"><span data-stu-id="d074e-126">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="d074e-127">Toutefois, il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="d074e-127">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="d074e-128">Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="d074e-128">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="d074e-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d074e-129">See Also</span></span>

[<span data-ttu-id="d074e-130">CustomControl, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d074e-130">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="d074e-131">Élément CustomEntry pour CustomEntries pour View (format)</span><span class="sxs-lookup"><span data-stu-id="d074e-131">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d074e-132">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="d074e-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
