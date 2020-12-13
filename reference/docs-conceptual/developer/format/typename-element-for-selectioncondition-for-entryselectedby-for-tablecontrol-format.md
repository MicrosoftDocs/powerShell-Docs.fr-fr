---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour SelectionCondition pour EntrySelectedBy pour TableControl (Format)
description: TypeName, élément pour SelectionCondition pour EntrySelectedBy pour TableControl (Format)
ms.openlocfilehash: 66e90ab33775cf35d5e98e45266996d2d1a622d7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659637"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="ebbcc-103">TypeName, élément pour SelectionCondition pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ebbcc-103">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="ebbcc-104">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="ebbcc-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="ebbcc-105">Lorsque ce type est présent, la condition est remplie et la ligne de table est utilisée.</span><span class="sxs-lookup"><span data-stu-id="ebbcc-105">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="ebbcc-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry élément (format) élément EntrySelectedBy pour TableRowEntry (format) élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format) élément TypeName pour SelectionCondition pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="ebbcc-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ebbcc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebbcc-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ebbcc-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ebbcc-108">Attributes and Elements</span></span>

<span data-ttu-id="ebbcc-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="ebbcc-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ebbcc-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="ebbcc-110">Attributes</span></span>

<span data-ttu-id="ebbcc-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ebbcc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ebbcc-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ebbcc-112">Child Elements</span></span>

<span data-ttu-id="ebbcc-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ebbcc-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ebbcc-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ebbcc-114">Parent Elements</span></span>

|<span data-ttu-id="ebbcc-115">Élément</span><span class="sxs-lookup"><span data-stu-id="ebbcc-115">Element</span></span>|<span data-ttu-id="ebbcc-116">Description</span><span class="sxs-lookup"><span data-stu-id="ebbcc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ebbcc-117">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ebbcc-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="ebbcc-118">Définit la condition qui doit exister pour cette ligne de table à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ebbcc-118">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ebbcc-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="ebbcc-119">Text Value</span></span>

<span data-ttu-id="ebbcc-120">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="ebbcc-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ebbcc-121">Notes</span><span class="sxs-lookup"><span data-stu-id="ebbcc-121">Remarks</span></span>

<span data-ttu-id="ebbcc-122">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="ebbcc-122">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="ebbcc-123">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ebbcc-123">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ebbcc-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="ebbcc-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ebbcc-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebbcc-125">See Also</span></span>

[<span data-ttu-id="ebbcc-126">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="ebbcc-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ebbcc-127">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="ebbcc-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ebbcc-128">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ebbcc-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="ebbcc-129">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ebbcc-129">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="ebbcc-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="ebbcc-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
