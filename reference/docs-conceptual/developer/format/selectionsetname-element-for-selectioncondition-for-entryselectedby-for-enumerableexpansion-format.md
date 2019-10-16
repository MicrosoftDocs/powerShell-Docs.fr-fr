---
title: Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361988"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="1f787-102">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="1f787-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="1f787-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="1f787-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="1f787-104">Quand l’un des types de cet ensemble est présent, la condition est remplie.</span><span class="sxs-lookup"><span data-stu-id="1f787-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="1f787-105">Élément de configuration élément DefaultSettings (format) élément EnumerableExpansions (format) élément EnumerableExpansions (format) élément EntrySelectedBy pour EnumerableExpansion (format) élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) SelectionSetName, élément de SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="1f787-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f787-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f787-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f787-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="1f787-107">Attributes and Elements</span></span>

<span data-ttu-id="1f787-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="1f787-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f787-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="1f787-109">Attributes</span></span>

<span data-ttu-id="1f787-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="1f787-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f787-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1f787-111">Child Elements</span></span>

<span data-ttu-id="1f787-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="1f787-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1f787-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1f787-113">Parent Elements</span></span>

|<span data-ttu-id="1f787-114">Élément</span><span class="sxs-lookup"><span data-stu-id="1f787-114">Element</span></span>|<span data-ttu-id="1f787-115">Description</span><span class="sxs-lookup"><span data-stu-id="1f787-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f787-116">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="1f787-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="1f787-117">Définit la condition qui doit exister pour développer les objets de collection de cette définition.</span><span class="sxs-lookup"><span data-stu-id="1f787-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1f787-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="1f787-118">Text Value</span></span>

<span data-ttu-id="1f787-119">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="1f787-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f787-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="1f787-120">Remarks</span></span>

<span data-ttu-id="1f787-121">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="1f787-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="1f787-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1f787-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1f787-123">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="1f787-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="1f787-124">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1f787-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f787-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f787-125">See Also</span></span>

[<span data-ttu-id="1f787-126">Définition des jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="1f787-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="1f787-127">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="1f787-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="1f787-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f787-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
