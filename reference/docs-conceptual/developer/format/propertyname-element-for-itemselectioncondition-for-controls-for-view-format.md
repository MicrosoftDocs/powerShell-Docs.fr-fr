---
title: Élément PropertyName pour ItemSelectionCondition pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c6517b8f63e0511ce071926ac3ac39ba82e7ed21
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783481"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="4abea-102">PropertyName, élément pour ItemSelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="4abea-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="4abea-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="4abea-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="4abea-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="4abea-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="4abea-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="4abea-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="4abea-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour la vue (format) élément CustomControl pour le contrôle des contrôles pour l’élément View (format) CustomEntries pour CustomControl pour l’élément CustomEntry (format) de la vue CustomEntries pour les contrôles pour l’élément CustomItem View (format) pour CustomEntry pour les contrôles pour l’élément ExpressionBinding (format) View pour CustomItem pour les contrôles pour l’élément View (format) ItemSelectionCondition de l’élément ExpressionBinding pour les contrôles pour l’élément View (format) PropertyName pour ItemSelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="4abea-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4abea-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4abea-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4abea-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4abea-108">Attributes and Elements</span></span>

<span data-ttu-id="4abea-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="4abea-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4abea-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="4abea-110">Attributes</span></span>

<span data-ttu-id="4abea-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4abea-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4abea-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4abea-112">Child Elements</span></span>

<span data-ttu-id="4abea-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4abea-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4abea-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4abea-114">Parent Elements</span></span>

|<span data-ttu-id="4abea-115">Élément</span><span class="sxs-lookup"><span data-stu-id="4abea-115">Element</span></span>|<span data-ttu-id="4abea-116">Description</span><span class="sxs-lookup"><span data-stu-id="4abea-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4abea-117">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="4abea-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="4abea-118">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="4abea-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4abea-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="4abea-119">Text Value</span></span>

<span data-ttu-id="4abea-120">Spécifiez le nom de la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="4abea-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="4abea-121">Notes</span><span class="sxs-lookup"><span data-stu-id="4abea-121">Remarks</span></span>

<span data-ttu-id="4abea-122">Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="4abea-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="4abea-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4abea-123">See Also</span></span>

[<span data-ttu-id="4abea-124">ScriptBlock, élément pour ItemSelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="4abea-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="4abea-125">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="4abea-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="4abea-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="4abea-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
