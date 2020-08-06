---
title: Élément SelectionSetName pour EntrySelectedBy pour EnumerableExpansion (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8745ef9e6f326c3e8a5dbf185a595bbe93e92414
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785317"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="b3c90-102">SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="b3c90-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="b3c90-103">Spécifie l’ensemble des types .NET développés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="b3c90-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="b3c90-104">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) élément EntrySelectedBy pour EnumerableExpansion (format) élément SelectionSetName pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="b3c90-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b3c90-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3c90-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b3c90-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b3c90-106">Attributes and Elements</span></span>

<span data-ttu-id="b3c90-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="b3c90-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b3c90-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="b3c90-108">Attributes</span></span>

<span data-ttu-id="b3c90-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b3c90-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b3c90-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b3c90-110">Child Elements</span></span>

<span data-ttu-id="b3c90-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b3c90-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b3c90-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b3c90-112">Parent Elements</span></span>

|<span data-ttu-id="b3c90-113">Élément</span><span class="sxs-lookup"><span data-stu-id="b3c90-113">Element</span></span>|<span data-ttu-id="b3c90-114">Description</span><span class="sxs-lookup"><span data-stu-id="b3c90-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b3c90-115">EntrySelectedBy, élément pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="b3c90-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="b3c90-116">Définit les objets de collection .NET développés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="b3c90-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b3c90-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="b3c90-117">Text Value</span></span>

<span data-ttu-id="b3c90-118">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="b3c90-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b3c90-119">Notes</span><span class="sxs-lookup"><span data-stu-id="b3c90-119">Remarks</span></span>

<span data-ttu-id="b3c90-120">Chaque définition doit spécifier un ou plusieurs noms de types, un jeu de sélection ou une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="b3c90-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="b3c90-121">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="b3c90-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="b3c90-122">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="b3c90-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="b3c90-123">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux d’objets pour une vue](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b3c90-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3c90-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3c90-124">See Also</span></span>

[<span data-ttu-id="b3c90-125">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="b3c90-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b3c90-126">EntrySelectedBy, élément pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="b3c90-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="b3c90-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3c90-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
