---
title: Élément TableColumnHeader (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361848"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="12398-102">TableColumnHeader, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="12398-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="12398-103">Définit l’étiquette, la largeur de la colonne et l’alignement de l’étiquette pour une colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="12398-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="12398-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableHeaders pour table ((format) élément TableColumnHeader pour TableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="12398-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="12398-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12398-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="12398-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="12398-106">Attributes and Elements</span></span>

<span data-ttu-id="12398-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TableColumnHeader`.</span><span class="sxs-lookup"><span data-stu-id="12398-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="12398-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="12398-108">Attributes</span></span>

<span data-ttu-id="12398-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="12398-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="12398-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="12398-110">Child Elements</span></span>

|<span data-ttu-id="12398-111">Élément</span><span class="sxs-lookup"><span data-stu-id="12398-111">Element</span></span>|<span data-ttu-id="12398-112">Description</span><span class="sxs-lookup"><span data-stu-id="12398-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="12398-113">Élément label pour TableColumnHeader pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="12398-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="12398-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="12398-114">Optional element.</span></span><br /><br /> <span data-ttu-id="12398-115">Définit l’étiquette qui s’affiche en haut de la colonne.</span><span class="sxs-lookup"><span data-stu-id="12398-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="12398-116">Si aucune étiquette n’est spécifiée, le nom de la propriété dont la valeur est affichée dans les lignes est utilisé.</span><span class="sxs-lookup"><span data-stu-id="12398-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="12398-117">Width, élément de TableColumnHeader pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="12398-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="12398-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="12398-118">Required element.</span></span><br /><br /> <span data-ttu-id="12398-119">Spécifie la largeur (en caractères) de la colonne.</span><span class="sxs-lookup"><span data-stu-id="12398-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="12398-120">Élément Alignment pour TableColumnHeader pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="12398-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="12398-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="12398-121">Optional element.</span></span><br /><br /> <span data-ttu-id="12398-122">Spécifie le mode d’affichage de l’étiquette de la colonne.</span><span class="sxs-lookup"><span data-stu-id="12398-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="12398-123">Si aucun alignement n’est spécifié, l’étiquette est alignée sur la gauche.</span><span class="sxs-lookup"><span data-stu-id="12398-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="12398-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="12398-124">Parent Elements</span></span>

|<span data-ttu-id="12398-125">Élément</span><span class="sxs-lookup"><span data-stu-id="12398-125">Element</span></span>|<span data-ttu-id="12398-126">Description</span><span class="sxs-lookup"><span data-stu-id="12398-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="12398-127">Élément TableHeaders (format)</span><span class="sxs-lookup"><span data-stu-id="12398-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="12398-128">Définit les colonnes d’une vue de table.</span><span class="sxs-lookup"><span data-stu-id="12398-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="12398-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="12398-129">Remarks</span></span>

<span data-ttu-id="12398-130">Spécifiez un en-tête pour chaque colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="12398-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="12398-131">Les colonnes sont affichées dans l’ordre dans lequel les éléments de `TableColumnHeader` sont définis.</span><span class="sxs-lookup"><span data-stu-id="12398-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="12398-132">Une table doit avoir le même nombre d’éléments `TableColumnHeader` que les éléments `TableRowEntry`.</span><span class="sxs-lookup"><span data-stu-id="12398-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="12398-133">L’en-tête de colonne définit le mode d’affichage du texte en haut de la table.</span><span class="sxs-lookup"><span data-stu-id="12398-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="12398-134">Les entrées de ligne définissent les données qui sont affichées dans les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="12398-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="12398-135">Pour plus d’informations sur les composants d’une vue de table, consultez [vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="12398-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="12398-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="12398-136">Example</span></span>

<span data-ttu-id="12398-137">L’exemple suivant montre deux éléments `TableColumnHeader`.</span><span class="sxs-lookup"><span data-stu-id="12398-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="12398-138">Le premier élément définit une colonne dont l’étiquette est « colonne 1 », a une largeur de 16 caractères et dont l’étiquette est alignée à gauche.</span><span class="sxs-lookup"><span data-stu-id="12398-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="12398-139">Le deuxième élément définit une colonne dont l’étiquette est « colonne 2 », a une largeur de 10 caractères et dont l’étiquette est centrée dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="12398-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="12398-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12398-140">See Also</span></span>

[<span data-ttu-id="12398-141">Élément Alignment pour TableColumnHeader pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="12398-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="12398-142">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="12398-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="12398-143">Élément label pour TableColumnHeader pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="12398-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="12398-144">Élément TableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="12398-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="12398-145">Largeur de TableColumnHeader pour l’élément table ((format)</span><span class="sxs-lookup"><span data-stu-id="12398-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="12398-146">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="12398-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
