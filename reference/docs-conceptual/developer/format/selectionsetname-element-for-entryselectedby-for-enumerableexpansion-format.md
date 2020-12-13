---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)
description: SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)
ms.openlocfilehash: 074f810f5a3cbad61ee8be69408967758f0591df
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651884"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="7fca1-103">SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7fca1-103">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="7fca1-104">Spécifie l’ensemble des types .NET développés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="7fca1-104">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="7fca1-105">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) élément EntrySelectedBy pour EnumerableExpansion (format) élément SelectionSetName pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7fca1-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7fca1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fca1-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="7fca1-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7fca1-107">Attributes and Elements</span></span>

<span data-ttu-id="7fca1-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="7fca1-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7fca1-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="7fca1-109">Attributes</span></span>

<span data-ttu-id="7fca1-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7fca1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7fca1-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7fca1-111">Child Elements</span></span>

<span data-ttu-id="7fca1-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7fca1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7fca1-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7fca1-113">Parent Elements</span></span>

|<span data-ttu-id="7fca1-114">Élément</span><span class="sxs-lookup"><span data-stu-id="7fca1-114">Element</span></span>|<span data-ttu-id="7fca1-115">Description</span><span class="sxs-lookup"><span data-stu-id="7fca1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7fca1-116">EntrySelectedBy, élément pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7fca1-116">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="7fca1-117">Définit les objets de collection .NET développés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="7fca1-117">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7fca1-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="7fca1-118">Text Value</span></span>

<span data-ttu-id="7fca1-119">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="7fca1-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="7fca1-120">Notes</span><span class="sxs-lookup"><span data-stu-id="7fca1-120">Remarks</span></span>

<span data-ttu-id="7fca1-121">Chaque définition doit spécifier un ou plusieurs noms de types, un jeu de sélection ou une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="7fca1-121">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="7fca1-122">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="7fca1-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="7fca1-123">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="7fca1-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="7fca1-124">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux d’objets pour une vue](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="7fca1-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7fca1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7fca1-125">See Also</span></span>

[<span data-ttu-id="7fca1-126">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="7fca1-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="7fca1-127">EntrySelectedBy, élément pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7fca1-127">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="7fca1-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="7fca1-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
