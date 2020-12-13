---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntry, élément pour CustomEntries pour CustomControl pour View (Format)
description: CustomEntry, élément pour CustomEntries pour CustomControl pour View (Format)
ms.openlocfilehash: ff481f13e6f16267bdda4c3053faebc96d9a6d3a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646051"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="86776-103">CustomEntry, élément pour CustomEntries pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="86776-103">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="86776-104">Fournit une définition de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="86776-104">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="86776-105">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour View (format)</span><span class="sxs-lookup"><span data-stu-id="86776-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86776-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86776-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86776-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="86776-107">Attributes and Elements</span></span>

<span data-ttu-id="86776-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="86776-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="86776-109">Vous devez spécifier les éléments affichés par la définition.</span><span class="sxs-lookup"><span data-stu-id="86776-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="86776-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="86776-110">Attributes</span></span>

<span data-ttu-id="86776-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="86776-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86776-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="86776-112">Child Elements</span></span>

|<span data-ttu-id="86776-113">Élément</span><span class="sxs-lookup"><span data-stu-id="86776-113">Element</span></span>|<span data-ttu-id="86776-114">Description</span><span class="sxs-lookup"><span data-stu-id="86776-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86776-115">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="86776-115">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="86776-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="86776-116">Optional element.</span></span><br /><br /> <span data-ttu-id="86776-117">Définit les types .NET qui utilisent la définition de l’affichage de contrôle personnalisé ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="86776-117">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="86776-118">Élément CustomItem pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="86776-118">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="86776-119">Définit un contrôle pour la définition de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="86776-119">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="86776-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="86776-120">Parent Elements</span></span>

|<span data-ttu-id="86776-121">Élément</span><span class="sxs-lookup"><span data-stu-id="86776-121">Element</span></span>|<span data-ttu-id="86776-122">Description</span><span class="sxs-lookup"><span data-stu-id="86776-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86776-123">CustomEntries, élément pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="86776-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="86776-124">Fournit les définitions de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="86776-124">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="86776-125">L’affichage de contrôle personnalisé doit spécifier une ou plusieurs définitions.</span><span class="sxs-lookup"><span data-stu-id="86776-125">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="86776-126">Notes</span><span class="sxs-lookup"><span data-stu-id="86776-126">Remarks</span></span>

<span data-ttu-id="86776-127">Dans la plupart des cas, une seule définition est requise pour chaque affichage de contrôle personnalisé, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="86776-127">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="86776-128">Dans ce cas, vous pouvez fournir une définition distincte pour chaque objet ou ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="86776-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="86776-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86776-129">See Also</span></span>

[<span data-ttu-id="86776-130">CustomControl, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="86776-130">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="86776-131">Élément CustomItem pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="86776-131">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="86776-132">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="86776-132">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="86776-133">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="86776-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
