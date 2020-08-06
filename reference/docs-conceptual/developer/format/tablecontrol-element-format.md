---
title: Élément table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 34e20006a7501650f2a22f71a3d7e999fb8b2337
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785130"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="c3782-102">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="c3782-102">TableControl Element (Format)</span></span>

<span data-ttu-id="c3782-103">Définit un format de table pour une vue.</span><span class="sxs-lookup"><span data-stu-id="c3782-103">Defines a table format for a view.</span></span>

<span data-ttu-id="c3782-104">Élément ViewDefinitions (format), élément de vue (format) élément table ((format)</span><span class="sxs-lookup"><span data-stu-id="c3782-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3782-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3782-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3782-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c3782-106">Attributes and Elements</span></span>

<span data-ttu-id="c3782-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableControl` élément.</span><span class="sxs-lookup"><span data-stu-id="c3782-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="c3782-108">Vous devez spécifier les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="c3782-108">You must specify the rows of the table.</span></span> <span data-ttu-id="c3782-109">Tous les autres éléments enfants sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="c3782-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="c3782-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="c3782-110">Attributes</span></span>

<span data-ttu-id="c3782-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c3782-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c3782-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c3782-112">Child Elements</span></span>

|<span data-ttu-id="c3782-113">Élément</span><span class="sxs-lookup"><span data-stu-id="c3782-113">Element</span></span>|<span data-ttu-id="c3782-114">Description</span><span class="sxs-lookup"><span data-stu-id="c3782-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3782-115">AutoSize, élément pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c3782-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="c3782-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="c3782-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c3782-117">Spécifie si la taille de colonne et le nombre de colonnes sont ajustés en fonction de la taille des données.</span><span class="sxs-lookup"><span data-stu-id="c3782-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="c3782-118">Élément HideTableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="c3782-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="c3782-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="c3782-119">Optional element.</span></span><br /><br /> <span data-ttu-id="c3782-120">Indique si l’en-tête de la table n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="c3782-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="c3782-121">Élément TableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="c3782-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="c3782-122">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="c3782-122">Required element.</span></span><br /><br /> <span data-ttu-id="c3782-123">Définit les étiquettes, les largeurs et l’alignement des données pour les colonnes de la vue table.</span><span class="sxs-lookup"><span data-stu-id="c3782-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="c3782-124">TableRowEntries, élément pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c3782-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="c3782-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="c3782-125">Optional element.</span></span><br /><br /> <span data-ttu-id="c3782-126">Fournit les définitions de la vue table.</span><span class="sxs-lookup"><span data-stu-id="c3782-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c3782-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c3782-127">Parent Elements</span></span>

|<span data-ttu-id="c3782-128">Élément</span><span class="sxs-lookup"><span data-stu-id="c3782-128">Element</span></span>|<span data-ttu-id="c3782-129">Description</span><span class="sxs-lookup"><span data-stu-id="c3782-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3782-130">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="c3782-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="c3782-131">Définit une vue qui est utilisée pour afficher les membres d’un ou de plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="c3782-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c3782-132">Notes</span><span class="sxs-lookup"><span data-stu-id="c3782-132">Remarks</span></span>

<span data-ttu-id="c3782-133">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c3782-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c3782-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3782-134">Example</span></span>

<span data-ttu-id="c3782-135">Cet exemple montre un `TableControl` élément qui est utilisé pour afficher les propriétés de l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="c3782-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c3782-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3782-136">See Also</span></span>

[<span data-ttu-id="c3782-137">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="c3782-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c3782-138">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="c3782-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="c3782-139">AutoSize, élément pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c3782-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="c3782-140">HideTableHeaders, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="c3782-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="c3782-141">TableHeaders, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="c3782-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="c3782-142">Élément TableRowEntries (format)</span><span class="sxs-lookup"><span data-stu-id="c3782-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="c3782-143">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3782-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
