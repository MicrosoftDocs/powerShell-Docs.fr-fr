---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy, élément pour TableRowEntry pour TableControl (Format)
description: EntrySelectedBy, élément pour TableRowEntry pour TableControl (Format)
ms.openlocfilehash: 1b7fc60b6fa9864b66e9edfebb3e4a86e287f3f8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645891"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="0f68f-103">EntrySelectedBy, élément pour TableRowEntry pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0f68f-103">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="0f68f-104">Définit les types .NET qui utilisent cette définition de la vue table ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="0f68f-104">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="0f68f-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry, élément (format) EntrySelectedBy, élément (format)</span><span class="sxs-lookup"><span data-stu-id="0f68f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0f68f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f68f-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0f68f-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0f68f-107">Attributes and Elements</span></span>

<span data-ttu-id="0f68f-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="0f68f-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0f68f-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="0f68f-109">Attributes</span></span>

<span data-ttu-id="0f68f-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0f68f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0f68f-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0f68f-111">Child Elements</span></span>

|<span data-ttu-id="0f68f-112">Élément</span><span class="sxs-lookup"><span data-stu-id="0f68f-112">Element</span></span>|<span data-ttu-id="0f68f-113">Description</span><span class="sxs-lookup"><span data-stu-id="0f68f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f68f-114">SelectionCondition, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0f68f-114">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="0f68f-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0f68f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0f68f-116">Définit la condition qui doit exister pour que cette définition de vue de table soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="0f68f-116">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="0f68f-117">SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0f68f-117">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="0f68f-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0f68f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0f68f-119">Spécifie un ensemble de types .NET qui utilisent cette définition de vue de table.</span><span class="sxs-lookup"><span data-stu-id="0f68f-119">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="0f68f-120">TypeName, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0f68f-120">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="0f68f-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0f68f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="0f68f-122">Spécifie un type .NET qui utilise cette définition de vue de table.</span><span class="sxs-lookup"><span data-stu-id="0f68f-122">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0f68f-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0f68f-123">Parent Elements</span></span>

|<span data-ttu-id="0f68f-124">Élément</span><span class="sxs-lookup"><span data-stu-id="0f68f-124">Element</span></span>|<span data-ttu-id="0f68f-125">Description</span><span class="sxs-lookup"><span data-stu-id="0f68f-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f68f-126">Élément TableRowEntry pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="0f68f-126">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="0f68f-127">Définit les données affichées dans une ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="0f68f-127">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0f68f-128">Notes</span><span class="sxs-lookup"><span data-stu-id="0f68f-128">Remarks</span></span>

<span data-ttu-id="0f68f-129">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition d’affichage de table.</span><span class="sxs-lookup"><span data-stu-id="0f68f-129">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="0f68f-130">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="0f68f-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="0f68f-131">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou un script spécifique prend la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="0f68f-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="0f68f-132">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0f68f-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="0f68f-133">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="0f68f-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0f68f-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="0f68f-134">Example</span></span>

<span data-ttu-id="0f68f-135">L’exemple suivant montre un `TableRowEntry` élément qui est utilisé pour afficher les propriétés de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="0f68f-135">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="0f68f-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f68f-136">See Also</span></span>

[<span data-ttu-id="0f68f-137">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="0f68f-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0f68f-138">SelectionCondition, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0f68f-138">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="0f68f-139">SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0f68f-139">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="0f68f-140">Élément TableRowEntry pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="0f68f-140">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="0f68f-141">TypeName, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0f68f-141">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="0f68f-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f68f-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
