---
title: Élément TableColumnItems pour TableRowEntry pour table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 661b938e8db0e68e10dc05f552e4f3a14608bc55
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785147"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="34336-102">TableColumnItems, élément pour TableRowEntry pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="34336-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="34336-103">Définit les propriétés ou les scripts dont les valeurs sont affichées dans une ligne.</span><span class="sxs-lookup"><span data-stu-id="34336-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="34336-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableRowEntries pour table ((format) élément TableRowEntry pour TableRowEntries pour table ((format) TableColumnItems élément pour TableControlEntry (format)</span><span class="sxs-lookup"><span data-stu-id="34336-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="34336-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34336-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34336-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="34336-106">Attributes and Elements</span></span>

<span data-ttu-id="34336-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableColumnItems` élément.</span><span class="sxs-lookup"><span data-stu-id="34336-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="34336-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="34336-108">Attributes</span></span>

<span data-ttu-id="34336-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="34336-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="34336-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="34336-110">Child Elements</span></span>

|<span data-ttu-id="34336-111">Élément</span><span class="sxs-lookup"><span data-stu-id="34336-111">Element</span></span>|<span data-ttu-id="34336-112">Description</span><span class="sxs-lookup"><span data-stu-id="34336-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34336-113">TableColumnItem, élément pour TableColumnItems pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="34336-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="34336-114">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="34336-114">Required element.</span></span><br /><br /> <span data-ttu-id="34336-115">Définit la propriété ou le script dont la valeur est affichée dans une colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="34336-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="34336-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="34336-116">Parent Elements</span></span>

|<span data-ttu-id="34336-117">Élément</span><span class="sxs-lookup"><span data-stu-id="34336-117">Element</span></span>|<span data-ttu-id="34336-118">Description</span><span class="sxs-lookup"><span data-stu-id="34336-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34336-119">TableRowEntry, élément pour TableRowEntries pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="34336-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="34336-120">Définit les données affichées dans une ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="34336-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="34336-121">Notes</span><span class="sxs-lookup"><span data-stu-id="34336-121">Remarks</span></span>

<span data-ttu-id="34336-122">Un `TableColumnItem` élément est requis pour chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="34336-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="34336-123">La première entrée est affichée dans la première colonne, la deuxième entrée de la deuxième colonne, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="34336-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="34336-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="34336-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="34336-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="34336-125">Example</span></span>

<span data-ttu-id="34336-126">L’exemple suivant montre un `TableColumnItems` élément qui définit trois propriétés de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="34336-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="34336-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34336-127">See Also</span></span>

[<span data-ttu-id="34336-128">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="34336-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="34336-129">Élément TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="34336-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="34336-130">Élément TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="34336-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="34336-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="34336-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
