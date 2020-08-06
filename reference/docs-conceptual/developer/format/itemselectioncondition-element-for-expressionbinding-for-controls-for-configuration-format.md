---
title: Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3bfd3efe916b4d88c024de8f959482cab515f777
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781220"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="f8842-102">ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="f8842-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f8842-103">Définit la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="f8842-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="f8842-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="f8842-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f8842-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format), élément CustomItem pour CustomEntry pour les contrôles de l’élément de configuration ExpressionBinding pour CustomItem pour les contrôles de configuration (format) ItemSelectionCondition élément pour ExpressionBinding pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="f8842-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f8842-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8842-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f8842-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f8842-107">Attributes and Elements</span></span>

<span data-ttu-id="f8842-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ItemSelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="f8842-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f8842-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="f8842-109">Attributes</span></span>

<span data-ttu-id="f8842-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f8842-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f8842-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f8842-111">Child Elements</span></span>

|<span data-ttu-id="f8842-112">Élément</span><span class="sxs-lookup"><span data-stu-id="f8842-112">Element</span></span>|<span data-ttu-id="f8842-113">Description</span><span class="sxs-lookup"><span data-stu-id="f8842-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8842-114">PropertyName, élément de ItemSelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="f8842-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f8842-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="f8842-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f8842-116">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="f8842-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f8842-117">Élément ScriptBlock pour ItemSelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="f8842-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f8842-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="f8842-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f8842-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="f8842-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f8842-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f8842-120">Parent Elements</span></span>

|<span data-ttu-id="f8842-121">Élément</span><span class="sxs-lookup"><span data-stu-id="f8842-121">Element</span></span>|<span data-ttu-id="f8842-122">Description</span><span class="sxs-lookup"><span data-stu-id="f8842-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8842-123">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="f8842-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="f8842-124">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="f8842-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f8842-125">Notes</span><span class="sxs-lookup"><span data-stu-id="f8842-125">Remarks</span></span>

<span data-ttu-id="f8842-126">Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="f8842-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8842-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8842-127">See Also</span></span>

[<span data-ttu-id="f8842-128">PropertyName, élément de ItemSelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="f8842-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f8842-129">Élément ScriptBlock pour ItemSelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="f8842-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f8842-130">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="f8842-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f8842-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8842-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
