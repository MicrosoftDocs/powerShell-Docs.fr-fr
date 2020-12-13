---
ms.date: 09/13/2016
ms.topic: reference
title: WideEntry, élément pour WideControl (Format)
description: WideEntry, élément pour WideControl (Format)
ms.openlocfilehash: 3faaf767d11914792effd6765beed956a502c642
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664553"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="0e712-103">WideEntry, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0e712-103">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="0e712-104">Fournit une définition de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="0e712-104">Provides a definition of the wide view.</span></span>

<span data-ttu-id="0e712-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) WideControl, élément (format) WideEntries, élément (format) WideEntry, élément (format)</span><span class="sxs-lookup"><span data-stu-id="0e712-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0e712-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e712-106">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0e712-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0e712-107">Attributes and Elements</span></span>

<span data-ttu-id="0e712-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `WideEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="0e712-108">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="0e712-109">Vous devez spécifier un seul `WideItem` élément enfant.</span><span class="sxs-lookup"><span data-stu-id="0e712-109">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0e712-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0e712-110">Attributes</span></span>

<span data-ttu-id="0e712-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0e712-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0e712-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0e712-112">Child Elements</span></span>

|<span data-ttu-id="0e712-113">Élément</span><span class="sxs-lookup"><span data-stu-id="0e712-113">Element</span></span>|<span data-ttu-id="0e712-114">Description</span><span class="sxs-lookup"><span data-stu-id="0e712-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e712-115">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0e712-115">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="0e712-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0e712-116">Optional element.</span></span><br /><br /> <span data-ttu-id="0e712-117">Définit les types .NET qui utilisent cette définition d’entrée étendue ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="0e712-117">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="0e712-118">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="0e712-118">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="0e712-119">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="0e712-119">Required element.</span></span><br /><br /> <span data-ttu-id="0e712-120">Définit la propriété ou le script dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="0e712-120">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0e712-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0e712-121">Parent Elements</span></span>

|<span data-ttu-id="0e712-122">Élément</span><span class="sxs-lookup"><span data-stu-id="0e712-122">Element</span></span>|<span data-ttu-id="0e712-123">Description</span><span class="sxs-lookup"><span data-stu-id="0e712-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e712-124">Élément WideEntries (format)</span><span class="sxs-lookup"><span data-stu-id="0e712-124">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="0e712-125">Fournit les définitions de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="0e712-125">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0e712-126">Notes</span><span class="sxs-lookup"><span data-stu-id="0e712-126">Remarks</span></span>

<span data-ttu-id="0e712-127">Un affichage étendu est un format de liste qui affiche une valeur de propriété ou une valeur de script unique pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="0e712-127">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="0e712-128">Contrairement à d’autres types de vues, vous ne pouvez spécifier qu’un seul élément Item pour chaque définition de vue.</span><span class="sxs-lookup"><span data-stu-id="0e712-128">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="0e712-129">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="0e712-129">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0e712-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="0e712-130">Example</span></span>

<span data-ttu-id="0e712-131">L’exemple suivant montre un `WideEntry` élément qui définit un `WideItem` élément unique.</span><span class="sxs-lookup"><span data-stu-id="0e712-131">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="0e712-132">L' `WideItem` élément définit la propriété dont la valeur est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="0e712-132">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="0e712-133">Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="0e712-133">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0e712-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e712-134">See Also</span></span>

[<span data-ttu-id="0e712-135">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="0e712-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="0e712-136">Élément SelectionCondition pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0e712-136">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="0e712-137">Élément SelectionSetName pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0e712-137">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="0e712-138">Élément TypeName pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0e712-138">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="0e712-139">Élément WideEntries (format)</span><span class="sxs-lookup"><span data-stu-id="0e712-139">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="0e712-140">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="0e712-140">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="0e712-141">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e712-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
