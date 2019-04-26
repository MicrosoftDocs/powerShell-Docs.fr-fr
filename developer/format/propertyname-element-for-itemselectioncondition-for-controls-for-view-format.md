---
title: Élément PropertyName pour ItemSelectionCondition pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075849"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="218aa-102">PropertyName, élément pour ItemSelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="218aa-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="218aa-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="218aa-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="218aa-104">Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie, et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="218aa-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="218aa-105">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="218aa-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="218aa-106">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour les contrôles d’élément de ExpressionBinding vue (Format) pour CustomItem pour les contrôles de vue (Format) Élément ItemSelectionCondition de ExpressionBinding pour les contrôles d’élément de PropertyName vue (Format) pour ItemSelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="218aa-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="218aa-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="218aa-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="218aa-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="218aa-108">Attributes and Elements</span></span>

<span data-ttu-id="218aa-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="218aa-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="218aa-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="218aa-110">Attributes</span></span>

<span data-ttu-id="218aa-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="218aa-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="218aa-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="218aa-112">Child Elements</span></span>

<span data-ttu-id="218aa-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="218aa-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="218aa-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="218aa-114">Parent Elements</span></span>

|<span data-ttu-id="218aa-115">Élément</span><span class="sxs-lookup"><span data-stu-id="218aa-115">Element</span></span>|<span data-ttu-id="218aa-116">Description</span><span class="sxs-lookup"><span data-stu-id="218aa-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="218aa-117">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="218aa-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="218aa-118">Définit la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="218aa-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="218aa-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="218aa-119">Text Value</span></span>

<span data-ttu-id="218aa-120">Spécifiez le nom de la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="218aa-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="218aa-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="218aa-121">Remarks</span></span>

<span data-ttu-id="218aa-122">Si cet élément est utilisé, vous ne pouvez pas spécifier le [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) élément lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="218aa-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="218aa-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="218aa-123">See Also</span></span>

[<span data-ttu-id="218aa-124">Élément ScriptBlock pour ItemSelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="218aa-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="218aa-125">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="218aa-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="218aa-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="218aa-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
