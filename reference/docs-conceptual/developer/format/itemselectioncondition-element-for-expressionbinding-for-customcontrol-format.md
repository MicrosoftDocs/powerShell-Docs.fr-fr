---
title: Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6a5c66a63c02980b16c2d2d9dd689410c8aec51c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781186"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="70c87-102">ItemSelectionCondition, élément pour ExpressionBinding pour CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="70c87-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="70c87-103">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="70c87-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="70c87-104">Il n’existe pas de limite au nombre de conditions de sélection qui peuvent être spécifiées pour un élément de contrôle.</span><span class="sxs-lookup"><span data-stu-id="70c87-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="70c87-105">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="70c87-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="70c87-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) CustomControl, élément (format) CustomEntries élément pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour la vue (format) élément CustomItem pour la liaison d’expression pour la vue (format) CustomEntry pour la vue (format)</span><span class="sxs-lookup"><span data-stu-id="70c87-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70c87-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70c87-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70c87-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="70c87-108">Attributes and Elements</span></span>

<span data-ttu-id="70c87-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ItemSelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="70c87-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70c87-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="70c87-110">Attributes</span></span>

<span data-ttu-id="70c87-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="70c87-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70c87-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="70c87-112">Child Elements</span></span>

|<span data-ttu-id="70c87-113">Élément</span><span class="sxs-lookup"><span data-stu-id="70c87-113">Element</span></span>|<span data-ttu-id="70c87-114">Description</span><span class="sxs-lookup"><span data-stu-id="70c87-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70c87-115">PropertyName, élément de ItemSelectionCondition pour CustomControl pour View (format</span><span class="sxs-lookup"><span data-stu-id="70c87-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="70c87-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="70c87-116">Optional element.</span></span><br /><br /> <span data-ttu-id="70c87-117">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="70c87-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="70c87-118">ScriptBlock, élément pour ItemSelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="70c87-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="70c87-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="70c87-119">Optional element.</span></span><br /><br /> <span data-ttu-id="70c87-120">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="70c87-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="70c87-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="70c87-121">Parent Elements</span></span>

|<span data-ttu-id="70c87-122">Élément</span><span class="sxs-lookup"><span data-stu-id="70c87-122">Element</span></span>|<span data-ttu-id="70c87-123">Description</span><span class="sxs-lookup"><span data-stu-id="70c87-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70c87-124">ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="70c87-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="70c87-125">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="70c87-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="70c87-126">Notes</span><span class="sxs-lookup"><span data-stu-id="70c87-126">Remarks</span></span>

<span data-ttu-id="70c87-127">Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="70c87-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="70c87-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70c87-128">See Also</span></span>

[<span data-ttu-id="70c87-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="70c87-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="70c87-130">ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="70c87-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
