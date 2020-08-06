---
title: Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e18c74bb95c658f2c3e7b7454628f78d523f7609
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787493"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="847e6-102">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="847e6-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="847e6-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="847e6-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="847e6-104">Quand l’un des types de cet ensemble est présent, la condition est remplie.</span><span class="sxs-lookup"><span data-stu-id="847e6-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="847e6-105">Élément de configuration élément DefaultSettings (format) élément EnumerableExpansions (format) élément EnumerableExpansions (format) élément EntrySelectedBy pour EnumerableExpansion (format) élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) SelectionSetName élément pour SelectionCondition pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="847e6-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="847e6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="847e6-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="847e6-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="847e6-107">Attributes and Elements</span></span>

<span data-ttu-id="847e6-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="847e6-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="847e6-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="847e6-109">Attributes</span></span>

<span data-ttu-id="847e6-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="847e6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="847e6-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="847e6-111">Child Elements</span></span>

<span data-ttu-id="847e6-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="847e6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="847e6-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="847e6-113">Parent Elements</span></span>

|<span data-ttu-id="847e6-114">Élément</span><span class="sxs-lookup"><span data-stu-id="847e6-114">Element</span></span>|<span data-ttu-id="847e6-115">Description</span><span class="sxs-lookup"><span data-stu-id="847e6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="847e6-116">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="847e6-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="847e6-117">Définit la condition qui doit exister pour développer les objets de collection de cette définition.</span><span class="sxs-lookup"><span data-stu-id="847e6-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="847e6-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="847e6-118">Text Value</span></span>

<span data-ttu-id="847e6-119">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="847e6-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="847e6-120">Notes</span><span class="sxs-lookup"><span data-stu-id="847e6-120">Remarks</span></span>

<span data-ttu-id="847e6-121">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="847e6-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="847e6-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="847e6-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="847e6-123">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="847e6-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="847e6-124">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="847e6-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="847e6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="847e6-125">See Also</span></span>

[<span data-ttu-id="847e6-126">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="847e6-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="847e6-127">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="847e6-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="847e6-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="847e6-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
