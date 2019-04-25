---
title: Élément SelectionSetName pour EntrySelectedBy pour EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076257"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="174f6-102">SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="174f6-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="174f6-103">Spécifie l’ensemble des types .NET qui sont développées par cette définition.</span><span class="sxs-lookup"><span data-stu-id="174f6-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="174f6-104">Configuration élément (Format) élément DefaultSettings (Format) EnumerableExpansions (Format) élément EnumerableExpansion (Format) EntrySelectedBy élément d’élément de SelectionSetName EnumerableExpansion (Format) pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="174f6-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="174f6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="174f6-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="174f6-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="174f6-106">Attributes and Elements</span></span>

<span data-ttu-id="174f6-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="174f6-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="174f6-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="174f6-108">Attributes</span></span>

<span data-ttu-id="174f6-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="174f6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="174f6-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="174f6-110">Child Elements</span></span>

<span data-ttu-id="174f6-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="174f6-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="174f6-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="174f6-112">Parent Elements</span></span>

|<span data-ttu-id="174f6-113">Élément</span><span class="sxs-lookup"><span data-stu-id="174f6-113">Element</span></span>|<span data-ttu-id="174f6-114">Description</span><span class="sxs-lookup"><span data-stu-id="174f6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="174f6-115">Élément EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="174f6-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="174f6-116">Définit les objets de collection .NET qui sont développées par cette définition.</span><span class="sxs-lookup"><span data-stu-id="174f6-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="174f6-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="174f6-117">Text Value</span></span>

<span data-ttu-id="174f6-118">Spécifiez le nom de l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="174f6-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="174f6-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="174f6-119">Remarks</span></span>

<span data-ttu-id="174f6-120">Chaque définition doit spécifier un ou plusieurs noms de type, un jeu de sélection ou une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="174f6-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="174f6-121">Sélection jeux sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="174f6-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="174f6-122">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="174f6-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="174f6-123">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition définit des objets pour une vue](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="174f6-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="174f6-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="174f6-124">See Also</span></span>

[<span data-ttu-id="174f6-125">Définition de jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="174f6-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="174f6-126">Élément EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="174f6-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="174f6-127">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="174f6-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
