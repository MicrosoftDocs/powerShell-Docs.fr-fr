---
ms.date: 09/13/2016
ms.topic: reference
title: CustomItem, élément pour CustomEntry pour Controls pour View (Format)
description: CustomItem, élément pour CustomEntry pour Controls pour View (Format)
ms.openlocfilehash: 67bff97c27cfedf046b17eea438efcd66ae2ee4a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666754"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="06e30-103">CustomItem, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="06e30-103">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="06e30-104">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="06e30-104">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="06e30-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="06e30-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="06e30-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour la vue (format) élément CustomControl pour le contrôle des contrôles pour l’élément View (format) CustomEntries pour CustomControl pour l’élément View (format) CustomEntry pour CustomEntries pour les contrôles pour l’élément View (format) CustomItem pour la vue (format)</span><span class="sxs-lookup"><span data-stu-id="06e30-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06e30-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06e30-107">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="06e30-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="06e30-108">Attributes and Elements</span></span>

<span data-ttu-id="06e30-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomItem` élément.</span><span class="sxs-lookup"><span data-stu-id="06e30-109">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="06e30-110">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="06e30-110">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="06e30-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="06e30-111">Attributes</span></span>

<span data-ttu-id="06e30-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="06e30-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06e30-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="06e30-113">Child Elements</span></span>

|<span data-ttu-id="06e30-114">Élément</span><span class="sxs-lookup"><span data-stu-id="06e30-114">Element</span></span>|<span data-ttu-id="06e30-115">Description</span><span class="sxs-lookup"><span data-stu-id="06e30-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06e30-116">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="06e30-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="06e30-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="06e30-117">Optional element.</span></span><br /><br /> <span data-ttu-id="06e30-118">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="06e30-118">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="06e30-119">Frame, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="06e30-119">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="06e30-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="06e30-120">Optional element.</span></span><br /><br /> <span data-ttu-id="06e30-121">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="06e30-121">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="06e30-122">NewLine, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="06e30-122">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="06e30-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="06e30-123">Optional element.</span></span><br /><br /> <span data-ttu-id="06e30-124">Ajoute une ligne vide à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="06e30-124">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="06e30-125">Text, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="06e30-125">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="06e30-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="06e30-126">Optional element.</span></span><br /><br /> <span data-ttu-id="06e30-127">Ajoute du texte, tel que des parenthèses ou des crochets, à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="06e30-127">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="06e30-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="06e30-128">Parent Elements</span></span>

|<span data-ttu-id="06e30-129">Élément</span><span class="sxs-lookup"><span data-stu-id="06e30-129">Element</span></span>|<span data-ttu-id="06e30-130">Description</span><span class="sxs-lookup"><span data-stu-id="06e30-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06e30-131">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="06e30-131">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="06e30-132">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="06e30-132">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="06e30-133">Notes</span><span class="sxs-lookup"><span data-stu-id="06e30-133">Remarks</span></span>

<span data-ttu-id="06e30-134">Lorsque vous spécifiez les éléments enfants de l' `CustomItem` élément, gardez à l’esprit les points suivants :</span><span class="sxs-lookup"><span data-stu-id="06e30-134">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="06e30-135">Les éléments enfants doivent être ajoutés dans la séquence suivante : `ExpressionBinding` , `NewLine` , `Text` et `Frame` .</span><span class="sxs-lookup"><span data-stu-id="06e30-135">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="06e30-136">Il n’existe pas de limite maximale pour le nombre de séquences que vous pouvez spécifier.</span><span class="sxs-lookup"><span data-stu-id="06e30-136">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="06e30-137">Dans chaque séquence, il n’existe pas de limite maximale pour le nombre d' `ExpressionBinding` éléments que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="06e30-137">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="06e30-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06e30-138">See Also</span></span>

[<span data-ttu-id="06e30-139">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="06e30-139">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="06e30-140">Frame, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="06e30-140">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="06e30-141">NewLine, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="06e30-141">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="06e30-142">Text, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="06e30-142">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="06e30-143">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="06e30-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
