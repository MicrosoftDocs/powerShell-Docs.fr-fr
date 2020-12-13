---
ms.date: 09/13/2016
ms.topic: reference
title: TableColumnItem, élément pour TableColumnItems pour TableControl (Format)
description: TableColumnItem, élément pour TableColumnItems pour TableControl (Format)
ms.openlocfilehash: 8ef5158c9bb9f074d5c58190d4d3b20c10c83744
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659858"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="7aa77-103">TableColumnItem, élément pour TableColumnItems pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7aa77-103">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="7aa77-104">Définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="7aa77-104">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="7aa77-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableRowEntries pour table ((format) élément TableRowEntry pour TableRowEntries pour table ((format) élément TableColumnItems pour TableControlEntry (format) table (élément pour TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="7aa77-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7aa77-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7aa77-106">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7aa77-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7aa77-107">Attributes and Elements</span></span>

<span data-ttu-id="7aa77-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableColumnItem` élément.</span><span class="sxs-lookup"><span data-stu-id="7aa77-108">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7aa77-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="7aa77-109">Attributes</span></span>

<span data-ttu-id="7aa77-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7aa77-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7aa77-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7aa77-111">Child Elements</span></span>

|<span data-ttu-id="7aa77-112">Élément</span><span class="sxs-lookup"><span data-stu-id="7aa77-112">Element</span></span>|<span data-ttu-id="7aa77-113">Description</span><span class="sxs-lookup"><span data-stu-id="7aa77-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7aa77-114">Alignment, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7aa77-114">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="7aa77-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="7aa77-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7aa77-116">Définit le mode d’affichage des données dans une colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="7aa77-116">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="7aa77-117">FormatString, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7aa77-117">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="7aa77-118">Spécifie un modèle de format utilisé pour mettre en forme les données dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="7aa77-118">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="7aa77-119">PropertyName, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7aa77-119">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="7aa77-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="7aa77-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7aa77-121">Spécifie le nom de la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="7aa77-121">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="7aa77-122">ScriptBlock, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7aa77-122">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="7aa77-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="7aa77-123">Optional element.</span></span><br /><br /> <span data-ttu-id="7aa77-124">Spécifie le script dont la valeur est affichée dans la colonne d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="7aa77-124">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7aa77-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7aa77-125">Parent Elements</span></span>

|<span data-ttu-id="7aa77-126">Élément</span><span class="sxs-lookup"><span data-stu-id="7aa77-126">Element</span></span>|<span data-ttu-id="7aa77-127">Description</span><span class="sxs-lookup"><span data-stu-id="7aa77-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7aa77-128">Élément TableColumnItems pour TableControlEntry pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="7aa77-128">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="7aa77-129">Définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="7aa77-129">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7aa77-130">Notes</span><span class="sxs-lookup"><span data-stu-id="7aa77-130">Remarks</span></span>

<span data-ttu-id="7aa77-131">Vous pouvez spécifier une propriété d’un objet ou un script dans chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="7aa77-131">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="7aa77-132">Si aucun élément enfant n’est spécifié, l’élément est un espace réservé et aucune donnée n’est affichée.</span><span class="sxs-lookup"><span data-stu-id="7aa77-132">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="7aa77-133">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="7aa77-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7aa77-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="7aa77-134">Example</span></span>

<span data-ttu-id="7aa77-135">Cet exemple montre un `TableColumnItem` élément qui affiche la valeur de la `Status` propriété de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="7aa77-135">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="7aa77-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7aa77-136">See Also</span></span>

[<span data-ttu-id="7aa77-137">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="7aa77-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7aa77-138">Alignment, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7aa77-138">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="7aa77-139">Élément TableColumnItems (format)</span><span class="sxs-lookup"><span data-stu-id="7aa77-139">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="7aa77-140">FormatString, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7aa77-140">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="7aa77-141">PropertyName, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7aa77-141">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="7aa77-142">ScriptBlock, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7aa77-142">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="7aa77-143">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="7aa77-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
