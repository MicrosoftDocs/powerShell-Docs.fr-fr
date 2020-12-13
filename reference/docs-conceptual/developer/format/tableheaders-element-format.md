---
ms.date: 09/13/2016
ms.topic: reference
title: TableHeaders, élément (Format)
description: TableHeaders, élément (Format)
ms.openlocfilehash: 5ac4dccae746c167ebf95add9f3d18030a2b3a99
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659821"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="3184f-103">TableHeaders, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="3184f-103">TableHeaders Element (Format)</span></span>

<span data-ttu-id="3184f-104">Définit les en-têtes pour les colonnes d’une table.</span><span class="sxs-lookup"><span data-stu-id="3184f-104">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="3184f-105">Élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="3184f-105">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3184f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3184f-106">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="3184f-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3184f-107">Attributes and Elements</span></span>

<span data-ttu-id="3184f-108">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `TableHeaders` élément.</span><span class="sxs-lookup"><span data-stu-id="3184f-108">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="3184f-109">Il doit y avoir un élément enfant pour chaque propriété de l’objet qui doit être affiché.</span><span class="sxs-lookup"><span data-stu-id="3184f-109">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="3184f-110">Les informations d’en-tête de colonne s’affichent dans l’ordre dans lequel les éléments enfants sont spécifiés.</span><span class="sxs-lookup"><span data-stu-id="3184f-110">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="3184f-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="3184f-111">Attributes</span></span>

<span data-ttu-id="3184f-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3184f-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3184f-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3184f-113">Child Elements</span></span>

|<span data-ttu-id="3184f-114">Élément</span><span class="sxs-lookup"><span data-stu-id="3184f-114">Element</span></span>|<span data-ttu-id="3184f-115">Description</span><span class="sxs-lookup"><span data-stu-id="3184f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3184f-116">TableColumnHeader, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="3184f-116">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="3184f-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3184f-117">Optional element.</span></span><br /><br /> <span data-ttu-id="3184f-118">Définit l’étiquette, la largeur et l’alignement des données pour une colonne d’une vue de table.</span><span class="sxs-lookup"><span data-stu-id="3184f-118">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3184f-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3184f-119">Parent Elements</span></span>

|<span data-ttu-id="3184f-120">Élément</span><span class="sxs-lookup"><span data-stu-id="3184f-120">Element</span></span>|<span data-ttu-id="3184f-121">Description</span><span class="sxs-lookup"><span data-stu-id="3184f-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3184f-122">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="3184f-122">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="3184f-123">Définit un format de table pour une vue.</span><span class="sxs-lookup"><span data-stu-id="3184f-123">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3184f-124">Notes</span><span class="sxs-lookup"><span data-stu-id="3184f-124">Remarks</span></span>

<span data-ttu-id="3184f-125">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="3184f-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3184f-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="3184f-126">Example</span></span>

<span data-ttu-id="3184f-127">Cet exemple montre un `TableHeaders` élément qui définit deux en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="3184f-127">This example shows a `TableHeaders` element that defines two column headers.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="3184f-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3184f-128">See Also</span></span>

[<span data-ttu-id="3184f-129">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="3184f-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="3184f-130">TableColumnHeader, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="3184f-130">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="3184f-131">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="3184f-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="3184f-132">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="3184f-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
