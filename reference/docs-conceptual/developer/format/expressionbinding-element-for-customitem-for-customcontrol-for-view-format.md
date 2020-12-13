---
ms.date: 09/13/2016
ms.topic: reference
title: ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)
description: ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)
ms.openlocfilehash: 8f4bfef4f6c65c6dabc7a776dda1083bac11fdf7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648191"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="cc90b-103">ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cc90b-103">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="cc90b-104">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="cc90b-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="cc90b-105">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="cc90b-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="cc90b-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour la vue (format) élément CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour CustomControl pour la vue (format) CustomItem élément pour CustomControl pour la vue (format), élément CustomEntry pour CustomControl pour la vue (format)</span><span class="sxs-lookup"><span data-stu-id="cc90b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cc90b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc90b-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="cc90b-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cc90b-108">Attributes and Elements</span></span>

<span data-ttu-id="cc90b-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ExpressionBinding` élément.</span><span class="sxs-lookup"><span data-stu-id="cc90b-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cc90b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="cc90b-110">Attributes</span></span>

<span data-ttu-id="cc90b-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cc90b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cc90b-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cc90b-112">Child Elements</span></span>

|<span data-ttu-id="cc90b-113">Élément</span><span class="sxs-lookup"><span data-stu-id="cc90b-113">Element</span></span>|<span data-ttu-id="cc90b-114">Description</span><span class="sxs-lookup"><span data-stu-id="cc90b-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="cc90b-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cc90b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="cc90b-116">Définit un contrôle qui est utilisé par ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="cc90b-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="cc90b-117">CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cc90b-117">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="cc90b-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cc90b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="cc90b-119">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="cc90b-119">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="cc90b-120">EnumerateCollection, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cc90b-120">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="cc90b-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cc90b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="cc90b-122">Spécifie que les éléments des collections sont affichés.</span><span class="sxs-lookup"><span data-stu-id="cc90b-122">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="cc90b-123">Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="cc90b-123">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="cc90b-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cc90b-124">Optional element.</span></span><br /><br /> <span data-ttu-id="cc90b-125">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="cc90b-125">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="cc90b-126">PropertyName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cc90b-126">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="cc90b-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cc90b-127">Optional element.</span></span><br /><br /> <span data-ttu-id="cc90b-128">Spécifie la propriété .NET dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="cc90b-128">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="cc90b-129">Élément ScriptBlock pour ExpressionBinding pour CustomCustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="cc90b-129">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="cc90b-130">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cc90b-130">Optional element.</span></span><br /><br /> <span data-ttu-id="cc90b-131">Spécifie le script dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="cc90b-131">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cc90b-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cc90b-132">Parent Elements</span></span>

|<span data-ttu-id="cc90b-133">Élément</span><span class="sxs-lookup"><span data-stu-id="cc90b-133">Element</span></span>|<span data-ttu-id="cc90b-134">Description</span><span class="sxs-lookup"><span data-stu-id="cc90b-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc90b-135">CustomItem, élément pour CustomEntry pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cc90b-135">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="cc90b-136">Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="cc90b-136">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cc90b-137">Notes</span><span class="sxs-lookup"><span data-stu-id="cc90b-137">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="cc90b-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc90b-138">See Also</span></span>

[<span data-ttu-id="cc90b-139">CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cc90b-139">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cc90b-140">EnumerateCollection, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cc90b-140">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cc90b-141">Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="cc90b-141">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="cc90b-142">PropertyName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cc90b-142">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cc90b-143">ScriptBlock, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cc90b-143">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cc90b-144">CustomItem, élément pour CustomEntry pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cc90b-144">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cc90b-145">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="cc90b-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
