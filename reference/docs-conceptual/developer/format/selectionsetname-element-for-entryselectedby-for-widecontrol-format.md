---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour EntrySelectedBy pour WideControl (Format)
description: SelectionSetName, élément pour EntrySelectedBy pour WideControl (Format)
ms.openlocfilehash: bf6a44bb733421f36a9140d0ec10e61aedfbda6a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651687"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="4c337-103">SelectionSetName, élément pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4c337-103">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="4c337-104">Spécifie un jeu d’objets .NET pour la définition.</span><span class="sxs-lookup"><span data-stu-id="4c337-104">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="4c337-105">La définition est utilisée chaque fois que l’un de ces objets est affiché.</span><span class="sxs-lookup"><span data-stu-id="4c337-105">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="4c337-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) EntrySelectedBy élément pour WideEntry (format) SelectionSetName élément pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="4c337-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4c337-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c337-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4c337-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4c337-108">Attributes and Elements</span></span>

<span data-ttu-id="4c337-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="4c337-109">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4c337-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="4c337-110">Attributes</span></span>

<span data-ttu-id="4c337-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4c337-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4c337-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4c337-112">Child Elements</span></span>

<span data-ttu-id="4c337-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4c337-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4c337-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4c337-114">Parent Elements</span></span>

|<span data-ttu-id="4c337-115">Élément</span><span class="sxs-lookup"><span data-stu-id="4c337-115">Element</span></span>|<span data-ttu-id="4c337-116">Description</span><span class="sxs-lookup"><span data-stu-id="4c337-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4c337-117">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4c337-117">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="4c337-118">Définit les types .NET qui utilisent cette entrée étendue ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="4c337-118">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4c337-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="4c337-119">Text Value</span></span>

<span data-ttu-id="4c337-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="4c337-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="4c337-121">Notes</span><span class="sxs-lookup"><span data-stu-id="4c337-121">Remarks</span></span>

<span data-ttu-id="4c337-122">Chaque définition doit spécifier un nom de type, un jeu de sélection ou une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="4c337-122">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="4c337-123">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="4c337-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="4c337-124">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="4c337-124">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="4c337-125">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux d’objets pour une vue](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="4c337-125">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="4c337-126">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="4c337-126">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c337-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c337-127">See Also</span></span>

[<span data-ttu-id="4c337-128">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="4c337-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4c337-129">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="4c337-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="4c337-130">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4c337-130">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="4c337-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="4c337-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
