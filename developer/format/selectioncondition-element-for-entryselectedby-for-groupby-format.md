---
title: Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855165"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="d0be7-102">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0be7-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="d0be7-103">Définit une condition qui doit exister pour une définition de contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d0be7-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="d0be7-104">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="d0be7-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d0be7-105">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de EntrySelectedBy GroupBy (Format) pour CustomEntry d’élément de SelectionCondition GroupBy (Format) pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0be7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d0be7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0be7-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0be7-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="d0be7-107">Attributes and Elements</span></span>

<span data-ttu-id="d0be7-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="d0be7-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0be7-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="d0be7-109">Attributes</span></span>

<span data-ttu-id="d0be7-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d0be7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d0be7-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d0be7-111">Child Elements</span></span>

|<span data-ttu-id="d0be7-112">Élément</span><span class="sxs-lookup"><span data-stu-id="d0be7-112">Element</span></span>|<span data-ttu-id="d0be7-113">Description</span><span class="sxs-lookup"><span data-stu-id="d0be7-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0be7-114">Élément PropertyName pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0be7-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="d0be7-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d0be7-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d0be7-116">Spécifie une propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="d0be7-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="d0be7-117">Élément ScriptBlock pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0be7-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="d0be7-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d0be7-118">Optional element.</span></span><br /><br /> <span data-ttu-id="d0be7-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="d0be7-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="d0be7-120">Élément SelectionSetName pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0be7-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="d0be7-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d0be7-121">Optional element.</span></span><br /><br /> <span data-ttu-id="d0be7-122">Spécifie le jeu des types .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="d0be7-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="d0be7-123">Élément TypeName pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0be7-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="d0be7-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d0be7-124">Optional element.</span></span><br /><br /> <span data-ttu-id="d0be7-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="d0be7-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d0be7-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d0be7-126">Parent Elements</span></span>

|<span data-ttu-id="d0be7-127">Élément</span><span class="sxs-lookup"><span data-stu-id="d0be7-127">Element</span></span>|<span data-ttu-id="d0be7-128">Description</span><span class="sxs-lookup"><span data-stu-id="d0be7-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0be7-129">Élément EntrySelectedBy pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0be7-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="d0be7-130">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d0be7-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d0be7-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="d0be7-131">Remarks</span></span>

<span data-ttu-id="d0be7-132">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="d0be7-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="d0be7-133">La condition de sélection doit spécifier un nom d’un propriété minimum ou un bloc de script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="d0be7-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="d0be7-134">La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="d0be7-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="d0be7-135">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d0be7-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0be7-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0be7-136">See Also</span></span>

[<span data-ttu-id="d0be7-137">Élément PropertyName pour SelectionCondition pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="d0be7-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d0be7-138">Élément ScriptBlock pour SelectionCondition pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="d0be7-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d0be7-139">Élément SelectionSetName pour SelectionCondition pour un contrôle personnalisé pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="d0be7-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d0be7-140">Élément TypeName pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0be7-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="d0be7-141">Élément EntrySelectedBy pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0be7-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="d0be7-142">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0be7-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
