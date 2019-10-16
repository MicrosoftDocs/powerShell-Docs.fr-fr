---
title: Élément SelectionSetName pour EntrySelectedBy pour EnumerableExpansion (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368328"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="55a9c-102">SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="55a9c-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="55a9c-103">Spécifie l’ensemble des types .NET développés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="55a9c-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="55a9c-104">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) élément EntrySelectedBy pour EnumerableExpansion (format) élément SelectionSetName pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="55a9c-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="55a9c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55a9c-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="55a9c-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="55a9c-106">Attributes and Elements</span></span>

<span data-ttu-id="55a9c-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="55a9c-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="55a9c-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="55a9c-108">Attributes</span></span>

<span data-ttu-id="55a9c-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="55a9c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55a9c-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="55a9c-110">Child Elements</span></span>

<span data-ttu-id="55a9c-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="55a9c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="55a9c-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="55a9c-112">Parent Elements</span></span>

|<span data-ttu-id="55a9c-113">Élément</span><span class="sxs-lookup"><span data-stu-id="55a9c-113">Element</span></span>|<span data-ttu-id="55a9c-114">Description</span><span class="sxs-lookup"><span data-stu-id="55a9c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55a9c-115">Élément EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="55a9c-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="55a9c-116">Définit les objets de collection .NET développés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="55a9c-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="55a9c-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="55a9c-117">Text Value</span></span>

<span data-ttu-id="55a9c-118">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="55a9c-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="55a9c-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="55a9c-119">Remarks</span></span>

<span data-ttu-id="55a9c-120">Chaque définition doit spécifier un ou plusieurs noms de types, un jeu de sélection ou une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="55a9c-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="55a9c-121">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="55a9c-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="55a9c-122">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="55a9c-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="55a9c-123">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux d’objets pour une vue](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="55a9c-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="55a9c-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55a9c-124">See Also</span></span>

[<span data-ttu-id="55a9c-125">Définition des jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="55a9c-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="55a9c-126">Élément EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="55a9c-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="55a9c-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="55a9c-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
