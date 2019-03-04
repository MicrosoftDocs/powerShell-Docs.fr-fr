---
title: Élément TableHeaders (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856875"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="33f2f-102">TableHeaders, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="33f2f-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="33f2f-103">Définit les en-têtes pour les colonnes d’une table.</span><span class="sxs-lookup"><span data-stu-id="33f2f-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="33f2f-104">Élément ViewDefinitions (Format) vue élément (Format) table (Format) TableHeaders élément pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="33f2f-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="33f2f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33f2f-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="33f2f-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="33f2f-106">Attributes and Elements</span></span>

<span data-ttu-id="33f2f-107">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de la `TableHeaders` élément.</span><span class="sxs-lookup"><span data-stu-id="33f2f-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="33f2f-108">Il doit être un élément enfant pour chaque propriété de l’objet qui doit être affichée.</span><span class="sxs-lookup"><span data-stu-id="33f2f-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="33f2f-109">Les informations d’en-tête de colonne s’affiche dans l’ordre que les éléments enfants sont spécifiées.</span><span class="sxs-lookup"><span data-stu-id="33f2f-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="33f2f-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="33f2f-110">Attributes</span></span>

<span data-ttu-id="33f2f-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="33f2f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33f2f-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="33f2f-112">Child Elements</span></span>

|<span data-ttu-id="33f2f-113">Élément</span><span class="sxs-lookup"><span data-stu-id="33f2f-113">Element</span></span>|<span data-ttu-id="33f2f-114">Description</span><span class="sxs-lookup"><span data-stu-id="33f2f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33f2f-115">Élément TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="33f2f-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="33f2f-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="33f2f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="33f2f-117">Définit l’étiquette, la largeur et l’alignement des données pour une colonne d’une vue de table.</span><span class="sxs-lookup"><span data-stu-id="33f2f-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="33f2f-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="33f2f-118">Parent Elements</span></span>

|<span data-ttu-id="33f2f-119">Élément</span><span class="sxs-lookup"><span data-stu-id="33f2f-119">Element</span></span>|<span data-ttu-id="33f2f-120">Description</span><span class="sxs-lookup"><span data-stu-id="33f2f-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33f2f-121">Élément de table (Format)</span><span class="sxs-lookup"><span data-stu-id="33f2f-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="33f2f-122">Définit un format de table pour une vue.</span><span class="sxs-lookup"><span data-stu-id="33f2f-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="33f2f-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="33f2f-123">Remarks</span></span>

<span data-ttu-id="33f2f-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="33f2f-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="33f2f-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="33f2f-125">Example</span></span>

<span data-ttu-id="33f2f-126">Cet exemple montre un `TableHeaders` élément qui définit deux en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="33f2f-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="33f2f-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33f2f-127">See Also</span></span>

[<span data-ttu-id="33f2f-128">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="33f2f-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="33f2f-129">Élément TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="33f2f-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="33f2f-130">Élément de table (Format)</span><span class="sxs-lookup"><span data-stu-id="33f2f-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="33f2f-131">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="33f2f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
