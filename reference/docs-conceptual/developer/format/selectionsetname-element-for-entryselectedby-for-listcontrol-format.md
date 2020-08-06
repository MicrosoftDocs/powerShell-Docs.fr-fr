---
title: Élément SelectionSetName pour EntrySelectedBy pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4315d81da4ceeb7a5b171087434ae15fb09e6592
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785266"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="485d3-102">SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="485d3-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="485d3-103">Spécifie un ensemble d’objets .NET pour l’entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="485d3-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="485d3-104">Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée.</span><span class="sxs-lookup"><span data-stu-id="485d3-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="485d3-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionSetName pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="485d3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="485d3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="485d3-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="485d3-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="485d3-107">Attributes and Elements</span></span>

<span data-ttu-id="485d3-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="485d3-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="485d3-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="485d3-109">Attributes</span></span>

<span data-ttu-id="485d3-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="485d3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="485d3-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="485d3-111">Child Elements</span></span>

<span data-ttu-id="485d3-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="485d3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="485d3-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="485d3-113">Parent Elements</span></span>

|<span data-ttu-id="485d3-114">Élément</span><span class="sxs-lookup"><span data-stu-id="485d3-114">Element</span></span>|<span data-ttu-id="485d3-115">Description</span><span class="sxs-lookup"><span data-stu-id="485d3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="485d3-116">Élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="485d3-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="485d3-117">Définit les types .NET qui utilisent cette entrée de liste ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="485d3-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="485d3-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="485d3-118">Text Value</span></span>

<span data-ttu-id="485d3-119">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="485d3-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="485d3-120">Notes</span><span class="sxs-lookup"><span data-stu-id="485d3-120">Remarks</span></span>

<span data-ttu-id="485d3-121">Au moins un nom de type, un jeu de sélection ou une condition de sélection doivent être définis pour chaque entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="485d3-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="485d3-122">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="485d3-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="485d3-123">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="485d3-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="485d3-124">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux d’objets pour une vue](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="485d3-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="485d3-125">Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="485d3-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="485d3-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="485d3-126">Example</span></span>

<span data-ttu-id="485d3-127">L’exemple suivant montre comment spécifier un jeu de sélection pour une entrée d’un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="485d3-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="485d3-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="485d3-128">See Also</span></span>

[<span data-ttu-id="485d3-129">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="485d3-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="485d3-130">Élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="485d3-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="485d3-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="485d3-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
