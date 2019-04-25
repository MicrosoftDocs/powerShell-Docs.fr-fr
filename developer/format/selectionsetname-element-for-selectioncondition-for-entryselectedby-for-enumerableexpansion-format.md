---
title: Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063858"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="5ca93-102">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="5ca93-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="5ca93-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="5ca93-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="5ca93-104">Quand les types dans cet ensemble sont présents, la condition est remplie.</span><span class="sxs-lookup"><span data-stu-id="5ca93-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="5ca93-105">Configuration élément DefaultSettings, élément (Format) élément EnumerableExpansions (Format) EnumerableExpansions (Format) EntrySelectedBy élément d’élément de SelectionCondition EnumerableExpansion (Format) pour EntrySelectedBy pour Élément de SelectionSetName EnumerableExpansion (Format) pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="5ca93-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ca93-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ca93-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ca93-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="5ca93-107">Attributes and Elements</span></span>

<span data-ttu-id="5ca93-108">Les sections suivantes décrivent des attributs, éléments enfants et élément parent de la `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="5ca93-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ca93-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="5ca93-109">Attributes</span></span>

<span data-ttu-id="5ca93-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5ca93-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ca93-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5ca93-111">Child Elements</span></span>

<span data-ttu-id="5ca93-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5ca93-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5ca93-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5ca93-113">Parent Elements</span></span>

|<span data-ttu-id="5ca93-114">Élément</span><span class="sxs-lookup"><span data-stu-id="5ca93-114">Element</span></span>|<span data-ttu-id="5ca93-115">Description</span><span class="sxs-lookup"><span data-stu-id="5ca93-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ca93-116">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="5ca93-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="5ca93-117">Définit la condition qui doit exister pour développer la collection d’objets de cette définition.</span><span class="sxs-lookup"><span data-stu-id="5ca93-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5ca93-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="5ca93-118">Text Value</span></span>

<span data-ttu-id="5ca93-119">Spécifiez le nom de l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="5ca93-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ca93-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="5ca93-120">Remarks</span></span>

<span data-ttu-id="5ca93-121">La condition de sélection peut spécifier un jeu de sélection ou d’un type .NET, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="5ca93-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="5ca93-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5ca93-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="5ca93-123">Les jeux de sélection sont courantes groupes d’objets .NET qui peuvent être utilisées par n’importe quelle vue qui définit le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="5ca93-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="5ca93-124">Pour plus d’informations sur la création et en faisant référence à des jeux de sélection, consultez [définition sélection définit](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="5ca93-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ca93-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ca93-125">See Also</span></span>

[<span data-ttu-id="5ca93-126">Définition de jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="5ca93-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="5ca93-127">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="5ca93-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="5ca93-128">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ca93-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
