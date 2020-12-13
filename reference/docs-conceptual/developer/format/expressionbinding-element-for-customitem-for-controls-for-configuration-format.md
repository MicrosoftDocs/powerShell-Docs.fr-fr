---
ms.date: 09/13/2016
ms.topic: reference
title: ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)
description: ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)
ms.openlocfilehash: 1abcf2173e18d45839161b4c7e59f1ad238f81a1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655336"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="aee99-103">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="aee99-103">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="aee99-104">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="aee99-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="aee99-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="aee99-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="aee99-106">Élément de configuration (format) Controls, élément de configuration (format), élément de contrôle pour la configuration (format) CustomControl, élément de Control pour configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément CustomItem pour CustomEntry pour les contrôles pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="aee99-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aee99-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aee99-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="aee99-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="aee99-108">Attributes and Elements</span></span>

<span data-ttu-id="aee99-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ExpressionBinding` élément.</span><span class="sxs-lookup"><span data-stu-id="aee99-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aee99-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="aee99-110">Attributes</span></span>

<span data-ttu-id="aee99-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="aee99-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aee99-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="aee99-112">Child Elements</span></span>

|<span data-ttu-id="aee99-113">Élément</span><span class="sxs-lookup"><span data-stu-id="aee99-113">Element</span></span>|<span data-ttu-id="aee99-114">Description</span><span class="sxs-lookup"><span data-stu-id="aee99-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="aee99-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="aee99-115">Optional element.</span></span><br /><br /> <span data-ttu-id="aee99-116">Définit un contrôle qui est utilisé par ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="aee99-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="aee99-117">CustomControlName, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="aee99-117">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="aee99-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="aee99-118">Optional element.</span></span><br /><br /> <span data-ttu-id="aee99-119">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="aee99-119">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="aee99-120">EnumerateCollection, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="aee99-120">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="aee99-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="aee99-121">Optional element.</span></span><br /><br /> <span data-ttu-id="aee99-122">Spécifie que les éléments des collections sont affichés par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="aee99-122">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="aee99-123">ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="aee99-123">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="aee99-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="aee99-124">Optional element.</span></span><br /><br /> <span data-ttu-id="aee99-125">Définit la condition qui doit exister pour que ce contrôle commun soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="aee99-125">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="aee99-126">PropertyName, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="aee99-126">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="aee99-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="aee99-127">Optional element.</span></span><br /><br /> <span data-ttu-id="aee99-128">Spécifie la propriété .NET dont la valeur est affichée par le contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="aee99-128">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="aee99-129">ScriptBlock, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="aee99-129">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="aee99-130">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="aee99-130">Optional element.</span></span><br /><br /> <span data-ttu-id="aee99-131">Spécifie le script dont la valeur est affichée par le contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="aee99-131">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="aee99-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="aee99-132">Parent Elements</span></span>

|<span data-ttu-id="aee99-133">Élément</span><span class="sxs-lookup"><span data-stu-id="aee99-133">Element</span></span>|<span data-ttu-id="aee99-134">Description</span><span class="sxs-lookup"><span data-stu-id="aee99-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aee99-135">Élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="aee99-135">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="aee99-136">Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="aee99-136">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="aee99-137">Notes</span><span class="sxs-lookup"><span data-stu-id="aee99-137">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="aee99-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aee99-138">See Also</span></span>

[<span data-ttu-id="aee99-139">Élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="aee99-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="aee99-140">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="aee99-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
