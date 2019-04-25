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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075407"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="176b2-102">TableHeaders, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="176b2-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="176b2-103">Définit les en-têtes pour les colonnes d’une table.</span><span class="sxs-lookup"><span data-stu-id="176b2-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="176b2-104">Élément ViewDefinitions (Format) vue élément (Format) table (Format) TableHeaders élément pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="176b2-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="176b2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="176b2-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="176b2-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="176b2-106">Attributes and Elements</span></span>

<span data-ttu-id="176b2-107">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de la `TableHeaders` élément.</span><span class="sxs-lookup"><span data-stu-id="176b2-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="176b2-108">Il doit être un élément enfant pour chaque propriété de l’objet qui doit être affichée.</span><span class="sxs-lookup"><span data-stu-id="176b2-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="176b2-109">Les informations d’en-tête de colonne s’affiche dans l’ordre que les éléments enfants sont spécifiées.</span><span class="sxs-lookup"><span data-stu-id="176b2-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="176b2-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="176b2-110">Attributes</span></span>

<span data-ttu-id="176b2-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="176b2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="176b2-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="176b2-112">Child Elements</span></span>

|<span data-ttu-id="176b2-113">Élément</span><span class="sxs-lookup"><span data-stu-id="176b2-113">Element</span></span>|<span data-ttu-id="176b2-114">Description</span><span class="sxs-lookup"><span data-stu-id="176b2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="176b2-115">Élément TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="176b2-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="176b2-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="176b2-116">Optional element.</span></span><br /><br /> <span data-ttu-id="176b2-117">Définit l’étiquette, la largeur et l’alignement des données pour une colonne d’une vue de table.</span><span class="sxs-lookup"><span data-stu-id="176b2-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="176b2-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="176b2-118">Parent Elements</span></span>

|<span data-ttu-id="176b2-119">Élément</span><span class="sxs-lookup"><span data-stu-id="176b2-119">Element</span></span>|<span data-ttu-id="176b2-120">Description</span><span class="sxs-lookup"><span data-stu-id="176b2-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="176b2-121">Élément de table (Format)</span><span class="sxs-lookup"><span data-stu-id="176b2-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="176b2-122">Définit un format de table pour une vue.</span><span class="sxs-lookup"><span data-stu-id="176b2-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="176b2-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="176b2-123">Remarks</span></span>

<span data-ttu-id="176b2-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="176b2-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="176b2-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="176b2-125">Example</span></span>

<span data-ttu-id="176b2-126">Cet exemple montre un `TableHeaders` élément qui définit deux en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="176b2-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="176b2-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="176b2-127">See Also</span></span>

[<span data-ttu-id="176b2-128">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="176b2-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="176b2-129">Élément TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="176b2-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="176b2-130">Élément de table (Format)</span><span class="sxs-lookup"><span data-stu-id="176b2-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="176b2-131">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="176b2-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
