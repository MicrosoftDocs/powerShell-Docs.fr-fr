---
title: Élément de table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063824"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="52724-102">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="52724-102">TableControl Element (Format)</span></span>

<span data-ttu-id="52724-103">Définit un format de table pour une vue.</span><span class="sxs-lookup"><span data-stu-id="52724-103">Defines a table format for a view.</span></span>

<span data-ttu-id="52724-104">ViewDefinitions élément (Format) vue (Format) table élément (Format)</span><span class="sxs-lookup"><span data-stu-id="52724-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="52724-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52724-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="52724-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="52724-106">Attributes and Elements</span></span>

<span data-ttu-id="52724-107">Les sections suivantes décrivent des attributs, éléments enfants et élément parent de la `TableControl` élément.</span><span class="sxs-lookup"><span data-stu-id="52724-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="52724-108">Vous devez spécifier les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="52724-108">You must specify the rows of the table.</span></span> <span data-ttu-id="52724-109">Tous les autres éléments enfants sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="52724-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="52724-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="52724-110">Attributes</span></span>

<span data-ttu-id="52724-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="52724-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="52724-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="52724-112">Child Elements</span></span>

|<span data-ttu-id="52724-113">Élément</span><span class="sxs-lookup"><span data-stu-id="52724-113">Element</span></span>|<span data-ttu-id="52724-114">Description</span><span class="sxs-lookup"><span data-stu-id="52724-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52724-115">Élément AutoSize pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="52724-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="52724-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="52724-116">Optional element.</span></span><br /><br /> <span data-ttu-id="52724-117">Spécifie si la taille de colonne et le nombre de colonnes sont ajustées en fonction de la taille des données.</span><span class="sxs-lookup"><span data-stu-id="52724-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="52724-118">Élément HideTableHeaders pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="52724-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="52724-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="52724-119">Optional element.</span></span><br /><br /> <span data-ttu-id="52724-120">Indique si l’en-tête de la table n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="52724-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="52724-121">Élément TableHeaders pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="52724-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="52724-122">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="52724-122">Required element.</span></span><br /><br /> <span data-ttu-id="52724-123">Définit les étiquettes, les largeurs et l’alignement des données pour les colonnes de la vue de table.</span><span class="sxs-lookup"><span data-stu-id="52724-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="52724-124">Élément TableRowEntries pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="52724-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="52724-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="52724-125">Optional element.</span></span><br /><br /> <span data-ttu-id="52724-126">Fournit les définitions de la vue de table.</span><span class="sxs-lookup"><span data-stu-id="52724-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="52724-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="52724-127">Parent Elements</span></span>

|<span data-ttu-id="52724-128">Élément</span><span class="sxs-lookup"><span data-stu-id="52724-128">Element</span></span>|<span data-ttu-id="52724-129">Description</span><span class="sxs-lookup"><span data-stu-id="52724-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52724-130">Élément d’affichage (Format)</span><span class="sxs-lookup"><span data-stu-id="52724-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="52724-131">Définit une vue qui est utilisée pour afficher les membres d’un ou plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="52724-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="52724-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="52724-132">Remarks</span></span>

<span data-ttu-id="52724-133">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="52724-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="52724-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="52724-134">Example</span></span>

<span data-ttu-id="52724-135">Cet exemple montre un `TableControl` élément qui est utilisé pour afficher les propriétés de la [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet.</span><span class="sxs-lookup"><span data-stu-id="52724-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="52724-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52724-136">See Also</span></span>

[<span data-ttu-id="52724-137">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="52724-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="52724-138">Élément d’affichage (Format)</span><span class="sxs-lookup"><span data-stu-id="52724-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="52724-139">Élément AutoSize pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="52724-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="52724-140">Élément HideTableHeaders (Format)</span><span class="sxs-lookup"><span data-stu-id="52724-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="52724-141">Élément TableHeaders (Format)</span><span class="sxs-lookup"><span data-stu-id="52724-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="52724-142">Élément TableRowEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="52724-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="52724-143">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="52724-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
