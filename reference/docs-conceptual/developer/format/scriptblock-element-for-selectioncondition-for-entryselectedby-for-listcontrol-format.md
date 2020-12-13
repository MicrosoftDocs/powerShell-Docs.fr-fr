---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)
description: ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)
ms.openlocfilehash: ec7691358d0ff3758411317a349221e1704a1895
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659899"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="958e3-103">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="958e3-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="958e3-104">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="958e3-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="958e3-105">Lorsque ce script est évalué à `true` , la condition est remplie et l’entrée de liste est utilisée.</span><span class="sxs-lookup"><span data-stu-id="958e3-105">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="958e3-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionCondition pour EntrySelectedBy pour ListEntry (format) élément ScriptBlock pour SelectionCondition pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="958e3-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="958e3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="958e3-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="958e3-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="958e3-108">Attributes and Elements</span></span>

<span data-ttu-id="958e3-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="958e3-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="958e3-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="958e3-110">Attributes</span></span>

<span data-ttu-id="958e3-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="958e3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="958e3-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="958e3-112">Child Elements</span></span>

<span data-ttu-id="958e3-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="958e3-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="958e3-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="958e3-114">Parent Elements</span></span>

|<span data-ttu-id="958e3-115">Élément</span><span class="sxs-lookup"><span data-stu-id="958e3-115">Element</span></span>|<span data-ttu-id="958e3-116">Description</span><span class="sxs-lookup"><span data-stu-id="958e3-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="958e3-117">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="958e3-117">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="958e3-118">Définit la condition qui doit exister pour que cette entrée de liste soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="958e3-118">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="958e3-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="958e3-119">Text Value</span></span>

<span data-ttu-id="958e3-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="958e3-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="958e3-121">Notes</span><span class="sxs-lookup"><span data-stu-id="958e3-121">Remarks</span></span>

<span data-ttu-id="958e3-122">La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="958e3-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="958e3-123">(Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).)</span><span class="sxs-lookup"><span data-stu-id="958e3-123">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="958e3-124">Pour plus d’informations sur les autres composants d’un affichage de liste, consultez [affichage de liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="958e3-124">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="958e3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="958e3-125">See Also</span></span>

[<span data-ttu-id="958e3-126">Élément ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="958e3-126">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="958e3-127">PropertyName, élément de SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="958e3-127">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="958e3-128">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="958e3-128">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="958e3-129">Mode liste</span><span class="sxs-lookup"><span data-stu-id="958e3-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="958e3-130">Définition des conditions d’utilisation d’une entrée ou d’un élément d’une vue</span><span class="sxs-lookup"><span data-stu-id="958e3-130">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="958e3-131">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="958e3-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
