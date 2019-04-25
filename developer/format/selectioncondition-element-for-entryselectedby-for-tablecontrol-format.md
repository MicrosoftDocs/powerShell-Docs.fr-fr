---
title: Élément SelectionCondition pour EntrySelectedBy pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075662"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="68f3b-102">SelectionCondition, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="68f3b-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="68f3b-103">Définit la condition qui doit exister pour pouvoir le pour utiliser pour cette définition de la vue de table.</span><span class="sxs-lookup"><span data-stu-id="68f3b-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="68f3b-104">Il n’existe aucune limite au nombre de conditions de sélection qui peut être spécifié pour une définition de table.</span><span class="sxs-lookup"><span data-stu-id="68f3b-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="68f3b-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableRowEntries, élément (Format) élément TableRowEntry (Format) EntrySelectedBy élément de configuration pour TableRowEntry (Format) Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="68f3b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="68f3b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68f3b-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="68f3b-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="68f3b-107">Attributes and Elements</span></span>

<span data-ttu-id="68f3b-108">Les sections suivantes décrivent l’élément parent de l’élément SelectionCondition, attributs et éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="68f3b-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="68f3b-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="68f3b-109">Attributes</span></span>

<span data-ttu-id="68f3b-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="68f3b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="68f3b-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="68f3b-111">Child Elements</span></span>

|<span data-ttu-id="68f3b-112">Élément</span><span class="sxs-lookup"><span data-stu-id="68f3b-112">Element</span></span>|<span data-ttu-id="68f3b-113">Description</span><span class="sxs-lookup"><span data-stu-id="68f3b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68f3b-114">Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="68f3b-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="68f3b-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="68f3b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="68f3b-116">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="68f3b-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="68f3b-117">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="68f3b-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="68f3b-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="68f3b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="68f3b-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="68f3b-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="68f3b-120">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="68f3b-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="68f3b-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="68f3b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="68f3b-122">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="68f3b-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="68f3b-123">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="68f3b-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="68f3b-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="68f3b-124">Optional element.</span></span><br /><br /> <span data-ttu-id="68f3b-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="68f3b-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="68f3b-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="68f3b-126">Parent Elements</span></span>

|<span data-ttu-id="68f3b-127">Élément</span><span class="sxs-lookup"><span data-stu-id="68f3b-127">Element</span></span>|<span data-ttu-id="68f3b-128">Description</span><span class="sxs-lookup"><span data-stu-id="68f3b-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68f3b-129">Élément EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="68f3b-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="68f3b-130">Définit les types .NET qui utilisent cette entrée de table ou de la condition qui doit exister pour cette entrée à utiliser.</span><span class="sxs-lookup"><span data-stu-id="68f3b-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="68f3b-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="68f3b-131">Remarks</span></span>

<span data-ttu-id="68f3b-132">Chaque entrée de liste doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.</span><span class="sxs-lookup"><span data-stu-id="68f3b-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="68f3b-133">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="68f3b-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="68f3b-134">La condition de sélection doit spécifier un nom d’un propriété minimum ou un bloc de script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="68f3b-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="68f3b-135">La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="68f3b-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="68f3b-136">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition Conditions pour lorsqu’une entrée de la vue ou d’élément est utilisé](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="68f3b-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="68f3b-137">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="68f3b-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="68f3b-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68f3b-138">See Also</span></span>

[<span data-ttu-id="68f3b-139">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="68f3b-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="68f3b-140">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="68f3b-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="68f3b-141">Élément EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="68f3b-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="68f3b-142">Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="68f3b-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="68f3b-143">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="68f3b-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="68f3b-144">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="68f3b-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="68f3b-145">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="68f3b-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="68f3b-146">Écriture d’un mise en forme de Windows PowerShell et de Types de fichier</span><span class="sxs-lookup"><span data-stu-id="68f3b-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
