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
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143584"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="e73ab-102">TableColumnItem, élément pour TableColumnItems pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e73ab-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="e73ab-103">Définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="e73ab-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="e73ab-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableRowEntries pour table ((format) élément TableRowEntry pour TableRowEntries pour table ((format) Élément TableColumnItems pour TableControlEntry pour table ((format) TableColumnItem, élément pour TableColumnItems pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="e73ab-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e73ab-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e73ab-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e73ab-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="e73ab-106">Attributes and Elements</span></span>

<span data-ttu-id="e73ab-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent `TableColumnItem` de l’élément.</span><span class="sxs-lookup"><span data-stu-id="e73ab-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e73ab-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="e73ab-108">Attributes</span></span>

<span data-ttu-id="e73ab-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e73ab-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e73ab-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e73ab-110">Child Elements</span></span>

|<span data-ttu-id="e73ab-111">Élément</span><span class="sxs-lookup"><span data-stu-id="e73ab-111">Element</span></span>|<span data-ttu-id="e73ab-112">Description</span><span class="sxs-lookup"><span data-stu-id="e73ab-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e73ab-113">Élément Alignment pour TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="e73ab-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="e73ab-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e73ab-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e73ab-115">Définit le mode d’affichage des données dans une colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="e73ab-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="e73ab-116">FormatString, élément de TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="e73ab-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="e73ab-117">Spécifie un modèle de format utilisé pour mettre en forme les données dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="e73ab-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="e73ab-118">PropertyName, élément de TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="e73ab-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="e73ab-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e73ab-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e73ab-120">Spécifie le nom de la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="e73ab-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="e73ab-121">Élément ScriptBlock pour TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="e73ab-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="e73ab-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e73ab-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e73ab-123">Spécifie le script dont la valeur est affichée dans la colonne d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="e73ab-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e73ab-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e73ab-124">Parent Elements</span></span>

|<span data-ttu-id="e73ab-125">Élément</span><span class="sxs-lookup"><span data-stu-id="e73ab-125">Element</span></span>|<span data-ttu-id="e73ab-126">Description</span><span class="sxs-lookup"><span data-stu-id="e73ab-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e73ab-127">Élément TableColumnItems pour TableControlEntry pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="e73ab-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="e73ab-128">Définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="e73ab-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e73ab-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="e73ab-129">Remarks</span></span>

<span data-ttu-id="e73ab-130">Vous pouvez spécifier une propriété d’un objet ou un script dans chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="e73ab-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="e73ab-131">Si aucun élément enfant n’est spécifié, l’élément est un espace réservé et aucune donnée n’est affichée.</span><span class="sxs-lookup"><span data-stu-id="e73ab-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="e73ab-132">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e73ab-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e73ab-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="e73ab-133">Example</span></span>

<span data-ttu-id="e73ab-134">Cet exemple montre un `TableColumnItem` élément qui affiche la valeur de la `Status` propriété de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="e73ab-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="e73ab-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e73ab-135">See Also</span></span>

[<span data-ttu-id="e73ab-136">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="e73ab-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e73ab-137">Élément Alignment pour TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="e73ab-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="e73ab-138">Élément TableColumnItems (format)</span><span class="sxs-lookup"><span data-stu-id="e73ab-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="e73ab-139">FormatString, élément de TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="e73ab-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="e73ab-140">PropertyName, élément de TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="e73ab-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="e73ab-141">Élément ScriptBlock pour TableColumnItem pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="e73ab-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="e73ab-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e73ab-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
