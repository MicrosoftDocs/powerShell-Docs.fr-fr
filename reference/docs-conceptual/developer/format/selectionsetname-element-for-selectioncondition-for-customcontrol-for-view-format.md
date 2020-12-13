---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour SelectionCondition pour CustomControl pour View (Format)
description: SelectionSetName, élément pour SelectionCondition pour CustomControl pour View (Format)
ms.openlocfilehash: 839032048739e529057d7066fb3bc6aa2fbc5037
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651607"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="68f41-103">SelectionSetName, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="68f41-103">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="68f41-104">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="68f41-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="68f41-105">Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="68f41-105">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="68f41-106">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="68f41-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="68f41-107">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour l’élément View (format) EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="68f41-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="68f41-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68f41-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="68f41-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="68f41-109">Attributes and Elements</span></span>

<span data-ttu-id="68f41-110">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="68f41-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="68f41-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="68f41-111">Attributes</span></span>

<span data-ttu-id="68f41-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="68f41-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="68f41-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="68f41-113">Child Elements</span></span>

<span data-ttu-id="68f41-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="68f41-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="68f41-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="68f41-115">Parent Elements</span></span>

|<span data-ttu-id="68f41-116">Élément</span><span class="sxs-lookup"><span data-stu-id="68f41-116">Element</span></span>|<span data-ttu-id="68f41-117">Description</span><span class="sxs-lookup"><span data-stu-id="68f41-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68f41-118">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="68f41-118">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="68f41-119">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="68f41-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="68f41-120">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="68f41-120">Text Value</span></span>

<span data-ttu-id="68f41-121">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="68f41-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="68f41-122">Notes</span><span class="sxs-lookup"><span data-stu-id="68f41-122">Remarks</span></span>

<span data-ttu-id="68f41-123">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="68f41-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="68f41-124">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="68f41-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="68f41-125">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="68f41-125">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="68f41-126">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="68f41-126">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="68f41-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68f41-127">See Also</span></span>

[<span data-ttu-id="68f41-128">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="68f41-128">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="68f41-129">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="68f41-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="68f41-130">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="68f41-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="68f41-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="68f41-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
