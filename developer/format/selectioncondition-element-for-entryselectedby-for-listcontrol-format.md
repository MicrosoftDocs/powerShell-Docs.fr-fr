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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064099"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="1df82-102">SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1df82-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="1df82-103">Définit la condition qui doit exister pour pouvoir utiliser cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="1df82-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="1df82-104">Il n’existe aucune limite au nombre de conditions de sélection qui peut être spécifié pour une définition de liste.</span><span class="sxs-lookup"><span data-stu-id="1df82-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="1df82-105">Configuration élément (Format) ViewDefinitions, élément (Format) vue (Format) d’élément objet ListControl, élément (Format) situés (Format) ListEntry, élément (Format) EntrySelectedBy élément d’élément de SelectionCondition ListEntry (Format) pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1df82-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1df82-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1df82-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1df82-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="1df82-107">Attributes and Elements</span></span>

<span data-ttu-id="1df82-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="1df82-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1df82-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="1df82-109">Attributes</span></span>

<span data-ttu-id="1df82-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="1df82-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1df82-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1df82-111">Child Elements</span></span>

|<span data-ttu-id="1df82-112">Élément</span><span class="sxs-lookup"><span data-stu-id="1df82-112">Element</span></span>|<span data-ttu-id="1df82-113">Description</span><span class="sxs-lookup"><span data-stu-id="1df82-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1df82-114">Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1df82-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="1df82-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1df82-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1df82-116">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="1df82-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="1df82-117">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1df82-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="1df82-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1df82-118">Optional element.</span></span><br /><br /> <span data-ttu-id="1df82-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="1df82-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="1df82-120">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1df82-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="1df82-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1df82-121">Optional element.</span></span><br /><br /> <span data-ttu-id="1df82-122">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="1df82-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="1df82-123">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1df82-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="1df82-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1df82-124">Optional element.</span></span><br /><br /> <span data-ttu-id="1df82-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="1df82-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1df82-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1df82-126">Parent Elements</span></span>

|<span data-ttu-id="1df82-127">Élément</span><span class="sxs-lookup"><span data-stu-id="1df82-127">Element</span></span>|<span data-ttu-id="1df82-128">Description</span><span class="sxs-lookup"><span data-stu-id="1df82-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1df82-129">Élément EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1df82-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="1df82-130">Définit les types .NET qui utilisent cette entrée de table ou de la condition qui doit exister pour cette entrée à utiliser.</span><span class="sxs-lookup"><span data-stu-id="1df82-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1df82-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="1df82-131">Remarks</span></span>

<span data-ttu-id="1df82-132">LLorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="1df82-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="1df82-133">La condition de sélection doit spécifier un nom d’un propriété minimum ou un bloc de script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="1df82-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="1df82-134">La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="1df82-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="1df82-135">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1df82-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1df82-136">Pour plus d’informations sur d’autres composants d’une vue liste, consultez [création d’une vue liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="1df82-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1df82-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1df82-137">See Also</span></span>

[<span data-ttu-id="1df82-138">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="1df82-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1df82-139">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="1df82-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1df82-140">Élément ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1df82-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="1df82-141">Élément SelectionSetName pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1df82-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="1df82-142">Élément TypeName pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1df82-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[<span data-ttu-id="1df82-143">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1df82-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
