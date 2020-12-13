---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)
description: PropertyName, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)
ms.openlocfilehash: 860683eb54b2a3579767640c1d3f0937897b8f8e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655121"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="51e6d-103">PropertyName, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="51e6d-103">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="51e6d-104">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="51e6d-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="51e6d-105">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="51e6d-105">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="51e6d-106">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="51e6d-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="51e6d-107">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de CustomItem, élément de configuration (format) pour CustomEntry pour les contrôles de l’élément de configuration ExpressionBinding pour CustomItem pour les contrôles de configuration (format) ItemSelectionCondition, élément pour ExpressionBinding pour les contrôles de configuration (format) PropertyName, élément pour ItemSeclectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="51e6d-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="51e6d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51e6d-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="51e6d-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="51e6d-109">Attributes and Elements</span></span>

<span data-ttu-id="51e6d-110">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="51e6d-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="51e6d-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="51e6d-111">Attributes</span></span>

<span data-ttu-id="51e6d-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="51e6d-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="51e6d-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="51e6d-113">Child Elements</span></span>

<span data-ttu-id="51e6d-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="51e6d-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="51e6d-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="51e6d-115">Parent Elements</span></span>

|<span data-ttu-id="51e6d-116">Élément</span><span class="sxs-lookup"><span data-stu-id="51e6d-116">Element</span></span>|<span data-ttu-id="51e6d-117">Description</span><span class="sxs-lookup"><span data-stu-id="51e6d-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51e6d-118">ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="51e6d-118">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="51e6d-119">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="51e6d-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="51e6d-120">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="51e6d-120">Text Value</span></span>

<span data-ttu-id="51e6d-121">Spécifiez le nom de la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="51e6d-121">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="51e6d-122">Notes</span><span class="sxs-lookup"><span data-stu-id="51e6d-122">Remarks</span></span>

<span data-ttu-id="51e6d-123">Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="51e6d-123">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="51e6d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51e6d-124">See Also</span></span>

[<span data-ttu-id="51e6d-125">ScriptBlock, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="51e6d-125">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="51e6d-126">ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="51e6d-126">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="51e6d-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="51e6d-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
