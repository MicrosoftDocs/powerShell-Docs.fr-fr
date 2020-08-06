---
title: PropertyName, élément de ItemSelectionCondition pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f6d671035bfd2ef6323b638fdd951bb020bd6548
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780880"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="e2bf0-102">PropertyName, élément pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e2bf0-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="e2bf0-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e2bf0-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e2bf0-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e2bf0-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="e2bf0-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="e2bf0-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e2bf0-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour l’élément GroupBy (format) CustomItem pour CustomEntry pour GroupBy (format) élément ExpressionBinding pour CustomItem pour l’élément GroupBy (format) ItemSelectionCondition pour ExpressionBinding pour l’élément GroupBy (format) PropertyName pour ItemSelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e2bf0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e2bf0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2bf0-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2bf0-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e2bf0-108">Attributes and Elements</span></span>

<span data-ttu-id="e2bf0-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="e2bf0-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2bf0-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="e2bf0-110">Attributes</span></span>

<span data-ttu-id="e2bf0-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e2bf0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2bf0-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e2bf0-112">Child Elements</span></span>

<span data-ttu-id="e2bf0-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e2bf0-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e2bf0-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e2bf0-114">Parent Elements</span></span>

|<span data-ttu-id="e2bf0-115">Élément</span><span class="sxs-lookup"><span data-stu-id="e2bf0-115">Element</span></span>|<span data-ttu-id="e2bf0-116">Description</span><span class="sxs-lookup"><span data-stu-id="e2bf0-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2bf0-117">ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e2bf0-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="e2bf0-118">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="e2bf0-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e2bf0-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="e2bf0-119">Text Value</span></span>

<span data-ttu-id="e2bf0-120">Spécifiez le nom de la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e2bf0-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2bf0-121">Notes</span><span class="sxs-lookup"><span data-stu-id="e2bf0-121">Remarks</span></span>

<span data-ttu-id="e2bf0-122">Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="e2bf0-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2bf0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2bf0-123">See Also</span></span>

[<span data-ttu-id="e2bf0-124">ScriptBlock, élément pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e2bf0-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="e2bf0-125">ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e2bf0-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="e2bf0-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2bf0-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
