---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)
description: PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)
ms.openlocfilehash: dcb59fc438ae217870566f09204fb16b8f031614
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665785"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="454cb-103">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="454cb-103">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="454cb-104">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="454cb-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="454cb-105">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et l’entrée de table est utilisée.</span><span class="sxs-lookup"><span data-stu-id="454cb-105">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="454cb-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry élément (format) élément EntrySelectedBy pour TableRowEntry (format) élément SelectionCondition pour EntrySelectedBy (format) NomPropriété, élément pour TableRowEntry pour SelectionCondition (format)</span><span class="sxs-lookup"><span data-stu-id="454cb-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="454cb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="454cb-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="454cb-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="454cb-108">Attributes and Elements</span></span>

<span data-ttu-id="454cb-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="454cb-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="454cb-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="454cb-110">Attributes</span></span>

<span data-ttu-id="454cb-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="454cb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="454cb-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="454cb-112">Child Elements</span></span>

<span data-ttu-id="454cb-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="454cb-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="454cb-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="454cb-114">Parent Elements</span></span>

|<span data-ttu-id="454cb-115">Élément</span><span class="sxs-lookup"><span data-stu-id="454cb-115">Element</span></span>|<span data-ttu-id="454cb-116">Description</span><span class="sxs-lookup"><span data-stu-id="454cb-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="454cb-117">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="454cb-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="454cb-118">Définit la condition qui doit exister pour que cette entrée de table soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="454cb-118">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="454cb-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="454cb-119">Text Value</span></span>

<span data-ttu-id="454cb-120">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="454cb-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="454cb-121">Notes</span><span class="sxs-lookup"><span data-stu-id="454cb-121">Remarks</span></span>

<span data-ttu-id="454cb-122">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="454cb-122">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="454cb-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="454cb-123">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="454cb-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="454cb-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="454cb-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="454cb-125">See Also</span></span>

[<span data-ttu-id="454cb-126">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="454cb-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="454cb-127">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="454cb-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="454cb-128">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="454cb-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="454cb-129">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="454cb-129">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="454cb-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="454cb-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
