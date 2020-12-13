---
ms.date: 09/13/2016
ms.topic: reference
title: ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)
description: ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)
ms.openlocfilehash: 6bd3d386ba64b33a1744fcc9e602cf13404765a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648087"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="bb681-103">ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="bb681-103">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="bb681-104">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="bb681-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="bb681-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="bb681-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="bb681-106">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format), élément CustomItem pour CustomEntry pour les contrôles de l’élément de configuration ExpressionBinding pour CustomItem pour les contrôles de configuration (format) ItemSelectionCondition élément pour ExpressionBinding pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bb681-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bb681-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb681-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bb681-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bb681-108">Attributes and Elements</span></span>

<span data-ttu-id="bb681-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ItemSelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="bb681-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bb681-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="bb681-110">Attributes</span></span>

<span data-ttu-id="bb681-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bb681-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bb681-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bb681-112">Child Elements</span></span>

|<span data-ttu-id="bb681-113">Élément</span><span class="sxs-lookup"><span data-stu-id="bb681-113">Element</span></span>|<span data-ttu-id="bb681-114">Description</span><span class="sxs-lookup"><span data-stu-id="bb681-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bb681-115">PropertyName, élément de ItemSelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bb681-115">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="bb681-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="bb681-116">Optional element.</span></span><br /><br /> <span data-ttu-id="bb681-117">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="bb681-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="bb681-118">Élément ScriptBlock pour ItemSelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bb681-118">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="bb681-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="bb681-119">Optional element.</span></span><br /><br /> <span data-ttu-id="bb681-120">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="bb681-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bb681-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bb681-121">Parent Elements</span></span>

|<span data-ttu-id="bb681-122">Élément</span><span class="sxs-lookup"><span data-stu-id="bb681-122">Element</span></span>|<span data-ttu-id="bb681-123">Description</span><span class="sxs-lookup"><span data-stu-id="bb681-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bb681-124">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="bb681-124">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="bb681-125">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="bb681-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bb681-126">Notes</span><span class="sxs-lookup"><span data-stu-id="bb681-126">Remarks</span></span>

<span data-ttu-id="bb681-127">Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="bb681-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb681-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb681-128">See Also</span></span>

[<span data-ttu-id="bb681-129">PropertyName, élément de ItemSelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bb681-129">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="bb681-130">Élément ScriptBlock pour ItemSelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bb681-130">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="bb681-131">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="bb681-131">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="bb681-132">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="bb681-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
