---
title: PropertyName, élément de ItemSelectionCondition pour CustomControl pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0131fa86be4be4daec1d9d24b50397fb8529f050
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785572"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="4e5f3-102">PropertyName, élément pour ItemSelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="4e5f3-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="4e5f3-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="4e5f3-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="4e5f3-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="4e5f3-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="4e5f3-105">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4e5f3-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="4e5f3-106">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour la vue (format) CustomItem, élément de CustomEntry pour l’élément ExpressionBinding View (format) de CustomItem pour CustomControl pour la vue (format) élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour l’élément View (format) PropertyName pour ItemSelectionCondition pour CustomControl pour View (format</span><span class="sxs-lookup"><span data-stu-id="4e5f3-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="4e5f3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e5f3-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4e5f3-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4e5f3-108">Attributes and Elements</span></span>

<span data-ttu-id="4e5f3-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="4e5f3-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e5f3-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="4e5f3-110">Attributes</span></span>

<span data-ttu-id="4e5f3-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4e5f3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4e5f3-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4e5f3-112">Child Elements</span></span>

<span data-ttu-id="4e5f3-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4e5f3-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4e5f3-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4e5f3-114">Parent Elements</span></span>

|<span data-ttu-id="4e5f3-115">Élément</span><span class="sxs-lookup"><span data-stu-id="4e5f3-115">Element</span></span>|<span data-ttu-id="4e5f3-116">Description</span><span class="sxs-lookup"><span data-stu-id="4e5f3-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e5f3-117">Élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="4e5f3-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="4e5f3-118">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="4e5f3-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4e5f3-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="4e5f3-119">Text Value</span></span>

<span data-ttu-id="4e5f3-120">Spécifiez le nom de la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="4e5f3-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="4e5f3-121">Notes</span><span class="sxs-lookup"><span data-stu-id="4e5f3-121">Remarks</span></span>

<span data-ttu-id="4e5f3-122">Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="4e5f3-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e5f3-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e5f3-123">See Also</span></span>

[<span data-ttu-id="4e5f3-124">ScriptBlock, élément pour ItemSelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="4e5f3-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4e5f3-125">Élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="4e5f3-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="4e5f3-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e5f3-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
