---
title: Élément ItemSelectionCondition pour ExpressionBinding pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a9b74f1882efc578f7d9ab27b8cd2f8a52833ab8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773434"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="a10e9-102">ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a10e9-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="a10e9-103">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="a10e9-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="a10e9-104">Il n’existe pas de limite au nombre de conditions de sélection qui peuvent être spécifiées pour un élément de contrôle.</span><span class="sxs-lookup"><span data-stu-id="a10e9-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="a10e9-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="a10e9-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a10e9-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour la vue (format) CustomControl, élément de GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) CustomItem élément pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a10e9-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a10e9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a10e9-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a10e9-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a10e9-108">Attributes and Elements</span></span>

<span data-ttu-id="a10e9-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ItemSelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="a10e9-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a10e9-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="a10e9-110">Attributes</span></span>

<span data-ttu-id="a10e9-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a10e9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a10e9-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a10e9-112">Child Elements</span></span>

|<span data-ttu-id="a10e9-113">Élément</span><span class="sxs-lookup"><span data-stu-id="a10e9-113">Element</span></span>|<span data-ttu-id="a10e9-114">Description</span><span class="sxs-lookup"><span data-stu-id="a10e9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a10e9-115">PropertyName, élément pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a10e9-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="a10e9-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a10e9-116">Optional element.</span></span><br /><br /> <span data-ttu-id="a10e9-117">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="a10e9-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a10e9-118">ScriptBlock, élément pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a10e9-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="a10e9-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a10e9-119">Optional element.</span></span><br /><br /> <span data-ttu-id="a10e9-120">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="a10e9-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a10e9-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a10e9-121">Parent Elements</span></span>

|<span data-ttu-id="a10e9-122">Élément</span><span class="sxs-lookup"><span data-stu-id="a10e9-122">Element</span></span>|<span data-ttu-id="a10e9-123">Description</span><span class="sxs-lookup"><span data-stu-id="a10e9-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a10e9-124">ExpressionBinding, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a10e9-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="a10e9-125">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="a10e9-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a10e9-126">Notes</span><span class="sxs-lookup"><span data-stu-id="a10e9-126">Remarks</span></span>

<span data-ttu-id="a10e9-127">Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="a10e9-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="a10e9-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a10e9-128">See Also</span></span>

[<span data-ttu-id="a10e9-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a10e9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="a10e9-130">ExpressionBinding, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a10e9-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
