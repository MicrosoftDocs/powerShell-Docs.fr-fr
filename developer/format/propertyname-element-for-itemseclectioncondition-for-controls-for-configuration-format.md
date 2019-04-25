---
title: Élément PropertyName pour ItemSeclectionCondition pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064890"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="24919-102">PropertyName, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="24919-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="24919-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="24919-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="24919-104">Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie, et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="24919-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="24919-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="24919-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="24919-106">Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de CustomItem Configuration (Format) pour CustomEntry pour les contrôles pour l’élément de Configuration ExpressionBinding CustomItem pour les contrôles de Configuration (Format) Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles d’élément de PropertyName Configuration (Format) pour ItemSeclectionCondition pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="24919-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="24919-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24919-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="24919-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="24919-108">Attributes and Elements</span></span>

<span data-ttu-id="24919-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="24919-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="24919-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="24919-110">Attributes</span></span>

<span data-ttu-id="24919-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="24919-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="24919-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="24919-112">Child Elements</span></span>

<span data-ttu-id="24919-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="24919-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="24919-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="24919-114">Parent Elements</span></span>

|<span data-ttu-id="24919-115">Élément</span><span class="sxs-lookup"><span data-stu-id="24919-115">Element</span></span>|<span data-ttu-id="24919-116">Description</span><span class="sxs-lookup"><span data-stu-id="24919-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="24919-117">Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="24919-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="24919-118">Définit la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="24919-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="24919-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="24919-119">Text Value</span></span>

<span data-ttu-id="24919-120">Spécifiez le nom de la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="24919-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="24919-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="24919-121">Remarks</span></span>

<span data-ttu-id="24919-122">Si cet élément est utilisé, vous ne pouvez pas spécifier le [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) élément lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="24919-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="24919-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24919-123">See Also</span></span>

[<span data-ttu-id="24919-124">Élément ScriptBlock pour ItemSeclectionCondition pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="24919-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="24919-125">Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="24919-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="24919-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="24919-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
