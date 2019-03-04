---
title: Élément SelectionCondition pour EntrySelectedBy pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858015"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="774ab-102">SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="774ab-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="774ab-103">Définit une condition qui doit exister pour la définition du contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="774ab-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="774ab-104">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="774ab-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="774ab-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour les contrôles d’élément de CustomEntry vue (Format) pour CustomEntries pour les contrôles d’élément de EntrySelectedBy vue (Format) pour CustomEntry pour les contrôles d’élément de SelectionCondition vue (Format) pour EntrySelectedBy pour les contrôles pour afficher ( Format)</span><span class="sxs-lookup"><span data-stu-id="774ab-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="774ab-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="774ab-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="774ab-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="774ab-107">Attributes and Elements</span></span>

<span data-ttu-id="774ab-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="774ab-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="774ab-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="774ab-109">Attributes</span></span>

<span data-ttu-id="774ab-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="774ab-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="774ab-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="774ab-111">Child Elements</span></span>

|<span data-ttu-id="774ab-112">Élément</span><span class="sxs-lookup"><span data-stu-id="774ab-112">Element</span></span>|<span data-ttu-id="774ab-113">Description</span><span class="sxs-lookup"><span data-stu-id="774ab-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="774ab-114">Élément PropertyName pour SelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="774ab-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="774ab-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="774ab-115">Optional element.</span></span><br /><br /> <span data-ttu-id="774ab-116">Spécifie une propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="774ab-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="774ab-117">Élément ScriptBlock pour SelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="774ab-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="774ab-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="774ab-118">Optional element.</span></span><br /><br /> <span data-ttu-id="774ab-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="774ab-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="774ab-120">Élément SelectionSetName pour SelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="774ab-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="774ab-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="774ab-121">Optional element.</span></span><br /><br /> <span data-ttu-id="774ab-122">Spécifie le jeu des types .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="774ab-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="774ab-123">Élément TypeName pour SelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="774ab-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="774ab-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="774ab-124">Optional element.</span></span><br /><br /> <span data-ttu-id="774ab-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="774ab-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="774ab-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="774ab-126">Parent Elements</span></span>

|<span data-ttu-id="774ab-127">Élément</span><span class="sxs-lookup"><span data-stu-id="774ab-127">Element</span></span>|<span data-ttu-id="774ab-128">Description</span><span class="sxs-lookup"><span data-stu-id="774ab-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="774ab-129">Élément EntrySelectedBy pour CustomEntry pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="774ab-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="774ab-130">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="774ab-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="774ab-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="774ab-131">Remarks</span></span>

<span data-ttu-id="774ab-132">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="774ab-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="774ab-133">La condition de sélection doit spécifier un nom d’un propriété minimum ou un bloc de script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="774ab-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="774ab-134">La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="774ab-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="774ab-135">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="774ab-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="774ab-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="774ab-136">See Also</span></span>

[<span data-ttu-id="774ab-137">Élément PropertyName pour SelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="774ab-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="774ab-138">Élément ScriptBlock pour SelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="774ab-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="774ab-139">Élément SelectionSetName pour SelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="774ab-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="774ab-140">Élément TypeName pour SelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="774ab-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="774ab-141">Élément EntrySelectedBy pour CustomEntry pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="774ab-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="774ab-142">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="774ab-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
