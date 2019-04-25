---
title: Élément TableColumnItem pour TableColumnItems pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063936"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="d9d24-102">TableColumnItem, élément pour TableColumnItems pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d9d24-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="d9d24-103">Définit la propriété ou un script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="d9d24-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="d9d24-104">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableRowEntries élément de configuration pour élément TableRowEntry de table (Format) pour TableRowEntries pour la table (Format) Élément TableColumnItems pour TableControlEntry pour élément TableColumnItem de table (Format) pour TableColumnItems pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="d9d24-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d9d24-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9d24-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d9d24-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="d9d24-106">Attributes and Elements</span></span>

<span data-ttu-id="d9d24-107">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `TableColumnItem` élément.</span><span class="sxs-lookup"><span data-stu-id="d9d24-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d9d24-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="d9d24-108">Attributes</span></span>

<span data-ttu-id="d9d24-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d9d24-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d9d24-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d9d24-110">Child Elements</span></span>

|<span data-ttu-id="d9d24-111">Élément</span><span class="sxs-lookup"><span data-stu-id="d9d24-111">Element</span></span>|<span data-ttu-id="d9d24-112">Description</span><span class="sxs-lookup"><span data-stu-id="d9d24-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9d24-113">Élément d’alignement pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="d9d24-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="d9d24-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d9d24-114">Optional element.</span></span><br /><br /> <span data-ttu-id="d9d24-115">Définit comment les données dans une colonne de la ligne sont affichées.</span><span class="sxs-lookup"><span data-stu-id="d9d24-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="d9d24-116">Élément FormatString pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="d9d24-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="d9d24-117">Spécifie un modèle de format qui est utilisé pour mettre en forme les données dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="d9d24-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="d9d24-118">Élément PropertyName pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="d9d24-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="d9d24-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d9d24-119">Optional element.</span></span><br /><br /> <span data-ttu-id="d9d24-120">Spécifie le nom de la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="d9d24-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="d9d24-121">Élément ScriptBlock pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="d9d24-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="d9d24-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d9d24-122">Optional element.</span></span><br /><br /> <span data-ttu-id="d9d24-123">Spécifie le script dont la valeur est affichée dans la colonne d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="d9d24-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d9d24-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d9d24-124">Parent Elements</span></span>

|<span data-ttu-id="d9d24-125">Élément</span><span class="sxs-lookup"><span data-stu-id="d9d24-125">Element</span></span>|<span data-ttu-id="d9d24-126">Description</span><span class="sxs-lookup"><span data-stu-id="d9d24-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9d24-127">Élément TableColumnItems pour TableControlEntry pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="d9d24-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="d9d24-128">Définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="d9d24-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d9d24-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="d9d24-129">Remarks</span></span>

<span data-ttu-id="d9d24-130">Vous pouvez spécifier une propriété d’un objet ou un script dans chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="d9d24-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="d9d24-131">Si aucun élément enfant n’est spécifié, l’élément est un espace réservé, et aucune donnée n’est affichée.</span><span class="sxs-lookup"><span data-stu-id="d9d24-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="d9d24-132">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d9d24-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d9d24-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="d9d24-133">Example</span></span>

<span data-ttu-id="d9d24-134">Cet exemple montre un `TableColumnItem` élément qui affiche la valeur de la `Status` propriété de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.</span><span class="sxs-lookup"><span data-stu-id="d9d24-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="d9d24-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9d24-135">See Also</span></span>

[<span data-ttu-id="d9d24-136">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="d9d24-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d9d24-137">Élément d’alignement pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="d9d24-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="d9d24-138">Élément TableColumnItems (Format)</span><span class="sxs-lookup"><span data-stu-id="d9d24-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="d9d24-139">Élément FormatString pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="d9d24-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="d9d24-140">Élément PropertyName pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="d9d24-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="d9d24-141">Élément ScriptBlock pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="d9d24-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="d9d24-142">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d9d24-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
