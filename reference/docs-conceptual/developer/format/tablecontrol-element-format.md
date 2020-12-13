---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl, élément (Format)
description: TableControl, élément (Format)
ms.openlocfilehash: 93e05e22d61504d7781b6f3c07f9a3fd0b3c9e8a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651459"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="a2adb-103">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a2adb-103">TableControl Element (Format)</span></span>

<span data-ttu-id="a2adb-104">Définit un format de table pour une vue.</span><span class="sxs-lookup"><span data-stu-id="a2adb-104">Defines a table format for a view.</span></span>

<span data-ttu-id="a2adb-105">Élément ViewDefinitions (format), élément de vue (format) élément table ((format)</span><span class="sxs-lookup"><span data-stu-id="a2adb-105">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a2adb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2adb-106">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a2adb-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a2adb-107">Attributes and Elements</span></span>

<span data-ttu-id="a2adb-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableControl` élément.</span><span class="sxs-lookup"><span data-stu-id="a2adb-108">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="a2adb-109">Vous devez spécifier les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="a2adb-109">You must specify the rows of the table.</span></span> <span data-ttu-id="a2adb-110">Tous les autres éléments enfants sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="a2adb-110">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="a2adb-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="a2adb-111">Attributes</span></span>

<span data-ttu-id="a2adb-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a2adb-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a2adb-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a2adb-113">Child Elements</span></span>

|<span data-ttu-id="a2adb-114">Élément</span><span class="sxs-lookup"><span data-stu-id="a2adb-114">Element</span></span>|<span data-ttu-id="a2adb-115">Description</span><span class="sxs-lookup"><span data-stu-id="a2adb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a2adb-116">AutoSize, élément pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a2adb-116">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="a2adb-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a2adb-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a2adb-118">Spécifie si la taille de colonne et le nombre de colonnes sont ajustés en fonction de la taille des données.</span><span class="sxs-lookup"><span data-stu-id="a2adb-118">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="a2adb-119">Élément HideTableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="a2adb-119">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="a2adb-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a2adb-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a2adb-121">Indique si l’en-tête de la table n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="a2adb-121">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="a2adb-122">Élément TableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="a2adb-122">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="a2adb-123">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="a2adb-123">Required element.</span></span><br /><br /> <span data-ttu-id="a2adb-124">Définit les étiquettes, les largeurs et l’alignement des données pour les colonnes de la vue table.</span><span class="sxs-lookup"><span data-stu-id="a2adb-124">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="a2adb-125">TableRowEntries, élément pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a2adb-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="a2adb-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a2adb-126">Optional element.</span></span><br /><br /> <span data-ttu-id="a2adb-127">Fournit les définitions de la vue table.</span><span class="sxs-lookup"><span data-stu-id="a2adb-127">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a2adb-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a2adb-128">Parent Elements</span></span>

|<span data-ttu-id="a2adb-129">Élément</span><span class="sxs-lookup"><span data-stu-id="a2adb-129">Element</span></span>|<span data-ttu-id="a2adb-130">Description</span><span class="sxs-lookup"><span data-stu-id="a2adb-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a2adb-131">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a2adb-131">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="a2adb-132">Définit une vue qui est utilisée pour afficher les membres d’un ou de plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="a2adb-132">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a2adb-133">Notes</span><span class="sxs-lookup"><span data-stu-id="a2adb-133">Remarks</span></span>

<span data-ttu-id="a2adb-134">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a2adb-134">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a2adb-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="a2adb-135">Example</span></span>

<span data-ttu-id="a2adb-136">Cet exemple montre un `TableControl` élément qui est utilisé pour afficher les propriétés de l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="a2adb-136">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="a2adb-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2adb-137">See Also</span></span>

[<span data-ttu-id="a2adb-138">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="a2adb-138">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a2adb-139">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a2adb-139">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="a2adb-140">AutoSize, élément pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a2adb-140">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="a2adb-141">HideTableHeaders, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a2adb-141">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="a2adb-142">TableHeaders, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a2adb-142">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="a2adb-143">Élément TableRowEntries (format)</span><span class="sxs-lookup"><span data-stu-id="a2adb-143">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="a2adb-144">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a2adb-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
