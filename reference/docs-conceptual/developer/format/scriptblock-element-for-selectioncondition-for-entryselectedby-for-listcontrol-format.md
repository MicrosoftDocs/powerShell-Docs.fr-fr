---
title: Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368588"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="ff53e-102">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ff53e-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="ff53e-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="ff53e-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="ff53e-104">Lorsque ce script est évalué à `true`, la condition est remplie et l’entrée de liste est utilisée.</span><span class="sxs-lookup"><span data-stu-id="ff53e-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="ff53e-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionCondition pour EntrySelectedBy pour ListEntry (format) élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ff53e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ff53e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff53e-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ff53e-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="ff53e-107">Attributes and Elements</span></span>

<span data-ttu-id="ff53e-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="ff53e-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ff53e-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="ff53e-109">Attributes</span></span>

<span data-ttu-id="ff53e-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ff53e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ff53e-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ff53e-111">Child Elements</span></span>

<span data-ttu-id="ff53e-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ff53e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ff53e-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ff53e-113">Parent Elements</span></span>

|<span data-ttu-id="ff53e-114">Élément</span><span class="sxs-lookup"><span data-stu-id="ff53e-114">Element</span></span>|<span data-ttu-id="ff53e-115">Description</span><span class="sxs-lookup"><span data-stu-id="ff53e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff53e-116">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ff53e-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="ff53e-117">Définit la condition qui doit exister pour que cette entrée de liste soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="ff53e-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ff53e-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="ff53e-118">Text Value</span></span>

<span data-ttu-id="ff53e-119">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="ff53e-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff53e-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="ff53e-120">Remarks</span></span>

<span data-ttu-id="ff53e-121">La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="ff53e-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="ff53e-122">(Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).)</span><span class="sxs-lookup"><span data-stu-id="ff53e-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="ff53e-123">Pour plus d’informations sur les autres composants d’un affichage de liste, consultez [affichage de liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="ff53e-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ff53e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff53e-124">See Also</span></span>

[<span data-ttu-id="ff53e-125">Élément ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ff53e-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="ff53e-126">PropertyName, élément de SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ff53e-126">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="ff53e-127">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ff53e-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="ff53e-128">Mode liste</span><span class="sxs-lookup"><span data-stu-id="ff53e-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ff53e-129">Définition des conditions d’utilisation d’une entrée ou d’un élément d’une vue</span><span class="sxs-lookup"><span data-stu-id="ff53e-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ff53e-130">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff53e-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
