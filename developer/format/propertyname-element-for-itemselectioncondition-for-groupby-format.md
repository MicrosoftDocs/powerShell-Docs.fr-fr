---
title: Élément PropertyName pour ItemSelectionCondition pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858265"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="65c5d-102">PropertyName, élément pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="65c5d-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="65c5d-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="65c5d-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="65c5d-104">Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie, et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="65c5d-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="65c5d-105">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="65c5d-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="65c5d-106">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de CustomItem GroupBy (Format) pour CustomEntry d’élément de ExpressionBinding GroupBy (Format) pour CustomItem d’élément de ItemSelectionCondition GroupBy (Format) pour ExpressionBinding d’élément de PropertyName GroupBy (Format) pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="65c5d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="65c5d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65c5d-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="65c5d-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="65c5d-108">Attributes and Elements</span></span>

<span data-ttu-id="65c5d-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="65c5d-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="65c5d-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="65c5d-110">Attributes</span></span>

<span data-ttu-id="65c5d-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="65c5d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="65c5d-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="65c5d-112">Child Elements</span></span>

<span data-ttu-id="65c5d-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="65c5d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="65c5d-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="65c5d-114">Parent Elements</span></span>

|<span data-ttu-id="65c5d-115">Élément</span><span class="sxs-lookup"><span data-stu-id="65c5d-115">Element</span></span>|<span data-ttu-id="65c5d-116">Description</span><span class="sxs-lookup"><span data-stu-id="65c5d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65c5d-117">Élément ItemSelectionCondition pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="65c5d-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="65c5d-118">Définit la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="65c5d-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="65c5d-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="65c5d-119">Text Value</span></span>

<span data-ttu-id="65c5d-120">Spécifiez le nom de la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="65c5d-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="65c5d-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="65c5d-121">Remarks</span></span>

<span data-ttu-id="65c5d-122">Si cet élément est utilisé, vous ne pouvez pas spécifier le [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) élément lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="65c5d-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="65c5d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65c5d-123">See Also</span></span>

[<span data-ttu-id="65c5d-124">Élément ScriptBlock pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="65c5d-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="65c5d-125">Élément ItemSelectionCondition pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="65c5d-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="65c5d-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="65c5d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
