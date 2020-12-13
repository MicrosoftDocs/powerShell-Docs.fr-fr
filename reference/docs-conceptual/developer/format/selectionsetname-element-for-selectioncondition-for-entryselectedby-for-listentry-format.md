---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)
description: SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)
ms.openlocfilehash: f3193799e67706eb07f0fe1c2cd42cce83f7af57
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651541"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="88337-103">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="88337-103">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="88337-104">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="88337-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="88337-105">Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="88337-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="88337-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionCondition pour EntrySelectedBy pour ListEntry (format) SelectionSetName élément pour SelectionCondition pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="88337-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="88337-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88337-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="88337-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="88337-108">Attributes and Elements</span></span>

<span data-ttu-id="88337-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="88337-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="88337-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="88337-110">Attributes</span></span>

<span data-ttu-id="88337-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="88337-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="88337-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="88337-112">Child Elements</span></span>

<span data-ttu-id="88337-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="88337-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="88337-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="88337-114">Parent Elements</span></span>

|<span data-ttu-id="88337-115">Élément</span><span class="sxs-lookup"><span data-stu-id="88337-115">Element</span></span>|<span data-ttu-id="88337-116">Description</span><span class="sxs-lookup"><span data-stu-id="88337-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88337-117">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="88337-117">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="88337-118">Définit la condition qui doit exister pour utiliser cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="88337-118">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="88337-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="88337-119">Text Value</span></span>

<span data-ttu-id="88337-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="88337-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="88337-121">Notes</span><span class="sxs-lookup"><span data-stu-id="88337-121">Remarks</span></span>

<span data-ttu-id="88337-122">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="88337-122">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="88337-123">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="88337-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="88337-124">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="88337-124">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="88337-125">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="88337-125">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="88337-126">Pour plus d’informations sur les autres composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="88337-126">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="88337-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88337-127">See Also</span></span>

[<span data-ttu-id="88337-128">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="88337-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="88337-129">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="88337-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="88337-130">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="88337-130">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="88337-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="88337-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
