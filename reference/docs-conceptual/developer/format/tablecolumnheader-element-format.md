---
ms.date: 09/13/2016
ms.topic: reference
title: TableColumnHeader, élément (Format)
description: TableColumnHeader, élément (Format)
ms.openlocfilehash: 30368512875b7c5c4cf3c686f3d09540dea1bd26
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651522"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="8f316-103">TableColumnHeader, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="8f316-103">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="8f316-104">Définit l’étiquette, la largeur de la colonne et l’alignement de l’étiquette pour une colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="8f316-104">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="8f316-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableHeaders pour table ((format) élément TableColumnHeader pour TableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="8f316-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8f316-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f316-106">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f316-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8f316-107">Attributes and Elements</span></span>

<span data-ttu-id="8f316-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableColumnHeader` élément.</span><span class="sxs-lookup"><span data-stu-id="8f316-108">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f316-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="8f316-109">Attributes</span></span>

<span data-ttu-id="8f316-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8f316-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8f316-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8f316-111">Child Elements</span></span>

|<span data-ttu-id="8f316-112">Élément</span><span class="sxs-lookup"><span data-stu-id="8f316-112">Element</span></span>|<span data-ttu-id="8f316-113">Description</span><span class="sxs-lookup"><span data-stu-id="8f316-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f316-114">Élément label pour TableColumnHeader pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="8f316-114">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="8f316-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="8f316-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8f316-116">Définit l’étiquette qui s’affiche en haut de la colonne.</span><span class="sxs-lookup"><span data-stu-id="8f316-116">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="8f316-117">Si aucune étiquette n’est spécifiée, le nom de la propriété dont la valeur est affichée dans les lignes est utilisé.</span><span class="sxs-lookup"><span data-stu-id="8f316-117">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="8f316-118">Width, élément pour TableColumnHeader pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8f316-118">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="8f316-119">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="8f316-119">Required element.</span></span><br /><br /> <span data-ttu-id="8f316-120">Spécifie la largeur (en caractères) de la colonne.</span><span class="sxs-lookup"><span data-stu-id="8f316-120">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="8f316-121">Alignment, élément pour TableColumnHeader pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8f316-121">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="8f316-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="8f316-122">Optional element.</span></span><br /><br /> <span data-ttu-id="8f316-123">Spécifie le mode d’affichage de l’étiquette de la colonne.</span><span class="sxs-lookup"><span data-stu-id="8f316-123">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="8f316-124">Si aucun alignement n’est spécifié, l’étiquette est alignée sur la gauche.</span><span class="sxs-lookup"><span data-stu-id="8f316-124">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8f316-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8f316-125">Parent Elements</span></span>

|<span data-ttu-id="8f316-126">Élément</span><span class="sxs-lookup"><span data-stu-id="8f316-126">Element</span></span>|<span data-ttu-id="8f316-127">Description</span><span class="sxs-lookup"><span data-stu-id="8f316-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f316-128">TableHeaders, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="8f316-128">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="8f316-129">Définit les colonnes d’une vue de table.</span><span class="sxs-lookup"><span data-stu-id="8f316-129">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8f316-130">Notes</span><span class="sxs-lookup"><span data-stu-id="8f316-130">Remarks</span></span>

<span data-ttu-id="8f316-131">Spécifiez un en-tête pour chaque colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="8f316-131">Specify a header for each column of the table.</span></span> <span data-ttu-id="8f316-132">Les colonnes sont affichées dans l’ordre dans lequel les `TableColumnHeader` éléments sont définis.</span><span class="sxs-lookup"><span data-stu-id="8f316-132">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="8f316-133">Une table doit avoir le même nombre d’éléments `TableColumnHeader` que les `TableRowEntry` éléments.</span><span class="sxs-lookup"><span data-stu-id="8f316-133">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="8f316-134">L’en-tête de colonne définit le mode d’affichage du texte en haut de la table.</span><span class="sxs-lookup"><span data-stu-id="8f316-134">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="8f316-135">Les entrées de ligne définissent les données qui sont affichées dans les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="8f316-135">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="8f316-136">Pour plus d’informations sur les composants d’une vue de table, consultez [vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="8f316-136">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8f316-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="8f316-137">Example</span></span>

<span data-ttu-id="8f316-138">L’exemple suivant montre deux `TableColumnHeader` éléments.</span><span class="sxs-lookup"><span data-stu-id="8f316-138">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="8f316-139">Le premier élément définit une colonne dont l’étiquette est « colonne 1 », a une largeur de 16 caractères et dont l’étiquette est alignée à gauche.</span><span class="sxs-lookup"><span data-stu-id="8f316-139">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="8f316-140">Le deuxième élément définit une colonne dont l’étiquette est « colonne 2 », a une largeur de 10 caractères et dont l’étiquette est centrée dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="8f316-140">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8f316-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f316-141">See Also</span></span>

[<span data-ttu-id="8f316-142">Alignment, élément pour TableColumnHeader pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8f316-142">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="8f316-143">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="8f316-143">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8f316-144">Label, élément pour TableColumnHeader pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8f316-144">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="8f316-145">Élément TableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="8f316-145">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="8f316-146">Largeur de TableColumnHeader pour l’élément table ((format)</span><span class="sxs-lookup"><span data-stu-id="8f316-146">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="8f316-147">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f316-147">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
