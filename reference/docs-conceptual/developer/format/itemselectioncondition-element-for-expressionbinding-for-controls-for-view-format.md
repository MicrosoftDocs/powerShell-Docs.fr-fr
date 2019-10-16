---
title: Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362938"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="6956c-102">ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="6956c-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="6956c-103">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="6956c-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="6956c-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="6956c-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="6956c-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour les contrôles pour l’élément CustomItem (format) View pour CustomEntry pour les contrôles pour l’élément View (format) ExpressionBinding pour CustomItem pour les contrôles pour View (format) Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="6956c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6956c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6956c-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6956c-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="6956c-107">Attributes and Elements</span></span>

<span data-ttu-id="6956c-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ItemSelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="6956c-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6956c-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="6956c-109">Attributes</span></span>

<span data-ttu-id="6956c-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="6956c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6956c-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6956c-111">Child Elements</span></span>

|<span data-ttu-id="6956c-112">Élément</span><span class="sxs-lookup"><span data-stu-id="6956c-112">Element</span></span>|<span data-ttu-id="6956c-113">Description</span><span class="sxs-lookup"><span data-stu-id="6956c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6956c-114">Élément PropertyName pour ItemSelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="6956c-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="6956c-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6956c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6956c-116">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="6956c-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="6956c-117">Élément ScriptBlock pour ItemSelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="6956c-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="6956c-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6956c-118">Optional element.</span></span><br /><br /> <span data-ttu-id="6956c-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="6956c-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6956c-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6956c-120">Parent Elements</span></span>

|<span data-ttu-id="6956c-121">Élément</span><span class="sxs-lookup"><span data-stu-id="6956c-121">Element</span></span>|<span data-ttu-id="6956c-122">Description</span><span class="sxs-lookup"><span data-stu-id="6956c-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6956c-123">Élément ExpressionBinding pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="6956c-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="6956c-124">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="6956c-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6956c-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="6956c-125">Remarks</span></span>

<span data-ttu-id="6956c-126">Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="6956c-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="6956c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6956c-127">See Also</span></span>

[<span data-ttu-id="6956c-128">Élément PropertyName pour ItemSelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="6956c-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="6956c-129">Élément ScriptBlock pour ItemSelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="6956c-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="6956c-130">Élément ExpressionBinding pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="6956c-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="6956c-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="6956c-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
