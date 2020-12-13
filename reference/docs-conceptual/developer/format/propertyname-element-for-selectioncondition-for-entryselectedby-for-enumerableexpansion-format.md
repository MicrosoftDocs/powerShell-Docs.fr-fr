---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)
description: PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)
ms.openlocfilehash: 8e28118894661b50e90a5ccc86a36fbbe77e4b03
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665836"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="cd275-103">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="cd275-103">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="cd275-104">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="cd275-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="cd275-105">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="cd275-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="cd275-106">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) élément EntrySelectedBy pour EnumerableExpansion (format) élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) NomPropriété, élément pour SelectionCondition pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="cd275-106">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cd275-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd275-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cd275-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cd275-108">Attributes and Elements</span></span>

<span data-ttu-id="cd275-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="cd275-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cd275-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="cd275-110">Attributes</span></span>

<span data-ttu-id="cd275-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cd275-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cd275-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cd275-112">Child Elements</span></span>

<span data-ttu-id="cd275-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cd275-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cd275-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cd275-114">Parent Elements</span></span>

|<span data-ttu-id="cd275-115">Élément</span><span class="sxs-lookup"><span data-stu-id="cd275-115">Element</span></span>|<span data-ttu-id="cd275-116">Description</span><span class="sxs-lookup"><span data-stu-id="cd275-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cd275-117">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="cd275-117">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="cd275-118">Définit la condition qui doit exister pour développer les objets de collection de cette définition.</span><span class="sxs-lookup"><span data-stu-id="cd275-118">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cd275-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="cd275-119">Text Value</span></span>

<span data-ttu-id="cd275-120">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="cd275-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="cd275-121">Notes</span><span class="sxs-lookup"><span data-stu-id="cd275-121">Remarks</span></span>

<span data-ttu-id="cd275-122">La condition de sélection doit spécifier au moins un nom de propriété ou un script à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="cd275-122">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="cd275-123">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="cd275-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cd275-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd275-124">See Also</span></span>

[<span data-ttu-id="cd275-125">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="cd275-125">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="cd275-126">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="cd275-126">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="cd275-127">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="cd275-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="cd275-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd275-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
