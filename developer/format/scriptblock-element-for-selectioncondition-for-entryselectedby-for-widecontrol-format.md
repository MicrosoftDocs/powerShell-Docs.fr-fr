---
title: Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862945"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="78c9c-102">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="78c9c-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="78c9c-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="78c9c-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="78c9c-104">Lorsque ce script est évalué à `true`, la condition est remplie, et la définition de l’entrée large est utilisée.</span><span class="sxs-lookup"><span data-stu-id="78c9c-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="78c9c-105">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément WideControl (Format) élément WideEntries (Format) élément WideEntry (Format) EntrySelectedBy élément pour l’élément de SelectionCondition WideEntry (Format) pour EntrySelectedBy pour WideEntry (Format), élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="78c9c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="78c9c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78c9c-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="78c9c-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="78c9c-107">Attributes and Elements</span></span>

<span data-ttu-id="78c9c-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="78c9c-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="78c9c-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="78c9c-109">Attributes</span></span>

<span data-ttu-id="78c9c-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="78c9c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="78c9c-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="78c9c-111">Child Elements</span></span>

<span data-ttu-id="78c9c-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="78c9c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="78c9c-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="78c9c-113">Parent Elements</span></span>

|<span data-ttu-id="78c9c-114">Élément</span><span class="sxs-lookup"><span data-stu-id="78c9c-114">Element</span></span>|<span data-ttu-id="78c9c-115">Description</span><span class="sxs-lookup"><span data-stu-id="78c9c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="78c9c-116">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="78c9c-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="78c9c-117">Définit la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="78c9c-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="78c9c-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="78c9c-118">Text Value</span></span>

<span data-ttu-id="78c9c-119">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="78c9c-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="78c9c-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="78c9c-120">Remarks</span></span>

<span data-ttu-id="78c9c-121">La condition de sélection doit spécifier au moins un nom de script ou une propriété à évaluer, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="78c9c-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="78c9c-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="78c9c-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="78c9c-123">Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [Affichage large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="78c9c-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="78c9c-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78c9c-124">See Also</span></span>

[<span data-ttu-id="78c9c-125">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="78c9c-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="78c9c-126">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="78c9c-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="78c9c-127">Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="78c9c-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="78c9c-128">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="78c9c-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="78c9c-129">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="78c9c-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
