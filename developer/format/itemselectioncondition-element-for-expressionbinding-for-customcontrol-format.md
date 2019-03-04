---
title: Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858185"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="27c6d-102">ItemSelectionCondition, élément pour ExpressionBinding pour CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="27c6d-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="27c6d-103">Définit la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="27c6d-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="27c6d-104">Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour un élément de contrôle.</span><span class="sxs-lookup"><span data-stu-id="27c6d-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="27c6d-105">Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="27c6d-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="27c6d-106">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour élément d’affichage (Format) de ExpressionBinding pour CustomItem pour CustomControl pour l’élément de ItemSelectionCondition d’affichage (Format) pour la liaison d’Expression pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="27c6d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="27c6d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27c6d-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="27c6d-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="27c6d-108">Attributes and Elements</span></span>

<span data-ttu-id="27c6d-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ItemSelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="27c6d-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="27c6d-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="27c6d-110">Attributes</span></span>

<span data-ttu-id="27c6d-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="27c6d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="27c6d-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="27c6d-112">Child Elements</span></span>

|<span data-ttu-id="27c6d-113">Élément</span><span class="sxs-lookup"><span data-stu-id="27c6d-113">Element</span></span>|<span data-ttu-id="27c6d-114">Description</span><span class="sxs-lookup"><span data-stu-id="27c6d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="27c6d-115">Élément PropertyName pour ItemSelectionCondition pour CustomControl pour (Format d’affichage</span><span class="sxs-lookup"><span data-stu-id="27c6d-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="27c6d-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="27c6d-116">Optional element.</span></span><br /><br /> <span data-ttu-id="27c6d-117">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="27c6d-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="27c6d-118">Élément ScriptBlock pour ItemSelectionCondition pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="27c6d-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="27c6d-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="27c6d-119">Optional element.</span></span><br /><br /> <span data-ttu-id="27c6d-120">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="27c6d-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="27c6d-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="27c6d-121">Parent Elements</span></span>

|<span data-ttu-id="27c6d-122">Élément</span><span class="sxs-lookup"><span data-stu-id="27c6d-122">Element</span></span>|<span data-ttu-id="27c6d-123">Description</span><span class="sxs-lookup"><span data-stu-id="27c6d-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="27c6d-124">Élément ExpressionBinding pour CustomItem pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="27c6d-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="27c6d-125">Définit les données qui sont affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="27c6d-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="27c6d-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="27c6d-126">Remarks</span></span>

<span data-ttu-id="27c6d-127">Vous pouvez spécifier un nom de propriété ou un script pour cette condition mais que vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="27c6d-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="27c6d-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27c6d-128">See Also</span></span>

[<span data-ttu-id="27c6d-129">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="27c6d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="27c6d-130">Élément ExpressionBinding pour CustomItem pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="27c6d-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
