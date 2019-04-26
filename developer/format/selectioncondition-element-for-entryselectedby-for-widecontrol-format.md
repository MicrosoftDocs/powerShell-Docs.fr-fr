---
title: Élément SelectionCondition pour EntrySelectedBy pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063980"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="80364-102">SelectionCondition, élément pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="80364-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="80364-103">Définit la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="80364-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="80364-104">Il n’existe aucune limite au nombre de conditions de sélection qui peut être spécifié pour une définition de l’entrée de large.</span><span class="sxs-lookup"><span data-stu-id="80364-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="80364-105">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément WideControl (Format) élément WideEntries (Format) élément WideEntry (Format) EntrySelectedBy élément pour l’élément de SelectionCondition WideEntry (Format) pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="80364-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="80364-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80364-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80364-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="80364-107">Attributes and Elements</span></span>

<span data-ttu-id="80364-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="80364-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="80364-109">Vous devez spécifier un seul `PropertyName` ou `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="80364-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="80364-110">Le `SelectionSetName` et `TypeName` éléments sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="80364-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="80364-111">Vous pouvez spécifier une de des deux éléments.</span><span class="sxs-lookup"><span data-stu-id="80364-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="80364-112">Attributes</span><span class="sxs-lookup"><span data-stu-id="80364-112">Attributes</span></span>

<span data-ttu-id="80364-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="80364-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80364-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="80364-114">Child Elements</span></span>

|<span data-ttu-id="80364-115">Élément</span><span class="sxs-lookup"><span data-stu-id="80364-115">Element</span></span>|<span data-ttu-id="80364-116">Description</span><span class="sxs-lookup"><span data-stu-id="80364-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80364-117">Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="80364-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="80364-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="80364-118">Optional element.</span></span><br /><br /> <span data-ttu-id="80364-119">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="80364-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="80364-120">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="80364-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="80364-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="80364-121">Optional element.</span></span><br /><br /> <span data-ttu-id="80364-122">Spécifie le bloc de script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="80364-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="80364-123">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="80364-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="80364-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="80364-124">Optional element.</span></span><br /><br /> <span data-ttu-id="80364-125">Spécifie le jeu des types .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="80364-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="80364-126">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="80364-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="80364-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="80364-127">Optional element.</span></span><br /><br /> <span data-ttu-id="80364-128">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="80364-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="80364-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="80364-129">Parent Elements</span></span>

|<span data-ttu-id="80364-130">Élément</span><span class="sxs-lookup"><span data-stu-id="80364-130">Element</span></span>|<span data-ttu-id="80364-131">Description</span><span class="sxs-lookup"><span data-stu-id="80364-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80364-132">Élément EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="80364-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="80364-133">Définit les types .NET qui utilisent cette entrée large ou la condition qui doit exister pour cette entrée à utiliser.</span><span class="sxs-lookup"><span data-stu-id="80364-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="80364-134">Remarques</span><span class="sxs-lookup"><span data-stu-id="80364-134">Remarks</span></span>

<span data-ttu-id="80364-135">Chaque entrée large doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.</span><span class="sxs-lookup"><span data-stu-id="80364-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="80364-136">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="80364-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="80364-137">La condition de sélection doit spécifier un nom d’un propriété minimum ou un bloc de script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="80364-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="80364-138">La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="80364-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="80364-139">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition Conditions pour lorsqu’une entrée de la vue ou d’élément est utilisé](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="80364-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="80364-140">Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="80364-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="80364-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80364-141">See Also</span></span>

[<span data-ttu-id="80364-142">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="80364-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="80364-143">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="80364-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="80364-144">Élément EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="80364-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="80364-145">Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="80364-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="80364-146">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="80364-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="80364-147">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="80364-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="80364-148">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="80364-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="80364-149">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="80364-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
