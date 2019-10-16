---
title: Élément TableHeaders (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361818"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="29f76-102">TableHeaders, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="29f76-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="29f76-103">Définit les en-têtes pour les colonnes d’une table.</span><span class="sxs-lookup"><span data-stu-id="29f76-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="29f76-104">Élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="29f76-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="29f76-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29f76-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="29f76-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="29f76-106">Attributes and Elements</span></span>

<span data-ttu-id="29f76-107">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l’élément `TableHeaders`.</span><span class="sxs-lookup"><span data-stu-id="29f76-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="29f76-108">Il doit y avoir un élément enfant pour chaque propriété de l’objet qui doit être affiché.</span><span class="sxs-lookup"><span data-stu-id="29f76-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="29f76-109">Les informations d’en-tête de colonne s’affichent dans l’ordre dans lequel les éléments enfants sont spécifiés.</span><span class="sxs-lookup"><span data-stu-id="29f76-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="29f76-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="29f76-110">Attributes</span></span>

<span data-ttu-id="29f76-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="29f76-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="29f76-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="29f76-112">Child Elements</span></span>

|<span data-ttu-id="29f76-113">Élément</span><span class="sxs-lookup"><span data-stu-id="29f76-113">Element</span></span>|<span data-ttu-id="29f76-114">Description</span><span class="sxs-lookup"><span data-stu-id="29f76-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29f76-115">Élément TableColumnHeader (format)</span><span class="sxs-lookup"><span data-stu-id="29f76-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="29f76-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="29f76-116">Optional element.</span></span><br /><br /> <span data-ttu-id="29f76-117">Définit l’étiquette, la largeur et l’alignement des données pour une colonne d’une vue de table.</span><span class="sxs-lookup"><span data-stu-id="29f76-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="29f76-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="29f76-118">Parent Elements</span></span>

|<span data-ttu-id="29f76-119">Élément</span><span class="sxs-lookup"><span data-stu-id="29f76-119">Element</span></span>|<span data-ttu-id="29f76-120">Description</span><span class="sxs-lookup"><span data-stu-id="29f76-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29f76-121">Élément table ((format)</span><span class="sxs-lookup"><span data-stu-id="29f76-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="29f76-122">Définit un format de table pour une vue.</span><span class="sxs-lookup"><span data-stu-id="29f76-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="29f76-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="29f76-123">Remarks</span></span>

<span data-ttu-id="29f76-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="29f76-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="29f76-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="29f76-125">Example</span></span>

<span data-ttu-id="29f76-126">Cet exemple montre un élément `TableHeaders` qui définit deux en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="29f76-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="29f76-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29f76-127">See Also</span></span>

[<span data-ttu-id="29f76-128">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="29f76-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="29f76-129">Élément TableColumnHeader (format)</span><span class="sxs-lookup"><span data-stu-id="29f76-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="29f76-130">Élément table ((format)</span><span class="sxs-lookup"><span data-stu-id="29f76-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="29f76-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="29f76-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
