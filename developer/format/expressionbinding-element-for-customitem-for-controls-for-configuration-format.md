---
title: Élément ExpressionBinding pour CustomItem pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855135"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="69516-102">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="69516-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="69516-103">Définit les données qui sont affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="69516-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="69516-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="69516-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="69516-105">Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de CustomItem Configuration (Format) pour CustomEntry pour les contrôles pour l’élément de Configuration ExpressionBinding CustomItem pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="69516-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="69516-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69516-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="69516-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="69516-107">Attributes and Elements</span></span>

<span data-ttu-id="69516-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ExpressionBinding` élément.</span><span class="sxs-lookup"><span data-stu-id="69516-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="69516-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="69516-109">Attributes</span></span>

<span data-ttu-id="69516-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="69516-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="69516-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="69516-111">Child Elements</span></span>

|<span data-ttu-id="69516-112">Élément</span><span class="sxs-lookup"><span data-stu-id="69516-112">Element</span></span>|<span data-ttu-id="69516-113">Description</span><span class="sxs-lookup"><span data-stu-id="69516-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="69516-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="69516-114">Optional element.</span></span><br /><br /> <span data-ttu-id="69516-115">Définit un contrôle qui est utilisé par ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="69516-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="69516-116">Élément CustomControlName pour ExpressionBinding pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="69516-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="69516-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="69516-117">Optional element.</span></span><br /><br /> <span data-ttu-id="69516-118">Spécifie le nom d’un contrôle commun ou un contrôle d’affichage.</span><span class="sxs-lookup"><span data-stu-id="69516-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="69516-119">Élément EnumerateCollection pour ExpressionBinding pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="69516-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="69516-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="69516-120">Optional element.</span></span><br /><br /> <span data-ttu-id="69516-121">Spécifié que les éléments des collections sont affichés par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="69516-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="69516-122">Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="69516-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="69516-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="69516-123">Optional element.</span></span><br /><br /> <span data-ttu-id="69516-124">Définit la condition qui doit exister pour ce contrôle commun à utiliser.</span><span class="sxs-lookup"><span data-stu-id="69516-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="69516-125">Élément PropertyName pour ExpressionBinding pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="69516-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="69516-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="69516-126">Optional element.</span></span><br /><br /> <span data-ttu-id="69516-127">Spécifie la propriété .NET dont la valeur est affichée par le contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="69516-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="69516-128">Élément ScriptBlock pour ExpressionBinding pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="69516-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="69516-129">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="69516-129">Optional element.</span></span><br /><br /> <span data-ttu-id="69516-130">Spécifie le script dont la valeur est affichée par le contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="69516-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="69516-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="69516-131">Parent Elements</span></span>

|<span data-ttu-id="69516-132">Élément</span><span class="sxs-lookup"><span data-stu-id="69516-132">Element</span></span>|<span data-ttu-id="69516-133">Description</span><span class="sxs-lookup"><span data-stu-id="69516-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="69516-134">Élément CustomItem pour CustomEntry pour les contrôles de Configuration</span><span class="sxs-lookup"><span data-stu-id="69516-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="69516-135">Définit les données affichées par la vue de contrôle personnalisé et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="69516-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="69516-136">Remarques</span><span class="sxs-lookup"><span data-stu-id="69516-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="69516-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69516-137">See Also</span></span>

[<span data-ttu-id="69516-138">Élément CustomItem pour CustomEntry pour les contrôles de Configuration</span><span class="sxs-lookup"><span data-stu-id="69516-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="69516-139">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="69516-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
