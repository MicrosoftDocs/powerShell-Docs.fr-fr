---
title: Élément ScriptBlock pour ItemSeclectionCondition pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f44b1a7f059fa5f41c19eed93762b61eda5110e8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772890"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="3d9f5-102">ScriptBlock, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3d9f5-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3d9f5-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="3d9f5-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="3d9f5-104">Lorsque ce script est évalué à `true` , la condition est remplie et le contrôle est utilisé.</span><span class="sxs-lookup"><span data-stu-id="3d9f5-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="3d9f5-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="3d9f5-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3d9f5-106">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément CustomItem pour CustomEntry pour les contrôles de l’élément ExpressionBinding de configuration pour CustomItem pour les contrôles pour la configuration (format) ItemSelectionCondition élément pour ExpressionBinding pour les contrôles de configuration (format) élément ScriptBlock pour ItemSelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3d9f5-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3d9f5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d9f5-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d9f5-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3d9f5-108">Attributes and Elements</span></span>

<span data-ttu-id="3d9f5-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="3d9f5-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d9f5-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="3d9f5-110">Attributes</span></span>

<span data-ttu-id="3d9f5-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3d9f5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d9f5-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3d9f5-112">Child Elements</span></span>

<span data-ttu-id="3d9f5-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3d9f5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3d9f5-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3d9f5-114">Parent Elements</span></span>

|<span data-ttu-id="3d9f5-115">Élément</span><span class="sxs-lookup"><span data-stu-id="3d9f5-115">Element</span></span>|<span data-ttu-id="3d9f5-116">Description</span><span class="sxs-lookup"><span data-stu-id="3d9f5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d9f5-117">ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3d9f5-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="3d9f5-118">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="3d9f5-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3d9f5-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="3d9f5-119">Text Value</span></span>

<span data-ttu-id="3d9f5-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="3d9f5-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="3d9f5-121">Notes</span><span class="sxs-lookup"><span data-stu-id="3d9f5-121">Remarks</span></span>

<span data-ttu-id="3d9f5-122">Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="3d9f5-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d9f5-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d9f5-123">See Also</span></span>

[<span data-ttu-id="3d9f5-124">PropertyName, élément pour ItemSelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3d9f5-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="3d9f5-125">ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3d9f5-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="3d9f5-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="3d9f5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
