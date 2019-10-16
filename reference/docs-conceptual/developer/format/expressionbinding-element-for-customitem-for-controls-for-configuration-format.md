---
title: Élément ExpressionBinding pour CustomItem pour les contrôles de configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363188"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="233e9-102">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="233e9-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="233e9-103">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="233e9-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="233e9-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="233e9-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="233e9-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration ( Format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément CustomItem pour CustomEntry pour les contrôles pour la configuration ExpressionBinding, élément pour CustomItem pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="233e9-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="233e9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="233e9-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="233e9-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="233e9-107">Attributes and Elements</span></span>

<span data-ttu-id="233e9-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ExpressionBinding`.</span><span class="sxs-lookup"><span data-stu-id="233e9-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="233e9-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="233e9-109">Attributes</span></span>

<span data-ttu-id="233e9-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="233e9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="233e9-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="233e9-111">Child Elements</span></span>

|<span data-ttu-id="233e9-112">Élément</span><span class="sxs-lookup"><span data-stu-id="233e9-112">Element</span></span>|<span data-ttu-id="233e9-113">Description</span><span class="sxs-lookup"><span data-stu-id="233e9-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="233e9-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="233e9-114">Optional element.</span></span><br /><br /> <span data-ttu-id="233e9-115">Définit un contrôle qui est utilisé par ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="233e9-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="233e9-116">Élément CustomControlName pour ExpressionBinding pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="233e9-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="233e9-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="233e9-117">Optional element.</span></span><br /><br /> <span data-ttu-id="233e9-118">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="233e9-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="233e9-119">Élément EnumerateCollection pour ExpressionBinding pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="233e9-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="233e9-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="233e9-120">Optional element.</span></span><br /><br /> <span data-ttu-id="233e9-121">Spécifie que les éléments des collections sont affichés par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="233e9-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="233e9-122">Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="233e9-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="233e9-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="233e9-123">Optional element.</span></span><br /><br /> <span data-ttu-id="233e9-124">Définit la condition qui doit exister pour que ce contrôle commun soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="233e9-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="233e9-125">PropertyName, élément de ExpressionBinding pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="233e9-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="233e9-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="233e9-126">Optional element.</span></span><br /><br /> <span data-ttu-id="233e9-127">Spécifie la propriété .NET dont la valeur est affichée par le contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="233e9-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="233e9-128">Élément ScriptBlock pour ExpressionBinding pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="233e9-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="233e9-129">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="233e9-129">Optional element.</span></span><br /><br /> <span data-ttu-id="233e9-130">Spécifie le script dont la valeur est affichée par le contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="233e9-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="233e9-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="233e9-131">Parent Elements</span></span>

|<span data-ttu-id="233e9-132">Élément</span><span class="sxs-lookup"><span data-stu-id="233e9-132">Element</span></span>|<span data-ttu-id="233e9-133">Description</span><span class="sxs-lookup"><span data-stu-id="233e9-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="233e9-134">Élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="233e9-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="233e9-135">Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="233e9-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="233e9-136">Remarks</span><span class="sxs-lookup"><span data-stu-id="233e9-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="233e9-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="233e9-137">See Also</span></span>

[<span data-ttu-id="233e9-138">Élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="233e9-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="233e9-139">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="233e9-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
