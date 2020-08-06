---
title: Élément SelectionSetName pour SelectionCondition pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0feb23f860487952344680f75ee674e9e0e6dcc6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787527"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="d0be1-102">SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d0be1-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="d0be1-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="d0be1-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="d0be1-104">Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="d0be1-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="d0be1-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="d0be1-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d0be1-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour View (format) CustomEntries element pour CustomControl pour les contrôles pour View (format) élément CustomEntry pour CustomEntries pour les contrôles de l’élément View (format) EntrySelectedBy pour CustomEntry pour les contrôles pour l’élément View (format) SelectionCondition pour les contrôles de l’élément View (format) EntrySelectedBy pour SelectionSetName pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="d0be1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d0be1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0be1-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0be1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d0be1-108">Attributes and Elements</span></span>

<span data-ttu-id="d0be1-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="d0be1-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0be1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="d0be1-110">Attributes</span></span>

<span data-ttu-id="d0be1-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d0be1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d0be1-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d0be1-112">Child Elements</span></span>

<span data-ttu-id="d0be1-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d0be1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d0be1-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d0be1-114">Parent Elements</span></span>

|<span data-ttu-id="d0be1-115">Élément</span><span class="sxs-lookup"><span data-stu-id="d0be1-115">Element</span></span>|<span data-ttu-id="d0be1-116">Description</span><span class="sxs-lookup"><span data-stu-id="d0be1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0be1-117">SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d0be1-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="d0be1-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="d0be1-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d0be1-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="d0be1-119">Text Value</span></span>

<span data-ttu-id="d0be1-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="d0be1-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0be1-121">Notes</span><span class="sxs-lookup"><span data-stu-id="d0be1-121">Remarks</span></span>

<span data-ttu-id="d0be1-122">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="d0be1-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="d0be1-123">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d0be1-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d0be1-124">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="d0be1-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="d0be1-125">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d0be1-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0be1-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0be1-126">See Also</span></span>

[<span data-ttu-id="d0be1-127">SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d0be1-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="d0be1-128">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="d0be1-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d0be1-129">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="d0be1-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d0be1-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0be1-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
