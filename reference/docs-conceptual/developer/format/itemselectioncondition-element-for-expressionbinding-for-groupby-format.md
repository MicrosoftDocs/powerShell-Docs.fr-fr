---
ms.date: 09/13/2016
ms.topic: reference
title: ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)
description: ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)
ms.openlocfilehash: 92120ace5ed316fbfbf1d51422071c27d5a604cf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651976"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="b288a-103">ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b288a-103">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="b288a-104">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="b288a-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="b288a-105">Il n’existe pas de limite au nombre de conditions de sélection qui peuvent être spécifiées pour un élément de contrôle.</span><span class="sxs-lookup"><span data-stu-id="b288a-105">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="b288a-106">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="b288a-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b288a-107">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour la vue (format) CustomControl, élément de GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) CustomItem élément pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b288a-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b288a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b288a-108">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b288a-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b288a-109">Attributes and Elements</span></span>

<span data-ttu-id="b288a-110">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ItemSelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="b288a-110">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b288a-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="b288a-111">Attributes</span></span>

<span data-ttu-id="b288a-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b288a-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b288a-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b288a-113">Child Elements</span></span>

|<span data-ttu-id="b288a-114">Élément</span><span class="sxs-lookup"><span data-stu-id="b288a-114">Element</span></span>|<span data-ttu-id="b288a-115">Description</span><span class="sxs-lookup"><span data-stu-id="b288a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b288a-116">PropertyName, élément pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b288a-116">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="b288a-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b288a-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b288a-118">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="b288a-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="b288a-119">ScriptBlock, élément pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b288a-119">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="b288a-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b288a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b288a-121">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="b288a-121">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b288a-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b288a-122">Parent Elements</span></span>

|<span data-ttu-id="b288a-123">Élément</span><span class="sxs-lookup"><span data-stu-id="b288a-123">Element</span></span>|<span data-ttu-id="b288a-124">Description</span><span class="sxs-lookup"><span data-stu-id="b288a-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b288a-125">ExpressionBinding, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b288a-125">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="b288a-126">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="b288a-126">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b288a-127">Notes</span><span class="sxs-lookup"><span data-stu-id="b288a-127">Remarks</span></span>

<span data-ttu-id="b288a-128">Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="b288a-128">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="b288a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b288a-129">See Also</span></span>

[<span data-ttu-id="b288a-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="b288a-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="b288a-131">ExpressionBinding, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b288a-131">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
