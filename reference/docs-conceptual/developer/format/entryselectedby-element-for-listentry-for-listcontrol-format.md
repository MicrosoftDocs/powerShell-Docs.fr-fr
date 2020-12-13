---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy, élément pour ListEntry pour ListControl (Format)
description: EntrySelectedBy, élément pour ListEntry pour ListControl (Format)
ms.openlocfilehash: 1981c8fae65f494504d6cdd9f59337d555350b07
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652286"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="07360-103">EntrySelectedBy, élément pour ListEntry pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="07360-103">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="07360-104">Définit les types .NET qui utilisent cette définition de vue de liste ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="07360-104">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="07360-105">Dans la plupart des cas, une seule définition est nécessaire pour une vue liste.</span><span class="sxs-lookup"><span data-stu-id="07360-105">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="07360-106">Toutefois, vous pouvez fournir plusieurs définitions pour le mode liste si vous souhaitez utiliser la même vue de liste pour afficher des données différentes pour différents objets.</span><span class="sxs-lookup"><span data-stu-id="07360-106">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="07360-107">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément pour ListEntry pour ListControl (format) EntrySelectedBy, élément pour ListEntry pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="07360-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="07360-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07360-108">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="07360-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="07360-109">Attributes and Elements</span></span>

<span data-ttu-id="07360-110">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="07360-110">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="07360-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="07360-111">Attributes</span></span>

<span data-ttu-id="07360-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="07360-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="07360-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="07360-113">Child Elements</span></span>

|<span data-ttu-id="07360-114">Élément</span><span class="sxs-lookup"><span data-stu-id="07360-114">Element</span></span>|<span data-ttu-id="07360-115">Description</span><span class="sxs-lookup"><span data-stu-id="07360-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07360-116">Élément SelectionCondition pour EntrySelectedBy pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="07360-116">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="07360-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="07360-117">Optional element.</span></span><br /><br /> <span data-ttu-id="07360-118">Définit la condition qui doit exister pour que cette définition de vue de liste soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="07360-118">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="07360-119">SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="07360-119">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="07360-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="07360-120">Optional element.</span></span><br /><br /> <span data-ttu-id="07360-121">Spécifie un ensemble de types .NET qui utilisent cette définition de vue liste.</span><span class="sxs-lookup"><span data-stu-id="07360-121">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="07360-122">TypeName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="07360-122">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="07360-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="07360-123">Optional element.</span></span><br /><br /> <span data-ttu-id="07360-124">Spécifie un type .NET qui utilise cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="07360-124">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="07360-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="07360-125">Parent Elements</span></span>

|<span data-ttu-id="07360-126">Élément</span><span class="sxs-lookup"><span data-stu-id="07360-126">Element</span></span>|<span data-ttu-id="07360-127">Description</span><span class="sxs-lookup"><span data-stu-id="07360-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07360-128">ListEntry, élément pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="07360-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="07360-129">Définit le mode d’affichage des lignes de la liste.</span><span class="sxs-lookup"><span data-stu-id="07360-129">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="07360-130">Notes</span><span class="sxs-lookup"><span data-stu-id="07360-130">Remarks</span></span>

<span data-ttu-id="07360-131">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition de vue de liste.</span><span class="sxs-lookup"><span data-stu-id="07360-131">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="07360-132">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="07360-132">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="07360-133">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou un script spécifique prend la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="07360-133">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="07360-134">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="07360-134">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="07360-135">Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="07360-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="07360-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="07360-136">Example</span></span>

<span data-ttu-id="07360-137">L’exemple suivant montre comment définir les objets pour une vue liste à l’aide de leur nom de type .NET.</span><span class="sxs-lookup"><span data-stu-id="07360-137">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="07360-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07360-138">See Also</span></span>

[<span data-ttu-id="07360-139">ListEntry, élément pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="07360-139">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="07360-140">SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="07360-140">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="07360-141">SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="07360-141">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="07360-142">TypeName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="07360-142">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="07360-143">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="07360-143">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="07360-144">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="07360-144">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="07360-145">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="07360-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
