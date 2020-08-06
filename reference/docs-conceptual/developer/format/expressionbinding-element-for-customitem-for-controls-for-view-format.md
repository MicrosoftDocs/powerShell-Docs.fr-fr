---
title: Élément ExpressionBinding pour CustomItem pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6760bf17be58411948ecb3437bf18bce40073954
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773808"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="138d3-102">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="138d3-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="138d3-103">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="138d3-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="138d3-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="138d3-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="138d3-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour View (format), élément CustomEntry pour CustomEntries pour les contrôles pour l’élément CustomItem (format) View pour CustomEntry pour les contrôles pour l’élément View (format) ExpressionBinding pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="138d3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="138d3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="138d3-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="138d3-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="138d3-107">Attributes and Elements</span></span>

<span data-ttu-id="138d3-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ExpressionBinding` élément.</span><span class="sxs-lookup"><span data-stu-id="138d3-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="138d3-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="138d3-109">Attributes</span></span>

<span data-ttu-id="138d3-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="138d3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="138d3-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="138d3-111">Child Elements</span></span>

|<span data-ttu-id="138d3-112">Élément</span><span class="sxs-lookup"><span data-stu-id="138d3-112">Element</span></span>|<span data-ttu-id="138d3-113">Description</span><span class="sxs-lookup"><span data-stu-id="138d3-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="138d3-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="138d3-114">Optional element.</span></span><br /><br /> <span data-ttu-id="138d3-115">Définit un contrôle qui est utilisé par ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="138d3-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="138d3-116">CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="138d3-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="138d3-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="138d3-117">Optional element.</span></span><br /><br /> <span data-ttu-id="138d3-118">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="138d3-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="138d3-119">EnumerateCollection, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="138d3-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="138d3-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="138d3-120">Optional element.</span></span><br /><br /> <span data-ttu-id="138d3-121">Spécifie que les éléments des collections sont affichés.</span><span class="sxs-lookup"><span data-stu-id="138d3-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="138d3-122">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="138d3-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="138d3-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="138d3-123">Optional element.</span></span><br /><br /> <span data-ttu-id="138d3-124">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="138d3-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="138d3-125">PropertyName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="138d3-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="138d3-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="138d3-126">Optional element.</span></span><br /><br /> <span data-ttu-id="138d3-127">Spécifie la propriété .NET dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="138d3-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="138d3-128">ScriptBlock, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="138d3-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="138d3-129">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="138d3-129">Optional element.</span></span><br /><br /> <span data-ttu-id="138d3-130">Spécifie le script dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="138d3-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="138d3-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="138d3-131">Parent Elements</span></span>

|<span data-ttu-id="138d3-132">Élément</span><span class="sxs-lookup"><span data-stu-id="138d3-132">Element</span></span>|<span data-ttu-id="138d3-133">Description</span><span class="sxs-lookup"><span data-stu-id="138d3-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="138d3-134">CustomItem, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="138d3-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="138d3-135">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="138d3-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="138d3-136">Notes</span><span class="sxs-lookup"><span data-stu-id="138d3-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="138d3-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="138d3-137">See Also</span></span>

[<span data-ttu-id="138d3-138">CustomItem, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="138d3-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="138d3-139">CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="138d3-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="138d3-140">EnumerateCollection, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="138d3-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="138d3-141">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="138d3-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="138d3-142">PropertyName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="138d3-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="138d3-143">ScriptBlock, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="138d3-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="138d3-144">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="138d3-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
