---
title: Élément ItemSelectionCondition pour ExpressionBinding pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853135"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="e7bde-102">ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e7bde-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="e7bde-103">Définit la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e7bde-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="e7bde-104">Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour un élément de contrôle.</span><span class="sxs-lookup"><span data-stu-id="e7bde-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="e7bde-105">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="e7bde-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e7bde-106">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de CustomItem GroupBy (Format) pour CustomEntry d’élément de ExpressionBinding GroupBy (Format) pour CustomItem d’élément de ItemSelectionCondition GroupBy (Format) pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e7bde-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e7bde-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7bde-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e7bde-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="e7bde-108">Attributes and Elements</span></span>

<span data-ttu-id="e7bde-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ItemSelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="e7bde-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e7bde-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="e7bde-110">Attributes</span></span>

<span data-ttu-id="e7bde-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e7bde-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e7bde-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e7bde-112">Child Elements</span></span>

|<span data-ttu-id="e7bde-113">Élément</span><span class="sxs-lookup"><span data-stu-id="e7bde-113">Element</span></span>|<span data-ttu-id="e7bde-114">Description</span><span class="sxs-lookup"><span data-stu-id="e7bde-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e7bde-115">Élément PropertyName pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e7bde-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="e7bde-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e7bde-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e7bde-117">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e7bde-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e7bde-118">Élément ScriptBlock pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e7bde-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="e7bde-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e7bde-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e7bde-120">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e7bde-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e7bde-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e7bde-121">Parent Elements</span></span>

|<span data-ttu-id="e7bde-122">Élément</span><span class="sxs-lookup"><span data-stu-id="e7bde-122">Element</span></span>|<span data-ttu-id="e7bde-123">Description</span><span class="sxs-lookup"><span data-stu-id="e7bde-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e7bde-124">Élément ExpressionBinding pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e7bde-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e7bde-125">Définit les données qui sont affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="e7bde-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e7bde-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="e7bde-126">Remarks</span></span>

<span data-ttu-id="e7bde-127">Vous pouvez spécifier un nom de propriété ou un script pour cette condition mais que vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="e7bde-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7bde-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7bde-128">See Also</span></span>

[<span data-ttu-id="e7bde-129">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7bde-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="e7bde-130">Élément ExpressionBinding pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e7bde-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
