---
title: Élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368448"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="6ac96-102">SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="6ac96-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="6ac96-103">Définit une condition qui doit exister pour qu’une définition de contrôle commun soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="6ac96-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="6ac96-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="6ac96-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="6ac96-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour les contrôles pour Configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément EntrySelectedBy pour CustomEntry pour les contrôles pour la configuration (format) SelectionCondition, élément pour EntrySelectedBy pour CustomEntry pour Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="6ac96-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6ac96-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ac96-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6ac96-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="6ac96-107">Attributes and Elements</span></span>

<span data-ttu-id="6ac96-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="6ac96-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6ac96-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="6ac96-109">Attributes</span></span>

<span data-ttu-id="6ac96-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="6ac96-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6ac96-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6ac96-111">Child Elements</span></span>

|<span data-ttu-id="6ac96-112">Élément</span><span class="sxs-lookup"><span data-stu-id="6ac96-112">Element</span></span>|<span data-ttu-id="6ac96-113">Description</span><span class="sxs-lookup"><span data-stu-id="6ac96-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ac96-114">PropertyName, élément de SelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="6ac96-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="6ac96-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6ac96-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6ac96-116">Spécifie une propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="6ac96-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="6ac96-117">Élément ScriptBlock pour SelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="6ac96-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="6ac96-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6ac96-118">Optional element.</span></span><br /><br /> <span data-ttu-id="6ac96-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="6ac96-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="6ac96-120">Élément SelectionSetName pour SelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="6ac96-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="6ac96-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6ac96-121">Optional element.</span></span><br /><br /> <span data-ttu-id="6ac96-122">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="6ac96-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="6ac96-123">Élément TypeName pour SelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="6ac96-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="6ac96-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6ac96-124">Optional element.</span></span><br /><br /> <span data-ttu-id="6ac96-125">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="6ac96-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6ac96-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6ac96-126">Parent Elements</span></span>

|<span data-ttu-id="6ac96-127">Élément</span><span class="sxs-lookup"><span data-stu-id="6ac96-127">Element</span></span>|<span data-ttu-id="6ac96-128">Description</span><span class="sxs-lookup"><span data-stu-id="6ac96-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ac96-129">Élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="6ac96-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="6ac96-130">Définit les types .NET qui utilisent cette entrée de la définition de contrôle commune.</span><span class="sxs-lookup"><span data-stu-id="6ac96-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6ac96-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="6ac96-131">Remarks</span></span>

<span data-ttu-id="6ac96-132">Les instructions suivantes doivent être suivies lors de la définition d’une condition de sélection :</span><span class="sxs-lookup"><span data-stu-id="6ac96-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="6ac96-133">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="6ac96-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="6ac96-134">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="6ac96-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="6ac96-135">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6ac96-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6ac96-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ac96-136">See Also</span></span>

[<span data-ttu-id="6ac96-137">PropertyName, élément de SelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="6ac96-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="6ac96-138">Élément ScriptBlock pour SelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="6ac96-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="6ac96-139">Élément SelectionSetName pour SelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="6ac96-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="6ac96-140">Élément TypeName pour SelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="6ac96-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="6ac96-141">Élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="6ac96-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="6ac96-142">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ac96-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
