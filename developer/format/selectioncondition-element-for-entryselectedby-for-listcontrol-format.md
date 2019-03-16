---
title: Élément SelectionCondition pour EntrySelectedBy pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 633204f3b181316761746ea2679910216fb74657
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058961"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="00978-102">SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="00978-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="00978-103">Définit la condition qui doit exister pour pouvoir utiliser cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="00978-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="00978-104">Il n’existe aucune limite au nombre de conditions de sélection qui peut être spécifié pour une définition de liste.</span><span class="sxs-lookup"><span data-stu-id="00978-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="00978-105">Configuration élément (Format) ViewDefinitions, élément (Format) vue (Format) d’élément objet ListControl, élément (Format) situés (Format) ListEntry, élément (Format) EntrySelectedBy élément d’élément de SelectionCondition ListEntry (Format) pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="00978-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="00978-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00978-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="00978-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="00978-107">Attributes and Elements</span></span>

<span data-ttu-id="00978-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="00978-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="00978-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="00978-109">Attributes</span></span>

<span data-ttu-id="00978-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="00978-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="00978-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="00978-111">Child Elements</span></span>

|<span data-ttu-id="00978-112">Élément</span><span class="sxs-lookup"><span data-stu-id="00978-112">Element</span></span>|<span data-ttu-id="00978-113">Description</span><span class="sxs-lookup"><span data-stu-id="00978-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00978-114">Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="00978-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="00978-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="00978-115">Optional element.</span></span><br /><br /> <span data-ttu-id="00978-116">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="00978-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="00978-117">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="00978-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="00978-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="00978-118">Optional element.</span></span><br /><br /> <span data-ttu-id="00978-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="00978-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="00978-120">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="00978-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="00978-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="00978-121">Optional element.</span></span><br /><br /> <span data-ttu-id="00978-122">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="00978-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="00978-123">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="00978-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="00978-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="00978-124">Optional element.</span></span><br /><br /> <span data-ttu-id="00978-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="00978-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="00978-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="00978-126">Parent Elements</span></span>

|<span data-ttu-id="00978-127">Élément</span><span class="sxs-lookup"><span data-stu-id="00978-127">Element</span></span>|<span data-ttu-id="00978-128">Description</span><span class="sxs-lookup"><span data-stu-id="00978-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00978-129">Élément EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="00978-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="00978-130">Définit les types .NET qui utilisent cette entrée de table ou de la condition qui doit exister pour cette entrée à utiliser.</span><span class="sxs-lookup"><span data-stu-id="00978-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="00978-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="00978-131">Remarks</span></span>

<span data-ttu-id="00978-132">LLorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="00978-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="00978-133">La condition de sélection doit spécifier un nom d’un propriété minimum ou un bloc de script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="00978-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="00978-134">La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="00978-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="00978-135">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="00978-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="00978-136">Pour plus d’informations sur d’autres composants d’une vue liste, consultez [création d’une vue liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="00978-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="00978-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00978-137">See Also</span></span>

[<span data-ttu-id="00978-138">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="00978-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="00978-139">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="00978-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="00978-140">Élément ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="00978-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="00978-141">Élément SelectionSetName pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="00978-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="00978-142">Élément TypeName pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="00978-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[<span data-ttu-id="00978-143">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="00978-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
