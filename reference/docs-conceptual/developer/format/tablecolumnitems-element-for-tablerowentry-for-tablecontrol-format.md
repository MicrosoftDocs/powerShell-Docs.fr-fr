---
ms.date: 09/13/2016
ms.topic: reference
title: TableColumnItems, élément pour TableRowEntry pour TableControl (Format)
description: TableColumnItems, élément pour TableRowEntry pour TableControl (Format)
ms.openlocfilehash: 4d600a366d2be1c453f05b301bdf575351dd51c1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667757"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="07f1f-103">TableColumnItems, élément pour TableRowEntry pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="07f1f-103">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="07f1f-104">Définit les propriétés ou les scripts dont les valeurs sont affichées dans une ligne.</span><span class="sxs-lookup"><span data-stu-id="07f1f-104">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="07f1f-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableRowEntries pour table ((format) élément TableRowEntry pour TableRowEntries pour table ((format) TableColumnItems élément pour TableControlEntry (format)</span><span class="sxs-lookup"><span data-stu-id="07f1f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="07f1f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07f1f-106">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="07f1f-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="07f1f-107">Attributes and Elements</span></span>

<span data-ttu-id="07f1f-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableColumnItems` élément.</span><span class="sxs-lookup"><span data-stu-id="07f1f-108">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="07f1f-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="07f1f-109">Attributes</span></span>

<span data-ttu-id="07f1f-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="07f1f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="07f1f-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="07f1f-111">Child Elements</span></span>

|<span data-ttu-id="07f1f-112">Élément</span><span class="sxs-lookup"><span data-stu-id="07f1f-112">Element</span></span>|<span data-ttu-id="07f1f-113">Description</span><span class="sxs-lookup"><span data-stu-id="07f1f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07f1f-114">TableColumnItem, élément pour TableColumnItems pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="07f1f-114">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="07f1f-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="07f1f-115">Required element.</span></span><br /><br /> <span data-ttu-id="07f1f-116">Définit la propriété ou le script dont la valeur est affichée dans une colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="07f1f-116">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="07f1f-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="07f1f-117">Parent Elements</span></span>

|<span data-ttu-id="07f1f-118">Élément</span><span class="sxs-lookup"><span data-stu-id="07f1f-118">Element</span></span>|<span data-ttu-id="07f1f-119">Description</span><span class="sxs-lookup"><span data-stu-id="07f1f-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07f1f-120">TableRowEntry, élément pour TableRowEntries pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="07f1f-120">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="07f1f-121">Définit les données affichées dans une ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="07f1f-121">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="07f1f-122">Notes</span><span class="sxs-lookup"><span data-stu-id="07f1f-122">Remarks</span></span>

<span data-ttu-id="07f1f-123">Un `TableColumnItem` élément est requis pour chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="07f1f-123">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="07f1f-124">La première entrée est affichée dans la première colonne, la deuxième entrée de la deuxième colonne, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="07f1f-124">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="07f1f-125">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="07f1f-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="07f1f-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="07f1f-126">Example</span></span>

<span data-ttu-id="07f1f-127">L’exemple suivant montre un `TableColumnItems` élément qui définit trois propriétés de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="07f1f-127">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a><span data-ttu-id="07f1f-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07f1f-128">See Also</span></span>

[<span data-ttu-id="07f1f-129">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="07f1f-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="07f1f-130">Élément TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="07f1f-130">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="07f1f-131">Élément TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="07f1f-131">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="07f1f-132">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="07f1f-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
