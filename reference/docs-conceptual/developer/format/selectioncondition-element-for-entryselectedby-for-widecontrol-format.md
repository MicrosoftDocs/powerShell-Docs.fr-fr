---
title: Élément SelectionCondition pour EntrySelectedBy pour WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364778"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="f5711-102">SelectionCondition, élément pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f5711-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="f5711-103">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="f5711-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="f5711-104">Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour une définition d’entrée étendue.</span><span class="sxs-lookup"><span data-stu-id="f5711-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="f5711-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) SelectionCondition, élément pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f5711-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5711-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5711-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5711-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="f5711-107">Attributes and Elements</span></span>

<span data-ttu-id="f5711-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="f5711-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="f5711-109">Vous devez spécifier un élément `PropertyName` ou `ScriptBlock` unique.</span><span class="sxs-lookup"><span data-stu-id="f5711-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="f5711-110">Les éléments `SelectionSetName` et `TypeName` sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="f5711-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="f5711-111">Vous pouvez spécifier l’un des deux éléments.</span><span class="sxs-lookup"><span data-stu-id="f5711-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5711-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="f5711-112">Attributes</span></span>

<span data-ttu-id="f5711-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f5711-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f5711-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f5711-114">Child Elements</span></span>

|<span data-ttu-id="f5711-115">Élément</span><span class="sxs-lookup"><span data-stu-id="f5711-115">Element</span></span>|<span data-ttu-id="f5711-116">Description</span><span class="sxs-lookup"><span data-stu-id="f5711-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5711-117">PropertyName, élément de SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f5711-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="f5711-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="f5711-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f5711-119">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="f5711-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f5711-120">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f5711-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="f5711-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="f5711-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f5711-122">Spécifie le bloc de script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="f5711-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="f5711-123">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f5711-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="f5711-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="f5711-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f5711-125">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="f5711-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="f5711-126">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f5711-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="f5711-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="f5711-127">Optional element.</span></span><br /><br /> <span data-ttu-id="f5711-128">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="f5711-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f5711-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f5711-129">Parent Elements</span></span>

|<span data-ttu-id="f5711-130">Élément</span><span class="sxs-lookup"><span data-stu-id="f5711-130">Element</span></span>|<span data-ttu-id="f5711-131">Description</span><span class="sxs-lookup"><span data-stu-id="f5711-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5711-132">Élément EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f5711-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="f5711-133">Définit les types .NET qui utilisent cette entrée étendue ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="f5711-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f5711-134">Remarks</span><span class="sxs-lookup"><span data-stu-id="f5711-134">Remarks</span></span>

<span data-ttu-id="f5711-135">Chaque entrée à largeur unique doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définie.</span><span class="sxs-lookup"><span data-stu-id="f5711-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="f5711-136">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="f5711-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="f5711-137">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="f5711-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f5711-138">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="f5711-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f5711-139">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f5711-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f5711-140">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f5711-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5711-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5711-141">See Also</span></span>

[<span data-ttu-id="f5711-142">Création d’un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="f5711-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f5711-143">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="f5711-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f5711-144">Élément EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f5711-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="f5711-145">PropertyName, élément de SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f5711-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="f5711-146">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f5711-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f5711-147">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f5711-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="f5711-148">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="f5711-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f5711-149">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="f5711-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
