---
title: Élément ItemSelectionCondition pour ExpressionBinding pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365288"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="ed83b-102">ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ed83b-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="ed83b-103">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="ed83b-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="ed83b-104">Il n’existe pas de limite au nombre de conditions de sélection qui peuvent être spécifiées pour un élément de contrôle.</span><span class="sxs-lookup"><span data-stu-id="ed83b-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="ed83b-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="ed83b-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="ed83b-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format) élément CustomItem pour CustomEntry pour GroupBy (format) élément ExpressionBinding pour CustomItem pour l’élément GroupBy (format) ItemSelectionCondition pour l’élément ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="ed83b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ed83b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed83b-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ed83b-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="ed83b-108">Attributes and Elements</span></span>

<span data-ttu-id="ed83b-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ItemSelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="ed83b-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ed83b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="ed83b-110">Attributes</span></span>

<span data-ttu-id="ed83b-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ed83b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ed83b-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ed83b-112">Child Elements</span></span>

|<span data-ttu-id="ed83b-113">Élément</span><span class="sxs-lookup"><span data-stu-id="ed83b-113">Element</span></span>|<span data-ttu-id="ed83b-114">Description</span><span class="sxs-lookup"><span data-stu-id="ed83b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ed83b-115">PropertyName, élément de ItemSelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="ed83b-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="ed83b-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ed83b-116">Optional element.</span></span><br /><br /> <span data-ttu-id="ed83b-117">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="ed83b-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="ed83b-118">Élément ScriptBlock pour ItemSelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="ed83b-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="ed83b-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ed83b-119">Optional element.</span></span><br /><br /> <span data-ttu-id="ed83b-120">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="ed83b-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ed83b-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ed83b-121">Parent Elements</span></span>

|<span data-ttu-id="ed83b-122">Élément</span><span class="sxs-lookup"><span data-stu-id="ed83b-122">Element</span></span>|<span data-ttu-id="ed83b-123">Description</span><span class="sxs-lookup"><span data-stu-id="ed83b-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ed83b-124">Élément ExpressionBinding pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="ed83b-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="ed83b-125">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="ed83b-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ed83b-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="ed83b-126">Remarks</span></span>

<span data-ttu-id="ed83b-127">Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="ed83b-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed83b-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed83b-128">See Also</span></span>

[<span data-ttu-id="ed83b-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed83b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="ed83b-130">Élément ExpressionBinding pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="ed83b-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
