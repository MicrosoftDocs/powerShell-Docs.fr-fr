---
title: Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368428"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="3aaec-102">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3aaec-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="3aaec-103">Définit une condition qui doit exister pour une définition de contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="3aaec-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="3aaec-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="3aaec-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="3aaec-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format) élément EntrySelectedBy pour CustomEntry pour GroupBy (format) élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3aaec-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3aaec-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3aaec-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3aaec-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="3aaec-107">Attributes and Elements</span></span>

<span data-ttu-id="3aaec-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="3aaec-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3aaec-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="3aaec-109">Attributes</span></span>

<span data-ttu-id="3aaec-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="3aaec-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3aaec-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3aaec-111">Child Elements</span></span>

|<span data-ttu-id="3aaec-112">Élément</span><span class="sxs-lookup"><span data-stu-id="3aaec-112">Element</span></span>|<span data-ttu-id="3aaec-113">Description</span><span class="sxs-lookup"><span data-stu-id="3aaec-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3aaec-114">PropertyName, élément de SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3aaec-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="3aaec-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3aaec-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3aaec-116">Spécifie une propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="3aaec-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="3aaec-117">Élément ScriptBlock pour SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3aaec-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="3aaec-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3aaec-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3aaec-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="3aaec-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="3aaec-120">Élément SelectionSetName pour SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3aaec-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="3aaec-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3aaec-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3aaec-122">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="3aaec-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="3aaec-123">Élément TypeName pour SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3aaec-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="3aaec-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3aaec-124">Optional element.</span></span><br /><br /> <span data-ttu-id="3aaec-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="3aaec-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3aaec-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3aaec-126">Parent Elements</span></span>

|<span data-ttu-id="3aaec-127">Élément</span><span class="sxs-lookup"><span data-stu-id="3aaec-127">Element</span></span>|<span data-ttu-id="3aaec-128">Description</span><span class="sxs-lookup"><span data-stu-id="3aaec-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3aaec-129">Élément EntrySelectedBy pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3aaec-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="3aaec-130">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="3aaec-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3aaec-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="3aaec-131">Remarks</span></span>

<span data-ttu-id="3aaec-132">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="3aaec-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="3aaec-133">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="3aaec-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="3aaec-134">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="3aaec-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="3aaec-135">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3aaec-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3aaec-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3aaec-136">See Also</span></span>

[<span data-ttu-id="3aaec-137">Élément PropertyName pour SelectionCondition pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3aaec-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3aaec-138">Élément ScriptBlock pour SelectionCondition pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3aaec-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3aaec-139">Élément SelectionSetName pour SelectionCondition pour un contrôle personnalisé pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3aaec-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3aaec-140">Élément TypeName pour SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3aaec-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="3aaec-141">Élément EntrySelectedBy pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3aaec-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="3aaec-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="3aaec-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
