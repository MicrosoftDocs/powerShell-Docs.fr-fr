---
title: Élément EntrySelectedBy pour TableRowEntry pour table ((format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363338"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="6d931-102">EntrySelectedBy, élément pour TableRowEntry pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6d931-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="6d931-103">Définit les types .NET qui utilisent cette définition de la vue table ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="6d931-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="6d931-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry, élément (format) EntrySelectedBy, élément (format)</span><span class="sxs-lookup"><span data-stu-id="6d931-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6d931-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d931-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6d931-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="6d931-106">Attributes and Elements</span></span>

<span data-ttu-id="6d931-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="6d931-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6d931-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="6d931-108">Attributes</span></span>

<span data-ttu-id="6d931-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="6d931-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6d931-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6d931-110">Child Elements</span></span>

|<span data-ttu-id="6d931-111">Élément</span><span class="sxs-lookup"><span data-stu-id="6d931-111">Element</span></span>|<span data-ttu-id="6d931-112">Description</span><span class="sxs-lookup"><span data-stu-id="6d931-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d931-113">Élément SelectionCondition pour EntrySelectedBy pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="6d931-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="6d931-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6d931-114">Optional element.</span></span><br /><br /> <span data-ttu-id="6d931-115">Définit la condition qui doit exister pour que cette définition de vue de table soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="6d931-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="6d931-116">Élément SelectionSetName pour EntrySelectedBy pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="6d931-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="6d931-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6d931-117">Optional element.</span></span><br /><br /> <span data-ttu-id="6d931-118">Spécifie un ensemble de types .NET qui utilisent cette définition de vue de table.</span><span class="sxs-lookup"><span data-stu-id="6d931-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="6d931-119">Élément TypeName pour EntrySelectedBy pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="6d931-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="6d931-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6d931-120">Optional element.</span></span><br /><br /> <span data-ttu-id="6d931-121">Spécifie un type .NET qui utilise cette définition de vue de table.</span><span class="sxs-lookup"><span data-stu-id="6d931-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6d931-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6d931-122">Parent Elements</span></span>

|<span data-ttu-id="6d931-123">Élément</span><span class="sxs-lookup"><span data-stu-id="6d931-123">Element</span></span>|<span data-ttu-id="6d931-124">Description</span><span class="sxs-lookup"><span data-stu-id="6d931-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d931-125">Élément TableRowEntry pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="6d931-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="6d931-126">Définit les données affichées dans une ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="6d931-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6d931-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="6d931-127">Remarks</span></span>

<span data-ttu-id="6d931-128">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition d’affichage de table.</span><span class="sxs-lookup"><span data-stu-id="6d931-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="6d931-129">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="6d931-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="6d931-130">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou un script spécifique prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="6d931-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="6d931-131">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6d931-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="6d931-132">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="6d931-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6d931-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d931-133">Example</span></span>

<span data-ttu-id="6d931-134">L’exemple suivant montre un élément `TableRowEntry` utilisé pour afficher les propriétés de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="6d931-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6d931-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d931-135">See Also</span></span>

[<span data-ttu-id="6d931-136">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="6d931-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6d931-137">Élément SelectionCondition pour EntrySelectedBy pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="6d931-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="6d931-138">Élément SelectionSetName pour EntrySelectedBy pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="6d931-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="6d931-139">Élément TableRowEntry pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="6d931-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="6d931-140">Élément TypeName pour EntrySelectedBy pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="6d931-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="6d931-141">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="6d931-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
