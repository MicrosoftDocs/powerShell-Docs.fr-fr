---
ms.date: 09/13/2016
ms.topic: reference
title: ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour View (Format)
description: ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour View (Format)
ms.openlocfilehash: adbe747bdb4f6c1d180e5b630247de0fd3d72b85
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648057"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="47a89-103">ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="47a89-103">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="47a89-104">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="47a89-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="47a89-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="47a89-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="47a89-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément CustomEntries View (format) pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour les contrôles de l’élément View (format) CustomItem pour CustomEntry pour les contrôles pour l’élément View (format) ExpressionBinding pour les contrôles pour la vue (format) CustomItem élément de ItemSelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="47a89-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="47a89-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47a89-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="47a89-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="47a89-108">Attributes and Elements</span></span>

<span data-ttu-id="47a89-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ItemSelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="47a89-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="47a89-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="47a89-110">Attributes</span></span>

<span data-ttu-id="47a89-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="47a89-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="47a89-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="47a89-112">Child Elements</span></span>

|<span data-ttu-id="47a89-113">Élément</span><span class="sxs-lookup"><span data-stu-id="47a89-113">Element</span></span>|<span data-ttu-id="47a89-114">Description</span><span class="sxs-lookup"><span data-stu-id="47a89-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47a89-115">PropertyName, élément pour ItemSelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="47a89-115">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="47a89-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="47a89-116">Optional element.</span></span><br /><br /> <span data-ttu-id="47a89-117">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="47a89-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="47a89-118">ScriptBlock, élément pour ItemSelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="47a89-118">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="47a89-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="47a89-119">Optional element.</span></span><br /><br /> <span data-ttu-id="47a89-120">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="47a89-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="47a89-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="47a89-121">Parent Elements</span></span>

|<span data-ttu-id="47a89-122">Élément</span><span class="sxs-lookup"><span data-stu-id="47a89-122">Element</span></span>|<span data-ttu-id="47a89-123">Description</span><span class="sxs-lookup"><span data-stu-id="47a89-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47a89-124">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="47a89-124">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="47a89-125">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="47a89-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="47a89-126">Notes</span><span class="sxs-lookup"><span data-stu-id="47a89-126">Remarks</span></span>

<span data-ttu-id="47a89-127">Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="47a89-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="47a89-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47a89-128">See Also</span></span>

[<span data-ttu-id="47a89-129">PropertyName, élément pour ItemSelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="47a89-129">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="47a89-130">ScriptBlock, élément pour ItemSelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="47a89-130">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="47a89-131">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="47a89-131">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="47a89-132">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="47a89-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
