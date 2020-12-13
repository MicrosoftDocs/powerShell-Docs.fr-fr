---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)
description: SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)
ms.openlocfilehash: a5a395f718d0e1a2d7f33d120ce4fd2ff787cc34
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651783"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="e48b2-103">SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e48b2-103">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="e48b2-104">Spécifie un ensemble de types .NET utilisés par cette entrée de la vue table.</span><span class="sxs-lookup"><span data-stu-id="e48b2-104">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="e48b2-105">Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée.</span><span class="sxs-lookup"><span data-stu-id="e48b2-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="e48b2-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry élément (format) EntrySelectedBy élément (format) SelectionSetName élément pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="e48b2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e48b2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e48b2-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e48b2-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e48b2-108">Attributes and Elements</span></span>

<span data-ttu-id="e48b2-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e48b2-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e48b2-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="e48b2-110">Attributes</span></span>

<span data-ttu-id="e48b2-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e48b2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e48b2-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e48b2-112">Child Elements</span></span>

<span data-ttu-id="e48b2-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e48b2-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e48b2-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e48b2-114">Parent Elements</span></span>

|<span data-ttu-id="e48b2-115">Élément</span><span class="sxs-lookup"><span data-stu-id="e48b2-115">Element</span></span>|<span data-ttu-id="e48b2-116">Description</span><span class="sxs-lookup"><span data-stu-id="e48b2-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e48b2-117">Élément EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="e48b2-117">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="e48b2-118">Définit les types .NET qui utilisent cette entrée ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="e48b2-118">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e48b2-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="e48b2-119">Text Value</span></span>

<span data-ttu-id="e48b2-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="e48b2-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e48b2-121">Notes</span><span class="sxs-lookup"><span data-stu-id="e48b2-121">Remarks</span></span>

<span data-ttu-id="e48b2-122">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="e48b2-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="e48b2-123">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="e48b2-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="e48b2-124">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux d’objets pour une vue](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e48b2-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="e48b2-125">Si vous spécifiez un jeu de sélection pour une entrée, vous ne pouvez pas spécifier un nom de type.</span><span class="sxs-lookup"><span data-stu-id="e48b2-125">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="e48b2-126">Pour plus d’informations sur la spécification d’un type .NET, consultez [élément TypeName pour EntrySelectedBy pour TableRowEntry (format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="e48b2-126">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="e48b2-127">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e48b2-127">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e48b2-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e48b2-128">See Also</span></span>

[<span data-ttu-id="e48b2-129">Élément EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="e48b2-129">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="e48b2-130">Définition de jeux d’objets pour une vue</span><span class="sxs-lookup"><span data-stu-id="e48b2-130">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e48b2-131">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="e48b2-131">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e48b2-132">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e48b2-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
