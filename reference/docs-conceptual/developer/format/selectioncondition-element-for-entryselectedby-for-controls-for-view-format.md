---
title: Élément SelectionCondition pour EntrySelectedBy pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1c14b2638249bdbfe25f7a96e917d66ea10ed239
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787578"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="a4222-102">SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a4222-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="a4222-103">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="a4222-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="a4222-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="a4222-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="a4222-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour les contrôles pour l’élément d’affichage (format) CustomEntry pour CustomEntries pour les contrôles de l’élément EntrySelectedBy (format) pour CustomEntry pour les contrôles de l’élément View (format) SelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="a4222-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a4222-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4222-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a4222-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a4222-107">Attributes and Elements</span></span>

<span data-ttu-id="a4222-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="a4222-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a4222-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="a4222-109">Attributes</span></span>

<span data-ttu-id="a4222-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a4222-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a4222-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a4222-111">Child Elements</span></span>

|<span data-ttu-id="a4222-112">Élément</span><span class="sxs-lookup"><span data-stu-id="a4222-112">Element</span></span>|<span data-ttu-id="a4222-113">Description</span><span class="sxs-lookup"><span data-stu-id="a4222-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a4222-114">PropertyName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a4222-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="a4222-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a4222-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a4222-116">Spécifie une propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="a4222-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a4222-117">ScriptBlock, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a4222-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="a4222-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a4222-118">Optional element.</span></span><br /><br /> <span data-ttu-id="a4222-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="a4222-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="a4222-120">SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a4222-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="a4222-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a4222-121">Optional element.</span></span><br /><br /> <span data-ttu-id="a4222-122">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="a4222-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="a4222-123">TypeName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a4222-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="a4222-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a4222-124">Optional element.</span></span><br /><br /> <span data-ttu-id="a4222-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="a4222-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a4222-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a4222-126">Parent Elements</span></span>

|<span data-ttu-id="a4222-127">Élément</span><span class="sxs-lookup"><span data-stu-id="a4222-127">Element</span></span>|<span data-ttu-id="a4222-128">Description</span><span class="sxs-lookup"><span data-stu-id="a4222-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a4222-129">EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a4222-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="a4222-130">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="a4222-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a4222-131">Notes</span><span class="sxs-lookup"><span data-stu-id="a4222-131">Remarks</span></span>

<span data-ttu-id="a4222-132">Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="a4222-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="a4222-133">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="a4222-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="a4222-134">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="a4222-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="a4222-135">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a4222-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a4222-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4222-136">See Also</span></span>

[<span data-ttu-id="a4222-137">PropertyName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a4222-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="a4222-138">ScriptBlock, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a4222-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="a4222-139">SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a4222-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="a4222-140">TypeName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a4222-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="a4222-141">EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a4222-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="a4222-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4222-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
