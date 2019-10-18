---
title: Élément WideEntry pour WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367898"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="f35a7-102">WideEntry, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f35a7-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="f35a7-103">Fournit une définition de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="f35a7-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="f35a7-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) WideControl, élément (format) WideEntries, élément (format) WideEntry, élément (format)</span><span class="sxs-lookup"><span data-stu-id="f35a7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f35a7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f35a7-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f35a7-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="f35a7-106">Attributes and Elements</span></span>

<span data-ttu-id="f35a7-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `WideEntry`.</span><span class="sxs-lookup"><span data-stu-id="f35a7-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="f35a7-108">Vous devez spécifier un seul élément enfant `WideItem`.</span><span class="sxs-lookup"><span data-stu-id="f35a7-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f35a7-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="f35a7-109">Attributes</span></span>

<span data-ttu-id="f35a7-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f35a7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f35a7-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f35a7-111">Child Elements</span></span>

|<span data-ttu-id="f35a7-112">Élément</span><span class="sxs-lookup"><span data-stu-id="f35a7-112">Element</span></span>|<span data-ttu-id="f35a7-113">Description</span><span class="sxs-lookup"><span data-stu-id="f35a7-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f35a7-114">Élément EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f35a7-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="f35a7-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="f35a7-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f35a7-116">Définit les types .NET qui utilisent cette définition d’entrée étendue ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="f35a7-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="f35a7-117">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="f35a7-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="f35a7-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="f35a7-118">Required element.</span></span><br /><br /> <span data-ttu-id="f35a7-119">Définit la propriété ou le script dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="f35a7-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f35a7-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f35a7-120">Parent Elements</span></span>

|<span data-ttu-id="f35a7-121">Élément</span><span class="sxs-lookup"><span data-stu-id="f35a7-121">Element</span></span>|<span data-ttu-id="f35a7-122">Description</span><span class="sxs-lookup"><span data-stu-id="f35a7-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f35a7-123">Élément WideEntries (format)</span><span class="sxs-lookup"><span data-stu-id="f35a7-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="f35a7-124">Fournit les définitions de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="f35a7-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f35a7-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="f35a7-125">Remarks</span></span>

<span data-ttu-id="f35a7-126">Un affichage étendu est un format de liste qui affiche une valeur de propriété ou une valeur de script unique pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="f35a7-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="f35a7-127">Contrairement à d’autres types de vues, vous ne pouvez spécifier qu’un seul élément Item pour chaque définition de vue.</span><span class="sxs-lookup"><span data-stu-id="f35a7-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="f35a7-128">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f35a7-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f35a7-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="f35a7-129">Example</span></span>

<span data-ttu-id="f35a7-130">L’exemple suivant montre un élément `WideEntry` qui définit un seul élément `WideItem`.</span><span class="sxs-lookup"><span data-stu-id="f35a7-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="f35a7-131">L’élément `WideItem` définit la propriété dont la valeur est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="f35a7-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="f35a7-132">Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="f35a7-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f35a7-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f35a7-133">See Also</span></span>

[<span data-ttu-id="f35a7-134">Création d’un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="f35a7-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f35a7-135">Élément SelectionCondition pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f35a7-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f35a7-136">Élément SelectionSetName pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f35a7-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f35a7-137">Élément TypeName pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f35a7-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="f35a7-138">Élément WideEntries (format)</span><span class="sxs-lookup"><span data-stu-id="f35a7-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="f35a7-139">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="f35a7-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="f35a7-140">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="f35a7-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)