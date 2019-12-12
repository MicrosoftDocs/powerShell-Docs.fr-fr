---
title: Élément ExpressionBinding pour CustomItem pour les contrôles pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363778"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="c950b-102">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="c950b-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="c950b-103">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="c950b-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="c950b-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="c950b-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c950b-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour les contrôles pour l’élément CustomItem (format) View pour CustomEntry pour les contrôles pour l’élément View (format) ExpressionBinding pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="c950b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c950b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c950b-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="c950b-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="c950b-107">Attributes and Elements</span></span>

<span data-ttu-id="c950b-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ExpressionBinding`.</span><span class="sxs-lookup"><span data-stu-id="c950b-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c950b-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="c950b-109">Attributes</span></span>

<span data-ttu-id="c950b-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c950b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c950b-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c950b-111">Child Elements</span></span>

|<span data-ttu-id="c950b-112">Élément</span><span class="sxs-lookup"><span data-stu-id="c950b-112">Element</span></span>|<span data-ttu-id="c950b-113">Description</span><span class="sxs-lookup"><span data-stu-id="c950b-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="c950b-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="c950b-114">Optional element.</span></span><br /><br /> <span data-ttu-id="c950b-115">Définit un contrôle qui est utilisé par ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="c950b-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="c950b-116">Élément CustomControlName pour ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="c950b-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="c950b-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="c950b-117">Optional element.</span></span><br /><br /> <span data-ttu-id="c950b-118">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="c950b-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="c950b-119">Élément EnumerateCollection pour ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="c950b-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="c950b-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="c950b-120">Optional element.</span></span><br /><br /> <span data-ttu-id="c950b-121">Spécifie que les éléments des collections sont affichés.</span><span class="sxs-lookup"><span data-stu-id="c950b-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="c950b-122">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="c950b-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="c950b-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="c950b-123">Optional element.</span></span><br /><br /> <span data-ttu-id="c950b-124">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="c950b-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="c950b-125">Élément PropertyName pour ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="c950b-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="c950b-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="c950b-126">Optional element.</span></span><br /><br /> <span data-ttu-id="c950b-127">Spécifie la propriété .NET dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="c950b-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="c950b-128">Élément ScriptBlock pour ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="c950b-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="c950b-129">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="c950b-129">Optional element.</span></span><br /><br /> <span data-ttu-id="c950b-130">Spécifie le script dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="c950b-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c950b-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c950b-131">Parent Elements</span></span>

|<span data-ttu-id="c950b-132">Élément</span><span class="sxs-lookup"><span data-stu-id="c950b-132">Element</span></span>|<span data-ttu-id="c950b-133">Description</span><span class="sxs-lookup"><span data-stu-id="c950b-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c950b-134">Élément CustomItem pour CustomEntry pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="c950b-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="c950b-135">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="c950b-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c950b-136">Remarks</span><span class="sxs-lookup"><span data-stu-id="c950b-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="c950b-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c950b-137">See Also</span></span>

[<span data-ttu-id="c950b-138">Élément CustomItem pour CustomEntry pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="c950b-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="c950b-139">Élément CustomControlName pour ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="c950b-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="c950b-140">Élément EnumerateCollection pour ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="c950b-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="c950b-141">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="c950b-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="c950b-142">Élément PropertyName pour ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="c950b-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="c950b-143">Élément ScriptBlock pour ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="c950b-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="c950b-144">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="c950b-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
