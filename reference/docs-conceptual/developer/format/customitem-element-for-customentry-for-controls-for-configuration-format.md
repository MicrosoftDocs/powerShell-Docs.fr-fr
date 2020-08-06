---
title: Élément CustomItem pour CustomEntry pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bb8124242496f192717127f201674bc1428e5de0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785861"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="db77c-102">CustomItem, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="db77c-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="db77c-103">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="db77c-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="db77c-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="db77c-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="db77c-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="db77c-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="db77c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db77c-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="db77c-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="db77c-107">Attributes and Elements</span></span>

<span data-ttu-id="db77c-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomItem` élément.</span><span class="sxs-lookup"><span data-stu-id="db77c-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="db77c-109">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="db77c-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="db77c-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="db77c-110">Attributes</span></span>

<span data-ttu-id="db77c-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="db77c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="db77c-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="db77c-112">Child Elements</span></span>

|<span data-ttu-id="db77c-113">Élément</span><span class="sxs-lookup"><span data-stu-id="db77c-113">Element</span></span>|<span data-ttu-id="db77c-114">Description</span><span class="sxs-lookup"><span data-stu-id="db77c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db77c-115">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="db77c-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="db77c-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db77c-116">Optional element.</span></span><br /><br /> <span data-ttu-id="db77c-117">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="db77c-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="db77c-118">Frame, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="db77c-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="db77c-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db77c-119">Optional element.</span></span><br /><br /> <span data-ttu-id="db77c-120">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="db77c-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="db77c-121">NewLine, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="db77c-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="db77c-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db77c-122">Optional element.</span></span><br /><br /> <span data-ttu-id="db77c-123">Ajoute une ligne vide à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="db77c-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="db77c-124">Text, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="db77c-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="db77c-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db77c-125">Optional element.</span></span><br /><br /> <span data-ttu-id="db77c-126">Ajoute du texte, tel que des parenthèses ou des crochets, à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="db77c-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="db77c-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="db77c-127">Parent Elements</span></span>

|<span data-ttu-id="db77c-128">Élément</span><span class="sxs-lookup"><span data-stu-id="db77c-128">Element</span></span>|<span data-ttu-id="db77c-129">Description</span><span class="sxs-lookup"><span data-stu-id="db77c-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db77c-130">CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="db77c-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="db77c-131">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="db77c-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="db77c-132">Notes</span><span class="sxs-lookup"><span data-stu-id="db77c-132">Remarks</span></span>

<span data-ttu-id="db77c-133">Lorsque vous spécifiez les éléments enfants de l' `CustomItem` élément, gardez à l’esprit les points suivants :</span><span class="sxs-lookup"><span data-stu-id="db77c-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="db77c-134">Les éléments enfants doivent être ajoutés dans la séquence suivante : `ExpressionBinding` , `NewLine` , `Text` et `Frame` .</span><span class="sxs-lookup"><span data-stu-id="db77c-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="db77c-135">Il n’existe pas de limite maximale pour le nombre de séquences que vous pouvez spécifier.</span><span class="sxs-lookup"><span data-stu-id="db77c-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="db77c-136">Dans chaque séquence, il n’existe pas de limite maximale pour le nombre d' `ExpressionBinding` éléments que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="db77c-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="db77c-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db77c-137">See Also</span></span>

[<span data-ttu-id="db77c-138">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="db77c-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="db77c-139">Frame, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="db77c-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="db77c-140">NewLine, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="db77c-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="db77c-141">Text, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="db77c-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="db77c-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="db77c-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
