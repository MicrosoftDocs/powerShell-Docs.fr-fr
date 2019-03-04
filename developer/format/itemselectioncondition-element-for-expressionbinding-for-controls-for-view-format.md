---
title: Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861845"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="ed0e7-102">ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ed0e7-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="ed0e7-103">Définit la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ed0e7-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="ed0e7-104">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="ed0e7-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ed0e7-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour les contrôles d’élément de ExpressionBinding vue (Format) pour CustomItem pour les contrôles de vue (Format) Élément ItemSelectionCondition de ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ed0e7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ed0e7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed0e7-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ed0e7-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="ed0e7-107">Attributes and Elements</span></span>

<span data-ttu-id="ed0e7-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ItemSelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="ed0e7-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ed0e7-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="ed0e7-109">Attributes</span></span>

<span data-ttu-id="ed0e7-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ed0e7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ed0e7-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ed0e7-111">Child Elements</span></span>

|<span data-ttu-id="ed0e7-112">Élément</span><span class="sxs-lookup"><span data-stu-id="ed0e7-112">Element</span></span>|<span data-ttu-id="ed0e7-113">Description</span><span class="sxs-lookup"><span data-stu-id="ed0e7-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ed0e7-114">Élément PropertyName pour ItemSelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ed0e7-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="ed0e7-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ed0e7-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ed0e7-116">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="ed0e7-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="ed0e7-117">Élément ScriptBlock pour ItemSelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ed0e7-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="ed0e7-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ed0e7-118">Optional element.</span></span><br /><br /> <span data-ttu-id="ed0e7-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="ed0e7-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ed0e7-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ed0e7-120">Parent Elements</span></span>

|<span data-ttu-id="ed0e7-121">Élément</span><span class="sxs-lookup"><span data-stu-id="ed0e7-121">Element</span></span>|<span data-ttu-id="ed0e7-122">Description</span><span class="sxs-lookup"><span data-stu-id="ed0e7-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ed0e7-123">Élément ExpressionBinding pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ed0e7-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="ed0e7-124">Définit les données qui sont affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="ed0e7-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ed0e7-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="ed0e7-125">Remarks</span></span>

<span data-ttu-id="ed0e7-126">Vous pouvez spécifier un nom de propriété ou un script pour cette condition mais que vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="ed0e7-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed0e7-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed0e7-127">See Also</span></span>

[<span data-ttu-id="ed0e7-128">Élément PropertyName pour ItemSelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ed0e7-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="ed0e7-129">Élément ScriptBlock pour ItemSelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ed0e7-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="ed0e7-130">Élément ExpressionBinding pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ed0e7-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="ed0e7-131">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed0e7-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
