---
title: Élément EntrySelectedBy pour ListEntry pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066190"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="94e0e-102">EntrySelectedBy, élément pour ListEntry pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="94e0e-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="94e0e-103">Définit les types .NET qui utilisent cette définition de la vue liste ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="94e0e-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="94e0e-104">Dans la plupart des cas qu’une seule définition est nécessaire pour un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="94e0e-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="94e0e-105">Toutefois, vous pouvez fournir plusieurs définitions pour l’affichage de liste si vous souhaitez utiliser la même vue de liste pour afficher des données différentes pour différents objets.</span><span class="sxs-lookup"><span data-stu-id="94e0e-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="94e0e-106">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément ListControl (Format) situés élément d’élément de ListEntry ListControl (Format) pour ListEntry d’élément de EntrySelectedBy ListControl (Format) pour ListEntry pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="94e0e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="94e0e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94e0e-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="94e0e-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="94e0e-108">Attributes and Elements</span></span>

<span data-ttu-id="94e0e-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="94e0e-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="94e0e-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="94e0e-110">Attributes</span></span>

<span data-ttu-id="94e0e-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="94e0e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="94e0e-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="94e0e-112">Child Elements</span></span>

|<span data-ttu-id="94e0e-113">Élément</span><span class="sxs-lookup"><span data-stu-id="94e0e-113">Element</span></span>|<span data-ttu-id="94e0e-114">Description</span><span class="sxs-lookup"><span data-stu-id="94e0e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94e0e-115">Élément SelectionCondition pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="94e0e-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="94e0e-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="94e0e-116">Optional element.</span></span><br /><br /> <span data-ttu-id="94e0e-117">Définit la condition qui doit exister pour cette définition de vue de liste à utiliser.</span><span class="sxs-lookup"><span data-stu-id="94e0e-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="94e0e-118">Élément SelectionSetName pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="94e0e-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="94e0e-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="94e0e-119">Optional element.</span></span><br /><br /> <span data-ttu-id="94e0e-120">Spécifie un ensemble de types .NET qui utilisent cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="94e0e-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="94e0e-121">Élément TypeName pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="94e0e-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="94e0e-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="94e0e-122">Optional element.</span></span><br /><br /> <span data-ttu-id="94e0e-123">Spécifie un type .NET qui utilise cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="94e0e-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="94e0e-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="94e0e-124">Parent Elements</span></span>

|<span data-ttu-id="94e0e-125">Élément</span><span class="sxs-lookup"><span data-stu-id="94e0e-125">Element</span></span>|<span data-ttu-id="94e0e-126">Description</span><span class="sxs-lookup"><span data-stu-id="94e0e-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94e0e-127">Élément ListEntry pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="94e0e-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="94e0e-128">Définit comment les lignes de la liste sont affichées.</span><span class="sxs-lookup"><span data-stu-id="94e0e-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="94e0e-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="94e0e-129">Remarks</span></span>

<span data-ttu-id="94e0e-130">Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour une définition de vue de liste.</span><span class="sxs-lookup"><span data-stu-id="94e0e-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="94e0e-131">Il n’existe aucune limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="94e0e-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="94e0e-132">Conditions de sélection permettent de définir une condition qui doit exister pour la définition à utiliser, par exemple quand un objet possède une propriété spécifique, ou qui a pour résultat une valeur de propriété spécifique ou un script `true`.</span><span class="sxs-lookup"><span data-stu-id="94e0e-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="94e0e-133">Pour plus d’informations sur les conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="94e0e-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="94e0e-134">Pour plus d’informations sur les composants d’une vue liste, consultez [création d’une vue liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="94e0e-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="94e0e-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="94e0e-135">Example</span></span>

<span data-ttu-id="94e0e-136">L’exemple suivant montre comment définir les objets pour un affichage de liste à l’aide de leur nom de type .NET.</span><span class="sxs-lookup"><span data-stu-id="94e0e-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="94e0e-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94e0e-137">See Also</span></span>

[<span data-ttu-id="94e0e-138">Élément ListEntry pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="94e0e-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="94e0e-139">Élément SelectionCondition pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="94e0e-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="94e0e-140">Élément SelectionSetName pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="94e0e-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="94e0e-141">Élément TypeName pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="94e0e-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="94e0e-142">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="94e0e-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="94e0e-143">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="94e0e-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="94e0e-144">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="94e0e-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
