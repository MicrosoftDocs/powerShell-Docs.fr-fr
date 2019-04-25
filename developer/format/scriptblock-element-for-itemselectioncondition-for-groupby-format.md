---
title: Élément ScriptBlock pour ItemSelectionCondition pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064541"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="694ba-102">ScriptBlock, élément pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="694ba-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="694ba-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="694ba-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="694ba-104">Lorsque ce script est évalué à `true`, la condition est remplie, et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="694ba-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="694ba-105">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="694ba-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="694ba-106">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de CustomItem GroupBy (Format) pour CustomEntry d’élément de ExpressionBinding GroupBy (Format) pour CustomItem d’élément de ItemSelectionCondition GroupBy (Format) pour ExpressionBinding pour un élément ScriptBlock de GroupBy (Format) pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="694ba-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="694ba-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="694ba-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="694ba-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="694ba-108">Attributes and Elements</span></span>

<span data-ttu-id="694ba-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="694ba-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="694ba-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="694ba-110">Attributes</span></span>

<span data-ttu-id="694ba-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="694ba-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="694ba-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="694ba-112">Child Elements</span></span>

<span data-ttu-id="694ba-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="694ba-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="694ba-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="694ba-114">Parent Elements</span></span>

|<span data-ttu-id="694ba-115">Élément</span><span class="sxs-lookup"><span data-stu-id="694ba-115">Element</span></span>|<span data-ttu-id="694ba-116">Description</span><span class="sxs-lookup"><span data-stu-id="694ba-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="694ba-117">Élément ItemSelectionCondition pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="694ba-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="694ba-118">Définit la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="694ba-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="694ba-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="694ba-119">Text Value</span></span>

<span data-ttu-id="694ba-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="694ba-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="694ba-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="694ba-121">Remarks</span></span>

<span data-ttu-id="694ba-122">Si cet élément est utilisé, vous ne pouvez pas spécifier le [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) élément lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="694ba-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="694ba-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="694ba-123">See Also</span></span>

[<span data-ttu-id="694ba-124">Élément ItemSelectionCondition pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="694ba-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="694ba-125">Élément PropertyName pour ItemSelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="694ba-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="694ba-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="694ba-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
