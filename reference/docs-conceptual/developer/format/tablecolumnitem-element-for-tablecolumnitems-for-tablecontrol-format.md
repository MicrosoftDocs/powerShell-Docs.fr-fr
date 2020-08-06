---
title: Élément TableColumnItem pour TableColumnItems pour table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: beadf771f02519394d799a03db374050e3302321
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785164"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="73de6-102">TableColumnItem, élément pour TableColumnItems pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="73de6-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="73de6-103">Définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="73de6-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="73de6-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableRowEntries pour table ((format) élément TableRowEntry pour TableRowEntries pour table ((format) élément TableColumnItems pour TableControlEntry (format) table (élément pour TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="73de6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="73de6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73de6-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="73de6-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="73de6-106">Attributes and Elements</span></span>

<span data-ttu-id="73de6-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableColumnItem` élément.</span><span class="sxs-lookup"><span data-stu-id="73de6-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="73de6-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="73de6-108">Attributes</span></span>

<span data-ttu-id="73de6-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="73de6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="73de6-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="73de6-110">Child Elements</span></span>

|<span data-ttu-id="73de6-111">Élément</span><span class="sxs-lookup"><span data-stu-id="73de6-111">Element</span></span>|<span data-ttu-id="73de6-112">Description</span><span class="sxs-lookup"><span data-stu-id="73de6-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73de6-113">Alignment, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="73de6-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="73de6-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="73de6-114">Optional element.</span></span><br /><br /> <span data-ttu-id="73de6-115">Définit le mode d’affichage des données dans une colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="73de6-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="73de6-116">FormatString, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="73de6-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="73de6-117">Spécifie un modèle de format utilisé pour mettre en forme les données dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="73de6-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="73de6-118">PropertyName, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="73de6-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="73de6-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="73de6-119">Optional element.</span></span><br /><br /> <span data-ttu-id="73de6-120">Spécifie le nom de la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="73de6-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="73de6-121">ScriptBlock, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="73de6-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="73de6-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="73de6-122">Optional element.</span></span><br /><br /> <span data-ttu-id="73de6-123">Spécifie le script dont la valeur est affichée dans la colonne d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="73de6-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="73de6-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="73de6-124">Parent Elements</span></span>

|<span data-ttu-id="73de6-125">Élément</span><span class="sxs-lookup"><span data-stu-id="73de6-125">Element</span></span>|<span data-ttu-id="73de6-126">Description</span><span class="sxs-lookup"><span data-stu-id="73de6-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73de6-127">Élément TableColumnItems pour TableControlEntry pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="73de6-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="73de6-128">Définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="73de6-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="73de6-129">Notes</span><span class="sxs-lookup"><span data-stu-id="73de6-129">Remarks</span></span>

<span data-ttu-id="73de6-130">Vous pouvez spécifier une propriété d’un objet ou un script dans chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="73de6-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="73de6-131">Si aucun élément enfant n’est spécifié, l’élément est un espace réservé et aucune donnée n’est affichée.</span><span class="sxs-lookup"><span data-stu-id="73de6-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="73de6-132">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="73de6-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="73de6-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="73de6-133">Example</span></span>

<span data-ttu-id="73de6-134">Cet exemple montre un `TableColumnItem` élément qui affiche la valeur de la `Status` propriété de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="73de6-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="73de6-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73de6-135">See Also</span></span>

[<span data-ttu-id="73de6-136">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="73de6-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="73de6-137">Alignment, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="73de6-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="73de6-138">Élément TableColumnItems (format)</span><span class="sxs-lookup"><span data-stu-id="73de6-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="73de6-139">FormatString, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="73de6-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="73de6-140">PropertyName, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="73de6-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="73de6-141">ScriptBlock, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="73de6-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="73de6-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="73de6-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
