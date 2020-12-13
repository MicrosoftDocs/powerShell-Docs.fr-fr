---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)
description: SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)
ms.openlocfilehash: c6466e3ac6e1f194df9172468d26448f9630da6a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655016"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="fdd89-103">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="fdd89-103">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="fdd89-104">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="fdd89-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="fdd89-105">Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de cette définition de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="fdd89-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="fdd89-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) élément SelectionCondition pour EntrySelectedBy (format) WideEntry élément pour SelectionSetName pour SelectionCondition (format)</span><span class="sxs-lookup"><span data-stu-id="fdd89-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fdd89-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdd89-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fdd89-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fdd89-108">Attributes and Elements</span></span>

<span data-ttu-id="fdd89-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="fdd89-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fdd89-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="fdd89-110">Attributes</span></span>

<span data-ttu-id="fdd89-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fdd89-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fdd89-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fdd89-112">Child Elements</span></span>

<span data-ttu-id="fdd89-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fdd89-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fdd89-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fdd89-114">Parent Elements</span></span>

|<span data-ttu-id="fdd89-115">Élément</span><span class="sxs-lookup"><span data-stu-id="fdd89-115">Element</span></span>|<span data-ttu-id="fdd89-116">Description</span><span class="sxs-lookup"><span data-stu-id="fdd89-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fdd89-117">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fdd89-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="fdd89-118">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="fdd89-118">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fdd89-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="fdd89-119">Text Value</span></span>

<span data-ttu-id="fdd89-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="fdd89-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="fdd89-121">Notes</span><span class="sxs-lookup"><span data-stu-id="fdd89-121">Remarks</span></span>

<span data-ttu-id="fdd89-122">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="fdd89-122">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="fdd89-123">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="fdd89-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="fdd89-124">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="fdd89-124">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="fdd89-125">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="fdd89-125">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="fdd89-126">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="fdd89-126">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fdd89-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fdd89-127">See Also</span></span>

[<span data-ttu-id="fdd89-128">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="fdd89-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="fdd89-129">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="fdd89-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="fdd89-130">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="fdd89-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="fdd89-131">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fdd89-131">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="fdd89-132">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fdd89-132">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="fdd89-133">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="fdd89-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
