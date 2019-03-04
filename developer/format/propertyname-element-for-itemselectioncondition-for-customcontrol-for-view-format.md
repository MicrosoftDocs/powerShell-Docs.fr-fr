---
title: Élément PropertyName pour ItemSelectionCondition pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854785"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="5524b-102">PropertyName, élément pour ItemSelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="5524b-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="5524b-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="5524b-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="5524b-104">Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie, et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="5524b-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="5524b-105">Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5524b-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="5524b-106">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour élément d’affichage (Format) de ExpressionBinding pour CustomItem pour CustomControl pour l’élément de ItemSelectionCondition d’affichage (Format) pour la liaison d’Expression pour CustomControl pour élément d’affichage (Format) de PropertyName pour ItemSelectionCondition pour CustomControl pour (Format d’affichage</span><span class="sxs-lookup"><span data-stu-id="5524b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="5524b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5524b-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5524b-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="5524b-108">Attributes and Elements</span></span>

<span data-ttu-id="5524b-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="5524b-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5524b-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="5524b-110">Attributes</span></span>

<span data-ttu-id="5524b-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5524b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5524b-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5524b-112">Child Elements</span></span>

<span data-ttu-id="5524b-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5524b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5524b-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5524b-114">Parent Elements</span></span>

|<span data-ttu-id="5524b-115">Élément</span><span class="sxs-lookup"><span data-stu-id="5524b-115">Element</span></span>|<span data-ttu-id="5524b-116">Description</span><span class="sxs-lookup"><span data-stu-id="5524b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5524b-117">Élément ItemSelectionCondition pour la liaison d’Expression pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="5524b-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="5524b-118">Définit la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5524b-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5524b-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="5524b-119">Text Value</span></span>

<span data-ttu-id="5524b-120">Spécifiez le nom de la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="5524b-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="5524b-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="5524b-121">Remarks</span></span>

<span data-ttu-id="5524b-122">Si cet élément est utilisé, vous ne pouvez pas spécifier le [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) élément lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="5524b-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="5524b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5524b-123">See Also</span></span>

[<span data-ttu-id="5524b-124">Élément ScriptBlock pour ItemSelectionCondition pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="5524b-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5524b-125">Élément ItemSelectionCondition pour la liaison d’Expression pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="5524b-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="5524b-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5524b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
