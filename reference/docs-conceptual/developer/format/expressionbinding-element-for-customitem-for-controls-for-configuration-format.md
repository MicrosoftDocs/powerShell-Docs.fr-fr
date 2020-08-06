---
title: Élément ExpressionBinding pour CustomItem pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1ad83fa9d915822eaefb490658f8a219defdddf2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773910"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="505fa-102">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="505fa-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="505fa-103">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="505fa-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="505fa-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="505fa-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="505fa-105">Élément de configuration (format) Controls, élément de configuration (format), élément de contrôle pour la configuration (format) CustomControl, élément de Control pour configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément CustomItem pour CustomEntry pour les contrôles pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="505fa-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="505fa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="505fa-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="505fa-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="505fa-107">Attributes and Elements</span></span>

<span data-ttu-id="505fa-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ExpressionBinding` élément.</span><span class="sxs-lookup"><span data-stu-id="505fa-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="505fa-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="505fa-109">Attributes</span></span>

<span data-ttu-id="505fa-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="505fa-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="505fa-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="505fa-111">Child Elements</span></span>

|<span data-ttu-id="505fa-112">Élément</span><span class="sxs-lookup"><span data-stu-id="505fa-112">Element</span></span>|<span data-ttu-id="505fa-113">Description</span><span class="sxs-lookup"><span data-stu-id="505fa-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="505fa-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="505fa-114">Optional element.</span></span><br /><br /> <span data-ttu-id="505fa-115">Définit un contrôle qui est utilisé par ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="505fa-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="505fa-116">CustomControlName, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="505fa-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="505fa-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="505fa-117">Optional element.</span></span><br /><br /> <span data-ttu-id="505fa-118">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="505fa-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="505fa-119">EnumerateCollection, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="505fa-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="505fa-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="505fa-120">Optional element.</span></span><br /><br /> <span data-ttu-id="505fa-121">Spécifie que les éléments des collections sont affichés par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="505fa-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="505fa-122">ItemSelectionCondition, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="505fa-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="505fa-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="505fa-123">Optional element.</span></span><br /><br /> <span data-ttu-id="505fa-124">Définit la condition qui doit exister pour que ce contrôle commun soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="505fa-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="505fa-125">PropertyName, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="505fa-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="505fa-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="505fa-126">Optional element.</span></span><br /><br /> <span data-ttu-id="505fa-127">Spécifie la propriété .NET dont la valeur est affichée par le contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="505fa-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="505fa-128">ScriptBlock, élément pour ExpressionBinding pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="505fa-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="505fa-129">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="505fa-129">Optional element.</span></span><br /><br /> <span data-ttu-id="505fa-130">Spécifie le script dont la valeur est affichée par le contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="505fa-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="505fa-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="505fa-131">Parent Elements</span></span>

|<span data-ttu-id="505fa-132">Élément</span><span class="sxs-lookup"><span data-stu-id="505fa-132">Element</span></span>|<span data-ttu-id="505fa-133">Description</span><span class="sxs-lookup"><span data-stu-id="505fa-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="505fa-134">Élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="505fa-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="505fa-135">Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="505fa-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="505fa-136">Notes</span><span class="sxs-lookup"><span data-stu-id="505fa-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="505fa-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="505fa-137">See Also</span></span>

[<span data-ttu-id="505fa-138">Élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="505fa-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="505fa-139">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="505fa-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
