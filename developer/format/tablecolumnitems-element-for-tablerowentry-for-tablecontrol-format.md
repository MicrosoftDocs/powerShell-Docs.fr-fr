---
title: Élément TableColumnItems pour TableRowEntry pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: faa9ba78397e713400f6072df9915f20d966bb37
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859445"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="f8346-102">TableColumnItems, élément pour TableRowEntry pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f8346-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="f8346-103">Définit les propriétés ou les scripts dont les valeurs sont affichées dans une ligne.</span><span class="sxs-lookup"><span data-stu-id="f8346-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="f8346-104">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableRowEntries élément de configuration pour élément TableRowEntry de table (Format) pour TableRowEntries pour la table (Format) Élément TableColumnItems pour TableControlEntry pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="f8346-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f8346-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8346-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f8346-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="f8346-106">Attributes and Elements</span></span>

<span data-ttu-id="f8346-107">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `TableColumnItems` élément.</span><span class="sxs-lookup"><span data-stu-id="f8346-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f8346-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="f8346-108">Attributes</span></span>

<span data-ttu-id="f8346-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f8346-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f8346-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f8346-110">Child Elements</span></span>

|<span data-ttu-id="f8346-111">Élément</span><span class="sxs-lookup"><span data-stu-id="f8346-111">Element</span></span>|<span data-ttu-id="f8346-112">Description</span><span class="sxs-lookup"><span data-stu-id="f8346-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8346-113">Élément TableColumnItem pour TableColumnItems pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="f8346-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="f8346-114">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="f8346-114">Required element.</span></span><br /><br /> <span data-ttu-id="f8346-115">Définit la propriété ou un script dont la valeur est affichée dans une colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="f8346-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f8346-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f8346-116">Parent Elements</span></span>

|<span data-ttu-id="f8346-117">Élément</span><span class="sxs-lookup"><span data-stu-id="f8346-117">Element</span></span>|<span data-ttu-id="f8346-118">Description</span><span class="sxs-lookup"><span data-stu-id="f8346-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8346-119">Élément TableRowEntry pour TableRowEntries pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="f8346-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="f8346-120">Définit les données qui s’affiche dans une ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="f8346-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f8346-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="f8346-121">Remarks</span></span>

<span data-ttu-id="f8346-122">Un `TableColumnItem` élément est requis pour chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="f8346-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="f8346-123">La première entrée s’affiche dans la première colonne, la deuxième entrée dans la deuxième colonne et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="f8346-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="f8346-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f8346-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f8346-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="f8346-125">Example</span></span>

<span data-ttu-id="f8346-126">L’exemple suivant montre un `TableColumnItems` élément qui définit trois propriétés de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.</span><span class="sxs-lookup"><span data-stu-id="f8346-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f8346-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8346-127">See Also</span></span>

[<span data-ttu-id="f8346-128">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="f8346-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f8346-129">Élément TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="f8346-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="f8346-130">Élément TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f8346-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="f8346-131">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8346-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
