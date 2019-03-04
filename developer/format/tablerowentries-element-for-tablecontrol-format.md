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
ms.openlocfilehash: d93750f919c1075f173dc9ac70324cc003e36879
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862185"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="6f8c8-102">TableRowEntries, élément pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6f8c8-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="6f8c8-103">Définit les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="6f8c8-103">Defines the rows of the table.</span></span>

<span data-ttu-id="6f8c8-104">Élément (Format) ViewDefinitions, élément (Format) vue élément (Format) table, élément (Format) TableRowEntries élément de configuration pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="6f8c8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6f8c8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f8c8-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6f8c8-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="6f8c8-106">Attributes and Elements</span></span>

<span data-ttu-id="6f8c8-107">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `TableRowEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="6f8c8-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6f8c8-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="6f8c8-108">Attributes</span></span>

<span data-ttu-id="6f8c8-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="6f8c8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6f8c8-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6f8c8-110">Child Elements</span></span>

|<span data-ttu-id="6f8c8-111">Élément</span><span class="sxs-lookup"><span data-stu-id="6f8c8-111">Element</span></span>|<span data-ttu-id="6f8c8-112">Description</span><span class="sxs-lookup"><span data-stu-id="6f8c8-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6f8c8-113">Élément TableRowEntry pour TableRowEntries pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="6f8c8-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="6f8c8-114">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="6f8c8-114">Required element.</span></span><br /><br /> <span data-ttu-id="6f8c8-115">Définit les données qui s’affiche dans une ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="6f8c8-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6f8c8-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6f8c8-116">Parent Elements</span></span>

|<span data-ttu-id="6f8c8-117">Élément</span><span class="sxs-lookup"><span data-stu-id="6f8c8-117">Element</span></span>|<span data-ttu-id="6f8c8-118">Description</span><span class="sxs-lookup"><span data-stu-id="6f8c8-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6f8c8-119">Élément de table (Format)</span><span class="sxs-lookup"><span data-stu-id="6f8c8-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="6f8c8-120">Définit un format de table pour une vue.</span><span class="sxs-lookup"><span data-stu-id="6f8c8-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6f8c8-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="6f8c8-121">Remarks</span></span>

<span data-ttu-id="6f8c8-122">Vous devez spécifier un ou plusieurs `TableRowEntry` éléments pour l’affichage de la table.</span><span class="sxs-lookup"><span data-stu-id="6f8c8-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="6f8c8-123">Il n’existe aucune limite maximale pour le nombre de `TableRowEntry` les éléments qui peuvent être ajoutées ni leur ordre n’est significative.</span><span class="sxs-lookup"><span data-stu-id="6f8c8-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="6f8c8-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="6f8c8-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6f8c8-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f8c8-125">Example</span></span>

<span data-ttu-id="6f8c8-126">L’exemple suivant montre un `TableRowEntries` élément qui définit une ligne qui affiche les valeurs de deux propriétés de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.</span><span class="sxs-lookup"><span data-stu-id="6f8c8-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6f8c8-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f8c8-127">See Also</span></span>

[<span data-ttu-id="6f8c8-128">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="6f8c8-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6f8c8-129">Élément de table (Format)</span><span class="sxs-lookup"><span data-stu-id="6f8c8-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="6f8c8-130">Élément TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6f8c8-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="6f8c8-131">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="6f8c8-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
