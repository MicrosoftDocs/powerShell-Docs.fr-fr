---
title: Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076342"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="d84f8-102">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d84f8-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="d84f8-103">Spécifie le bloc de script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="d84f8-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="d84f8-104">Lorsque ce script est évalué à `true`, la condition est remplie, et l’entrée de table est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d84f8-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="d84f8-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableRowEntries, élément (Format) élément TableRowEntry (Format) EntrySelectedBy élément de configuration pour TableRowEntry (Format) Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format), élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d84f8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d84f8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d84f8-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d84f8-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="d84f8-107">Attributes and Elements</span></span>

<span data-ttu-id="d84f8-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="d84f8-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d84f8-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="d84f8-109">Attributes</span></span>

<span data-ttu-id="d84f8-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d84f8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d84f8-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d84f8-111">Child Elements</span></span>

<span data-ttu-id="d84f8-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d84f8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d84f8-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d84f8-113">Parent Elements</span></span>

|<span data-ttu-id="d84f8-114">Élément</span><span class="sxs-lookup"><span data-stu-id="d84f8-114">Element</span></span>|<span data-ttu-id="d84f8-115">Description</span><span class="sxs-lookup"><span data-stu-id="d84f8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d84f8-116">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d84f8-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="d84f8-117">Définit la condition qui doit exister pour cette entrée de table à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d84f8-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d84f8-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="d84f8-118">Text Value</span></span>

<span data-ttu-id="d84f8-119">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="d84f8-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="d84f8-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="d84f8-120">Remarks</span></span>

<span data-ttu-id="d84f8-121">La condition de sélection doit spécifier au moins un nom de bloc ou une propriété de script, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="d84f8-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="d84f8-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition Conditions pour lorsqu’une entrée de la vue ou d’élément est utilisé](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d84f8-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d84f8-123">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d84f8-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d84f8-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d84f8-124">See Also</span></span>

[<span data-ttu-id="d84f8-125">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="d84f8-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d84f8-126">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="d84f8-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d84f8-127">Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d84f8-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="d84f8-128">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d84f8-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="d84f8-129">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d84f8-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
