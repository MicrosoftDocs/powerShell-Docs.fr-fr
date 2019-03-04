---
title: Élément ExpressionBinding pour CustomItem pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854925"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="b28d5-102">ExpressionBinding, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b28d5-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="b28d5-103">Définit les données qui sont affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="b28d5-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="b28d5-104">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="b28d5-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b28d5-105">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de CustomItem GroupBy (Format) pour CustomEntry d’élément de ExpressionBinding GroupBy (Format) pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b28d5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b28d5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b28d5-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b28d5-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="b28d5-107">Attributes and Elements</span></span>

<span data-ttu-id="b28d5-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ExpressionBinding` élément.</span><span class="sxs-lookup"><span data-stu-id="b28d5-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b28d5-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="b28d5-109">Attributes</span></span>

<span data-ttu-id="b28d5-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="b28d5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b28d5-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b28d5-111">Child Elements</span></span>

|<span data-ttu-id="b28d5-112">Élément</span><span class="sxs-lookup"><span data-stu-id="b28d5-112">Element</span></span>|<span data-ttu-id="b28d5-113">Description</span><span class="sxs-lookup"><span data-stu-id="b28d5-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="b28d5-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b28d5-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b28d5-115">Définit un contrôle qui est utilisé par ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="b28d5-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="b28d5-116">Élément CustomControlName pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b28d5-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b28d5-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b28d5-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b28d5-118">Spécifie le nom d’un contrôle commun ou un contrôle d’affichage.</span><span class="sxs-lookup"><span data-stu-id="b28d5-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="b28d5-119">[Élément EnumerateCollection pour ExpressionBinding pour GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)élément EnumerateCollection pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b28d5-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="b28d5-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b28d5-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b28d5-121">Spécifié que les éléments des collections sont affichés.</span><span class="sxs-lookup"><span data-stu-id="b28d5-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="b28d5-122">Élément ItemSelectionCondition pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b28d5-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b28d5-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b28d5-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b28d5-124">Définit la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b28d5-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="b28d5-125">Élément PropertyName pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b28d5-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b28d5-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b28d5-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b28d5-127">Spécifie la propriété .NET dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="b28d5-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="b28d5-128">Élément ScriptBlock pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b28d5-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b28d5-129">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b28d5-129">Optional element.</span></span><br /><br /> <span data-ttu-id="b28d5-130">Spécifie le script dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="b28d5-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b28d5-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b28d5-131">Parent Elements</span></span>

|<span data-ttu-id="b28d5-132">Élément</span><span class="sxs-lookup"><span data-stu-id="b28d5-132">Element</span></span>|<span data-ttu-id="b28d5-133">Description</span><span class="sxs-lookup"><span data-stu-id="b28d5-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b28d5-134">Élément CustomItem pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b28d5-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="b28d5-135">Définit les données affichées par la vue de contrôle personnalisé et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="b28d5-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b28d5-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b28d5-136">See Also</span></span>

[<span data-ttu-id="b28d5-137">Élément CustomControlName pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b28d5-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b28d5-138">Élément EnumerateCollection pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b28d5-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b28d5-139">Élément ItemSelectionCondition pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b28d5-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b28d5-140">Élément PropertyName pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b28d5-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b28d5-141">Élément ScriptBlock pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b28d5-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b28d5-142">Élément CustomItem pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b28d5-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="b28d5-143">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b28d5-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
