---
title: Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 44c88ce75ae485e1c48ceb08bfd12f739a632996
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787442"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="222ec-102">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="222ec-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="222ec-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="222ec-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="222ec-104">Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de cette définition de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="222ec-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="222ec-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) élément SelectionCondition pour EntrySelectedBy (format) WideEntry élément pour SelectionSetName pour SelectionCondition (format)</span><span class="sxs-lookup"><span data-stu-id="222ec-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="222ec-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="222ec-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="222ec-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="222ec-107">Attributes and Elements</span></span>

<span data-ttu-id="222ec-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="222ec-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="222ec-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="222ec-109">Attributes</span></span>

<span data-ttu-id="222ec-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="222ec-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="222ec-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="222ec-111">Child Elements</span></span>

<span data-ttu-id="222ec-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="222ec-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="222ec-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="222ec-113">Parent Elements</span></span>

|<span data-ttu-id="222ec-114">Élément</span><span class="sxs-lookup"><span data-stu-id="222ec-114">Element</span></span>|<span data-ttu-id="222ec-115">Description</span><span class="sxs-lookup"><span data-stu-id="222ec-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="222ec-116">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="222ec-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="222ec-117">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="222ec-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="222ec-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="222ec-118">Text Value</span></span>

<span data-ttu-id="222ec-119">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="222ec-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="222ec-120">Notes</span><span class="sxs-lookup"><span data-stu-id="222ec-120">Remarks</span></span>

<span data-ttu-id="222ec-121">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="222ec-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="222ec-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="222ec-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="222ec-123">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="222ec-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="222ec-124">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="222ec-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="222ec-125">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="222ec-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="222ec-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="222ec-126">See Also</span></span>

[<span data-ttu-id="222ec-127">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="222ec-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="222ec-128">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="222ec-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="222ec-129">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="222ec-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="222ec-130">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="222ec-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="222ec-131">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="222ec-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="222ec-132">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="222ec-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
