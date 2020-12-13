---
ms.date: 09/13/2016
ms.topic: reference
title: CustomItem, élément pour CustomEntry pour Controls pour Configuration (Format)
description: CustomItem, élément pour CustomEntry pour Controls pour Configuration (Format)
ms.openlocfilehash: 06c399e982b6ac0fba9c11e20c468fe8bef6f694
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666771"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="47ced-103">CustomItem, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="47ced-103">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="47ced-104">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="47ced-104">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="47ced-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="47ced-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="47ced-106">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="47ced-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="47ced-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47ced-107">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="47ced-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="47ced-108">Attributes and Elements</span></span>

<span data-ttu-id="47ced-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomItem` élément.</span><span class="sxs-lookup"><span data-stu-id="47ced-109">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="47ced-110">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="47ced-110">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="47ced-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="47ced-111">Attributes</span></span>

<span data-ttu-id="47ced-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="47ced-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="47ced-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="47ced-113">Child Elements</span></span>

|<span data-ttu-id="47ced-114">Élément</span><span class="sxs-lookup"><span data-stu-id="47ced-114">Element</span></span>|<span data-ttu-id="47ced-115">Description</span><span class="sxs-lookup"><span data-stu-id="47ced-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47ced-116">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="47ced-116">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="47ced-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="47ced-117">Optional element.</span></span><br /><br /> <span data-ttu-id="47ced-118">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="47ced-118">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="47ced-119">Frame, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="47ced-119">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="47ced-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="47ced-120">Optional element.</span></span><br /><br /> <span data-ttu-id="47ced-121">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="47ced-121">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="47ced-122">NewLine, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="47ced-122">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="47ced-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="47ced-123">Optional element.</span></span><br /><br /> <span data-ttu-id="47ced-124">Ajoute une ligne vide à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="47ced-124">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="47ced-125">Text, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="47ced-125">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="47ced-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="47ced-126">Optional element.</span></span><br /><br /> <span data-ttu-id="47ced-127">Ajoute du texte, tel que des parenthèses ou des crochets, à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="47ced-127">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="47ced-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="47ced-128">Parent Elements</span></span>

|<span data-ttu-id="47ced-129">Élément</span><span class="sxs-lookup"><span data-stu-id="47ced-129">Element</span></span>|<span data-ttu-id="47ced-130">Description</span><span class="sxs-lookup"><span data-stu-id="47ced-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47ced-131">CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="47ced-131">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="47ced-132">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="47ced-132">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="47ced-133">Notes</span><span class="sxs-lookup"><span data-stu-id="47ced-133">Remarks</span></span>

<span data-ttu-id="47ced-134">Lorsque vous spécifiez les éléments enfants de l' `CustomItem` élément, gardez à l’esprit les points suivants :</span><span class="sxs-lookup"><span data-stu-id="47ced-134">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="47ced-135">Les éléments enfants doivent être ajoutés dans la séquence suivante : `ExpressionBinding` , `NewLine` , `Text` et `Frame` .</span><span class="sxs-lookup"><span data-stu-id="47ced-135">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="47ced-136">Il n’existe pas de limite maximale pour le nombre de séquences que vous pouvez spécifier.</span><span class="sxs-lookup"><span data-stu-id="47ced-136">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="47ced-137">Dans chaque séquence, il n’existe pas de limite maximale pour le nombre d' `ExpressionBinding` éléments que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="47ced-137">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="47ced-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47ced-138">See Also</span></span>

[<span data-ttu-id="47ced-139">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="47ced-139">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="47ced-140">Frame, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="47ced-140">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="47ced-141">NewLine, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="47ced-141">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="47ced-142">Text, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="47ced-142">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="47ced-143">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="47ced-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
