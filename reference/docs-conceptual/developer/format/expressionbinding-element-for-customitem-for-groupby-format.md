---
title: Élément ExpressionBinding pour CustomItem pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368628"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="3c648-102">ExpressionBinding, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3c648-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="3c648-103">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="3c648-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="3c648-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="3c648-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="3c648-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format) élément CustomItem pour CustomEntry pour GroupBy (format) élément ExpressionBinding pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3c648-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c648-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c648-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="3c648-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="3c648-107">Attributes and Elements</span></span>

<span data-ttu-id="3c648-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ExpressionBinding`.</span><span class="sxs-lookup"><span data-stu-id="3c648-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c648-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="3c648-109">Attributes</span></span>

<span data-ttu-id="3c648-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="3c648-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c648-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3c648-111">Child Elements</span></span>

|<span data-ttu-id="3c648-112">Élément</span><span class="sxs-lookup"><span data-stu-id="3c648-112">Element</span></span>|<span data-ttu-id="3c648-113">Description</span><span class="sxs-lookup"><span data-stu-id="3c648-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="3c648-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3c648-114">Optional element.</span></span><br /><br /> <span data-ttu-id="3c648-115">Définit un contrôle qui est utilisé par ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="3c648-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="3c648-116">Élément CustomControlName pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3c648-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="3c648-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3c648-117">Optional element.</span></span><br /><br /> <span data-ttu-id="3c648-118">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="3c648-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="3c648-119">[Élément EnumerateCollection pour ExpressionBinding pour GroupBy (format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Élément EnumerateCollection pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3c648-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="3c648-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3c648-120">Optional element.</span></span><br /><br /> <span data-ttu-id="3c648-121">Spécifie que les éléments des collections sont affichés.</span><span class="sxs-lookup"><span data-stu-id="3c648-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="3c648-122">Élément ItemSelectionCondition pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3c648-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="3c648-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3c648-123">Optional element.</span></span><br /><br /> <span data-ttu-id="3c648-124">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="3c648-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="3c648-125">PropertyName, élément de ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3c648-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="3c648-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3c648-126">Optional element.</span></span><br /><br /> <span data-ttu-id="3c648-127">Spécifie la propriété .NET dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="3c648-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="3c648-128">Élément ScriptBlock pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3c648-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="3c648-129">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3c648-129">Optional element.</span></span><br /><br /> <span data-ttu-id="3c648-130">Spécifie le script dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="3c648-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3c648-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3c648-131">Parent Elements</span></span>

|<span data-ttu-id="3c648-132">Élément</span><span class="sxs-lookup"><span data-stu-id="3c648-132">Element</span></span>|<span data-ttu-id="3c648-133">Description</span><span class="sxs-lookup"><span data-stu-id="3c648-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c648-134">Élément CustomItem pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3c648-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="3c648-135">Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="3c648-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="3c648-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c648-136">See Also</span></span>

[<span data-ttu-id="3c648-137">Élément CustomControlName pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3c648-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="3c648-138">Élément EnumerateCollection pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3c648-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="3c648-139">Élément ItemSelectionCondition pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3c648-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="3c648-140">PropertyName, élément de ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3c648-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="3c648-141">Élément ScriptBlock pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3c648-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="3c648-142">Élément CustomItem pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3c648-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="3c648-143">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c648-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)