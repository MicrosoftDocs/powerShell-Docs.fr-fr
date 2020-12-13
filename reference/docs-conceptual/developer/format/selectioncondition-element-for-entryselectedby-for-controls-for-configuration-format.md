---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)
description: SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)
ms.openlocfilehash: ce00cdf868a3075875043aeb59f2cb8a17d049a9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645777"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="7badf-103">SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="7badf-103">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="7badf-104">Définit une condition qui doit exister pour qu’une définition de contrôle commun soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="7badf-104">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="7badf-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="7badf-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="7badf-106">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour les contrôles de configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) EntrySelectedBy, élément pour CustomEntry pour les contrôles pour la configuration (format) SelectionCondition, élément pour EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="7badf-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7badf-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7badf-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7badf-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7badf-108">Attributes and Elements</span></span>

<span data-ttu-id="7badf-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="7badf-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7badf-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="7badf-110">Attributes</span></span>

<span data-ttu-id="7badf-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7badf-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7badf-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7badf-112">Child Elements</span></span>

|<span data-ttu-id="7badf-113">Élément</span><span class="sxs-lookup"><span data-stu-id="7badf-113">Element</span></span>|<span data-ttu-id="7badf-114">Description</span><span class="sxs-lookup"><span data-stu-id="7badf-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7badf-115">PropertyName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="7badf-115">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="7badf-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="7badf-116">Optional element.</span></span><br /><br /> <span data-ttu-id="7badf-117">Spécifie une propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="7badf-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="7badf-118">ScriptBlock, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="7badf-118">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="7badf-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="7badf-119">Optional element.</span></span><br /><br /> <span data-ttu-id="7badf-120">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="7badf-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="7badf-121">SelectionSetName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="7badf-121">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="7badf-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="7badf-122">Optional element.</span></span><br /><br /> <span data-ttu-id="7badf-123">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="7badf-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="7badf-124">TypeName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="7badf-124">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="7badf-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="7badf-125">Optional element.</span></span><br /><br /> <span data-ttu-id="7badf-126">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="7badf-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7badf-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7badf-127">Parent Elements</span></span>

|<span data-ttu-id="7badf-128">Élément</span><span class="sxs-lookup"><span data-stu-id="7badf-128">Element</span></span>|<span data-ttu-id="7badf-129">Description</span><span class="sxs-lookup"><span data-stu-id="7badf-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7badf-130">EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="7badf-130">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="7badf-131">Définit les types .NET qui utilisent cette entrée de la définition de contrôle commune.</span><span class="sxs-lookup"><span data-stu-id="7badf-131">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7badf-132">Notes</span><span class="sxs-lookup"><span data-stu-id="7badf-132">Remarks</span></span>

<span data-ttu-id="7badf-133">Les instructions suivantes doivent être suivies lors de la définition d’une condition de sélection :</span><span class="sxs-lookup"><span data-stu-id="7badf-133">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="7badf-134">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="7badf-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="7badf-135">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="7badf-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="7badf-136">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7badf-136">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7badf-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7badf-137">See Also</span></span>

[<span data-ttu-id="7badf-138">PropertyName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="7badf-138">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7badf-139">ScriptBlock, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="7badf-139">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7badf-140">SelectionSetName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="7badf-140">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7badf-141">TypeName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="7badf-141">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7badf-142">EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="7badf-142">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="7badf-143">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7badf-143">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
