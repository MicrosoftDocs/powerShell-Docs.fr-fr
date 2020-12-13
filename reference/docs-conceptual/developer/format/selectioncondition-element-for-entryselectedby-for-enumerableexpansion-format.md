---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)
description: SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)
ms.openlocfilehash: 3ecf7fde99b9ee66a153eea416792f351ff62af3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647914"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="ba0eb-103">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="ba0eb-103">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="ba0eb-104">Définit la condition qui doit exister pour développer les objets de collection de cette définition.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-104">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="ba0eb-105">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) élément EntrySelectedBy pour EnumerableExpansion (format) élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="ba0eb-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ba0eb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba0eb-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ba0eb-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ba0eb-107">Attributes and Elements</span></span>

<span data-ttu-id="ba0eb-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="ba0eb-109">Vous devez spécifier un seul `PropertyName` `ScriptBlock` élément ou.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="ba0eb-110">Les `SelectionSetName` `TypeName` éléments et sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="ba0eb-111">Vous pouvez spécifier l’un des deux éléments.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ba0eb-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="ba0eb-112">Attributes</span></span>

<span data-ttu-id="ba0eb-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ba0eb-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ba0eb-114">Child Elements</span></span>

|<span data-ttu-id="ba0eb-115">Élément</span><span class="sxs-lookup"><span data-stu-id="ba0eb-115">Element</span></span>|<span data-ttu-id="ba0eb-116">Description</span><span class="sxs-lookup"><span data-stu-id="ba0eb-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ba0eb-117">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="ba0eb-117">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="ba0eb-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-118">Optional element.</span></span><br /><br /> <span data-ttu-id="ba0eb-119">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="ba0eb-120">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="ba0eb-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="ba0eb-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-121">Optional element.</span></span><br /><br /> <span data-ttu-id="ba0eb-122">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-122">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="ba0eb-123">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="ba0eb-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="ba0eb-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-124">Optional element.</span></span><br /><br /> <span data-ttu-id="ba0eb-125">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="ba0eb-126">TypeName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="ba0eb-126">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="ba0eb-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-127">Optional element.</span></span><br /><br /> <span data-ttu-id="ba0eb-128">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ba0eb-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ba0eb-129">Parent Elements</span></span>

|<span data-ttu-id="ba0eb-130">Élément</span><span class="sxs-lookup"><span data-stu-id="ba0eb-130">Element</span></span>|<span data-ttu-id="ba0eb-131">Description</span><span class="sxs-lookup"><span data-stu-id="ba0eb-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ba0eb-132">EntrySelectedBy, élément pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="ba0eb-132">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="ba0eb-133">Définit les objets de collection .NET développés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-133">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ba0eb-134">Notes</span><span class="sxs-lookup"><span data-stu-id="ba0eb-134">Remarks</span></span>

<span data-ttu-id="ba0eb-135">Au moins un nom de type, un jeu de sélection ou une condition de sélection doivent être définis pour chaque définition.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-135">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="ba0eb-136">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="ba0eb-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="ba0eb-137">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="ba0eb-138">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="ba0eb-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="ba0eb-139">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions pour la diffusion des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ba0eb-139">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ba0eb-140">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="ba0eb-140">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba0eb-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba0eb-141">See Also</span></span>

[<span data-ttu-id="ba0eb-142">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="ba0eb-142">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ba0eb-143">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba0eb-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
