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
ms.openlocfilehash: 5d80bdd736ad540f01c5ebc1f3d31dc9bd628ba5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862415"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="ea5f2-102">TableColumnItem, élément pour TableColumnItems pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ea5f2-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="ea5f2-103">Définit la propriété ou un script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="ea5f2-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="ea5f2-104">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableRowEntries élément de configuration pour élément TableRowEntry de table (Format) pour TableRowEntries pour la table (Format) Élément TableColumnItems pour TableControlEntry pour élément TableColumnItem de table (Format) pour TableColumnItems pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="ea5f2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ea5f2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea5f2-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <SciptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ea5f2-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="ea5f2-106">Attributes and Elements</span></span>

<span data-ttu-id="ea5f2-107">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `TableColumnItem` élément.</span><span class="sxs-lookup"><span data-stu-id="ea5f2-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ea5f2-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="ea5f2-108">Attributes</span></span>

<span data-ttu-id="ea5f2-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ea5f2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ea5f2-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ea5f2-110">Child Elements</span></span>

|<span data-ttu-id="ea5f2-111">Élément</span><span class="sxs-lookup"><span data-stu-id="ea5f2-111">Element</span></span>|<span data-ttu-id="ea5f2-112">Description</span><span class="sxs-lookup"><span data-stu-id="ea5f2-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ea5f2-113">Élément d’alignement pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="ea5f2-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="ea5f2-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ea5f2-114">Optional element.</span></span><br /><br /> <span data-ttu-id="ea5f2-115">Définit comment les données dans une colonne de la ligne sont affichées.</span><span class="sxs-lookup"><span data-stu-id="ea5f2-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="ea5f2-116">Élément FormatString pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="ea5f2-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="ea5f2-117">Spécifie un modèle de format qui est utilisé pour mettre en forme les données dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="ea5f2-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="ea5f2-118">Élément PropertyName pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="ea5f2-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="ea5f2-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ea5f2-119">Optional element.</span></span><br /><br /> <span data-ttu-id="ea5f2-120">Spécifie le nom de la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="ea5f2-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="ea5f2-121">Élément ScriptBlock pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="ea5f2-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="ea5f2-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ea5f2-122">Optional element.</span></span><br /><br /> <span data-ttu-id="ea5f2-123">Spécifie le script dont la valeur est affichée dans la colonne d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="ea5f2-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ea5f2-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ea5f2-124">Parent Elements</span></span>

|<span data-ttu-id="ea5f2-125">Élément</span><span class="sxs-lookup"><span data-stu-id="ea5f2-125">Element</span></span>|<span data-ttu-id="ea5f2-126">Description</span><span class="sxs-lookup"><span data-stu-id="ea5f2-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ea5f2-127">Élément TableColumnItems pour TableControlEntry pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="ea5f2-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="ea5f2-128">Définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="ea5f2-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ea5f2-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="ea5f2-129">Remarks</span></span>

<span data-ttu-id="ea5f2-130">Vous pouvez spécifier une propriété d’un objet ou un script dans chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="ea5f2-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="ea5f2-131">Si aucun élément enfant n’est spécifié, l’élément est un espace réservé, et aucune donnée n’est affichée.</span><span class="sxs-lookup"><span data-stu-id="ea5f2-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="ea5f2-132">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="ea5f2-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ea5f2-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="ea5f2-133">Example</span></span>

<span data-ttu-id="ea5f2-134">Cet exemple montre un `TableColumnItem` élément qui affiche la valeur de la `Status` propriété de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.</span><span class="sxs-lookup"><span data-stu-id="ea5f2-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="ea5f2-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea5f2-135">See Also</span></span>

[<span data-ttu-id="ea5f2-136">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="ea5f2-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ea5f2-137">Élément d’alignement pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="ea5f2-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="ea5f2-138">Élément TableColumnItems (Format)</span><span class="sxs-lookup"><span data-stu-id="ea5f2-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="ea5f2-139">Élément FormatString pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="ea5f2-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="ea5f2-140">Élément PropertyName pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="ea5f2-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="ea5f2-141">Élément ScriptBlock pour TableColumnItem pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="ea5f2-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="ea5f2-142">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea5f2-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
