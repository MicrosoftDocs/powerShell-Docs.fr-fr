---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour EntrySelectedBy pour TableControl (Format)
description: TypeName, élément pour EntrySelectedBy pour TableControl (Format)
ms.openlocfilehash: 5a9f5cda1810d461d19ffb48a1cfa2d41f87ca96
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651431"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="b40f9-103">TypeName, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b40f9-103">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="b40f9-104">Spécifie un type .NET qui utilise cette entrée de la vue table.</span><span class="sxs-lookup"><span data-stu-id="b40f9-104">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="b40f9-105">Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une entrée de table.</span><span class="sxs-lookup"><span data-stu-id="b40f9-105">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="b40f9-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry, élément (format) EntrySelectedBy élément (format) TypeName, élément pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="b40f9-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b40f9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b40f9-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b40f9-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b40f9-108">Attributes and Elements</span></span>

<span data-ttu-id="b40f9-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="b40f9-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b40f9-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="b40f9-110">Attributes</span></span>

<span data-ttu-id="b40f9-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b40f9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b40f9-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b40f9-112">Child Elements</span></span>

<span data-ttu-id="b40f9-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b40f9-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b40f9-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b40f9-114">Parent Elements</span></span>

|<span data-ttu-id="b40f9-115">Élément</span><span class="sxs-lookup"><span data-stu-id="b40f9-115">Element</span></span>|<span data-ttu-id="b40f9-116">Description</span><span class="sxs-lookup"><span data-stu-id="b40f9-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b40f9-117">Élément EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="b40f9-117">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="b40f9-118">Définit les types .NET qui utilisent cette entrée ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="b40f9-118">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b40f9-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="b40f9-119">Text Value</span></span>

<span data-ttu-id="b40f9-120">Spécifiez le nom du type .NET.</span><span class="sxs-lookup"><span data-stu-id="b40f9-120">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="b40f9-121">Notes</span><span class="sxs-lookup"><span data-stu-id="b40f9-121">Remarks</span></span>

<span data-ttu-id="b40f9-122">Au moins un nom de type, un jeu de sélection ou une condition de sélection doivent être définis pour chaque entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="b40f9-122">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="b40f9-123">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b40f9-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b40f9-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b40f9-124">See Also</span></span>

[<span data-ttu-id="b40f9-125">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="b40f9-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b40f9-126">Élément EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="b40f9-126">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="b40f9-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="b40f9-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
