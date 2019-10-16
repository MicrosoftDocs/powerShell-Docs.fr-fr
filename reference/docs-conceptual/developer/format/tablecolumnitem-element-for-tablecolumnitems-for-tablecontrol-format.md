---
title: Élément TableColumnItem pour TableColumnItems pour table ((format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368228"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="cafbd-102">TableColumnItem, élément pour TableColumnItems pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="cafbd-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="cafbd-103">Définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="cafbd-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="cafbd-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableRowEntries pour table ((format) élément TableRowEntry pour TableRowEntries pour table ((format) Élément TableColumnItems pour TableControlEntry pour table ((format) TableColumnItem, élément pour TableColumnItems pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="cafbd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cafbd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cafbd-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cafbd-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="cafbd-106">Attributes and Elements</span></span>

<span data-ttu-id="cafbd-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TableColumnItem`.</span><span class="sxs-lookup"><span data-stu-id="cafbd-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cafbd-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="cafbd-108">Attributes</span></span>

<span data-ttu-id="cafbd-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="cafbd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cafbd-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cafbd-110">Child Elements</span></span>

|<span data-ttu-id="cafbd-111">Élément</span><span class="sxs-lookup"><span data-stu-id="cafbd-111">Element</span></span>|<span data-ttu-id="cafbd-112">Description</span><span class="sxs-lookup"><span data-stu-id="cafbd-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cafbd-113">Élément Alignment pour TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="cafbd-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="cafbd-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cafbd-114">Optional element.</span></span><br /><br /> <span data-ttu-id="cafbd-115">Définit le mode d’affichage des données dans une colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="cafbd-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="cafbd-116">FormatString, élément de TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="cafbd-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="cafbd-117">Spécifie un modèle de format utilisé pour mettre en forme les données dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="cafbd-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="cafbd-118">PropertyName, élément de TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="cafbd-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="cafbd-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cafbd-119">Optional element.</span></span><br /><br /> <span data-ttu-id="cafbd-120">Spécifie le nom de la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="cafbd-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="cafbd-121">Élément ScriptBlock pour TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="cafbd-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="cafbd-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cafbd-122">Optional element.</span></span><br /><br /> <span data-ttu-id="cafbd-123">Spécifie le script dont la valeur est affichée dans la colonne d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="cafbd-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cafbd-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cafbd-124">Parent Elements</span></span>

|<span data-ttu-id="cafbd-125">Élément</span><span class="sxs-lookup"><span data-stu-id="cafbd-125">Element</span></span>|<span data-ttu-id="cafbd-126">Description</span><span class="sxs-lookup"><span data-stu-id="cafbd-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cafbd-127">Élément TableColumnItems pour TableControlEntry pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="cafbd-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="cafbd-128">Définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="cafbd-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cafbd-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="cafbd-129">Remarks</span></span>

<span data-ttu-id="cafbd-130">Vous pouvez spécifier une propriété d’un objet ou un script dans chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="cafbd-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="cafbd-131">Si aucun élément enfant n’est spécifié, l’élément est un espace réservé et aucune donnée n’est affichée.</span><span class="sxs-lookup"><span data-stu-id="cafbd-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="cafbd-132">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="cafbd-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="cafbd-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="cafbd-133">Example</span></span>

<span data-ttu-id="cafbd-134">Cet exemple montre un élément `TableColumnItem` qui affiche la valeur de la propriété `Status` de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="cafbd-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="cafbd-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cafbd-135">See Also</span></span>

[<span data-ttu-id="cafbd-136">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="cafbd-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="cafbd-137">Élément Alignment pour TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="cafbd-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="cafbd-138">Élément TableColumnItems (format)</span><span class="sxs-lookup"><span data-stu-id="cafbd-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="cafbd-139">FormatString, élément de TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="cafbd-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="cafbd-140">PropertyName, élément de TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="cafbd-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="cafbd-141">Élément ScriptBlock pour TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="cafbd-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="cafbd-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="cafbd-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
