---
title: Élément ExpressionBinding pour CustomItem pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858295"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="2fe54-102">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="2fe54-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="2fe54-103">Définit les données qui sont affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="2fe54-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="2fe54-104">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="2fe54-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="2fe54-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour les contrôles d’élément de ExpressionBinding vue (Format) pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="2fe54-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2fe54-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fe54-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="2fe54-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="2fe54-107">Attributes and Elements</span></span>

<span data-ttu-id="2fe54-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ExpressionBinding` élément.</span><span class="sxs-lookup"><span data-stu-id="2fe54-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2fe54-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="2fe54-109">Attributes</span></span>

<span data-ttu-id="2fe54-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="2fe54-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2fe54-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2fe54-111">Child Elements</span></span>

|<span data-ttu-id="2fe54-112">Élément</span><span class="sxs-lookup"><span data-stu-id="2fe54-112">Element</span></span>|<span data-ttu-id="2fe54-113">Description</span><span class="sxs-lookup"><span data-stu-id="2fe54-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="2fe54-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="2fe54-114">Optional element.</span></span><br /><br /> <span data-ttu-id="2fe54-115">Définit un contrôle qui est utilisé par ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="2fe54-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="2fe54-116">Élément CustomControlName pour ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="2fe54-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="2fe54-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="2fe54-117">Optional element.</span></span><br /><br /> <span data-ttu-id="2fe54-118">Spécifie le nom d’un contrôle commun ou un contrôle d’affichage.</span><span class="sxs-lookup"><span data-stu-id="2fe54-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="2fe54-119">Élément EnumerateCollection pour ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="2fe54-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="2fe54-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="2fe54-120">Optional element.</span></span><br /><br /> <span data-ttu-id="2fe54-121">Spécifie que les éléments des collections sont affichés.</span><span class="sxs-lookup"><span data-stu-id="2fe54-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="2fe54-122">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="2fe54-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="2fe54-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="2fe54-123">Optional element.</span></span><br /><br /> <span data-ttu-id="2fe54-124">Définit la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="2fe54-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="2fe54-125">Élément PropertyName pour ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="2fe54-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="2fe54-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="2fe54-126">Optional element.</span></span><br /><br /> <span data-ttu-id="2fe54-127">Spécifie la propriété .NET dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="2fe54-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="2fe54-128">Élément ScriptBlock pour ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="2fe54-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="2fe54-129">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="2fe54-129">Optional element.</span></span><br /><br /> <span data-ttu-id="2fe54-130">Spécifie le script dont la valeur est affichée par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="2fe54-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2fe54-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2fe54-131">Parent Elements</span></span>

|<span data-ttu-id="2fe54-132">Élément</span><span class="sxs-lookup"><span data-stu-id="2fe54-132">Element</span></span>|<span data-ttu-id="2fe54-133">Description</span><span class="sxs-lookup"><span data-stu-id="2fe54-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2fe54-134">Élément CustomItem pour CustomEntry pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="2fe54-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="2fe54-135">Définit les données affichées par le contrôle et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="2fe54-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2fe54-136">Remarques</span><span class="sxs-lookup"><span data-stu-id="2fe54-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="2fe54-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fe54-137">See Also</span></span>

[<span data-ttu-id="2fe54-138">Élément CustomItem pour CustomEntry pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="2fe54-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="2fe54-139">Élément CustomControlName pour ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="2fe54-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="2fe54-140">Élément EnumerateCollection pour ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="2fe54-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="2fe54-141">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="2fe54-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="2fe54-142">Élément PropertyName pour ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="2fe54-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="2fe54-143">Élément ScriptBlock pour ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="2fe54-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="2fe54-144">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2fe54-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
