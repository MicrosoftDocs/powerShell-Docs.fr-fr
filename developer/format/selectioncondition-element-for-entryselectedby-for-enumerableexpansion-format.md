---
title: Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064133"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="eea21-102">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="eea21-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="eea21-103">Définit la condition qui doit exister pour développer la collection d’objets de cette définition.</span><span class="sxs-lookup"><span data-stu-id="eea21-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="eea21-104">Configuration élément (Format) élément DefaultSettings (Format) EnumerableExpansions (Format) élément EnumerableExpansion (Format) EntrySelectedBy élément d’élément de SelectionCondition EnumerableExpansion (Format) pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="eea21-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eea21-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eea21-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eea21-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="eea21-106">Attributes and Elements</span></span>

<span data-ttu-id="eea21-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="eea21-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="eea21-108">Vous devez spécifier un seul `PropertyName` ou `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="eea21-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="eea21-109">Le `SelectionSetName` et `TypeName` éléments sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="eea21-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="eea21-110">Vous pouvez spécifier une de des deux éléments.</span><span class="sxs-lookup"><span data-stu-id="eea21-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="eea21-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="eea21-111">Attributes</span></span>

<span data-ttu-id="eea21-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="eea21-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eea21-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="eea21-113">Child Elements</span></span>

|<span data-ttu-id="eea21-114">Élément</span><span class="sxs-lookup"><span data-stu-id="eea21-114">Element</span></span>|<span data-ttu-id="eea21-115">Description</span><span class="sxs-lookup"><span data-stu-id="eea21-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eea21-116">Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="eea21-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="eea21-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="eea21-117">Optional element.</span></span><br /><br /> <span data-ttu-id="eea21-118">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="eea21-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="eea21-119">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="eea21-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="eea21-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="eea21-120">Optional element.</span></span><br /><br /> <span data-ttu-id="eea21-121">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="eea21-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="eea21-122">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="eea21-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="eea21-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="eea21-123">Optional element.</span></span><br /><br /> <span data-ttu-id="eea21-124">Spécifie le jeu des types .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="eea21-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="eea21-125">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="eea21-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="eea21-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="eea21-126">Optional element.</span></span><br /><br /> <span data-ttu-id="eea21-127">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="eea21-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="eea21-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="eea21-128">Parent Elements</span></span>

|<span data-ttu-id="eea21-129">Élément</span><span class="sxs-lookup"><span data-stu-id="eea21-129">Element</span></span>|<span data-ttu-id="eea21-130">Description</span><span class="sxs-lookup"><span data-stu-id="eea21-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eea21-131">Élément EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="eea21-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="eea21-132">Définit les objets de collection .NET sont développées par cette définition.</span><span class="sxs-lookup"><span data-stu-id="eea21-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="eea21-133">Remarques</span><span class="sxs-lookup"><span data-stu-id="eea21-133">Remarks</span></span>

<span data-ttu-id="eea21-134">Chaque définition doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.</span><span class="sxs-lookup"><span data-stu-id="eea21-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="eea21-135">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="eea21-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="eea21-136">La condition de sélection doit spécifier un nom d’un propriété minimum ou un bloc de script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="eea21-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="eea21-137">La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="eea21-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="eea21-138">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour les données de Diplaying](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="eea21-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="eea21-139">Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [Affichage large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="eea21-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eea21-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eea21-140">See Also</span></span>

[<span data-ttu-id="eea21-141">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="eea21-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="eea21-142">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="eea21-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
