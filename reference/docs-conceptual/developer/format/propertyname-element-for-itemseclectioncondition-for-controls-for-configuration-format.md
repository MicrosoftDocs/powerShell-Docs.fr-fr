---
title: PropertyName, élément de ItemSeclectionCondition pour les contrôles de configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362528"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="8a119-102">PropertyName, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="8a119-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="8a119-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="8a119-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="8a119-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true`, la condition est remplie et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="8a119-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="8a119-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="8a119-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="8a119-106">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration ( Format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément CustomItem pour CustomEntry pour les contrôles pour la configuration ExpressionBinding, élément pour CustomItem pour les contrôles de configuration (format) Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles pour la configuration (format) PropertyName, élément pour ItemSeclectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8a119-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8a119-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a119-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8a119-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="8a119-108">Attributes and Elements</span></span>

<span data-ttu-id="8a119-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="8a119-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8a119-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="8a119-110">Attributes</span></span>

<span data-ttu-id="8a119-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="8a119-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8a119-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8a119-112">Child Elements</span></span>

<span data-ttu-id="8a119-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="8a119-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8a119-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8a119-114">Parent Elements</span></span>

|<span data-ttu-id="8a119-115">Élément</span><span class="sxs-lookup"><span data-stu-id="8a119-115">Element</span></span>|<span data-ttu-id="8a119-116">Description</span><span class="sxs-lookup"><span data-stu-id="8a119-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8a119-117">Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8a119-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="8a119-118">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="8a119-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8a119-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="8a119-119">Text Value</span></span>

<span data-ttu-id="8a119-120">Spécifiez le nom de la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="8a119-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a119-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="8a119-121">Remarks</span></span>

<span data-ttu-id="8a119-122">Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="8a119-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a119-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a119-123">See Also</span></span>

[<span data-ttu-id="8a119-124">Élément ScriptBlock pour ItemSeclectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8a119-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="8a119-125">Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8a119-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="8a119-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a119-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
