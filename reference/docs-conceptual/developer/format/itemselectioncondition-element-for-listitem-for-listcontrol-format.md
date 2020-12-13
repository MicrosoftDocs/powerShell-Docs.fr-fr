---
ms.date: 09/13/2016
ms.topic: reference
title: ItemSelectionCondition, élément pour ListItem pour ListControl (Format)
description: ItemSelectionCondition, élément pour ListItem pour ListControl (Format)
ms.openlocfilehash: 13d925da10c2386123983d52b109c03a0c3c63ab
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667808"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="6f9c2-103">ItemSelectionCondition, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6f9c2-103">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="6f9c2-104">Définit la condition qui doit exister pour l’élément de liste à utiliser.</span><span class="sxs-lookup"><span data-stu-id="6f9c2-104">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="6f9c2-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément de ListEntries pour ListControl (format) ListItems, élément de ListEntry pour ListControl (format) ListItem, élément de ListItems pour ListControl (format) élément ItemSelectionCondition pour ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="6f9c2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6f9c2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f9c2-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6f9c2-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6f9c2-107">Attributes and Elements</span></span>

<span data-ttu-id="6f9c2-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ItemSelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="6f9c2-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6f9c2-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="6f9c2-109">Attributes</span></span>

<span data-ttu-id="6f9c2-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6f9c2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6f9c2-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6f9c2-111">Child Elements</span></span>

|<span data-ttu-id="6f9c2-112">Élément</span><span class="sxs-lookup"><span data-stu-id="6f9c2-112">Element</span></span>|<span data-ttu-id="6f9c2-113">Description</span><span class="sxs-lookup"><span data-stu-id="6f9c2-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6f9c2-114">PropertyName, élément pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6f9c2-114">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="6f9c2-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6f9c2-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6f9c2-116">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="6f9c2-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="6f9c2-117">ScriptBlock, élément pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6f9c2-117">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="6f9c2-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6f9c2-118">Optional element.</span></span><br /><br /> <span data-ttu-id="6f9c2-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="6f9c2-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6f9c2-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6f9c2-120">Parent Elements</span></span>

|<span data-ttu-id="6f9c2-121">Élément</span><span class="sxs-lookup"><span data-stu-id="6f9c2-121">Element</span></span>|<span data-ttu-id="6f9c2-122">Description</span><span class="sxs-lookup"><span data-stu-id="6f9c2-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6f9c2-123">ListItem, élément pour ListItems pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6f9c2-123">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="6f9c2-124">Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="6f9c2-124">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6f9c2-125">Notes</span><span class="sxs-lookup"><span data-stu-id="6f9c2-125">Remarks</span></span>

<span data-ttu-id="6f9c2-126">Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="6f9c2-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f9c2-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f9c2-127">See Also</span></span>

[<span data-ttu-id="6f9c2-128">ListItem, élément pour ListItems pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6f9c2-128">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="6f9c2-129">PropertyName, élément pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6f9c2-129">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="6f9c2-130">ScriptBlock, élément pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6f9c2-130">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="6f9c2-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="6f9c2-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
