---
title: Élément TableColumnItems pour TableRowEntry pour table ((format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361808"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="2ad55-102">TableColumnItems, élément pour TableRowEntry pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2ad55-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="2ad55-103">Définit les propriétés ou les scripts dont les valeurs sont affichées dans une ligne.</span><span class="sxs-lookup"><span data-stu-id="2ad55-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="2ad55-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableRowEntries pour table ((format) élément TableRowEntry pour TableRowEntries pour table ((format) Élément TableColumnItems pour TableControlEntry pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="2ad55-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ad55-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ad55-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2ad55-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="2ad55-106">Attributes and Elements</span></span>

<span data-ttu-id="2ad55-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TableColumnItems`.</span><span class="sxs-lookup"><span data-stu-id="2ad55-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2ad55-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="2ad55-108">Attributes</span></span>

<span data-ttu-id="2ad55-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="2ad55-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2ad55-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2ad55-110">Child Elements</span></span>

|<span data-ttu-id="2ad55-111">Élément</span><span class="sxs-lookup"><span data-stu-id="2ad55-111">Element</span></span>|<span data-ttu-id="2ad55-112">Description</span><span class="sxs-lookup"><span data-stu-id="2ad55-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ad55-113">Élément TableColumnItem pour TableColumnItems pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="2ad55-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="2ad55-114">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="2ad55-114">Required element.</span></span><br /><br /> <span data-ttu-id="2ad55-115">Définit la propriété ou le script dont la valeur est affichée dans une colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2ad55-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2ad55-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2ad55-116">Parent Elements</span></span>

|<span data-ttu-id="2ad55-117">Élément</span><span class="sxs-lookup"><span data-stu-id="2ad55-117">Element</span></span>|<span data-ttu-id="2ad55-118">Description</span><span class="sxs-lookup"><span data-stu-id="2ad55-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ad55-119">Élément TableRowEntry pour TableRowEntries pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="2ad55-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="2ad55-120">Définit les données affichées dans une ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="2ad55-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2ad55-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="2ad55-121">Remarks</span></span>

<span data-ttu-id="2ad55-122">Un élément `TableColumnItem` est requis pour chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2ad55-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="2ad55-123">La première entrée est affichée dans la première colonne, la deuxième entrée de la deuxième colonne, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="2ad55-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="2ad55-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="2ad55-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2ad55-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ad55-125">Example</span></span>

<span data-ttu-id="2ad55-126">L’exemple suivant montre un élément `TableColumnItems` qui définit trois propriétés de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="2ad55-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2ad55-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ad55-127">See Also</span></span>

[<span data-ttu-id="2ad55-128">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="2ad55-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2ad55-129">Élément TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="2ad55-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="2ad55-130">Élément TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="2ad55-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="2ad55-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="2ad55-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
