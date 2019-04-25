---
title: Élément ScriptBlock pour ItemSelectionCondition pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064711"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="9720f-102">ScriptBlock, élément pour ItemSelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="9720f-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="9720f-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="9720f-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="9720f-104">Lorsque ce script est évalué à `true`, la condition est remplie, et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="9720f-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="9720f-105">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="9720f-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="9720f-106">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour les contrôles d’élément de ExpressionBinding vue (Format) pour CustomItem pour les contrôles de vue (Format) Élément ItemSelectionCondition de ExpressionBinding pour les contrôles d’élément ScriptBlock de vue (Format) pour ItemSelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="9720f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9720f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9720f-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9720f-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="9720f-108">Attributes and Elements</span></span>

<span data-ttu-id="9720f-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="9720f-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9720f-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="9720f-110">Attributes</span></span>

<span data-ttu-id="9720f-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="9720f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9720f-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9720f-112">Child Elements</span></span>

<span data-ttu-id="9720f-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="9720f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9720f-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9720f-114">Parent Elements</span></span>

|<span data-ttu-id="9720f-115">Élément</span><span class="sxs-lookup"><span data-stu-id="9720f-115">Element</span></span>|<span data-ttu-id="9720f-116">Description</span><span class="sxs-lookup"><span data-stu-id="9720f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9720f-117">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="9720f-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="9720f-118">Définit la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="9720f-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9720f-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="9720f-119">Text Value</span></span>

<span data-ttu-id="9720f-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="9720f-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="9720f-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="9720f-121">Remarks</span></span>

<span data-ttu-id="9720f-122">Si cet élément est utilisé, vous ne pouvez pas spécifier le [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) élément lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="9720f-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="9720f-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9720f-123">See Also</span></span>

[<span data-ttu-id="9720f-124">Élément PropertyName pour ItemSelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="9720f-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="9720f-125">Élément ItemSelectionCondition de ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="9720f-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="9720f-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9720f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
