---
title: Élément EntrySelectedBy pour ListEntry pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363828"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="38b6a-102">EntrySelectedBy, élément pour ListEntry pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="38b6a-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="38b6a-103">Définit les types .NET qui utilisent cette définition de vue de liste ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="38b6a-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="38b6a-104">Dans la plupart des cas, une seule définition est nécessaire pour une vue liste.</span><span class="sxs-lookup"><span data-stu-id="38b6a-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="38b6a-105">Toutefois, vous pouvez fournir plusieurs définitions pour le mode liste si vous souhaitez utiliser la même vue de liste pour afficher des données différentes pour différents objets.</span><span class="sxs-lookup"><span data-stu-id="38b6a-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="38b6a-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément pour ListEntry pour ListControl (format) EntrySelectedBy, élément de ListEntry pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="38b6a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="38b6a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38b6a-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="38b6a-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="38b6a-108">Attributes and Elements</span></span>

<span data-ttu-id="38b6a-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="38b6a-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="38b6a-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="38b6a-110">Attributes</span></span>

<span data-ttu-id="38b6a-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="38b6a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="38b6a-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="38b6a-112">Child Elements</span></span>

|<span data-ttu-id="38b6a-113">Élément</span><span class="sxs-lookup"><span data-stu-id="38b6a-113">Element</span></span>|<span data-ttu-id="38b6a-114">Description</span><span class="sxs-lookup"><span data-stu-id="38b6a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38b6a-115">Élément SelectionCondition pour EntrySelectedBy pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="38b6a-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="38b6a-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="38b6a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="38b6a-117">Définit la condition qui doit exister pour que cette définition de vue de liste soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="38b6a-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="38b6a-118">Élément SelectionSetName pour EntrySelectedBy pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="38b6a-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="38b6a-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="38b6a-119">Optional element.</span></span><br /><br /> <span data-ttu-id="38b6a-120">Spécifie un ensemble de types .NET qui utilisent cette définition de vue liste.</span><span class="sxs-lookup"><span data-stu-id="38b6a-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="38b6a-121">Élément TypeName pour EntrySelectedBy pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="38b6a-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="38b6a-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="38b6a-122">Optional element.</span></span><br /><br /> <span data-ttu-id="38b6a-123">Spécifie un type .NET qui utilise cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="38b6a-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="38b6a-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="38b6a-124">Parent Elements</span></span>

|<span data-ttu-id="38b6a-125">Élément</span><span class="sxs-lookup"><span data-stu-id="38b6a-125">Element</span></span>|<span data-ttu-id="38b6a-126">Description</span><span class="sxs-lookup"><span data-stu-id="38b6a-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38b6a-127">Élément ListEntry pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="38b6a-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="38b6a-128">Définit le mode d’affichage des lignes de la liste.</span><span class="sxs-lookup"><span data-stu-id="38b6a-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="38b6a-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="38b6a-129">Remarks</span></span>

<span data-ttu-id="38b6a-130">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition de vue de liste.</span><span class="sxs-lookup"><span data-stu-id="38b6a-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="38b6a-131">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="38b6a-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="38b6a-132">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou un script spécifique prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="38b6a-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="38b6a-133">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="38b6a-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="38b6a-134">Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="38b6a-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="38b6a-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="38b6a-135">Example</span></span>

<span data-ttu-id="38b6a-136">L’exemple suivant montre comment définir les objets pour une vue liste à l’aide de leur nom de type .NET.</span><span class="sxs-lookup"><span data-stu-id="38b6a-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="38b6a-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38b6a-137">See Also</span></span>

[<span data-ttu-id="38b6a-138">Élément ListEntry pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="38b6a-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="38b6a-139">Élément SelectionCondition pour EntrySelectedBy pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="38b6a-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="38b6a-140">Élément SelectionSetName pour EntrySelectedBy pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="38b6a-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="38b6a-141">Élément TypeName pour EntrySelectedBy pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="38b6a-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="38b6a-142">Création d’un affichage de liste</span><span class="sxs-lookup"><span data-stu-id="38b6a-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="38b6a-143">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="38b6a-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="38b6a-144">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="38b6a-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
