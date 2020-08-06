---
title: Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour ListEntry (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3666888f149f176126d9a19bdbad62469ca9f064
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787476"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="48831-102">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="48831-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="48831-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="48831-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="48831-104">Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="48831-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="48831-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionCondition pour EntrySelectedBy pour ListEntry (format) SelectionSetName élément pour SelectionCondition pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="48831-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="48831-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48831-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="48831-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="48831-107">Attributes and Elements</span></span>

<span data-ttu-id="48831-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="48831-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="48831-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="48831-109">Attributes</span></span>

<span data-ttu-id="48831-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="48831-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="48831-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="48831-111">Child Elements</span></span>

<span data-ttu-id="48831-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="48831-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="48831-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="48831-113">Parent Elements</span></span>

|<span data-ttu-id="48831-114">Élément</span><span class="sxs-lookup"><span data-stu-id="48831-114">Element</span></span>|<span data-ttu-id="48831-115">Description</span><span class="sxs-lookup"><span data-stu-id="48831-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48831-116">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="48831-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="48831-117">Définit la condition qui doit exister pour utiliser cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="48831-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="48831-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="48831-118">Text Value</span></span>

<span data-ttu-id="48831-119">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="48831-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="48831-120">Notes</span><span class="sxs-lookup"><span data-stu-id="48831-120">Remarks</span></span>

<span data-ttu-id="48831-121">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="48831-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="48831-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="48831-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="48831-123">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="48831-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="48831-124">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="48831-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="48831-125">Pour plus d’informations sur les autres composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="48831-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="48831-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48831-126">See Also</span></span>

[<span data-ttu-id="48831-127">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="48831-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="48831-128">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="48831-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="48831-129">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="48831-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="48831-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="48831-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
