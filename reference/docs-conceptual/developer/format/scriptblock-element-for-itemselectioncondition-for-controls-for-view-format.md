---
title: Élément ScriptBlock pour ItemSelectionCondition pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74b3e23005f595c4c550320849cac5b196e9d479
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787663"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="672f1-102">ScriptBlock, élément pour ItemSelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="672f1-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="672f1-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="672f1-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="672f1-104">Lorsque ce script est évalué à `true` , la condition est remplie et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="672f1-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="672f1-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="672f1-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="672f1-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour la vue (format) élément CustomControl pour le contrôle des contrôles pour l’élément View (format) CustomEntries pour CustomControl pour l’élément CustomEntry (format) de la vue CustomEntries pour les contrôles pour l’élément CustomItem View (format) pour CustomEntry pour les contrôles pour l’élément ExpressionBinding (format) View pour CustomItem pour les contrôles pour l’élément View (format) ItemSelectionCondition de l’élément ExpressionBinding pour les contrôles pour l’élément ScriptBlock View (format) pour ItemSelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="672f1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="672f1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="672f1-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="672f1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="672f1-108">Attributes and Elements</span></span>

<span data-ttu-id="672f1-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="672f1-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="672f1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="672f1-110">Attributes</span></span>

<span data-ttu-id="672f1-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="672f1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="672f1-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="672f1-112">Child Elements</span></span>

<span data-ttu-id="672f1-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="672f1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="672f1-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="672f1-114">Parent Elements</span></span>

|<span data-ttu-id="672f1-115">Élément</span><span class="sxs-lookup"><span data-stu-id="672f1-115">Element</span></span>|<span data-ttu-id="672f1-116">Description</span><span class="sxs-lookup"><span data-stu-id="672f1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="672f1-117">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="672f1-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="672f1-118">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="672f1-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="672f1-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="672f1-119">Text Value</span></span>

<span data-ttu-id="672f1-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="672f1-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="672f1-121">Notes</span><span class="sxs-lookup"><span data-stu-id="672f1-121">Remarks</span></span>

<span data-ttu-id="672f1-122">Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="672f1-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="672f1-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="672f1-123">See Also</span></span>

[<span data-ttu-id="672f1-124">PropertyName, élément pour ItemSelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="672f1-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="672f1-125">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="672f1-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="672f1-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="672f1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
