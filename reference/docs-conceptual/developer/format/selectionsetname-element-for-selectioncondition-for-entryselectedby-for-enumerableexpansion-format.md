---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)
description: SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)
ms.openlocfilehash: 0c9372113a79f75cfbda67acf869164fde894ee3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651589"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="89b8a-103">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="89b8a-103">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="89b8a-104">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="89b8a-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="89b8a-105">Quand l’un des types de cet ensemble est présent, la condition est remplie.</span><span class="sxs-lookup"><span data-stu-id="89b8a-105">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="89b8a-106">Élément de configuration élément DefaultSettings (format) élément EnumerableExpansions (format) élément EnumerableExpansions (format) élément EntrySelectedBy pour EnumerableExpansion (format) élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) SelectionSetName élément pour SelectionCondition pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="89b8a-106">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="89b8a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89b8a-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="89b8a-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="89b8a-108">Attributes and Elements</span></span>

<span data-ttu-id="89b8a-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="89b8a-109">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="89b8a-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="89b8a-110">Attributes</span></span>

<span data-ttu-id="89b8a-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="89b8a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="89b8a-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="89b8a-112">Child Elements</span></span>

<span data-ttu-id="89b8a-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="89b8a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="89b8a-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="89b8a-114">Parent Elements</span></span>

|<span data-ttu-id="89b8a-115">Élément</span><span class="sxs-lookup"><span data-stu-id="89b8a-115">Element</span></span>|<span data-ttu-id="89b8a-116">Description</span><span class="sxs-lookup"><span data-stu-id="89b8a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89b8a-117">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="89b8a-117">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="89b8a-118">Définit la condition qui doit exister pour développer les objets de collection de cette définition.</span><span class="sxs-lookup"><span data-stu-id="89b8a-118">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="89b8a-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="89b8a-119">Text Value</span></span>

<span data-ttu-id="89b8a-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="89b8a-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="89b8a-121">Notes</span><span class="sxs-lookup"><span data-stu-id="89b8a-121">Remarks</span></span>

<span data-ttu-id="89b8a-122">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="89b8a-122">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="89b8a-123">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="89b8a-123">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="89b8a-124">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="89b8a-124">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="89b8a-125">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="89b8a-125">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="89b8a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89b8a-126">See Also</span></span>

[<span data-ttu-id="89b8a-127">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="89b8a-127">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="89b8a-128">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="89b8a-128">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="89b8a-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="89b8a-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
