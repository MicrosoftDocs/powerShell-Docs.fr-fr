---
title: Élément SelectionCondition pour EntrySelectedBy pour les contrôles pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362048"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="8b77a-102">SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="8b77a-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="8b77a-103">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="8b77a-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="8b77a-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="8b77a-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="8b77a-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour les contrôles pour l’élément d’affichage (format) CustomEntry pour CustomEntries pour les contrôles pour l’élément EntrySelectedBy (format) de vue pour CustomEntry pour les contrôles pour l’élément d’affichage (format) SelectionCondition pour les contrôles pour la vue ( Format</span><span class="sxs-lookup"><span data-stu-id="8b77a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8b77a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b77a-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8b77a-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="8b77a-107">Attributes and Elements</span></span>

<span data-ttu-id="8b77a-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="8b77a-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8b77a-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="8b77a-109">Attributes</span></span>

<span data-ttu-id="8b77a-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="8b77a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8b77a-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8b77a-111">Child Elements</span></span>

|<span data-ttu-id="8b77a-112">Élément</span><span class="sxs-lookup"><span data-stu-id="8b77a-112">Element</span></span>|<span data-ttu-id="8b77a-113">Description</span><span class="sxs-lookup"><span data-stu-id="8b77a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b77a-114">Élément PropertyName pour SelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8b77a-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8b77a-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="8b77a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8b77a-116">Spécifie une propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="8b77a-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="8b77a-117">Élément ScriptBlock pour SelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8b77a-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8b77a-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="8b77a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8b77a-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="8b77a-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="8b77a-120">Élément SelectionSetName pour SelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8b77a-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8b77a-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="8b77a-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8b77a-122">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="8b77a-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="8b77a-123">Élément TypeName pour SelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8b77a-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8b77a-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="8b77a-124">Optional element.</span></span><br /><br /> <span data-ttu-id="8b77a-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="8b77a-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8b77a-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8b77a-126">Parent Elements</span></span>

|<span data-ttu-id="8b77a-127">Élément</span><span class="sxs-lookup"><span data-stu-id="8b77a-127">Element</span></span>|<span data-ttu-id="8b77a-128">Description</span><span class="sxs-lookup"><span data-stu-id="8b77a-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b77a-129">Élément EntrySelectedBy pour CustomEntry pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8b77a-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="8b77a-130">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="8b77a-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8b77a-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="8b77a-131">Remarks</span></span>

<span data-ttu-id="8b77a-132">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="8b77a-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="8b77a-133">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="8b77a-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="8b77a-134">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="8b77a-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="8b77a-135">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8b77a-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b77a-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b77a-136">See Also</span></span>

[<span data-ttu-id="8b77a-137">Élément PropertyName pour SelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8b77a-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8b77a-138">Élément ScriptBlock pour SelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8b77a-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8b77a-139">Élément SelectionSetName pour SelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8b77a-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8b77a-140">Élément TypeName pour SelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8b77a-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8b77a-141">Élément EntrySelectedBy pour CustomEntry pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8b77a-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="8b77a-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b77a-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
