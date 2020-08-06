---
title: Élément TableColumnHeader (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6296aea5c567663b1c3c0a2cf0a57b21aa5394de
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785181"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="395bd-102">TableColumnHeader, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="395bd-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="395bd-103">Définit l’étiquette, la largeur de la colonne et l’alignement de l’étiquette pour une colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="395bd-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="395bd-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableHeaders pour table ((format) élément TableColumnHeader pour TableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="395bd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="395bd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="395bd-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="395bd-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="395bd-106">Attributes and Elements</span></span>

<span data-ttu-id="395bd-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableColumnHeader` élément.</span><span class="sxs-lookup"><span data-stu-id="395bd-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="395bd-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="395bd-108">Attributes</span></span>

<span data-ttu-id="395bd-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="395bd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="395bd-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="395bd-110">Child Elements</span></span>

|<span data-ttu-id="395bd-111">Élément</span><span class="sxs-lookup"><span data-stu-id="395bd-111">Element</span></span>|<span data-ttu-id="395bd-112">Description</span><span class="sxs-lookup"><span data-stu-id="395bd-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="395bd-113">Élément label pour TableColumnHeader pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="395bd-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="395bd-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="395bd-114">Optional element.</span></span><br /><br /> <span data-ttu-id="395bd-115">Définit l’étiquette qui s’affiche en haut de la colonne.</span><span class="sxs-lookup"><span data-stu-id="395bd-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="395bd-116">Si aucune étiquette n’est spécifiée, le nom de la propriété dont la valeur est affichée dans les lignes est utilisé.</span><span class="sxs-lookup"><span data-stu-id="395bd-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="395bd-117">Width, élément pour TableColumnHeader pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="395bd-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="395bd-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="395bd-118">Required element.</span></span><br /><br /> <span data-ttu-id="395bd-119">Spécifie la largeur (en caractères) de la colonne.</span><span class="sxs-lookup"><span data-stu-id="395bd-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="395bd-120">Alignment, élément pour TableColumnHeader pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="395bd-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="395bd-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="395bd-121">Optional element.</span></span><br /><br /> <span data-ttu-id="395bd-122">Spécifie le mode d’affichage de l’étiquette de la colonne.</span><span class="sxs-lookup"><span data-stu-id="395bd-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="395bd-123">Si aucun alignement n’est spécifié, l’étiquette est alignée sur la gauche.</span><span class="sxs-lookup"><span data-stu-id="395bd-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="395bd-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="395bd-124">Parent Elements</span></span>

|<span data-ttu-id="395bd-125">Élément</span><span class="sxs-lookup"><span data-stu-id="395bd-125">Element</span></span>|<span data-ttu-id="395bd-126">Description</span><span class="sxs-lookup"><span data-stu-id="395bd-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="395bd-127">TableHeaders, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="395bd-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="395bd-128">Définit les colonnes d’une vue de table.</span><span class="sxs-lookup"><span data-stu-id="395bd-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="395bd-129">Notes</span><span class="sxs-lookup"><span data-stu-id="395bd-129">Remarks</span></span>

<span data-ttu-id="395bd-130">Spécifiez un en-tête pour chaque colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="395bd-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="395bd-131">Les colonnes sont affichées dans l’ordre dans lequel les `TableColumnHeader` éléments sont définis.</span><span class="sxs-lookup"><span data-stu-id="395bd-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="395bd-132">Une table doit avoir le même nombre d’éléments `TableColumnHeader` que les `TableRowEntry` éléments.</span><span class="sxs-lookup"><span data-stu-id="395bd-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="395bd-133">L’en-tête de colonne définit le mode d’affichage du texte en haut de la table.</span><span class="sxs-lookup"><span data-stu-id="395bd-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="395bd-134">Les entrées de ligne définissent les données qui sont affichées dans les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="395bd-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="395bd-135">Pour plus d’informations sur les composants d’une vue de table, consultez [vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="395bd-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="395bd-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="395bd-136">Example</span></span>

<span data-ttu-id="395bd-137">L’exemple suivant montre deux `TableColumnHeader` éléments.</span><span class="sxs-lookup"><span data-stu-id="395bd-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="395bd-138">Le premier élément définit une colonne dont l’étiquette est « colonne 1 », a une largeur de 16 caractères et dont l’étiquette est alignée à gauche.</span><span class="sxs-lookup"><span data-stu-id="395bd-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="395bd-139">Le deuxième élément définit une colonne dont l’étiquette est « colonne 2 », a une largeur de 10 caractères et dont l’étiquette est centrée dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="395bd-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="395bd-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="395bd-140">See Also</span></span>

[<span data-ttu-id="395bd-141">Alignment, élément pour TableColumnHeader pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="395bd-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="395bd-142">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="395bd-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="395bd-143">Label, élément pour TableColumnHeader pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="395bd-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="395bd-144">Élément TableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="395bd-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="395bd-145">Largeur de TableColumnHeader pour l’élément table ((format)</span><span class="sxs-lookup"><span data-stu-id="395bd-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="395bd-146">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="395bd-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
