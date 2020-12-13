---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour SelectionCondition pour GroupBy (Format)
description: SelectionSetName, élément pour SelectionCondition pour GroupBy (Format)
ms.openlocfilehash: a4f28c1caba3790718b99f63659cb0cbed8def16
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654985"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="98a50-103">SelectionSetName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="98a50-103">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="98a50-104">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="98a50-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="98a50-105">Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="98a50-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="98a50-106">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="98a50-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="98a50-107">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour la vue (format) CustomControl, élément de GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) EntrySelectedBy élément pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="98a50-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="98a50-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98a50-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="98a50-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="98a50-109">Attributes and Elements</span></span>

<span data-ttu-id="98a50-110">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="98a50-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="98a50-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="98a50-111">Attributes</span></span>

<span data-ttu-id="98a50-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="98a50-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="98a50-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="98a50-113">Child Elements</span></span>

<span data-ttu-id="98a50-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="98a50-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="98a50-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="98a50-115">Parent Elements</span></span>

|<span data-ttu-id="98a50-116">Élément</span><span class="sxs-lookup"><span data-stu-id="98a50-116">Element</span></span>|<span data-ttu-id="98a50-117">Description</span><span class="sxs-lookup"><span data-stu-id="98a50-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98a50-118">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="98a50-118">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="98a50-119">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="98a50-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="98a50-120">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="98a50-120">Text Value</span></span>

<span data-ttu-id="98a50-121">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="98a50-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="98a50-122">Notes</span><span class="sxs-lookup"><span data-stu-id="98a50-122">Remarks</span></span>

<span data-ttu-id="98a50-123">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="98a50-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="98a50-124">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="98a50-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="98a50-125">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="98a50-125">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="98a50-126">Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="98a50-126">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="98a50-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98a50-127">See Also</span></span>

[<span data-ttu-id="98a50-128">TypeName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="98a50-128">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="98a50-129">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="98a50-129">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="98a50-130">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="98a50-130">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="98a50-131">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="98a50-131">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="98a50-132">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="98a50-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
