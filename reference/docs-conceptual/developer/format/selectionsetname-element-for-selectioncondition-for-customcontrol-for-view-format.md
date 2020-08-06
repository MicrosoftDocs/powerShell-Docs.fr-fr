---
title: Élément SelectionSetName pour SelectionCondition pour CustomControl pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c7fdd92475ba24d27e61371d1c6b54fa1a55647c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787510"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="9b810-102">SelectionSetName, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="9b810-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="9b810-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="9b810-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="9b810-104">Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="9b810-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="9b810-105">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9b810-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="9b810-106">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour l’élément View (format) EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="9b810-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9b810-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b810-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9b810-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9b810-108">Attributes and Elements</span></span>

<span data-ttu-id="9b810-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="9b810-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9b810-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="9b810-110">Attributes</span></span>

<span data-ttu-id="9b810-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9b810-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9b810-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9b810-112">Child Elements</span></span>

<span data-ttu-id="9b810-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9b810-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9b810-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9b810-114">Parent Elements</span></span>

|<span data-ttu-id="9b810-115">Élément</span><span class="sxs-lookup"><span data-stu-id="9b810-115">Element</span></span>|<span data-ttu-id="9b810-116">Description</span><span class="sxs-lookup"><span data-stu-id="9b810-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9b810-117">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="9b810-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="9b810-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="9b810-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9b810-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="9b810-119">Text Value</span></span>

<span data-ttu-id="9b810-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="9b810-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b810-121">Notes</span><span class="sxs-lookup"><span data-stu-id="9b810-121">Remarks</span></span>

<span data-ttu-id="9b810-122">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="9b810-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="9b810-123">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="9b810-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="9b810-124">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="9b810-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="9b810-125">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9b810-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9b810-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b810-126">See Also</span></span>

[<span data-ttu-id="9b810-127">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="9b810-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="9b810-128">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="9b810-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9b810-129">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="9b810-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="9b810-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="9b810-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
