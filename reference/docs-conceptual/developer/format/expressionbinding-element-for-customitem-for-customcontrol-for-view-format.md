---
title: Élément ExpressionBinding pour CustomItem pour CustomControl pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1885a2820c0cb250aa6fda80544f58d06136cfeb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773791"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="e8b0b-102">ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e8b0b-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="e8b0b-103">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="e8b0b-104">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e8b0b-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour la vue (format) élément CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour CustomControl pour la vue (format) CustomItem élément pour CustomControl pour la vue (format), élément CustomEntry pour CustomControl pour la vue (format)</span><span class="sxs-lookup"><span data-stu-id="e8b0b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e8b0b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8b0b-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e8b0b-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e8b0b-107">Attributes and Elements</span></span>

<span data-ttu-id="e8b0b-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ExpressionBinding` élément.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e8b0b-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="e8b0b-109">Attributes</span></span>

<span data-ttu-id="e8b0b-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e8b0b-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e8b0b-111">Child Elements</span></span>

|<span data-ttu-id="e8b0b-112">Élément</span><span class="sxs-lookup"><span data-stu-id="e8b0b-112">Element</span></span>|<span data-ttu-id="e8b0b-113">Description</span><span class="sxs-lookup"><span data-stu-id="e8b0b-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="e8b0b-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e8b0b-115">Définit un contrôle qui est utilisé par ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="e8b0b-116">CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e8b0b-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="e8b0b-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e8b0b-118">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="e8b0b-119">EnumerateCollection, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e8b0b-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="e8b0b-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e8b0b-121">Spécifie que les éléments des collections sont affichés.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="e8b0b-122">Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="e8b0b-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="e8b0b-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-123">Optional element.</span></span><br /><br /> <span data-ttu-id="e8b0b-124">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="e8b0b-125">PropertyName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e8b0b-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="e8b0b-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-126">Optional element.</span></span><br /><br /> <span data-ttu-id="e8b0b-127">Spécifie la propriété .NET dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="e8b0b-128">Élément ScriptBlock pour ExpressionBinding pour CustomCustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="e8b0b-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="e8b0b-129">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-129">Optional element.</span></span><br /><br /> <span data-ttu-id="e8b0b-130">Spécifie le script dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e8b0b-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e8b0b-131">Parent Elements</span></span>

|<span data-ttu-id="e8b0b-132">Élément</span><span class="sxs-lookup"><span data-stu-id="e8b0b-132">Element</span></span>|<span data-ttu-id="e8b0b-133">Description</span><span class="sxs-lookup"><span data-stu-id="e8b0b-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e8b0b-134">CustomItem, élément pour CustomEntry pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e8b0b-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="e8b0b-135">Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="e8b0b-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e8b0b-136">Notes</span><span class="sxs-lookup"><span data-stu-id="e8b0b-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e8b0b-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8b0b-137">See Also</span></span>

[<span data-ttu-id="e8b0b-138">CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e8b0b-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e8b0b-139">EnumerateCollection, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e8b0b-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e8b0b-140">Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="e8b0b-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="e8b0b-141">PropertyName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e8b0b-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e8b0b-142">ScriptBlock, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e8b0b-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e8b0b-143">CustomItem, élément pour CustomEntry pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e8b0b-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e8b0b-144">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8b0b-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
