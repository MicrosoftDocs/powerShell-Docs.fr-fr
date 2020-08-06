---
title: Élément ScriptBlock pour ItemSelectionCondition pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7738b180f328c7360275058cdb9dea01df6ea285
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787646"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="0c7a5-102">ScriptBlock, élément pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0c7a5-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="0c7a5-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="0c7a5-104">Lorsque ce script est évalué à `true` , la condition est remplie et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="0c7a5-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="0c7a5-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour l’élément GroupBy (format) CustomItem pour CustomEntry pour GroupBy (format) élément ExpressionBinding pour CustomItem pour l’élément GroupBy (format) ItemSelectionCondition pour ExpressionBinding pour l’élément ScriptBlock GroupBy (format) pour ItemSelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0c7a5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0c7a5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c7a5-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0c7a5-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0c7a5-108">Attributes and Elements</span></span>

<span data-ttu-id="0c7a5-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0c7a5-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0c7a5-110">Attributes</span></span>

<span data-ttu-id="0c7a5-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0c7a5-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0c7a5-112">Child Elements</span></span>

<span data-ttu-id="0c7a5-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0c7a5-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0c7a5-114">Parent Elements</span></span>

|<span data-ttu-id="0c7a5-115">Élément</span><span class="sxs-lookup"><span data-stu-id="0c7a5-115">Element</span></span>|<span data-ttu-id="0c7a5-116">Description</span><span class="sxs-lookup"><span data-stu-id="0c7a5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c7a5-117">ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0c7a5-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="0c7a5-118">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0c7a5-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="0c7a5-119">Text Value</span></span>

<span data-ttu-id="0c7a5-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c7a5-121">Notes</span><span class="sxs-lookup"><span data-stu-id="0c7a5-121">Remarks</span></span>

<span data-ttu-id="0c7a5-122">Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c7a5-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c7a5-123">See Also</span></span>

[<span data-ttu-id="0c7a5-124">ItemSelectionCondition, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0c7a5-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="0c7a5-125">PropertyName, élément pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0c7a5-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="0c7a5-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c7a5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
