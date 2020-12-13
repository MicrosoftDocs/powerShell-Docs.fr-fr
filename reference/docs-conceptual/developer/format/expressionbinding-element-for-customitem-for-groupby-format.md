---
ms.date: 09/13/2016
ms.topic: reference
title: ExpressionBinding, élément pour CustomItem pour GroupBy (Format)
description: ExpressionBinding, élément pour CustomItem pour GroupBy (Format)
ms.openlocfilehash: 742d9f081a674dc3ee4c84d600933aaf57b2aa6b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655299"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="99d4b-103">ExpressionBinding, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99d4b-103">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="99d4b-104">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="99d4b-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="99d4b-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="99d4b-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="99d4b-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) CustomItem élément pour CustomEntry pour GroupBy (format) élément ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="99d4b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="99d4b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99d4b-107">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="99d4b-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="99d4b-108">Attributes and Elements</span></span>

<span data-ttu-id="99d4b-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ExpressionBinding` élément.</span><span class="sxs-lookup"><span data-stu-id="99d4b-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="99d4b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="99d4b-110">Attributes</span></span>

<span data-ttu-id="99d4b-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="99d4b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="99d4b-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="99d4b-112">Child Elements</span></span>

|<span data-ttu-id="99d4b-113">Élément</span><span class="sxs-lookup"><span data-stu-id="99d4b-113">Element</span></span>|<span data-ttu-id="99d4b-114">Description</span><span class="sxs-lookup"><span data-stu-id="99d4b-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="99d4b-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="99d4b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="99d4b-116">Définit un contrôle qui est utilisé par ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="99d4b-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="99d4b-117">CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99d4b-117">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="99d4b-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="99d4b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="99d4b-119">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="99d4b-119">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="99d4b-120">[Élément EnumerateCollection pour ExpressionBinding pour GroupBy (format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Élément EnumerateCollection pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="99d4b-120">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="99d4b-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="99d4b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="99d4b-122">Spécifie que les éléments des collections sont affichés.</span><span class="sxs-lookup"><span data-stu-id="99d4b-122">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="99d4b-123">ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99d4b-123">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="99d4b-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="99d4b-124">Optional element.</span></span><br /><br /> <span data-ttu-id="99d4b-125">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="99d4b-125">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="99d4b-126">PropertyName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99d4b-126">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="99d4b-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="99d4b-127">Optional element.</span></span><br /><br /> <span data-ttu-id="99d4b-128">Spécifie la propriété .NET dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="99d4b-128">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="99d4b-129">ScriptBlock, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99d4b-129">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="99d4b-130">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="99d4b-130">Optional element.</span></span><br /><br /> <span data-ttu-id="99d4b-131">Spécifie le script dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="99d4b-131">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="99d4b-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="99d4b-132">Parent Elements</span></span>

|<span data-ttu-id="99d4b-133">Élément</span><span class="sxs-lookup"><span data-stu-id="99d4b-133">Element</span></span>|<span data-ttu-id="99d4b-134">Description</span><span class="sxs-lookup"><span data-stu-id="99d4b-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="99d4b-135">CustomItem, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99d4b-135">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="99d4b-136">Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="99d4b-136">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="99d4b-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99d4b-137">See Also</span></span>

[<span data-ttu-id="99d4b-138">CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99d4b-138">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="99d4b-139">EnumerateCollection, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99d4b-139">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="99d4b-140">ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99d4b-140">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="99d4b-141">PropertyName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99d4b-141">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="99d4b-142">ScriptBlock, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99d4b-142">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="99d4b-143">CustomItem, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99d4b-143">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="99d4b-144">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="99d4b-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
