---
title: Élément TableRowEntries pour table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4cc5d354df3e552e181a95148caa020f0041db92
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785113"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="bfb11-102">TableRowEntries, élément pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bfb11-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="bfb11-103">Définit les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="bfb11-103">Defines the rows of the table.</span></span>

<span data-ttu-id="bfb11-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableRowEntries pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="bfb11-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bfb11-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfb11-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bfb11-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bfb11-106">Attributes and Elements</span></span>

<span data-ttu-id="bfb11-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableRowEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="bfb11-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bfb11-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="bfb11-108">Attributes</span></span>

<span data-ttu-id="bfb11-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bfb11-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bfb11-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bfb11-110">Child Elements</span></span>

|<span data-ttu-id="bfb11-111">Élément</span><span class="sxs-lookup"><span data-stu-id="bfb11-111">Element</span></span>|<span data-ttu-id="bfb11-112">Description</span><span class="sxs-lookup"><span data-stu-id="bfb11-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bfb11-113">TableRowEntry, élément pour TableRowEntries pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bfb11-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="bfb11-114">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="bfb11-114">Required element.</span></span><br /><br /> <span data-ttu-id="bfb11-115">Définit les données affichées dans une ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="bfb11-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bfb11-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bfb11-116">Parent Elements</span></span>

|<span data-ttu-id="bfb11-117">Élément</span><span class="sxs-lookup"><span data-stu-id="bfb11-117">Element</span></span>|<span data-ttu-id="bfb11-118">Description</span><span class="sxs-lookup"><span data-stu-id="bfb11-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bfb11-119">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="bfb11-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="bfb11-120">Définit un format de table pour une vue.</span><span class="sxs-lookup"><span data-stu-id="bfb11-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bfb11-121">Notes</span><span class="sxs-lookup"><span data-stu-id="bfb11-121">Remarks</span></span>

<span data-ttu-id="bfb11-122">Vous devez spécifier un ou plusieurs `TableRowEntry` éléments pour la vue de la table.</span><span class="sxs-lookup"><span data-stu-id="bfb11-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="bfb11-123">Il n’existe pas de limite maximale pour le nombre d' `TableRowEntry` éléments qui peuvent être ajoutés ou dont l’ordre est significatif.</span><span class="sxs-lookup"><span data-stu-id="bfb11-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="bfb11-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="bfb11-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="bfb11-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="bfb11-125">Example</span></span>

<span data-ttu-id="bfb11-126">L’exemple suivant montre un `TableRowEntries` élément qui définit une ligne qui affiche les valeurs de deux propriétés de l' [objet System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="bfb11-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bfb11-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfb11-127">See Also</span></span>

[<span data-ttu-id="bfb11-128">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="bfb11-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="bfb11-129">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="bfb11-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="bfb11-130">Élément TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="bfb11-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="bfb11-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="bfb11-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
