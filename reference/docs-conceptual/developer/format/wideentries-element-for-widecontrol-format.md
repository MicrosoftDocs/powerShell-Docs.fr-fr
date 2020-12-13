---
ms.date: 09/13/2016
ms.topic: reference
title: WideEntries, élément pour WideControl (Format)
description: WideEntries, élément pour WideControl (Format)
ms.openlocfilehash: 567b8acdd0d2e8d5daaef2c31b4fe4ce38c23a47
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651231"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="c28b9-103">WideEntries, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c28b9-103">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="c28b9-104">Fournit les définitions de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="c28b9-104">Provides the definitions of the wide view.</span></span> <span data-ttu-id="c28b9-105">La vue étendue doit spécifier une ou plusieurs définitions.</span><span class="sxs-lookup"><span data-stu-id="c28b9-105">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="c28b9-106">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément WideControl (format) WideEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="c28b9-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c28b9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c28b9-107">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c28b9-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c28b9-108">Attributes and Elements</span></span>

<span data-ttu-id="c28b9-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `WideEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="c28b9-109">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="c28b9-110">Au moins un élément enfant doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="c28b9-110">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="c28b9-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="c28b9-111">Attributes</span></span>

<span data-ttu-id="c28b9-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c28b9-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c28b9-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c28b9-113">Child Elements</span></span>

|<span data-ttu-id="c28b9-114">Élément</span><span class="sxs-lookup"><span data-stu-id="c28b9-114">Element</span></span>|<span data-ttu-id="c28b9-115">Description</span><span class="sxs-lookup"><span data-stu-id="c28b9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c28b9-116">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c28b9-116">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="c28b9-117">Fournit une définition de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="c28b9-117">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c28b9-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c28b9-118">Parent Elements</span></span>

|<span data-ttu-id="c28b9-119">Élément</span><span class="sxs-lookup"><span data-stu-id="c28b9-119">Element</span></span>|<span data-ttu-id="c28b9-120">Description</span><span class="sxs-lookup"><span data-stu-id="c28b9-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c28b9-121">WideControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="c28b9-121">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="c28b9-122">Définit un format de liste larges (à valeur unique) pour la vue.</span><span class="sxs-lookup"><span data-stu-id="c28b9-122">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c28b9-123">Notes</span><span class="sxs-lookup"><span data-stu-id="c28b9-123">Remarks</span></span>

<span data-ttu-id="c28b9-124">Un affichage étendu est un format de liste qui affiche une valeur de propriété ou une valeur de script unique pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="c28b9-124">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="c28b9-125">Pour plus d’informations sur les composants d’une vue étendue, consultez [composants de vue larges](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="c28b9-125">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c28b9-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="c28b9-126">Example</span></span>

<span data-ttu-id="c28b9-127">L’exemple suivant montre un `WideEntries` élément qui définit un `WideEntry` élément unique.</span><span class="sxs-lookup"><span data-stu-id="c28b9-127">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="c28b9-128">L' `WideEntry` élément contient un `WideItem` élément unique qui définit la valeur de la propriété ou du script qui est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="c28b9-128">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="c28b9-129">Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="c28b9-129">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c28b9-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c28b9-130">See Also</span></span>

[<span data-ttu-id="c28b9-131">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="c28b9-131">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c28b9-132">WideControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="c28b9-132">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="c28b9-133">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c28b9-133">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="c28b9-134">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="c28b9-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
