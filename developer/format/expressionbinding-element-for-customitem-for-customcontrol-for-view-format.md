---
title: Élément ExpressionBinding pour CustomItem pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860685"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="ff13e-102">ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ff13e-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="ff13e-103">Définit les données qui sont affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="ff13e-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="ff13e-104">Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ff13e-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="ff13e-105">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) CustomControl élément pour élément d’affichage (Format) de CustomEntries pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour CustomControl pour la vue ( Format), élément CustomItem pour CustomEntry pour CustomControl pour élément d’affichage (Format) de ExpressionBinding pour CustomItem pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ff13e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ff13e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff13e-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="ff13e-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="ff13e-107">Attributes and Elements</span></span>

<span data-ttu-id="ff13e-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ExpressionBinding` élément.</span><span class="sxs-lookup"><span data-stu-id="ff13e-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ff13e-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="ff13e-109">Attributes</span></span>

<span data-ttu-id="ff13e-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ff13e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ff13e-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ff13e-111">Child Elements</span></span>

|<span data-ttu-id="ff13e-112">Élément</span><span class="sxs-lookup"><span data-stu-id="ff13e-112">Element</span></span>|<span data-ttu-id="ff13e-113">Description</span><span class="sxs-lookup"><span data-stu-id="ff13e-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="ff13e-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ff13e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="ff13e-115">Définit un contrôle qui est utilisé par ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="ff13e-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="ff13e-116">Élément CustomControlName pour ExpressionBinding pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ff13e-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="ff13e-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ff13e-117">Optional element.</span></span><br /><br /> <span data-ttu-id="ff13e-118">Spécifie le nom d’un contrôle commun ou un contrôle d’affichage.</span><span class="sxs-lookup"><span data-stu-id="ff13e-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="ff13e-119">Élément EnumerateCollection pour ExpressionBinding pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ff13e-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="ff13e-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ff13e-120">Optional element.</span></span><br /><br /> <span data-ttu-id="ff13e-121">Spécifié que les éléments des collections sont affichés.</span><span class="sxs-lookup"><span data-stu-id="ff13e-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="ff13e-122">Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ff13e-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="ff13e-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ff13e-123">Optional element.</span></span><br /><br /> <span data-ttu-id="ff13e-124">Définit la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ff13e-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="ff13e-125">Élément PropertyName pour ExpressionBinding pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ff13e-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="ff13e-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ff13e-126">Optional element.</span></span><br /><br /> <span data-ttu-id="ff13e-127">Spécifie la propriété .NET dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="ff13e-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="ff13e-128">Élément ScriptBlock pour ExpressionBinding pour CustomCustomControl pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ff13e-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="ff13e-129">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ff13e-129">Optional element.</span></span><br /><br /> <span data-ttu-id="ff13e-130">Spécifie le script dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="ff13e-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ff13e-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ff13e-131">Parent Elements</span></span>

|<span data-ttu-id="ff13e-132">Élément</span><span class="sxs-lookup"><span data-stu-id="ff13e-132">Element</span></span>|<span data-ttu-id="ff13e-133">Description</span><span class="sxs-lookup"><span data-stu-id="ff13e-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff13e-134">Élément CustomItem pour CustomEntry pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ff13e-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="ff13e-135">Définit les données affichées par la vue de contrôle personnalisé et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="ff13e-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ff13e-136">Remarques</span><span class="sxs-lookup"><span data-stu-id="ff13e-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="ff13e-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff13e-137">See Also</span></span>

[<span data-ttu-id="ff13e-138">Élément CustomControlName pour ExpressionBinding pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ff13e-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ff13e-139">Élément EnumerateCollection pour ExpressionBinding pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ff13e-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ff13e-140">Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ff13e-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="ff13e-141">Élément PropertyName pour ExpressionBinding pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ff13e-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ff13e-142">Élément ScriptBlock pour ExpressionBinding pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ff13e-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ff13e-143">Élément CustomItem pour CustomEntry pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ff13e-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ff13e-144">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff13e-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
