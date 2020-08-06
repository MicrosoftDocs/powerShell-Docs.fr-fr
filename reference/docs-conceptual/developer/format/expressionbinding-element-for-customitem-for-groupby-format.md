---
title: Élément ExpressionBinding pour CustomItem pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5b0017e487aab4ffcbf901cd44aad9b275b22832
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773723"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="13791-102">ExpressionBinding, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="13791-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="13791-103">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="13791-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="13791-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="13791-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="13791-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) CustomItem élément pour CustomEntry pour GroupBy (format) élément ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="13791-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="13791-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13791-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="13791-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="13791-107">Attributes and Elements</span></span>

<span data-ttu-id="13791-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ExpressionBinding` élément.</span><span class="sxs-lookup"><span data-stu-id="13791-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="13791-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="13791-109">Attributes</span></span>

<span data-ttu-id="13791-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="13791-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="13791-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="13791-111">Child Elements</span></span>

|<span data-ttu-id="13791-112">Élément</span><span class="sxs-lookup"><span data-stu-id="13791-112">Element</span></span>|<span data-ttu-id="13791-113">Description</span><span class="sxs-lookup"><span data-stu-id="13791-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="13791-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="13791-114">Optional element.</span></span><br /><br /> <span data-ttu-id="13791-115">Définit un contrôle qui est utilisé par ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="13791-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="13791-116">CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="13791-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="13791-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="13791-117">Optional element.</span></span><br /><br /> <span data-ttu-id="13791-118">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="13791-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="13791-119">[Élément EnumerateCollection pour ExpressionBinding pour GroupBy (format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Élément EnumerateCollection pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="13791-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="13791-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="13791-120">Optional element.</span></span><br /><br /> <span data-ttu-id="13791-121">Spécifie que les éléments des collections sont affichés.</span><span class="sxs-lookup"><span data-stu-id="13791-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="13791-122">ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="13791-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="13791-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="13791-123">Optional element.</span></span><br /><br /> <span data-ttu-id="13791-124">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="13791-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="13791-125">PropertyName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="13791-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="13791-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="13791-126">Optional element.</span></span><br /><br /> <span data-ttu-id="13791-127">Spécifie la propriété .NET dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="13791-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="13791-128">ScriptBlock, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="13791-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="13791-129">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="13791-129">Optional element.</span></span><br /><br /> <span data-ttu-id="13791-130">Spécifie le script dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="13791-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="13791-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="13791-131">Parent Elements</span></span>

|<span data-ttu-id="13791-132">Élément</span><span class="sxs-lookup"><span data-stu-id="13791-132">Element</span></span>|<span data-ttu-id="13791-133">Description</span><span class="sxs-lookup"><span data-stu-id="13791-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13791-134">CustomItem, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="13791-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="13791-135">Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="13791-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="13791-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13791-136">See Also</span></span>

[<span data-ttu-id="13791-137">CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="13791-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="13791-138">EnumerateCollection, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="13791-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="13791-139">ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="13791-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="13791-140">PropertyName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="13791-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="13791-141">ScriptBlock, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="13791-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="13791-142">CustomItem, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="13791-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="13791-143">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="13791-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
