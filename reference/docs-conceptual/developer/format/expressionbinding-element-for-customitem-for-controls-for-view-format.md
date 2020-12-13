---
ms.date: 09/13/2016
ms.topic: reference
title: ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)
description: ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)
ms.openlocfilehash: da87bb26d21dcb051871e67997cc3fba7ce73c74
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649900"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="3f55e-103">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3f55e-103">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="3f55e-104">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="3f55e-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="3f55e-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="3f55e-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="3f55e-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour View (format), élément CustomEntry pour CustomEntries pour les contrôles pour l’élément CustomItem (format) View pour CustomEntry pour les contrôles pour l’élément View (format) ExpressionBinding pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3f55e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3f55e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f55e-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="3f55e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3f55e-108">Attributes and Elements</span></span>

<span data-ttu-id="3f55e-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ExpressionBinding` élément.</span><span class="sxs-lookup"><span data-stu-id="3f55e-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3f55e-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="3f55e-110">Attributes</span></span>

<span data-ttu-id="3f55e-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3f55e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3f55e-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3f55e-112">Child Elements</span></span>

|<span data-ttu-id="3f55e-113">Élément</span><span class="sxs-lookup"><span data-stu-id="3f55e-113">Element</span></span>|<span data-ttu-id="3f55e-114">Description</span><span class="sxs-lookup"><span data-stu-id="3f55e-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="3f55e-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3f55e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3f55e-116">Définit un contrôle qui est utilisé par ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="3f55e-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="3f55e-117">CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3f55e-117">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="3f55e-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3f55e-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3f55e-119">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="3f55e-119">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="3f55e-120">EnumerateCollection, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3f55e-120">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="3f55e-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3f55e-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3f55e-122">Spécifie que les éléments des collections sont affichés.</span><span class="sxs-lookup"><span data-stu-id="3f55e-122">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="3f55e-123">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3f55e-123">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="3f55e-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3f55e-124">Optional element.</span></span><br /><br /> <span data-ttu-id="3f55e-125">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="3f55e-125">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="3f55e-126">PropertyName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3f55e-126">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="3f55e-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3f55e-127">Optional element.</span></span><br /><br /> <span data-ttu-id="3f55e-128">Spécifie la propriété .NET dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="3f55e-128">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="3f55e-129">ScriptBlock, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3f55e-129">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="3f55e-130">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3f55e-130">Optional element.</span></span><br /><br /> <span data-ttu-id="3f55e-131">Spécifie le script dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="3f55e-131">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3f55e-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3f55e-132">Parent Elements</span></span>

|<span data-ttu-id="3f55e-133">Élément</span><span class="sxs-lookup"><span data-stu-id="3f55e-133">Element</span></span>|<span data-ttu-id="3f55e-134">Description</span><span class="sxs-lookup"><span data-stu-id="3f55e-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3f55e-135">CustomItem, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3f55e-135">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="3f55e-136">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="3f55e-136">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3f55e-137">Notes</span><span class="sxs-lookup"><span data-stu-id="3f55e-137">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="3f55e-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f55e-138">See Also</span></span>

[<span data-ttu-id="3f55e-139">CustomItem, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3f55e-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="3f55e-140">CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3f55e-140">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="3f55e-141">EnumerateCollection, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3f55e-141">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="3f55e-142">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3f55e-142">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="3f55e-143">PropertyName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3f55e-143">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="3f55e-144">ScriptBlock, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3f55e-144">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="3f55e-145">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f55e-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
