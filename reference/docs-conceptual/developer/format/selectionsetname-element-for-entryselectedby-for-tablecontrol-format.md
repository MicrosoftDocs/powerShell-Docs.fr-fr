---
title: Élément SelectionSetName pour EntrySelectedBy pour table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e68aa74b201abf345e87411db6cb2787ddd4f72b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772686"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="a48c5-102">SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a48c5-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="a48c5-103">Spécifie un ensemble de types .NET utilisés par cette entrée de la vue table.</span><span class="sxs-lookup"><span data-stu-id="a48c5-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="a48c5-104">Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée.</span><span class="sxs-lookup"><span data-stu-id="a48c5-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="a48c5-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry élément (format) EntrySelectedBy élément (format) SelectionSetName élément pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="a48c5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a48c5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a48c5-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a48c5-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a48c5-107">Attributes and Elements</span></span>

<span data-ttu-id="a48c5-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a48c5-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a48c5-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="a48c5-109">Attributes</span></span>

<span data-ttu-id="a48c5-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a48c5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a48c5-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a48c5-111">Child Elements</span></span>

<span data-ttu-id="a48c5-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a48c5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a48c5-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a48c5-113">Parent Elements</span></span>

|<span data-ttu-id="a48c5-114">Élément</span><span class="sxs-lookup"><span data-stu-id="a48c5-114">Element</span></span>|<span data-ttu-id="a48c5-115">Description</span><span class="sxs-lookup"><span data-stu-id="a48c5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a48c5-116">Élément EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="a48c5-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="a48c5-117">Définit les types .NET qui utilisent cette entrée ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="a48c5-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a48c5-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="a48c5-118">Text Value</span></span>

<span data-ttu-id="a48c5-119">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="a48c5-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a48c5-120">Notes</span><span class="sxs-lookup"><span data-stu-id="a48c5-120">Remarks</span></span>

<span data-ttu-id="a48c5-121">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="a48c5-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="a48c5-122">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="a48c5-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="a48c5-123">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux d’objets pour une vue](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a48c5-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="a48c5-124">Si vous spécifiez un jeu de sélection pour une entrée, vous ne pouvez pas spécifier un nom de type.</span><span class="sxs-lookup"><span data-stu-id="a48c5-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="a48c5-125">Pour plus d’informations sur la spécification d’un type .NET, consultez [élément TypeName pour EntrySelectedBy pour TableRowEntry (format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="a48c5-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="a48c5-126">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a48c5-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a48c5-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a48c5-127">See Also</span></span>

[<span data-ttu-id="a48c5-128">Élément EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="a48c5-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="a48c5-129">Définition de jeux d’objets pour une vue</span><span class="sxs-lookup"><span data-stu-id="a48c5-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a48c5-130">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="a48c5-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a48c5-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a48c5-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
