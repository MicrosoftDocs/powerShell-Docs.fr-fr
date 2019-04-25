---
title: Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075764"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="5fbdc-102">SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5fbdc-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5fbdc-103">Définit une condition qui doit exister pour une définition commune de contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="5fbdc-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5fbdc-105">Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour les contrôles pour Élément de CustomEntry de configuration (Format) pour CustomControl pour les contrôles d’élément de EntrySelectedBy Configuration (Format) pour CustomEntry pour les contrôles d’élément de SelectionCondition Configuration (Format) pour EntrySelectedBy pour CustomEntry pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5fbdc-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5fbdc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fbdc-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5fbdc-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="5fbdc-107">Attributes and Elements</span></span>

<span data-ttu-id="5fbdc-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5fbdc-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="5fbdc-109">Attributes</span></span>

<span data-ttu-id="5fbdc-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5fbdc-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5fbdc-111">Child Elements</span></span>

|<span data-ttu-id="5fbdc-112">Élément</span><span class="sxs-lookup"><span data-stu-id="5fbdc-112">Element</span></span>|<span data-ttu-id="5fbdc-113">Description</span><span class="sxs-lookup"><span data-stu-id="5fbdc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5fbdc-114">Élément PropertyName pour SelectionCondition pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5fbdc-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="5fbdc-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5fbdc-116">Spécifie une propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="5fbdc-117">Élément ScriptBlock pour SelectionCondition pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5fbdc-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="5fbdc-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5fbdc-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="5fbdc-120">Élément SelectionSetName pour SelectionCondition pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5fbdc-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="5fbdc-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-121">Optional element.</span></span><br /><br /> <span data-ttu-id="5fbdc-122">Spécifie le jeu des types .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="5fbdc-123">Élément TypeName pour SelectionCondition pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5fbdc-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="5fbdc-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-124">Optional element.</span></span><br /><br /> <span data-ttu-id="5fbdc-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5fbdc-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5fbdc-126">Parent Elements</span></span>

|<span data-ttu-id="5fbdc-127">Élément</span><span class="sxs-lookup"><span data-stu-id="5fbdc-127">Element</span></span>|<span data-ttu-id="5fbdc-128">Description</span><span class="sxs-lookup"><span data-stu-id="5fbdc-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5fbdc-129">Élément EntrySelectedBy pour CustomEntry pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5fbdc-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="5fbdc-130">Définit les types .NET qui utilisent cette entrée de la définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5fbdc-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="5fbdc-131">Remarks</span></span>

<span data-ttu-id="5fbdc-132">Les instructions suivantes doivent être suivies lors de la définition d’une condition de sélection :</span><span class="sxs-lookup"><span data-stu-id="5fbdc-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="5fbdc-133">La condition de sélection doit spécifier un nom d’un propriété minimum ou un bloc de script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="5fbdc-134">La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="5fbdc-135">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5fbdc-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5fbdc-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fbdc-136">See Also</span></span>

[<span data-ttu-id="5fbdc-137">Élément PropertyName pour SelectionCondition pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5fbdc-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="5fbdc-138">Élément ScriptBlock pour SelectionCondition pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5fbdc-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="5fbdc-139">Élément SelectionSetName pour SelectionCondition pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5fbdc-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="5fbdc-140">Élément TypeName pour SelectionCondition pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5fbdc-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="5fbdc-141">Élément EntrySelectedBy pour CustomEntry pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5fbdc-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="5fbdc-142">Écriture d’un mise en forme de Windows PowerShell et de Types de fichier</span><span class="sxs-lookup"><span data-stu-id="5fbdc-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
