---
title: Élément TableRowEntries pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055731"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="e155b-102">TableRowEntries, élément pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e155b-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="e155b-103">Définit les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="e155b-103">Defines the rows of the table.</span></span>

<span data-ttu-id="e155b-104">Élément (Format) ViewDefinitions, élément (Format) vue élément (Format) table, élément (Format) TableRowEntries élément de configuration pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="e155b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e155b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e155b-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e155b-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="e155b-106">Attributes and Elements</span></span>

<span data-ttu-id="e155b-107">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `TableRowEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="e155b-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e155b-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="e155b-108">Attributes</span></span>

<span data-ttu-id="e155b-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e155b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e155b-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e155b-110">Child Elements</span></span>

|<span data-ttu-id="e155b-111">Élément</span><span class="sxs-lookup"><span data-stu-id="e155b-111">Element</span></span>|<span data-ttu-id="e155b-112">Description</span><span class="sxs-lookup"><span data-stu-id="e155b-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e155b-113">Élément TableRowEntry pour TableRowEntries pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="e155b-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="e155b-114">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="e155b-114">Required element.</span></span><br /><br /> <span data-ttu-id="e155b-115">Définit les données qui s’affiche dans une ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="e155b-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e155b-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e155b-116">Parent Elements</span></span>

|<span data-ttu-id="e155b-117">Élément</span><span class="sxs-lookup"><span data-stu-id="e155b-117">Element</span></span>|<span data-ttu-id="e155b-118">Description</span><span class="sxs-lookup"><span data-stu-id="e155b-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e155b-119">Élément de table (Format)</span><span class="sxs-lookup"><span data-stu-id="e155b-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="e155b-120">Définit un format de table pour une vue.</span><span class="sxs-lookup"><span data-stu-id="e155b-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e155b-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="e155b-121">Remarks</span></span>

<span data-ttu-id="e155b-122">Vous devez spécifier un ou plusieurs `TableRowEntry` éléments pour l’affichage de la table.</span><span class="sxs-lookup"><span data-stu-id="e155b-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="e155b-123">Il n’existe aucune limite maximale pour le nombre de `TableRowEntry` les éléments qui peuvent être ajoutées ni leur ordre n’est significative.</span><span class="sxs-lookup"><span data-stu-id="e155b-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="e155b-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e155b-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e155b-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="e155b-125">Example</span></span>

<span data-ttu-id="e155b-126">L’exemple suivant montre un `TableRowEntries` élément qui définit une ligne qui affiche les valeurs de deux propriétés de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.</span><span class="sxs-lookup"><span data-stu-id="e155b-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e155b-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e155b-127">See Also</span></span>

[<span data-ttu-id="e155b-128">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="e155b-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e155b-129">Élément de table (Format)</span><span class="sxs-lookup"><span data-stu-id="e155b-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="e155b-130">Élément TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e155b-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="e155b-131">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e155b-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
