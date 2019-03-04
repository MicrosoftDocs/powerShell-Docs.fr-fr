---
title: Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: fd708473d04a76bcf6cf3a8f8278e1d15fb9addf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858655"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="2817d-102">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2817d-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="2817d-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="2817d-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="2817d-104">Lorsque ce script est évalué à `true`, la condition est remplie, et l’entrée de liste est utilisée.</span><span class="sxs-lookup"><span data-stu-id="2817d-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="2817d-105">Configuration élément (Format) ViewDefinitions, élément (Format) vue (Format) d’élément objet ListControl, élément (Format) situés (Format) ListEntry, élément (Format) EntrySelectedBy élément d’élément de SelectionCondition ListEntry (Format) pour EntrySelectedBy pour ListEntry (Format), élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2817d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2817d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2817d-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2817d-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="2817d-107">Attributes and Elements</span></span>

<span data-ttu-id="2817d-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="2817d-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2817d-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="2817d-109">Attributes</span></span>

<span data-ttu-id="2817d-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="2817d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2817d-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2817d-111">Child Elements</span></span>

<span data-ttu-id="2817d-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="2817d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2817d-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2817d-113">Parent Elements</span></span>

|<span data-ttu-id="2817d-114">Élément</span><span class="sxs-lookup"><span data-stu-id="2817d-114">Element</span></span>|<span data-ttu-id="2817d-115">Description</span><span class="sxs-lookup"><span data-stu-id="2817d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2817d-116">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2817d-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2817d-117">Définit la condition qui doit exister pour cette entrée de liste à utiliser.</span><span class="sxs-lookup"><span data-stu-id="2817d-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2817d-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="2817d-118">Text Value</span></span>

<span data-ttu-id="2817d-119">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="2817d-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="2817d-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="2817d-120">Remarks</span></span>

<span data-ttu-id="2817d-121">La condition de sélection doit spécifier un moins un script ou le nom à évaluer, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="2817d-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="2817d-122">(Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition Conditions pour lorsqu’une entrée de la vue ou d’élément est utilisé](./defining-conditions-for-displaying-data.md).)</span><span class="sxs-lookup"><span data-stu-id="2817d-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="2817d-123">Pour plus d’informations sur les autres composants d’une vue liste, consultez [mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="2817d-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2817d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2817d-124">See Also</span></span>

[<span data-ttu-id="2817d-125">Élément ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2817d-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="2817d-126">Élément PropertyName pour SelectionCondition pour EmtrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2817d-126">PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2817d-127">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2817d-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2817d-128">Affichage de liste</span><span class="sxs-lookup"><span data-stu-id="2817d-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2817d-129">Définissent les Conditions d’une entrée de la vue ou un élément est utilisé.</span><span class="sxs-lookup"><span data-stu-id="2817d-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2817d-130">Écriture d’un mise en forme de Windows PowerShell et de Types de fichier</span><span class="sxs-lookup"><span data-stu-id="2817d-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
