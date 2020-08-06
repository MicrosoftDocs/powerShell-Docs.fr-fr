---
title: Élément EntrySelectedBy pour ListEntry pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d6ab1c08dd353da74d1a7d27c569d2fa86e083c3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774114"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="e5eb5-102">EntrySelectedBy, élément pour ListEntry pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e5eb5-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="e5eb5-103">Définit les types .NET qui utilisent cette définition de vue de liste ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="e5eb5-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="e5eb5-104">Dans la plupart des cas, une seule définition est nécessaire pour une vue liste.</span><span class="sxs-lookup"><span data-stu-id="e5eb5-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="e5eb5-105">Toutefois, vous pouvez fournir plusieurs définitions pour le mode liste si vous souhaitez utiliser la même vue de liste pour afficher des données différentes pour différents objets.</span><span class="sxs-lookup"><span data-stu-id="e5eb5-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="e5eb5-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément pour ListEntry pour ListControl (format) EntrySelectedBy, élément pour ListEntry pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="e5eb5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5eb5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5eb5-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5eb5-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e5eb5-108">Attributes and Elements</span></span>

<span data-ttu-id="e5eb5-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="e5eb5-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5eb5-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="e5eb5-110">Attributes</span></span>

<span data-ttu-id="e5eb5-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e5eb5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5eb5-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e5eb5-112">Child Elements</span></span>

|<span data-ttu-id="e5eb5-113">Élément</span><span class="sxs-lookup"><span data-stu-id="e5eb5-113">Element</span></span>|<span data-ttu-id="e5eb5-114">Description</span><span class="sxs-lookup"><span data-stu-id="e5eb5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5eb5-115">Élément SelectionCondition pour EntrySelectedBy pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="e5eb5-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="e5eb5-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e5eb5-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e5eb5-117">Définit la condition qui doit exister pour que cette définition de vue de liste soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="e5eb5-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="e5eb5-118">SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e5eb5-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="e5eb5-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e5eb5-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e5eb5-120">Spécifie un ensemble de types .NET qui utilisent cette définition de vue liste.</span><span class="sxs-lookup"><span data-stu-id="e5eb5-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="e5eb5-121">TypeName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e5eb5-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="e5eb5-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e5eb5-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e5eb5-123">Spécifie un type .NET qui utilise cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="e5eb5-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5eb5-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e5eb5-124">Parent Elements</span></span>

|<span data-ttu-id="e5eb5-125">Élément</span><span class="sxs-lookup"><span data-stu-id="e5eb5-125">Element</span></span>|<span data-ttu-id="e5eb5-126">Description</span><span class="sxs-lookup"><span data-stu-id="e5eb5-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5eb5-127">ListEntry, élément pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e5eb5-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="e5eb5-128">Définit le mode d’affichage des lignes de la liste.</span><span class="sxs-lookup"><span data-stu-id="e5eb5-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5eb5-129">Notes</span><span class="sxs-lookup"><span data-stu-id="e5eb5-129">Remarks</span></span>

<span data-ttu-id="e5eb5-130">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition de vue de liste.</span><span class="sxs-lookup"><span data-stu-id="e5eb5-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="e5eb5-131">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="e5eb5-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="e5eb5-132">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou un script spécifique prend la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="e5eb5-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="e5eb5-133">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e5eb5-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e5eb5-134">Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e5eb5-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e5eb5-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="e5eb5-135">Example</span></span>

<span data-ttu-id="e5eb5-136">L’exemple suivant montre comment définir les objets pour une vue liste à l’aide de leur nom de type .NET.</span><span class="sxs-lookup"><span data-stu-id="e5eb5-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="e5eb5-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5eb5-137">See Also</span></span>

[<span data-ttu-id="e5eb5-138">ListEntry, élément pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e5eb5-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="e5eb5-139">SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e5eb5-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="e5eb5-140">SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e5eb5-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="e5eb5-141">TypeName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e5eb5-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="e5eb5-142">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="e5eb5-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e5eb5-143">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="e5eb5-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e5eb5-144">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5eb5-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
