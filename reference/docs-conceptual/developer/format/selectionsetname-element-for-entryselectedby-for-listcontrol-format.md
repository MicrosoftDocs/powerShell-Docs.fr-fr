---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)
description: SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)
ms.openlocfilehash: 413a77f7ba06fe952e574061e58d0b5d80c5b3c4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651828"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="0a2dd-103">SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0a2dd-103">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="0a2dd-104">Spécifie un ensemble d’objets .NET pour l’entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="0a2dd-104">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="0a2dd-105">Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée.</span><span class="sxs-lookup"><span data-stu-id="0a2dd-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="0a2dd-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionSetName pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0a2dd-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0a2dd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a2dd-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0a2dd-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0a2dd-108">Attributes and Elements</span></span>

<span data-ttu-id="0a2dd-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="0a2dd-109">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0a2dd-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0a2dd-110">Attributes</span></span>

<span data-ttu-id="0a2dd-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0a2dd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0a2dd-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0a2dd-112">Child Elements</span></span>

<span data-ttu-id="0a2dd-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0a2dd-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0a2dd-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0a2dd-114">Parent Elements</span></span>

|<span data-ttu-id="0a2dd-115">Élément</span><span class="sxs-lookup"><span data-stu-id="0a2dd-115">Element</span></span>|<span data-ttu-id="0a2dd-116">Description</span><span class="sxs-lookup"><span data-stu-id="0a2dd-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0a2dd-117">Élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0a2dd-117">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="0a2dd-118">Définit les types .NET qui utilisent cette entrée de liste ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="0a2dd-118">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0a2dd-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="0a2dd-119">Text Value</span></span>

<span data-ttu-id="0a2dd-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="0a2dd-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a2dd-121">Notes</span><span class="sxs-lookup"><span data-stu-id="0a2dd-121">Remarks</span></span>

<span data-ttu-id="0a2dd-122">Au moins un nom de type, un jeu de sélection ou une condition de sélection doivent être définis pour chaque entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="0a2dd-122">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="0a2dd-123">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="0a2dd-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="0a2dd-124">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="0a2dd-124">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="0a2dd-125">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux d’objets pour une vue](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0a2dd-125">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="0a2dd-126">Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="0a2dd-126">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0a2dd-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="0a2dd-127">Example</span></span>

<span data-ttu-id="0a2dd-128">L’exemple suivant montre comment spécifier un jeu de sélection pour une entrée d’un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="0a2dd-128">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="0a2dd-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a2dd-129">See Also</span></span>

[<span data-ttu-id="0a2dd-130">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="0a2dd-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0a2dd-131">Élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0a2dd-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="0a2dd-132">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a2dd-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
