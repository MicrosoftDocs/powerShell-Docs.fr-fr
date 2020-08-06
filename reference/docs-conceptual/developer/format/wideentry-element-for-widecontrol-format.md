---
title: Élément WideEntry pour WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13dd1f6ad7ac1e9d8d0524f0a0f18fe80ffaf8e2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780013"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="bea7b-102">WideEntry, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bea7b-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="bea7b-103">Fournit une définition de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="bea7b-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="bea7b-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) WideControl, élément (format) WideEntries, élément (format) WideEntry, élément (format)</span><span class="sxs-lookup"><span data-stu-id="bea7b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bea7b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bea7b-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bea7b-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bea7b-106">Attributes and Elements</span></span>

<span data-ttu-id="bea7b-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `WideEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="bea7b-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="bea7b-108">Vous devez spécifier un seul `WideItem` élément enfant.</span><span class="sxs-lookup"><span data-stu-id="bea7b-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bea7b-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="bea7b-109">Attributes</span></span>

<span data-ttu-id="bea7b-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bea7b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bea7b-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bea7b-111">Child Elements</span></span>

|<span data-ttu-id="bea7b-112">Élément</span><span class="sxs-lookup"><span data-stu-id="bea7b-112">Element</span></span>|<span data-ttu-id="bea7b-113">Description</span><span class="sxs-lookup"><span data-stu-id="bea7b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bea7b-114">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="bea7b-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="bea7b-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="bea7b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="bea7b-116">Définit les types .NET qui utilisent cette définition d’entrée étendue ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="bea7b-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="bea7b-117">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="bea7b-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="bea7b-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="bea7b-118">Required element.</span></span><br /><br /> <span data-ttu-id="bea7b-119">Définit la propriété ou le script dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="bea7b-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bea7b-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bea7b-120">Parent Elements</span></span>

|<span data-ttu-id="bea7b-121">Élément</span><span class="sxs-lookup"><span data-stu-id="bea7b-121">Element</span></span>|<span data-ttu-id="bea7b-122">Description</span><span class="sxs-lookup"><span data-stu-id="bea7b-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bea7b-123">Élément WideEntries (format)</span><span class="sxs-lookup"><span data-stu-id="bea7b-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="bea7b-124">Fournit les définitions de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="bea7b-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bea7b-125">Notes</span><span class="sxs-lookup"><span data-stu-id="bea7b-125">Remarks</span></span>

<span data-ttu-id="bea7b-126">Un affichage étendu est un format de liste qui affiche une valeur de propriété ou une valeur de script unique pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="bea7b-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="bea7b-127">Contrairement à d’autres types de vues, vous ne pouvez spécifier qu’un seul élément Item pour chaque définition de vue.</span><span class="sxs-lookup"><span data-stu-id="bea7b-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="bea7b-128">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="bea7b-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="bea7b-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="bea7b-129">Example</span></span>

<span data-ttu-id="bea7b-130">L’exemple suivant montre un `WideEntry` élément qui définit un `WideItem` élément unique.</span><span class="sxs-lookup"><span data-stu-id="bea7b-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="bea7b-131">L' `WideItem` élément définit la propriété dont la valeur est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="bea7b-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="bea7b-132">Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="bea7b-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bea7b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bea7b-133">See Also</span></span>

[<span data-ttu-id="bea7b-134">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="bea7b-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="bea7b-135">Élément SelectionCondition pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="bea7b-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="bea7b-136">Élément SelectionSetName pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="bea7b-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="bea7b-137">Élément TypeName pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="bea7b-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="bea7b-138">Élément WideEntries (format)</span><span class="sxs-lookup"><span data-stu-id="bea7b-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="bea7b-139">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="bea7b-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="bea7b-140">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="bea7b-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
