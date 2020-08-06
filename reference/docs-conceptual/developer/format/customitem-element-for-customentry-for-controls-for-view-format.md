---
title: Élément CustomItem pour CustomEntry pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 747ea14e7118be62ebee00e7d80af2dccb5c8353
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785844"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="6c1a3-102">CustomItem, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="6c1a3-103">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="6c1a3-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="6c1a3-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour la vue (format) élément CustomControl pour le contrôle des contrôles pour l’élément View (format) CustomEntries pour CustomControl pour l’élément View (format) CustomEntry pour CustomEntries pour les contrôles pour l’élément View (format) CustomItem pour la vue (format)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6c1a3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c1a3-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6c1a3-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6c1a3-107">Attributes and Elements</span></span>

<span data-ttu-id="6c1a3-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomItem` élément.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="6c1a3-109">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="6c1a3-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="6c1a3-110">Attributes</span></span>

<span data-ttu-id="6c1a3-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6c1a3-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6c1a3-112">Child Elements</span></span>

|<span data-ttu-id="6c1a3-113">Élément</span><span class="sxs-lookup"><span data-stu-id="6c1a3-113">Element</span></span>|<span data-ttu-id="6c1a3-114">Description</span><span class="sxs-lookup"><span data-stu-id="6c1a3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6c1a3-115">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="6c1a3-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-116">Optional element.</span></span><br /><br /> <span data-ttu-id="6c1a3-117">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="6c1a3-118">Frame, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="6c1a3-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-119">Optional element.</span></span><br /><br /> <span data-ttu-id="6c1a3-120">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="6c1a3-121">NewLine, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="6c1a3-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-122">Optional element.</span></span><br /><br /> <span data-ttu-id="6c1a3-123">Ajoute une ligne vide à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="6c1a3-124">Text, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="6c1a3-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-125">Optional element.</span></span><br /><br /> <span data-ttu-id="6c1a3-126">Ajoute du texte, tel que des parenthèses ou des crochets, à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6c1a3-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6c1a3-127">Parent Elements</span></span>

|<span data-ttu-id="6c1a3-128">Élément</span><span class="sxs-lookup"><span data-stu-id="6c1a3-128">Element</span></span>|<span data-ttu-id="6c1a3-129">Description</span><span class="sxs-lookup"><span data-stu-id="6c1a3-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6c1a3-130">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="6c1a3-131">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6c1a3-132">Notes</span><span class="sxs-lookup"><span data-stu-id="6c1a3-132">Remarks</span></span>

<span data-ttu-id="6c1a3-133">Lorsque vous spécifiez les éléments enfants de l' `CustomItem` élément, gardez à l’esprit les points suivants :</span><span class="sxs-lookup"><span data-stu-id="6c1a3-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="6c1a3-134">Les éléments enfants doivent être ajoutés dans la séquence suivante : `ExpressionBinding` , `NewLine` , `Text` et `Frame` .</span><span class="sxs-lookup"><span data-stu-id="6c1a3-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="6c1a3-135">Il n’existe pas de limite maximale pour le nombre de séquences que vous pouvez spécifier.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="6c1a3-136">Dans chaque séquence, il n’existe pas de limite maximale pour le nombre d' `ExpressionBinding` éléments que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c1a3-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c1a3-137">See Also</span></span>

[<span data-ttu-id="6c1a3-138">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="6c1a3-139">Frame, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="6c1a3-140">NewLine, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="6c1a3-141">Text, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="6c1a3-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="6c1a3-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
