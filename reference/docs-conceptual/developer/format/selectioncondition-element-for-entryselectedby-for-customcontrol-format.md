---
title: Élément SelectionCondition pour EntrySelectedBy pour CustomControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368438"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="1f96d-102">SelectionCondition, élément pour EntrySelectedBy pour CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1f96d-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="1f96d-103">Définit une condition qui doit exister pour une définition de contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="1f96d-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="1f96d-104">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1f96d-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="1f96d-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour l’élément View (format) CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour CustomControl pour View ( Format) élément CustomItem pour CustomEntry pour CustomControl pour la vue (format) élément EntrySelectedBy pour CustomEntry pour CustomControl pour l’élément View (format) SelectionCondition pour CustomControl pour la vue (format)</span><span class="sxs-lookup"><span data-stu-id="1f96d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f96d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f96d-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f96d-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="1f96d-107">Attributes and Elements</span></span>

<span data-ttu-id="1f96d-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="1f96d-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f96d-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="1f96d-109">Attributes</span></span>

<span data-ttu-id="1f96d-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="1f96d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f96d-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1f96d-111">Child Elements</span></span>

|<span data-ttu-id="1f96d-112">Élément</span><span class="sxs-lookup"><span data-stu-id="1f96d-112">Element</span></span>|<span data-ttu-id="1f96d-113">Description</span><span class="sxs-lookup"><span data-stu-id="1f96d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f96d-114">Élément PropertyName pour SelectionCondition pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f96d-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="1f96d-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1f96d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1f96d-116">Spécifie une propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="1f96d-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="1f96d-117">Élément ScriptBlock pour SelectionCondition pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f96d-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="1f96d-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1f96d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="1f96d-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="1f96d-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="1f96d-120">Élément SelectionSetName pour SelectionCondition pour un contrôle personnalisé pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f96d-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="1f96d-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1f96d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="1f96d-122">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="1f96d-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="1f96d-123">Élément TypeName pour SelectionCondition pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f96d-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="1f96d-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1f96d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="1f96d-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="1f96d-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1f96d-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1f96d-126">Parent Elements</span></span>

|<span data-ttu-id="1f96d-127">Élément</span><span class="sxs-lookup"><span data-stu-id="1f96d-127">Element</span></span>|<span data-ttu-id="1f96d-128">Description</span><span class="sxs-lookup"><span data-stu-id="1f96d-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f96d-129">Élément EntrySelectedBy pour CustomEntry pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f96d-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="1f96d-130">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="1f96d-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1f96d-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="1f96d-131">Remarks</span></span>

<span data-ttu-id="1f96d-132">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="1f96d-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="1f96d-133">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="1f96d-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="1f96d-134">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="1f96d-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="1f96d-135">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1f96d-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f96d-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f96d-136">See Also</span></span>

[<span data-ttu-id="1f96d-137">Élément PropertyName pour SelectionCondition pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f96d-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1f96d-138">Élément ScriptBlock pour SelectionCondition pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f96d-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1f96d-139">Élément SelectionSetName pour SelectionCondition pour un contrôle personnalisé pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f96d-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1f96d-140">Élément TypeName pour SelectionCondition pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f96d-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1f96d-141">Élément EntrySelectedBy pour CustomEntry pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f96d-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1f96d-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f96d-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
