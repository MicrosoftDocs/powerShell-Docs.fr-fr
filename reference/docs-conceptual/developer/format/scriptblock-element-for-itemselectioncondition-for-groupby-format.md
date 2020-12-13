---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour ItemSelectionCondition pour GroupBy (Format)
description: ScriptBlock, élément pour ItemSelectionCondition pour GroupBy (Format)
ms.openlocfilehash: fe366fa31b93e8d69409cc49c3fe2c350d4d06d9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665095"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="e5c7b-103">ScriptBlock, élément pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e5c7b-103">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="e5c7b-104">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e5c7b-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="e5c7b-105">Lorsque ce script est évalué à `true` , la condition est remplie et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e5c7b-105">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="e5c7b-106">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="e5c7b-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e5c7b-107">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour l’élément GroupBy (format) CustomItem pour CustomEntry pour GroupBy (format) élément ExpressionBinding pour CustomItem pour l’élément GroupBy (format) ItemSelectionCondition pour ExpressionBinding pour l’élément ScriptBlock GroupBy (format) pour ItemSelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e5c7b-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5c7b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5c7b-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5c7b-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e5c7b-109">Attributes and Elements</span></span>

<span data-ttu-id="e5c7b-110">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="e5c7b-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5c7b-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="e5c7b-111">Attributes</span></span>

<span data-ttu-id="e5c7b-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e5c7b-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5c7b-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e5c7b-113">Child Elements</span></span>

<span data-ttu-id="e5c7b-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e5c7b-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e5c7b-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e5c7b-115">Parent Elements</span></span>

|<span data-ttu-id="e5c7b-116">Élément</span><span class="sxs-lookup"><span data-stu-id="e5c7b-116">Element</span></span>|<span data-ttu-id="e5c7b-117">Description</span><span class="sxs-lookup"><span data-stu-id="e5c7b-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5c7b-118">ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e5c7b-118">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="e5c7b-119">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="e5c7b-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e5c7b-120">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="e5c7b-120">Text Value</span></span>

<span data-ttu-id="e5c7b-121">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="e5c7b-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5c7b-122">Notes</span><span class="sxs-lookup"><span data-stu-id="e5c7b-122">Remarks</span></span>

<span data-ttu-id="e5c7b-123">Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="e5c7b-123">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5c7b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5c7b-124">See Also</span></span>

[<span data-ttu-id="e5c7b-125">ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e5c7b-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="e5c7b-126">PropertyName, élément pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e5c7b-126">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="e5c7b-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5c7b-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
