---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)
description: SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)
ms.openlocfilehash: b23ee5310d415cf287bf99c73b1173f70ae15f4c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651648"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="3ece6-103">SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3ece6-103">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="3ece6-104">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="3ece6-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="3ece6-105">Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="3ece6-105">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="3ece6-106">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="3ece6-106">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="3ece6-107">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour View (format) CustomEntries element pour CustomControl pour les contrôles pour View (format) élément CustomEntry pour CustomEntries pour les contrôles de l’élément View (format) EntrySelectedBy pour CustomEntry pour les contrôles pour l’élément View (format) SelectionCondition pour les contrôles de l’élément View (format) EntrySelectedBy pour SelectionSetName pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3ece6-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ece6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ece6-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ece6-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3ece6-109">Attributes and Elements</span></span>

<span data-ttu-id="3ece6-110">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="3ece6-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ece6-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="3ece6-111">Attributes</span></span>

<span data-ttu-id="3ece6-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3ece6-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ece6-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3ece6-113">Child Elements</span></span>

<span data-ttu-id="3ece6-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3ece6-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3ece6-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3ece6-115">Parent Elements</span></span>

|<span data-ttu-id="3ece6-116">Élément</span><span class="sxs-lookup"><span data-stu-id="3ece6-116">Element</span></span>|<span data-ttu-id="3ece6-117">Description</span><span class="sxs-lookup"><span data-stu-id="3ece6-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ece6-118">SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3ece6-118">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="3ece6-119">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="3ece6-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3ece6-120">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="3ece6-120">Text Value</span></span>

<span data-ttu-id="3ece6-121">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="3ece6-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ece6-122">Notes</span><span class="sxs-lookup"><span data-stu-id="3ece6-122">Remarks</span></span>

<span data-ttu-id="3ece6-123">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="3ece6-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="3ece6-124">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="3ece6-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="3ece6-125">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="3ece6-125">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="3ece6-126">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3ece6-126">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3ece6-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ece6-127">See Also</span></span>

[<span data-ttu-id="3ece6-128">SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3ece6-128">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="3ece6-129">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="3ece6-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3ece6-130">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="3ece6-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="3ece6-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ece6-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
