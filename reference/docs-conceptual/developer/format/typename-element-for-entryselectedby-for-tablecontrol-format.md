---
title: Élément TypeName pour EntrySelectedBy pour table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c514d3e6155278ddd3a0565c87e9377dc8419356
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780200"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="8e725-102">TypeName, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8e725-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="8e725-103">Spécifie un type .NET qui utilise cette entrée de la vue table.</span><span class="sxs-lookup"><span data-stu-id="8e725-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="8e725-104">Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une entrée de table.</span><span class="sxs-lookup"><span data-stu-id="8e725-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="8e725-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry, élément (format) EntrySelectedBy élément (format) TypeName, élément pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="8e725-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8e725-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e725-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e725-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8e725-107">Attributes and Elements</span></span>

<span data-ttu-id="8e725-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="8e725-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e725-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="8e725-109">Attributes</span></span>

<span data-ttu-id="8e725-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8e725-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8e725-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8e725-111">Child Elements</span></span>

<span data-ttu-id="8e725-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8e725-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8e725-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8e725-113">Parent Elements</span></span>

|<span data-ttu-id="8e725-114">Élément</span><span class="sxs-lookup"><span data-stu-id="8e725-114">Element</span></span>|<span data-ttu-id="8e725-115">Description</span><span class="sxs-lookup"><span data-stu-id="8e725-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e725-116">Élément EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="8e725-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="8e725-117">Définit les types .NET qui utilisent cette entrée ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="8e725-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8e725-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="8e725-118">Text Value</span></span>

<span data-ttu-id="8e725-119">Spécifiez le nom du type .NET.</span><span class="sxs-lookup"><span data-stu-id="8e725-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="8e725-120">Notes</span><span class="sxs-lookup"><span data-stu-id="8e725-120">Remarks</span></span>

<span data-ttu-id="8e725-121">Au moins un nom de type, un jeu de sélection ou une condition de sélection doivent être définis pour chaque entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="8e725-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="8e725-122">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="8e725-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8e725-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e725-123">See Also</span></span>

[<span data-ttu-id="8e725-124">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="8e725-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8e725-125">Élément EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="8e725-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="8e725-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e725-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
