---
title: PropertyName, élément de ItemSelectionCondition pour CustomControl pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362438"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="b8f7a-102">PropertyName, élément pour ItemSelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="b8f7a-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="b8f7a-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="b8f7a-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b8f7a-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true`, la condition est remplie et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="b8f7a-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="b8f7a-105">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b8f7a-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="b8f7a-106">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour la vue (format) CustomItem, élément de CustomEntry pour l’élément ExpressionBinding View (format) de CustomItem pour CustomControl pour la vue (format) élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour l’élément View (format) PropertyName pour ItemSelectionCondition pour CustomControl pour View (format</span><span class="sxs-lookup"><span data-stu-id="b8f7a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="b8f7a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8f7a-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b8f7a-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="b8f7a-108">Attributes and Elements</span></span>

<span data-ttu-id="b8f7a-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="b8f7a-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b8f7a-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="b8f7a-110">Attributes</span></span>

<span data-ttu-id="b8f7a-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="b8f7a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b8f7a-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b8f7a-112">Child Elements</span></span>

<span data-ttu-id="b8f7a-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="b8f7a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b8f7a-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b8f7a-114">Parent Elements</span></span>

|<span data-ttu-id="b8f7a-115">Élément</span><span class="sxs-lookup"><span data-stu-id="b8f7a-115">Element</span></span>|<span data-ttu-id="b8f7a-116">Description</span><span class="sxs-lookup"><span data-stu-id="b8f7a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8f7a-117">Élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="b8f7a-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="b8f7a-118">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="b8f7a-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b8f7a-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="b8f7a-119">Text Value</span></span>

<span data-ttu-id="b8f7a-120">Spécifiez le nom de la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="b8f7a-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8f7a-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="b8f7a-121">Remarks</span></span>

<span data-ttu-id="b8f7a-122">Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="b8f7a-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8f7a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8f7a-123">See Also</span></span>

[<span data-ttu-id="b8f7a-124">Élément ScriptBlock pour ItemSelectionCondition pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="b8f7a-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b8f7a-125">Élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="b8f7a-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="b8f7a-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8f7a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
