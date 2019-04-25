---
title: Élément ScriptBlock pour ItemSelectionCondition pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064473"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="15da7-102">ScriptBlock, élément pour ItemSelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="15da7-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="15da7-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="15da7-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="15da7-104">Lorsque ce script est évalué à `true`, la condition est remplie, et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="15da7-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="15da7-105">Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="15da7-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="15da7-106">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour élément d’affichage (Format) de ExpressionBinding pour CustomItem pour CustomControl pour l’élément de ItemSelectionCondition d’affichage (Format) pour la liaison d’Expression pour CustomControl pour élément ScriptBlock de vue (Format) pour ItemSelectionCondition pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="15da7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="15da7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15da7-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="15da7-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="15da7-108">Attributes and Elements</span></span>

<span data-ttu-id="15da7-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="15da7-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="15da7-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="15da7-110">Attributes</span></span>

<span data-ttu-id="15da7-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="15da7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="15da7-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="15da7-112">Child Elements</span></span>

<span data-ttu-id="15da7-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="15da7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="15da7-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="15da7-114">Parent Elements</span></span>

|<span data-ttu-id="15da7-115">Élément</span><span class="sxs-lookup"><span data-stu-id="15da7-115">Element</span></span>|<span data-ttu-id="15da7-116">Description</span><span class="sxs-lookup"><span data-stu-id="15da7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="15da7-117">Élément ItemSelectionCondition pour la liaison d’Expression pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="15da7-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="15da7-118">Définit la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="15da7-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="15da7-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="15da7-119">Text Value</span></span>

<span data-ttu-id="15da7-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="15da7-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="15da7-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="15da7-121">Remarks</span></span>

<span data-ttu-id="15da7-122">Si cet élément est utilisé, vous ne pouvez pas spécifier le [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) élément lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="15da7-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="15da7-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15da7-123">See Also</span></span>

[<span data-ttu-id="15da7-124">Élément PropertyName pour ItemSelectionCondition pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="15da7-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="15da7-125">Élément ItemSelectionCondition pour la liaison d’Expression pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="15da7-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="15da7-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="15da7-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
