---
ms.date: 09/13/2016
ms.topic: reference
title: TableRowEntries, élément pour TableControl (Format)
description: TableRowEntries, élément pour TableControl (Format)
ms.openlocfilehash: 1df63e645234da8276c7ccc5af34e81a56475e43
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651458"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="1f5a2-103">TableRowEntries, élément pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1f5a2-103">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="1f5a2-104">Définit les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="1f5a2-104">Defines the rows of the table.</span></span>

<span data-ttu-id="1f5a2-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableRowEntries pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="1f5a2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f5a2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f5a2-106">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f5a2-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1f5a2-107">Attributes and Elements</span></span>

<span data-ttu-id="1f5a2-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableRowEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="1f5a2-108">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f5a2-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="1f5a2-109">Attributes</span></span>

<span data-ttu-id="1f5a2-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1f5a2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f5a2-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1f5a2-111">Child Elements</span></span>

|<span data-ttu-id="1f5a2-112">Élément</span><span class="sxs-lookup"><span data-stu-id="1f5a2-112">Element</span></span>|<span data-ttu-id="1f5a2-113">Description</span><span class="sxs-lookup"><span data-stu-id="1f5a2-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f5a2-114">TableRowEntry, élément pour TableRowEntries pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1f5a2-114">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="1f5a2-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="1f5a2-115">Required element.</span></span><br /><br /> <span data-ttu-id="1f5a2-116">Définit les données affichées dans une ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="1f5a2-116">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1f5a2-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1f5a2-117">Parent Elements</span></span>

|<span data-ttu-id="1f5a2-118">Élément</span><span class="sxs-lookup"><span data-stu-id="1f5a2-118">Element</span></span>|<span data-ttu-id="1f5a2-119">Description</span><span class="sxs-lookup"><span data-stu-id="1f5a2-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f5a2-120">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="1f5a2-120">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="1f5a2-121">Définit un format de table pour une vue.</span><span class="sxs-lookup"><span data-stu-id="1f5a2-121">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1f5a2-122">Notes</span><span class="sxs-lookup"><span data-stu-id="1f5a2-122">Remarks</span></span>

<span data-ttu-id="1f5a2-123">Vous devez spécifier un ou plusieurs `TableRowEntry` éléments pour la vue de la table.</span><span class="sxs-lookup"><span data-stu-id="1f5a2-123">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="1f5a2-124">Il n’existe pas de limite maximale pour le nombre d' `TableRowEntry` éléments qui peuvent être ajoutés ou dont l’ordre est significatif.</span><span class="sxs-lookup"><span data-stu-id="1f5a2-124">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="1f5a2-125">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="1f5a2-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1f5a2-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f5a2-126">Example</span></span>

<span data-ttu-id="1f5a2-127">L’exemple suivant montre un `TableRowEntries` élément qui définit une ligne qui affiche les valeurs de deux propriétés de l' [objet System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="1f5a2-127">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>
    <EntrySelectedBy>
      <TypeName>System.Diagnostics.Process</TypeName>
    </EntrySelectedBy>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName> Property for first column</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName> Property for second column</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>

```

## <a name="see-also"></a><span data-ttu-id="1f5a2-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f5a2-128">See Also</span></span>

[<span data-ttu-id="1f5a2-129">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="1f5a2-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1f5a2-130">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="1f5a2-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="1f5a2-131">Élément TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1f5a2-131">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="1f5a2-132">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f5a2-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
