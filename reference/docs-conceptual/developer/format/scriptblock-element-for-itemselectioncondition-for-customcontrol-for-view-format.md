---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour ItemSelectionCondition pour CustomControl pour View (Format)
description: ScriptBlock, élément pour ItemSelectionCondition pour CustomControl pour View (Format)
ms.openlocfilehash: d762f400f5bb52af314093079fe94223c56d3f31
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665126"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="26e90-103">ScriptBlock, élément pour ItemSelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="26e90-103">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="26e90-104">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="26e90-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="26e90-105">Lorsque ce script est évalué à `true` , la condition est remplie et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="26e90-105">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="26e90-106">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="26e90-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="26e90-107">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour la vue (format) CustomItem, élément de CustomEntry pour l’élément ExpressionBinding View (format) de CustomItem pour CustomControl pour la vue (format) élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour la vue (format) élément ScriptBlock pour ItemSelectionCondition pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="26e90-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="26e90-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26e90-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="26e90-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="26e90-109">Attributes and Elements</span></span>

<span data-ttu-id="26e90-110">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="26e90-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="26e90-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="26e90-111">Attributes</span></span>

<span data-ttu-id="26e90-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="26e90-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="26e90-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="26e90-113">Child Elements</span></span>

<span data-ttu-id="26e90-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="26e90-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="26e90-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="26e90-115">Parent Elements</span></span>

|<span data-ttu-id="26e90-116">Élément</span><span class="sxs-lookup"><span data-stu-id="26e90-116">Element</span></span>|<span data-ttu-id="26e90-117">Description</span><span class="sxs-lookup"><span data-stu-id="26e90-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26e90-118">Élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="26e90-118">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="26e90-119">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="26e90-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="26e90-120">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="26e90-120">Text Value</span></span>

<span data-ttu-id="26e90-121">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="26e90-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="26e90-122">Notes</span><span class="sxs-lookup"><span data-stu-id="26e90-122">Remarks</span></span>

<span data-ttu-id="26e90-123">Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="26e90-123">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="26e90-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26e90-124">See Also</span></span>

[<span data-ttu-id="26e90-125">PropertyName, élément pour ItemSelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="26e90-125">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="26e90-126">Élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="26e90-126">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="26e90-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="26e90-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
