---
title: Élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 748aa1aa0ba603a44334d9401e9e2c0e68f14e03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783413"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="1c417-102">SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="1c417-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="1c417-103">Définit une condition qui doit exister pour qu’une définition de contrôle commun soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="1c417-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="1c417-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="1c417-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="1c417-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour les contrôles de configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) EntrySelectedBy, élément pour CustomEntry pour les contrôles pour la configuration (format) SelectionCondition, élément pour EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="1c417-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1c417-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c417-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1c417-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1c417-107">Attributes and Elements</span></span>

<span data-ttu-id="1c417-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="1c417-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1c417-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="1c417-109">Attributes</span></span>

<span data-ttu-id="1c417-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1c417-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1c417-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1c417-111">Child Elements</span></span>

|<span data-ttu-id="1c417-112">Élément</span><span class="sxs-lookup"><span data-stu-id="1c417-112">Element</span></span>|<span data-ttu-id="1c417-113">Description</span><span class="sxs-lookup"><span data-stu-id="1c417-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c417-114">PropertyName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="1c417-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="1c417-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1c417-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1c417-116">Spécifie une propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="1c417-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="1c417-117">ScriptBlock, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="1c417-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="1c417-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1c417-118">Optional element.</span></span><br /><br /> <span data-ttu-id="1c417-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="1c417-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="1c417-120">SelectionSetName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="1c417-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="1c417-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1c417-121">Optional element.</span></span><br /><br /> <span data-ttu-id="1c417-122">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="1c417-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="1c417-123">TypeName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="1c417-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="1c417-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1c417-124">Optional element.</span></span><br /><br /> <span data-ttu-id="1c417-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="1c417-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1c417-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1c417-126">Parent Elements</span></span>

|<span data-ttu-id="1c417-127">Élément</span><span class="sxs-lookup"><span data-stu-id="1c417-127">Element</span></span>|<span data-ttu-id="1c417-128">Description</span><span class="sxs-lookup"><span data-stu-id="1c417-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c417-129">EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="1c417-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="1c417-130">Définit les types .NET qui utilisent cette entrée de la définition de contrôle commune.</span><span class="sxs-lookup"><span data-stu-id="1c417-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1c417-131">Notes</span><span class="sxs-lookup"><span data-stu-id="1c417-131">Remarks</span></span>

<span data-ttu-id="1c417-132">Les instructions suivantes doivent être suivies lors de la définition d’une condition de sélection :</span><span class="sxs-lookup"><span data-stu-id="1c417-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="1c417-133">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="1c417-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="1c417-134">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="1c417-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="1c417-135">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1c417-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c417-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c417-136">See Also</span></span>

[<span data-ttu-id="1c417-137">PropertyName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="1c417-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="1c417-138">ScriptBlock, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="1c417-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="1c417-139">SelectionSetName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="1c417-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="1c417-140">TypeName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="1c417-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="1c417-141">EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="1c417-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="1c417-142">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c417-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
