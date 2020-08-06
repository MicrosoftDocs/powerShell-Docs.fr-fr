---
title: Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d5858145e092dc962174a776889a4f62db366d71
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785334"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="3e4f3-102">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="3e4f3-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="3e4f3-103">Définit la condition qui doit exister pour développer les objets de collection de cette définition.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="3e4f3-104">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) élément EntrySelectedBy pour EnumerableExpansion (format) élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="3e4f3-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3e4f3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e4f3-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3e4f3-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3e4f3-106">Attributes and Elements</span></span>

<span data-ttu-id="3e4f3-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="3e4f3-108">Vous devez spécifier un seul `PropertyName` `ScriptBlock` élément ou.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="3e4f3-109">Les `SelectionSetName` `TypeName` éléments et sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="3e4f3-110">Vous pouvez spécifier l’un des deux éléments.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3e4f3-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="3e4f3-111">Attributes</span></span>

<span data-ttu-id="3e4f3-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3e4f3-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3e4f3-113">Child Elements</span></span>

|<span data-ttu-id="3e4f3-114">Élément</span><span class="sxs-lookup"><span data-stu-id="3e4f3-114">Element</span></span>|<span data-ttu-id="3e4f3-115">Description</span><span class="sxs-lookup"><span data-stu-id="3e4f3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3e4f3-116">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="3e4f3-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="3e4f3-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-117">Optional element.</span></span><br /><br /> <span data-ttu-id="3e4f3-118">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="3e4f3-119">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="3e4f3-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="3e4f3-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-120">Optional element.</span></span><br /><br /> <span data-ttu-id="3e4f3-121">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="3e4f3-122">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="3e4f3-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="3e4f3-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-123">Optional element.</span></span><br /><br /> <span data-ttu-id="3e4f3-124">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="3e4f3-125">TypeName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="3e4f3-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="3e4f3-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-126">Optional element.</span></span><br /><br /> <span data-ttu-id="3e4f3-127">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3e4f3-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3e4f3-128">Parent Elements</span></span>

|<span data-ttu-id="3e4f3-129">Élément</span><span class="sxs-lookup"><span data-stu-id="3e4f3-129">Element</span></span>|<span data-ttu-id="3e4f3-130">Description</span><span class="sxs-lookup"><span data-stu-id="3e4f3-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3e4f3-131">EntrySelectedBy, élément pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="3e4f3-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="3e4f3-132">Définit les objets de collection .NET développés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3e4f3-133">Notes</span><span class="sxs-lookup"><span data-stu-id="3e4f3-133">Remarks</span></span>

<span data-ttu-id="3e4f3-134">Au moins un nom de type, un jeu de sélection ou une condition de sélection doivent être définis pour chaque définition.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="3e4f3-135">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="3e4f3-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="3e4f3-136">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="3e4f3-137">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="3e4f3-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="3e4f3-138">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions pour la diffusion des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3e4f3-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3e4f3-139">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="3e4f3-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3e4f3-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e4f3-140">See Also</span></span>

[<span data-ttu-id="3e4f3-141">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="3e4f3-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3e4f3-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e4f3-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
