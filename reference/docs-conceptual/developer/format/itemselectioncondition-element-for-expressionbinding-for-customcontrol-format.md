---
ms.date: 09/13/2016
ms.topic: reference
title: ItemSelectionCondition, élément pour ExpressionBinding pour CustomControl (Format)
description: ItemSelectionCondition, élément pour ExpressionBinding pour CustomControl (Format)
ms.openlocfilehash: 38c88ad47e57cd20902c6b8aabdb0b8e8b682ba4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648046"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="718cf-103">ItemSelectionCondition, élément pour ExpressionBinding pour CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="718cf-103">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="718cf-104">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="718cf-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="718cf-105">Il n’existe pas de limite au nombre de conditions de sélection qui peuvent être spécifiées pour un élément de contrôle.</span><span class="sxs-lookup"><span data-stu-id="718cf-105">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="718cf-106">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="718cf-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="718cf-107">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) CustomControl, élément (format) CustomEntries élément pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour la vue (format) élément CustomItem pour la liaison d’expression pour la vue (format) CustomEntry pour la vue (format)</span><span class="sxs-lookup"><span data-stu-id="718cf-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="718cf-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="718cf-108">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="718cf-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="718cf-109">Attributes and Elements</span></span>

<span data-ttu-id="718cf-110">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ItemSelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="718cf-110">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="718cf-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="718cf-111">Attributes</span></span>

<span data-ttu-id="718cf-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="718cf-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="718cf-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="718cf-113">Child Elements</span></span>

|<span data-ttu-id="718cf-114">Élément</span><span class="sxs-lookup"><span data-stu-id="718cf-114">Element</span></span>|<span data-ttu-id="718cf-115">Description</span><span class="sxs-lookup"><span data-stu-id="718cf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="718cf-116">PropertyName, élément de ItemSelectionCondition pour CustomControl pour View (format</span><span class="sxs-lookup"><span data-stu-id="718cf-116">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="718cf-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="718cf-117">Optional element.</span></span><br /><br /> <span data-ttu-id="718cf-118">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="718cf-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="718cf-119">ScriptBlock, élément pour ItemSelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="718cf-119">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="718cf-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="718cf-120">Optional element.</span></span><br /><br /> <span data-ttu-id="718cf-121">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="718cf-121">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="718cf-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="718cf-122">Parent Elements</span></span>

|<span data-ttu-id="718cf-123">Élément</span><span class="sxs-lookup"><span data-stu-id="718cf-123">Element</span></span>|<span data-ttu-id="718cf-124">Description</span><span class="sxs-lookup"><span data-stu-id="718cf-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="718cf-125">ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="718cf-125">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="718cf-126">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="718cf-126">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="718cf-127">Notes</span><span class="sxs-lookup"><span data-stu-id="718cf-127">Remarks</span></span>

<span data-ttu-id="718cf-128">Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="718cf-128">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="718cf-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="718cf-129">See Also</span></span>

[<span data-ttu-id="718cf-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="718cf-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="718cf-131">ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="718cf-131">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
