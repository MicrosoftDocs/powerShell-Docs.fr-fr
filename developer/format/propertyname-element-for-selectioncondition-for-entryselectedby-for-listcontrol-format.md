---
title: Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059012"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="dd6e3-102">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="dd6e3-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="dd6e3-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="dd6e3-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="dd6e3-104">Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie, et l’entrée de liste est utilisée.</span><span class="sxs-lookup"><span data-stu-id="dd6e3-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="dd6e3-105">Configuration élément (Format) ViewDefinitions, élément (Format) vue (Format) d’élément objet ListControl, élément (Format) situés (Format) ListEntry, élément (Format) EntrySelectedBy élément d’élément de SelectionCondition ListEntry (Format) pour EntrySelectedBy d’élément de PropertyName ListEntry (Format) pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dd6e3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dd6e3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd6e3-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dd6e3-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="dd6e3-107">Attributes and Elements</span></span>

<span data-ttu-id="dd6e3-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="dd6e3-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dd6e3-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="dd6e3-109">Attributes</span></span>

<span data-ttu-id="dd6e3-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="dd6e3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dd6e3-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dd6e3-111">Child Elements</span></span>

<span data-ttu-id="dd6e3-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="dd6e3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dd6e3-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dd6e3-113">Parent Elements</span></span>

|<span data-ttu-id="dd6e3-114">Élément</span><span class="sxs-lookup"><span data-stu-id="dd6e3-114">Element</span></span>|<span data-ttu-id="dd6e3-115">Description</span><span class="sxs-lookup"><span data-stu-id="dd6e3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd6e3-116">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dd6e3-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="dd6e3-117">Définit la condition qui doit exister pour cette entrée de liste à utiliser.</span><span class="sxs-lookup"><span data-stu-id="dd6e3-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dd6e3-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="dd6e3-118">Text Value</span></span>

<span data-ttu-id="dd6e3-119">Spécifiez le nom de propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="dd6e3-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="dd6e3-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="dd6e3-120">Remarks</span></span>

<span data-ttu-id="dd6e3-121">La condition de sélection doit spécifier nom d’au moins une propriété ou un bloc de script, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="dd6e3-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="dd6e3-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition Conditions pour lorsqu’une entrée de la vue ou d’élément est utilisé](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="dd6e3-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="dd6e3-123">Pour plus d’informations sur d’autres composants d’une vue liste, consultez [création d’une vue de liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="dd6e3-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd6e3-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd6e3-124">See Also</span></span>

[<span data-ttu-id="dd6e3-125">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="dd6e3-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="dd6e3-126">Définition des Conditions pour les données lorsque s’affiche.</span><span class="sxs-lookup"><span data-stu-id="dd6e3-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="dd6e3-127">Élément ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dd6e3-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="dd6e3-128">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dd6e3-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="dd6e3-129">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd6e3-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
