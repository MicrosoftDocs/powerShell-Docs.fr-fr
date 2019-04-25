---
title: Élément EntrySelectedBy pour TableRowEntry pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066156"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="b8674-102">EntrySelectedBy, élément pour TableRowEntry pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b8674-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="b8674-103">Définit les types .NET qui utilisent cette définition de la vue de la table ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b8674-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="b8674-104">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément de table (Format) élément TableRowEntries (Format) élément TableRowEntry (Format) EntrySelectedBy élément (Format)</span><span class="sxs-lookup"><span data-stu-id="b8674-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b8674-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8674-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b8674-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="b8674-106">Attributes and Elements</span></span>

<span data-ttu-id="b8674-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="b8674-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b8674-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="b8674-108">Attributes</span></span>

<span data-ttu-id="b8674-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="b8674-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b8674-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b8674-110">Child Elements</span></span>

|<span data-ttu-id="b8674-111">Élément</span><span class="sxs-lookup"><span data-stu-id="b8674-111">Element</span></span>|<span data-ttu-id="b8674-112">Description</span><span class="sxs-lookup"><span data-stu-id="b8674-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8674-113">Élément SelectionCondition pour EntrySelectedBy pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="b8674-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="b8674-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b8674-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b8674-115">Définit la condition qui doit exister pour cette définition de vue de table à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b8674-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="b8674-116">Élément SelectionSetName pour EntrySelectedBy pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="b8674-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="b8674-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b8674-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b8674-118">Spécifie un ensemble de types .NET qui utilisent cette définition de vue de table.</span><span class="sxs-lookup"><span data-stu-id="b8674-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="b8674-119">Élément TypeName pour EntrySelectedBy pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="b8674-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="b8674-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b8674-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b8674-121">Spécifie un type .NET qui utilise cette définition de vue de table.</span><span class="sxs-lookup"><span data-stu-id="b8674-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b8674-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b8674-122">Parent Elements</span></span>

|<span data-ttu-id="b8674-123">Élément</span><span class="sxs-lookup"><span data-stu-id="b8674-123">Element</span></span>|<span data-ttu-id="b8674-124">Description</span><span class="sxs-lookup"><span data-stu-id="b8674-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8674-125">Élément TableRowEntry pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="b8674-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="b8674-126">Définit les données qui s’affiche dans une ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="b8674-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b8674-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="b8674-127">Remarks</span></span>

<span data-ttu-id="b8674-128">Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour une définition de vue de table.</span><span class="sxs-lookup"><span data-stu-id="b8674-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="b8674-129">Il n’existe aucune limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="b8674-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="b8674-130">Conditions de sélection permettent de définir une condition qui doit exister pour la définition à utiliser, par exemple quand un objet possède une propriété spécifique, ou qui a pour résultat une valeur de propriété spécifique ou un script `true`.</span><span class="sxs-lookup"><span data-stu-id="b8674-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="b8674-131">Pour plus d’informations sur les conditions de sélection, consultez [définition Conditions pour lorsqu’une entrée de la vue ou d’élément est utilisé](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b8674-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b8674-132">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b8674-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b8674-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="b8674-133">Example</span></span>

<span data-ttu-id="b8674-134">L’exemple suivant montre un `TableRowEntry` élément qui est utilisé pour afficher les propriétés de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.</span><span class="sxs-lookup"><span data-stu-id="b8674-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b8674-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8674-135">See Also</span></span>

[<span data-ttu-id="b8674-136">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="b8674-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b8674-137">Élément SelectionCondition pour EntrySelectedBy pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="b8674-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b8674-138">Élément SelectionSetName pour EntrySelectedBy pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="b8674-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b8674-139">Élément TableRowEntry pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="b8674-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="b8674-140">Élément TypeName pour EntrySelectedBy pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="b8674-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b8674-141">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8674-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
