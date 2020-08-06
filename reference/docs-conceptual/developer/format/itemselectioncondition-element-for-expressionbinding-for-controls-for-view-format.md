---
title: Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e8e3ea64fd947fbb2b98c410ac08533f386c9505
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781203"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="ff7aa-102">ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ff7aa-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="ff7aa-103">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="ff7aa-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="ff7aa-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="ff7aa-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ff7aa-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément CustomEntries View (format) pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour les contrôles de l’élément View (format) CustomItem pour CustomEntry pour les contrôles pour l’élément View (format) ExpressionBinding pour les contrôles pour la vue (format) CustomItem élément de ItemSelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="ff7aa-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ff7aa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff7aa-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ff7aa-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ff7aa-107">Attributes and Elements</span></span>

<span data-ttu-id="ff7aa-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ItemSelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="ff7aa-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ff7aa-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="ff7aa-109">Attributes</span></span>

<span data-ttu-id="ff7aa-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ff7aa-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ff7aa-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ff7aa-111">Child Elements</span></span>

|<span data-ttu-id="ff7aa-112">Élément</span><span class="sxs-lookup"><span data-stu-id="ff7aa-112">Element</span></span>|<span data-ttu-id="ff7aa-113">Description</span><span class="sxs-lookup"><span data-stu-id="ff7aa-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff7aa-114">PropertyName, élément pour ItemSelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ff7aa-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="ff7aa-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ff7aa-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ff7aa-116">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="ff7aa-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="ff7aa-117">ScriptBlock, élément pour ItemSelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ff7aa-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="ff7aa-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ff7aa-118">Optional element.</span></span><br /><br /> <span data-ttu-id="ff7aa-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="ff7aa-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ff7aa-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ff7aa-120">Parent Elements</span></span>

|<span data-ttu-id="ff7aa-121">Élément</span><span class="sxs-lookup"><span data-stu-id="ff7aa-121">Element</span></span>|<span data-ttu-id="ff7aa-122">Description</span><span class="sxs-lookup"><span data-stu-id="ff7aa-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff7aa-123">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ff7aa-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="ff7aa-124">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="ff7aa-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ff7aa-125">Notes</span><span class="sxs-lookup"><span data-stu-id="ff7aa-125">Remarks</span></span>

<span data-ttu-id="ff7aa-126">Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="ff7aa-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff7aa-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff7aa-127">See Also</span></span>

[<span data-ttu-id="ff7aa-128">PropertyName, élément pour ItemSelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ff7aa-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="ff7aa-129">ScriptBlock, élément pour ItemSelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ff7aa-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="ff7aa-130">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ff7aa-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="ff7aa-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff7aa-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
