---
title: Élément SelectionCondition pour EntrySelectedBy pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 7150b29ad84dfb587215ee3e64c356adbd5a6305
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417543"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="52320-102">SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="52320-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="52320-103">Définit la condition qui doit exister pour utiliser cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="52320-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="52320-104">Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour une définition de liste.</span><span class="sxs-lookup"><span data-stu-id="52320-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="52320-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="52320-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="52320-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52320-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="52320-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="52320-107">Attributes and Elements</span></span>

<span data-ttu-id="52320-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="52320-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="52320-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="52320-109">Attributes</span></span>

<span data-ttu-id="52320-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="52320-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="52320-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="52320-111">Child Elements</span></span>

|<span data-ttu-id="52320-112">Élément</span><span class="sxs-lookup"><span data-stu-id="52320-112">Element</span></span>|<span data-ttu-id="52320-113">Description</span><span class="sxs-lookup"><span data-stu-id="52320-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52320-114">PropertyName, élément de SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="52320-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="52320-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="52320-115">Optional element.</span></span><br /><br /> <span data-ttu-id="52320-116">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="52320-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="52320-117">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="52320-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="52320-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="52320-118">Optional element.</span></span><br /><br /> <span data-ttu-id="52320-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="52320-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="52320-120">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="52320-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="52320-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="52320-121">Optional element.</span></span><br /><br /> <span data-ttu-id="52320-122">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="52320-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="52320-123">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="52320-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="52320-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="52320-124">Optional element.</span></span><br /><br /> <span data-ttu-id="52320-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="52320-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="52320-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="52320-126">Parent Elements</span></span>

|<span data-ttu-id="52320-127">Élément</span><span class="sxs-lookup"><span data-stu-id="52320-127">Element</span></span>|<span data-ttu-id="52320-128">Description</span><span class="sxs-lookup"><span data-stu-id="52320-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52320-129">Élément EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="52320-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="52320-130">Définit les types .NET qui utilisent cette entrée de table ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="52320-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="52320-131">Notes</span><span class="sxs-lookup"><span data-stu-id="52320-131">Remarks</span></span>

<span data-ttu-id="52320-132">lWhen vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="52320-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="52320-133">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="52320-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="52320-134">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="52320-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="52320-135">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="52320-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="52320-136">Pour plus d’informations sur les autres composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="52320-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="52320-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52320-137">See Also</span></span>

[<span data-ttu-id="52320-138">Création d’un affichage de liste</span><span class="sxs-lookup"><span data-stu-id="52320-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="52320-139">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="52320-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="52320-140">Élément ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="52320-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="52320-141">Élément SelectionSetName pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="52320-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="52320-142">Élément TypeName pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="52320-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="52320-143">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="52320-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
