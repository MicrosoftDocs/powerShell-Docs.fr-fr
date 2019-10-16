---
title: Élément table ((format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368198"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="20195-102">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="20195-102">TableControl Element (Format)</span></span>

<span data-ttu-id="20195-103">Définit un format de table pour une vue.</span><span class="sxs-lookup"><span data-stu-id="20195-103">Defines a table format for a view.</span></span>

<span data-ttu-id="20195-104">Élément ViewDefinitions (format), élément de vue (format) élément table ((format)</span><span class="sxs-lookup"><span data-stu-id="20195-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="20195-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20195-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="20195-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="20195-106">Attributes and Elements</span></span>

<span data-ttu-id="20195-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TableControl`.</span><span class="sxs-lookup"><span data-stu-id="20195-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="20195-108">Vous devez spécifier les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="20195-108">You must specify the rows of the table.</span></span> <span data-ttu-id="20195-109">Tous les autres éléments enfants sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="20195-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="20195-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="20195-110">Attributes</span></span>

<span data-ttu-id="20195-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="20195-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="20195-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="20195-112">Child Elements</span></span>

|<span data-ttu-id="20195-113">Élément</span><span class="sxs-lookup"><span data-stu-id="20195-113">Element</span></span>|<span data-ttu-id="20195-114">Description</span><span class="sxs-lookup"><span data-stu-id="20195-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20195-115">AutoSize, élément de table ((format)</span><span class="sxs-lookup"><span data-stu-id="20195-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="20195-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="20195-116">Optional element.</span></span><br /><br /> <span data-ttu-id="20195-117">Spécifie si la taille de colonne et le nombre de colonnes sont ajustés en fonction de la taille des données.</span><span class="sxs-lookup"><span data-stu-id="20195-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="20195-118">Élément HideTableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="20195-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="20195-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="20195-119">Optional element.</span></span><br /><br /> <span data-ttu-id="20195-120">Indique si l’en-tête de la table n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="20195-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="20195-121">Élément TableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="20195-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="20195-122">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="20195-122">Required element.</span></span><br /><br /> <span data-ttu-id="20195-123">Définit les étiquettes, les largeurs et l’alignement des données pour les colonnes de la vue table.</span><span class="sxs-lookup"><span data-stu-id="20195-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="20195-124">Élément TableRowEntries pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="20195-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="20195-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="20195-125">Optional element.</span></span><br /><br /> <span data-ttu-id="20195-126">Fournit les définitions de la vue table.</span><span class="sxs-lookup"><span data-stu-id="20195-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="20195-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="20195-127">Parent Elements</span></span>

|<span data-ttu-id="20195-128">Élément</span><span class="sxs-lookup"><span data-stu-id="20195-128">Element</span></span>|<span data-ttu-id="20195-129">Description</span><span class="sxs-lookup"><span data-stu-id="20195-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20195-130">View, élément (format)</span><span class="sxs-lookup"><span data-stu-id="20195-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="20195-131">Définit une vue qui est utilisée pour afficher les membres d’un ou de plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="20195-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="20195-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="20195-132">Remarks</span></span>

<span data-ttu-id="20195-133">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="20195-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="20195-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="20195-134">Example</span></span>

<span data-ttu-id="20195-135">Cet exemple montre un élément `TableControl` qui est utilisé pour afficher les propriétés de l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="20195-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="20195-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20195-136">See Also</span></span>

[<span data-ttu-id="20195-137">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="20195-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="20195-138">View, élément (format)</span><span class="sxs-lookup"><span data-stu-id="20195-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="20195-139">AutoSize, élément de table ((format)</span><span class="sxs-lookup"><span data-stu-id="20195-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="20195-140">Élément HideTableHeaders (format)</span><span class="sxs-lookup"><span data-stu-id="20195-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="20195-141">Élément TableHeaders (format)</span><span class="sxs-lookup"><span data-stu-id="20195-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="20195-142">Élément TableRowEntries (format)</span><span class="sxs-lookup"><span data-stu-id="20195-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="20195-143">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="20195-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
