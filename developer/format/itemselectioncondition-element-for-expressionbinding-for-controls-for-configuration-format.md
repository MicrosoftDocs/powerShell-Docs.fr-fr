---
title: Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065499"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="f4707-102">ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="f4707-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f4707-103">Définit la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f4707-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="f4707-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="f4707-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f4707-105">Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de CustomItem Configuration (Format) pour CustomEntry pour les contrôles pour l’élément de Configuration ExpressionBinding CustomItem pour les contrôles de Configuration (Format) Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="f4707-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f4707-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4707-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f4707-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="f4707-107">Attributes and Elements</span></span>

<span data-ttu-id="f4707-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ItemSelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="f4707-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f4707-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="f4707-109">Attributes</span></span>

<span data-ttu-id="f4707-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f4707-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f4707-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f4707-111">Child Elements</span></span>

|<span data-ttu-id="f4707-112">Élément</span><span class="sxs-lookup"><span data-stu-id="f4707-112">Element</span></span>|<span data-ttu-id="f4707-113">Description</span><span class="sxs-lookup"><span data-stu-id="f4707-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4707-114">Élément PropertyName pour ItemSelectionCondition pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="f4707-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f4707-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="f4707-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f4707-116">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="f4707-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f4707-117">Élément ScriptBlock pour ItemSelectionCondition pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="f4707-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f4707-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="f4707-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f4707-119">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="f4707-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f4707-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f4707-120">Parent Elements</span></span>

|<span data-ttu-id="f4707-121">Élément</span><span class="sxs-lookup"><span data-stu-id="f4707-121">Element</span></span>|<span data-ttu-id="f4707-122">Description</span><span class="sxs-lookup"><span data-stu-id="f4707-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4707-123">Élément ExpressionBinding pour CustomItem pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="f4707-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="f4707-124">Définit les données qui sont affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="f4707-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f4707-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="f4707-125">Remarks</span></span>

<span data-ttu-id="f4707-126">Vous pouvez spécifier un nom de propriété ou un script pour cette condition mais que vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="f4707-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4707-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4707-127">See Also</span></span>

[<span data-ttu-id="f4707-128">Élément PropertyName pour ItemSelectionCondition pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="f4707-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f4707-129">Élément ScriptBlock pour ItemSelectionCondition pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="f4707-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f4707-130">Élément ExpressionBinding pour CustomItem pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="f4707-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f4707-131">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f4707-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
