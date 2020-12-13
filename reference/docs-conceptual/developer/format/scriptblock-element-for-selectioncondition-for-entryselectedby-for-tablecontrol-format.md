---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour TableControl (Format)
description: ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour TableControl (Format)
ms.openlocfilehash: a984bda6b8fba3a5cb9485576ffd847f0d366d3e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659896"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="7419c-103">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7419c-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="7419c-104">Spécifie le bloc de script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="7419c-104">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="7419c-105">Lorsque ce script est évalué à `true` , la condition est remplie et l’entrée de table est utilisée.</span><span class="sxs-lookup"><span data-stu-id="7419c-105">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="7419c-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry élément (format) élément EntrySelectedBy pour TableRowEntry (format) élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format) élément ScriptBlock pour SelectionCondition pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="7419c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7419c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7419c-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7419c-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7419c-108">Attributes and Elements</span></span>

<span data-ttu-id="7419c-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="7419c-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7419c-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="7419c-110">Attributes</span></span>

<span data-ttu-id="7419c-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7419c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7419c-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7419c-112">Child Elements</span></span>

<span data-ttu-id="7419c-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7419c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7419c-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7419c-114">Parent Elements</span></span>

|<span data-ttu-id="7419c-115">Élément</span><span class="sxs-lookup"><span data-stu-id="7419c-115">Element</span></span>|<span data-ttu-id="7419c-116">Description</span><span class="sxs-lookup"><span data-stu-id="7419c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7419c-117">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="7419c-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="7419c-118">Définit la condition qui doit exister pour que cette entrée de table soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="7419c-118">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7419c-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="7419c-119">Text Value</span></span>

<span data-ttu-id="7419c-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="7419c-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="7419c-121">Notes</span><span class="sxs-lookup"><span data-stu-id="7419c-121">Remarks</span></span>

<span data-ttu-id="7419c-122">La condition de sélection doit spécifier au moins un bloc de script ou un nom de propriété, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="7419c-122">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="7419c-123">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7419c-123">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7419c-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="7419c-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7419c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7419c-125">See Also</span></span>

[<span data-ttu-id="7419c-126">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="7419c-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7419c-127">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="7419c-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7419c-128">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7419c-128">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="7419c-129">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="7419c-129">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="7419c-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="7419c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
