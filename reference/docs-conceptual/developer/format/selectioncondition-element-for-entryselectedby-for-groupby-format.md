---
title: Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0930d8076c314c12cac6cdfa2b33716b7efeb6a9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772839"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="a0972-102">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a0972-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="a0972-103">Définit une condition qui doit exister pour une définition de contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="a0972-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="a0972-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="a0972-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a0972-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) EntrySelectedBy élément pour CustomEntry pour GroupBy (format) élément SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a0972-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a0972-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0972-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a0972-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a0972-107">Attributes and Elements</span></span>

<span data-ttu-id="a0972-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="a0972-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a0972-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="a0972-109">Attributes</span></span>

<span data-ttu-id="a0972-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a0972-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a0972-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a0972-111">Child Elements</span></span>

|<span data-ttu-id="a0972-112">Élément</span><span class="sxs-lookup"><span data-stu-id="a0972-112">Element</span></span>|<span data-ttu-id="a0972-113">Description</span><span class="sxs-lookup"><span data-stu-id="a0972-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a0972-114">PropertyName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a0972-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="a0972-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a0972-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a0972-116">Spécifie une propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="a0972-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a0972-117">Élément ScriptBlock pour SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a0972-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="a0972-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a0972-118">Optional element.</span></span><br /><br /> <span data-ttu-id="a0972-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="a0972-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="a0972-120">SelectionSetName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a0972-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="a0972-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a0972-121">Optional element.</span></span><br /><br /> <span data-ttu-id="a0972-122">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="a0972-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="a0972-123">Élément TypeName pour SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a0972-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="a0972-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a0972-124">Optional element.</span></span><br /><br /> <span data-ttu-id="a0972-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="a0972-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a0972-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a0972-126">Parent Elements</span></span>

|<span data-ttu-id="a0972-127">Élément</span><span class="sxs-lookup"><span data-stu-id="a0972-127">Element</span></span>|<span data-ttu-id="a0972-128">Description</span><span class="sxs-lookup"><span data-stu-id="a0972-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a0972-129">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a0972-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="a0972-130">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="a0972-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a0972-131">Notes</span><span class="sxs-lookup"><span data-stu-id="a0972-131">Remarks</span></span>

<span data-ttu-id="a0972-132">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="a0972-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="a0972-133">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="a0972-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="a0972-134">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="a0972-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="a0972-135">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a0972-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0972-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0972-136">See Also</span></span>

[<span data-ttu-id="a0972-137">PropertyName, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a0972-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a0972-138">ScriptBlock, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a0972-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a0972-139">Élément SelectionSetName pour SelectionCondition pour un contrôle personnalisé pour View (format)</span><span class="sxs-lookup"><span data-stu-id="a0972-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a0972-140">Élément TypeName pour SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a0972-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="a0972-141">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a0972-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="a0972-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0972-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
