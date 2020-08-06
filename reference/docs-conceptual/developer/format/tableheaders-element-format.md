---
title: Élément TableHeaders (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b3176cbe1316d5b30cb61831d9915a80389709a5
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787425"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="031c3-102">TableHeaders, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="031c3-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="031c3-103">Définit les en-têtes pour les colonnes d’une table.</span><span class="sxs-lookup"><span data-stu-id="031c3-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="031c3-104">Élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="031c3-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="031c3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="031c3-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="031c3-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="031c3-106">Attributes and Elements</span></span>

<span data-ttu-id="031c3-107">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `TableHeaders` élément.</span><span class="sxs-lookup"><span data-stu-id="031c3-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="031c3-108">Il doit y avoir un élément enfant pour chaque propriété de l’objet qui doit être affiché.</span><span class="sxs-lookup"><span data-stu-id="031c3-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="031c3-109">Les informations d’en-tête de colonne s’affichent dans l’ordre dans lequel les éléments enfants sont spécifiés.</span><span class="sxs-lookup"><span data-stu-id="031c3-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="031c3-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="031c3-110">Attributes</span></span>

<span data-ttu-id="031c3-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="031c3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="031c3-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="031c3-112">Child Elements</span></span>

|<span data-ttu-id="031c3-113">Élément</span><span class="sxs-lookup"><span data-stu-id="031c3-113">Element</span></span>|<span data-ttu-id="031c3-114">Description</span><span class="sxs-lookup"><span data-stu-id="031c3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="031c3-115">TableColumnHeader, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="031c3-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="031c3-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="031c3-116">Optional element.</span></span><br /><br /> <span data-ttu-id="031c3-117">Définit l’étiquette, la largeur et l’alignement des données pour une colonne d’une vue de table.</span><span class="sxs-lookup"><span data-stu-id="031c3-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="031c3-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="031c3-118">Parent Elements</span></span>

|<span data-ttu-id="031c3-119">Élément</span><span class="sxs-lookup"><span data-stu-id="031c3-119">Element</span></span>|<span data-ttu-id="031c3-120">Description</span><span class="sxs-lookup"><span data-stu-id="031c3-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="031c3-121">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="031c3-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="031c3-122">Définit un format de table pour une vue.</span><span class="sxs-lookup"><span data-stu-id="031c3-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="031c3-123">Notes</span><span class="sxs-lookup"><span data-stu-id="031c3-123">Remarks</span></span>

<span data-ttu-id="031c3-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="031c3-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="031c3-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="031c3-125">Example</span></span>

<span data-ttu-id="031c3-126">Cet exemple montre un `TableHeaders` élément qui définit deux en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="031c3-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="031c3-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="031c3-127">See Also</span></span>

[<span data-ttu-id="031c3-128">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="031c3-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="031c3-129">TableColumnHeader, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="031c3-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="031c3-130">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="031c3-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="031c3-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="031c3-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
