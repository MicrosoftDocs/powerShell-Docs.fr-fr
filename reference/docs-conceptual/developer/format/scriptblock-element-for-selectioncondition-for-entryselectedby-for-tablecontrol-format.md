---
title: Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a23d3515749393e9f5a2053634a44d1a817ebf38
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783447"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="8f92e-102">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8f92e-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="8f92e-103">Spécifie le bloc de script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="8f92e-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="8f92e-104">Lorsque ce script est évalué à `true` , la condition est remplie et l’entrée de table est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8f92e-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="8f92e-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry élément (format) élément EntrySelectedBy pour TableRowEntry (format) élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format) élément ScriptBlock pour SelectionCondition pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="8f92e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8f92e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f92e-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f92e-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8f92e-107">Attributes and Elements</span></span>

<span data-ttu-id="8f92e-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="8f92e-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f92e-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="8f92e-109">Attributes</span></span>

<span data-ttu-id="8f92e-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8f92e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8f92e-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8f92e-111">Child Elements</span></span>

<span data-ttu-id="8f92e-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8f92e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8f92e-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8f92e-113">Parent Elements</span></span>

|<span data-ttu-id="8f92e-114">Élément</span><span class="sxs-lookup"><span data-stu-id="8f92e-114">Element</span></span>|<span data-ttu-id="8f92e-115">Description</span><span class="sxs-lookup"><span data-stu-id="8f92e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f92e-116">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8f92e-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="8f92e-117">Définit la condition qui doit exister pour que cette entrée de table soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="8f92e-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8f92e-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="8f92e-118">Text Value</span></span>

<span data-ttu-id="8f92e-119">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="8f92e-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f92e-120">Notes</span><span class="sxs-lookup"><span data-stu-id="8f92e-120">Remarks</span></span>

<span data-ttu-id="8f92e-121">La condition de sélection doit spécifier au moins un bloc de script ou un nom de propriété, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="8f92e-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="8f92e-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8f92e-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8f92e-123">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="8f92e-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8f92e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f92e-124">See Also</span></span>

[<span data-ttu-id="8f92e-125">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="8f92e-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8f92e-126">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="8f92e-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="8f92e-127">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8f92e-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="8f92e-128">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8f92e-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="8f92e-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f92e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
